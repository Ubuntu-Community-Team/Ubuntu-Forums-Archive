---
title: "UFW log have a LOTs of &quot;UFW BLOCK INPUT&quot;"
date: 2008-05-30
forum: Security
---

### Post by hkbruvold on 2008-05-30
When I run:
```
grep UFW /var/log/syslog
```

I get about 1000 lines from the log...


here is an example:

> May 30 23:29:37 hk-laptop kernel: [21293.571203] [UFW BLOCK INPUT]: IN=wlan0 OUT= MAC=00:13:02:9c:0a:ec:00:xx:xx:xx:xx:xx:xx:xx SRC=125.211.198.24 DST=79.136.xxx.xxx LEN=485 TOS=0x00 PREC=0x00 TTL=41 ID=0 DF PROTO=UDP SPT=41645 DPT=1026 LEN=465


What does this mean?
Does it shows when someone tries to access my pc? (in that case I'm very popular)

Why does the log contain that many "UFW BLOCK INPUT"s?

---

### Post by Monicker on 2008-05-30
Most likely its an attempt to deliver "popup" spam to a Windows machine via the messenging service.  Its pretty common.  I also see lots of it in my home router logs.


```
  23082 UDP:1026
  21802 UDP:1027
  16196 TCP:57470
   6876 UDP:1028
   2429 UDP:10089
   2357 UDP:30757
   1762 TCP:23163
   1754 UDP:35462
   1417 TCP:10089
   1042 UDP:33436
   1012 UDP:47008
    988 TCP:30757
    747 UDP:23163
    720 TCP:26736
    648 TCP:8080
    509 TCP:8000
    494 TCP:7212
    430 TCP:2967
    420 TCP:1080
    416 TCP:5900
```

---

### Post by hkbruvold on 2008-05-30
ok, thank you.

I tried to find out what port these where blocked from, and it was things like epmap, Microsoft SQL Server, Microsoft SQL Monitor.

I haven't searched the whole list, but anyway Thanks :)

---

### Post by SerafeimG on 2010-09-08
I have also many "UFW block" messages in my log files when I am connected to the internet through a wired connection. I think this slows down my internet connection. Sometimes for some minutes I can not even load pages.
How can I fix this problem?

---

