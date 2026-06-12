---
title: "Server 10.04 no upload folder in /tmp with php upload script"
date: 2010-06-13
forum: Server Platforms
---

### Post by Gambakoker on 2010-06-13
Hello everyone,

I have set up a LAMP server with ubuntu 10.04 server edition x86 for my study in VMware Workstation 7.1 

For a assignment I had to make a php script that would load a file up to the server and set the name in a mysql database. According to the book the server should set the image in a cryptic folder in the /tmp/ folder.

This isn't working and i also try'd locate and find to find the image i uploaded. I checked the php.ini and file uploads were on but no folder so i set that one to /tmp/ but still no images. Can anyone help me with enabling this function?

If any more information is required or the scripts i'll post it.

Regards,

Gambakoker

---

### Post by Ryan Dwyer on 2010-06-13
Start by writing var_dump($_FILES) in your PHP script in your form processing code. If it's false, you've got something wrong with your upload form. You need a certain enctype attribute on your HTML form tag, but I don't recall what it is at the moment.

When uploading a file, it puts it in /tmp with a random, unused name. If you want to store it permanently you must move it out because the /tmp directory is cleared on every reboot. You don't need to worry about storing it in a folder inside /tmp.

Also, have a read of this:
[http://php.net/manual/en/features.file-upload.php](http://php.net/manual/en/features.file-upload.php)

---

### Post by Gambakoker on 2010-06-13
> **Ryan Dwyer said:**
> Start by writing var_dump($_FILES) in your PHP script in your form processing code. If it's false, you've got something wrong with your upload form. You need a certain enctype attribute on your HTML form tag, but I don't recall what it is at the moment.

When uploading a file, it puts it in /tmp with a random, unused name. If you want to store it permanently you must move it out because the /tmp directory is cleared on every reboot. You don't need to worry about storing it in a folder inside /tmp.

Also, have a read of this:
[http://php.net/manual/en/features.file-upload.php](http://php.net/manual/en/features.file-upload.php)

Thank you for the quick reply! It worked fantastic. To get a question about this now, the output of the var_dump was:

array(1) { ["screenshot"]=>  array(5) { ["name"]=>  string(11) "biggrin.gif" ["type"]=>  string(9) "image/gif" ["tmp_name"]=>  string(14) "/tmp/phpJvSJ94" ["error"]=>  int(0) ["size"]=>  int(1052) } } 

When i check my mysql database the tmp_name is stored correctly so that works fine to but when i check it on the server with ls -hal /tmp/ it's still empty (on 2 vmware defaults). Is that what it is supposed to do?

---

### Post by Ryan Dwyer on 2010-06-13
PHP (or Apache) is probably removing the file from /tmp after the request is finished. As I said earlier, if you want to store the file permanently you should move it out of /tmp in your form processing code.

---

