---
title: "remove other os"
date: 2011-07-07
forum: Server Platforms
---

### Post by darkeale on 2011-07-07
Hi all,

I have a desktop with 3 hard disks.  One with Ubuntu Server 10.04, one with Linux Mint, and one just as a backup.  I am using the computer headlessly, and using Ubuntu Server 10.04, so all that I do has to be done through a Putty terminal on my Vista machine.  Can anyone tell me how I can uninstall Linux Mint completely from the other hard disk?  If I do this, will I have to edit the grub menu?  At the moment it automatically boots into Ubuntu Server 10.04 and I want it to stay this way.

Thanks,
Alex

---

### Post by darkeale on 2011-07-29
If I just format the drive with Linux Mint on it will this do the job?  And then is there some command to run to rebuild the Grub menu?  

Thanks,
Alex

---

### Post by el_koraco on 2011-07-29
It depends on which Grub is in the MBR. If it's the Ubuntu one, you ca just format the second hard drive, then do a ```
sudo update-grub
``` and you're set.

---

### Post by darkeale on 2011-07-29
ok, thanks.

I'm pretty sure it's the Ubuntu grub version.  However, because I run it headless I don't see the Grub screen, I just SSH in once it has booted up.  Is there a way to check once it has booted up which Grub is being used?

Thanks,
Alex

---

### Post by volkswagner on 2011-07-29
A few things to check before formatting the drive:

Find out which drive/drives/partitions are set as bootable.

```
sudo fdisk -l
```

If the drive that is set as bootable is your linux Mint drive, you may be trashing Grub anyway.

To be safe, it may be best to reinstall grub after formatting the drive, before rebooting the machine.  Just make sure you specify when installing grub to install to the MBR of the bootable disk.  Reinstalling grub should find any other OS on the system.

---

### Post by egrovesystems on 2011-07-29
This is possible but we could do in Crub only...

---

