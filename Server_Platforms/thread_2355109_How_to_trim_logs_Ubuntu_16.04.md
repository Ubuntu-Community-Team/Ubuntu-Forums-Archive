---
title: "How to trim logs Ubuntu 16.04"
date: 2017-03-09
forum: Server Platforms
---

### Post by deepakdeshp on 2017-03-09
Hello,

[LIST=1]
[*]How to find out which application is creating biggest logs in /var/log? Is there any script which sums the files by a particular log?
[*]How to trim /var/log folder?
[/LIST]
I tried ```
 sudo fstrim -v /var/log
``` but the error was ```
 fstrim: /var/log: the discard operation is not supported  
```.
I am using a single disk with ext4 file system.

---

### Post by TheFu on 2017-03-09
fstrim isn't for files. It is for ssd hardware and already run weekly on systems with ssds.

To manage log files, use **logrotate**. There are config files for each log file in /etc/logrotate.d/ . These config files are self-explanatory. Easy to copy and modify based on the 10+ examples already there. For example, to manage ufw logs, my system has:
```
/var/log/ufw.log
{
        rotate 4
        weekly
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                invoke-rc.d rsyslog reload >/dev/null 2>&1 || true
        endscript
}

```
Pretty clear what it does. Keeps 4 weeks of logs, rotates them weekly, then compresses and when all done, restarts rsyslog.

If you want to see log file sizes, use **du**. That is the normal tool besides **ls** to see file sizes.
Of course, since you are on a server, you'll want to check the manpages of those tools for any extra options that might be desired in your specific situation.

---

### Post by deepakdeshp on 2017-03-10
Thank you very much Thefu.

What would be the statement if I dont want the log file to be compressed but instead deleted from the disk?

---

### Post by TheFu on 2017-03-10
I dunno, perhaps change
[I]
rotate 4 --> rotate 3 or to rotate 1?
[/I]

There is a manpage for this stuff - probably in logrotate.conf.  I'd look at the time settings. When something accepts "weekly", I bet that daily, hourly, yearly, monthly, are also possible.  In my Linux Admin classes, I teach manpages, heavily.  Not enough use of those things around here, IMHO. The logrotate manpage is excellent, BTW.

---

