---
title: "Weekly log rotation is actually 6 days, then 8 days, then 6 days, ..."
date: 2016-04-11
forum: Server Platforms
---

### Post by Doug S on 2016-04-11
As the title says, my weekly log file rotation is alternating between 6 days and 8 days. Another way to say it, is that every other week the rotation will be correct, alternating weeks being one day late. Example:
```
doug@DOUG-64:~$ ls -l /var/log/kern*
-rw-r----- 1 syslog adm 5215435 Apr 10 23:27 /var/log/kern.log  [COLOR="#FF0000"]  <<< Will rotate later tonight.[/COLOR]
-rw-r----- 1 syslog adm 4908548 Apr  3 04:31 /var/log/kern.log.1[COLOR="#FF0000"]  <<< Correct[/COLOR]
-rw-r----- 1 syslog adm  780991 Mar 28 04:38 /var/log/kern.log.2.gz[COLOR="#FF0000"]  <<< One day late[/COLOR]
-rw-r----- 1 syslog adm 1042772 Mar 20 04:54 /var/log/kern.log.3.gz[COLOR="#FF0000"]  <<< Correct[/COLOR]
-rw-r----- 1 syslog adm  774831 Mar 14 04:38 /var/log/kern.log.4.gz[COLOR="#FF0000"]  <<< One day late[/COLOR]
```

Anybody else seen this behavior?
Note: I am a little behind on updates on this particular server. I suppose I should update and check again in two weeks.

---

### Post by dino99 on 2016-04-11
Looks ok on my desktop:

 ls -l /var/log/kern*
-rw-r----- 1 syslog adm  524413 Apr 11 10:49 /var/log/kern.log
-rw-r----- 1 syslog adm 1023422 Apr 10 05:35 /var/log/kern.log.1
-rw-r----- 1 syslog adm  252975 Apr  4 02:48 /var/log/kern.log.2.gz

---

### Post by Doug S on 2016-04-11
> **dino99 said:**
> Looks ok on my desktop:

 ls -l /var/log/kern*
-rw-r----- 1 syslog adm  524413 Apr 11 10:49 /var/log/kern.log
-rw-r----- 1 syslog adm 1023422 Apr 10 05:35 /var/log/kern.log.1
-rw-r----- 1 syslog adm  252975 Apr  4 02:48 /var/log/kern.log.2.gzShouldn't your April 4th one have been done on April 3rd?

---

### Post by dino99 on 2016-04-11
4+7=11 ; so wait & see tomorrow :P

---

### Post by Doug S on 2016-04-11
> **dino99 said:**
> 4+7=11 ; so wait & see tomorrow :PDino, It already rotated on the 10th, so that was 6 days. As far as I can tell, from a limited number of samples, you have the same issue.

---

### Post by dino99 on 2016-04-11
does not known 'how' it has been defined a 'week'; does it apply on delta & only works on some week's day(s). Well i'm not daily focussed on it :D

---

### Post by Doug S on 2016-04-11
By the way, I have the same issue on my main test 16.04 Server (a different computer):
```
-rw-r----- 1 syslog adm     7897 Apr 11 07:45 auth.log  [COLOR="#FF0000"]  <<< Current[/COLOR]
-rw-r----- 1 syslog adm   426894 Apr 11 03:25 auth.log.1[COLOR="#FF0000"]  <<< was a day late[/COLOR]
-rw-r----- 1 syslog adm     8314 Apr  3 03:47 auth.log.2.gz[COLOR="#FF0000"]  <<< was O.K.[/COLOR]
-rw-r----- 1 syslog adm    13569 Mar 28 03:39 auth.log.3.gz[COLOR="#FF0000"]  <<< was a day late[/COLOR]
-rw-r----- 1 syslog adm    15461 Mar 20 03:47 auth.log.4.gz[COLOR="#FF0000"] <<< was O.K.[/COLOR]

```Dino, the day of the week to do the rotation is defined in the crontab file. Because I am often awake and at my desk between 6 and 7 A.M., I always change the default time to sometime earlier.
```
doug@s15:~/config/etc$ diff crontab crontab.16.04.original
12,14c12,14
< 25 3  * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
< 47 3  * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
< 52 3  1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
---
> 25 6  * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
> 47 6  * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
> 52 6  1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
```The day of the week is the default Sunday:```
doug@s15:~/config/etc$ cat crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 3    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 3    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 3    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
```

---

### Post by dino99 on 2016-04-11
maybe  some way to dig:
if i remember well, long time ago, a discussion was about to run cron jobs only when the system was idled+some delay, to avoid some races. I dont know if that has been applied nor if today it still exist.

---

