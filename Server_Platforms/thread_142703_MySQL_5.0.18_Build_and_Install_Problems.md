---
title: "MySQL 5.0.18 Build and Install Problems"
date: 2006-03-11
forum: Server Platforms
---

### Post by anson on 2006-03-11
I tried to build MySQL 5.0.18 on the Ubuntu 5.10 box following the steps in [wiki]("https://wiki.ubuntu.com/MYSQL5FromSource") and I encountered errors in "make", "make install", and "mysql-test-run" respectively:

**_ERRORS DURING MAKE:_**
[INDENT]nroff -mm user.r > user.t
troff: fatal error: can't find macro file m
make[2]: [user.t] Error 1 (ignored)
groff -mm user.r > user.ps
troff: fatal error: can't find macro file m
make[2]: [user.ps] Error 1 (ignored)
make[2]: Leaving directory `/home/admin/build/mysql-5.0.18/dbug'[/INDENT]

**_ERRORS DURING MAKE INSTALL:_**
[INDENT]/usr/bin/install -c -m 644 ./t/*.disabled /usr/local/mysql/mysql-test/t
/usr/bin/install: cannot stat `./t/*.disabled': No such file or directory
make[4]: [install-data-local] Error 1 (ignored)[/INDENT]

**_FAILURE DURING MYSQL-TEST-RUN:_**
[INDENT]rpl_rotate_logs [ fail ]

Errors are (from /usr/local/mysql/mysql-test/var/log/mysqltest-time) :
mysqltest: At line 28: query 'start slave' failed with wrong errno 1201 instead of 1105...
(the last lines may be the most important ones)

Ending Tests
Shutting-down MySQL daemon

Master shutdown finished
Slave shutdown finished[/INDENT]

Are these ignorable or are they critical??  Will they be related??  What would have caused these problems??  Any hints and help for resolving the problems is appreciated, thanks.

Anson

---

