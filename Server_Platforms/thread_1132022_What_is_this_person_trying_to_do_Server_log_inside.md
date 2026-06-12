---
title: "What is this person trying to do? Server log inside"
date: 2009-04-21
forum: Server Platforms
---

### Post by dj 2501 on 2009-04-21
Just locked down my system and setup ufw and viewing my log im seeing alot of blocked connection attempts.

Heres a little piece of the log. What do you think they are trying to access?
```

Apr 20 04:45:05 vwm01 kernel: [19155.168638] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=82.165.237.158 DST=174.143.26.225 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=54636 DF PROTO=TCP SPT=2614 DPT=32000 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 20 04:45:08 vwm01 kernel: [19158.013014] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=82.165.237.158 DST=174.143.26.225 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=55964 DF PROTO=TCP SPT=2614 DPT=32000 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 20 04:59:45 vwm01 -- MARK --
Apr 20 05:19:45 vwm01 -- MARK --
Apr 20 05:39:45 vwm01 -- MARK --
Apr 20 05:59:45 vwm01 -- MARK --
Apr 20 06:19:45 vwm01 -- MARK --
Apr 20 06:39:23 vwm01 kernel: [25869.006123] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=208.158.237.2 DST=174.143.26.225 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=10384 DF PROTO=TCP SPT=20714 DPT=1433 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 20 06:39:26 vwm01 kernel: [25871.975437] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=208.158.237.2 DST=174.143.26.225 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=12297 DF PROTO=TCP SPT=20714 DPT=1433 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 20 06:59:45 vwm01 -- MARK --
Apr 20 07:19:45 vwm01 -- MARK --
Apr 20 07:39:45 vwm01 -- MARK --
Apr 20 07:59:45 vwm01 -- MARK --
Apr 20 08:19:45 vwm01 -- MARK --
Apr 20 08:21:09 vwm01 kernel: [31833.280831] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=202.67.205.129 DST=174.143.26.225 LEN=104 TOS=0x00 PREC=0x00 TTL=116 ID=8105 PROTO=UDP SPT=26852 DPT=40635 LEN=84 
Apr 20 08:32:29 vwm01 kernel: [32498.243367] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=222.186.23.232 DST=174.143.26.225 LEN=40 TOS=0x00 PREC=0x00 TTL=104 ID=256 PROTO=TCP SPT=6000 DPT=2967 WINDOW=16384 RES=0x00 SYN URGP=0 
Apr 20 08:59:45 vwm01 -- MARK --
Apr 20 09:19:45 vwm01 -- MARK --
Apr 20 09:39:45 vwm01 -- MARK --
Apr 20 09:59:45 vwm01 -- MARK --
Apr 20 10:02:33 vwm01 kernel: [37775.998835] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=89.148.254.220 DST=174.143.26.225 LEN=203 TOS=0x00 PREC=0x00 TTL=114 ID=32598 PROTO=UDP SPT=2519 DPT=58196 LEN=183 
Apr 20 10:04:40 vwm01 kernel: [37899.282981] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=218.63.198.90 DST=174.143.26.225 LEN=404 TOS=0x00 PREC=0x00 TTL=114 ID=25265 PROTO=UDP SPT=4859 DPT=1434 LEN=384 
Apr 20 10:19:45 vwm01 -- MARK --
Apr 20 10:39:45 vwm01 -- MARK --
Apr 20 10:55:05 vwm01 kernel: [40854.624776] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=61.160.216.6 DST=174.143.26.225 LEN=40 TOS=0x00 PREC=0x00 TTL=104 ID=20014 PROTO=TCP SPT=6000 DPT=1433 WINDOW=16384 RES=0x00 SYN URGP=0 
Apr 20 11:15:35 vwm01 kernel: [42055.799333] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=115.192.154.151 DST=174.143.26.225 LEN=158 TOS=0x00 PREC=0x00 TTL=114 ID=30058 PROTO=UDP SPT=7597 DPT=58196 LEN=138 
Apr 20 11:39:46 vwm01 -- MARK --
Apr 20 11:59:46 vwm01 -- MARK --
Apr 20 12:19:46 vwm01 -- MARK --
Apr 20 12:38:49 vwm01 kernel: [46928.993028] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=211.96.27.65 DST=174.143.26.225 LEN=404 TOS=0x00 PREC=0x00 TTL=115 ID=51378 PROTO=UDP SPT=3101 DPT=1434 LEN=384 
Apr 20 12:41:11 vwm01 kernel: [47066.440169] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=24.244.132.66 DST=174.143.26.225 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=44599 DF PROTO=TCP SPT=58193 DPT=135 WINDOW=16384 RES=0x00 SYN URGP=0 
Apr 20 12:59:46 vwm01 -- MARK --
Apr 20 13:19:46 vwm01 -- MARK --
Apr 20 13:39:46 vwm01 -- MARK --
Apr 20 13:59:46 vwm01 -- MARK --
Apr 20 14:19:46 vwm01 -- MARK --
Apr 20 14:39:46 vwm01 -- MARK --
Apr 20 14:43:56 vwm01 kernel: [54246.614640] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=87.112.66.83 DST=174.143.26.225 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=44145 DF PROTO=TCP SPT=2628 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
Apr 20 14:45:21 vwm01 kernel: [54329.474641] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=82.165.237.158 DST=174.143.26.225 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=35693 DF PROTO=TCP SPT=4922 DPT=32000 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 20 14:45:24 vwm01 kernel: [54332.465529] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=82.165.237.158 DST=174.143.26.225 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=36832 DF PROTO=TCP SPT=4922 DPT=32000 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 20 14:54:38 vwm01 kernel: [54872.671107] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=218.75.199.50 DST=174.143.26.225 LEN=404 TOS=0x00 PREC=0x00 TTL=113 ID=1879 PROTO=UDP SPT=2484 DPT=1434 LEN=384 
Apr 20 15:19:46 vwm01 -- MARK --
Apr 20 15:39:46 vwm01 -- MARK --
Apr 20 15:59:46 vwm01 -- MARK --
Apr 20 16:19:46 vwm01 -- MARK --
Apr 20 16:39:46 vwm01 -- MARK --
Apr 20 16:54:28 vwm01 kernel: [61879.897902] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=190.77.144.234 DST=174.143.26.225 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=58143 DF PROTO=TCP SPT=8355 DPT=39553 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 20 16:54:31 vwm01 kernel: [61882.893998] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=190.77.144.234 DST=174.143.26.225 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=58195 DF PROTO=TCP SPT=8355 DPT=39553 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 20 16:57:10 vwm01 kernel: [62037.795160] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=81.104.143.54 DST=174.143.26.225 LEN=58 TOS=0x00 PREC=0x00 TTL=113 ID=17141 PROTO=UDP SPT=1799 DPT=40635 LEN=38 
Apr 20 17:19:46 vwm01 -- MARK --
Apr 20 17:39:46 vwm01 -- MARK --
Apr 20 17:49:42 vwm01 kernel: [65108.665329] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=65.98.240.53 DST=174.143.26.225 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=256 PROTO=TCP SPT=6000 DPT=8888 WINDOW=16384 RES=0x00 SYN URGP=0 
Apr 20 17:59:46 vwm01 -- MARK --
Apr 20 18:19:46 vwm01 -- MARK --
Apr 20 18:39:47 vwm01 -- MARK --
Apr 20 18:55:06 vwm01 kernel: [68932.923054] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=85.112.121.147 DST=174.143.26.225 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=49488 DF PROTO=TCP SPT=3888 DPT=39553 WINDOW=65280 RES=0x00 SYN URGP=0 
Apr 20 19:18:14 vwm01 kernel: [70285.511814] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=60.170.82.59 DST=174.143.26.225 LEN=404 TOS=0x00 PREC=0x00 TTL=112 ID=6044 PROTO=UDP SPT=1452 DPT=1434 LEN=384 
Apr 20 19:39:47 vwm01 -- MARK --
Apr 20 19:59:47 vwm01 -- MARK --
Apr 20 20:01:00 vwm01 kernel: [72786.340305] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=174.137.204.49 DST=174.143.26.225 LEN=52 TOS=0x00 PREC=0x00 TTL=49 ID=59159 DF PROTO=TCP SPT=16784 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
Apr 20 20:15:45 vwm01 syslogd 1.5.0#1ubuntu1: restart.
Apr 20 20:21:45 vwm01 kernel: [73998.811821] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=220.231.20.204 DST=174.143.26.225 LEN=40 TOS=0x00 PREC=0x00 TTL=103 ID=256 PROTO=TCP SPT=6000 DPT=3389 WINDOW=16384 RES=0x00 SYN URGP=0 
Apr 20 20:39:47 vwm01 -- MARK --
Apr 20 20:59:47 vwm01 -- MARK --
Apr 20 21:19:47 vwm01 -- MARK --
Apr 20 21:31:10 vwm01 kernel: [78058.579873] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=213.203.181.119 DST=174.143.26.225 LEN=69 TOS=0x00 PREC=0x00 TTL=107 ID=45735 PROTO=UDP SPT=14129 DPT=40635 LEN=49 
Apr 20 21:45:55 vwm01 kernel: [78921.085974] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=74.53.76.178 DST=174.143.26.225 LEN=40 TOS=0x00 PREC=0x00 TTL=247 ID=10880 PROTO=TCP SPT=3832 DPT=1433 WINDOW=4096 RES=0x00 SYN URGP=0 
Apr 20 21:59:47 vwm01 -- MARK --
Apr 20 22:19:47 vwm01 -- MARK --
Apr 20 22:39:47 vwm01 -- MARK --
Apr 20 22:59:47 vwm01 -- MARK --
Apr 20 23:19:47 vwm01 -- MARK --
Apr 20 23:39:47 vwm01 -- MARK --
Apr 20 23:59:47 vwm01 -- MARK --
Apr 21 00:18:12 vwm01 kernel: [87824.637359] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=77.247.188.150 DST=174.143.26.225 LEN=48 TOS=0x00 PREC=0x00 TTL=108 ID=45763 PROTO=TCP SPT=40793 DPT=17542 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 21 00:18:15 vwm01 kernel: [87827.512489] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=77.247.188.150 DST=174.143.26.225 LEN=48 TOS=0x00 PREC=0x00 TTL=108 ID=45769 PROTO=TCP SPT=40793 DPT=17542 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 21 00:39:47 vwm01 -- MARK --
Apr 21 00:59:47 vwm01 -- MARK --
Apr 21 01:19:47 vwm01 -- MARK --
Apr 21 01:39:47 vwm01 -- MARK --
Apr 21 01:59:48 vwm01 -- MARK --
Apr 21 02:19:48 vwm01 -- MARK --
Apr 21 02:39:48 vwm01 -- MARK --
Apr 21 02:59:48 vwm01 -- MARK --
Apr 21 03:13:12 vwm01 kernel: [98053.152241] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=218.22.113.170 DST=174.143.26.225 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=13831 DF PROTO=TCP SPT=37270 DPT=39553 WINDOW=65535 RES=0x00 SYN URGP=0 
Apr 21 03:39:48 vwm01 -- MARK --
Apr 21 03:59:48 vwm01 -- MARK --
Apr 21 04:05:42 vwm01 kernel: [101116.514971] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=61.1.148.104 DST=174.143.26.225 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=48639 DF PROTO=TCP SPT=1661 DPT=17542 WINDOW=16384 RES=0x00 SYN URGP=0 
Apr 21 04:07:35 vwm01 kernel: [101226.082462] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=40:40:c1:72:82:4e:00:23:33:f2:a6:7f:08:00 SRC=218.170.229.104 DST=174.143.26.225 LEN=52 TOS=0x00 PREC=0xA0 TTL=112 ID=2064 PROTO=UDP SPT=1052 DPT=58196 LEN=32
```

