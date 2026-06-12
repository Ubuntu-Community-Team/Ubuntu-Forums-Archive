---
title: "Help I've been hacked I think?"
date: 2011-06-29
forum: Security
---

### Post by r0astedbean on 2011-06-29
Hi all,
I think I have been hacked. I have been having problems with the program loading and sometimes when I start the computer it boots into a sub routine that loads a version of Ubuntu with limited options. Then it will all of a sudden switch over to my regular desktop environment. In the log file I found this:

bruce rtkit-daemon[1182]: Successfully made thread 1601 of process 1601 (n/a) owned by '1000' high priority at nice level -11.
Jun 26 09:07:40 bruce rtkit-daemon[1182]: Supervising 4 threads of 2 processes of 2 users.
Jun 26 09:07:40 bruce rtkit-daemon[1182]: Successfully made thread 1602 of process 1601 (n/a) owned by '1000' RT at priority 5.
Jun 26 09:07:40 bruce rtkit-daemon[1182]: Supervising 5 threads of 2 processes of 2 users.
Jun 26 09:07:41 bruce rtkit-daemon[1182]: Successfully made thread 1603 of process 1601 (n/a) owned by '1000' RT at priority 5.
Jun 26 09:07:41 bruce rtkit-daemon[1182]: Supervising 6 threads of 2 processes of 2 users.
Jun 26 09:17:01 bruce CRON[1913]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

and also this: 

bruce rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="433" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jun 29 07:11:46 bruce kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jun 29 07:11:46 bruce rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="409" x-info="http://www.rsyslog.com"] (re)start
Jun 29 07:11:47 bruce rsyslogd: rsyslogd's groupid changed to 103
Jun 29 07:11:47 bruce rsyslogd: rsyslogd's userid changed to 101
Jun 29 07:11:46 bruce rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jun 29 07:11:47 bruce kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 29 07:11:47 bruce kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 29 07:11:47 bruce kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
Jun 2

these are from system log 01 and I am wondering if some one could have a look at the full system log 01,the boot log and the auth log. whaer should I post these as they are quite large. 

Any help would be much appreciated  I am running Ubuntu 11.04

---

### Post by guzjd on 2011-06-29
Check your /etc/passwd and /etc/group file to match up those uid and gids. It could be possible you have multiple users using one of these uid or gid. 
 
The daemons specified are part of normal operation.  I don't see anything obvious in these logs.

---

### Post by r0astedbean on 2011-06-29
Thank you for your reply,
I will have a look and see. :)

---

### Post by Rubi1200 on 2011-06-29
Hi and welcome to the forums r0astedbean :)

Could you please be more specific about what program/s are not responding as well as providing relevant information such as computer specifications, whether you have remote desktop applications running, server software or any other potentially vulnerable programs.

As  guzjd mentioned, you should check those files in the terminal and can use the following commands:

```
cat /etc/passwd

groups
```

You can also use the ```
last
``` command to look for logins and so on.

Those daemons, as mentioned, are normal:
[http://manpages.ubuntu.com/manpages/natty/en/man8/rsyslogd.8.html](http://manpages.ubuntu.com/manpages/natty/en/man8/rsyslogd.8.html)
[http://manpages.ubuntu.com/manpages/lucid/man8/rtkitctl.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/rtkitctl.8.html)

---

