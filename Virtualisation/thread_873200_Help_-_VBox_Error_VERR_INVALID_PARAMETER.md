---
title: "Help - VBox Error: VERR_INVALID_PARAMETER"
date: 2008-07-28
forum: Virtualisation
---

### Post by apolloxi on 2008-07-28
So, I looked around for ways to to create a VM for my already-existing Windows XP Partition, and I found this wonderful guide: [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

Everything was working well until I got to step two.

Now, I get this message:

Quote:
sean@sean-laptop:~$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
VirtualBox Command Line Management Interface Version 1.6.2
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

ERROR: VMDK: cannot go backwards for partitioning information in '/home/sean/.VirtualBox/WindowsXP.vmdk'
Error code VERR_INVALID_PARAMETER at /home/vbox/vbox-1.6.2/src/VBox/Devices/Storage/VmdkHDDCore.cpp(251 in function int vmdkCreateRawImage(VMDKIMAGE*, VBOXHDDRAW*, uint64_t)
Error while creating the raw disk VMDK: VERR_INVALID_PARAMETER

Does anyone know what's going on here and how this can be fixed, if it can? I haven't found too many solutions to this problem.

And, can somebody PLEASE respond this time? I made a previous topic about this very same problem about about 40 people viewed and I didn't even get one reply.

---

### Post by apolloxi on 2008-07-29
Anybody?

---

### Post by CameO73 on 2008-07-29
I've some good and some bad news.

The good news is, is that you're problem can be solved by following the instructions in [this thread](http://forums.virtualbox.org/viewtopic.php?t=4501&highlight=ubuntu@ubuntu) (the 6th post; by postfix).

The bad news is, is that this could have some serious consequences, since it changes the partition order. This could mean you have to change some Linux files manually to get things working again. If you're not comfortable with this idea, you should find another way to get a virtual XP machine (e.g. by creating a new VM and installing XP from scratch).

Good luck!

---

### Post by apolloxi on 2008-07-31
Thanks for replying. I appreciate it.

I'll look into this solution.

---

### Post by Sand Lee on 2008-11-22
> **apolloxi said:**
> Thanks for replying. I appreciate it.

I'll look into this solution.

Hey **apolloxi**, I have posted a new version of the tutorial that should fix the problem you experienced.

---

