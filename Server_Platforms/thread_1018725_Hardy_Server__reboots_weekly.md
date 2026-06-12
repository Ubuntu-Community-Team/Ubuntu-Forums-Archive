---
title: "Hardy Server:  reboots weekly"
date: 2008-12-22
forum: Server Platforms
---

### Post by vortmax on 2008-12-22
I have an interesting problem. It appears that my server is rebooting itself every week.

Here are the filtered results from my kernel logs:

```


May  7 19:20:59 Cerberus kernel: [    0.000000] Initializing cgroup subsys cpuset
May  7 20:01:02 Cerberus kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 15 05:48:57 Cerberus kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 15 06:41:16 Cerberus kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  8 05:49:38 Cerberus kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  8 06:28:37 Cerberus kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  1 05:48:34 Cerberus kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  1 06:28:34 Cerberus kernel: [    0.000000] Initializing cgroup subsys cpuset


```

So as you see, it reboots every monday morning at 5:48ish then again almost 40 minutes later.  

I checked cron and there are no crontabs scheduled at either time.  cron.weekly is scheduled to run later at 6:47, so I don't think it's a cron triggered event.

The only commonality between events is the startup of syslog-ng

Here are some excerpts of the syslog surrounding the events:

```

Dec 15 05:39:01 Cerberus /USR/SBIN/CRON[15450]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0
 rm)
Dec 15 05:48:57 Cerberus syslog-ng[4331]: syslog-ng starting up; version='2.0.9'
Dec 15 05:48:57 Cerberus kernel: [    0.000000] Initializing cgroup subsys cpuset


Dec 15 06:25:01 Cerberus /USR/SBIN/CRON[5872]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Dec 15 06:41:16 Cerberus syslog-ng[4313]: syslog-ng starting up; version='2.0.9'
Dec 15 06:41:16 Cerberus kernel: [    0.000000] Initializing cgroup subsys cpuset


Dec 22 05:41:20 Cerberus nagios: Auto-save of retention data completed successfully.
May  7 19:20:59 Cerberus syslog-ng[4340]: syslog-ng starting up; version='2.0.9'
May  7 19:20:59 Cerberus kernel: [    0.000000] Initializing cgroup subsys cpuset

May  7 20:01:02 Cerberus syslog-ng[4339]: syslog-ng starting up; version='2.0.9'
May  7 20:01:02 Cerberus kernel: [    0.000000] Initializing cgroup subsys cpuset

```

The weird thing is in the event that happened today.  For some reason,  after 05:41:20 on Dec 22 (the nagios Auto-save event), the system time reset to May 7th 19:20:59 and the system rebooted.

Anyone encounter this before or know where to start digging for an answer?  The normal log files haven't really shown anything beyond what I posted above

---

