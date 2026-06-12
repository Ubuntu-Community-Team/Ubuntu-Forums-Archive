---
title: "Hard disk misalignment"
date: 2012-06-02
forum: System76 Support
---

### Post by rmc_0 on 2012-06-02
Hi,

Update Manager is running right now and a problem has popped up regarding grub:

> 
The GRUB boot loader was previously installed to a disk  is no longer present, or whose unique identifier has changed for some reason. It is important to make sure that the installed GRUB core image stays in sync with GRUB modules and grub.cfg. Please check again to make sure that GRUB is written to the appropriate boot devices.
I also found that all of the partitions on my disk are misaligned: sda1 by 2048 bytes, sda2 by 3072 bytes, and sda3 by 2560 bytes. I ran fdisk -lu, and here is what I got:

```

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00022cd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2148  1449724609   724861231   83  Linux
Partition 1 does not start on physical sector boundary.
/dev/sda2      1449724610  1465149167     7712279    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1449724611  1465149167     7712278+  83  Linux
Partition 5 does not start on physical sector boundary.

```This is on a panp9, I have done nothing to the disk since it arrived a few weeks ago. How did this happen, and what should I do?

edit: 'Writing GRUB to boot device failed - continue?' just came up on Configuring grub-pc. I'm not shutting down until I get answers, and I'm backing up.

---

### Post by christopherbalz on 2012-06-02
I had the same issue, rebooted, and - surprise surprise - am writing this thread as I work from a usb image that I am using to repair my boot system. 

This is the second time a 12.04 LTS update has removed the boot feature from my operating system.  And I'm even on officially-supported hardware: a System76 'leo1'!  

[http://chrismbalz.typepad.com/computerburn/2012/05/rough-upgrade-from-ubuntu-1004-lts-to-1204-lts.html](http://chrismbalz.typepad.com/computerburn/2012/05/rough-upgrade-from-ubuntu-1004-lts-to-1204-lts.html)

It's like back to the old days of Ubuntu six years ago!   Seems like the whole distro may be crumbling.

---

### Post by techvish81 on 2012-06-03
i have a western digital advance format harddisk and the ubuntu installer fails to create properly aligned partitions, but if the partitions are done with gparted using live system and with proper settings,  it can be done properly.

what i did was, 

boot to live ubuntu dvd/usb,  create a first primary partition of 100 mb with "align to mb "  option ticked and leave 1-2 mb space before the partition and name the partition as "efi",  than for dual boot a second primary partition for windows and an extended partition (leaving 1-2 mb after the partition) for linux in which you can create logical partitions for boot,  root  , home etc... 

i dont know why it worked, because i use the bios boot not efi, but i think some systems are using hybrid type.. may be this could be the reason. i failed in several attempts using the ubiquity installer and creating partitions in  different ways, it was the only thing that worked..


i'm not a geek or dev,  so i can't explain it,  but it happens due to advance format disks..

---

### Post by christopherbalz on 2012-06-03
In my case, the issue was that I rather naively followed the Grub suggestion to install grub on all partitions.  From a live usb instance of Ubuntu, I ran a purge and re-install of updated Grub via the boot-repair program.  

I saw in the console output from that run a message that said something to the effect that putting Grub on a partition is a "BAD idea".  This is confusing since iirc, boot partitions are pretty normal.  I guessed that they meant my root file system. So I re-did the purge and re-install, this time only installing on my 'sda' volume, vs. my root filesystem, sda1.

I have a very vanilla system and one would think that Grub messages would indicate what I saw in the console output.  Or that somehow, this could just be made more navigable by those of us not up on the latest Grub details.

---

### Post by rmc_0 on 2012-06-04
Well, this is all just so *fantastic* to hear, especially for someone like me who is altogether new to the Ubuntu/Linux experience. I am still hoping to hear from a System76 rep, but it sounds like it's more to do with the OS than anything else. Great.

[QUOTE="christopherbalz"]So I re-did the purge and re-install, this time only installing on my 'sda' volume, vs. my root filesystem, sda1.[/QUOTE]

As I am new to this, I've never touched the partitioning on the hard drive or any of the GRUB or BIOS settings, I just figured I'd leave it as is until I learn more. Okay, so run this by me again: when you reinstalled, you installed /root and GRUB on one volume (sda1) instead of having a separate volume for /boot? How many partitions do you have altogether?

[QUOTE="techvish81"]i dont know why it worked, because i use the bios boot not efi, but i  think some systems are using hybrid type.. may be this could be the  reason. i failed in several attempts using the ubiquity installer and  creating partitions in  different ways, it was the only thing that  worked..[/QUOTE]

I'm not sure what the panp9 has, though I assumed it's just a garden variety BIOS boot. If it's a hybrid, I'm not looking forward to dealing with it; I had previously installed Oneiric on a MacBook Pro (which uses EFI), and while I was able to dual-boot, it was nothing but headaches from the outset. I'm not experienced enough to handle that sort of thing.

I haven't done anything yet because I want to get as much info as I can on this as possible before I plunge headlong into a new series of headaches, but I'm taking into consideration everything that both of you have suggested thus far, thanks.

---

### Post by rmc_0 on 2012-06-05
Well, I got a response from System 76, and I think I'm just going to restore GRUB, which is easy enough, and leave it at that for now. If the misalignment doesn't cause any problems, then I can wait until Quantal Quetzal comes out and deal with it with a fresh install.

Thanks everyone for your responses, and good day.

---

### Post by christopherbalz on 2012-06-06
> **rmc_0 said:**
> Okay, so run this by me again: when you reinstalled, you installed /root and GRUB on one volume (sda1) instead of having a separate volume for /boot? How many partitions do you have altogether?.

I have two partitions: sda and sda1.  My issue, apparently, was that I'd installed grub on sda1.  So instead, I just put it on sda (purge, then re-install, this time just on sda - not sda1).  I also re-enabled the master boot record (MBA), but don't know if that helped.  To get to these options on the boot-repair program, just click the 'Advanced' option at lower left on the boot-repair gui.

---

