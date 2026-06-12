---
title: "ubuntu 16.04 doesn't recognize all RAID hard disks"
date: 2016-10-21
forum: Server Platforms
---

### Post by sesamelai on 2016-10-21
I try to install ubuntu 16.04 on an HP workstation(Z820). It is supposed to have 8.7 TB space with RAID, but during the installation, ubuntu can only see a disk with 2.1TB and some other smaller partitions. I tried red hat enterprise 7.0 on the same computer and it did not have any issue to recognize all the disks.

Here is the result after I run fdisk:

[PHP]ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.3 GiB, 1433468928 bytes, 2799744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start        End    Sectors Size Id Type
/dev/sda1           1 4294967295 4294967295   2T ee GPT

Partition 1 does not start on physical sector boundary.


Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sdd: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00000001

Device     Boot Start        End    Sectors Size Id Type
/dev/sdd1           1 4294967295 4294967295   2T ee GPT

Partition 1 does not start on physical sector boundary.


Disk /dev/sde: 7.5 GiB, 8053063680 bytes, 15728640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0e0e8e70

Device     Boot   Start     End Sectors  Size Id Type
/dev/sde1  *          0 2902111 2902112  1.4G  0 Empty
/dev/sde2       2888004 2892739    4736  2.3M ef EFI (FAT-12/16/32)




The primary GPT table is corrupt, but the backup appears OK, so that will be used.
Disk /dev/mapper/isw_dfieccfcie_RAIDVOL: 2.2 TiB, 2404692000768 bytes, 4696664064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 65536 bytes / 196608 bytes
Disklabel type: gpt
Disk identifier: 819BF841-8EE1-4970-B417-C416E63407F4

Device                                        Start        End    Sectors   Size Type
/dev/mapper/isw_dfieccfcie_RAIDVOL-part1        384    1050623    1050240 512.8M EFI Sys
/dev/mapper/isw_dfieccfcie_RAIDVOL-part2    1050624 4428374783 4427324160   2.1T Linux f
/dev/mapper/isw_dfieccfcie_RAIDVOL-part3 4428374784 4696663679  268288896   128G Linux s

[/PHP]

Is there any one knows what the issue is? Thanks.

---

### Post by oldfred on 2016-10-21
Even though a workstation, I am moving thread to server sub-forum where those who know RAID can help.
I do not know RAID, other than desktop installer does not fully support RAID. Back with 12.04 they had an alternative installer for desktop RAID installs, but that was obsoleted. Suggestions then were to install using server installer and add desktop of choice.

You also show mixed dos & gpt (label type or partitioning) . With large drives, you should only have gpt partitioning.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[URL="http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"]http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface
[/URL]
 MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record) 

      
 Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel 
    [URL="http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"]
[/URL]

---

### Post by darkod on 2016-10-21
1. Please specify if you are trying to install Ubuntu Desktop or Ubuntu Server. I see the output you posted is from the desktop version, but let us know which version exactly you plan to install.

2. With larger disks these days do not use fdisk because it doesn't work good with gpt. Instead try something like:
```
sudo parted -l
```

3. Workstations usually use fakeraid bios raid, which is neither HW raid or SW raid in the true meaning. We all have different opinions but most people think fakeraid is one of the worst options to use, especially if you are not dual booting. If you plan to use only ubuntu, I suggest to go into the bios raid config, delete all raid volumes you have created, and then disable the raid function in the bios. Use the sata controller in standard AHCI mode. Let the ubuntu OS run its own mdadm SW raid.

---

### Post by sesamelai on 2016-10-21
Thanks. I tried the server installer and it worked.

---

### Post by sesamelai on 2016-10-21
Thanks. I forgot to say it was desktop installer. Now it works for server installer.

---

