---
title: "constant BSODs in vmware server"
date: 2008-09-20
forum: Virtualisation
---

### Post by Matt26 on 2008-09-20
i have vmware server setup under ubuntu 8.04.  i originally started out with v1.0.5 (which i have just recently upgraded to 1.0.7 build 10231) and a virtual machine of windows xp sp3.  i started getting BSODs in the windows xp VM so i decided to reformat the vm and reinstall windows xp- after i completely reinstalled windows xp i continued to get BSODs.  so i removed the xp VM and created a completely new virtual disk and then installed windows vista ultimate sp1- same thing happened there as well, more BSODs.  i just recently reinstalled vista again completely and ran into another BSOD again, and i'm really confused as to why this keeps happening.

unfortunately i don't have the technical details on the BSODs i am getting (i just recall that each time it performs a physical memory dump before restarting the VM) but i find it weird that this continues to happen even after the OS has been completely reinstalled a number of times and the virtual disk has been completely recreated as well.

does anyone have any ideas as to why this might be happening?

thanks.

---

### Post by frogotronic on 2008-11-05
> **Matt26 said:**
> i have vmware server setup under ubuntu 8.04.  i originally started out with v1.0.5 (which i have just recently upgraded to 1.0.7 build 10231) and a virtual machine of windows xp sp3.  i started getting BSODs in the windows xp VM so i decided to reformat the vm and reinstall windows xp- after i completely reinstalled windows xp i continued to get BSODs.  so i removed the xp VM and created a completely new virtual disk and then installed windows vista ultimate sp1- same thing happened there as well, more BSODs.  i just recently reinstalled vista again completely and ran into another BSOD again, and i'm really confused as to why this keeps happening.

unfortunately i don't have the technical details on the BSODs i am getting (i just recall that each time it performs a physical memory dump before restarting the VM) but i find it weird that this continues to happen even after the OS has been completely reinstalled a number of times and the virtual disk has been completely recreated as well.

does anyone have any ideas as to why this might be happening?

thanks.

same problem after upgrading to 2.0 - I think it has to do with the "hardware" change.  In other words, the change in the virtualization environment

---

