---
title: "Shorewall Cloggin up Syslog"
date: 2010-10-29
forum: Server Platforms
---

### Post by Merrigan on 2010-10-29
Hi All,

I have been using Ubuntu for some time now for most of our servers at the office. I have always been having this problem, but until now it hasn't really bothered me that much, but now that I really need syslog to do some troubleshooting, it's a hassle. 

I recently (A Day Ago) installed Ubuntu Server 10.04 x64 on our main firewall/proxy machine, and it works well.

The problem I'm having, is that shorewall/iptables/something to do with the firewall is clogging up my syslog (400MB of logs in 16 hours). Now I have drive space and that is not the problem, the problem is that it fills it so fast I'm unable to read anything that scrolls when I tailf /var/log/syslog

I have turned off every bit of logging I could find in any configuration file for shorewall, but For some odd reason the logging still continues. This is the info it fills up with:

> 
Oct 29 12:21:55 moses kernel: [ 9314.347026] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=69.63.189.39 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=3255 DF PROTO=TCP SPT=33923 DPT=80 WINDOW=92 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9314.347153] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=69.63.189.39 LEN=1380 TOS=0x00 PREC=0x00 TTL=64 ID=3256 DF PROTO=TCP SPT=33923 DPT=80 WINDOW=92 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9314.347169] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=69.63.189.39 LEN=145 TOS=0x00 PREC=0x00 TTL=64 ID=3257 DF PROTO=TCP SPT=33923 DPT=80 WINDOW=92 RES=0x00 ACK PSH URGP=0
Oct 29 12:21:55 moses kernel: [ 9314.347203] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=69.63.189.39 LEN=235 TOS=0x00 PREC=0x00 TTL=64 ID=3258 DF PROTO=TCP SPT=33923 DPT=80 WINDOW=92 RES=0x00 ACK PSH URGP=0
Oct 29 12:21:55 moses kernel: [ 9314.486632] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=69.63.189.39 DST=196.211.145.220 LEN=52 TOS=0x00 PREC=0x00 TTL=61 ID=13569 DF PROTO=TCP SPT=80 DPT=33923 WINDOW=8288 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9314.604638] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=69.63.189.39 DST=196.211.145.220 LEN=52 TOS=0x00 PREC=0x00 TTL=61 ID=15807 DF PROTO=TCP SPT=80 DPT=33923 WINDOW=8300 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9315.057391] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=196.33.130.47 DST=196.211.145.220 LEN=1380 TOS=0x00 PREC=0x00 TTL=121 ID=2462 DF PROTO=TCP SPT=80 DPT=47083 WINDOW=65072 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9315.060527] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=196.33.130.47 DST=196.211.145.220 LEN=1380 TOS=0x00 PREC=0x00 TTL=121 ID=2463 DF PROTO=TCP SPT=80 DPT=47083 WINDOW=65072 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9315.060550] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=196.33.130.47 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=57890 DF PROTO=TCP SPT=47083 DPT=80 WINDOW=63744 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9315.063706] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=196.33.130.47 DST=196.211.145.220 LEN=1380 TOS=0x00 PREC=0x00 TTL=121 ID=2464 DF PROTO=TCP SPT=80 DPT=47083 WINDOW=65072 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9315.064637] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=196.33.130.47 DST=196.211.145.220 LEN=643 TOS=0x00 PREC=0x00 TTL=121 ID=2465 DF PROTO=TCP SPT=80 DPT=47083 WINDOW=65072 RES=0x00 ACK PSH URGP=0
Oct 29 12:21:55 moses kernel: [ 9315.064659] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=196.33.130.47 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=57891 DF PROTO=TCP SPT=47083 DPT=80 WINDOW=63744 RES=0x00 ACK URGP=0
Oct 29 12:21:56 moses kernel: [ 9315.355495] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=69.63.189.39 DST=196.211.145.220 LEN=378 TOS=0x00 PREC=0x00 TTL=61 ID=28825 DF PROTO=TCP SPT=80 DPT=33923 WINDOW=8300 RES=0x00 ACK PSH URGP=0
Oct 29 12:21:56 moses kernel: [ 9315.355534] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=69.63.189.39 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=3259 DF PROTO=TCP SPT=33923 DPT=80 WINDOW=108 RES=0x00 ACK URGP=0
Oct 29 12:21:56 moses kernel: [ 9315.357068] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=69.63.189.39 DST=196.211.145.220 LEN=539 TOS=0x00 PREC=0x00 TTL=61 ID=28826 DF PROTO=TCP SPT=80 DPT=33923 WINDOW=8300 RES=0x00 ACK PSH URGP=0
Oct 29 12:21:56 moses kernel: [ 9315.357090] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=69.63.189.39 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=3260 DF PROTO=TCP SPT=33923 DPT=80 WINDOW=125 RES=0x00 ACK URGP=0


I have been using shorewall for some time now, and on my one Gentoo Server as well. There is no such hassles on that and the log is nice & quiet. Is there **ANYONE** out there that can maybe help, as I'm at my wits end.

Regards,

---

### Post by Merrigan on 2010-10-29
Hi All,

I have been using Ubuntu for some time now for most of our servers at the office. I have always been having this problem, but until now it hasn't really bothered me that much, but now that I really need syslog to do some troubleshooting, it's a hassle. 

I recently (A Day Ago) installed Ubuntu Server 10.04 x64 on our main firewall/proxy machine, and it works well.

