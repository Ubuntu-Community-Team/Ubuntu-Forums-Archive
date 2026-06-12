---
title: "sysctl / forwarding - conflicting info"
date: 2007-03-28
forum: Server Platforms
---

### Post by jsacksteder on 2007-03-28
Forwarding between interfaces is not activated by default. I have verified this by actually trying to send packets across. I set

net.ipv4.conf.default.forwarding=1

After rebooting,
 cat /proc/sys/net/ipv4/conf/default/forwarding produces '1' indicating that stsctl.conf is being processed. However, forwarding still fails.

I  must "echo 1 > /proc/sys/net/ipv4/ip_forwarding" (note the different path) to get forwarding to start. 

What gives?

---

### Post by Mr. C. on 2007-03-29
Did you create a route entry in your routing table to forward from one network to another ?

IP is a packet forwarding protocol.  No route = no forward.

MrC

---

### Post by Insti on 2007-05-08
The line you actually need in /etc/sysctl.conf is:

net.ipv4.ip_forward=1

I have not looked into why the other line does not work.

---

