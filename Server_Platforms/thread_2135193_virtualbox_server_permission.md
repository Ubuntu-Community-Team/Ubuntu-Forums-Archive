---
title: "virtualbox server permission"
date: 2013-04-13
forum: Server Platforms
---

### Post by mijonuha on 2013-04-13
Hi
i have a virtual machine. host=ubuntu, guest=ubuntu
i do not run apache on my laptop. but it is running in my virtual machine.
i  want to keep my php files on my host instead of my virtual guest. so i  kept them in my ext4 home drive and shared it with my virtual machine.

this is the last line of my fstab:
```
[SIZE=3]www /var/www vboxsf rw,uid=1000,gid=1000,auto,exec 0 0[/SIZE]
```

first, my phpmyadmin gave me a blank page. so i used mysql workbench and solved.
then, when i was installing drupal i faced another error on:
192.168.1.101/drupal/install.php?profile=standard&locale=en
drupal gave me this error:
> [SIZE=3]the directory sites/default/files does not exist[/SIZE]
after creating this folder, drupal said that this file is not writable.

[CENTER]
[IMG]http://oi46.tinypic.com/fd8tp1.jpg[/IMG]
[/CENTER]

i have googled that. on forums, most of people are ok with giving 777 permission while i'm not!!!
i dont want to set up a site that can be hacked. i have experience of being hacked a lot!!!

on virtual machine terminal i typed:
```
[SIZE=3]root@avepc:/var/www/drupal# ll[/SIZE]
```
> total 264
drwxr-xr-x 1 aven aven  4096 Apr 13 20:11 ./
drwxrwxr-x 1 aven aven  4096 Apr 13 17:26 ../
-rw-r--r-- 1 aven aven  6604 Apr  4 01:59 authorize.php
-rw-r--r-- 1 aven aven 79216 Apr  4 01:59 CHANGELOG.txt
-rw-r--r-- 1 aven aven  1481 Apr  4 01:59 COPYRIGHT.txt
-rw-r--r-- 1 aven aven   720 Apr  4 01:59 cron.php
-rw-r--r-- 1 aven aven   174 Apr  4 01:59 .gitignore
-rw-r--r-- 1 aven aven  5603 Apr  4 01:59 .htaccess
drwxr-xr-x 1 aven aven  4096 Apr  4 01:59 includes/
-rw-r--r-- 1 aven aven   529 Apr  4 01:59 index.php
-rw-r--r-- 1 aven aven  1451 Apr  4 01:59 INSTALL.mysql.txt
-rw-r--r-- 1 aven aven  1874 Apr  4 01:59 INSTALL.pgsql.txt
-rw-r--r-- 1 aven aven   703 Apr  4 01:59 install.php
-rw-r--r-- 1 aven aven  1298 Apr  4 01:59 INSTALL.sqlite.txt
-rw-r--r-- 1 aven aven 17861 Apr  4 01:59 INSTALL.txt
-rw-rw-r-- 1 aven aven 18092 Sep 18  2011 LICENSE.txt
-rw-r--r-- 1 aven aven  8191 Apr  4 01:59 MAINTAINERS.txt
drwxr-xr-x 1 aven aven  4096 Apr  4 01:59 misc/
drwxr-xr-x 1 aven aven  4096 Apr  4 01:59 modules/
drwxr-xr-x 1 aven aven  4096 Apr  4 01:59 profiles/
-rw-r--r-- 1 aven aven  5376 Apr  4 01:59 README.txt
-rw-r--r-- 1 aven aven  1561 Apr  4 01:59 robots.txt
drwxr-xr-x 1 aven aven  4096 Apr  4 01:59 scripts/
drwxr-xr-x 1 aven aven  4096 Apr  4 01:59 sites/
drwxr-xr-x 1 aven aven  4096 Apr  4 01:59 themes/
-rw-r--r-- 1 aven aven 19941 Apr  4 01:59 update.php
-rw-r--r-- 1 aven aven  9642 Apr  4 01:59 UPGRADE.txt
-rw-r--r-- 1 aven aven  2051 Apr  4 01:59 web.config
-rw-r--r-- 1 aven aven   417 Apr  4 01:59 xmlrpc.php

if virtual machine has write permission, what's wrong with apache??
thanks a lot

---

### Post by mijonuha on 2013-04-13
solved by changing last line of /etc/fstab to:
```
[SIZE=3]www /var/www vboxsf umask=0022,gid=33,uid=33[/SIZE]
```

i dont know how to flag this thread as solved!?

---

