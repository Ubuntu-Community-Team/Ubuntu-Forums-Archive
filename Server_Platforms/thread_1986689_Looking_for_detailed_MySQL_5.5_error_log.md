---
title: "Looking for detailed MySQL 5.5 error log"
date: 2012-05-25
forum: Server Platforms
---

### Post by gottaa on 2012-05-25
I have looked in /var/log/syslog but the details just don't seem complete, I'm basically seeing the MySQL service stop with what appears to be no warnings or messages and I'm trying to find out exactly where the problem is.

The syslog details are as follows, incase I'm missing something ?

```
May 25 04:17:01 dd-slave2 CRON[4338]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 25 04:39:28 dd-slave2 kernel: [76151.162341] init: mysql main process (1156) terminated with status 1
May 25 04:39:28 dd-slave2 kernel: [76151.162360] init: mysql main process ended, respawning
May 25 04:39:28 dd-slave2 kernel: [76151.166584] audit_printk_skb: 6 callbacks suppressed
May 25 04:39:28 dd-slave2 kernel: [76151.166585] type=1400 audit(1337917168.048:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4347 comm="apparmor_parser"
May 25 04:39:30 dd-slave2 /etc/mysql/debian-start[4393]: Upgrading MySQL tables if necessary.
May 25 04:39:30 dd-slave2 /etc/mysql/debian-start[4396]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
May 25 04:39:30 dd-slave2 /etc/mysql/debian-start[4396]: Looking for 'mysql' as: /usr/bin/mysql
May 25 04:39:30 dd-slave2 /etc/mysql/debian-start[4396]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
May 25 04:39:30 dd-slave2 /etc/mysql/debian-start[4396]: This installation of MySQL is already upgraded to 5.5.22, use --force if you still need to run mysql_upgrade
May 25 04:39:30 dd-slave2 /etc/mysql/debian-start[4407]: Checking for insecure root accounts.
May 25 04:39:30 dd-slave2 /etc/mysql/debian-start[4412]: Triggering myisam-recover for all MyISAM tables
May 25 04:39:37 dd-slave2 kernel: [76160.527664] init: mysql main process (4351) terminated with status 1
May 25 04:39:37 dd-slave2 kernel: [76160.527687] init: mysql main process ended, respawning
May 25 04:39:37 dd-slave2 kernel: [76160.531857] type=1400 audit(1337917177.428:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4437 comm="apparmor_parser"
May 25 04:39:39 dd-slave2 /etc/mysql/debian-start[4576]: Upgrading MySQL tables if necessary.
May 25 04:39:39 dd-slave2 /etc/mysql/debian-start[4579]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
May 25 04:39:39 dd-slave2 /etc/mysql/debian-start[4579]: Looking for 'mysql' as: /usr/bin/mysql
May 25 04:39:39 dd-slave2 /etc/mysql/debian-start[4579]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
May 25 04:39:39 dd-slave2 /etc/mysql/debian-start[4579]: This installation of MySQL is already upgraded to 5.5.22, use --force if you still need to run mysql_upgrade
May 25 04:39:39 dd-slave2 /etc/mysql/debian-start[4590]: Checking for insecure root accounts.
May 25 04:39:39 dd-slave2 /etc/mysql/debian-start[4595]: Triggering myisam-recover for all MyISAM tables
May 25 04:39:39 dd-slave2 kernel: [76162.733660] init: mysql main process (4445) terminated with status 1
May 25 04:39:39 dd-slave2 kernel: [76162.733680] init: mysql main process ended, respawning
May 25 04:39:39 dd-slave2 kernel: [76162.737833] type=1400 audit(1337917179.636:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4618 comm="apparmor_parser"
May 25 04:39:41 dd-slave2 /etc/mysql/debian-start[4759]: Upgrading MySQL tables if necessary.
May 25 04:39:41 dd-slave2 /etc/mysql/debian-start[4762]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
May 25 04:39:41 dd-slave2 /etc/mysql/debian-start[4762]: Looking for 'mysql' as: /usr/bin/mysql
May 25 04:39:41 dd-slave2 /etc/mysql/debian-start[4762]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
May 25 04:39:41 dd-slave2 /etc/mysql/debian-start[4762]: This installation of MySQL is already upgraded to 5.5.22, use --force if you still need to run mysql_upgrade
May 25 04:39:41 dd-slave2 /etc/mysql/debian-start[4773]: Checking for insecure root accounts.
May 25 04:39:41 dd-slave2 /etc/mysql/debian-start[4778]: Triggering myisam-recover for all MyISAM tables
May 25 04:39:41 dd-slave2 kernel: [76164.998963] init: mysql main process (4627) terminated with status 1
May 25 04:39:41 dd-slave2 kernel: [76164.998988] init: mysql respawning too fast, stopped
May 25 05:17:01 dd-slave2 CRON[4896]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

Included the leading and trailing cron jobs so I didn't miss anything.

When I got to the machine this morning I couldn't start the MySQL service (though I did only try once), but a 'sudo reboot' everything fired up perfectly.

Anyone have any ideas on either the issue that caused the crash, or how to get a more complete error log in the future ?

---

