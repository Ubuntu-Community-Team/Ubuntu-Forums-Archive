---
title: "vmware, windows 2000 professional mouse problem"
date: 2008-02-11
forum: Virtualisation
---

### Post by pablosanchezuy on 2008-02-11
Hi there.
I'm using gutsy/amd64 with vmware server 1.04 with windows 2000 professional into it . Actually it runs quite nice, but i face a real problem :
The system was slow, so i began to troubleshoot it : devices, programs, services. Accidentally i started to move the mouse, let's say in circles in the windows vm, both cpu's go 100 % . 
I changed some configs to the mouse device options, but no change.

I use an usb mouse, and pluging it on/off doesnt' make the difference .

The machine is a HP6820s notebook (C2D 2.0 GHZ, 2 GB Ram DDR2-667, HDD 160BG SATA 300)
I tried Windows XP seems to run fine., but Windows 2000 have lesser footprint .

Any hints ?

Regards .

Pablo .

---

### Post by fjgaude on 2008-02-11
VMware v1.0.4 doesn't handle correctly dual-core. Set it to use only one core and everything changes for the better... very fast, quick VMs.

---

### Post by pablosanchezuy on 2008-02-11
thanks for the tip. 

i configured the vm to run with one cpu, but the problem persist, this time on one cpu. I don't know how to figure which cpu is that vm using, but when i move the mouse in circles, one or the other cpu goes under heavy usage.

Regards,
Pablo .

---

### Post by fjgaude on 2008-02-11
Strange... never have seen such before. Try re-booting... can't say if that will have any effect.

Don't know what to suggest.

---

