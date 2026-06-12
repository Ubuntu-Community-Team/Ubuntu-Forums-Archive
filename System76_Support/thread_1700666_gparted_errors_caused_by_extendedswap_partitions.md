---
title: "gparted errors caused by extended/swap partitions"
date: 2011-03-05
forum: System76 Support
---

### Post by StephenDavison on 2011-03-05
My ratu1 was delivered with a 3.5 GB extended partition occupied with one logical partition for swap.  The rest of the 1.5TB drive was consumed by one primary partition formatted as ext4 and mounted on /.  For obvious reasons, I insist on mounting /home from it's own file system.  Gparted is my tool of choice for manipulating disk partitions and this is where I started running into problems.  Every time I tried to resize, move, create or format a partition, gparted failed to perform the operation with an error message stating that libparted couldn't inform the kernel of changes to /dev/sda2 (the swap partition) because the device was busy or something.  I got the same message on /dev/sda5 (the extended partition) after removing the swap space.  Gparted is behaving only after removing the extended partition.  The swap space is now a primary partition.  

At any rate, now I've been able to shrink the root file system and create two more primary partitions (one for another distro/version playground, and one for my /home).  Palimpsest Disk Utility was able to do some of what I wanted, but I still prefer to use gparted.

Now to the questions:

Has anybody else run into this problem?

What is the point of putting swap in an extended partition when there is only one other partition on the drive?  (I must be missing something.)

---

### Post by psusi on 2011-03-05
> **StephenDavison said:**
> For obvious reasons, I insist on mounting /home from it's own file system.

It isn't obvious at all.  Why do you feel this is necessary?

> **StephenDavison said:**
> Every time I tried to resize, move, create or format a partition, gparted failed to perform the operation with an error message stating that libparted couldn't inform the kernel of changes to /dev/sda2 (the swap partition) because the device was busy or something.

You need to unmount the partition to resize it.

---

### Post by StephenDavison on 2011-03-05
To separate user data from the operating system.  Separating /home makes it possible to reinstall the OS without having to restore your data from backup(s).  It also makes it easy if you want to share data across versions/distros without sharing root file systems.  But the most important reason might be to protect your root file system from a full disk.  I leave it at / and /home, but particularly in server environments, it's more common to create additional file systems to protect the root from areas that could potentially fill the disk: /var is a good one.

Gparted disables all the operations I mentioned when a file system is mounted.  And there's no way to unmount the root file system when you're using it.  (I was getting errors, not disabled options.)  I also had swap off.

---

### Post by psusi on 2011-03-05
> **StephenDavison said:**
> To separate user data from the operating system.  Separating /home makes it possible to reinstall the OS without having to restore your data from backup(s).

This is a persistent misconception.  You don't need a separate /home partition to do this; simply don't tick the format box when you reinstall.

> **StephenDavison said:**
> Gparted disables all the operations I mentioned when a file system is mounted.  And there's no way to unmount the root file system when you're using it.  (I was getting errors, not disabled options.)  I also had swap off.

That's why you need to run it from the livecd.  Are you sure you had unmounted everything on the disk?  Something had to have been accessing the disk to cause that error.

---

### Post by StephenDavison on 2011-03-05
> **psusi said:**
> 
That's why you need to run it from the livecd.  Are you sure you had unmounted everything on the disk?  Something had to have been accessing the disk to cause that error.

I was running from the LiveCD.  Nothing mounted and swap off. I suspect it was just a quirk in how the disk was partitioned/imaged during the initial system build.  I only brought it up because I've never run into it before in the many times I've manipulated partitions with gparted.

---

### Post by plumj2.4 on 2011-05-30
> **StephenDavison said:**
> 

Has anybody else run into this problem?

What is the point of putting swap in an extended partition when there is only one other partition on the drive?  (I must be missing something.)

Yes, I've just run into this same problem (I'm not using ubuntu though).  I was using a Parted Magic live CD to run gparted to resize and move an ext3 partition /dev/sda3. It kept failing with a message from libparted "Error informing kernel about modifications to partition /dev/sda5 - Device or resource busy".  /dev/sda5 was a linux-swap logical (extended) partition. My eventual workaround was to go to a command prompt and use fdisk to delete the swap partition then reboot back into the live CD, whereupon gparted then worked as expected (even after recreating the swap partition exactly as it had been before).  Like you I had nothing mounted and swap off (as far as I could tell). My disc was originally partitioned with CrunchBang Linux. Must also be a quirk. 

The point of using an extended partition may be to leave the remaining primary partitions free in case you later need to install an OS that won't work unless it is in a primary partition.

---

