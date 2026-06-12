---
title: "Gutsy server restart every day at 06:25"
date: 2008-01-06
forum: Server Platforms
---

### Post by frankabel on 2008-01-06
Hi all,

Anybody known why a gutsy server with fews things installed restart every day at 06:25AM?

All seen that something put in "/etc/cron.daily/" is restarting the server because a second before restart the only thing that happen is the execution of cron tasks.:

Dec 31 06:25:01 vmm01 /USR/SBIN/CRON[5472]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))


Look what I have in " /etc/cron.daily/"


drwxr-xr-x  2 root root 4096 2007-12-16 23:46 .
drwxr-xr-x 67 root root 4096 2007-12-19 21:24 ..
-rwxr-xr-x  1 root root 5811 2007-10-15 16:40 apt
-rwxr-xr-x  1 root root  314 2007-09-15 05:25 aptitude
-rwxr-xr-x  1 root root  502 2007-05-15 05:47 bsdmainutils
-rwxr-xr-x  1 root root  473 2007-10-03 14:36 find
-rwxr-xr-x  1 root root   89 2006-06-19 14:21 logrotate
-rwxr-xr-x  1 root root  946 2007-05-23 02:52 man-db
-rw-r--r--  1 root root  102 2006-12-20 09:46 .placeholder
-rwxr-xr-x  1 root root 3283 2006-12-20 09:46 standard
-rwxr-xr-x  1 root root 1309 2007-09-17 16:54 sysklogd

Here what I saw in the log that let me think that my server is restarting every days.

Jan  4 06:25:02 vmm01 syslogd 1.4.1#21ubuntu3: restart.
Jan  3 06:25:02 vmm01 syslogd 1.4.1#21ubuntu3: restart.
Jan  2 06:25:02 vmm01 syslogd 1.4.1#21ubuntu3: restart.
Jan  1 06:25:03 vmm01 syslogd 1.4.1#21ubuntu3: restart.
Dec 31 06:25:03 vmm01 syslogd 1.4.1#21ubuntu3: restart.
Dec 30 06:25:03 vmm01 syslogd 1.4.1#21ubuntu3: restart.
Dec 30 06:47:02 vmm01 syslogd 1.4.1#21ubuntu3: restart.

Someone can know something about?

Thanks in advanced

Salute
Frank Abel

---

### Post by frankabel on 2008-01-06
Auto reply and another question ;)

I find in the /etc/cron.daily/ directory and found at line 47 in file sysklogd  the followfing line

/etc/init.d/sysklogd reload-or-restart > /dev/null

So all seen like what I though an system restarting entry in the log is just the syslogd restarting entry.

I restart my server manually (sudo reboot) at Jan  6 17:46:33 and as you can see the entry is the same.

Jan  6 06:47:01 logs syslogd 1.4.1#21ubuntu3: restart.
Jan  6 17:46:33 logs syslogd 1.4.1#21ubuntu3: restart.

Now that I know that my server isn't restarting every day, my question is:

How can I know when my server restart and when the syslogd restart? I mean, I want know the last time that my server was restarted

Salute
Frank Abel

---

### Post by p_quarles on 2008-01-06
Just the command
```
uptime
```
will tell you how long it's been running.

---

### Post by Sporkman on 2008-01-23
Typing in the command:

last

will also tell you when reboots occurred...

---

### Post by ikt on 2008-04-02
Hi all,

This message:

> syslogd 1.4.1#21ubuntu3: restart.

Appears everyday in our logs, however the server has been up for over a month now, happens around 7:30 every day.



What does it mean?

---

### Post by googlah on 2008-04-03
Perhaps that syslogd is being restarted? :o

---

### Post by frankabel on 2008-04-03
This script/etc/cron.daily/sysklogd is executed all day and restart syslog, not the system.

Salute
Frank Abel

---

### Post by ikt on 2008-04-03
thanks :)

---

