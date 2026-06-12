---
title: "MySQL up and died"
date: 2006-09-11
forum: Server Platforms
---

### Post by Dragonmantank on 2006-09-11
I ran an 'apt-get update' and 'apt-get upgrade' on my webserver about an hour ago, and the update and such seemed to go just fine. Now though, MySQL has apparently died. Apache2 and PHP do not see it at all, and I cannot get it to start via '/etc/init.d/mysql start'. When I try to get it to start, I get this:

```
Starting MySQL database server: mysqld.
.
.
.
.
.
.
.
.
.
.
.
.
.
...failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

I tried removing mysql-server and reinstalling it, but I get the same thing. I even removed everything mysql (at least I think I did) with 'apt-get --purge remove mysql*', which ended up only selecting about 5 things after mysql-server was removed.

Any ideas? I've tried restarting just Apache2 and even the entire box to no avail.

---

### Post by bhartsock on 2006-09-13
Same exact problem.

Syslog output:
```
Sep 13 18:00:17 localhost mysqld_safe[11261]: started
Sep 13 18:00:17 localhost mysqld[11266]: 060913 18:00:17 [Warning] Can't create test file /var/lib/mysql/mythtv-box.lower-test
Sep 13 18:00:17 localhost mysqld[11266]: 060913 18:00:17 [Warning] One can only use the --user switch if running as root
Sep 13 18:00:17 localhost mysqld[11266]:
Sep 13 18:00:17 localhost mysqld[11266]: 060913 18:00:17  InnoDB: Operating system error number 13 in a file operation.
Sep 13 18:00:17 localhost mysqld[11266]: InnoDB: The error means mysqld does not have the access rights to
Sep 13 18:00:17 localhost mysqld[11266]: InnoDB: the directory.
Sep 13 18:00:17 localhost mysqld[11266]: InnoDB: File name ./ibdata1
Sep 13 18:00:17 localhost mysqld[11266]: InnoDB: File operation call: 'open'.
Sep 13 18:00:17 localhost mysqld[11266]: InnoDB: Cannot continue operation.
Sep 13 18:00:17 localhost mysqld_safe[11270]: ended
Sep 13 18:00:31 localhost /etc/init.d/mysql[11417]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Sep 13 18:00:31 localhost /etc/init.d/mysql[11417]: Could not open required defaults file: /etc/mysql/debian.cnf
Sep 13 18:00:31 localhost /etc/init.d/mysql[11417]: Fatal error in defaults handling. Program aborted
Sep 13 18:00:31 localhost /etc/init.d/mysql[11417]:

```

---

### Post by bhartsock on 2006-09-13
My bad, restart fixed it for some odd reason.  Everything is dandy over here.

---

### Post by Dragonmantank on 2006-09-14
All is well here now too, but I ended up having to rebuild the machine. At least it was just the LAMP install.

---

