---
title: "Allow PHP script write permissions"
date: 2018-05-05
forum: Server Platforms
---

### Post by forumate on 2018-05-05
I have PHP script which lets users select an image and upload it to **/var/www/html/images**.
Currently the script works only if I give **/images** folder 777 permission, because it needs to save the images there.
That's not very secure, I suppose, so I wanted to know what would your solution be?

I was thinking to maybe take **/images** folder outside of **/var/www/html** and place it completely outside there so that users cant access it via address bar directly, and give it 777 permission there.
Is that OK? would love to get suggestions!

Thanks!

---

### Post by cariboo on 2018-05-07
Moved here so more people will see it.

---

### Post by darkod on 2018-05-08
Who is the owner of the images folder? I'm not web expert, but if php scripts run as www-data user (same as apache), then you just makes sure that is the owner of the folder. Then you can set permissions to something like 775 or even 770.

Bottom line is: find which user the script uses and that should be the folder owner.

---

### Post by SeijiSensei on 2018-05-08
On Ubuntu, the Apache web server runs as user www-data with group www-data.  As darkod says, that user needs to be able to write into any directories to which files are uploaded.

Usually I put such directories outside the web tree, like a separate /var/www/images directory with user:group www-data and 755 permissions.  I'm not sure I understand from reading your post what's supposed to happen to these files once they are uploaded?  Should they be viewable after upload?  If so, then the directory needs to be in the web tree, or referenced using an Alias directive in the configuration file for this virtual host:
```

<VirtualHost *:80>
ServerName myweb.example.com
DocumentRoot /var/www/html
Alias /images /var/www/images
[etc.]

```

Are you using the file uploading features in PHP?  The temporary upload directory is specified by the [upload_temp_dir](http://php.net/manual/en/ini.core.php#ini.upload-tmp-dir) directive in php.ini.  Usually you would use [move_uploaded_file()]("http://php.net/manual/en/function.move-uploaded-file.php") to relocate the file to its permanent location.  Both the temporary directory and the one specified in the target of move_uploaded_file() must be writable by the www-data user.

---

