---
title: "How to install php-xdebug 2.0.5 on Ubuntu 8.10 Server?"
date: 2009-11-11
forum: Server Platforms
---

### Post by Titanium on 2009-11-11
Hi,

I'm using Ubuntu 8.10 server. I'm trying to install PHPUnit by using pear. Running the following:
```
$ sudo pear install phpunit/PHPUnit
```
Results in:
```
Did not download optional dependencies: pear/Image_GraphViz, pear/Log, use --alldeps to download automatically
phpunit/PHPUnit can optionally use package "pear/Image_GraphViz" (version >= 1.2.1)
phpunit/PHPUnit can optionally use package "pear/Log"
phpunit/PHPUnit can optionally use PHP extension "pdo_sqlite"
phpunit/PHPUnit **requires PHP extension "xdebug" (version >= 2.0.5), installed version is 2.0.3**
No valid packages found
install failed
```

There doesn't seem to be a newer version of xdebug in the repositories. How can I install the latest xdebug, so I can use PHPUnit?

Thank you.

---

### Post by t3r0 on 2009-11-11
Remove the xdebug you installed from repos, install php dev packages, run: pecl install xdebug, create new file /etc/php5/conf.d/xdebug.custom.ini with content: zend_extension="/path/to/new/compiled/xdebug.so", restart apache. 

Sorry I dont have time to explain more right now, but google for more information if needed and check xdebug documentation for more info :) 

- Tero

---

### Post by Titanium on 2009-11-12
Thank you! That was all I needed.

---

### Post by Titanium on 2009-11-12
I had to remove the xdebug.custom.ini file because executing PHP applications through the command line resulted in the following warning:
```
PHP Warning: Module 'xdebug' already loaded in Unknown on line 0
```

/etc/php5/conf.d/xdebug.ini already contains:
```
zend_extension=/usr/lib/php5/20060613+lfs/xdebug.so
```

---

