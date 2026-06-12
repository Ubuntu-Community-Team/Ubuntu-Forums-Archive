---
title: "/var/log/syslog - cron question"
date: 2008-02-22
forum: Security Discussions
---

### Post by Spitphire on 2008-02-22
*not sure if this is the proper category*

The below command is running every 30 minutes.. I'm not sure what it's for, or what it does.  Should I be concerned about this?  It's being run as root...

```

EXTRACT FROM /var/log/syslog:

Feb 22 15:39:01 lp /USR/SBIN/CRON[6854]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

```

---

### Post by Adnarim on 2008-02-23
Looks like some cache is deleted every 30min.

---

### Post by Spitphire on 2008-02-24
hmm. ok thanks.

---

### Post by Mr. C. on 2008-02-25
Removing old, no longer inuse PHP session files.

---

