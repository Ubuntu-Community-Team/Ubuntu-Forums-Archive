---
title: "MySQL init/etc scripts"
date: 2008-07-24
forum: Server Platforms
---

### Post by Xiol on 2008-07-24
Hello,

I had massive trouble configuring MySQL after importing a dump from elsewhere. The debian-sys-maint account stopped working, and I couldn't login as root anymore, nor would MySQL start correctly.

Ok, I thought, lets purge MySQL, delete all the configuration files, init scripts, etc, and then reinstall it and start again from scratch.

Well, it's not working. Purge removes most of the stuff, but I manually removed the init scripts and stuff in /etc/mysql. Why is this not being reinstalled when the packages are reinstalled?

I don't want to copy configuration from elsewhere, I just want apt to reinstall *everything* related to the MySQL package from scratch. How do I go about this?

I've tried purging everything related to MySQL and it still won't reinstall the stuff in /etc. 

Here are the errors I was getting:

```
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                                                                                                                       [ OK ]
080724 11:42:47 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/user.frm' (errno: 13)
080724 11:42:47 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/user.frm' (errno: 13)
ERROR: 1017  Can't find file: './mysql/user.frm' (errno: 13)
080724 11:42:47 [ERROR] Aborting

080724 11:42:47 [Note] /usr/sbin/mysqld: Shutdown complete

Reloading AppArmor profiles : done.
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
 * Starting MySQL database server mysqld                                                                                                                                       [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Xiol on 2008-07-24
Nevermind folks, sorted it! Thanks.

---

