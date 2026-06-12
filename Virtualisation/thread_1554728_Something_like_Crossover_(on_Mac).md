---
title: "Something like Crossover (on Mac)"
date: 2010-08-17
forum: Virtualisation
---

### Post by darukka on 2010-08-17
Is there a possibility to use install a Windows System on a real partition and then access the OS directly (DualBoot) and inside my Ubuntu System with Virtual Box? Has anyone managed to do it?

I have my Ubuntu System set up so far, and I have a 50 GB NTFS partition reserved for my Windows Installation. I could create a .vmdk that links to the specific partition.

```
sudo VBoxManage internalcommands createrawvmdk -filename ./WinXP.vmdk -rawdisk /dev/sda3
```

I have quite some problems with the installation actually because VirtualBox is executed as a user and the partition can only be accessed by root. Anyone has some ideas?

---

