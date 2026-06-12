---
title: "I need to setup security logs on my box?"
date: 2007-08-19
forum: Server Platforms
---

### Post by Mia_tech on 2007-08-19
I need to setup security logs on my box, one of the thing I wold like is to see a list of all users login either failed or successful dating several days back.

this file only shows login and cmd from the current day /var/log/auth.log 

thanks

---

### Post by Mr. C. on 2007-08-20
The system by default logs the important events.  They are rotated by two different methods in Ubunutu: the script /etc/cron.daily/sysklogd and the utility logrotate, depending upon how the log files are generated.

The syslog generated files (as seen in /etc/syslog.conf) are rotated by the script /etc/cron.daily/sysklogd.  You could move that to either /etc/cron.weekly, or /etc/cron.monthly to get weekly or monthy rotations.

The logrotate utility is configured with a default of rotating logs every 4 weeks, which you can change to your liking.  See /etc/logrotate.conf, /etc/logrotate.d and man logrotate.

A list of logins is maintained in a binary format in /var/log/wtmp, and access via the command:

```
last
```

MrC

---

