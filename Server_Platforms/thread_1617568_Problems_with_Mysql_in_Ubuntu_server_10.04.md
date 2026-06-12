---
title: "Problems with Mysql in Ubuntu server 10.04"
date: 2010-11-09
forum: Server Platforms
---

### Post by Tres_Iqus on 2010-11-09
Mysql can not start socket

/etc/init.d/mysql stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop mysql
stop: Job has already been stopped: mysql


and now when upgrade the system will not let me install mysql installation stuck

---

### Post by dapperdanny77 on 2010-11-09
what's your objective? upgrading vom 10.04 to 10.10?

have a look at /var/log/mysql/ for error logfiles

---

