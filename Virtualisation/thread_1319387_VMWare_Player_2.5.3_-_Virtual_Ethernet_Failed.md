---
title: "VMWare Player 2.5.3 - Virtual Ethernet Failed"
date: 2009-11-08
forum: Virtualisation
---

### Post by corruptor1972 on 2009-11-08
Hi,

I'm running Kubuntu 9.10 x64, kernel 2.6.31-14-generic.

After getting round the bug in the VMWare 2.5.3 installer I ran:
   sudo vmware-modconfig --console --install-all

All the modules seemed to compile OK but the Virtual Ethernet service fails to start.  Compile logs containing the fail message (gzipped) are attached.  

Naturally then VMs run OK but without networking, which is a bit of a bummer!

Has anyone any ideas?

Ta muchly!

---

### Post by fjgaude on 2009-11-08
I believe you have to re-install using player 3.0, which can handle the massive changes made in Ubuntu 9.10.

---

### Post by corruptor1972 on 2010-08-07
Solved.  Works fine with VMWare 3.  :D

---

