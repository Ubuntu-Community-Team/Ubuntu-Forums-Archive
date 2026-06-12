---
title: "[SOLVED] PHP require_once not found error"
date: 2008-07-26
forum: Server Platforms
---

### Post by wgbuntu on 2008-07-26
I have checked every where and have not found an answer to this problem in my php script:

<?php require_once "/Services/Weather/Metar.php"; ?>

loading the web page:

Fatal error: require_once() [function.require]: Failed opening required '/Services/Weather/Metar.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/irry/irry.php on line 24

locate finds it here:

$ locate Metar.php
/usr/share/php/Services/Weather/Metar.php


Changing permissions didn't fix things.  What am I missing, Thanks

---

### Post by cariboo on 2008-07-26
Have you got php-pear installed? It is in the repositories.

Jim

---

### Post by wgbuntu on 2008-07-26
Synaptic package manager says its installed, but I don't know what directories/modules to locate to verify it's there.

---

### Post by cariboo on 2008-07-27
In synaptic, highlight the package in question and then select properties, either by clicking the properties butoon or by right clicking the package and selecting properties. Click the installed files tab, and you will get a list of installed files, this will tell you where the files are installed.

Jim

---

### Post by ad_267 on 2008-07-27
Try changing 
```
<?php require_once "/Services/Weather/Metar.php"; ?>
```
to
```
<?php require_once "Services/Weather/Metar.php"; ?>
```
i.e. without the first "/"

---

### Post by wgbuntu on 2008-07-27
That helped, I must have missed that this is a different message for missing DB.php.  I have all the php-pear modules installed, I have DB for perl, but not php.  Installing php-db and removing the first '/' fixed my errors.  Thanks.



> **ad_267 said:**
> Try changing 
```
<?php require_once "/Services/Weather/Metar.php"; ?>
```
to
```
<?php require_once "Services/Weather/Metar.php"; ?>
```
i.e. without the first "/"

---

