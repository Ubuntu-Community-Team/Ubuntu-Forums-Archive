---
title: "Fatal Error: Allowed memory size...."
date: 2011-11-27
forum: Server Platforms
---

### Post by shpoonman on 2011-11-27
I have been reading quite a bit about this on the forums so far and have tried a few different fixes to no avail. I am setting up a dev environment on a local machine for Magento. This site is currently in production, so I know the application works. My machine is a i5 with 8GB ram running Natty with a fresh LAMP install. 

The error is: Fatal error: Allowed memory size of 536870912 bytes exhausted (tried to allocate 523800 bytes) in /var/www/app/code/core/Mage/Core/Model/Config.php on line 639 

I have set the memory_limit  512M in /var/www/.htaccess, /etc/php5/apache2/php.ini and /etc/php5/cli.php.ini. I have also put ini_set("memory_limit”,"512M"); in my index.php. Also php -i and php --help both work. 

It does not matter what the actual memory_limit is set to, the error just changes the Allowed memory size to the max.

Any help would be greatly appreciated. I am racking my brain on this one.

---

### Post by artjomtro on 2011-11-27
Use nginx like back-end it will help you
in this case:
1)apache will only work with php
2)nginx will send images videos etc...
don't forget gzip and earcelerator!
realy i use it and don't know problems.
if you want i can write manual! (but if it realy needed for you just google)

---

