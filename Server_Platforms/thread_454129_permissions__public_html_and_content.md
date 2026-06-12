---
title: "permissions / public_html and content"
date: 2007-05-25
forum: Server Platforms
---

### Post by cywhale on 2007-05-25
Hello.
I'm doing some research about installing and configuring a LAMP-server with ubuntu feisty. One question remaining is how do I have to set up the permissions for a _local_ wordpress installation (for webdeveloping and testing purposes only)?

My current permission setup:

public_html: drwxr-xr-x 6 cywhale cywhale 4096 2007-05-24 13:32 public_html
index.php: -rw-rw-rw- 1 cywhale cywhale 94 2007-05-24 13:38 index.php
.htacess: -rwxrwxrwx 1 cywhale cywhale 223 2007-05-24 13:39 .htaccess
wp.config: -rw-rw-rw- 1 cywhale cywhale 845 2007-05-24 13:38 wp-config.php
directory wp-content: drwxr-xr-x 6 cywhale cywhale 4096 2007-05-24 13:38 wp-content

wp-content content: 
-rw-rw-rw- 1 cywhale cywhale 32 2007-05-24 13:38 index.php
drwxr-xr-x 8 cywhale cywhale 4096 2007-05-24 13:38 myfotos
drwxr-xr-x 22 cywhale cywhale 4096 2007-05-24 13:38 plugins
drwxr-xr-x 10 cywhale cywhale 4096 2007-05-24 13:38 themes

Everything including .htacess is working fine but I don't know if the permissions shoult be altered for security.

---

### Post by turinglabs on 2007-05-25
Even though this is just a local install, there is no reason to have world-writeable files anywhere in your wordpress installation (two exceptions - your backup directory and themes may need to be writeable by the www-data user to enable web-based backups and theme editing from the wordpress control panel). So .htaccess should have permissions of 664, along with index.php. Here is one way to get rid of world-writeable permissions on a directory tree. Run these from your public_html direfctory:

find . -type f | xargs chmod 664
find . -type d | xargs chmod 775

Since your user owns the files, you will still be able to edit them. In production, they should be owned by user and group 'root' (with the exception of a backup directory and themes, if needed, which should be owned by user www-data).

Doug

---

