---
title: "domain.com shows a directory listing"
date: 2018-09-26
forum: Server Platforms
---

### Post by mitaskeksis on 2018-09-26
I've installed Ubuntu 18.04 on a VPS to serve Humhub for a community. The problem is that domain.com shows a directory listing with directory humhub/ and domain.com/humhub shows the login page.

I'd like to see the login page directly on domain.com. Also, I can access humhub/protected/ from my browser which is not good...

Here are roughly the steps I've taken so far:

Install
 apache2
 mysql-server
 php

Configure
 run mysql_secure_installation
 test php (phpinfo)
 set up apache virtual hosts
 set up Let's Encrypt
 install and enable php extensions
 install humhub and set correct permissions

/etc/apache2/sites-enabled/domain.com.conf:

```
<VirtualHost *:80>
    ServerAdmin asd@asd.com
    ServerName domain.com
    ServerAlias www.domain.com
    DocumentRoot /var/www/domain.com/html/humhub
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
RewriteEngine on
RewriteCond %{SERVER_NAME} =domain.com [OR]
RewriteCond %{SERVER_NAME} =www.domain.com
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>
```

```
root@ubuntu /var/www/domain.com/html/humhub # ll
total 56
drwxr-xr-x  8     1002     1002 4096 Sep 26 21:58 ./
drwxr-xr-x  3 root     root     4096 Sep 26 20:41 ../
-rwxr-xr-x  1     1002     1002 1721 Sep 25 11:55 .htaccess*
-rwxr-xr-x  1     1002     1002  312 Sep 25 11:55 .php_cs.dist*
drwxr-xr-x  2     1002     1002 4096 Sep 25 11:55 .travis/
-rwxr-xr-x  1     1002     1002 1900 Sep 25 11:55 CONTRIBUTING.md*
-rwxr-xr-x  1     1002     1002  690 Sep 25 11:55 README.md*
drwxr-xr-x 15 www-data www-data 4096 Sep 26 21:54 assets/
-rwxr-xr-x  1     1002     1002  880 Sep 26 21:12 index.php*
drwxr-xr-x  7     1002     1002 4096 Sep 25 11:55 protected/
-rwxr-xr-x  1     1002     1002   23 Sep 25 11:55 robots.txt*
drwxr-xr-x  8     1002     1002 4096 Sep 25 11:55 static/
drwxr-xr-x  3     1002     1002 4096 Sep 25 11:55 themes/
drwxr-xr-x  5 www-data www-data 4096 Sep 26 21:05 uploads/

```

If I enable pretty urls for Humhub I can't access it at all.

This must be something very simple I overlooked. Any input is appreciated, thanks in advance!

---

