---
title: "[HOWTO] Fix MySQL after upgrade with different datadir"
date: 2011-10-15
forum: Server Platforms
---

### Post by mwjones on 2011-10-15
During the upgrade to 11.10, an option was presented to remove the custom /etc/mysql/my.cnf and replace it with the distro.  The changes looked insignificant and I had a custom location in there for my datadir.  After the upgrade, MySQL would not start.

All searches for the error log entry **Can't start server : Bind on unix socket: Permission denied** yielded results about setting permissions; but permissions had already been set correctly via chown at the time of install.

In the end, the solution was to merge the two apparmor files.  New version of **/etc/apparmor.d/usr.sbin.mysqld:**
>   /{,var/}run/mysqld/mysqld.pid w,
  /{,var/}run/mysqld/mysqld.sock w,
...
  /RAMPAGE/mysql/ r,
  /RAMPAGE/mysql/** rwk,

For search engine indexing, here is what other stuff looked like. 

**/var/log/mysql/error.log:**
>  InnoDB: Starting shutdown...
 InnoDB: Shutdown completed; log sequence number 0 7547009
[Note] /usr/sbin/mysqld: Shutdown complete

[Note] Plugin 'FEDERATED' is disabled.
 InnoDB: Initializing buffer pool, size = 8.0M
 InnoDB: Completed initialization of buffer pool
 InnoDB: Started; log sequence number 0 7547009
[ERROR] Can't start server : Bind on unix socket: Permission denied
[ERROR] Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
[ERROR] Aborting

**/var/run/mysqld/:** 
```
$ sudo ls -Al /var/run/mysqld/ 
total 0
```

**/etc/mysql/my.cnf:**
> [client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]
user            = mysql
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
# datadir               = /var/lib/mysql
datadir         = /RAMPAGE/mysql
tmpdir          = /tmp
skip-external-locking

bind-address            = 127.0.0.1

---

### Post by venkatesh20 on 2011-10-19
Can you please give the commands that I can use to fix the issue. My mysql stopped working after upgrade to 11.10 due to the same issue mentioned here. Thanks

---

### Post by bradleyayers on 2012-02-01
Thanks for this! Worked perfectly. However I only needed the /{,var/}run... lines -- I didn't need to change the data directory permissions.

---

