---
title: "MySQL will not start"
date: 2010-05-04
forum: Server Platforms
---

### Post by stevo81989 on 2010-05-04
I dont know. I have had tons of issues with the linux today. Now when I try and start mysql it just fails. the syslog says:


May 3 16:19:40 tp-inventory /etc/init.d/mysql[7783]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
May 3 16:19:40 tp-inventory /etc/init.d/mysql[7783]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
May 3 16:19:40 tp-inventory /etc/init.d/mysql[7783]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
May 3 16:19:40 tp-inventory /etc/init.d/mysql[7783]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
May 3 16:19:40 tp-inventory /etc/init.d/mysql[7783]:
May 3 16:19:50 tp-inventory kernel: [ 1295.530016] parport0: FIFO is stuck
May 3 16:19:50 tp-inventory kernel: [ 1295.570018] parport0: BUSY timeout (1) in compat_write_block_pio

I have already tried to create and modify the /var/run/mysql folder. Doesnt work. When I type mysqld I get:


100503 16:21:01 InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.


The command mysql results in:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I have even tried to uninstall mysql and reinstall it an nothing works. Any suggestions?

---

### Post by richardjh on 2010-05-04
This is a permissions problem on the directory that stores the data.

Check in /etc/mysql/my.cnf to see where your data directory is. If you  haven't changed it, it should be 

```
datadir        = /var/lib/mysql
```

Then check the permissions are correct on this directory, they should  look like this

```
drwx------ 3 mysql mysql 4096 2010-05-04 14:43 /var/lib/mysql
```

Then check there are no MySQL processes running using

```
ps -ef | grep mysqld
```

If there are then kill those processes.

Then try to start mysqld properly using 

```
sudo service mysql start
```

Post back if problems persist.

---

### Post by stevo81989 on 2010-05-04
No such luck. I think it maybe time to throw in the towel. I have tried about everything I can think of and there is no fix on the internet yet. now it is:


mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.3) ...
 * Stopping MySQL database server mysqld                                                                                                             [ OK ]
 * Reloading AppArmor profiles ...                                                                                                                   [ OK ]
 * Starting MySQL database server mysqld                                                                                                             [ OK ]
/etc/init.d/mysql: line 115: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.
^Cdpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script killed by signal (Interrupt)
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by stevo81989 on 2010-05-04
Looks like I got it to work I just had to create the file. Thanks!

---

### Post by Qu4rk on 2011-03-21
> **stevo81989 said:**
> Looks like I got it to work I just had to create the file. Thanks!

I'm having the same issue.  What file did you create?

---

### Post by grokenberger on 2012-12-21
……yeah! What file??!

---

### Post by howefield on 2012-12-21
Old thread closed.

---

