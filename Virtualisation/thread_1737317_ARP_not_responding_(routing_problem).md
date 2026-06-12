---
title: "ARP not responding? (routing problem)"
date: 2011-04-23
forum: Virtualisation
---

### Post by capsula4 on 2011-04-23
Hi

I have virtualized a router and ubuntu, and i have a real router (gateway) which is 192.168.1.1

.......... 192.168.100.0/24 ............................ 192.168.1.0/24 ............................
**UBUNTU (.2) -----> (.1) VIRTUALIZED ROUTER (.103) -----> (.1) REAL ROUTER**
.................eth0.......eth0.........................................eth1..............eth0

When ubuntu (192.168.100.2) pings something, the reply never comes back.

I was tcpdumping eth1 of virtualized router and discovered than when REAL ROUTER (192.168.1.1) ARPed for 192.168.100.2, seem he never get any reply from virtualized router (at least that is what I think might be causing the problem). packet forwarding is okay.

What could be the problem?

---

### Post by capsula4 on 2011-04-23
nevermind, I just realized I had to make some static routing on the real router, so it can finds the private networks behind.

im just newbie!

---

