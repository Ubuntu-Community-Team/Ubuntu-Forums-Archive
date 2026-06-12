---
title: "crontab defunct"
date: 2010-04-16
forum: Server Platforms
---

### Post by Eps1loN on 2010-04-16
Hi,

Every night daily.crontab fails and goes to <defunct>
In the morning I see:

\_ /bin/sh -c test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
 \_ run-parts --report /etc/cron.daily
             \_ [logrotate] <defunct>

If I manually srart "run-parts" or "logrotate" in verbose modes all goes without problems. /var/log/* gives no ideas. Ubuntu Server 9.04

Next some information about server conf:

/etc/crontab

25 5    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )



ls -l /etc/logrotate.d/

-rw-r--r-- 1 root root 293 2009-08-18 17:30 apache2
-rw-r--r-- 1 root root  84 2009-04-17 07:27 apt
-rw-r--r-- 1 root root  79 2009-02-10 15:45 aptitude
-rw-r--r-- 1 root root 111 2009-01-07 14:32 dpkg
-rw-r--r-- 1 root root 837 2009-03-03 04:41 mysql-server
-rw-r--r-- 1 root root  94 2009-02-20 19:25 ppp
-rw-r--r-- 1 root root 285 2008-11-19 16:40 stunnel4
-rw-r--r-- 1 root root 106 2009-04-09 04:44 wpa_action
-rw-r--r-- 1 root root 114 2009-04-09 04:44 wpa_supplicant

Any suggestions?

Regards,
EpsiloN.

---

