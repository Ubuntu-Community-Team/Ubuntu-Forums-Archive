---
title: "IBM x3200 Install: Partman Volume Groups"
date: 2008-04-05
forum: Server Platforms
---

### Post by chimaster on 2008-04-05
Hey Everyone.

Debian user first time Ubuntu Install.  I've just received my shiney new (bottom of the range) IBM x3200 M2 Server with Hardware Raid Built in

 (LSILOGIC Mini PCI Raid Card)

I had previously installed Debian Etch AMD64 on it and was planning on running Zimbra. However, Zimbra Network Edition is not supported on Debian and only Ubuntu 6.06 LTS. I figured The install would be as simple (although I pulled my hair out configuring the Broadcom 57xx until I found the tg3 drivers)

Anyways, The Hardware detection on Install was quite slow, it gave up on the Broadcom as I expected which is fine as I can compile the tg3 driver for that and have a 3com PCI if I need anything. It also took a while to find the hardware drivers, it's now moved onto the next stage but has left be with a blank screen.  When I check the syslog in the console I see..

Cat /var/log/syslog
-----
Apr 5 20:33:21 partman: File descriptor 6 left open
Apr 5 20:33:21 partman: Reading all physical volumes. This may Take a while
..
Apr 5 20:33:21 partman:   No volume groups found
-----

Can anyone offer some advice please, I haven't even hit a partition screen yet and am guessing that it's not detecting the RAID card, but... given the my debian install had no issue and picked everything up.. I was hoping... ..??  

Any advice appreciated. Thanks.

---

