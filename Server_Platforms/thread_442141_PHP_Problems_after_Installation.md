---
title: "PHP Problems after Installation"
date: 2007-05-13
forum: Server Platforms
---

### Post by Josh1 on 2007-05-13
Hey Everyone,

I have just installed Apache2,MySQL,PHP5 on my laptop as a test (because I am a webdesigner and need this), but when I try to run php scripts I just get the code right back!

For example:
```
<?php phpinfo(); ?>
```

Shows as:

```
<?php phpinfo(); ?>
```

(Yes, the file is a php file..)

I've tried:
```
sudo a2enmod php5
sudo /etc/init.d/apache2 force-reload
```

But still nothing..

---

### Post by iiibill on 2007-05-13
It looks like the apache configuration is missing a statement of the form:

  AddType application/x-httpd-php .php

In ubuntu-land the way that this statement gets included in the apache configuration is by creating symbolic links between files in the /etc/apache2/mods-available and /etc/apache2/mods-enabled directories.  On my system that is using php4 I have the following links:

   /etc/apache2/mods-enabled/php4.conf -> /etc/apache2/mods-available/php4.conf
   /etc/apache2/mods-enabled/php4.load -> /etc/apache2/mods-available/php4.load

I would guess you need to issue the commands:

  sudo ln -s /etc/apache2/mods-available/php5.conf /etc/apache2/mods-enabled/php5.conf
  sudo in -s /etc/apache2/mods-available/php5.load /etc/apache2/mods-enabled/php5.load

and then restart apache.

Bill

---

### Post by mohnkern on 2007-05-14
I'm seeing a similar error, when I open up the "home page" firefox wants me to download it, rather than displaying the page . It says it wants to open a file which is: application/x-httpd-php and then offers a save or download.

I check /etc/apache/httpd.conf and it has entries for php in it.


httpd.conf:    DirectoryIndex index.html index.htm index.shtml index.cgi index.php
httpd.conf:    # distribution - see [http://www.php.net](http://www.php.net)) will typically use:
httpd.conf:    #AddType application/x-httpd-php3 .php3
httpd.conf:    #AddType application/x-httpd-php3-source .phps
httpd.conf:AddType application/x-httpd-php .php    
httpd.conf:    #AddType application/x-httpd-php .php
httpd.conf:    #AddType application/x-httpd-php-source .phps
mime.types:application/x-httpd-php                              phtml pht php
mime.types:application/x-httpd-php-source                       phps
mime.types:application/x-httpd-php3                     php3
mime.types:application/x-httpd-php3-preprocessed                php3p
mime.types:application/x-httpd-php4                     php4
mohnkern@Scott:/etc/apache$

---

### Post by az on 2007-05-14
Do you have the libapache2-mod-php5 package installed?

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