### Post by mc4man on 2016-04-11
7 till last one - 
```
-rw-r----- 1 syslog adm 1891927 Apr 11 20:03 /var/log/kern.log
-rw-r----- 1 syslog adm 1494304 Apr  3 21:25 /var/log/kern.log.1
-rw-r----- 1 syslog adm  304411 Mar 27 07:36 /var/log/kern.log.2.gz
-rw-r----- 1 syslog adm  357351 Mar 20 23:28 /var/log/kern.log.3.gz
-rw-r----- 1 syslog adm  543458 Mar 13 09:46 /var/log/kern.log.4.gz

```

---

### Post by Doug S on 2016-04-24
> **Doug S said:**
> 
Anybody else seen this behavior?
Note: I am a little behind on updates on this particular server. I suppose I should update and check again in two weeks.O.K. so it is Sunday morning, two weeks later. On one server the weekly log files did not rotate last night. On another server, they did rotate (but I had just re-booted that one).

Edit: Now Monday morning, and they rotated last night, a day late.

It will be two weeks before I have another data point.

---

### Post by Doug S on 2016-12-07
This problem is still driving me crazy, and I am not sure how to debug it and isolate the root issue. Also, I keep hoping it will be fixed with regular updates, but then it takes two weeks to obtain a new data point. For now, I have turned up the cron loglevel to 15 from the default of 1. I wonder if it might be related to RandomizedDelaySec, since the numbers seems a little ridiculous:```
doug@DOUG-64:~$ journalctl -u apt-daily.timer
-- Logs begin at Thu 2016-12-01 23:59:47 PST, end at Wed 2016-12-07 15:29:26 PST. --
Dec 02 04:28:46 DOUG-64 systemd[1]: apt-daily.timer: Adding 11h 51min 45.431720s random time.
Dec 02 04:28:46 DOUG-64 systemd[1]: apt-daily.timer: Adding 33min 10.381070s random time.
Dec 02 06:33:14 DOUG-64 systemd[1]: apt-daily.timer: Adding 1h 37min 40.293373s random time.
Dec 02 06:33:14 DOUG-64 systemd[1]: apt-daily.timer: Adding 7h 22min 2.287543s random time.
Dec 03 01:22:45 DOUG-64 systemd[1]: apt-daily.timer: Adding 8h 50min 14.263104s random time.
Dec 03 01:22:45 DOUG-64 systemd[1]: apt-daily.timer: Adding 21min 2.971556s random time.
Dec 03 06:21:14 DOUG-64 systemd[1]: apt-daily.timer: Adding 4h 25min 54.589150s random time.
Dec 03 06:21:14 DOUG-64 systemd[1]: apt-daily.timer: Adding 4h 11min 796.301ms random time.
Dec 03 22:11:24 DOUG-64 systemd[1]: apt-daily.timer: Adding 2h 59min 56.353718s random time.
Dec 03 22:11:24 DOUG-64 systemd[1]: apt-daily.timer: Adding 11h 24min 8.513789s random time.
Dec 04 17:24:30 DOUG-64 systemd[1]: apt-daily.timer: Adding 6h 6min 4.193918s random time.
Dec 04 17:24:30 DOUG-64 systemd[1]: apt-daily.timer: Adding 10h 8min 47.630313s random time.
Dec 05 04:09:36 DOUG-64 systemd[1]: apt-daily.timer: Adding 6h 53min 53.232083s random time.
Dec 05 04:09:36 DOUG-64 systemd[1]: apt-daily.timer: Adding 9h 21min 38.388531s random time.
Dec 05 15:22:24 DOUG-64 systemd[1]: apt-daily.timer: Adding 8h 18min 53.282520s random time.
Dec 05 15:22:24 DOUG-64 systemd[1]: apt-daily.timer: Adding 2h 59min 14.612127s random time.
Dec 05 20:59:24 DOUG-64 systemd[1]: apt-daily.timer: Adding 10min 59.247599s random time.
Dec 05 20:59:24 DOUG-64 systemd[1]: apt-daily.timer: Adding 1h 2min 24.021689s random time.
Dec 06 07:02:59 DOUG-64 systemd[1]: apt-daily.timer: Adding 2h 48min 26.636804s random time.
Dec 06 07:02:59 DOUG-64 systemd[1]: apt-daily.timer: Adding 8h 23min 7.157010s random time.
Dec 07 02:23:41 DOUG-64 systemd[1]: apt-daily.timer: Adding 5h 51min 11.407411s random time.
Dec 07 02:23:41 DOUG-64 systemd[1]: apt-daily.timer: Adding 3h 59min 15.279809s random time.
Dec 07 09:59:24 DOUG-64 systemd[1]: apt-daily.timer: Adding 2h 46min 5.576885s random time.
Dec 07 09:59:24 DOUG-64 systemd[1]: apt-daily.timer: Adding 7h 43min 5.258571s random time.

```

