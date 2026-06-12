---
title: "syslog monitor free hdd space"
date: 2007-09-04
forum: Server Platforms
---

### Post by newuserxyz on 2007-09-04
Hi,

Is there a way to make syslog send a message to a syslog server once the hard disk is 90-95% full? I have found some scripts that use the df and sed but those were old and i was wondering if there was an easier way to do so.

Also, is there a way not to send a deamon.info, deamon.notice messages once i have a telnet connect from a specific IP only. I want to see all other deamon message from all other hosts.

Thanks

---

### Post by GigaVolt on 2007-09-04
Hint:
[http://www.cyberciti.biz/tips/shell-script-to-watch-the-disk-space.html](http://www.cyberciti.biz/tips/shell-script-to-watch-the-disk-space.html)

---

### Post by Mr. C. on 2007-09-06
Create a simple script that calls df and sends its output to the logger command. Run it as often as you need via a cron job.

```
man cron
man logger
```

Programs that use syslog do so via a standard syslog(2) call.  They define the facility and priority the log messages.  Many can be configured to log using a specified facility, and to only log messages at or above a given priority.  You configure syslog (man syslog.conf) to either log or ignore messages for a given facility and at a given priority.  You also configure where those messages will be sent (eg. a log file, a remote syslog server, the terminal, etc.).

The standard syslog is all or nothing - it does not selectively allow disabling logging by process or by pattern.  If a given facility and priority is configured to be log, it will be logged for all services that use that facility/priority combination.  Look into syslog-ng for more versatility, but tyipically syslog is sufficient.

MrC

---

