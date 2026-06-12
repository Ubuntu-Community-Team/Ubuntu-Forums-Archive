---
title: "Old HD always boots instead of new one"
date: 2009-06-03
forum: Server Platforms
---

### Post by cmwslw on 2009-06-03
Hello, me again.

I just finished copying my server's old drive to a new one (including GRUB, etc). Everything works fine when I take out the old drive and put in the new one. Everything boots, and all my files are there. I want to use the old drive for extra space for backup. The problem is, whenever I put the old drive in, it boots instead of  the new drive. I'm pretty sure I have my master/slave/cable configurations right. I'm guessing the problem has to do with the old drive still having GRUB written to the MBR. I would think that the master would override this, but maybe it boots the slave (old) drive anyways. Does anyone know what might be happening? If the GRUB for the old drive needs to be uninstalled, how do I do that?

---

### Post by Therion on 2009-06-03
Check you BIOS settings. 

I've seen numerous instances where the boot sequence has to be mapped for not only type of device to boot from and in what order (e.g. Floppy, then Optical, then Hard drive) but also WHICH hard drive to look at first (for a boot sector).  

So, while your BIOS might be set up to boot from the devices in the proper order, it's also set to boot to the wrong drive, primarily, and you just need set the *other* drive as the primary bootable hard drive.

Make sense?

---

### Post by cmwslw on 2009-06-03
> **Therion said:**
> Check you BIOS settings. 

I've seen numerous instances where the boot sequence has to be mapped for not only type of device to boot from and in what order (e.g. Floppy, then Optical, then Hard drive) but also WHICH hard drive to look at first (for a boot sector).  

So, while your BIOS might be set up to boot from the devices in the proper order, it's also set to boot to the wrong drive, primarily, and you just need set the *other* drive as the primary bootable hard drive.

Make sense?

I just tried setting the BIOS to boot from the HD1 and the HD0 first. Both of them ended up booting to the old drive. Does anyone know how I can tell which drive the GRUB is running on? I'm beginning to thing that the new GRUB bootloader is pointing to the old drive. I just looked and the menu.lst on both hard drives appear to boot to the local drive. Despite being a slave, the old drive is always booted from, but I have no idea why. Any suggestions?

---

### Post by cmwslw on 2009-06-03
EDIT: Forget everything I said before! Here's what's happening: The MBR on my new drive is pointing to the GRUB on my old drive. When the old drive is not connected, it resorts to the GRUB on the new drive (which is what I want to be happening). How do I fix the MBR so it always points to the local GRUB?

---

### Post by cmwslw on 2009-06-06
Sorry if this is a little late, but I wanted to help out the people that might have this problem. It turned out that the UUIDs were cloned and that confused GRUB when it tried to boot from one. I ended up having to change the duplicate UUID. [Here]("http://www.clustur.com/node/23") is a tutorial I wrote in case anyone wants to look at it.

-hope this helps

---