Note: this thread was started when 16.04 was still the development version, but now it is not. Maybe a moderator would be kind enough to move it to the Server platforms sub-forum.

EDIT: The issue is not exactly every other week, sometimes it will be O.K. two weeks in a row. In late October / early November it was O.K. for three consecutive weeks, which had me thinking the issue had been resolved.

---

### Post by cariboo on 2016-12-07
> **Doug S said:**
> 
Note: this thread was started when 16.04 was still the development version, but now it is not. Maybe a moderator would be kind enough to move it to the Server platforms sub-forum.

Done

---

### Post by Graham_Willis on 2016-12-10
Doug S: 

1. What's the contents of /etc/logrotate.conf ? 
2. Create /root/dump_logrotate_log.sh, with the following contents:

```

#!/bin/bash
/usr/sbin/logrotate -d /etc/logrotate.conf > /var/log/logrotate/logrotate_$(date +"%d.%m.%Y-%H:%M").txt 2>&1

```

Then **mkdir /var/log/logrotate**, **chmod 700 /root/dump_logrotate.sh **and add to the /etc/crontab an entry which will make it run every one hour.

Add your own task also writing logs (remember to set its permissions to 700) to /etc/cron.daily so you'd know if cron daily is working properly. In the meantime you can scan /var/log/syslog for some cron-related entries, but unfortunately these logs in Ubuntu don't seem to be very useful.

---

### Post by Doug S on 2016-12-10
Hi Graham,
Thanks very much for your reply.

> **Graham_Willis said:**
> Doug S: 

1. What's the contents of /etc/logrotate.conf ?
My /etc/logrotate.conf file is the default, I have not messed with it:```
doug@DOUG-64:~$ [COLOR="#FF0000"]cat /etc/logrotate.conf[/COLOR]
# see "man logrotate" for details
# rotate log files weekly
weekly

# use the syslog group by default, since this is the owning group
# of /var/log/syslog.
su root syslog

# keep 4 weeks worth of backlogs
rotate 4

# create new (empty) log files after rotating old ones
create

# uncomment this if you want your log files compressed
#compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

# no packages own wtmp, or btmp -- we'll rotate them here
/var/log/wtmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

/var/log/btmp {
    missingok
    monthly
    create 0660 root utmp
    rotate 1
}

# system-specific logs may be configured here

```

> **Graham_Willis said:**
> 2. Create /root/dump_logrotate_log.sh, with the following contents:

```

#!/bin/bash
/usr/sbin/logrotate -d /etc/logrotate.conf > /var/log/logrotate/logrotate_$(date +"%d.%m.%Y-%H:%M").txt 2>&1

```

Then **mkdir /var/log/logrotate**, **chmod 700 /root/dump_logrotate.sh **and add to the /etc/crontab an entry which will make it run every one hour.O.K. Will do. Thanks.

