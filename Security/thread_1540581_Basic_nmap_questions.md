---
title: "Basic nmap questions"
date: 2010-07-28
forum: Security
---

### Post by methodtwo on 2010-07-28
Hi
If i did an nmap port scan from inside my home LAN, would i get a different result from people scanning from outside?.If so how would i obtain the results that everyone else sees.Could i just do:
```
$sudo nmap external_ip_address
```
to get what others would see from outside my LAN?
Thank you for your time
regards

---

### Post by methodtwo on 2010-07-28
So basically should nmap-online give a different result as scanning from inside the LAN?

---

### Post by HPD2 on 2010-07-28
There is a website that will use nmap to scan your system, if i remember correctly. Yes if you are behind a router then the external nmap scan will look different to an internal one.
*edit* You can use _[Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2")_ to scan your system.

---

### Post by yeleek on 2010-07-28
nmap-online can be used to perform custom scans - need to know the parameters you want.
[http://nmap-online.com/](http://nmap-online.com/)

As for if you scanned from your LAN outwards to an external address, depends very much on the configuration of your LAN and what FW rules etc you have.

---

### Post by bodhi.zazen on 2010-07-28
> **methodtwo said:**
> So basically should nmap-online give a different result as scanning from inside the LAN?

Assuming you have a router, nmap (or similar) from external will scan your router.

If you use nmap on your LAN from a second machine you are scanning your interface (eth0).

If you use nmap on you local machine you are scanning the loop back interface (lo).

Edit: If you stop for a minute and review your network architecture and the route packets take the above should make perfect sense.

---

