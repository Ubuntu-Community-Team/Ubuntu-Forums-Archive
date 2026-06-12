---
title: "Drupal: how do I install it too my Webhost?"
date: 2007-06-29
forum: Server Platforms
---

### Post by jingo811 on 2007-06-29
I finally managed to install LAMP on my Ubuntu 6.06 Desktop after that installing Drupal following this guide was a cakewalk.
[https://help.ubuntu.com/community/Drupal#head-1ccec9154b045c6549f6f7e1ec](https://help.ubuntu.com/community/Drupal#head-1ccec9154b045c6549f6f7e1ec)...

But what I don't understand is how do I do this on my Webhost. I don't recall having priviligeus using CLI commands for my domain. And I'm not even sure that they're using Ubuntu Server. I only know they use the latest PHP and MySQL.

I saw this video but the files the guy uploaded via FTP seemed to be Windows files? (I'm still new to Linux so I'm not good with the .tar thingys yet!) Can I simply do the same to my Webhost?
[http://video.google.com/videoplay?docid=-1412997312232368487&q=drupal&to](http://video.google.com/videoplay?docid=-1412997312232368487&q=drupal&to)...
Since I didn't install like that for my Ubuntu Desktop I'm a little unsure how that click-and-drag approach will install Drupal correctly.

What can I do?
I'm using One.com by the way.

---

### Post by az on 2007-06-29
> **jingo811 said:**
> I finally managed to install LAMP on my Ubuntu 6.06 Desktop after that installing Drupal following this guide was a cakewalk.
[https://help.ubuntu.com/community/Drupal#head-1ccec9154b045c6549f6f7e1ec](https://help.ubuntu.com/community/Drupal#head-1ccec9154b045c6549f6f7e1ec)...


Thank you.  I wrote most of that.

Do you want to create a fresh install or copy the installation you already have on your Ubuntu box?

To do a fresh install, you can just follow the documentation that comes with Drupal.  To copy it, you basically need to do the same thing, but you need to copy your database into a file and then load that file into your hosting database.  You then need to change the settings.php file for that site to point to the new website URL as well as the new database name, user and password.

Check with your hosting provider as to how to upload stuff into your database.  They most probably use phpmyadmin.  You can install phpmyadmin on your Ubuntu box and export all your data into a file and then use phpmyadmin on the host server to import the data.

You can use Nautilus to do FTP.  Go to Places - Connect to server and enter your FTP information for your hosting provider.  That will create an icon on your desktop.  Open than and you will be browsing your hosting provider.

Open a nautilus window to your drupal install and drag and drop it into your web hosting provider one.  (Don't forget to show hidden files or you will forget to copy your .htaccess.)

---

### Post by jingo811 on 2007-06-30
tnx :p

Another thing...
```
sudo mkdir /var/www/drupal/files
**sudo chown www-data:www-data** /var/www/drupal/files
```
I've seen this chown www-data:www-data somewhere else also when doing configs for some other web stuff.  But I never understood what it means and how much I can change things on that CLI command without lowering the current security settings?

Drupal admin site complained about this:
> File system	Not writable
The [COLOR="Red"]directory files is not writable[/COLOR]. You may need to set the correct directory at the file system settings page or change the current directory's permissions so that it is writable.
> 
mike@sanka:/var/www/drupal$** ls -l**
total 184
-rw-r--r--  1 mike     anbu     29044 2007-01-29 22:51 CHANGELOG.txt
-rw-r--r--  1 mike     anbu       262 2006-08-09 09:42 cron.php
drwxr-xr-x  2 **www-data www-data**  4096 2007-06-30 00:59 [COLOR="RoyalBlue"]files[/COLOR]
drwxr-xr-x  2 mike     anbu      4096 2007-01-30 01:20[COLOR="RoyalBlue"] includes[/COLOR]
-rw-r--r--  1 mike     anbu       872 2006-12-12 10:32 index.php
-rw-r--r--  1 mike     anbu      1431 2006-09-08 18:29 INSTALL.mysql.txt

Can I just change www-data AND www-data to my current user/group name or is there some other prefered method for doing this if many users on the same Ubuntu machine develops in LAMP+Drupal?

---

### Post by az on 2007-07-01
> **jingo811 said:**
> tnx :p

Another thing...
```
sudo mkdir /var/www/drupal/files
**sudo chown www-data:www-data** /var/www/drupal/files
```
I've seen this chown www-data:www-data somewhere else also when doing configs for some other web stuff.  But I never understood what it means and how much I can change things on that CLI command without lowering the current security settings?

Drupal admin site complained about this:


Can I just change www-data AND www-data to my current user/group name or is there some other prefered method for doing this if many users on the same Ubuntu machine develops in LAMP+Drupal?

Well, it's best to only make writable what needs to be writable.  If you are only running a test site, create the directory in your home drive, make the /files subdirectory world-writable and create a new virtual host in apache who's documentroot points to that folder in your home directory.  No need to use /var/www.

On a hosting provider, just use the ftp client to change the permissions of the /files directory.

---

### Post by jingo811 on 2007-07-01
tnx.

---

