---
title: "Php pdo extension?"
date: 2009-11-02
forum: Server Platforms
---

### Post by ubuntüser on 2009-11-02
I have a fresh install of Ubuntu Server 9.10 64bit. I chose the LAMP server (and others, but thats not important).

So I need sqlite support now. So I did sudo apt-get install sqlite.

But sqlite doesn't work with php yet. I know that pdo and pdo_sqlite modules are needed. But how to get those? If I use pecl install pdo and pecl install pdo_sqlite, and add those as pdo.so and pdo_sqlite.so to the php.ini file, it doesn't work. I get an error like this: 

```
PHP Fatal error:  PDO: driver sqlite2 requires PDO API version 20060511; this is PDO version 20060409 in Unknown on line 0

```

So I uninstalled the pecl modules, and I am stuck here. How do I get sqlite working with my php?

Edit: If I uninstall all the pdo modules (and remove their respective entries from php.ini), apache/php works fine.

---

### Post by CyberJack on 2009-11-03
did you install php5-sqlite package?

---

### Post by ubuntüser on 2009-11-03
Ok. I have done the following:

Installed LAMP server and Ubuntu server 9.10 64bit

Installed the following packages:
```

sudo apt-get install libmysqlclient15-dev
sudo apt-get install sqlite
sudo apt-get install php5-sqlite

```

Built the following from pecl:

```

sudo pecl install pdo
sudo pecl install pdo_sqlite

```

Added the following to php.ini (in /etc/php5/apache2/php.ini)

```

extension=pdo.so
extension=pdo_sqlite.so
extension=sqlite.so

```
and in that order.

The builds from pecl were OK too.

What's wrong? Any ideas?

I get the following from /var/log/apache2/error.log

```

PHP Warning:  Module 'PDO' already loaded in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613/pdo_mysql.so' - /usr/lib/php5/20060613/pdo_mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  Module 'pdo_sqlite' already loaded in Unknown on line 0
PHP Warning:  Module 'SQLite' already loaded in Unknown on line 0
PHP Fatal error:  PDO: driver sqlite2 requires PDO API version 20060511; this is PDO version 20060409 in Unknown on line 0
PHP Fatal error:  Unable to start SQLite module in Unknown on line 0

```

Is anything form LAMP conflicting?

Basically, what I want is functional Apache2, PHP, MySQL, and Sqlite support

---

### Post by Nandox7 on 2009-11-03
By the error msg.

Is the file really there: /usr/lib/php5/20060613/pdo_mysql.so ?

---

### Post by ubuntüser on 2009-11-03
Yeah, the files are all there. The pdo.so, pdo_mysql.so, and sqlite.so are all there. But it's not working.

---

### Post by ubuntüser on 2009-11-03
If I enable the extension_dir="./" in the php.ini file, then I do not get the errors on apache2 startup. It seems to function fine. BUT THERE IS NO SQLITE SUPPORT!? When I try to use pdo, I get

```

Fatal error: Class 'PDOStatement' not found in /var/www/wtorrent/lib/cls/PDOe.cls.php on line 13
```

---

### Post by ubuntüser on 2009-11-04
In the process of removing/installing all these things, my LAMP got messed up. PHPMyAdmin said that mysqli extension was missing. It had worked before. So I thought I messed something up in the proess of all this. So what I did:

```
sudo apt-get --purge remove apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql

sudo tasksel install lamp-server

sudo apt-get install phpmyadmin
```

And now, I'm not using rtorrent/wtorrent anymore. Im using torrentflux-b4rt. It was too hard getting mysqli to work with apache2.

---

### Post by volekvolek on 2009-11-09
I have the same problem. After upgrading to Ubuntu 9.10 from 9.04.  I start seeing this error message.   

```
php -v 
PHP Fatal error:  PDO: driver sqlite requires PDO API version 20060511; this is PDO version 20060409 in Unknown on line 0
PHP Fatal error:  Unable to start pdo_sqlite module in Unknown on line 0

```

I have the :
 pecl list
Installed packages, channel pecl.php.net:
=========================================
Package   Version State
PDO       1.0.3   stable
PDO_MYSQL 1.0.2   stable
xdebug    2.0.5   stable



I have the usual php packages also installed (mysql, dev, etc ) 

Regards

---

### Post by thebitguru on 2009-12-19
I am also seeing the same issue, has anyone figured this out yet?  I am also running 9.10.

---

### Post by CashCostello on 2010-03-13
uninstall php5-sqlite and use the sqlite from pecl

---

### Post by gansvv on 2010-05-09
Thanks @CashCostello. Removing php5-sqlite did it for me. Apache is back online!

---

