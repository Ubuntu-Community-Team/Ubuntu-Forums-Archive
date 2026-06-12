---
title: "Apache not running PHP"
date: 2009-03-27
forum: Server Platforms
---

### Post by FuriousSam on 2009-03-27
I am running Apache2 on Ubuntu 8.10 (Intrepid). I install Apache2, PHP, MySQL, and phpmyadmin successfully. Typing in "localhost" returns a successful page. "localhost/testphp.php" also returns a successful page filled with php5 info. I made a user directory labeled public_html in my /home/user/ directory in such a fashion that "localhost/~user" displays the index.html page successfully.

**However,**when I attempt to open a .php file (that I put in /home/user/public_html), it requests to download the file.

My /etc/apache2/httpd.conf file

```
<Directory "/home/sam/public_html">
        Options FollowSymLinks
        AllowOverride All

        Order allow,deny
        Allow from all
</Directory>

DirectoryIndex index.html index.htm default.htm

ServerName localhost
```

My .htaccess file

```
# Use PHP5 as default
AddHandler application/x-httpd-php5 .php
addtype application/x-httpd-php .html .php .htm
```

NOTE: .php files run perfectly if I put them in /var/www/ and open them in Firefox via localhost/phpfile.php

I've tried a bunch of addtype application solutions but nothing seems to work. It always asks if I want to download the php file instead of actually executing them. I'm also extremely new to Ubuntu and Apache in general, so if I left out any vital info, please ask me for it.

Thanks, 
Sam

---

### Post by ktrnka on 2009-03-27
Same thing happened to me because I forgot to restart apache.

```
sudo /etc/init.d/apache2 restart
```

---

### Post by FuriousSam on 2009-03-27
I have restarted Apache multiple times without error to no avail. PHP still refuses to work properly.

---

### Post by neilevan814 on 2009-03-28
I have php scripts running on my server under the same directory you have set up /home/user/public_html but I have things done slightly differently.  My httpd.conf is empty and I have that configuration script set up in /etc/apache2/sites-enabled/mysite

I also did not set up any .htaccess script to allow for php to be interpreted in the browser and all is well

check my site if you'd like [http://webwork.thruhere.net/sales_system/sales.php](http://webwork.thruhere.net/sales_system/sales.php)

hope that helps...

I followed this how to to get set up:
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

