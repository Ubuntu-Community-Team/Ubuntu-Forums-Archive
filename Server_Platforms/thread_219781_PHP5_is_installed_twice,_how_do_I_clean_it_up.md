---
title: "PHP5 is installed twice, how do I clean it up?"
date: 2006-07-20
forum: Server Platforms
---

### Post by vayu on 2006-07-20
Way back in Hoary I installed PHP5.0 from non ubuntu sources.  After upgrading to Dapper I notice that I now have two versions of PHP (PHP5 and PHP5.0)  The original one (PHP5.0) seems to be the one that responds to changes in PHP.ini.

How do I get rid of the non ubuntu version without borking my setup?

```
~$ dpkg -l \*php\* | grep ii
ii  libapache2-mod-php5   5.1.2-1ubuntu3   server-side, HTML-embedded scripting languag
ii  libapache2-mod-php5.0 5.0.5-0.6~hoary1 HTML-embedded scripting language (apache 2.0
ii  php-pear              5.1.2-1ubuntu3   PEAR - PHP Extension and Application Reposit
ii  php5-cli              5.1.2-1ubuntu3   command-line interpreter for the php5 script
ii  php5-common           5.1.2-1ubuntu3   Common files for packages built from the php
ii  php5-curl             5.1.2-1ubuntu3   CURL module for php5
ii  php5-gd               5.1.2-1ubuntu3   GD module for php5
ii  php5-mcrypt           5.1.2-1          MCrypt module for php5
ii  php5.0                5.0.5-0.6~hoary1 server-side, HTML-embedded scripting languag
ii  php5.0-common         5.0.5-0.6~hoary1 common files for packages built from the php
ii  php5.0-mysql          5.0.5-0.6~hoary1 MySQL module for PHP 5.0
ii  phpmyadmin            2.8.0.3-1        set of PHP-scripts to administrate MySQL ove
```

---

