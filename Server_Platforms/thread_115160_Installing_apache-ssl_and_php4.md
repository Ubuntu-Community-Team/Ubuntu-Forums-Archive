---
title: "Installing apache-ssl and php4"
date: 2006-01-10
forum: Server Platforms
---

### Post by geekman on 2006-01-10
Hi,
Im trying to install ssl with apache-ssl on my server. i firstly did:
sudo apt-get install apache php4
and it works fine with php, then i wanted to install ssl easily so i did
sudo apt-get install apache-ssl
and php still works without ssl but under ssl it wont work, i have searched everywhere for how to fix this, i have:
-added LoadModule php4_module /usr/lib/apache/1.3/libphp4.so  to the apache-ssl config
-added <IfModule mod_dir.c>
    DirectoryIndex index.html index.htm index.shtml index.cgi index.php index.phtml
    AddType application/x-httpd-php .php
    AddType application/x-httpd-php .phtml
</IfModule>
 to the apache-ssl config

-added LoadModule php4_module /usr/lib/apache/1.3/libphp4.so
to the apache-ssl modules conf

Please, any ideas?:confused:

---

### Post by shadowman on 2006-01-11
You didn't mention if your server brings up the default web page when you browse to [https://localhost](https://localhost).  The reason I ask is it should just work if your ssl config is set up properly to bring up the default page.

---

