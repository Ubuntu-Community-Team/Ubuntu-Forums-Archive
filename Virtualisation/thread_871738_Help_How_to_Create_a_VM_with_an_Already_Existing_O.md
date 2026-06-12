---
title: "Help: How to Create a VM with an Already Existing OS"
date: 2008-07-27
forum: Virtualisation
---

### Post by apolloxi on 2008-07-27
***EDIT***

So, I looked around for ways to to create a VM for my already-existing Windows XP Partition, and I found this wonderful guide: [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

Everything was working well until I got to step two.

Now, I get this message:

> sean@sean-laptop:~$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
VirtualBox Command Line Management Interface Version 1.6.2
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

ERROR: VMDK: cannot go backwards for partitioning information in '/home/sean/.VirtualBox/WindowsXP.vmdk'
Error code VERR_INVALID_PARAMETER at /home/vbox/vbox-1.6.2/src/VBox/Devices/Storage/VmdkHDDCore.cpp(2518) in function int vmdkCreateRawImage(VMDKIMAGE*, VBOXHDDRAW*, uint64_t)
Error while creating the raw disk VMDK: VERR_INVALID_PARAMETER


Does anyone know what's going on here and how this can be fixed, if it can? I haven't found too many solutions to this problem.

---

### Post by apolloxi on 2008-07-27
...Anybody, please?

---

### Post by apolloxi on 2008-07-27
...ANYBODY?

I hate to keep posting in my own topic, but I would really like some help with this. If somebody could take some time to actually respond with some help and not just view my topic, I'd appreciate it greatly.

---

