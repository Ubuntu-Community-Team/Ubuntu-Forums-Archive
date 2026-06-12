---
title: "UFW output written to console..."
date: 2009-04-20
forum: Server Platforms
---

### Post by jimxms on 2009-04-20
Hi peeps,

I just installed 3 servers today running 8.04 and enabled UFW on them. However for some reason this evening two of them have started writing what appears to be output from UFW to the screen:

[18793.990541] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=xx:0c:82:xx:bf:ce:00:c0:9f:3d:0b:52:xx:00 SRC=xxx.xx.xx.24 DST=xxx.xx.xx.83 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=81 DF PROTO=UDP SPT=53879 DPT=32006 LEN=32 
[18796.796167] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=xx:0c:82:xx:bf:ce:00:1a:92:98:7f:64:xx:00 SRC=xxx.xx.xx.85 DST=xxx.xx.xx.83 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=30785 DF PROTO=TCP SPT=3701 DPT=5900 WINDOW=65535 RES=0x00 SYN URGP=0 
[18799.912867] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=xx:0c:82:xx:bf:ce:00:1a:92:98:7f:64:xx:00 SRC=xxx.xx.xx.85 DST=xxx.xx.xx.83 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=2751 DF PROTO=TCP SPT=3701 DPT=5900 WINDOW=65535 RES=0x00 SYN URGP=0 
[18805.851674] [UFW BLOCK INPUT]: IN=eth1 OUT= MAC=xx:0c:82:xx:bf:ce:00:1a:92:98:7f:64:xx:00 SRC=xxx.xx.xx.85 DST=xxx.xx.xx.83 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=14039 DF PROTO=TCP SPT=3701 DPT=5900 WINDOW=65535 RES=0x00 SYN URGP=0 

This kind of output is just spamming the screen constantly, but the servers are working fine aside from this.

A restart of UFW gets rid of it for a short while. Any ideas?

---

### Post by jimxms on 2009-04-21
Nobody? Or am I missing something really obvious? If so, please humour me...

---