---

### Post by BkkBonanza on 2009-04-21
Just random garbage. This is nothing. If you start getting pounded many times per second then it may be interesting to look at. Welcome to the internet - there is constant traffic all the time hitting you. The stuff you're blocking isn't the concern - it's the stuff that gets in you worry about. Keep your software patched with security updates. Only open ports you need. Do a port scan from outside your network to make sure unused ports are stealth.

BTW 1433 is MS SQL server. Probably someone looking for an exploitable Windows server.

When you tire of people hitting your SSH/22 port and filling your logs you may want to move ssh to a random higher port so that it rarely gets picked upon.

---

### Post by dj 2501 on 2009-04-22
Thanks for the info it really helped me out.

Right now when I port scan my server from an outside network the block ports dont respond back at all. Is that good? or do I need to do something else to have them come up as stealth?

---

### Post by daboroe on 2009-04-22
dj 2501: Where did you get that log? What command did you run?

---

### Post by dj 2501 on 2009-04-22
/var/log/kern.log

---

### Post by kpatz on 2009-04-22
> **dj 2501 said:**
> Thanks for the info it really helped me out.

Right now when I port scan my server from an outside network the block ports dont respond back at all. Is that good? or do I need to do something else to have them come up as stealth?No response to a port = stealthed port.  If a port is blocked but not stealthed, it responds as closed (or rejected).

There are ongoing arguments as to whether stealthing is more secure or not...but it doesn't hurt to use it.

---

### Post by kustomjs on 2009-04-22
I would also make sure the ftp port is moved or closed if you have ftp server on your server.

---

### Post by windependence on 2009-04-22
> **BkkBonaza said:**
> Just random garbage. This is nothing. If you start getting pounded many times per second then it may be interesting to look at. Welcome to the internet - there is constant traffic all the time hitting you. The stuff you're blocking isn't the concern - it's the stuff that gets in you worry about. Keep your software patched with security updates. Only open ports you need. Do a port scan from outside your network to make sure unused ports are stealth.

BTW 1433 is MS SQL server. Probably someone looking for an exploitable Windows server.

When you tire of people hitting your SSH/22 port and filling your logs you may want to move ssh to a random higher port so that it rarely gets picked upon.

I agree totally with this post with the exception that moving the ssh port will probably not make much difference. Other than that, like Bkk says, welcome to the net, just worry about what gets in. Seeing blocked attempts is a GOOD thing. Seeing logins is not. :)

-Tim

---

