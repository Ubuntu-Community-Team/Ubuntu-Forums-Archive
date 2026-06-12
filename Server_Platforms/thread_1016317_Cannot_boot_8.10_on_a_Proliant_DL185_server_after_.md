---
title: "Cannot boot 8.10 on a Proliant DL185 server after installation"
date: 2008-12-19
forum: Server Platforms
---

### Post by kimovski on 2008-12-19
After finishing the installation of Ubuntu 8.10 server (both 32 and 64bit) everything seems fine in the install and partition of the disks (and cpqarray). But for some reason the boot process after installation get's stuck after PXE with just a black screen with a white cursor blinking up in the left corner.. I read that there are some performance issues with ext3 but I've also tried with reiserfs facing the same problem.. Any suggestions?

---

### Post by Ferret-Simpson on 2008-12-20
Depending on your Generation, you may find hardy works. There are issues with the Intrepid bootloader. Also, isn't PXE Netbooting? It shouldn't be getting that far!

4 DL360's here (A gen1 and 3 Gen2's) none will boot intrepid, Hardy works a treat.

---

