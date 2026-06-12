---
title: "Logs Erased or Purged Server 12.04"
date: 2013-01-08
forum: Server Platforms
---

### Post by Image0fman on 2013-01-08
I went to check my server logs today and it looks I only have stuff beginning January 6th. When I use the 'last' command I only see logins from today and when I check auth.log I only see entries from January 6th and in syslog only from today.. Did something happen after the 1st? Anyone have this happen to them before? Also my server hasn't rebooted in 19 days..

---

### Post by Cheesemill on 2013-01-08
Have the old logs been compressed and renamed by logrotate?

Can you post the result of 'ls -lh' in one of the log directories you are concerned about please.

---

### Post by Image0fman on 2013-01-09
-rw-r--r-- 1 root      root    0 Jan  1 06:37 alternatives.log
-rw-r--r-- 1 root      root 5.5K Dec 11 09:21 alternatives.log.1
-rw-r--r-- 1 root      root  134 Nov 30 06:27 alternatives.log.2.gz
-rw-r--r-- 1 root      root 1.9K Nov 25 23:19 alternatives.log.3.gz
drwxr-xr-x 2 root      root 4.0K Jan  1 06:37 apt
-rw-r----- 1 syslog    adm   17K Jan  9 10:18 auth.log
-rw-r----- 1 syslog    adm   33K Jan  6 06:47 auth.log.1
-rw-r----- 1 syslog    adm  2.9K Dec 30 06:25 auth.log.2.gz
-rw-r----- 1 syslog    adm  260K Dec 23 06:47 auth.log.3
-rw-r----- 1 syslog    adm  8.6K Dec 18 06:25 auth.log.4.gz
-rw-r----- 1 root      adm    31 Oct 13 19:04 boot
-rw-r--r-- 1 root      root 1.3K Dec 19 23:01 boot.log
-rw-rw---- 1 root      utmp    0 Jan  1 06:37 btmp
-rw-rw---- 1 root      utmp    0 Dec  1 06:37 btmp.1
drwxr-xr-x 2 root      root 4.0K Apr 20  2012 dist-upgrade
-rw-r----- 1 root      adm   51K Dec 19 23:01 dmesg
-rw-r----- 1 root      adm   50K Dec 17 09:14 dmesg.0
-rw-r----- 1 root      adm   14K Dec 16 21:58 dmesg.1.gz
-rw-r----- 1 root      adm   14K Nov 26 00:11 dmesg.2.gz
-rw-r----- 1 root      adm   14K Nov 25 22:55 dmesg.3.gz
-rw-r----- 1 root      adm   14K Nov 25 22:54 dmesg.4.gz
-rw-r--r-- 1 root      root    0 Jan  1 06:37 dpkg.log
-rw-r--r-- 1 root      root  92K Dec 25 06:34 dpkg.log.1
-rw-r--r-- 1 root      root  925 Nov 30 06:27 dpkg.log.2.gz
-rw-r--r-- 1 root      root  31K Nov 25 23:19 dpkg.log.3.gz
-rw-r--r-- 1 root      root  32K Dec 17 15:38 faillog
-rw-r--r-- 1 root      root  410 Dec 11 09:21 fontconfig.log
drwxr-xr-x 2 root      root 4.0K Oct 13 19:04 fsck
drwxr-xr-x 3 root      root 4.0K Oct 13 23:35 installer
-rw-r----- 1 syslog    adm  1.3K Jan  9 06:44 kern.log
-rw-r----- 1 syslog    adm  3.4K Jan  6 06:54 kern.log.1
-rw-r----- 1 syslog    adm   906 Dec 30 06:40 kern.log.2.gz
-rw-r----- 1 syslog    adm   46K Dec 23 06:50 kern.log.3.gz
-rw-r----- 1 syslog    adm   48K Dec 18 06:41 kern.log.4.gz
drwxr-xr-x 2 landscape root 4.0K Oct 13 23:36 landscape
-rw-rw-r-- 1 root      utmp 286K Jan  9 09:46 lastlog
-rw-r----- 1 syslog    adm   426 Jan  9 06:44 mail.err
-rw-r----- 1 syslog    adm   742 Jan  5 06:26 mail.err.1
-rw-r----- 1 syslog    adm   193 Dec 29 06:55 mail.err.2.gz
-rw-r----- 1 syslog    adm   183 Dec 22 06:42 mail.err.3.gz
-rw-r----- 1 syslog    adm   218 Dec 15 06:34 mail.err.4.gz
-rw-r----- 1 syslog    adm   426 Jan  9 06:44 mail.log
-rw-r----- 1 syslog    adm   742 Jan  5 06:26 mail.log.1
-rw-r----- 1 syslog    adm   193 Dec 29 06:55 mail.log.2.gz
-rw-r----- 1 syslog    adm   183 Dec 22 06:42 mail.log.3.gz
-rw-r----- 1 syslog    adm   218 Dec 15 06:34 mail.log.4.gz
drwxr-xr-x 2 root      root 4.0K Oct 13 23:36 news
-rw-r----- 1 syslog    adm   589 Jan  9 10:17 syslog
-rw-r----- 1 syslog    adm  3.3K Jan  9 06:44 syslog.1
-rw-r----- 1 syslog    adm   623 Jan  8 06:42 syslog.2.gz
-rw-r----- 1 syslog    adm   628 Jan  7 06:32 syslog.3.gz
-rw-r----- 1 syslog    adm   724 Jan  6 06:54 syslog.4.gz
-rw-r----- 1 syslog    adm   624 Jan  5 06:26 syslog.5.gz
-rw-r----- 1 syslog    adm   540 Jan  4 06:38 syslog.6.gz
-rw-r----- 1 syslog    adm   633 Jan  3 06:34 syslog.7.gz
-rw-r--r-- 1 root      root 234K Dec 19 23:01 udev
-rw-r----- 1 syslog    adm     0 Oct 13 23:36 ufw.log
drwxr-xr-x 2 root      root 4.0K Jan  1 06:37 unattended-upgrades
drwxr-xr-x 2 root      root 4.0K Dec 20 06:50 upstart
-rw-r----- 1 root      adm     0 Dec 23 06:51 vsftpd.log
-rw------- 1 root      root 3.3K Dec 17 17:39 vsftpd.log.1
-rw-rw-r-- 1 root      utmp 2.7K Jan  9 09:46 wtmp
-rw-rw-r-- 1 root      utmp  68K Dec 25 23:37 wtmp.1

