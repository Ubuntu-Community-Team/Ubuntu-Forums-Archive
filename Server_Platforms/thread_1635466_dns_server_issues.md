---
title: "dns server issues"
date: 2010-12-01
forum: Server Platforms
---

### Post by cbarron on 2010-12-01
I have a dns server started with 2 NIC Cards in it. The bios sees both cards but they both dont show in ifconfig. is there a way to activate the second card?

---

### Post by Sazhen86 on 2010-12-02
Hi

Is the network interface listed if you type 

cat /proc/net/dev

Is there an entry in /etc/network/interfaces for the second card?

Cheers

---

