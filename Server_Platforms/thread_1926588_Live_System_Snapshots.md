---
title: "Live System Snapshots"
date: 2012-02-16
forum: Server Platforms
---

### Post by sirsiwsh on 2012-02-16
Hi all,

I'm a stone's throw from having a perfect linux server, but there are a few things that are vexing me at the moment. Most importantly, I'd like to be able to take a live disk snapshot of my boot hard drive for disaster recovery.

The boot device (obviously /dev/sda) is MBR partitioned, with 5 partitions on the disk:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8287    66565296   83  Linux
/dev/sda2   *        8288        8300      102400    7  HPFS/NTFS
/dev/sda3            8300       15589    58545962+   7  HPFS/NTFS
/dev/sda4           15589       19453    31034369    5  Extended
/dev/sda5           15589       19288    29710336   83  Linux
/dev/sda6           19288       19453     1323008   82  Linux swap / Solaris

/dev/sda5 is the partition on which linux sits, formatted ext3 (default, by the installer) the other partitions are for Windows and the swap etc..

I've been trying for a while now to get a dd image to restore successfully to a(nother) drive so that I can boot it and resume where I left off before the (currently hypothetical) disaster.

If I take an image of the drive  (sudo dd if=/dev/sda of=/path/to/some.img) dd only copies /dev/sda5. The image is fairly corrupt, however after a quick fsck (sudo fsck -y /path/to/some.img)
the image can be mounted and seems complete. When I try to boot with the device, however BIOS throws the error:

No boot device found (blah, blah)

If I copy the drive to another device (sudo dd if=/dev/sda of=/dev/sdf conv=sync,noerrors) the partition structure is recreated. Again, a quick fsck brings /dev/sdf5 back to a point where it can be mounted, however it is missing about half the folders from / , notably /etc, /usr and a few others. When I try to boot with this device, I get the error:

Cannot mount ... device, wn-blcok (0,0)

What I'd like to be able to do is boot from this dd image. I don't mind if it doesn't recreate the whole device, all I need is the boot partition. On these forums somewhere are instructions to tell GRUB the new disk UUIDs and mount points, however GRUB2 uses grub.cfg (or similar) instead of the menu.lst file given in the tutorial, so I can't tell GRUB about the new device, especially in the second case where /etc is missing (so I have no /etc/fstab).

Please, does anyone know of a way I can automatically take a live system image from which I can boot? I'm fairly open to suggestions, including the use of scripts to start restart the machine from a recovery disk, take a snapshot then boot back into the system proper. Obviously I'm backing the system up (with BackInTime), although it misses several key config files I'm desperate to keep. Plus it'd be great to have a warm recovery option.

Vital stats:

Standard Ubuntu 10.04 x86 (32bit) installation (with X)
/dev/sda5: MBR, with NTFS and ext3 partitions
Oh, and it'd be great if this could all be accomplished whilst the machine is running!

If anyone out there has any experience with live system snapshots, dd or disaster recovery, please let me know. The machine is getting very, very good at what it does and I'll be writing HOWTOs for everything it does when I get it to the point I consider stable so the love will be returned to the community.

Thanks!

---

### Post by sudodus on 2012-02-16
I'll try to help you.

1. In principle, your command with dd should work (although it is often discouraged, 'disk destroyer').
- Did you get any error output?
- How did you make a clone from the image file?
- Did you start the command from another drive (for example a live CD or USB drive)?
- Was there space enough on the target partition?
- Is there some bad sectors on the drive?
- Did you remove the original drive, when trying to boot from the clone? The drives should be identical (for example the same UUIDs) which could create problems if you want to boot from one with the other one in the computer.

2. There are safer cloning tools, for example Clonezilla. Also it is faster than dd. Download the iso file and make a live CD or USB drive! Use it to clone the drive or make an image of it!

---

### Post by sirsiwsh on 2012-02-17
> **sudodus said:**
> I'll try to help you.
...
2. There are safer cloning tools, for example Clonezilla. Also it is faster than dd. Download the iso file and make a live CD or USB drive! Use it to clone the drive or make an image of it!

Sudodus, what a legend. That looks avery interesting. I suspect the problem was becuase I was being lazy and using dd on a live system, although I see no reason why this isn't possible? I like the fact it seems I can script this, so perhaps next week I can post some code that will automatically restart a system from the USB, take a clone and restart back into the server again. I will check this out very soon and let you know.

