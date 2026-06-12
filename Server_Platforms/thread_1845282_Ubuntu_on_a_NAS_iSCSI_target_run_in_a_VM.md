---
title: "Ubuntu on a NAS iSCSI target run in a VM ?"
date: 2011-09-16
forum: Server Platforms
---

### Post by BakaOnigiri on 2011-09-16
Hello,

I have a little problem, I need to install Ubuntu LTS 10.04 in a VM (VMWare Fusion) but with the drive setup as a iSCSI target (shared by a Synology NAS).


Everything went fine during the setup (normal boot on the iso in the VM), setup of the iSCSI target went fine too, until it had to reboot.


For the reboot, the iso of the install CD is disabled in the VM, and as there is no hard drive, it try to boot via PXE.

But I don't have PXE.

I understand that the problem is that the drive information (where to find the iSCSI target) is somewhere in the /boot folder, and that it is a cyclic problem.


What is the minimalist and good way to tell the VM that the boot is in the iSCSI target ?


Thanks for all.

Regards.

---

