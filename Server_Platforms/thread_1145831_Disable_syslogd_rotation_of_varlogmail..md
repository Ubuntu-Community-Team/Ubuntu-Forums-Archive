---
title: "Disable syslogd rotation of /var/log/mail.*"
date: 2009-05-02
forum: Server Platforms
---

### Post by botfish on 2009-05-02
Hi,

I'm running a Postfix mail server on Ubuntu 7.10 and use awstats to process /var/log/mail.log.

I run a daily cron that reads /var/log/mail.log and updates the awstats database.

The problem I have is that /var/log/mail.log is rotated weekly by syslogd. This means I lose data if syslogd does a log rotate before awstats reads /var/log/mail.log

I would like to disable syslogd rotation of /var/log/mail.* files and use logrotate to rotate them. I am then able to use a prerotate directive to update awstats. This way I will not lose any data.

How do I disable syslogd rotation of /var/log/mail.* files?

Cheers.

---

### Post by John Cheng on 2009-05-04
You probably want to start by looking at the script that does the rotation, at /etc/cron.daily/sysklogd.

For Ubuntu 9.04, it appears to use  "/usr/sbin/syslogd-listfiles" to determine what files to rotate.

---

