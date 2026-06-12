---
title: "Issue mounting Office 2007 for Virtualbox Installation"
date: 2008-03-26
forum: Virtualisation
---

### Post by dcianf on 2008-03-26
I am trying to ditch my dual-boot altogether and run a virtual windows machine for office 2007.  I currently have a working windows XP machine virtualized.

My problem is that Ubuntu will not mount the dvd for me to pass to the virtual machine running on virtualbox.  I have tried it both with the passthrough enabled and disabled, and I have tried mounting it in the Ubuntu console, but nothing I have tried can mount the dvd.  It just says "No Medium Found"

Yes it is an official version of office 2007 (student edition).

Any advice?

---

### Post by keratos on 2008-03-26
> **dcianf said:**
> I am trying to ditch my dual-boot altogether and run a virtual windows machine for office 2007.  I currently have a working windows XP machine virtualized.

My problem is that Ubuntu will not mount the dvd for me to pass to the virtual machine running on virtualbox.  I have tried it both with the passthrough enabled and disabled, and I have tried mounting it in the Ubuntu console, but nothing I have tried can mount the dvd.  It just says "No Medium Found"

Yes it is an official version of office 2007 (student edition).

Any advice?

have you enabled the DVD in the virtualbox machine settings, before the machine is powered on .... ie powered down.

---

### Post by dcianf on 2008-03-26
Yes I have, I also installed the operating system from the same drive.

On another note, I also can confirm that the dvd worked fine when this computer still booted windows.

---

### Post by Jovec on 2008-03-26
> **dcianf said:**
> I am trying to ditch my dual-boot altogether and run a virtual windows machine for office 2007.  I currently have a working windows XP machine virtualized.

My problem is that Ubuntu will not mount the dvd for me to pass to the virtual machine running on virtualbox.  I have tried it both with the passthrough enabled and disabled, and I have tried mounting it in the Ubuntu console, but nothing I have tried can mount the dvd.  It just says "No Medium Found"

Yes it is an official version of office 2007 (student edition).

Any advice?

Having no specific knowledge of your problem, you could try creating an ISO of the Office CD, then having the VM mount that off the HDD.

---

### Post by Red Shift on 2008-03-26
It can be hit or miss to get VirtualBox to recognize the host CD/DVD-ROM drive.

I "solved" this problem by mounting and unmounting the drive in VirtualBox -> Details -> CD/DVD-ROM and starting then ending the virtual machine until the CD was recognized.

I also mounted then unmounted the drive while the guest OS was running until the CD was recognized.

This method is completely non-technical, but you may catch a break.

---

### Post by keratos on 2008-03-27
Does it work if you start with the VM off, insert a CD, turn on the VM and mount the CDROM in the VM?

If not, with the VM on and CD mounted (or at least you've tried to)..
post output of
```
ls -l /dev/cdrom*
cat /etc/fstab
mount
```

---

### Post by dcianf on 2008-03-30
```
dan@dan-ubuntu:~$ ls -l /dev/cdrom*
lrwxrwxrwx 1 root root 4 2008-03-30 21:33 /dev/cdrom -> scd0
dan@dan-ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=38242738-e557-4e7f-aedf-253948db8d87 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9C6485FF6485DC80 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=AC3C485C3C4823A4 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=5BE1B4336D955300 /media/sdb2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=7bbcbd5a-f394-48f9-8cf5-1c27d49bdfa4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

I'm not quite sure what that does, but it worked.  The disk mounted for the first time in Ubuntu, and in the virtual machine. 

Thanks!

---

### Post by keratos on 2008-04-07
Sorry but I cannot take the credit for this!

It shouldn't have "done" anything. It was only intended to retrieve information and is passive, nothing should have changed.

Purely coincidental that it caused your CDROM to be recongised correctly.

You must have, unwittingly, done something different.

---

### Post by glacialfury on 2008-09-11
He's not alone in this.  I, too, received a student edition of MSOffice 2007; the disc loads perfectly fine in Windows, but inserting the disc on Ubuntu, the system doesn't automount the disc like it would any other.  Because Ubuntu doesn't see it, I imagine that's why Windows-inside-of-Virtualbox doesn't see it.

If anyone has tips on how to force mount it, by all means, spill forth.

---