> **sudodus said:**
> 1. In principle, your command with dd should work (although it is often discouraged, 'disk destroyer').
- Did you get any error output?
- How did you make a clone from the image file?
- Did you start the command from another drive (for example a live CD or USB drive)?
- Was there space enough on the target partition?
- Is there some bad sectors on the drive?
- Did you remove the original drive, when trying to boot from the clone?  The drives should be identical (for example the same UUIDs) which could  create problems if you want to boot from one with the other one in the  computer.
To answer your questions:
- No error output
- I made the clone from the image file by simply reversing the direction of dd
  sudo dd if=/path/to/some.img of=/dev/sdf
- No, I started the command from the system running on /dev/sda (i.e the terminal I was using was running from a booted partition on /dev/sda - the live system)
- Yes, when using a disk it was exactly the same size (160GB). The image went to an ext4 filesystem with >>200GB free space
- No, no bad sectors. fsck on /dev/sda does nothing. SMART reports the drive passes. I get no read error, etc, etc.
- Yes, when trying to boot from the clone I used a seperate machine to try and boot it (I would prefer not take down the server, hence the want for a live system snapshot, also it would give me peace of mind that my backup is more disaster proof if some hardware dies. I see no reason why the machine should (ultimately, once the drive is configured correctly) make any difference at all). When I tried to change the UUIDs of the drive in GRUB2, I got nowhere. Do you know where I can change them? (This forum gives /boot/grub/menu.lst which is only valid for GRUB(1). The new GRUB2 uses /boot/grub/grub.cfg but this file is autogenerated and it contains a warning at the top not to mess with it. I guess, however that this is not a "normal scenario" so messing with it is fine??) Changing the grub.cfg file is possible in both methods as /boot is reacreated- in the clone to another disk method (if=/sda of=/sdf) dd does not copy the /etc folder so I cannot update the fstab :(


Thanks again for your help, I hope this gives you a better idea of what I've done and what I'm trying to accomplish. 

> **sudodus said:**
> 1. In principle, your command with dd should work 
I've been tearing my hair out with this. It seems like it should be so simple- start at 'bit 0' and, er, Go! If you would like/need me to post any output from various commands please let me know!

Thanks!

---

### Post by sudodus on 2012-02-17
> **sirsiwsh said:**
> ...

To answer your questions:
...
- No, I started the command from the system running on /dev/sda (i.e the terminal I was using was running from a booted partition on /dev/sda - the live system)

You should ***not*** run dd on a drive/partition that is mounted, and definitely not on the active system partition /dev/sda5 mounted on / in your case. If you want to get a live snapshot, you need to do something more advanced and I cannot help you with that, but there are people at the Ubuntu Forums, that could (if they happen to read your thread).
> 
...
- Yes, when trying to boot from the clone I used a seperate machine to try and boot it (I would prefer not take down the server, hence the want for a live system snapshot, also it would give me peace of mind that my backup is more disaster proof if some hardware dies. I see no reason why the machine should (ultimately, once the drive is configured correctly) make any difference at all). When I tried to change the UUIDs of the drive in GRUB2, I got nowhere. Do you know where I can change them? (This forum gives /boot/grub/menu.lst which is only valid for GRUB(1). The new GRUB2 uses /boot/grub/grub.cfg but this file is autogenerated and it contains a warning at the top not to mess with it. I guess, however that this is not a "normal scenario" so messing with it is fine??) Changing the grub.cfg file is possible in both methods as /boot is reacreated- in the clone to another disk method (if=/sda of=/sdf) dd does not copy the /etc folder so I cannot update the fstab :(
...If you have no proprietary drivers or references to hardware in configuration files (for example /etc/fstab) the drive should work in another computer. But to be sure, you should test the original drive (or a perfect clone made from a system booted from a CD or USB drive). Alternatively, disconnect the original drive in your computer, and connect the clone. If is doesn't work properly, it is not a perfect clone.

There are links to grub2 (and yes, you can edit /boot/grub/grub.cfg but there are better ways, that you'll learn)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

And some years ago I found a method to change the UUID to what I wanted (edited it). But I can't find it right now (it's somewhere on the internet).

---

