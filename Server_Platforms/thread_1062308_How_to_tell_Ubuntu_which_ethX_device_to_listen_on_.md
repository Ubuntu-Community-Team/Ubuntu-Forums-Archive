---
title: "How to tell Ubuntu which ethX device to listen on for DHCP"
date: 2009-02-06
forum: Server Platforms
---

### Post by Go_Big_Blue on 2009-02-06
Okay - had a problem with a Zonet ethernet card and getting the driver to load, so I changed out the card to a Netgear GA311 ethernet card.  did the whole modprobe thing, and got it up and running.  But I don't remember what file it is that I need to go in and edit to tell the DHCP server to listen to this ethernet adapter.  The Zonet card was on eth1, but now the Netgear card (in the same slot as the Zonet) is on eth2.  

I can remember the syntax, but don't know what file it is in to edit it.  Anyone?

---

### Post by inphektion on 2009-02-06
I think
 /etc/defaults/dhcp3-server
then the interfaces= line

---

### Post by Go_Big_Blue on 2009-02-06
Thanks. but that wasn't the right file. Still can't seem to find the right file.

---

### Post by mregister on 2009-02-06
nano /etc/network/interfaces

---

