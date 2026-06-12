---
title: "php / pear"
date: 2012-12-28
forum: Server Platforms
---

### Post by ELMIT on 2012-12-28
I moved a php program to a new server and see in the apache2 error log file:

> PHP Fatal error:  Unknown: Failed opening required '/var/www/bc.elmit.com/rss.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0


I uncomment "include_path=.:/usr/share/php" line in /etc/php5/apache2/php.ini configuration file

Now the error goes to: 
> PHP Fatal error:  Unknown: Failed opening required '/var/www/bc.elmit.com/rss.php' (include_path='.:/usr/share/php') in Unknown on line 0


What do I miss?

---

### Post by pqwoerituytrueiwoq on 2012-12-28
probably needs this command run
```
sudo apt-get install php-pear
```

---

### Post by ELMIT on 2012-12-28
sudo apt-get install php-pear
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php-pear is already the newest version.


Seems not the case.

---

### Post by pqwoerituytrueiwoq on 2012-12-28
i believe php is in /usr/bin not /usr/share try changing that in the config file and restart apache2

---

### Post by ELMIT on 2012-12-28
I think there is another problem. Look at the complete log file, not just the last lines:

> [Fri Dec 28 22:20:03 2012] [error] [client 111.248.240.40] PHP Warning:  Unknown: failed to open stream: Permission denied in Unknown on line 0
[Fri Dec 28 22:20:03 2012] [error] [client 111.248.240.40] PHP Fatal error:  Unknown: Failed opening required '/var/www/bc.elmit.com/rss.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
[Fri Dec 28 22:49:08 2012] [error] [client 111.248.240.40] PHP Warning:  Unknown: failed to open stream: Permission denied in Unknown on line 0
[Fri Dec 28 22:49:08 2012] [error] [client 111.248.240.40] PHP Fatal error:  Unknown: Failed opening required '/var/www/bc.elmit.com/rss.php' (include_path='.:/usr/share/php') in Unknown on line 0
[Sat Dec 29 04:26:36 2012] [error] [client 114.36.107.217] PHP Warning:  Unknown: failed to open stream: Permission denied in Unknown on line 0
[Sat Dec 29 04:26:36 2012] [error] [client 114.36.107.217] PHP Fatal error:  Unknown: Failed opening required '/var/www/bc.elmit.com/rss.php' (include_path='./usr/bin/') in Unknown on line 0


I think it should not be /usr/bin since that points to the executive program php, but to the library /usr/share/

The line before said Permission denied.

> ls -la /usr/share/php/
total 144
drwxr-xr-x  12 root root  4096 Oct 15 06:00 .
drwxr-xr-x 117 root root  4096 Nov 12 18:41 ..
drwxr-xr-x   2 root root  4096 Oct 11 09:21 Archive
drwxr-xr-x   3 root root  4096 Oct 11 09:21 .channels
drwxr-xr-x   2 root root  4096 Oct 11 09:21 Console
drwxr-xr-x   3 root root  4096 Oct 11 09:21 data
-rw-r--r--   1 root root  2437 Oct 11 09:22 .depdb
-rw-r--r--   1 root root     0 Oct 11 09:22 .depdblock
lrwxrwxrwx   1 root root    20 Sep 12 21:06 doc -> ../doc/php-pear/PEAR
-rw-r--r--   1 root root  8670 Oct 11 09:22 .filemap
drwxr-xr-x   3 root root  4096 Oct 15 06:00 libphp-phpmailer
-rw-r--r--   1 root root     0 Oct 11 09:22 .lock
drwxr-xr-x   2 root root  4096 Oct 11 09:21 OS
drwxr-xr-x  11 root root  4096 Oct 11 09:21 PEAR
-rw-r--r--   1 root root  1087 Sep 12 21:04 PEAR5.php
-rw-r--r--   1 root root 14428 Sep 12 21:04 pearcmd.php
-rw-r--r--   1 root root 33897 Sep 12 21:04 PEAR.php
-rw-r--r--   1 root root   926 Sep 12 21:04 peclcmd.php
drwxr-xr-x   3 root root  4096 Oct 11 09:22 .registry
drwxr-xr-x   3 root root  4096 Oct 11 09:21 Structures
-rw-r--r--   1 root root 20243 Sep 12 21:04 System.php
drwxr-xr-x   2 root root  4096 Oct 11 09:21 XML


---

### Post by pqwoerituytrueiwoq on 2012-12-28
are all the permissions set right in /var/www/bc.elmit.com/
for example can www-data write/read files where it needs to?

---

### Post by sandyd on 2012-12-28
**Moved to Server Platforms**
> **ELMIT said:**
> I think there is another problem. Look at the complete log file, not just the last lines:



I think it should not be /usr/bin since that points to the executive program php, but to the library /usr/share/

The line before said Permission denied.

Have you followed the verification instructions at [http://pear.php.net/manual/en/installation.checking.php](http://pear.php.net/manual/en/installation.checking.php) ?

---

### Post by ELMIT on 2012-12-28
thanks!

Indeed I forgot to use chown -R www-data:www-data on that web site !!!

---

