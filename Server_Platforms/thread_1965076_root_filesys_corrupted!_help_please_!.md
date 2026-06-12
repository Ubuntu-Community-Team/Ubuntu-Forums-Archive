---
title: "/root filesys corrupted! help please !"
date: 2012-04-25
forum: Server Platforms
---

### Post by dchen on 2012-04-25
Ubuntu server 11.10, tried to "clean" up the .gvfs filesys caused the /root filesystem corrupted!
Now it can't boot even tried to boot to the "recovery mode";  can't get to the single user mode!
Here is the console message:  Mount: mounting /dev/mapper/server-lv_root on /root failed: invalid argument.

Tried to use the installer CD, and select the "Rescue Mode", and select the "/dev/server/lv_root" when prompt "Device to use as root file system", responded the following error:
              Mount failed
     An error occurred while mounting the device you entered for your root filesystem     
     /dev/server/lv_root on /target

Any idea what I should do before re-install  everything !?  Even if I re-install, is there a way to prevent from erasing my /dev/mapper/server-lv_home which is mounted on /home ?

---

### Post by Jonathan L on 2012-04-25
Hi dchen

> Any idea what I should do before re-install  everything !?

I'd try booting with the CD to a running shell, and try mounting your filesystem on /mnt and fixing it there. The kernel has to give up if it's got a broken root filesystem, but will let you do more with a damaged other system.  As soon as you have it visible (perhaps readonly), then copy your own work off to another medium.  If it was me, I'd then wipe and reinstall.

Hope that's helpful.

Kind regards (and good luck)
Jonathan.

---

### Post by dchen on 2012-04-26
> **Jonathan L said:**
> Hi dchen



I'd try booting with the CD to a running shell, and try mounting your filesystem on /mnt and fixing it there. The kernel has to give up if it's got a broken root filesystem, but will let you do more with a damaged other system.  As soon as you have it visible (perhaps readonly), then copy your own work off to another medium.  If it was me, I'd then wipe and reinstall.

Hope that's helpful.

Kind regards (and good luck)
Jonathan.
Thanks Jon,

I tried to back up the /home filesystem, after mounting the /dev/server/lv_home on /mnt, I inserted a usb device for the backup storage, but the /media can't automatically mount the usb device, I have to go into the  disk partitioning section to find the device name and sector for the usb drive, then mount it.  At the end I encountered the mounting error on the usb drive due to the incompatible format.  I guessed I need an Unix ext3 or ext4 format partition on the usb drive, right ?

---

### Post by seoexpertrizwan on 2012-04-26
If your root file system is too corrupted to run and showing nonsense messages and you want to restore your system , you must have an emergency boot floppy disk which must have a kernel OR you must have a partial re installation.

---

### Post by Jonathan L on 2012-04-26
> I tried to back up the /home filesystem, after mounting the /dev/server/lv_home on /mnt, I inserted a usb device for the backup storage, but the /media can't automatically mount the usb device, I have to go into the  disk partitioning section to find the device name and sector for the usb drive, then mount it.  At the end I encountered the mounting error on the usb drive due to the incompatible format.  I guessed I need an Unix ext3 or ext4 format partition on the usb drive, right ?

That's great you got your data mounted.

USB drives are often used with Microsoft FAT filesystems of various kinds, and should work perfectly.  You can certainly format them ext3 or whatever, or use a FAT one.  I normally use tar to make a single backup file, so I know that ownership, permissions, and times will be maintained.  (You can lose these if you simply copy files to a filesystem which doesn't have them.)

I'd try another USB drive, or reformat this one if you're sure you don't need what's on it.

Kind regards,
Jonathan.

---

