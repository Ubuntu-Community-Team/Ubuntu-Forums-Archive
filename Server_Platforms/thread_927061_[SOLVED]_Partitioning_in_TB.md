---
title: "[SOLVED] Partitioning in TB"
date: 2008-09-22
forum: Server Platforms
---

### Post by DarkPhoenixTSi on 2008-09-22
Okay, now that I got my GRUB issue out of the way, I am looking for a way to have the Ubuntu Server actually partition and format the array into two 4.5TB drives. Gparted has a 500GB max. 

Does anyone use anything else for this, or should I just partition them down to smaller units?

---

### Post by Yannick Le Saint kyncani on 2008-09-22
> **DarkPhoenixTSi said:**
> Gparted has a 500GB max.

Hmm, I've used gparted yesterday to create a 1T ext3 partition ...

---

### Post by DarkPhoenixTSi on 2008-09-22
Really? It is showing me that I can only do a 470GB max, that is with ext3.


EDITED: I pared the two drives in the array to 4 2.73TB drives using RAID0, but gparted still only says that 10% is the max that it can be formatted to. In this case 275GB. 

I need a better solution, as this will be used as a media server for my movies.

---

### Post by Yannick Le Saint kyncani on 2008-09-22
Well, I don't know if this has anything to do with it working well here, or if will do anything good for you, but I've zeroed the ms-dos partition table before using gparted.

To zero a ms-dos partition table :

- Make sure your disk is not mounted.

- sudo dd if=/dev/zero of=/dev/sdf bs=1M count=1

Assuming your disk is /dev/sdf of course. Don't screw this up and zero a disk you're using btw.

Then I've used the standard parted available in hardy (libparted-1.7.1, gparted-0.3.5).

---

### Post by DarkPhoenixTSi on 2008-09-22
Now are you using an array, or is it just one drive? 

And I zeroed out the drive, and gparted gave me the same size limitation.

Edit: It is giving me a limit of 745GB on a 2.73TB drive.

---

### Post by Yannick Le Saint kyncani on 2008-09-22
It was just one regular usb drive.

Just off my head, you might want to try :

- parted, the command-line tool, to make sure it's a libparted limitation and not a gparted bug.

- A more recent version of parted. I've noticed hardy is using libparted-1.7 and intrepid libparted-1.8 (you never know which bugs have been fixed in newer versions).

- Or try fdisk, if you're desperate enough ;)

Good luck.

---

### Post by fjgaude on 2008-09-22
How is the raid0 array being created? from the motherboard, software or a hardware card?

I've never been able to use gparted with anything that is raid. I usually use cfdisk.

---

### Post by DarkPhoenixTSi on 2008-09-23
It's running off of a PCI-E card.

I have to attempt fdisk again. If that doesn't work, then I will be trying LVM2.

I'll post updates.

---

### Post by DarkPhoenixTSi on 2008-09-24
GOT IT!! I used parted and all is well. Now to work on why the Samba folder I created can't be opened by my Microshaft machine.

Thanks for everyone's help!!

---

