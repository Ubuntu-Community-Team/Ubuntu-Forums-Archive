---
title: "fix label letter to uuid"
date: 2011-07-24
forum: Server Platforms
---

### Post by fizk on 2011-07-24
Is there any somewhat straightforward way of lock the drive letters to certain drives at boot?

I have searched a lot on this and the only thing that have come up is a rather long and complicated way using scripts etc.

A simple fstab example on how to make an uuid to boot at say sda1 everytime and not like now totally random even though I have the same drives in the same places with no portable devices and only a std setup with /boot, /, /home, /swap. +some storage drives.

This uuid creates a havoc on my Truecrypt favorites mounting that relies on labels.

If this is not possible how far back do I have to go get rid of uuid?
I know that 10.04 LTS was working fine at first, is it in the kernel version that it is decided?

Any help is much appreciated!

---

### Post by capscrew on 2011-07-24
> **fizk said:**
> Is there any somewhat straightforward way of lock the drive letters to certain drives at boot?

I have searched a lot on this and the only thing that have come up is a rather long and complicated way using scripts etc.

A simple fstab example on how to make an uuid to boot at say sda1 everytime and not like now totally random even though I have the same drives in the same places with no portable devices and only a std setup with /boot, /, /home, /swap. +some storage drives.

This uuid creates a havoc on my Truecrypt favorites mounting that relies on labels.

If this is not possible how far back do I have to go get rid of uuid?
I know that 10.04 LTS was working fine at first, is it in the kernel version that it is decided?

Any help is much appreciated!
There is no way to use /dev/sdx to ID a Linux partition consistently. This is due to the nature of the kernel's method of enumeration of the partitions.

If UUID is truly causing you problems then you can always apply a *"label"* to the partition.  Assuming you are using the default EXT partition scheme; there are a couple of methods to do this.  I use the command *e2label*.  The man page has the details```
man e2label
```  A quick Google search provides [this]("http://www.cyberciti.biz/faq/linux-partition-howto-set-labels/") reference.

---

### Post by fizk on 2011-07-24
Since the command #e2label /dev/sda1 didn't give anything but a blank line
I don't think that will be a solution. 
(I run it with all but the OS drive pulled out. And /boot with ext2 was on sda1)

So what is the latest kernel/ubuntu server version I can run without this uuid trouble?

It is a backup server only used in LAN running a ftp-server that clients sync to.
Running an old OS is not as important as having many years of data stored on TrueCrypt disks readily available.

---

### Post by capscrew on 2011-07-24
> **fizk said:**
> Since the command #e2label /dev/sda1 didn't give anything but a blank line
I don't think that will be a solution.
The command that you show is used to display the label.  First you have to name the partition (create the label).  Then you can display it.  To name it you do this (as root or using sudo) ```
e2label <device> <LABEL>
```  If I wanted to name /dev/sdd1 as *backup* I would do this```
e2label /dev/sdd1 backup
``` >  
(I run it with all but the OS drive pulled out. And /boot with ext2 was on sda1)

So what is the latest kernel/ubuntu server version I can run without this uuid trouble?
I believe that all Linux kernels using EXT (the Linux native FS) use UUID for consistent ID's. >  

It is a backup server only used in LAN running a ftp-server that clients sync to.
Running an old OS is not as important as having many years of data stored on TrueCrypt disks readily available.
I came from Solaris and was surprised to see UUID's used, but that was 10 years ago.  You might try OpenSolaris.

---

