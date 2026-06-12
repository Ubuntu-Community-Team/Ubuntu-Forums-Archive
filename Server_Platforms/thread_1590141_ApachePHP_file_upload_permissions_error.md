---
title: "Apache/PHP file upload permissions error"
date: 2010-10-07
forum: Server Platforms
---

### Post by starr0stealer on 2010-10-07
We are running into issues with a File Upload script written in PHP. We can upload files without issues except with .*x files (such as .docx) We are getting permission denied errors.

The error occurs when we use move upload file, to the new directory within our PHP app. If we give the uploads folder 777 access, it works fine without error. I dont like that. So I set it to 775 (Also dont like this), but it didnt work until I gave group ownership to www-data (I really dont like this)

This issue only happens on our production server, which is Ubuntu 9.04, running Apache2.2 and PHP5 will all the newest updates.
We also have all MIME's configured, and are able to download the file from Apache without error.
The first thing we noticed before the file permissions error, was that the MIME type changed to .zip when we used mime content type function. But yet using the FILES array, it still showed .docx.

Thoughts?

---

### Post by SeijiSensei on 2010-10-07
> **starr0stealer said:**
> The error occurs when we use move upload file, to the new directory within our PHP app. If we give the uploads folder 777 access, it works fine without error. I dont like that. So I set it to 775 (Also dont like this), but it didnt work until I gave group ownership to www-data (I really dont like this)

There really isn't another option since the Apache server needs to have write privileges to the destination location in order for the script to put the files there.

You could use 770 with root.www-data ownership, but regardless of how you configure the directory, if you're uploading files with a PHP script it's only going to have the same permissions as the www-data user that Apache runs as.

Is there some specific reason this arrangement bothers you so? The only way to become the www-data user is to use "su www-data" after gaining root privileges.  Obviously if an intruder already has root, you're in a lot bigger pickle.

---

### Post by starr0stealer on 2010-10-07
I was under the impression that once Apache is started the process is handed off from www-data to root. That therefore Apache is running under root. When I first deployed the Apache I sent everything to belong to root user and group, and until now never ran into permission issues.

The main reason I dont want anything to belong to www-data or the group, is that the account doesnt have a password that I am aware of. Which seems to be a security issue to me. 
From what I remember reading, in Linux you set Apache to start as one user and then its handed off to root, and you make root ownership of any content you need to display.
This is because the security issues with www-data.

The strangest part of this issue, is that only .*X files give us the permission errors, any other file type works fine with root and the owner and group. My scripts also work without any issues.

---

