---
title: "Possible to turn off all logging?"
date: 2014-10-14
forum: Security
---

### Post by welefort on 2014-10-14
Im working on  a project for my own customized version of Ubuntu.  Right now I would like to turn off All logging for the system.  Everything.  Syslog, apt, upstart....everything.

I have looked into pointing it to /dev/null  but that is creating another issue at the moment.

Any suggestions?

---

### Post by tgalati4 on 2014-10-14
What is the Use Case?  What is the purpose of this distro?  Embedded device?  Kiosk?  Running digital signage?  

I would create a RAMdisk and put /var/log in the RAMdisk.  That way you still get logging when the OS is running.  Run a cronjob to clear out /var/log when it gets full.  Remove the logrotate scripts, you won't need them.  You can set up remote logging (with rsyslogd) to a running server so that you have a backup log when you lose power.

So many frameworks use logging, that it it would be easier to redirect logging rather than turn it off for each framework.  

Perhaps redirect /var/log to a USB flash drive.

My first thought would be to simply create a symbolic link to /dev/null.  You might need to loosen permissions (try 777) on /dev/null, because soooo many processes want to write to /var/log.

---