> **Graham_Willis said:**
> Add your own task also writing logs (remember to set its permissions to 700) to /etc/cron.daily so you'd know if cron daily is working properly. In the meantime you can scan /var/log/syslog for some cron-related entries, but unfortunately these logs in Ubuntu don't seem to be very useful.Since I increased the verbosity, I am basically waiting for a weekly run. Since I have never seen two bad weeks in a row, this Sunday (tomorrow) should be O.K. Yes, I constantly grep /var/log/syslog for cron-related entries. Example:```
doug@DOUG-64:~$ [COLOR="#FF0000"]grep CRON /var/log/syslog.1 | tail -4[/COLOR]
Dec 10 04:09:02 DOUG-64 CRON[20713]: (root) END ([20714]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 04:17:01 DOUG-64 CRON[20755]: (root) CMD ([20756]    cd / && run-parts --report /etc/cron.hourly)
Dec 10 04:17:01 DOUG-64 CRON[20755]: (root) END ([20756]    cd / && run-parts --report /etc/cron.hourly)
Dec 10 04:25:01 DOUG-64 CRON[20760]: (root) CMD ([20761] test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
doug@DOUG-64:~$ [COLOR="#FF0000"]grep CRON /var/log/syslog[/COLOR]
Dec 10 04:25:04 DOUG-64 CRON[20760]: (root) END ([20761] test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Dec 10 04:39:01 DOUG-64 CRON[20838]: (root) CMD ([20839]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 04:39:01 DOUG-64 CRON[20838]: (root) END ([20839]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 05:09:01 DOUG-64 CRON[20883]: (root) CMD ([20884]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 05:09:01 DOUG-64 CRON[20883]: (root) END ([20884]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 05:17:01 DOUG-64 CRON[21165]: (root) CMD ([21166]    cd / && run-parts --report /etc/cron.hourly)
Dec 10 05:17:01 DOUG-64 CRON[21165]: (root) END ([21166]    cd / && run-parts --report /etc/cron.hourly)
Dec 10 05:39:01 DOUG-64 CRON[21175]: (root) CMD ([21176]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 05:39:01 DOUG-64 CRON[21175]: (root) END ([21176]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 06:09:01 DOUG-64 CRON[21225]: (root) CMD ([21226]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 06:09:01 DOUG-64 CRON[21225]: (root) END ([21226]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 06:17:01 DOUG-64 CRON[21260]: (root) CMD ([21261]    cd / && run-parts --report /etc/cron.hourly)
Dec 10 06:17:01 DOUG-64 CRON[21260]: (root) END ([21261]    cd / && run-parts --report /etc/cron.hourly)
Dec 10 06:39:01 DOUG-64 CRON[21273]: (root) CMD ([21274]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 06:39:01 DOUG-64 CRON[21273]: (root) END ([21274]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 07:09:01 DOUG-64 CRON[21386]: (root) CMD ([21387]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 07:09:01 DOUG-64 CRON[21386]: (root) END ([21387]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 07:17:01 DOUG-64 CRON[21423]: (root) CMD ([21424]    cd / && run-parts --report /etc/cron.hourly)
Dec 10 07:17:01 DOUG-64 CRON[21423]: (root) END ([21424]    cd / && run-parts --report /etc/cron.hourly)
Dec 10 07:39:01 DOUG-64 CRON[21442]: (root) CMD ([21443]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 07:39:01 DOUG-64 CRON[21442]: (root) END ([21443]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 08:09:01 DOUG-64 CRON[21498]: (root) CMD ([21499]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 08:09:01 DOUG-64 CRON[21498]: (root) END ([21499]   [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Dec 10 08:17:01 DOUG-64 CRON[21538]: (root) CMD ([21539]    cd / && run-parts --report /etc/cron.hourly)
Dec 10 08:17:01 DOUG-64 CRON[21538]: (root) END ([21539]    cd / && run-parts --report /etc/cron.hourly)

```

---

### Post by Graham_Willis on 2016-12-10
What's the output of:

**cat /var/log/kern.log | awk '{print $1,$2}' | sort | uniq | sort -k2n**

and equivalents commands (use **zcat)** applied with regard to already archived kern.logs?

> Since I increased the verbosity, I am basically waiting for a weekly run. Since I have never seen two bad weeks in a row, this Sunday (tomorrow) should be O.K

It'd really be better to add a logging script to /etc/cron.daily because in this way you'll be immediately able to check if cron's working properly. The best solution would be to also call a script executing logrotate with debug logging - just take care to give the log a name which wouldn't cause a conflict with logs generated hourly. However, it's very important to collect the exact date of execution of the script (including hour and minutes) - you can save it in the log itself.

> Yes, I constantly grep /var/log/syslog for cron-related entries.

Have you checked if the cron.daily fired in the days in which you suppose that the rotation was missing?

---

### Post by Doug S on 2016-12-10
> **Graham_Willis said:**
> What's the output of:

**cat /var/log/kern.log | awk '{print $1,$2}' | sort | uniq | sort -k2n**

