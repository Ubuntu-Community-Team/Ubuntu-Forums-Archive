---
title: "PHP include functions no longer work after enabling a2enmod"
date: 2011-09-30
forum: Server Platforms
---

### Post by nowashburn on 2011-09-30
I have a dedicated server running 11.04 and did the following steps:

1. installed lampserver, phpmyadmin, and webmin by following these simple instructions:
[http://gregrickaby.com/2011/05/how-to-install-lamp-on-ubuntu-1104-natty.html](http://gregrickaby.com/2011/05/how-to-install-lamp-on-ubuntu-1104-natty.html)

Simple, quick setup and everything works great. Awesome. I then upload my application (CakePHP 2.0)

2. I then needed mod rewrite, so by doing some searching, I came across these instructions:
[http://ubuntu-for-humans.blogspot.com/2009/11/enable-mode-rewrite-on-apache-ubuntu.html](http://ubuntu-for-humans.blogspot.com/2009/11/enable-mode-rewrite-on-apache-ubuntu.html)

I now go to my application and again, everything looks great and mod rewrite is working. But... I then realize that any PHP include or require function is no longer working as they did before enabling mod rewrite. I immediately thought that maybe there was a setting within the application that was causing this to not work. So, to test I made 2 simple files completely outside of the app and with no .htaccess files to test a simple include function. What do you know, it still does not work!

A real head scratcher here that is driving my nuts. Anyone have any suggestions? Thanks!

---

### Post by SeijiSensei on 2011-09-30
Start by reviewing /var/log/apache2/error.log.

---

### Post by nowashburn on 2011-09-30
> **SeijiSensei said:**
> Start by reviewing /var/log/apache2/error.log.

here is the error in the error log:
PHP Warning:  include(): Failed opening '1' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/index.php on line 10

the index.php file has the following code for testing:

[PHP]<?php

error_reporting(E_ALL);
ini_set('display_errors', '1');

?>
index.php
<?php

	include("index2.php") or die();

?>[/PHP]

index2.php does exist and even doing a file_exists returns true.

---

### Post by SeijiSensei on 2011-09-30
You don't give the complete path to index2.php in the include().  PHP will search for includes by default in the list of directories mentioned in include_path, which was shown in the error message.

```
include_path='.:/usr/share/php:/usr/share/pear'
```

Just make sure you use full paths in the include() statements, and everything will work fine.

I put all my custom includes in a separate directory like /var/www/include, then declare this at the beginning of the script like this:

```
<?
$incdir="/var/www/include/";     # note the trailing slash

[...]

include($incdir."somefile.inc");

?>
```

---

