---
title: "phpMyAdmin 500 Internal Server Error when I put AuthConf in HTTPD"
date: 2013-03-20
forum: Server Platforms
---

### Post by Maurices5000 on 2013-03-20
This has been resolved thanks!

This is a new installation. I used sudo apt-get install libapache2-mod-auth-mysql phpmyadmin 

If i put the following code in my httpd config file I get a 500 Internal Server Error.  Any idea why I"m getting this error?

This is httpd.conf
<Directory /usr/share/phpmyadmin>
Options FollowSymLinks
DirectoryIndex index.php
# AllowOverride AuthConfig
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /usr/share/password/.htpasswd
Require valid-user
</Directory>

---