and equivalents commands (use **zcat)** applied with regard to already archived kern.logs?
```
doug@DOUG-64:~/temp3$ [COLOR="#FF0000"]cat kern.log | awk '{print $1,$2}' | sort | uniq | sort -k2n[/COLOR]
Dec 5
Dec 6
Dec 7
Dec 8
Dec 9
Dec 10
doug@DOUG-64:~/temp3$ [COLOR="#FF0000"]cat kern.log.1 | awk '{print $1,$2}' | sort | uniq | sort -k2n[/COLOR]
Dec 1
Dec 2
Dec 3
Dec 4
Dec 5
Nov 27
Nov 28
Nov 29
Nov 30
doug@DOUG-64:~/temp3$ [COLOR="#FF0000"]cat kern.log.2 | awk '{print $1,$2}' | sort | uniq | sort -k2n[/COLOR]
Nov 20
Nov 21
Nov 22
Nov 23
Nov 24
Nov 25
Nov 26
Nov 27
doug@DOUG-64:~/temp3$ [COLOR="#FF0000"]cat kern.log.3 | awk '{print $1,$2}' | sort | uniq | sort -k2n[/COLOR]
Nov 14
Nov 15
Nov 16
Nov 17
Nov 18
Nov 19
Nov 20
doug@DOUG-64:~/temp3$ [COLOR="#FF0000"]cat kern.log.4 | awk '{print $1,$2}' | sort | uniq | sort -k2n[/COLOR]
Nov 6
Nov 7
Nov 8
Nov 9
Nov 10
Nov 11
Nov 12
Nov 13
Nov 14
doug@DOUG-64:~/temp3$[COLOR="#FF0000"] tail -1 kern.log.4[/COLOR]
Nov 14 04:24:56 DOUG-64 kernel: [69124.639436] GENERIC:IN=enp4s0...
doug@DOUG-64:~/temp3$ [COLOR="#FF0000"]head -1 kern.log.3[/COLOR]
Nov 14 04:33:19 DOUG-64 kernel: [69627.047148] GENERIC:IN=enp4s0 ...
doug@DOUG-64:~/temp3$ [COLOR="#FF0000"]tail -1 kern.log.3[/COLOR]
Nov 20 04:19:30 DOUG-64 kernel: [587198.749220] GENERIC:IN=enp4s0 ...
doug@DOUG-64:~/temp3$ [COLOR="#FF0000"]head -1 kern.log.2[/COLOR]
Nov 20 04:28:35 DOUG-64 kernel: [587743.324982] NEW80:IN=enp4s0 ...
doug@DOUG-64:~/temp3$ [COLOR="#FF0000"]tail -1 kern.log.2[/COLOR]
Nov 27 04:19:04 DOUG-64 kernel: [1191972.172522] GENERIC:IN=enp4s0 ...
doug@DOUG-64:~/temp3$ [COLOR="#FF0000"]head -1 kern.log.1[/COLOR]
Nov 27 04:30:21 DOUG-64 kernel: [1192649.451820] GENERIC:IN=enp4s0 ...
doug@DOUG-64:~/temp3$ [COLOR="#FF0000"]tail -1 kern.log.1[/COLOR]
Dec  5 04:24:52 DOUG-64 kernel: [1883520.315096] GENERIC:IN=enp4s0 ...
doug@DOUG-64:~/temp3$ [COLOR="#FF0000"]head -1 kern.log[/COLOR]
Dec  5 04:25:08 DOUG-64 kernel: [1883536.315202] GENERIC:IN=enp4s0 ...
doug@DOUG-64:~/temp3$
```I keep my apache logs for 52 weeks, and have data 6 or 7 or 8 day data going back to when this issue started on or about 2016.02 (Feb).
Starting from December 5th, which was a bad weekly rotation, a day late, and working backwards (b = a day late, g = on the proper day):
bggbgggbgbgbgbgbggbgbggbgbgbggbgbgbgbgbgbggg
> **Graham_Willis said:**
> Have you checked if the cron.daily fired in the days in which you suppose that the rotation was missing?I have never seen any issue with the daily stuff, including the daily log rotations, i.e. /var/log/syslog. I'll check more carefully going forward.

I'm working on your other suggestions.

---

### Post by Graham_Willis on 2016-12-11
What's the contents of files returned after you execute **grep -Rl 'kern\.log' * **in /etc/logrotate.d?
What's the contents of /var/lib/logrotate/status?
Is there something apparently abnormal in logs dumped by dump_logrotate.sh?
Do kern.log and syslog files (including archived ones) contain any logrotate-related information?

---

### Post by Doug S on 2016-12-11
> **Graham_Willis said:**
> What's the contents of files returned after you execute **grep -Rl 'kern\.log' * **in /etc/logrotate.d?```
doug@DOUG-64:/etc/logrotate.d$ [COLOR="#FF0000"]grep -Rl 'kern\.log' *[/COLOR]
rsyslog

