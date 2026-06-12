---
title: "Ubuntu 11.04 MySQL shutting down on its own"
date: 2012-04-25
forum: Server Platforms
---

### Post by og9 on 2012-04-25
About a month ago MySQL shut down at 6.33 in the morning on its own, only thing I can find in logs is a normal shutdown message.

This morning, the same thing has happened with just a normal shutdown message appearing, I had to reboot the server to get it to start again.

Has anyone come across this?  Something strange was at around the same time **logcheck** sent me and email containging the following, but there is a root password already and the test database doesn't exist.

**NOTE:** Although the logcheck message seems to indicate MySQL starting, the service was not running.


I can see a mention of apparmour just afterwards, perhaps this relates to the problem?

Any help much appreciated. :confused:

> 
Apr 25 06:54:41 entry8 mysqld[22344]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER ! Apr 25 06:54:41 entry8 mysqld[22344]: To do so, start the server, then issue the following commands: Apr 25 06:54:41 entry8 mysqld[22344]: /usr/bin/mysqladmin -u root password 'new-password' Apr 25 06:54:41 entry8 mysqld[22344]: /usr/bin/mysqladmin -u root -h entry8 password 'new-password' Apr 25 06:54:41 entry8 mysqld[22344]: Alternatively you can run: Apr 25 06:54:41 entry8 mysqld[22344]: /usr/bin/mysql_secure_installation Apr 25 06:54:41 entry8 mysqld[22344]: which will also give you the option of removing the test Apr 25 06:54:41 entry8 mysqld[22344]: databases and anonymous user created by default.  This is Apr 25 06:54:41 entry8 mysqld[22344]: strongly recommended for production servers. Apr 25 06:54:41 entry8 mysqld[22344]: See the manual for more instructions. Apr 25 06:54:41 entry8 mysqld[22344]: Please report any problems with the /usr/scripts/mysqlbug script! Apr 25 06:55:03 entry8 kernel: [1097116.769605] type=1400 audit(1335333303.653:31): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=22461 comm="apparmor_parser"
And here are the **SYSLOG** entries on both dates:

120313  6:33:51 [Note] /usr/sbin/mysqld: Normal shutdown
120313  6:33:53  InnoDB: Starting shutdown...
120313  6:33:57  InnoDB: Starting shutdown...
120313  6:34:02  InnoDB: Starting shutdown...
120313  6:34:08  InnoDB: Starting shutdown...
120313  6:34:13  InnoDB: Starting shutdown...

120425  6:54:35 [Note] /usr/sbin/mysqld: Normal shutdown
120425  6:54:37  InnoDB: Starting shutdown...
120425  6:54:41  InnoDB: Starting shutdown...
120425  6:54:47  InnoDB: Starting shutdown...
120425  6:54:52  InnoDB: Starting shutdown...
120425  6:54:58  InnoDB: Starting shutdown...

**ADDITIONAL INFO:** Forgot to mention I'm running MonIT on this  system which I think tried to restart MySQL.  On manually trying  '/etc/init.d/mysql start' I got 'permission denied' (as root) and  service mysql start said 'unrecognized service'.  Reboot start MySQL up  fine.

---

