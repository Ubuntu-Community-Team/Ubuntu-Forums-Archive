---
title: "phpMyAdmin - install error # 2002 (socket/port ?? )"
date: 2018-06-04
forum: Server Platforms
---

### Post by oygle on 2018-06-04
I installed PhpMyAdmin and the log for the installation looks fine, until the last part

```

Creating config file /etc/phpmyadmin/config-db.php with new version
mysql: [Warning] mysql: Empty value for 'port' specified. Will throw an error in future versions
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2).
unable to connect to mysql server.
error encountered creating user:
mysql: [Warning] mysql: Empty value for 'port' specified. Will throw an error in future versions ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
dbconfig-common: phpmyadmin configure: ignoring errors from here forwards
populating database via sql...  done.
dbconfig-common: flushing administrative password
apache2_invoke: Enable configuration phpmyadmin
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for systemd (229-4ubuntu21.2) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for ufw (0.35-0ubuntu2) ...
Processing triggers for libapache2-mod-php7.0 (7.0.30-0ubuntu0.16.04.1) ...

```

Then when I tried running PhpMyAdmin the following (similar) error occured

```

#2002 - No such file or directory<br />The server is not responding (or the local server's socket is not correctly configured).

and

Connection for controluser as defined in your configuration failed.
```

Have done some searching and the post at [https://stackoverflow.com/questions/1676688/php-mysql-connection-not-working-2002-no-such-file-or-directory](https://stackoverflow.com/questions/1676688/php-mysql-connection-not-working-2002-no-such-file-or-directory) has some tips. Also in the thread at [https://stackoverflow.com/questions/11657829/error-2002-hy000-cant-connect-to-local-mysql-server-through-socket-var-run](https://stackoverflow.com/questions/11657829/error-2002-hy000-cant-connect-to-local-mysql-server-through-socket-var-run) , it mentions to check if mysql-server is installed. Under synaptic I see

mysql-server-core-5.7  is installed
mysql-server  is **NOT** installed
mysql-server-5.7 is **NOT** installed

There are so many suggestions in those 2 threads. Is this just a port/socket error ? MySQL doesn't seem to be running, and I can't start it either ? Some commands I tried ..

```

$ cat /var/run/mysqld/mysqld.sock
cat: /var/run/mysqld/mysqld.sock: No such file or directory

$ pgrep mysql

$ sudo service mysql restart
Failed to restart mysql.service: Unit mysql.service not found.

$ sudo service mysql start
Failed to start mysql.service: Unit mysql.service not found.
```

The port value here is empty. Not sure what value it should be..

```

$ sudo cat /etc/phpmyadmin/config-db.php
<?php
##
## database access settings in php format
## automatically generated from /etc/dbconfig-common/phpmyadmin.conf
## by /usr/sbin/dbconfig-generate-include
##
## by default this file is managed via ucf, so you shouldn't have to
## worry about manual changes being silently discarded.  *however*,
## you'll probably also want to edit the configuration file mentioned
## above too.
##
$dbuser='*****************';
$dbpass='**************';
$basepath='';
$dbname='phpmyadmin';
$dbserver='localhost';
$dbport='';
$dbtype='mysql';

```

---

### Post by oygle on 2018-06-04
Looking through the dependencies of PhpMyAdmin, it seems that it needs mysql-server package. So I installed that and then

```
sudo dpkg-reconfigure phpmyadmin
```

and at least now I can login to PhpMyadmin. There are a few databases there, but I don't see the one called 'phpmyadmin' ? When I attempt to browse a msg ..

```
 Connection for controluser as defined in your configuration failed.
```

---

### Post by LHammonds on 2018-06-04
phpMyAdmin is used to provide a web interface on a MySQL/MariaDB server.

Sounds like you did not have a database server to start with.  So why are you trying to install phpMyAdmin?

Also, when you install MySQL/MariaDB, you should run the following command to tighten up security:

```
mysql_secure_installation
```

I do not suggest running phpMyAdmin on a production server since that creates additional attack surfaces (Apache web server and the php application itself) and also reduces performance of the database.

LHammonds

---

### Post by oygle on 2018-06-04
> **LHammonds said:**
> Sounds like you did not have a database server to start with.  So why are you trying to install phpMyAdmin?

Two reasons. (i) I wanted to see what MySQL databases were currently being used, and (ii) I had extracted some SQL code in preparation to load a new database. I would have thought that phpMyAdmin would have installed mysql-server as a dependancy, but that is not the case. When I installed mysql-server, I was able to login using phpMyAdmin and at least see the current databases.

> **LHammonds said:**
> 
Also, when you install MySQL/MariaDB, you should run the following command to tighten up security:

```
mysql_secure_installation
```

Okay thanks, I have run that.

> **LHammonds said:**
> 
I do not suggest running phpMyAdmin on a production server since that creates additional attack surfaces (Apache web server and the php application itself) and also reduces performance of the database.

No worries. This is local only. Thanks for your help.  :)

---

