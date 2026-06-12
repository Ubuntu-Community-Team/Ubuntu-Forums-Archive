---
title: "MySQL ERROR 2002 (HY000): Can't connect to local"
date: 2011-02-16
forum: Server Platforms
---

### Post by adeee on 2011-02-16
guys i try to install apache php mysql and phpmyadmin through this  article.
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)
install apache2 ------ successfully
install php --------- successfully
But when i try to install mysql and phpmyadmin then this error occure.

[ATTACH]183629[/ATTACH]

And while removing this. 

sudo apt-get purge apache2 php5 libapache2-mod-php5 mysql-server libapache2-mod-auth-mysql php5-mysql phpmyadmin

i got this error.

```
Setting up phpmyadmin (4:3.3.2-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
Replacing config file /etc/phpmyadmin/config-db.php with new version
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2).
unable to connect to mysql server.
error encountered creating user:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
dbconfig-common: phpmyadmin configure: ignoring errors from here forwards
populating database via sql...  done.
dbconfig-common: flushing administrative password

adeee@adeee:~$ 


```
 
How can i install apache mysql phpmyadmin and php fine?

Remeber while testing php run fine but phpmyadmin run not fine.

---

### Post by DegreesCelsius on 2011-02-16
Try removing all those that you have installed already.

Then go to your terminal and type
```

sudo apt-get install php5 mysql-server apache2 phpmyadmin

```

and hit enter.

---

### Post by adeee on 2011-02-17
Guys now i try to remove PHP5, apache2, and mysql

and then try again to install via this site. [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Now apache not work.
This is the installing procces 


```
Setting up apache2-mpm-prefork (2.2.14-5ubuntu8.4) ...
 * Starting web server apache2
apache2: [COLOR=Red]Syntax error on line 233 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory                                           [fail][/COLOR]
invoke-rc.d: initscript apache2, action "start" failed.

Setting up dbconfig-common (1.8.44ubuntu1) ...

Setting up wwwconfig-common (0.2.1) ...
Setting up javascript-common (7) ...

Setting up php5-common (5.3.2-1ubuntu4.7) ...
Setting up libapache2-mod-php5 (5.3.2-1ubuntu4.7) ...
Your apache2 configuration is broken, so we're not restarting it for you.

Setting up mysql-common (5.1.41-3ubuntu12.9) ...
Setting up libmysqlclient16 (5.1.41-3ubuntu12.9) ...

Setting up libnet-daemon-perl (0.43-1) ...
Setting up libplrpc-perl (0.2020-2) ...
Setting up libdbi-perl (1.609-1build1) ...
Setting up libdbd-mysql-perl (4.012-1ubuntu1) ...
Setting up libjs-mootools (1.2.4.0~debian1-1) ...
Setting up libmcrypt4 (2.5.8-3.1) ...

Setting up libt1-5 (5.1.2-3build1) ...

Setting up mysql-client-core-5.1 (5.1.41-3ubuntu12.9) ...
Setting up mysql-client-5.1 (5.1.41-3ubuntu12.9) ...
Setting up mysql-client (5.1.41-3ubuntu12.9) ...
Setting up php5-gd (5.3.2-1ubuntu4.7) ...
Setting up php5-mcrypt (5.3.2-0ubuntu1) ...
Setting up php5-mysql (5.3.2-1ubuntu4.7) ...
Setting up phpmyadmin (4:3.3.2-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf

Creating config file /etc/dbconfig-common/phpmyadmin.conf with new version

Creating config file /etc/phpmyadmin/config-db.php with new version
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2).
unable to connect to mysql server.
error encountered creating user:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
dbconfig-common: phpmyadmin configure: aborted.
dbconfig-common: flushing administrative password
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2).
unable to connect to mysql server.
error encountered creating database:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
dbconfig-common: phpmyadmin configure: aborted.
dbconfig-common: flushing administrative password
populating database via sql...  error encountered populating database:
mysql said: ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
dbconfig-common: phpmyadmin configure: aborted.
dbconfig-common: flushing administrative password
done.
dbconfig-common: flushing administrative password

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

``` and upper i mention the error in picture are occurs.
so how i install lampp server properly?
can i need to install ubuntu again?

---

### Post by adeee on 2011-02-17
reply please. :P

---

### Post by lprofil on 2011-09-12
DegreesCelsius <- you made my day. Thank you!


> **DegreesCelsius said:**
> Try removing all those that you have installed already.

Then go to your terminal and type
```

sudo apt-get install php5 mysql-server apache2 phpmyadmin

```

and hit enter.

Thanks for that. It solved my problem. I forgot to install mysql-server because i thought mysql-common would come with it. My mistake.

After installing mysql-server with 

```

sudo apt-get install mysql-server

```

i could reconfigure php-myadmin

```

dpkg-reconfigure phpmyadmin

```
 flawless.

/lprofil

---

