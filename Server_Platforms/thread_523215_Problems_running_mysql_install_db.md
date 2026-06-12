---
title: "Problems running mysql_install_db"
date: 2007-08-11
forum: Server Platforms
---

### Post by ka1ssr on 2007-08-11
I am having trouble running mysql_install_db on Fiesty.  Here's what happens when I run the command:

ka1ssr@ka1ssr-desktop:~$ sudo mysql_install_db
Password:
Installing MySQL system tables...
ERROR: 1062  Duplicate entry '%-test-' for key 1
070811 16:19:34 [ERROR] Aborting

070811 16:19:34 [Note] /usr/sbin/mysqld: Shutdown complete

Installation of system tables failed!

Examine the logs in /var/lib/mysql for more information.
You can try to start the mysqld daemon with:
/usr/sbin/mysqld --skip-grant &
and use the command line tool
/usr/bin/mysql to connect to the mysql
database and look at the grant tables:

shell> /usr/bin/mysql -u root mysql
mysql> show tables

Try 'mysqld --help' if you have problems with paths. Using --log
gives you a log in /var/lib/mysql that may be helpful.

The latest information about MySQL is available on the web at
[http://www.mysql.com](http://www.mysql.com)
Please consult the MySQL manual section: 'Problems running mysql_install_db',
and the manual section that describes problems on your OS.
Another information source is the MySQL email archive.
Please check all of the above before mailing us!
And if you do mail us, you MUST use the /usr/bin/mysqlbug script!


I'm a realative newcomer to mysql and would appreciate any help.

Bill

---

