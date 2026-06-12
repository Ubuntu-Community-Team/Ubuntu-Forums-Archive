---
title: "Ubuntu Server 12.04 64bit won't boot without usb flash"
date: 2012-08-19
forum: Server Platforms
---

### Post by padred123 on 2012-08-19
I installed Ubuntu Server 12.04 64bit from a usb flash drive that I setup with [YUMI]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/"). I've reinstalled it twice. The 2nd time I manullay setup the partitions but it still won't boot without usb flash. I'm installing it on a dell gx620 2gb ram n 2tb hd. The bios is finicky but appears to be set right but when I boot without a flash I'm prompted "No boot device available - strike F1 to retry boot, F2 for setup utility.


I've tried a few things from google searching including [this]("http://ubuntuforums.org/showthread.php?t=1973947") but still no luck.

Heres my fdisk -l:
```

Disk /dev/sda: 2000.4 GB, 2000397852160 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907027055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000abffc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  3867187199  1933592576   83  Linux
/dev/sda2      3867189246  3871875071     2342913    5  Extended
/dev/sda5      3867189248  3871875071     2342912   82  Linux swap / Solaris

Disk /dev/sdb: 15.8 GB, 15812526080 bytes
255 heads, 63 sectors/track, 1922 cylinders, total 30883840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         128    30883839    15441856    c  W95 FAT32 (LBA)
padred123@padreserv:~$


```

and I've attached my RESULTS.txt

---

### Post by darkapec on 2012-08-19
Im not familiar with YUMI, but I am very familiar with boot disk not found errors. One of two things is happening, the bios is not set to boot from the proper drive, or YUMI is screwing up. 

I would suggest using unetbootin and try a reinstall that way. It is possible that grub is not installing correctly to the drive and I am not comfortable enough with grub2 to walk you through the process of setting up grub2 manually. 

unetbootin should do the trick though

EDIT: it looks like YUMI is the problem, from what it sounds like it is a utility designed to allow you to boot multiple distros from a flash drive, so the flash drive would always have to be present. Try unetbootin and report back.

---

### Post by darkod on 2012-08-19
The bootloader on the stick should not matter, you only use it to boot the installation.

The results file looks OK, I can only think of two things:

1. The BIOS has the limitation not to be able to find boot files beyond 137GB on the disk, and your grub files can be beyond that mark on a 2TB disk.

2. The results file says you have version 12.04.1 LTS which should be officially released on 23rd, it's not yet released. Did you hurry up and install a version which is not yet released? It's very unlikely, but it might have some pre-release issues.

The No boot device can be also related to the boot flag but you have one on sda1 so that shouldn't be a problem.

---

### Post by padred123 on 2012-08-19
> **darkod said:**
> The bootloader on the stick should not matter, you only use it to boot the installation.

The results file looks OK, I can only think of two things:

1. The BIOS has the limitation not to be able to find boot files beyond 137GB on the disk, and your grub files can be beyond that mark on a 2TB disk.

2. The results file says you have version 12.04.1 LTS which should be officially released on 23rd, it's not yet released. Did you hurry up and install a version which is not yet released? It's very unlikely, but it might have some pre-release issues.

The No boot device can be also related to the boot flag but you have one on sda1 so that shouldn't be a problem.


That all seems plausible but then why would it boot ok with the usb flash inserted? The MBR/bootloader must have installed on the flash drive? Right? Sorry Im somewhat noobish..

---

### Post by darkod on 2012-08-19
> **padred123 said:**
> That all seems plausible but then why would it boot ok with the usb flash inserted? The MBR/bootloader must have installed on the flash drive? Right? Sorry Im somewhat noobish..

Yeah, I thought of that too. But the results file says the grub2 bootloader is on the hdd, unless it's somehow confused.

Double check the boot options in BIOS and make sure the HDD is there. Is it possible that it isn't?

---

### Post by LHammonds on 2012-08-19
/dev/sda1 = FAT32?

I see the boot flag being enabled but it seems like a large partition.  Being a large partition and FAT32 may be the problem.

As for being able to boot from the USB, that has no affect on the boot ability of the OS it is loading on the HD.

When I setup servers, I create a 200 MB boot partition and set it to EXT2.

I am not familiar with that multi-boot USB thingy but I assume it chose FAT32 to be the least common denominator so you could boot MS-DOS, Windows or Linux.  If you are not wanting to run a multi-OS system, just stick to EXT2 for the boot partition.

If you like reading, you can click on my Ubuntu server link in my sig and look at the partition and LVM sections which is how I setup servers to be flexible for any kind of server I want them to turn into.

LHammonds

---

### Post by padred123 on 2012-08-19
I'll double check the bios first(it is screwy) 


> **LHammonds said:**
> /dev/sda1 = FAT32?

I see the boot flag being enabled but it seems like a large partition.  Being a large partition and FAT32 may be the problem.

As for being able to boot from the USB, that has no affect on the boot ability of the OS it is loading on the HD.

When I setup servers, I create a 200 MB boot partition and set it to EXT2.

I am not familiar with that multi-boot USB thingy but I assume it chose FAT32 to be the least common denominator so you could boot MS-DOS, Windows or Linux.  If you are not wanting to run a multi-OS system, just stick to EXT2 for the boot partition.

If you like reading, you can click on my Ubuntu server link in my sig and look at the partition and LVM sections which is how I setup servers to be flexible for any kind of server I want them to turn into.

LHammonds

Sounds good! I'll follow your tutorial n reinstall with unetbootin instead of yumi. Wish me luck.

---

### Post by padred123 on 2012-08-21
> **padred123 said:**
> I'll double check the bios first(it is screwy) 




Sounds good! I'll follow your tutorial n reinstall with unetbootin instead of yumi. Wish me luck.

Still wont boot without the flash! I setup the LVM as per instructed but I am still using my yumi bootable flash. Upon boot without the flash I get "Drive 1 not found: Serial ATA,  SATA-2".

I think I'm gonna try installing grub separately.

---

### Post by padred123 on 2012-08-21
> **padred123 said:**
> Still wont boot without the flash! I setup the LVM as per instructed but I am still using my yumi bootable flash. Upon boot without the flash I get "Drive 1 not found: Serial ATA,  SATA-2".

I think I'm gonna try installing grub separately.

Nevermind all that! IT WAS THE BIOS!! Now I feel dumb.. n have a new hatred for dells bios(wasted me many hours/days) but I learned about LVM(thanks LHammonds). So I guess it wasn't entirely a bad thing.

Sorry for wasting your time.

All I had to do is restore defaults.

---

### Post by LHammonds on 2012-08-21
Ouch!  And the BIOS check was mentioned in the very 1st post.  lol.   Live-n-learn.

I have experience with IBM, Dell, and Compaq BIOS and never really thought any of them were too difficult concerning boot options.  Granted, some are quirky in how they allow you to control things like boot order changing requiring odd key sequences (but documented) and the occasional (did this save my changes when it exited) diversion from standard interfaces. :)

**EDIT: **Don't forget to use the "Thread Tools" on the 1st post to mark this thread as SOLVED.

LHammonds

---