The problem I'm having, is that shorewall/iptables/something to do with the firewall is clogging up my syslog (400MB of logs in 16 hours). Now I have drive space and that is not the problem, the problem is that it fills it so fast I'm unable to read anything that scrolls when I tailf /var/log/syslog

I have turned off every bit of logging I could find in any configuration file for shorewall, but For some odd reason the logging still continues. This is the info it fills up with:

> 
Oct 29 12:21:55 moses kernel: [ 9314.347026] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=69.63.189.39 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=3255 DF PROTO=TCP SPT=33923 DPT=80 WINDOW=92 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9314.347153] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=69.63.189.39 LEN=1380 TOS=0x00 PREC=0x00 TTL=64 ID=3256 DF PROTO=TCP SPT=33923 DPT=80 WINDOW=92 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9314.347169] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=69.63.189.39 LEN=145 TOS=0x00 PREC=0x00 TTL=64 ID=3257 DF PROTO=TCP SPT=33923 DPT=80 WINDOW=92 RES=0x00 ACK PSH URGP=0
Oct 29 12:21:55 moses kernel: [ 9314.347203] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=69.63.189.39 LEN=235 TOS=0x00 PREC=0x00 TTL=64 ID=3258 DF PROTO=TCP SPT=33923 DPT=80 WINDOW=92 RES=0x00 ACK PSH URGP=0
Oct 29 12:21:55 moses kernel: [ 9314.486632] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=69.63.189.39 DST=196.211.145.220 LEN=52 TOS=0x00 PREC=0x00 TTL=61 ID=13569 DF PROTO=TCP SPT=80 DPT=33923 WINDOW=8288 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9314.604638] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=69.63.189.39 DST=196.211.145.220 LEN=52 TOS=0x00 PREC=0x00 TTL=61 ID=15807 DF PROTO=TCP SPT=80 DPT=33923 WINDOW=8300 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9315.057391] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=196.33.130.47 DST=196.211.145.220 LEN=1380 TOS=0x00 PREC=0x00 TTL=121 ID=2462 DF PROTO=TCP SPT=80 DPT=47083 WINDOW=65072 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9315.060527] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=196.33.130.47 DST=196.211.145.220 LEN=1380 TOS=0x00 PREC=0x00 TTL=121 ID=2463 DF PROTO=TCP SPT=80 DPT=47083 WINDOW=65072 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9315.060550] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=196.33.130.47 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=57890 DF PROTO=TCP SPT=47083 DPT=80 WINDOW=63744 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9315.063706] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=196.33.130.47 DST=196.211.145.220 LEN=1380 TOS=0x00 PREC=0x00 TTL=121 ID=2464 DF PROTO=TCP SPT=80 DPT=47083 WINDOW=65072 RES=0x00 ACK URGP=0
Oct 29 12:21:55 moses kernel: [ 9315.064637] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=196.33.130.47 DST=196.211.145.220 LEN=643 TOS=0x00 PREC=0x00 TTL=121 ID=2465 DF PROTO=TCP SPT=80 DPT=47083 WINDOW=65072 RES=0x00 ACK PSH URGP=0
Oct 29 12:21:55 moses kernel: [ 9315.064659] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=196.33.130.47 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=57891 DF PROTO=TCP SPT=47083 DPT=80 WINDOW=63744 RES=0x00 ACK URGP=0
Oct 29 12:21:56 moses kernel: [ 9315.355495] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=69.63.189.39 DST=196.211.145.220 LEN=378 TOS=0x00 PREC=0x00 TTL=61 ID=28825 DF PROTO=TCP SPT=80 DPT=33923 WINDOW=8300 RES=0x00 ACK PSH URGP=0
Oct 29 12:21:56 moses kernel: [ 9315.355534] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=69.63.189.39 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=3259 DF PROTO=TCP SPT=33923 DPT=80 WINDOW=108 RES=0x00 ACK URGP=0
Oct 29 12:21:56 moses kernel: [ 9315.357068] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:11:95:60:03:f6:00:14:a9:7a:70:30:08:00 SRC=69.63.189.39 DST=196.211.145.220 LEN=539 TOS=0x00 PREC=0x00 TTL=61 ID=28826 DF PROTO=TCP SPT=80 DPT=33923 WINDOW=8300 RES=0x00 ACK PSH URGP=0
Oct 29 12:21:56 moses kernel: [ 9315.357090] BANDWIDTH_OUT:IN= OUT=eth0 SRC=196.211.145.220 DST=69.63.189.39 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=3260 DF PROTO=TCP SPT=33923 DPT=80 WINDOW=125 RES=0x00 ACK URGP=0


I have been using shorewall for some time now, and on my one Gentoo Server as well. There is no such hassles on that and the log is nice & quiet. Is there **ANYONE** out there that can maybe help, as I'm at my wits end.

Regards,

---

### Post by s.fox on 2010-10-29
Threads merged. Please do not create duplicate threads. Thank you.

---

### Post by jon.newcomb on 2011-01-07
It is your iptables firewall. Its set to log all incomming / outgoing traffic. Just modify the firewall entries and you are good to go.

---

### Post by davidcapo on 2012-05-29
Hi, hello

You need is to first delete the iptables rules completely, ie with **iptables-F** and then add the rules that had before if it is the first time that happens with this is resolved. regards

[www.hostingwebddpyp.com.ar]("http://www.hostingwebddpyp.com.ar")

---

