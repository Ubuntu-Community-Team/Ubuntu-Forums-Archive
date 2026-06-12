---
title: "Can't connect to local MySQL server through socket '/tmp/mysql.sock'"
date: 2006-12-04
forum: Server Platforms
---

### Post by DeepThoughts on 2006-12-04
Apparently my MySQL-server is taking drugs.

In the conf-files I've found (/etc/mysql/debian.cnf & /etc/mysql/my.cnf) the port is defined as "/var/run/mysqld/mysqld.sock" and when I do 'ps aux | grep mysqld' I get this:
```
root     13970  0.0  0.2   3692  1460 pts/0    S    18:38   0:00 /bin/sh /usr/bin/mysqld_safe
mysql    14108  1.0  3.8 126896 19700 pts/0    Sl   18:38   0:05 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root     14109  0.0  0.1   2648   724 pts/0    S    18:38   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
stefan   14424 14.0  0.1   2888   820 pts/0    S+   18:47   0:00 grep mysqld
```
And the "--socket=/var/run/mysqld/mysqld.sock" suggests that the conf-files are correct. But...

When I try to connect using 'mysql' I get this:
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)
```

Why, oh why is it looking in the /tmp-folder??? What triggered this behavior and more importantly how do I fix this? It seriously irritating to have a test-server which can't be used for it's purpose.

This is all happening on an Dapper Drake install.

---

### Post by daniminas on 2006-12-04
You can try to locate where mysqld.sock is:
> whereis mysqld.sock

and then edit /etc/mysql/my.cnf and write the new path.

:-k

---

### Post by DeepThoughts on 2006-12-04
> **daniminas said:**
> You can try to locate where mysqld.sock is:
> whereis mysqld.sock

and then edit /etc/mysql/my.cnf and write the new path.

:-k

If it was that easy...

There is a mysqld.sock at /var/run/mysqld/mysqld.sock which is the path configured in both debian.cnf and my.cnf but for some reason it looks in /tmp anyway.

To make things worse (at least I presume) when running 'whereis mysqld.sock' it only returns this:
```
mysqld: /usr/sbin/mysqld /usr/share/man/man8/mysqld.8.gz
```

How big should a *.sock file be? Nautilus reports it as 0 bytes...

---

### Post by craigmp on 2006-12-04
I used to have problems running mysql on centos and the first 2 things I've always done were do run mysql_install_db and to change the owner and group on /var/db/mysql

chown -R mysql msyql
chgrp -R mysql mysql

just a thought...

---

### Post by DeepThoughts on 2006-12-04
> **craigmp said:**
> I used to have problems running mysql on centos and the first 2 things I've always done were do run mysql_install_db and to change the owner and group on /var/db/mysql

chown -R mysql msyql
chgrp -R mysql mysql

just a thought...

Unless something drastic changed I doubt that it is the problem. Because I've had everything up and running. This started (or stopped depending on how you see it) sometime during the last week. I'm inclined to believe an update of MySQL is to blame but I have no idea if that really is the case.

---

### Post by mcclimont on 2006-12-06
I'm also having this same problem.

The version of mysql client/server i have installed is 5.0.21-3ubuntu1.

I've found that although the server runs correctly, the clients do not.

With further exploration, i found that the settings used by the server (using the --print-defaults flag) are correct, but the mysql client does not have any of these defaults.

# mysqld --print-defaults
mysqld would have been started with the following arguments:
--user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306 --basedir=/usr --datadir=/var/lib/mysql --tmpdir=/tmp --language=/usr/share/mysql/english --skip-external-locking --old_passwords=1 --bind-address=127.0.0.1 --key_buffer=16M --max_allowed_packet=16M --thread_stack=128K --query_cache_limit=1048576 --query_cache_size=16777216 --query_cache_type=1 --log-bin=/var/log/mysql/mysql-bin.log --expire-logs-days=20 --max_binlog_size=104857600 --skip-bdb --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306 --basedir=/usr --datadir=/var/lib/mysql --tmpdir=/tmp --language=/usr/share/mysql/english --skip-external-locking --old_passwords=1 --bind-address=127.0.0.1 --key_buffer=16M --max_allowed_packet=16M --thread_stack=128K --query_cache_limit=1048576 --query_cache_size=16777216 --query_cache_type=1 --log-bin=/var/log/mysql/mysql-bin.log --expire-logs-days=20 --max_binlog_size=104857600 --skip-bdb


# mysql --print-defaults
mysql would have been started with the following arguments:
*(none)*


So, i start the server again, getting the failed output on mysqlcheck which is run on startup.

# /etc/init.d/mysql start
Starting MySQL database server: mysqld.
# /usr/bin/mysqlcheck: Got error: 2002: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2) when trying to connect


As expected, the mysql client fails to start too.

# mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)


Until i specify the socket to use!

# mysql --socket=/var/run/mysqld/mysqld.sock
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 6 to server version: 5.0.21-Debian_3ubuntu1-log

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>


Now this should prove that mysqld is running fine, but that the defaults mysql and other clients need to connect to mysqld just are not there (as shown with --print-defaults)


My configuration file is still the default, and the client section does have the correct path to mysqld.sock file.


This raises the questions:
   * Why are the defaults not there for the clients?
   * Is this in error with this build of mysql client?
   * How do i fix this?


Anyone have any thoughts?

---

### Post by kdiebold on 2007-07-31
On Dapper (at least on my install), the problem is that the clients (mysql and mysqladmin) were looking for /etc/my.cnf instead of /etc/mysql/my.cnf. Seems like a compile-time bug in the package.

Easiest fix is:
sudo ln -s /etc/mysql/my.cnf /etc/my.cnf

---

