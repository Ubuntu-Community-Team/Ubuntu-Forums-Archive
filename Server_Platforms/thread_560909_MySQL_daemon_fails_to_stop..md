---
title: "MySQL daemon fails to stop."
date: 2007-09-26
forum: Server Platforms
---

### Post by TheDom on 2007-09-26
I'm running a small webserver, the basis of which is a Ubuntu (feisty) LAMP install.

Every few days the MySQL daemon fails to stop, but I can't work out why.
There is a (very) simple script being run as a cron job, which executes every day at 1am. For the most part this works fine, but one in five times seems to fail to stop mysql(d).

Script contents:

#!/bin/bash
#Stop everything.
 /etc/init.d/apache2 stop
 /etc/init.d/mysql stop
#Backup.
 rsync -arv --delete /etc /home /var /backup
#Start daemons.
 /etc/init.d/mysql start
 /etc/init.d/apache2 start

I've checked the syslog from one of the occasions where msql has [failed], which says:

[1514]: 070914  1:00:02 [Note] /usr/sbin/mysqld: Normal shutdown
[1514]: 070914  1:00:02  InnoDB: Starting shutdown...
[1514]: 070914  1:00:05InnoDB: Assertion failure in thread 2967804816 in file os0sync.c line 319
[1514]: InnoDB: Failing assertion: 0 == pthread_cond_destroy(&(event->cond_var))

Of course the first thing I did when I noticed this had happened was to check my databases for corruption, so tried "mysqladmin -u -p shutdown", then killall mysql and mysql_safe.
All the databases checked out, with no errors or corrupted tables.

The problem happens about twice a week, the rest of the time mysql(d) stopping properly. It is not on a specific day, nor does there seem to be a pattern.

I don't know where to go from here. Does anyone have any suggestions? :)

---

### Post by TheDom on 2007-09-27
No ideas? :)

I am more than happy to provide more information or logs if it would help, I just don't know what else might be relevant.
Just let me know what.

---

