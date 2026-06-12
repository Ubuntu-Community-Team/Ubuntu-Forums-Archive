---
title: "Seeing data in raw disk from virtualized windows"
date: 2007-12-20
forum: Virtualisation
---

### Post by NellyvdH on 2007-12-20
I have a problem with sharing files between the host (Linux Ubuntu) and the guest system (Windows 98). I put the data to be shared system disk partition of the host (FAT32). I can make that partition partly readable by the guest system (making a .vdmk file for raw data access in VirtualBox or using "qemu -hdb /dev/hdb -hda file.img ..." in QEMU). The problem is that both virtualisation programs can see the content of only some of the folders/directories on my hard disk partition but not of most of the other folders/directories. I have looked at differences between the two types of directories, but under the LINUX host they all have the same owner and usergroup and the same settings for using the directories.

---

