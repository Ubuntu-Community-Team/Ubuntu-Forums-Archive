---
title: "Remove UFW Block from kern.log and sys.log"
date: 2016-11-30
forum: Server Platforms
---

### Post by neodjandre on 2016-11-30
Using Nginx, Wordpress and Ubuntu 16.
I am constantly bombarded with these messages in kern.log , syslog and ufw.log
```
Nov 28 21:02:28 kernel: [246817.450026] [UFW BLOCK] IN=eth0 OUT= MAC=xx.xx SRC=122.3.133.77 DST=xx.xx LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=22334 DF PROTO=TCP SPT=45750 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
Nov 28 21:02:31 kernel: [246820.443191] [UFW BLOCK] IN=eth0 OUT= MAC=xx.xx SRC=122.3.133.77 DST=xx.xx LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=22335 DF PROTO=TCP SPT=45750 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
Nov 28 21:02:33 kernel: [246822.448520] [UFW BLOCK] IN=eth0 OUT= MAC=xx.xx SRC=195.154.181.110 DST=xx.xx LEN=40 TOS=0x00 PREC=0x00 TTL=246 ID=6401 PROTO=TCP SPT=52845 DPT=8709 WINDOW=1024 RES=0x00 SYN URGP=0 
Nov 28 21:02:37 kernel: [246826.438721] [UFW BLOCK] IN=eth0 OUT= MAC=xx.xx SRC=122.3.133.77 DST=xx.xx LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=22336 DF PROTO=TCP SPT=45750 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
Nov 28 21:03:26 kernel: [246875.605969] [UFW BLOCK] IN=eth0 OUT= MAC=xx.xx SRC=89.163.146.88 DST=xx.xx LEN=444 TOS=0x00 PREC=0x00 TTL=59 ID=45590 DF PROTO=UDP SPT=5149 DPT=5060 LEN=424 
Nov 28 21:03:41 kernel: [246890.099144] [UFW BLOCK] IN=eth0 OUT= MAC=xx.xx SRC=82.81.171.85 DST=xx.xx LEN=44 TOS=0x00 PREC=0x00 TTL=56 ID=19683 PROTO=TCP SPT=63561 DPT=2323 WINDOW=58193 RES=0x00 SYN URGP=0 
Nov 28 21:03:46 kernel: [246895.517766] [UFW BLOCK] IN=eth0 OUT= MAC=xx.xx SRC=94.102.49.174 DST=xx.xx LEN=40 TOS=0x00 PREC=0x00 TTL=249 ID=2066 PROTO=TCP SPT=51511 DPT=8000 WINDOW=1024 RES=0x00 SYN URGP=0 
Nov 28 21:03:49 kernel: [246898.714239] [UFW BLOCK] IN=eth0 OUT= MAC=xx.xx SRC=61.240.144.65 DST=xx.xx LEN=40 TOS=0x00 PREC=0x00 TTL=236 ID=31567 PROTO=TCP SPT=46807 DPT=8009 WINDOW=1024 RES=0x00 SYN URGP=0 
Nov 28 21:04:14 kernel: [246923.959948] [UFW BLOCK] IN=eth0 OUT= MAC=xx.xx SRC=163.172.91.185 DST=xx.xx LEN=40 TOS=0x08 PREC=0x00 TTL=243 ID=54321 PROTO=TCP SPT=47175 DPT=22 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov 28 21:04:31 kernel: [246940.250298] [UFW BLOCK] IN=eth0 OUT= MAC=xx.xx SRC=78.168.185.115 DST=xx.xx LEN=40 TOS=0x00 PREC=0x00 TTL=51 ID=62125 PROTO=TCP SPT=52008 DPT=7547 WINDOW=13555 RES=0x00 SYN URGP=0 
```

[LIST=1]
[*]Since these are already logged in ufw.log how can i stop them from appearing at kern.log and syslog ?
[*]Is there something I must do to prevent these attacks or is this normal for a server to experience?

many thanks!
[/LIST]

---

### Post by howefield on 2016-11-30
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by kpatz on 2016-11-30
Any server exposed to the internet is going to get scanned, a lot.  That's what the firewall is there for.  You could reconfigure ufw to not log blocked attempts, or if you just want to stop them from landing in kern.log, edit the file /etc/syslog.d/20-ufw.conf and uncomment the last line that says "& stop".

So instead of:
```
# Log kernel generated UFW log messages to file
:msg,contains,"[UFW " /var/log/ufw.log

# Uncomment the following to stop logging anything that matches the last rule.
# Doing this will stop logging kernel generated UFW log messages to the file
# normally containing kern.* messages (eg, /var/log/kern.log)
#& stop

```

you'd have:
```
# Log kernel generated UFW log messages to file
:msg,contains,"[UFW " /var/log/ufw.log

# Uncomment the following to stop logging anything that matches the last rule.
# Doing this will stop logging kernel generated UFW log messages to the file
# normally containing kern.* messages (eg, /var/log/kern.log)
& stop
```

---

### Post by neodjandre on 2016-11-30
many thanks! do you think disabling ufw logging is better?

---

### Post by kpatz on 2016-11-30
Unless you want to keep logs of every random bot and script kiddie that scans your IP looking for ways in, I'd just disable the logging.

---

