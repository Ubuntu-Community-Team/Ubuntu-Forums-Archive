---
title: "multiple remote desktop connections, help?"
date: 2007-05-15
forum: Windows
---

### Post by zachtib on 2007-05-15
I realize that this isn't exactly a windows support forum, but I hope that someone here might have an idea...


Here's the situation.  I have one external IP address for my house, and both myself and a housemate have an XP machine behind our router on the local network.  We both want to be able to connect remotely using RDP, but with port forwarding we can only forward the port to one computer.

We both have separate domainnames that resolve to our IP, so I was wondering if there's any way to use name based resolution for the RDP connection.  Have one domain forward to computer A, the other to computer B.

---

### Post by chrono310 on 2007-09-05
Eh, I dunno that you can do it that way. A lot of routers will let you forward different outside ports to the same port on different internal IPs. If you don't want to buy another router, perhaps you could change the port that Windows listens to for incoming RDP connections?

---

### Post by thelinuxguy on 2007-09-06
> **chrono310 said:**
> A lot of routers will let you forward different outside ports to the same port on different internal IPs.

Confirm chono's solution. Have it working on my side. Forward 2 ports on your router to 3389 on the 2 machines.

---

