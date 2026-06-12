---
title: "MySQL will not shut down"
date: 2010-04-11
forum: Server Platforms
---

### Post by kpm on 2010-04-11
A while back I set up two vps Ubuntu v8.10 servers, one to hosts web sites, the other for backup. I used this How To about mysql replication ([http://www.howtoforge.com/mysql_database_replication](http://www.howtoforge.com/mysql_database_replication)) and the AutoMySQLBackup script for backing up the web server.

I recently upgraded the web server from 8.10 to 9.04 then finally to the current 9.10 release. All went well with the exception of it taking me a while to find out I had to comment out "skip-bdb" on my.cnf to get MySQL up and running again.

However, I am now attempting to do the same (step through the upgrade to 9.10)  with the backup vps but MySQL refuses to shut down. The results and error I get in the term after issuing an 'apt-get upgrade' command is:
```
root@backup:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common dhcp3-client dhcp3-common
  libapache2-mod-php5 libcups2 libcupsimage2 libexpat1 libkrb53 libpng12-0 libpq5 libssl0.9.8
  libthai-data libthai0 mysql-server mysql-server-5.0 openssl php5 php5-cli php5-common php5-curl php5-gd
  php5-mysql python2.5 python2.5-minimal sudo tzdata
29 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/43.9MB of archives.
After this operation, 53.2kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 18393 files and directories currently installed.)
Preparing to replace mysql-server 5.0.67-0ubuntu6 (using .../mysql-server_5.0.67-0ubuntu6.1_all.deb) ...
 * Stopping MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "stop" failed.
invoke-rc.d returned 1
There is a MySQL server running, but we failed in our attempts to stop it.
Stop it yourself and try again!
dpkg: error processing /var/cache/apt/archives/mysql-server_5.0.67-0ubuntu6.1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server_5.0.67-0ubuntu6.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Can anyone point me in the proper direction?
Thanks

---

### Post by Ryan Dwyer on 2010-04-11
What happens when you try to stop it yourself?

Eg.
sudo /etc/init.d/mysql stop

---

### Post by kpm on 2010-04-11
I get the same error.

---

### Post by Ryan Dwyer on 2010-04-11
cat /var/log/syslog | grep mysql

---

### Post by kpm on 2010-04-14
interesting... i am getting zero mysql log entries in syslog.  Same for /var/log/mysql.log or mysql.err

If I run /etc/init.d/mysql status i get the following error:

/etc/init.d/mysql status
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
 * 

if I log into mysql and run the status command, the status is returned, which is;

mysql> status
--------------
mysql  Ver 14.12 Distrib 5.0.67, for debian-linux-gnu (i486) using readline 5.2

Connection id:		1067
Current database:	
Current user:		root@localhost
SSL:			Not in use
Current pager:		stdout
Using outfile:		''
Using delimiter:	;
Server version:		5.0.67-0ubuntu6 (Ubuntu)
Protocol version:	10
Connection:		Localhost via UNIX socket
Server characterset:	latin1
Db     characterset:	latin1
Client characterset:	latin1
Conn.  characterset:	latin1
UNIX socket:		/var/run/mysqld/mysqld.sock
Uptime:			65 days 11 hours 34 min 29 sec

Threads: 1  Questions: 2017240  Slow queries: 0  Opens: 347556  Flush tables: 1  Open tables: 64  Queries per second avg: 0.357
--------------

---

### Post by s_ø on 2010-04-14
You have probably lost the debian-sys-maint user. This is the user your system uses to start/stop mysql. The password for debian-sys-maint is in /etc/mysql/debian.cnf

---

### Post by s_ø on 2010-04-14
That was kind of a headless post by me.
You should log into mysql as root and verify that the user debian-sys-maint exists, and have privileges to administrate the database. The default is all privileges for debian-sys-maint@localhost.
If you need to recreat the user, you can give it the password from the debian.cnf file.

---

### Post by kpm on 2010-04-15
Thanks for all the help!
I do however have the debian-sys-maint, and it appears it has the shutdown and kill process privileges.

mysql> SELECT user, Shutdown_priv, Process_priv FROM user WHERE user LIKE "debian-sys-maint";
+------------------+---------------+--------------+
| user             | Shutdown_priv | Process_priv |
+------------------+---------------+--------------+
| debian-sys-maint | Y             | Y            | 
+------------------+---------------+--------------+

I also noticed though, that the slave user for the replication did not have the shutdown or process kill privileges, so I granted 'slave' those privileges and tried again... Still same error.

---

### Post by s_ø on 2010-04-15
Take a look at **/etc/mysql/debian.cnf** there should be a line with the password.
Check if the password matches the one in the mysql db.
```
 mysql> SELECT user FROM user WHERE password = PASSWORD('your-password');
```

---

### Post by kpm on 2010-04-16
it is the proper password...

mysql> SELECT user FROM user WHERE password = PASSWORD('********');
+------------------+
| user             |
+------------------+
| debian-sys-maint | 
+------------------+
1 row in set (0.00 sec)

---

### Post by kpm on 2010-04-17
I ended up resolving this by:
ps -A | grep mysql

noted the pid numbers for each process and the:
kill #####

And I had to kill-9  a mysqld process that wouldn't stop with the kill command.

Anyway, after that, I was able to continue on and complete the upgrade.

Thanks for all the help.

Cheers

---

