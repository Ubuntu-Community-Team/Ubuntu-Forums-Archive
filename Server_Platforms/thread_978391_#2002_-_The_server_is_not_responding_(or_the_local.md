---
title: "#2002 - The server is not responding (or the local MySQL server's socket is not corre"
date: 2008-11-11
forum: Server Platforms
---

### Post by ubunken on 2008-11-11
Hi all I am new to Linux, and am now configuring a LAMP system. However i am facing an error when trying to log on to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) page.

However i managed to enter the page via [http://locahost/phpadmin](http://locahost/phpadmin)
I have no idea as to why I was able to do that. Is there are way to help me with it because when i tried accessing [http://localhost/phpmyadmin](http://localhost/phpmyadmin) i had this error : " 404 error Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch Server at localhost Port 80 "

The following was displayed after logging on to mysql and running ps aux | grep mysql

/# ps ax | grep mysql
 7942 pts/0    S      0:00 /bin/sh /usr/bin/mysqld_safe
 7981 pts/0    Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 7983 pts/0    S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
 8152 pts/0    S+     0:00 grep mysql

Hope someone can help me with it

---

### Post by Philio on 2008-11-11
Are you able to access the mysql server from the command line with something like:

mysql -u user -p

If so you might want to check the php.ini mysql settings and the phpMyAdmin config file.

Sometimes php.ini defaults to using /tmp/mysql.sock I'm not sure if this is the case with Ubuntu though. It may be the case that phpMyAdmin defaults to /tmp/mysql.sock as well as it's usually the standard location for it.

---

