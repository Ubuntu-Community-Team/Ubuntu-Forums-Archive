---
title: "What rotates logs for syslog, auth, and cron?"
date: 2015-08-10
forum: Server Platforms
---

### Post by FlintL on 2015-08-10
What is responsible for rotating the syslog, auth.log, and cron logs? I can’t find a file dedicated to these in /etc/logrotate.d, which is what I thought would be responsible.

I am new to linux, so the solution may be obvious, but my searching led me to log rotate mostly.

The logs I am talking about are in /var/log/.

---

### Post by howefield on 2015-08-10
Have a look in /etc/cron.daily/logrotate, and /etc/logrotate.conf.

---

### Post by volkswagner on 2015-08-10
On Ubuntu 14.04.2, I have /etc/logrotate.d/rsyslog. This file handles many of the base log files such as syslog, mail, auth, etc.

What version of Ubuntu are you running?

---

### Post by FlintL on 2015-08-10
I found it in /etc/logrotate.d/rsyslog in 14.04. I guess I just  overlooked that file. It seems to control the rotation of most default  system logs. 

Is there a reason it might be named **r**syslog instead of simply syslog? Does the **r** stand for something?

---

### Post by volkswagner on 2015-08-10
If you look in /etc/init.d you'll find rsyslog not syslog. Rsyslog is the application that collects the log info.

You can find a bit of reading on [rsyslog]("http://www.rsyslog.com/"), [rsyslog vs syslogd]("http://askubuntu.com/questions/55435/difference-between-rsyslogd-and-syslogd").

---

