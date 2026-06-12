---
title: "Apache doesn't recognize upgraded php version"
date: 2015-07-21
forum: Server Platforms
---

### Post by peter1897 on 2015-07-21
I manually instlled php 5.4 on Ubuntu 10.04. The old version was 5.3.2. Now if i check the php version it shows 5.4:
```
max@ubuntu:/etc/php5$ php -v
PHP 5.4.0 (cli) (built: Jul 21 2015 14:04:16)
Copyright (c) 1997-2012 The PHP Group
Zend Engine v2.4.0, Copyright (c) 1998-2012 Zend Technologies
```

But if i load index.php file in /var/www/ the apache still shows that the php version is 5.3.2. 
Also, if i check the installed packages it doesn't show the php 5.4 version. May be bacause i installed it manually, but i am not sure:

```
max@ubuntu:/etc/php5$ dpkg -l | grep php
ii  libapache2-mod-php5                  5.3.2-1ubuntu4.30                          server-side, HTML-embedded scripting language (Apache 2 modul
ii  php5                                 5.3.2-1ubuntu4.30                          server-side, HTML-embedded scripting language (metapackage)
ii  php5-cli                             5.3.2-1ubuntu4.30                          command-line interpreter for the php5 scripting language
ii  php5-common                          5.3.2-1ubuntu4.30                          Common files for packages built from the php5 source
ii  php5-curl                            5.3.2-1ubuntu4.30                          CURL module for php5
ii  php5-gd                              5.3.2-1ubuntu4.30                          GD module for php5
ii  php5-geoip                           1.0.7-1ubuntu1                             GeoIP module for php5
ii  php5-mcrypt                          5.3.2-0ubuntu1                             MCrypt module for php5
ii  php5-memcached                       1.0.0-1build1                              memcached extension module for PHP5
ii  php5-mysql                           5.3.2-1ubuntu4.30                          MySQL module for php5
ii  phpmyadmin                           4:3.3.2-1ubuntu1                           MySQL web administration tool
```

How to make apache recognize the new php 5.4 version?

---

### Post by SeijiSensei on 2015-07-21
Since 10.04 server has reached its [end-of-life]("https://wiki.ubuntu.com/Releases"), you'd be much better off upgrading to 14.04 server which has PHP 5.5.9 as its current default version.

---

### Post by peter1897 on 2015-07-21
.

---

### Post by peter1897 on 2015-07-21
I think there is something wrong. I even upgraded to Ubuntu 12.04 but it still can't upgrade php. If i run: **sudo apt-get install php5** it still installs php 5.3.2

---

