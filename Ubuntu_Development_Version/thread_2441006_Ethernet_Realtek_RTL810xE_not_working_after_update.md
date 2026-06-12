---
title: "Ethernet Realtek RTL810xE not working after updates"
date: 2020-04-17
forum: Ubuntu Development Version
---

### Post by corradoventu on 2020-04-17
After updates from kernel 5.4.0-21 to 5.4.0-24 ethernet Realtek RTL810xE stopped working
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1873512](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1873512)
Realtek RTL810xE works fine with ubuntu 19.10 and 20.04 with old kernel 5.4.0-21
it works fine also with kernel 5.5.0

---

### Post by cookiecruncher on 2020-04-17
Updated kernel with some other stuff and network not working thereafter. Rebooted to previous kernel and network back up again (24 back to 21)
EDIT: Looks similar to post above :D

```
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 05)
```

---

### Post by corradoventu on 2020-04-18
so if You have a launchpad account please subscribe to my bug - click on 'this bug affects you'

---

### Post by cookiecruncher on 2020-04-20
Kernel [COLOR=#000000]5.4.0-25 not working for me either.[/COLOR]

---

### Post by cookiecruncher on 2020-04-22
Kernel 5.4.0-26 now driving my card and LAN back online.

---