```
> **Graham_Willis said:**
> What's the contents of /var/lib/logrotate/status?```
doug@DOUG-64:/var/lib/logrotate$[COLOR="#FF0000"] ls -l[/COLOR]
total 4
-rw-r--r-- 1 root root 1471 Dec 11 04:25 status
doug@DOUG-64:/var/lib/logrotate$ [COLOR="#FF0000"]cat status[/COLOR]
logrotate state -- version 2
"/var/log/mysql.log" 2016-12-11-4:0:0
"/var/log/mail.warn" 2016-12-11-4:0:0
"/var/log/user.log" 2016-12-11-4:0:0
"/var/log/btmp" 2016-12-1-4:25:1
"/var/log/unattended-upgrades/unattended-upgrades-dpkg.log" 2016-12-11-4:0:0
"/var/log/wtmp" 2016-12-1-4:25:1
"/var/log/apache2/access.log" 2016-12-11-4:25:2
"/var/log/cron.log" 2016-12-11-4:0:0
"/var/log/lpr.log" 2016-12-11-4:0:0
"/var/log/auth.log" 2016-12-11-4:25:2
"/var/log/samba/log.smbd" 2016-12-11-4:25:2
"/var/log/apport.log" 2016-5-14-4:25:1
"/var/log/syslog" 2016-12-11-4:25:2
"/var/log/samba/log.winbindd" 2016-12-11-4:25:2
"/var/log/mysql/error.log" 2016-12-11-4:25:2
"/var/log/messages" 2016-12-11-4:0:0
"/var/log/daemon.log" 2016-12-11-4:0:0
"/var/log/dpkg.log" 2016-12-1-4:25:1
"/var/log/debug" 2016-12-11-4:0:0
"/var/log/ppp-connect-errors" 2016-12-11-4:0:0
"/var/log/ufw.log" 2016-12-11-4:0:0
"/var/log/apt/term.log" 2016-12-1-4:25:1
"/var/log/unattended-upgrades/unattended-upgrades.log" 2016-12-11-4:0:0
"/var/log/apt/history.log" 2016-12-1-4:25:1
"/var/log/mail.err" 2016-11-14-4:25:2
"/var/log/samba/log.nmbd" 2016-12-11-4:25:2
"/var/log/unattended-upgrades/unattended-upgrades-shutdown.log" 2016-1-31-6:0:0
"/var/log/alternatives.log" 2016-11-12-4:25:2
"/var/log/apache2/other_vhosts_access.log" 2016-1-31-6:0:0
"/var/log/mail.info" 2016-12-11-4:0:0
"/var/log/mail.log" 2016-12-11-4:25:2
"/var/log/kern.log" 2016-12-11-4:25:2
"/var/log/apache2/error.log" 2016-12-11-4:25:2

```Oh, that is a useful file to know about. I'll start keep copies of old ones, week by week.
> **Graham_Willis said:**
> Is there something apparently abnormal in logs dumped by dump_logrotate.sh?
No, they look fine. Recall that last week was a bad week, and so we expected the log files to start showing wanting to do something as of the change in day. i.e. we know (or more correctly, I learned yesterday) that logrotate will want to take the "if the current weekday is less than the weekday of the last rotation" weekly path. And it shows that desire every hour until the real execution of logrotate. You can observe by file size below (and note, after a few hours,  I changed the way it names the files from your original instructions):```
doug@DOUG-64:/var/log/logrotate$[COLOR="#FF0000"] ls -l[/COLOR]
total 280
-rw-r--r-- 1 root root     2 Dec 10 21:35 a_2016-12-10-21-35-35.txt   [COLOR="#FF0000"]<<< Test run of after logrotate time stamp script[/COLOR]
-rw-r--r-- 1 root root     2 Dec 10 21:36 b_2016-12-10-21-36-13.txt   [COLOR="#FF0000"]<<< Test run of before logrotate time stamp script[/COLOR]
-rw-r--r-- 1 root root  6896 Dec 10 10:45 logrotate_10.12.2016-10:45.txt
-rw-r--r-- 1 root root  6896 Dec 10 11:45 logrotate_10.12.2016-11:45.txt
-rw-r--r-- 1 root root  6896 Dec 10 12:45 logrotate_10.12.2016-12:45.txt
-rw-r--r-- 1 root root  6896 Dec 10 13:45 logrotate_10.12.2016-13:45.txt
-rw-r--r-- 1 root root  6896 Dec 10 14:45 logrotate_10.12.2016-14:45.txt
-rw-r--r-- 1 root root  6896 Dec 10 15:45 logrotate_10.12.2016-15:45.txt
-rw-r--r-- 1 root root  6896 Dec 10 16:45 logrotate_10.12.2016-16:45.txt
-rw-r--r-- 1 root root  6896 Dec 10 17:45 logrotate_2016-12-10-17-45-01.txt
-rw-r--r-- 1 root root  6896 Dec 10 18:45 logrotate_2016-12-10-18-45-01.txt
-rw-r--r-- 1 root root  6896 Dec 10 19:45 logrotate_2016-12-10-19-45-01.txt
-rw-r--r-- 1 root root  6896 Dec 10 20:45 logrotate_2016-12-10-20-45-01.txt
-rw-r--r-- 1 root root  6896 Dec 10 21:45 logrotate_2016-12-10-21-45-01.txt
-rw-r--r-- 1 root root  6896 Dec 10 22:45 logrotate_2016-12-10-22-45-01.txt
-rw-r--r-- 1 root root  6896 Dec 10 23:45 logrotate_2016-12-10-23-45-01.txt
-rw-r--r-- 1 root root [COLOR="#FF0000"]30047[/COLOR] Dec 11 00:45 logrotate_2016-12-11-00-45-01.txt
-rw-r--r-- 1 root root [COLOR="#FF0000"]30047[/COLOR] Dec 11 01:45 logrotate_2016-12-11-01-45-01.txt
-rw-r--r-- 1 root root [COLOR="#FF0000"]30047[/COLOR] Dec 11 02:45 logrotate_2016-12-11-02-45-01.txt
-rw-r--r-- 1 root root [COLOR="#FF0000"]30047[/COLOR] Dec 11 03:45 logrotate_2016-12-11-03-45-01.txt
-rw-r--r-- 1 root root  6896 Dec 11 04:45 logrotate_2016-12-11-04-45-01.txt
-rw-r--r-- 1 root root  6896 Dec 11 05:45 logrotate_2016-12-11-05-45-01.txt
-rw-r--r-- 1 root root  6896 Dec 11 06:45 logrotate_2016-12-11-06-45-01.txt
-rw-r--r-- 1 root root  6896 Dec 11 07:45 logrotate_2016-12-11-07-45-01.txt

