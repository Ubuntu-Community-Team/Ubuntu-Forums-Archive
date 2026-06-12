---
title: "Question about RAID 1 on new 11.04 Server Install"
date: 2011-08-09
forum: Server Platforms
---

### Post by grunge09 on 2011-08-09
I have been working in my spare time over the last few days, Had problems with the whole grub2 not installing on RAID 1.  Then I found out that I had to have a separate non raid Ext4 partition on one drive with "/Boot" as mount point and install went though fine.

My question is, will the developers FIX this.  I mean if I only have 2 x 2tb drives in teh pc as RAID 1, and the one fails with the boot partition the whole machine goes down.  Kinda defeats the whole RAID feature huh.

I USED to run a windows network with RAID 5 servers, and windows never had a problem installing everything on the RAID.  Or even setting up RAID 1 in the bios on the PC and installing XP or NT4 on the RAID 1.  There was never a need for a separate non raid boot partition.  

Do we need a separate RAID friendly/enabled Grub?

I guess for now I will get a 250gb drive and install the Server OS to it, and setup RAID1 manually after the server OS boots.  Then will make a ghost type image of the server in case that drive fails so I can quickly install a new drive and restore the image and get it back up and running again.

---

### Post by psusi on 2011-08-09
Works fine for me...

---

### Post by Entilza on 2011-08-09
Are you using software raid?

I'm running an adaptec 6805 and have everything on a RAID 5 array.  The /boot partition is a separate partition but still within the raid 5 array and set as ext2 where the rest of the system is ext4.

---

### Post by psusi on 2011-08-09
I thought you said raid1?  Either way works for me, and I don't bother with a separate /boot partition.

---

### Post by YesWeCan on 2011-08-09
Grub2 has been able to directly boot a linux RAID1 since 10.04, if not earlier.

Is this a linux RAID that is being booted?

---

### Post by kevinthecomputerguy on 2011-08-10
I once had this problem. It turned out to be the 2TB drives. They use a GPT tables instead of the old DOS tags. (making small partitions on the drive wont help) its the overall table that is different.
 
I got around this by using a 1GB usb flash drive as /boot
I also used dd to make an image of the flash drive incase the flash drive ever dies.
 
But if you stick with 1.5TB drives or smaller, even grub1 and old install cd's will work.
 
*with software raid i also wait 24 hours after creating md0, before procedding to the next screen. If you do this the raid will already be synced, and then the grub install to hd0 should actually be written to both devices.

---

### Post by psusi on 2011-08-10
Ahh, to install grub on a GPT disk, you must create a 1 mb bios_grub partition.

---

### Post by kevinthecomputerguy on 2011-08-12
I have had the best success with doing this (if you cant use 1.5TB disks or smaller)
 
For example, Raid 5, launch fdisk and create (3) 1GB partions as "non-fs" or "da"
then create (3) xxxGB partitions for the root fs as ext2
 
Create (2) raid5 md devices, and do not format the non-fs raid 5, and set the second md as /
 
Grub2 will find it, and install ok
 
But having done hundreds of these, i say stick with less than 1.5TB disks until a grub3 comes out.

---

### Post by YesWeCan on 2011-08-13
@kevinthecomputerguy
When you prescribe <1.5TB do you mean that specific size or do you mean this as a rule of thumb to avoid GPT disks?

My understanding is that GPT format is not required unless the disk is >2TiB (for a 512 byte sector size because of block address restrictions in the MBR PT).

GPT is awkward for installing to at the moment so I would be inclined to reformat any sub 2TiB GPT disks to MBR before using them. This can be done in Disk Utility.

@all:
BTW the fdisk -l command doesn't always show whether a disk is GPT. Better to use sfdisk -l or parted -l.

---

### Post by kevinthecomputerguy on 2011-08-13
Meant as a rule of thumb to avoid GPT disks.
 

But your not always able to, so i gave some work arounds. So far the non-fs partition has been the easiest. Or a USB flash drive as /boot
 

But when possible, atleast for a few more months until it gets simpler, i try and recommend builds with 1.5TB disks instead of 2GB, so new users dont get discouraged trying to setup raid.

---

### Post by YesWeCan on 2011-08-13
> Or a USB flash drive as /boot
I have to say there is a lot to be said for the USB flash drive boot. Especially these new ones that have hardly any body at all. Ideal for a laptop. And you can install a whole Ubuntu to one so that it can be a completely stand-alone boot loader - no more problems when deleting an OS or adding a new one, and no more Windows MBR issues.

---

