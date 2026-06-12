---
title: "Phpmyadmin won't import database"
date: 2013-04-28
forum: Server Platforms
---

### Post by Cvetan on 2013-04-28
I can't import database with phpmyadmin control panel. 
php.ini settings are ok it's not upload limit, since the database sql file is very small(less than 1 MB).

The database can be imported in console with mysql commands but on phpmyadmin control panel can't. 

Any suggestions?

---

### Post by Cvetan on 2013-05-03
I looked in apache error log and it says file upload error:
```
[Sun Apr 28 21:48:19 2013] [notice] Graceful restart requested, doing restart
[Sun Apr 28 21:48:19 2013] [notice] Apache/2.2.22 (Ubuntu)  PHP/5.3.10-1ubuntu3.6 with Suhosin-Patch configured -- resuming normal  operations
[Sun Apr 28 21:48:22 2013] [notice] caught SIGTERM, shutting down
[Sun Apr 28 21:48:23 2013] [notice] Apache/2.2.22 (Ubuntu)  PHP/5.3.10-1ubuntu3.6 with Suhosin-Patch configured -- resuming normal  operations
[Sun Apr 28 21:49:00 2013] [error] [client 127.0.0.1] PHP  Warning:  Unknown: open_basedir restriction in effect. File(/tmp) is not  within the allowed path(s):  (/usr/share/phpmyadmin/:/etc/phpmyadmin/:/var/lib/phpmyadmin/:/usr/share/php/php-gettext)  in Unknown on line 0, referer:  http://localhost/phpmyadmin/db_import.php?db=jp-kultura-i-sport&server=1&token=8cf6a22befb5076d00bfb6a4365f0c13
[Sun Apr 28 21:49:00 2013] [error] [client 127.0.0.1] PHP Warning:  File  upload error - unable to create a temporary file in Unknown on line 0,  referer:  http://localhost/phpmyadmin/db_import.php?db=jp-kultura-i-sport&server=1&token=8cf6a22befb5076d00bfb6a4365f0c13
[Sun Apr 28 21:52:27 2013] [notice] caught SIGTERM, shutting down
[Mon Apr 29 00:52:02 2013] [notice] Apache/2.2.22 (Ubuntu)  PHP/5.3.10-1ubuntu3.6 with Suhosin-Patch configured -- resuming normal  operations
[Mon Apr 29 01:15:26 2013] [notice] caught SIGTERM, shutting down
[Mon Apr 29 12:55:17 2013] [notice] Apache/2.2.22 (Ubuntu)  PHP/5.3.10-1ubuntu3.6 with Suhosin-Patch configured -- resuming normal  operations


```
And i don't know how to solve this. Owner of www directory is my user account, and i don't know why it can not upload file. 

```
ps -ef | grep apache
```

```
root      1201     1  0 20:26 ?        00:00:00 /usr/sbin/apache2 -k start
cvetan    1216  1201  0 20:26 ?        00:00:00 /usr/sbin/apache2 -k start
cvetan    1217  1201  0 20:26 ?        00:00:00 /usr/sbin/apache2 -k start
cvetan    1218  1201  0 20:26 ?        00:00:00 /usr/sbin/apache2 -k start
cvetan    1221  1201  0 20:26 ?        00:00:00 /usr/sbin/apache2 -k start
cvetan    1222  1201  0 20:26 ?        00:00:00 /usr/sbin/apache2 -k start
cvetan    2556  2498  0 20:30 pts/0    00:00:00 grep --color=auto apache
```

---

### Post by cariboo on 2013-05-03
One of your problems is the owner of /var/www, and the user that runs apache. /var/www should be owned by root, and apache should be run by www-data. here is a listing of the command that you ran on my system:

```
cariboo@willy:~$ ps -ef | grep apache
root      1557     1  0 Mar28 ?        00:00:45 /usr/sbin/apache2 -k start
www-data  2000  1557  0 Apr30 ?        00:00:01 /usr/sbin/apache2 -k start
www-data  2304  1557  0 Apr30 ?        00:00:01 /usr/sbin/apache2 -k start
www-data  4350  1557  0 May01 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  4366  1557  0 May01 ?        00:00:00 /usr/sbin/apache2 -k start
cariboo  16101 15996  0 11:45 pts/0    00:00:00 grep --color=auto apache
www-data 29338  1557  0 Apr28 ?        00:00:02 /usr/sbin/apache2 -k start
www-data 29339  1557  0 Apr28 ?        00:00:02 /usr/sbin/apache2 -k start
www-data 29340  1557  0 Apr28 ?        00:00:03 /usr/sbin/apache2 -k start
www-data 30211  1557  0 Apr28 ?        00:00:01 /usr/sbin/apache2 -k start
www-data 30218  1557  0 Apr28 ?        00:00:02 /usr/sbin/apache2 -k start
www-data 30471  1557  0 Apr28 ?        00:00:02 /usr/sbin/apache2 -k start
```

---

