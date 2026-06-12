---
title: "MySQL and apparmor problem"
date: 2009-07-03
forum: Server Platforms
---

### Post by lfsierra on 2009-07-03
Hi

I have a problem with Mysql when I configure in my.cnf innodb_file_per_table and default-storage-engine=INNODB.

When execute a stored procedure that create a temporary table an error occurs, in the syslog file the next message is written:

219 Jul  2 19:39:04 srv mysqld[3665]: InnoDB: Unable to lock /tmp/#sqle50_a_0.ibd, error: 13
220 Jul  2 19:39:04 srv mysqld[3665]: InnoDB: Check that you do not already have another mysqld process
221 Jul  2 19:39:04 srv mysqld[3665]: InnoDB: using the same InnoDB data or log files.
222 Jul  2 19:39:04 srv mysqld[3665]: 090702 19:39:04  InnoDB: Error creating file '/tmp/#sqle50_a_0.ibd'.
223 Jul  2 19:39:04 srv mysqld[3665]: 090702 19:39:04  InnoDB: Operating system error number 13 in a file operation.
224 Jul  2 19:39:04 srv mysqld[3665]: InnoDB: The error means mysqld does not have the access rights to
225 Jul  2 19:39:04 srv mysqld[3665]: InnoDB: the directory.


**My ubuntu version is**:
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy


**Mysql**
mysql  Ver 14.12 Distrib 5.0.51a, for debian-linux-gnu (x86_64) using readline 5.2

**usr.sbin.mysqld armor file**:
# vim:syntax=apparmor
# Last Modified: Tue Jun 19 17:37:30 2007
#include <tunables/global>

/usr/sbin/mysqld {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/mysql>

  capability dac_override,
  capability setgid,
  capability setuid,

  /etc/hosts.allow r,
  /etc/hosts.deny r,

  /etc/group              m,
  /etc/passwd             m,

  /etc/mysql/*.pem r,
  /etc/mysql/conf.d/ r,
  /etc/mysql/conf.d/* r,
  /etc/mysql/my.cnf r,
  /usr/sbin/mysqld mr,
  /usr/share/mysql/** r,
  /var/lib/mysql/ r,
  /var/lib/mysql/** rwk,
  /var/log/mysql/ r,
  /var/log/mysql/* rw,
  /var/run/mysqld/mysqld.pid w,
  /var/run/mysqld/mysqld.sock w,
  /tmp/** rwk,

}

Any idea?

-------------------

**Solved.**:p

Before configure usr.bin.mysqld file with permision over /tmp/** rwk, I reload apparmor:
     /etc/init.d/apparmor reload

But this not apply the change on usr.bin.mysqld

So I stop an then start apparmor:
/etc/init.d/apparmor stop
/etc/init.d/apparmor start

And then all goes fine.

---

