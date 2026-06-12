---
title: "How to separate traffic based on interfaces?"
date: 2014-11-23
forum: Security
---

### Post by carlos80 on 2014-11-23
Hi, 

I have one machine and inside two VM guests (guest1 and guest2).

The host has two interfaces. (eth0 + eth1)

I need to define:
Host uses only eth0
Guest1 uses eth1
Guest2 uses eth0

Is this possible?

What is the best way and have it secured that the traffic from each interface won't mix with each other.

Thanks!

---

### Post by HermanAB on 2014-11-26
Howdy,

You can enforce port to port security with a VLAN.

---

