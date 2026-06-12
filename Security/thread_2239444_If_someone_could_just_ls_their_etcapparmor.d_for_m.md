---
title: "If someone could just ls their /etc/apparmor.d for me that'd be great"
date: 2014-08-13
forum: Security
---

### Post by Hungry Man on 2014-08-13
I was hoping someone could just post the output of ls -l /etc/apparmor.d/ for me? *Only* if you have not added or removed any profiles, that is.

And if anyone has a *default* apparmor install (no profiles enforced that were not before, complained, etc) the output of aa-status.

---

### Post by Bashing-om on 2014-08-13
Hungry Man; Sure !

Here are my outputs.
Be advised I am booting a core-install on 14.04's kernel version 3.13.0-33-generic .
```

sysop@1404mini:~$ ls -l /etc/apparmor.d/
total 36
drwxr-xr-x 4 root root 4096 Jul  6 13:40 abstractions
drwxr-xr-x 2 root root 4096 Jul  6 13:44 cache
drwxr-xr-x 2 root root 4096 May 19  2013 disable
drwxr-xr-x 2 root root 4096 Apr 18  2013 force-complain
drwxr-xr-x 2 root root 4096 Jul  6 13:40 local
-rw-r--r-- 1 root root 2371 Apr  7 08:37 sbin.dhclient
drwxr-xr-x 5 root root 4096 Jul  6 13:40 tunables
-rw-r--r-- 1 root root 1393 Apr 18  2013 usr.sbin.rsyslogd
-rw-r--r-- 1 root root 1418 Aug 20  2012 usr.sbin.tcpdump
sysop@1404mini:~$ 

uname -r
3.13.0-33-generic
sysop@1404mini:~$

sysop@1404mini:~$ aa-status
apparmor module is loaded.
You do not have enough privilege to read the profile set.
sysop@1404mini:~$ sudo aa-status
[sudo] password for sysop: 
apparmor module is loaded.
4 profiles are loaded.
4 profiles are in enforce mode.
   /sbin/dhclient
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/sbin/tcpdump
0 profiles are in complain mode.
1 processes have profiles defined.
1 processes are in enforce mode.
   /sbin/dhclient (615) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
sysop@1404mini:~$

```
[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by Hungry Man on 2014-08-14
Thank you very much.

---

### Post by uRock on 2014-08-14
I haven't added anything to it, but the system has as I have installed apps.```
ls -l /etc/apparmor.d/
total 80
drwxr-xr-x 4 root root 4096 Jun 11 08:56 abstractions
drwxr-xr-x 2 root root 4096 Jul 22 07:21 cache
drwxr-xr-x 2 root root 4096 Apr 16 18:23 disable
drwxr-xr-x 2 root root 4096 Dec  4  2013 force-complain
-rw-r--r-- 1 root root  357 Apr 11 11:22 lightdm-guest-session
drwxr-xr-x 2 root root 4096 Jul  9 09:53 local
-rw-r--r-- 1 root root 2371 Apr  7 06:37 sbin.dhclient
drwxr-xr-x 5 root root 4096 Apr 16 18:25 tunables
-rw-r--r-- 1 root root 5528 Mar 11 10:55 usr.bin.evince
-rw-r--r-- 1 root root 4907 Jul 15 14:42 usr.bin.firefox
-rw-r--r-- 1 root root 1028 Apr 28 14:29 usr.bin.freshclam
-rw-r--r-- 1 root root 6904 Apr  7 07:31 usr.lib.telepathy
-rw-r--r-- 1 root root  420 Apr  7 13:04 usr.sbin.cups-browsed
-rw-r--r-- 1 root root 4490 Apr 10 11:40 usr.sbin.cupsd
-rw-r--r-- 1 root root 1393 Apr 18  2013 usr.sbin.rsyslogd
-rw-r--r-- 1 root root 1418 Jan 13  2014 usr.sbin.tcpdump
```

---

