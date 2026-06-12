---
title: "PHP and apache uploading problems"
date: 2008-08-04
forum: Server Platforms
---

### Post by eludlow on 2008-08-04
I've a php upload script I've used many times on hosted servers, but I've just tried it on my Ubuntu machine and I cannot get it working.

The script is:

[PHP]$uploaddir = '/var/www/intranet/uploaded_files/';
$uploadfile = $uploaddir . $_FILES['filename']['name'];

if (move_uploaded_file($_FILES['filename']['tmp_name'], $uploadfile)) {
    echo "File is valid, and was successfully uploaded.\n";
} else {
    echo "File not uploaded - " . $_FILES['filename']['error'] . "\n";
}[/PHP]

In my phpinfo() the settings for uploads are as follows:

file_uploads: on
upload_max_filesize: 2M
upload_tmp_dir: no value

I'm wondering should upload_tmp_dir be set?  I would guess it defaults to /tmp if it's not set.  /tmp is CHMODed to 777, as is /var/www/intranet/uploaded_files/

$_FILES['filename']['error'] is not outputting anything.  

I've been playing with this for an hour or so now...and am stumped!  Any help appreciated.

Thanks,
Ed Ludlow

---

### Post by cdenley on 2008-08-04
Check the log for clues.
```

less /var/log/apache2/error.log

```

---

### Post by eludlow on 2008-08-04
Nothing showing in the logs.
E

---

### Post by hyper_ch on 2008-08-04
try
[php]
$uploadfile = $uploaddir . basename($_FILES['userfile']['name']);
[/php]

---

### Post by cdenley on 2008-08-04
What does this give you?
[php]
$uploaddir = '/var/www/intranet/uploaded_files/';
$uploadfile = $uploaddir . $_FILES['filename']['name'];
print_r($_FILES);
if (move_uploaded_file($_FILES['filename']['tmp_name'], $uploadfile)) {
    echo "File is valid, and was successfully uploaded.\n";
} else {
    echo "File not uploaded - " . $_FILES['filename']['error'] . "\n";
}
[/php]

---

### Post by eludlow on 2008-08-04
> **cdenley said:**
> What does this give you?
[php]
$uploaddir = '/var/www/intranet/uploaded_files/';
$uploadfile = $uploaddir . $_FILES['filename']['name'];
print_r($_FILES);
if (move_uploaded_file($_FILES['filename']['tmp_name'], $uploadfile)) {
    echo "File is valid, and was successfully uploaded.\n";
} else {
    echo "File not uploaded - " . $_FILES['filename']['error'] . "\n";
}
[/php]

"Array ( ) File not uploaded - " - so it's still returning nothing from $_FILES['x']['error'].

**hyper_ch** - adding the basename() function doesn't help either :(

Ed

---

