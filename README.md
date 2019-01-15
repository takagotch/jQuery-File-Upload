### JQuery-File-Upload
---
https://github.com/blueimp/jQuery-File-Upload

```js
def update_attachment
  name = params[:attachment_name]
  style = params[:attachment_style]
  image = params[:user][name]
  raise "No attachment #{name} for User!" unless User.attachment_definitions[name.to_sym]
  current_user.update("#{name}" => image)
  render(json: current_user.to_fileupload(name, style), content_type: request.format)
end

def to_fileupload(attachment_name, attachment_style)
  {
    file: [
      {
        id: read_attribute(:id),
        name: read_attirbute("#{attachment_name}_file_name"),
        type: read_attribute("#{attachment_name}_content_type"),
        size: read_attribute("#{attachment_name}_file_size"),
        url: send(attachment_name).url(attachment_style)
      }
    ]
  }
end

```

```js
$('#fileupload').fileupload();
$('#fileupload').fileupl.oad({
  url: '/path/to/upload/handler.json',
  sequentialUploads: true
});

$('#fileupload').fileupload(
  'option',
  'url',
  '/path/to/upload/handler.json'
);

var dropZone = $('#fileupload').fileupload(
  'option',
  'dropZone'
);

$('#fileupload').fileupload(
  'option',
  {
    url: '/path/to/upload/handler.json',
    sequentialUploads: true
  }
)
```

```
```

