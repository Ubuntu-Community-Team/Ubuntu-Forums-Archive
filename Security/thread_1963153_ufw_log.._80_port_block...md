---
title: "ufw log.. 80 port block.."
date: 2012-04-22
forum: Security
---

### Post by oklokl on 2012-04-22
ubuntu 11.10 dvd 64bit
ufw is only system

Is this an attack?
How do I block?

[SIZE=1]Apr 22 13:16:02 kds kernel: [ 4046.134593] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.49 DST=211.144.150.14 LEN=52 TOS=0x00 PREC=0x00 TTL=52 ID=1523 DF PROTO=TCP SPT=80 DPT=43838 WINDOW=7756 RES=0x00 ACK FIN URGP=0 
Apr 22 13:16:02 kds kernel: [ 4046.167311] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=114.108.157.211 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=25909 DF PROTO=TCP SPT=80 DPT=35057 WINDOW=32 RES=0x00 ACK FIN URGP=0 
Apr 22 13:16:03 kds kernel: [ 4046.355312] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=110.45.215.87 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=30650 DF PROTO=TCP SPT=80 DPT=43931 WINDOW=32 RES=0x00 ACK FIN URGP=0 
Apr 22 13:16:03 kds kernel: [ 4046.372486] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=114.108.157.211 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=25910 DF PROTO=TCP SPT=80 DPT=35057 WINDOW=32 RES=0x00 ACK FIN URGP=0 
Apr 22 13:16:03 kds kernel: [ 4046.390523] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.49 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=52019 DF PROTO=TCP SPT=80 DPT=43837 WINDOW=32 RES=0x00 ACK FIN URGP=0 
Apr 22 13:16:15 kds kernel: [ 4059.051719] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.49 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=52023 DF PROTO=TCP SPT=80 DPT=43837 WINDOW=32 RES=0x00 ACK FIN URGP=0 
Apr 22 13:16:55 kds kernel: [ 4098.633381] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=110.45.215.87 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=30658 DF PROTO=TCP SPT=80 DPT=43931 WINDOW=32 RES=0x00 ACK FIN URGP=0 
Apr 22 13:16:55 kds kernel: [ 4098.765021] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=110.45.229.15 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=41261 DF PROTO=TCP SPT=80 DPT=33983 WINDOW=32 RES=0x00 ACK FIN URGP=0 
Apr 22 13:17:58 kds kernel: [ 414.947431] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.49 DST=211.144.150.14 LEN=52 TOS=0x00 PREC=0x00 TTL=52 ID=59456 DF PROTO=TCP SPT=80 DPT=43885 WINDOW=9162 RES=0x00 ACK FIN URGP=0 
Apr 22 13:17:58 kds kernel: [ 414.990544] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.49 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=40632 DF PROTO=TCP SPT=80 DPT=43875 WINDOW=31 RES=0x00 ACK FIN URGP=0 
Apr 22 13:17:58 kds kernel: [ 4162.019127] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=114.108.157.200 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=55613 DF PROTO=TCP SPT=80 DPT=39115 WINDOW=39 RES=0x00 ACK FIN URGP=0 
Apr 22 13:18:11 kds kernel: [ 4174.572626] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=114.108.157.211 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=45529 DF PROTO=TCP SPT=80 DPT=35099 WINDOW=31 RES=0x00 ACK FIN URGP=0 
Apr 22 13:18:50 kds kernel: [ 4214.126613] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=114.108.157.211 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=45531 DF PROTO=TCP SPT=80 DPT=35099 WINDOW=31 RES=0x00 ACK FIN URGP=0 
Apr 22 13:18:51 kds kernel: [ 4214.574777] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=110.45.215.87 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=63580 DF PROTO=TCP SPT=80 DPT=43983 WINDOW=31 RES=0x00 ACK FIN URGP=0 
Apr 22 13:22:18 kds kernel: [ 4421.634226] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=110.45.215.87 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=38214 DF PROTO=TCP SPT=80 DPT=44055 WINDOW=31 RES=0x00 ACK FIN URGP=0 
Apr 22 13:22:18 kds kernel: [ 4421.770766] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.49 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=40309 DF PROTO=TCP SPT=80 DPT=43961 WINDOW=31 RES=0x00 ACK FIN URGP=0 
Apr 22 13:22:24 kds kernel: [ 4428.193894] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=110.45.215.87 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=38215 DF PROTO=TCP SPT=80 DPT=44055 WINDOW=31 RES=0x00 ACK FIN URGP=0 
Apr 22 13:22:25 kds kernel: [ 4428.334923] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.49 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=40310 DF PROTO=TCP SPT=80 DPT=43961 WINDOW=31 RES=0x00 ACK FIN URGP=0 
Apr 22 13:22:38 kds kernel: [ 4441.451481] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.49 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=40311 DF PROTO=TCP SPT=80 DPT=43961 WINDOW=31 RES=0x00 ACK FIN URGP=0 
Apr 22 13:23:04 kds kernel: [ 4467.692631] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.49 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=40312 DF PROTO=TCP SPT=80 DPT=43961 WINDOW=31 RES=0x00 ACK FIN URGP=0 
Apr 22 13:43:12 kds kernel: [ 5675.602528] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=211.244.82.39 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=16395 DF PROTO=TCP SPT=80 DPT=41963 WINDOW=27 RES=0x00 ACK FIN URGP=0 
Apr 22 13:43:12 kds kernel: [ 5675.616683] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=114.108.157.76 DST=211.144.150.14 LEN=52 TOS=0x00 PREC=0x00 TTL=51 ID=28394 DF PROTO=TCP SPT=80 DPT=47661 WINDOW=6432 RES=0x00 ACK FIN URGP=0 
Apr 22 13:43:12 kds kernel: [ 5675.636532] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.242 DST=211.144.150.14 LEN=52 TOS=0x00 PREC=0x00 TTL=52 ID=65034 DF PROTO=TCP SPT=80 DPT=45606 WINDOW=6432 RES=0x00 ACK FIN URGP=0 
Apr 22 13:43:12 kds kernel: [ 5675.653862] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.73 DST=211.144.150.14 LEN=52 TOS=0x00 PREC=0x00 TTL=51 ID=14729 DF PROTO=TCP SPT=80 DPT=56954 WINDOW=7504 RES=0x00 ACK FIN URGP=0 
Apr 22 13:43:12 kds kernel: [ 5675.655779] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.242 DST=211.144.150.14 LEN=52 TOS=0x00 PREC=0x00 TTL=52 ID=17417 DF PROTO=TCP SPT=80 DPT=45602 WINDOW=6432 RES=0x00 ACK FIN URGP=0 
Apr 22 13:43:12 kds kernel: [ 5675.655801] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.242 DST=211.144.150.14 LEN=52 TOS=0x00 PREC=0x00 TTL=52 ID=20535 DF PROTO=TCP SPT=80 DPT=45605 WINDOW=6432 RES=0x00 ACK FIN URGP=0 
Apr 22 13:43:12 kds kernel: [ 5675.673751] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.242 DST=211.144.150.14 LEN=52 TOS=0x00 PREC=0x00 TTL=52 ID=40383 DF PROTO=TCP SPT=80 DPT=45604 WINDOW=6432 RES=0x00 ACK FIN URGP=0 
Apr 22 13:43:12 kds kernel: [ 5675.673820] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.242 DST=211.144.150.14 LEN=52 TOS=0x00 PREC=0x00 TTL=52 ID=31792 DF PROTO=TCP SPT=80 DPT=45603 WINDOW=6432 RES=0x00 ACK FIN URGP=0 
Apr 22 13:43:12 kds kernel: [ 5675.687885] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=114.108.157.76 DST=211.144.150.14 LEN=52 TOS=0x00 PREC=0x00 TTL=51 ID=5298 DF PROTO=TCP SPT=80 DPT=47644 WINDOW=6432 RES=0x00 ACK FIN URGP=0 
Apr 22 13:43:12 kds kernel: [ 5675.727987] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=180.70.134.73 DST=211.144.150.14 LEN=52 TOS=0x00 PREC=0x00 TTL=51 ID=30860 DF PROTO=TCP SPT=80 DPT=56958 WINDOW=7504 RES=0x00 ACK FIN URGP=0 
Apr 22 13:43:38 kds kernel: [ 5701.785961] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e5:eb:ed:ce:00:d0:cb:4d:d6:2b:03:00 SRC=211.244.82.39 DST=211.144.150.14 LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=63532 DF PROTO=TCP SPT=80 DPT=41960 WINDOW=27 RES=0x00 ACK FIN URGP=0 
Apr 22 13:44:04 kds kernel: [ 5728.027510] [UFW BLOCK] IN=eth0 OUT= MAC=00:0e:e8:eb:ed:ad:00:d0:cb:7d:d6[/SIZE]