---

### Post by Cheesemill on 2013-01-09
Your logs are being handled by logrotate to make sure they don't grow too large, every now and then old logs are compressed and new ones are started.
```
-rw-r----- 1 syslog    adm   17K Jan  9 10:18 auth.log
-rw-r----- 1 syslog    adm   33K Jan  6 06:47 auth.log.1
-rw-r----- 1 syslog    adm  2.9K Dec 30 06:25 auth.log.2.gz
-rw-r----- 1 syslog    adm  260K Dec 23 06:47 auth.log.3
-rw-r----- 1 syslog    adm  8.6K Dec 18 06:25 auth.log.4.gz
```From your output you can see this has happened with your auth.log file, every week a new compressed file is created. To look at these old files you could use a command such as
```
zcat auth.log.2.gz | less 
```

---

### Post by sandyd on 2013-01-09
Moved to Server Platforms

---

### Post by Image0fman on 2013-01-11
> **Cheesemill said:**
> Your logs are being handled by logrotate to make sure they don't grow too large, every now and then old logs are compressed and new ones are started.
```
-rw-r----- 1 syslog    adm   17K Jan  9 10:18 auth.log
-rw-r----- 1 syslog    adm   33K Jan  6 06:47 auth.log.1
-rw-r----- 1 syslog    adm  2.9K Dec 30 06:25 auth.log.2.gz
-rw-r----- 1 syslog    adm  260K Dec 23 06:47 auth.log.3
-rw-r----- 1 syslog    adm  8.6K Dec 18 06:25 auth.log.4.gz
```From your output you can see this has happened with your auth.log file, every week a new compressed file is created. To look at these old files you could use a command such as
```
zcat auth.log.2.gz | less 
```

Cool thanks for your help, I appreciate it. I didn't know about the zcat utility, that's gonna come in handy. I see the configs for logrotate are located in /etc/logrotate.d and if you read the man page it shows you how to configure the rotation options.. pretty neat.. thanks !!

---

