---
title: "syslog message"
date: 2008-04-16
forum: Security Discussions
---

### Post by heikaman on 2008-04-16
hi...
I keep seeing this message in syslog log file:

> 
/USR/SBIN/CRON[20534]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)


What does this mean :confused:

---

### Post by kidders on 2008-04-19
Hi there,

That's an execution log for a cron job that checks that /var/lib/php5 is a directory, searches it for files last updated a certain amount of time ago, and deletes them.

In English, it's trashing old PHP sessions. The cron script itself is probably in /etc/cron.d.

---

### Post by heikaman on 2008-04-19
Thank you very much for replying, now that you've explained it, reading it makes more sense :D

---

### Post by kidders on 2008-04-19
No problem. :-)

---

