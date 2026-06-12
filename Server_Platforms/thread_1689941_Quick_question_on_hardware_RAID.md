---
title: "Quick question on hardware RAID"
date: 2011-02-17
forum: Server Platforms
---

### Post by garfonzo on 2011-02-17
Hey Folks:

I just received my new server and it has an Adaptec 5405 RAID controller in it. I have two 500GB hard drives attached to the controller, with a third 500GB attached to the motherboard. 

I setup a RAID1 array in the controller's BIOS. Now that I've done a clean install of Ubuntu Server 10.04.1 and check my disks, it is showing two disks as follows:

```


garfonzo@MyServer:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00014a7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59325   476519424   83  Linux
/dev/sda2           59325       60802    11865089    5  Extended
/dev/sda5           59325       60802    11865088   82  Linux swap / Solaris

Disk /dev/sdb: 499.3 GB, 499279462400 bytes
255 heads, 63 sectors/track, 60700 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

Now, I think I have done this correctly as I want the OS on the single hard drive, and all my data to be located on the RAID. 

My question is, does the above look correct? I mean, if I start creating partitions on sdb as usual, is this going to work on the RAID so that both hard drives on the RAID will receive a mirror of the partitions and data?

I've never worked with a hardware RAID controller before so this is new territory for me. 

Thanks!

---

### Post by garfonzo on 2011-02-17
I should probably note that I didn't do anything special during the Ubuntu install. Simply inserted the disc and installed. I didn't add any modules or packages to handle the Adaptec controller as it was listed on Ubuntu's site as being supported natively.

---

### Post by koenn on 2011-02-17
quick answer:

looks right, 
ie the raidcontroller does the raid thing - mirroring the disks - but the OS doesn't see this because the "mirrored set' is presented as just  1 disk to the operating system -> that's /dev/sdb.
Whatever your OS tries to do to this "disk device" -create a partition, write a file ... , the raidcontroller will apply to both (physical) disks

---

### Post by garfonzo on 2011-02-17
> **koenn said:**
> quick answer:

looks right, 
ie the raidcontroller does the raid thing - mirroring the disks - but the OS doesn't see this because the "mirrored set' is presented as just  1 disk to the operating system -> that's /dev/sdb.
Whatever your OS tries to do to this "disk device" -create a partition, write a file ... , the raidcontroller will apply to both (physical) disks

Cool. Ya, I knew that I still had to create the partition and mount the drive. I just wanted to make sure that it really is acting as it should (as one drive). 

Thanks for the help!

---

