---
title: "Problems with mysql connection in AWS instance"
date: 2009-04-14
forum: Server Platforms
---

### Post by akdeiva on 2009-04-14
Hi,

We are using ami-71fd1a18. And we have the mysql 5.0.57 version installed in this instance.

We have some cron jobs which connect to the DB and install DB and related tables which we do from the shell script. We are facing issues while running this cron and it throws the below error:


root@ip-xx-xxx-xxx-xxx:~# /usr/bin/php /var/code/installer/install_db_automation.php
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

We checked the cnf file and based on the path we setup the file and folder permissions for them.

Here is the permission details:

root@ip-xx-xxx-xxx-xxx:~# ls -al /var/run/mysqld
total 4
drwxrwxrwx 2 mysql root   80 2009-04-13 11:49 .
drwxr-xr-x 9 root  root  360 2009-04-13 07:04 ..
-rw-rw---- 1 mysql mysql   6 2009-04-13 11:49 mysqld.pid
srwxrwxrwx 1 mysql mysql   0 2009-04-13 11:49 mysqld.sock

Here is the values in the my.cnf file:


[client]
port            = 3306
#socket         = /var/lib/mysql/mysql.sock
socket          = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]
#
# * Basic Settings
#


#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306

After going thru the google, and suggestions we came across there is no real solution available and we couldn't proceed further on this.

While the same DB is connected thru the application its working fine, and not throwing the error, only when the cron job is run it throws the error. In the cron job we directly use the mysql commands and i am pasting the sample here for the same as well:

mysql -p$rootpass --execute="$cmduser";
mysqladmin -p$rootpass create $dbname;
mysql -p$rootpass --execute="$cmdgrant";
mysql -p$rootpass --execute="$granttoroot";
mysql -p$rootpass $dbname < /var/code/dbrepo/db.sql;
mysql -p$rootpass $dbname < /var/code/dbrepo/sps/sp1.sql;
mysql -p$rootpass $dbname < /var/code/dbrepo/sps/sp2.sql;
mysql -p$rootpass $dbname < /var/code/dbrepo/sps/sp3.sql;
mysql -p$rootpass $dbname < /var/code/dbrepo/sps/sp4.sql;
mysql -p$rootpass $dbname < /var/code/dbrepo/sps/sp5.sql;
mysql -p$rootpass $dbname < /var/code/dbrepo/sps/sp6.sql;
mysql -p$rootpass $dbname < /var/code/dbrepo/sps/sp7.sql;
mysql -p$rootpass $dbname < /var/code/dbrepo/sps/sp8.sql;
mysql -p$rootpass $dbname < /var/code/dbrepo/sps/sp9.sql;
mysql -p$rootpass $dbname < /var/code/dbrepo/sps/sp11.sql;
mysql -p$rootpass $dbname < /var/code/dbrepo/sps/sp13.sql;

We are attaching the EBS volume as mentioned [http://developer.amazonwebservices.com/connect/entry.jspa?externalID=1663](http://developer.amazonwebservices.com/connect/entry.jspa?externalID=1663).

We followed the approach of using the symbolic links for the path so that the cnf file need not to be touched.

Any help / direction / guidelines will be appreciated.

Thanks.

---

### Post by ikonia on 2009-04-15
ok - looking at your output, check the basics first

1.) it's complaining about the socket file not being usable, it's there so that's not the problem, and it's permissions are fine.

2.) is mysql running. ps -ef | grep mysql

3.) if you look at the error there is a line in there
mysqladmin: connect to server at 'localhost' failed

so mysqladmin can't connect to "localhost"

try to connect yourself

mysql -u root -h localhost -p 

then look at the php to see exactly what mysqladmin command is being used then try that command yourself.

I suspect either the mysql server is not running, or the permissions for the user wanting to connect in the application is a problem (db permissions, not file)

---

