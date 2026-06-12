---
title: "UFW log syntax"
date: 2010-09-19
forum: Security
---

### Post by spandey on 2010-09-19
How to interpret UFW logs? Is there any manul or tutorial to understrand format/syntax of UFW logs?

---

### Post by bodhi.zazen on 2010-09-19
The logs are fairly straight forward, post one example you do not understand .

---

### Post by spandey on 2010-09-20
Thanks for help. 
I am new to Linux and no nothing about TCP so trying to learn the ropes. As my DSL is not working wihtout me setting MTU manually, I was suggested to look at Firewall/UFW logs for clues.
For example:Sep 20 15:36:34 spandey-desktop kernel: [ 1944.145762] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=220.225.108.170 DST=117.197.243.67 LEN=48 TOS=0x00 PREC=0x20 TTL=57 ID=35970 DF PROTO=TCP SPT=53391 DPT=9950 WINDOW=5840 RES=0x00 SYN URGP=0 

Sep 20 15:52:00 spandey-desktop kernel: [ 2870.303541] [UFW AUDIT] IN= OUT=ppp0 SRC=117.197.243.67 DST=218.248.255.163 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=52751 DF PROTO=UDP SPT=57548 DPT=53 LEN=42 


What does this mean and how can I interpret others?

---

### Post by bodhi.zazen on 2010-09-20
If you do not understand those logs, you will need to read a bit on networking protocols.

There is not simple short cut, try the introductory sections here :

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

> Sep 20 15:36:34 spandey-desktop kernel: [ 1944.145762] [UFW BLOCK]  IN=ppp0 OUT= MAC= SRC=220.225.108.170 DST=117.197.243.67 LEN=48 TOS=0x00  PREC=0x20 TTL=57 ID=35970 DF PROTO=TCP SPT=53391 DPT=9950 WINDOW=5840  RES=0x00 SYN URGP=0

BLOCK = the connection was blocked
MAC - you MAC
SRC source of packet (by IP address)
DST = destination of packet
LEN = lenght
spt = source port
dpt = destination port

should get you started at least ...

---

### Post by spandey on 2010-09-20
Thank you so much. Will be back once I have digested those stuff..:P

---

### Post by bodhi.zazen on 2010-09-20
> **spandey said:**
> Thank you so much. Will be back once I have digested those stuff..:P

Perfect, it takes a while to digest.

---

