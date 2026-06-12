---
title: "Ultra 5-10 Network failure"
date: 2008-02-28
forum: Sun Sparc Users
---

### Post by oh nuts am I crazy on 2008-02-28
When I look at lsmod it does not show the ethernet cards but lspci shows the happymeal cards I cannot update until I figure out how to get the ethernet working can anyone asst me

When I typ ifconfig -a the ethrenet card are there but renamed and both with the same MAC address

Looked in /etc/network/interfaces found
auto lo


Added auto eth1 and restarted networking and I am up 
Thanks to the guys that worked a problem on PClinux I found the answer.

---

