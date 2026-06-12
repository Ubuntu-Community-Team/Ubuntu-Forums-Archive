---
title: "update process (and I) can't stop mysql server"
date: 2010-03-10
forum: Server Platforms
---

### Post by davidshere on 2010-03-10
I'm running an update, and get this:

```
The following packages will be upgraded:
  apache2 apache2-doc apache2-mpm-prefork apache2-utils apache2.2-common libcupsys2 libmysqlclient15-dev linux-libc-dev mysql-server
  mysql-server-5.0 php5-imap sudo
12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/38.9MB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]?
Preconfiguring packages ...
(Reading database ... 42204 files and directories currently installed.)
Preparing to replace mysql-server 5.0.51a-3ubuntu5.4 (using .../mysql-server_5.0.51a-3ubuntu5.5_all.deb) ...
 * Stopping MySQL database server mysqld                                                                                        [fail]
invoke-rc.d: initscript mysql, action "stop" failed.
invoke-rc.d returned 1
There is a MySQL server running, but we failed in our attempts to stop it.
Stop it yourself and try again!
dpkg: error processing /var/cache/apt/archives/mysql-server_5.0.51a-3ubuntu5.5_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server_5.0.51a-3ubuntu5.5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
david@falcon:~$

```

I seem to be having the same problem as this user:

[http://ubuntuforums.org/showthread.php?t=625055](http://ubuntuforums.org/showthread.php?t=625055)

I've tried the two solutions in that thread, and they have not worked:

```
david@falcon:~$ sudo /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                                                                                        [fail]
david@falcon:~$ ps ax | grep mysql
 4181 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 4223 ?        Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 4225 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
 4563 pts/0    R+     0:00 grep mysql
david@falcon:~$ sudo kill 4181 4223 4225
david@falcon:~$ ps ax | grep mysql
 4181 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 4586 ?        Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 4588 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
 4599 pts/0    R+     0:00 grep mysql
david@falcon:~$

```

These log files are blank:

```

david@falcon:~$ tail /var/log/mysql.err
david@falcon:~$ tail /var/log/mysql.log
david@falcon:~$

```

Since it is extremely rare to run into problems during an upgrade on Ubuntu servers, I suspect this is a bug.

My machine is hardy server 8.04.4.  (It's not the one described in my signature.)

---

### Post by HubertB on 2010-03-11
The default kill signal for "kill" is SIGTERM. Maybe SIGKILL really kills him, so try "kill -9 {pids}"

---

