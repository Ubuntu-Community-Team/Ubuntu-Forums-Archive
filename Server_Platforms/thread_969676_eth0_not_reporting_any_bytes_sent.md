---
title: "eth0 not reporting any bytes sent"
date: 2008-11-03
forum: Server Platforms
---

### Post by chadoe on 2008-11-03
Hi, I installed ubuntu server 8.10, lamp & email on my home server. Everything is working good except when I want to monitor the bandwidth used it always reports 0 bytes sent, received bytes seems to be ok.

This is the output from ifconfig eth0:> eth0      Link encap:Ethernet  HWaddr 00:21:97:8a:2f:a5
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:97ff:fe8a:2fa5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84967 errors:0 dropped:0 overruns:0 frame:0
          [COLOR="Red"]TX packets:111845[/COLOR] errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:7942679 (7.9 MB)  [COLOR="Red"]TX bytes:0 (0.0 B)[/COLOR]
          Memory:febc0000-fec00000

Any ideas?

---

