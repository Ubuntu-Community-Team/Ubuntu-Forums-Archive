---
title: "Traffic Control Problems"
date: 2011-07-18
forum: Server Platforms
---

### Post by liuhb86 on 2011-07-18
Hello,

I want to set up a DNS server and due to cost restrictions, we need to limit the traffic extremely, about 30M bytes/month.

So I used the following command:

tc qdisc add dev eth0 root tbf rate 100bit burst 240mb limit 20kb mtu 1540

That means at 100bps, we can get about 30MB/month, and with a high  burst, unused token can be accumulated so that if the net is idle for a  long time, the following packet can be sent quickly using the  accumulated tokens. 

However it doesn't works. Using tc qdisc ls. I get:

qdisc tbf 8008: dev eth0 root refcnt 2 rate 96bit burst 2293b lat 1515.5s

which means that burst is set to 2293b instead of 240mb. I think the  large burst value with respect to small rate causes a integer overflow.  So I don't know what to do now.

Does anyone know how to do that? 

TIA

liuhb

---

### Post by David006 on 2011-11-17
Did you make any headway with this?


I'm researching a similar issue (with TC as a possible solution) for: **Ubuntu 11.10 (Oneiric)** and **Ubuntu 10.04.3 LTS ..**


( Will report back .. )

---

