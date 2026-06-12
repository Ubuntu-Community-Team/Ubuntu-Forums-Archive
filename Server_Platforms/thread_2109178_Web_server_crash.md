---
title: "Web server crash"
date: 2013-01-26
forum: Server Platforms
---

### Post by bigmonmulgrew on 2013-01-26
Hi guys

Earlier today my web server crashed. I have an android phone app set to check if my website is live every 15 min. The alarm went off at around 18:15.

Its a LAMP server on ubuntu 12.04 running drupal.

The server was completely unresponsive both to web addresses and SSH. After a reboot it appears to be fine but I want to make sure this does no happen again.

Here are the log entries around that time, any other info needed please ask.

syslog
```
Jan 26 19:03:53 MEwebServer kernel: [364839.434669] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=386 TOS=0x00 PREC=0x00 TTL=50 ID=18147 DF PROTO=TCP SPT=52954 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
Jan 26 19:04:46 MEwebServer kernel: [364891.508692] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=567 TOS=0x00 PREC=0x00 TTL=50 ID=45232 DF PROTO=TCP SPT=53015 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
Jan 26 19:04:48 MEwebServer kernel: [364893.513086] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=571 TOS=0x00 PREC=0x00 TTL=50 ID=23727 DF PROTO=TCP SPT=53016 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
Jan 26 19:05:52 MEwebServer kernel: [364957.608402] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=571 TOS=0x00 PREC=0x00 TTL=50 ID=15720 DF PROTO=TCP SPT=53016 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
Jan 26 19:06:56 MEwebServer kernel: [365021.721702] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=571 TOS=0x00 PREC=0x00 TTL=50 ID=13085 DF PROTO=TCP SPT=53016 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
Jan 26 19:37:50 MEwebServer postfix/master[1178]: warning: process /usr/lib/postfix/qmgr pid 1191 exit status 1
Jan 26 19:38:04 MEwebServer postfix/qmgr[15097]: AB109360C87: from=<adminofmywebsite@emailaddress.com>, size=903, nrcpt=1 (queue active)
Jan 26 19:38:23 MEwebServer postfix/qmgr[15097]: 9F076361DD9: from=<adminofmywebsite@emailaddress.com>, size=931, nrcpt=1 (queue active)
Jan 26 19:40:04 MEwebServer CRON[15106]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Jan 26 19:40:10 MEwebServer postfix/qmgr[15097]: 692CD360BD4: from=<adminofmywebsite@emailaddress.com>, size=904, nrcpt=1 (queue active)
Jan 26 19:40:11 MEwebServer CRON[15107]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Jan 26 19:40:11 MEwebServer postfix/qmgr[15097]: 40A1B36267D: from=<adminofmywebsite@emailaddress.com>, size=902, nrcpt=1 (queue active)
Jan 26 19:41:33 MEwebServer postfix/smtp[15101]: AB109360C87: host mailin-03.mx.aol.com[205.188.156.193] said: 421 4.4.2 mtain-dl02.r1000.mx.aol.com Error: timeout exceeded (in reply to end of DATA command)
Jan 26 19:41:44 MEwebServer postfix/smtp[15104]: 9F076361DD9: host mailin-02.mx.aol.com[205.188.190.1] refused to talk to me: 421 4.4.2 mtain-de02.r1000.mx.aol.com Error: timeout exceeded
Jan 26 19:41:45 MEwebServer postfix/smtp[15104]: 9F076361DD9: host mailin-04.mx.aol.com[205.188.103.2] said: 421 4.2.1 :  (DNS:NR)  http://postmaster.info.aol.com/errors/421dnsnr.html (in reply to end of DATA command)
Jan 26 19:41:50 MEwebServer postfix/smtp[15117]: 692CD360BD4: host mx00.gmx.net[213.165.67.114] refused to talk to me: 554-gmx.net (mxgmx007) Nemesis ESMTP Service not available 554-No SMTP service 554 invalid DNS PTR resource record
Jan 26 19:42:53 MEwebServer postfix/smtp[15119]: 40A1B36267D: host mailin-03.mx.aol.com[64.12.137.161] said: 421 4.2.1 :  (DNS:NR)  http://postmaster.info.aol.com/errors/421dnsnr.html (in reply to end of DATA command)
```

1-kern.log
```
Jan 26 17:53:48 MEwebServer kernel: [360633.503236] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=119.246.10.196 DST=192.168.0.200 LEN=60 TOS=0x00 PREC=0x00 TTL=46 ID=44907 DF PROTO=TCP SPT=3463 DPT=23 WINDOW=5840 RES=0x00 SYN URGP=0 
Jan 26 19:03:53 MEwebServer kernel: [364839.434669] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=386 TOS=0x00 PREC=0x00 TTL=50 ID=18147 DF PROTO=TCP SPT=52954 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
Jan 26 19:04:46 MEwebServer kernel: [364891.508692] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=567 TOS=0x00 PREC=0x00 TTL=50 ID=45232 DF PROTO=TCP SPT=53015 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
Jan 26 19:04:48 MEwebServer kernel: [364893.513086] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=571 TOS=0x00 PREC=0x00 TTL=50 ID=23727 DF PROTO=TCP SPT=53016 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
Jan 26 19:05:52 MEwebServer kernel: [364957.608402] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=571 TOS=0x00 PREC=0x00 TTL=50 ID=15720 DF PROTO=TCP SPT=53016 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
Jan 26 19:06:56 MEwebServer kernel: [365021.721702] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=571 TOS=0x00 PREC=0x00 TTL=50 ID=13085 DF PROTO=TCP SPT=53016 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
```

ufw.log
```
Jan 26 19:03:53 MEwebServer kernel: [364839.434669] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=386 TOS=0x00 PREC=0x00 TTL=50 ID=18147 DF PROTO=TCP SPT=52954 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
Jan 26 19:04:46 MEwebServer kernel: [364891.508692] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=567 TOS=0x00 PREC=0x00 TTL=50 ID=45232 DF PROTO=TCP SPT=53015 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
Jan 26 19:04:48 MEwebServer kernel: [364893.513086] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=571 TOS=0x00 PREC=0x00 TTL=50 ID=23727 DF PROTO=TCP SPT=53016 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
Jan 26 19:05:52 MEwebServer kernel: [364957.608402] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=571 TOS=0x00 PREC=0x00 TTL=50 ID=15720 DF PROTO=TCP SPT=53016 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
Jan 26 19:06:56 MEwebServer kernel: [365021.721702] [UFW BLOCK] IN=eth0 OUT= MAC=00:24:1d:66:65:be:2c:b0:5d:8d:79:76:08:00 SRC=86.168.14.8 DST=192.168.0.200 LEN=571 TOS=0x00 PREC=0x00 TTL=50 ID=13085 DF PROTO=TCP SPT=53016 DPT=80 WINDOW=33304 RES=0x00 ACK PSH FIN URGP=0 
```

---

