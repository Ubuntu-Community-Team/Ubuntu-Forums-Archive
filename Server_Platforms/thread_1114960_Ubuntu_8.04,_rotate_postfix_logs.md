---
title: "Ubuntu 8.04, rotate postfix logs"
date: 2009-04-03
forum: Server Platforms
---

### Post by batfastad on 2009-04-03
Hi guys

I've got a VPS set up as a private remote relay with postfix. It's all working great, but I'm getting a bit concerned at the size of the mail logs.

mail.info and mail.log are approaching 100MB

I've read that log rotation in Ubuntu is handled by syslog.conf, is that correct?

Anyone know what config changes I need to make to get it rotating my mail logs?
And preferably zipping them up as well?

Ideally rotating once per week and keeping 4 weeks worth then deleting.

Any ideas/suggestions?

---

### Post by batfastad on 2009-04-03
As a follow up... my syslog is also at around 100MB so I guess that receives all the postfix logging as well.

When I look in /etc/logrotate.d I only have 3 files:
apt
aptitude
dpkg

When I look in /etc/syslog.conf...
```
#  /etc/syslog.conf     Configuration file for syslogd.
#
#                       For more information see syslog.conf(5)
#                       manpage.

#
# First some standard logfiles.  Log by facility.
#

auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          -/var/log/mail.log
user.*                          -/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info                       -/var/log/mail.info
mail.warn                       -/var/log/mail.warn
mail.err                        /var/log/mail.err
```

Do I need to create a profile for mail in /etc/logrotate.d?

Should this not be done automatically when I installed postfix?
I used aptitude to install

Any ideas?
Cheers, B

---

### Post by albinootje on 2009-04-03
> **batfastad said:**
>  I've read that log rotation in Ubuntu is handled by syslog.conf, is that correct?

Not sure about that.
But do you have the package logrotate installed ?
Can you see a <defunct> logrotate when you use "top" or "ps auxw" ?
I'm using Ubuntu and Debian in VPS-es and by default all logfiles are rotated.

---

### Post by batfastad on 2009-04-08
Ok you've solved it!
logrotate wasn't installed, it is now and is seems to be working!

Cheers, B

---

