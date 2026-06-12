---
title: "Load system configuration depending on running virtualized or native"
date: 2010-04-21
forum: Virtualisation
---

### Post by sunside on 2010-04-21
Hi,

I recently installed Ubuntu 10.04 on an external USB2/eSATA disk and during that procedure my graphics card drivers - NVIDIA kernel module, etc. - were correctly installed. Now I booted into windows and created a 'RAW disk' vmdk for VirtualBox and booted my external Ubuntu disk in the VM, which also worked fine.

The problem is that Ubuntu/X now tries to load/use the NVIDIA drivers which, running virtualized, don't work, resulting in flickering and eventually popping up the menu where I can select the fail-safe graphics mode. (Which works.)

The question is: Is it possible to load different configurations of kernel modules / X configurations depending on running the system 'native' or virtualized so that a native boot uses the proprietary drivers while booting in the VM uses the VirtualBox drivers? (And, if yes, how? :))

Best regards,
Markus

---

