---
title: "Can't Create Guest OS onto a Non Primary Hard Drive"
date: 2009-05-04
forum: Virtualisation
---

### Post by DocEsq on 2009-05-04
I have been dabbling with Ubuntu and Kubuntu for about a year now while dual booting with XP.  I have installed the latest version of VirtualBox which I can start from the Terminal (for whatever reason it does not show up in Applications).  When I try to create the Guest OS so as to install XP, it does not let me place it on one of my other hard drives or partitions.

I have Ubuntu/Kubuntu installed on a 14GB IDE drive.  I have another 250GB hard drive which is partitioned and holds Windows XP and to which I can boot to when needed.  I have two other partitions on this desk which have enough free space to handle a guest OS.  I also have a 300GB SATA drive connected.  The SATA and the other IDE drive (which has XP) are both formatted as FAT32 if that means anything to my problem.

When trying to create the Guest OS Virtual Hard Drive, I can only save it on the 14GB drive that holds Ubuntu/Kubuntu.  I do not see my other hard drives or partitions at all.

If I try to create a 10GB Virtual Hard Drive on to my drive the process fails which makes sense since there is not enough physical free space on the drive.

How can I create the Virtual Hard Drive and save it upon creation onto another hard drive.

If this can not be done then I will need to reinstall Ubuntu onto a bigger drive which I would rather not do since I would loose all of the tweaking I have done to get things to work the way I want.

Any help would be appreciated.

FYI, a google search did not turn up anything on this issue that I could find.

Thanks.

DocEsq

---

### Post by dcstar on 2009-05-06
> **DocEsq said:**
> I have been dabbling with Ubuntu and Kubuntu for about a year now while dual booting with XP.  I have installed the latest version of VirtualBox which I can start from the Terminal (for whatever reason it does not show up in Applications).  When I try to create the Guest OS so as to install XP, it does not let me place it on one of my other hard drives or partitions.

I have Ubuntu/Kubuntu installed on a 14GB IDE drive.  I have another 250GB hard drive which is partitioned and holds Windows XP and to which I can boot to when needed.  I have two other partitions on this desk which have enough free space to handle a guest OS.  I also have a 300GB SATA drive connected.  The SATA and the other IDE drive (which has XP) are both formatted as FAT32 if that means anything to my problem.
.........

FAT filesystems are **useless** as they do not support security attributes required by Linux. Create Linux filesystems and mount them and the problem should go away.

---

### Post by DocEsq on 2009-05-06
Getting rid of FAT is not an option at this time since I Dual Boot and need to be able to access the FAT partitions in both Windows and Ubuntu/Linux..

Is there another option I can do?

DocEsq

---

