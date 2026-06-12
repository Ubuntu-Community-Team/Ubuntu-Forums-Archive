---
title: "no web cam in dmesg, how to install it in ubuntu 14  vmware player 12 in window 7"
date: 2016-04-14
forum: Virtualisation
---

### Post by zerop2 on 2016-04-14
no web cam in dmesg, how to install it in ubuntu 14 64 bit  vmware player 12 in window 7

i have tired USB 2.0 and USB 3.0 and reboot, still not camera detected

---

### Post by Bucky Ball on 2016-04-14
*Thread moved to **Virtualisation**. *

---

### Post by MAFoElffen on 2016-04-15
In VMWare Player 12, in the VM Manager Window, with that VM highlighted, but not running, under VM settings > USB, see if show all USB devices is checked.

Then, once the VM is re-started, in a terminal, post the output of:
```

sudo lsusb

```
Once player is using that hosts USB ports with USB 1.2, 2.0 & 3.0 compatibility, it should then see those ports and any USB devices connected to them. In Workstation 12, it is in the USB Controller settings for the VM.

---