```Note: my time stamp scripts did not run. Now I have a week to figure that out.

> **Graham_Willis said:**
> Do kern.log and syslog files (including archived ones) contain any logrotate-related information?Not that I could find. I do observe that it took 6 seconds to run daily:```
Dec 11 04:25:01 DOUG-64 CRON[25612]: (root) CMD ([25613] test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Dec 11 04:25:07 DOUG-64 CRON[25612]: (root) END ([25613] test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
```

I also looked at the source code for logrotate and am very very surprised to learn that there doesn't seem to be any jitter margin in the one week calculation:```
        case ROT_WEEKLY:
            /* rotate if:
               1) the current weekday is before the weekday of the
               last rotation
               2) more then a week has passed since the last
               rotation */
            state->doRotate = ((now.tm_wday < state->lastRotated.tm_wday)
                               ||
                               ((mktime(&now) -
                                 mktime(&state->lastRotated)) >
                                (7 * 24 * 3600)));
            if (!state->doRotate) {
            message(MESS_DEBUG, "  log does not need rotating "
                    "(log has been rotated at %d-%d-%d %d:%d, "
                    "that is not week ago yet)\n", state->lastRotated.tm_year,
                    state->lastRotated.tm_mon, state->lastRotated.tm_mday,
                    state->lastRotated.tm_hour, state->lastRotated.tm_min);
```Note: part of that debug message above is newer than what is currently in 16.04.
I also looked back at the source code for 12.04, and that part is the same, but without the debug message. O.K. so I went back to an old backup from when this very same server was 12.04, but there the weekly logs rotated faithfully always on Sunday (well, I only checked 1/2 of 2013).

EDIT: Adding pastebin links for [logrotate_2016-12-10-23-45-01.txt]("https://paste.ubuntu.com/23614845/") and [logrotate_2016-12-11-00-45-01.txt]("https://paste.ubuntu.com/23614829/")

---

### Post by Doug S on 2016-12-11
> **Doug S said:**
> I also looked at the source code for logrotate and am very very surprised to learn that there doesn't seem to be any jitter margin in the one week calculation.

O.K. so it seems that Debian Wheezy used to only store the date in the status file, but Debian Jessie stores the full date and time.
Reference: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=825776]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=825776")

It just so happens that I had my older 12.04 server (it is a normally turned off backup of the backup computer) turned on earlier today, and indeed the status file only has the date, no time of day.

I also have an old 14.04 server VM. And while logrotate has never been run on it, I did it manually so as to generate the status file. O.K. so now the date and hour is stored, but that's all, the minutes and seconds are always 0.

Conclusion: Everything now makes sense.

Anyway, the suggested patch is to introduce 60 seconds allowable jitter (myself, I would make it more, but O.K.)

I'll enter a launchpad bug report against the logrotate package and link in the upstream Debian bug report, which in turn needs to go upstream.

Graham: Thanks for your very valuable help on this one.

EDIT: [Launchpad Bug Report]("https://bugs.launchpad.net/ubuntu/+source/logrotate/+bug/1649168")

---

### Post by Graham_Willis on 2016-12-11
There's one more thing that we really need to know: What's the contents of /etc/logrotate.d/rsyslog ("[COLOR=#000000]*What's the **contents** of files returned after you execute *[/COLOR]**grep -Rl 'kern\.log' * ***in****/etc/logrotate.d?***"**)?. It might have local definitions overriding global ones.

But what you found makes sense. Note that there's a simple workaround - it should be sufficient to run logrotate hourly, not daily.

---

### Post by Doug S on 2016-12-11
> **Graham_Willis said:**
> There's one more thing that we really need to know: What's the contents of /etc/logrotate.d/rsyslog ("[COLOR=#000000]*What's the **contents** of files returned after you execute *[/COLOR]**grep -Rl 'kern\.log' * ***in****/etc/logrotate.d?***"**)?. It might have local definitions overriding global ones.I misread what you wanted. My file is the default:```
doug@DOUG-64:/etc/logrotate.d$ [COLOR="#FF0000"]cat rsyslog[/COLOR]
/var/log/syslog
{
        rotate 7
        daily
        missingok
        notifempty
        delaycompress
        compress
        postrotate
                invoke-rc.d rsyslog rotate > /dev/null
        endscript
}

/var/log/mail.info
/var/log/mail.warn
/var/log/mail.err
/var/log/mail.log
/var/log/daemon.log
/var/log/kern.log
/var/log/auth.log
/var/log/user.log
/var/log/lpr.log
/var/log/cron.log
/var/log/debug
/var/log/messages
{
        rotate 4
        weekly
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                invoke-rc.d rsyslog rotate > /dev/null
        endscript
}

```
> **Graham_Willis said:**
> But what you found makes sense. Note that there's a simple workaround - it should be sufficient to run logrotate hourly, not daily.Agreed.

---

### Post by Doug S on 2016-12-12
There is also issue 93 at GitHub:

[https://github.com/logrotate/logrotate/issues/93](https://github.com/logrotate/logrotate/issues/93)

I seem to be unable to create a GitHub account so that I can add to the issue discussion, and point to here.

EDIT 1: [https://www.clearos.com/clearfoundation/social/community/clearos-7-logrotate-not-always-rotating-as-expected]("https://www.clearos.com/clearfoundation/social/community/clearos-7-logrotate-not-always-rotating-as-expected")
EDIT 2:[ https://tracker.clearos.com/view.php?id=11331]("https://tracker.clearos.com/view.php?id=11331")

---

### Post by Doug S on 2016-12-15
> **Graham_Willis said:**
> But what you found makes sense. Note that there's a simple workaround - it should be sufficient to run logrotate hourly, not daily.
> **Doug S said:**
> Agreed.
Actually, if running logrotate hourly, then the weekly rotate time can migrate by as much as an hour per week. Eventually, it would kick back due to the day of week override.

---

### Post by Doug S on 2016-12-27
> **Doug S said:**
> There is also issue 93 at GitHub:

[https://github.com/logrotate/logrotate/issues/93](https://github.com/logrotate/logrotate/issues/93)

I seem to be unable to create a GitHub account so that I can add to the issue discussion, and point to here.I did finally manage to create a GIT account ( I had to use a different browser than firefox to do so ). And have chimed in there.

Setting this to "solved". While the issue still exists, it is now fully understood and no more help is required herein.

---

### Post by Graham_Willis on 2016-12-27
[quote="[COLOR=#000000]Doug S[/COLOR]"]Actually, if running logrotate hourly, then the weekly rotate time can migrate by as much as an hour per week. Eventually, it would kick back due to the day of week override.[/quote]

I don't exactly get what you're saying. As far as I understand the problem arose from the fact that the time condition under which logs are to be rotated is > 7*24*3600. Now, rotating logs can take a while and the date with time is being saved, so chances are that the next time the rotation won't happen, because it'll be a few seconds from the > 7 * 24 * 3600 condition.

Now, you are saying that this shift could take a full hour? It seems to be totally unrealistic. But I'm not sure if I understood you properly, did I?

Or perhaps you're saying about similar problems with hourly log rotation if such rotation's defined? But I think that it's hardly ever used.

Well, or you're saying that the rotation won't be always in the same hour - that's true, but it isn't something that I would too much care about.

---

### Post by Doug S on 2016-12-28
> **Graham_Willis said:**
> I don't exactly get what you're saying. As far as I understand the problem arose from the fact that the time condition under which logs are to be rotated is > 7*24*3600. Now, rotating logs can take a while and the date with time is being saved, so chances are that the next time the rotation won't happen, because it'll be a few seconds from the > 7 * 24 * 3600 condition.Yes.

> **Graham_Willis said:**
> Now, you are saying that this shift could take a full hour? It seems to be totally unrealistic. But I'm not sure if I understood you properly, did I? No. What I was saying is that if, due to the no jitter allowance, it misses that hour that it would normally have shifted, then yes it will get it the next hour, but the time stamp for the week after will also have shifted by an hour, and will be subject to the same lack of jitter tolerance. Eventually, it will shift another hour and then another hour. Once it tries to shift into Monday, then the day of the week condition will kick in it'll go back to the first hour of Sunday. However, I don't want the log rotations time to shift around anywhere on Sunday, I would prefer it to stay somewhere between 3 and 5 A.M. Sunday morning.

---

