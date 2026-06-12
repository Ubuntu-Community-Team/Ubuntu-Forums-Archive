---
title: "pdo_dblib.so fails to load in php5 5.3.2-1ubuntu4.5"
date: 2010-11-25
forum: Server Platforms
---

### Post by aaronjb on 2010-11-25
Afternoon everyone..

Before I go ahead and create a bug report (since I can't find an existing one about this), I thought I'd check here and see if anyone else has seen this..

On a fresh install of 10.04.1 LTS server edition with the LAMP environment and php5-sybase for database support, I get the following error when Apache starts up:

```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/pdo_dblib.so' - /usr/lib/php5/20090626+lfs/pdo_dblib.so: undefined symbol: php_pdo_register_driver in Unknown on line 0
```


This appears to be due to the order in which the files in /etc/php5/conf.d are loaded and parsed; pdo.ini needs to be loaded before any libraries which depend on it, however pdo_dblib.ini gets loaded first and you get the warning above.

Renaming 'pdo.ini' to '0_pdo.ini' causes it to be loaded first, and the error goes away, e.g.:
```
root@chrsupdev01:~# cd /etc/php5/conf.d/
root@chrsupdev01:/etc/php5/conf.d# ls
0_pdo.ini  gd.ini    mssql.ini   mysql.ini      pdo_mysql.ini   sqlite3.ini
curl.ini   ldap.ini  mysqli.ini  pdo_dblib.ini  pdo_sqlite.ini  sqlite.ini
```


Anyone else spotted this, or does it sound like I went wrong somewhere else? :)

Cheers,
Aaron

---

### Post by wongo888 on 2010-11-25
You might try:

```
$ sudo apt-get check php5-sybase
```

I've seen a similar error due to a php version mismatch. I'm assuming that your have the "php command line interpreter" *php5-cli* package installed.

BTW, I'm running an updated 10.04 server 32-bit version with the sybase module and no errors. I included an md5 hash of the lib in case you want to check.

```
$ php -v
PHP 5.3.2-1ubuntu4.5 with Suhosin-Patch (cli) (built: Sep 17 2010 13:41:55) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies

$ php -i | grep PDO
PDO
PDO support => enabled
PDO drivers => dblib, mysql
PDO Driver for FreeTDS/Sybase DB-lib => enabled
PDO Driver for MySQL => enabled

$ uname -a
Linux example.com 2.6.32-22-generic-pae #33-Ubuntu SMP Wed Apr 28 14:57:29 UTC 2010 i686 GNU/Linux

$ ls -l /etc/php5/conf.d/
total 24
-rw-r--r-- 1 root root 57 2010-09-17 13:53 mssql.ini
-rw-r--r-- 1 root root 57 2010-04-09 08:35 mysqli.ini
-rw-r--r-- 1 root root 56 2010-04-09 08:35 mysql.ini
-rw-r--r-- 1 root root 61 2010-09-17 13:53 pdo_dblib.ini
-rw-r--r-- 1 root root 52 2010-04-09 08:35 pdo.ini
-rw-r--r-- 1 root root 60 2010-04-09 08:35 pdo_mysql.ini

$ openssl md5 /usr/lib/php5/20090626+lfs/pdo_dblib.so 
MD5(/usr/lib/php5/20090626+lfs/pdo_dblib.so)= 3521797787661d486aacef238a2c4eb1
```

---

### Post by aaronjb on 2010-11-26
Thanks for that :)

Oddly enough no version mismatches etc showed up, and inspecting my system showed the same data as yours aside from a slightly different kernel.

After rebuilding the server, though, the error has gone away - which is especially odd since I have a preseed file and post-install script so multiple servers can be built identically, making it a non-user-interactive process.

How strange.. I must have done *something* between the initial install on that server and the problem happening, but I've no idea what - I only installed it a couple of days ago :)

Oh well - fixed now, thanks!

---