---

### Post by wacky_sung on 2012-04-22
Are you running any bittorrent client? If so, this is kinda common. Thus you are from china instead of being from south Korea indicated. Remove your destination ip source otherwise some lamers may like to visit you.
[IMG]http://i42.tinypic.com/35c4qxi.png[/IMG]

---

### Post by oklokl on 2012-04-22
My MAC or IP has changed.
 For security reasons, I. ..

Torrent has not used.

[SIZE=1]DST=211.144.150.14
my pc..
[/SIZE]
booting and time..
Apr 22 12:34:35 kds NetworkManager[872]: <info>   domain name 'kornet'
Apr 22 12:34:35 kds dbus[859]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 22 12:34:35 kds dbus[859]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 22 12:37:42 kds sudo: pam_ecryptfs: pam_sm_authenticate: /home/kds is already mounted
Apr 22 12:37:52 kds kernel: [ 1756.264822] audit_printk_skb: 120 callbacks suppressed

Torrent not executed.

---

### Post by wacky_sung on 2012-04-22
Are you behind TOR? If so, this is kinda common and don't worry so much as your firewall is blocking it. You are very likely using using browser to surf the net and getting all those responses.

---

### Post by oklokl on 2012-04-22
Thanks in advice ..
 Firefox doubt.
 Icon discoloration. Are often
 Suspicious symptoms
 Since this part is killing me.

 When My pc boot the desktop icons are replaced.


Apr 22 19:54:26 kds dbus[886]: [system] Activating service name='org.debian.apt' (using servicehelper)
Apr 22 19:54:27 kds AptDaemon: INFO: Initializing daemon
Apr 22 19:54:27 kds dbus[886]: [system] Successfully activated service 'org.debian.apt'
Apr 22 19:54:27 kds AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Apr 22 19:54:27 kds AptDaemon.Trans: INFO: Simulate was called
Apr 22 19:54:27 kds AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/33c36ff1234567ffa1234ec3eeb1c6ks
Apr 22 19:54:32 kds AptDaemon.Worker: INFO: Upgrade system with safe mode: 1

---

### Post by wacky_sung on 2012-04-22
Probably you shall indicate which version of Ubuntu and firefox you are using. 

Simple steps to trouble and narrow down your issues is to follow the 2 steps as below.
1. Install [Bleachbit]("http://bleachbit.sourceforge.net/") and clear all your firefox data, temporary files, etc.
2. Install [clam antivirus]("https://help.ubuntu.com/community/ClamAV") and perform a full system scan.

---

