---
title: "Nvidia driver install i386 packages on amd64, why?"
date: 2020-10-11
forum: Ubuntu Development Version
---

### Post by Yahoé on 2020-10-11
Having bought a new video card, I installed the latest nvdia-driver from the Ubuntu repos. A whole bunch of i386 packages got installed in the process on this amd64 only. Any idea why, can these packages be safely removed?

---

### Post by CelticWarrior on 2020-10-11
32-bit libraries are often needed for the main purpose of a Nvidia card which is gaming. Keep them.

---

### Post by Yahoé on 2020-10-11
> **CelticWarrior said:**
> 32-bit libraries are often needed for the main purpose of a Nvidia card which is gaming. Keep them.

Thank you @CelticWarrior. This computer is an HTPC, I went ahead and deleted all the unneeded i386 packages installed by nvidia-driver-i386 and my system works without them.

---

