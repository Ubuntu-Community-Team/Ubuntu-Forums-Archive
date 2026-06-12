---
title: "Something kills all network every Sunday?"
date: 2008-01-06
forum: Server Platforms
---

### Post by TurboRush on 2008-01-06
Not sure I'll get a solution here, more looking for ideas of how to track this down...

Every Sunday at 6:25am something happens that causes Apache to receive a graceful restart request and also kills SSH... basically, it kills my network connectivity to the point that I need to restart the system to recover it...

Where would you start in trying to identify what process is doing this...

---

### Post by k_grdn on 2008-01-06
Hi,

A good start would be checking your logs for activity around that time:

grep 06:[0-9] /var/log/syslog

The culprits usually are syslog & logrotate, sysklogd rotates system logfiles weekly.  

syslogd-listfiles -w will list the files that are rotated, check that you have enough free space in /var, also check ownership/permisisons of files.  You may also want to check /etc/logrotate.d/ files for errors.


Regards,

k_grdn

---

### Post by TurboRush on 2008-01-06
So it does look like it has something to do with the logs rotating as it kicks off 1 second before I see the command issued in apache...

/var/ is only 1% used.

However, it appears that Apache recovers fine, my network does not... is there anyway to kill the log rotation so I can see if I am still alive next Sunday? If I am then I'll have to figure out what is killing my network...

---

### Post by k_grdn on 2008-01-06
Hi,

What exactly do you mean by killing your network?

What files are rotated by sysklogd?

What files are in /etc/logrotate.d/?

What happens when you run /etc/init.d/network restart?

Check the structure of you interfaces file.

Simplest way to remove sysklogd from /etc/cron.weekly but beware as your logfile sizes will increase!
 
Or remove offending file[s] from /etc/logrotate.d/, egrep the dir for 'restart|reload', this will narrow things down a bit.

Regards,

k_grdn

---

