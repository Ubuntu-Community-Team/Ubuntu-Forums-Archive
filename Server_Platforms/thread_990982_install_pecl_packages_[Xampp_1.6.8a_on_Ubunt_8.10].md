---
title: "install pecl packages [Xampp 1.6.8a on Ubunt 8.10]"
date: 2008-11-23
forum: Server Platforms
---

### Post by dgoosens on 2008-11-23
hi,

I was wondering if somebody can tell me how I can install pecl packages when using Xampp.

when running:
```
sudo /opt/lampp/bin/pecl install channel://pecl.php.net/docblock-0.2.0
```

I get the following error message:
```
downloading docblock-0.2.0.tgz ...
Starting to download docblock-0.2.0.tgz (28,197 bytes)
.........done: 28,197 bytes
9 source files, building
running: phpize
grep: /opt/lampp/include/php/main/php.h: No such file or directory
grep: /opt/lampp/include/php/Zend/zend_modules.h: No such file or directory
grep: /opt/lampp/include/php/Zend/zend_extensions.h: No such file or directory
Configuring for:
PHP Api Version:
Zend Module Api No:
Zend Extension Api No:
Cannot find autoconf. Please check your autoconf installation and the $PHP_AUTOCONF
environment variable is set correctly and then rerun this script.

ERROR: `phpize' failed
```

does anybody have a clue ?

thanks a lot...
dGo

---

### Post by dgoosens on 2008-11-27
no one ?

---

### Post by joeradtke on 2010-01-07
I have run up against the same problem trying to use pear, pecl phpunit etc with xampp.

The problem is that with xampp everything is in /opt/lampp and the commands are in /opt/lampp/bin.

PHP based programs such as php, pear, pecl, phpunit, etc must reside in the /opt/lampp/lib/php/ directory.  You have to make sure that you don't have the regular ubuntu php installed or the ubuntu pear as they will be in a different directory and when you use the command line the default path will be /usr/bin.  You need to remove these packages.  It can be done with the synaptic package manager or from the command line.

You then need to link your commands to /usr/bin eg.:

ln -s /opt/lampp/bin/php /usr/bin/php

I have been beating my head against the wall trying to use phpunit for months with it unable to find any files, claiming mysql.pdo wasn't installed etc when it was all a duplicate system (the original ubuntu php system) that I didn't realize I had.  The xampp php will run just fine with a server program but when you try to run something from the command line you will get the ubuntu resident program which has a different path.

---

