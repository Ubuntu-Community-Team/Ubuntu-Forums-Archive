---
title: "Network slowness"
date: 2008-06-22
forum: Server Platforms
---

### Post by michellez on 2008-06-22
Hi Guys,

This started off with me experiencing Samba slowness. After reading and trying various things round the forums I decided to try a different NIC.

I was using an Intel Pro 100 PCI NIC (eth0). Then changed to the onboard 3COM NIC (Dell box) (eth1).

01:08.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

Now it's even worse. SSH and VNC are useless. Anything across the network is useless on it, HTTP, you name it. Useless as in it happens eventually, most of the time, but is painfully slow. VNC you just get a small fraction of the screen though. SSH just locks for ages. HTTP just sits there for ever and hopefully you'll get a page served (tends more likely to work the smaller the page is..).

If you're on the machine and say downloading things, it's fine though!

Have I missed something somewhere and all the services are trying to use eth0 still instead of eth1 for example?

All I did was swap the configuration around in /etc/network/interfaces for the two interfaces.

Thanks,
Michellez

---

### Post by cariboo on 2008-06-23
Have you pull the intel nic out, to see if it makes any difference?

Jim

---

### Post by artesvida on 2008-06-23
Did you change out your cables?

Sorry if this is a bog-obvious, of-course-I-tried-that-do-you-think-I'm-stupid suggestion, but I've pulled my hair out over slow/flaky network issues only to find out that one of the cables was bad.

---

