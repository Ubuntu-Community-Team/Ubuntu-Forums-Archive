---
title: "Server network  card"
date: 2006-06-13
forum: Server Platforms
---

### Post by jitesh on 2006-06-13
installed the server os but I don't think the installation conifigured the network card, How do I see if my network card is functioning on the server and if need be how do I install a network card on Ubuntu Server.

---

### Post by LordHunter317 on 2006-06-13
If the card is up, /sbin/ifconfig will list an entry for it.  dmesg should report it's existance to the kernel.

---

