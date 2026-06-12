---
title: "Collabtive doesn't run (HTTP 500)"
date: 2017-04-10
forum: Server Platforms
---

### Post by m-dw on 2017-04-10
I'm trying to install Collabtive on Ubuntu server 16.04 LTS from the standard repository. I have a working Apache2 installation with PHP7.  When trying to access [http://server/colabtive/install.php](http://server/colabtive/install.php) I'm getting a 500 error. The only error logged in Apache's error.log is:

```

PHP Fatal error:  Uncaught Error: Class 'HTMLPurifier_Bootstrap' not found in /usr/share/php/HTMLPurifier.autoload.php:11\nStack trace:\n#0 /usr/share/collabtive/www/init.php(31): require()\n#1 /usr/share/collabtive/www/admin.php(3): require('/usr/share/coll...')\n#2 {main}\n  thrown in /usr/share/php/HTMLPurifier.autoload.php on line 11

```

I don't get an error when trying to access install.php. Am I missing something?

---

