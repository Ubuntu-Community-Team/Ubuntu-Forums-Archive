---
title: "Windows Virus... Hard Drive missing... Help!!!"
date: 2009-01-31
forum: Windows
---

### Post by wall0645 on 2009-01-31
Hi,

My friend got a virus or something, and I tried to help him out. We have a Windows Install disk, but when we put it in the computer, it says something along the lines of "We can't find your hard drive, sorry!"

Now, I used an Ubuntu Install disk to use GParted to delete the rouge partition. Yet still the Windows Install disk cannot find the hard drive!! I thought that deleting the partition would delete whatever was causing that!

I installed Ubuntu just so my friend would have a computer to use. However I don't think he wants to keep Ubuntu as his operating system forever.

Is there any way that I can get Windows installed? Any ideas on why the installer won't work?

Please help!! Thank you!

---

### Post by 3rdalbum on 2009-01-31
The Windows installer is not as smart as the Ubuntu installer. It can only detect a hard disk if it has a Fat32 or NTFS partition on it. Use Gparted to add one.

Also, Windows XP's installer doesn't recognise SATA controllers. If your friend's computer uses SATA (if it's relatively recent it will), you either need to load the SATA controller's drivers from a floppy disk during the install, or switch the BIOS to use legacy IDE emulation.

---

### Post by wall0645 on 2009-01-31
> **3rdalbum said:**
> The Windows installer is not as smart as the Ubuntu installer. It can only detect a hard disk if it has a Fat32 or NTFS partition on it. Use Gparted to add one.

Also, Windows XP's installer doesn't recognise SATA controllers. If your friend's computer uses SATA (if it's relatively recent it will), you either need to load the SATA controller's drivers from a floppy disk during the install, or switch the BIOS to use legacy IDE emulation.

I tried formatting the hard disk to NTFS because I thought that'd be a good idea, but that didn't work. I guess the problem is the SATA thing, then?

I don't think anyone has SATA controller drivers on a floppy disk... I'll try to get the BIOS to use legacy IDE emulation. If I have trouble I'll ask here!

I'll post the error message that comes up if/when it comes up again.

Thank you!

---

### Post by wall0645 on 2009-01-31
Um... so I checked the BIOS and didn't find anything at all about Legacy IDE emulation...

Any other ideas??

I'm just so confused as to why the Windows Setup can't see the hard disk. :(

---

### Post by jrusso2 on 2009-02-01
Because Windows XP has been out since 2001 but SATA was born years after that.  Thats why Xp didn't have the driver.

If you slipstream the service packs onto xp that usually works if you don't do the floppy thing to add them.

---

### Post by tsali on 2009-02-01
If you have previously modified the Master Boot Record by installing linux (grub or LILO), then you will have to clear the MBR.

There are couple of ways to do this.

First, I would use a live CD like Knoppix to reformat the entire disk to clear all partitions. Then, use the same live cd to clear the MBR with the following command:

```
dd if=/dev/zero of=/dev/hda bs=512 count=1
```

where "hda" would be the disk in your system (could be "sda" if you have sata drives.)

After this, you should be ready to install Windows on a clean disk.

---

### Post by tsali on 2009-02-01
> **jrusso2 said:**
> Because Windows XP has been out since 2001 but SATA was born years after that.  Thats why Xp didn't have the driver.

If you slipstream the service packs onto xp that usually works if you don't do the floppy thing to add them.

My XP SP1 install disk recognizes SATA drives without an issue, so it would depend on the installer the OP is using.

---

### Post by wall0645 on 2009-02-01
Sorry, I just didn't notice the SATA options in the BIOS the first time around. I figured it out. Thank you all!

---

