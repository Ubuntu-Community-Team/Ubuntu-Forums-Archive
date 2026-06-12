---
title: "Virtualization of an Ubuntu phisical pc to VmWare Player"
date: 2017-10-17
forum: Virtualisation
---

### Post by cico.sail on 2017-10-17
Hello to all
I have an Ubuntu 14.04 physical PC that before I reformatted it I wold like to virtualize to use in VmWare Player.
I am using VmWare vCenter Converter Stanadlone 6.11 with I have already done the same thing on Windows PCs.
Exceed login problems like root, ssh activation etc. at the step "Destination System" only offers me a VMware infrastructure and not a VMware player format ...
Something wrong?
Does the converter behave differently between Win and Linux?
Regards
Cico.Sail

---

### Post by TheFu on 2017-10-18
I don't know anything about VMware stuff anymore.  Used to be a huge user, before they screwed almost all their customers around 2010-ish (doubled the costs of their tools). Since then, we've avoided all their stuff and take clients to other options.

To move any Linux from physical to virtual, just backup the system and restore it like you would normally do into the VM.  It is best to remove any wacky hardware-specific drivers first - like nvidia/AMD GPU drivers or HW-RAID setups.  But for normal things like NICs, SATA disks, the OS figures out drivers at boot time.

The fstab will need to be manually fixed too - UUIDs change from partition to partition.  I use a live-boot ISO for that.  VMs make that really, really, easy.

If you know what you are doing, all of this will take about 5 minutes after the system is restored, at most.

If there is whole disk encryption, it is best just to perform a fresh installation and use something like **aptik** as the backup/restore tool for your settings, packages, and files.  Encryption always makes backups and restores much more complicated. Using encryption means there is a requirement to have 100% know-you-can-restore backups anyways.

14.04 is kinda old for most desktop uses.  I would take this opportunity to move to 16.04 on a fresh install.  Don't get me wrong, my main desktop is on 14.04 (actually running inside a KVM VM), but if I were moving it, then I would move to a 16.04 setup.

Good luck.  BTW - KVM + virt-manager makes for an extremely fast, stable, virtualization host setup.

---

