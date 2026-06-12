---
title: "Install Ubuntu 18.04 on VirtualBox 5.2 leaves Ubuntu not bootable"
date: 2018-04-10
forum: Virtualisation
---

### Post by sr712 on 2018-04-10
If I install Ubuntu 18.04 daily build on Virtualbox 5.2 (on Ubuntu 16.04, Kernel 4.15.16) with following parameters:
- 4096MG, 674MB Video RAM, 2 CPU - English, German Keyboard, Vienna, Default Partitioning, 3rd Party Tools
the system finsihes to install but can't boot after that.
If I boot then with pressed Shift Key and press "e"  and delete the boot parameters "quiet splash" the system boots without problem?
Later I have to modify the /etc/default/grub  and do update-grub
There is no EFI enabled in VirtualBox.

What's wrong?

---

### Post by wildmanne39 on 2018-04-10
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by sr712 on 2018-04-10
A fried told me the solution. I had kernel 4.15 then 4.15 on my host system. When I changed back to 4.13 from xenial hwe package it works without any problems.

---

### Post by Whoopie on 2018-04-11
> **sr712 said:**
> A fried told me the solution. I had kernel 4.15 then 4.15 on my host system. When I changed back to 4.13 from xenial hwe package it works without any problems.

You can also disable Wayland in /etc/gdm3/custom.conf by uncommenting "WaylandEnable = false". Afterwards, the system boots fine here with the default kernel 4.15.

---

