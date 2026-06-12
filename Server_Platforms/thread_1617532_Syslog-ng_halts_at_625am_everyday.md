---
title: "Syslog-ng halts at 6:25am everyday"
date: 2010-11-09
forum: Server Platforms
---

### Post by azimmerman on 2010-11-09
Hello Everyone,

First Post w00t!

I wish it was under better circumstances...

Every morning at 6:25am syslog-ng stops logging, right after it attempts to log rotate. 

its odd... the daemon doesnt die... it gets a new PID, but doesnt write the output to /var/log/syslog.

Yet if I manually restart or reload syslog-ng it works great... its just like it doesnt like the logrotate...

I have googled around and tried a few things...

first I changed the postrotate in the logrotate.d/syslog-ng

--------/etc/logrotate.d/syslog-ng---------
/var/log/syslog {
   rotate 7
   daily
   compress
   postrotate
      /usr/sbin/invoke-rc.d syslog-ng reload >/dev/null
   endscript
--------end-------- 

to 

--------/etc/logrotate.d/syslog-ng---------
/var/log/syslog {
   rotate 7
   daily
   compress
   postrotate
      /usr/sbin/invoke-rc.d syslog-ng restart >/dev/null
   endscript
--------end--------

Thinking it was a syntax but no success...same results

so I tried adding delaycompress to /etc/logrotate.d/syslog-ng thinking it was not unlocking the log to be archived...

Still I am having the same results.

syslog-ng version is 2.0.9-4.2

Any feedback would be greatly appreciated as I am pretty new to Linux. Thanks! :)

---

### Post by azimmerman on 2010-11-09
any ideas?

I would seriously take any advice at this point on where to look.

Thanks :)

---

### Post by dtfinch on 2010-11-09
What happens when you run the command "/usr/sbin/invoke-rc.d syslog-ng restart" directly without redirecting its output to null? Any errors?

Searching around a bit, there's a patch to /etc/init.d/syslog-ng attached to [https://bugs.launchpad.net/ubuntu/+source/syslog-ng/+bug/661745](https://bugs.launchpad.net/ubuntu/+source/syslog-ng/+bug/661745) which might fix the problem, changing the line "--pidfile "$PIDFILE" $SYSLOGNG_OPTS" to "--pidfile "$PIDFILE" -- $SYSLOGNG_OPTS".

---

