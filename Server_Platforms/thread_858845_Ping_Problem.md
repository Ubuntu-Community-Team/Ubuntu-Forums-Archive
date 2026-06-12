---
title: "Ping Problem"
date: 2008-07-14
forum: Server Platforms
---

### Post by FeNCinGeR on 2008-07-14
Hello,

I have made small Wireless Access Point network which consist of 9 (Linksys WAP2000) AP. 

So then I made up a server for monitoring them based on Ubuntu 8.04 LTS Server Edition. Running Smokeping and Cacti.

But then actually comes the problem. Server loses the ping in Ethernet on Ubuntu machine, but when I try to ping devices from machine running on Windows XP everything is fine - i tried to put Linux and Windows machine both on 24h test sending ping on all Wireless AP. So in the end Windows XP machine has no error, while Linux loses ping all the time.

I tried to change network cards, even reinstall system and on fresh copy of ubuntu server system it make the same when you write for example 192.168.1.1 It loses ping anyway. 

Does anyone have idea what's the problem and how to solve it?

---

### Post by windependence on 2008-07-14
Are you pinging them using the IP address or the DNS name?

-Tim

---

### Post by FeNCinGeR on 2008-07-14
IP address 

both server and WAP are on the same subnet:
192.168.1.xxx

---

### Post by FeNCinGeR on 2008-07-14
Nobody have no idea ? :confused:

---

