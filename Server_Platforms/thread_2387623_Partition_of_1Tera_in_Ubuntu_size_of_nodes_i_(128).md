---
title: "Partition of 1Tera in Ubuntu: size_of_nodes_i (128) * number_of_nodes_i (0) is too m"
date: 2018-03-21
forum: Server Platforms
---

### Post by aaaa42 on 2018-03-21
Hello, A new 1Tb hard disk have been installed, and I want to make it accessible from ubuntu.

if I do a fdisk -l to see the disks, and I see the new one: Disk

```
/dev/sdc: 1 TiB, 1099511627776 bytes, 2147483648 
sectorsUnits: sectors of 1 * 512 = 512 bytesSector 
size (logical / physical): 512 bytes / 512 bytesI / 
O size (minimum / optimal): 512 bytes / 512 bytes
Disklabel type: two
Disk identifier: 0xe88946f3
```

Now I create the partition:    fdisk /dev/sdc

Partition n_new and e_xtended .... first and last cylinder by default ..... 

I have my disk partitioned ...

Devices Start Start Final Sectors Size Id Type
/dev/sdc1 2048 2147483647 2147481600 1024G 5 Extended

now 'partprobe' for the system to re-read the partitions

Now format with     mkfs.ext4 / dev / sdc1

but I get the following message:

A partition table two has been found in / dev / sdc1 Continue anyway? (s, n) smkfs.ext4: size_of_nodes_i (128) * number_of_nodes_i (0) is too muchlarge for a file system with 0 blocks; specifya greater ratio of nodes-i (-i) or a smaller number of nodes-i (-N).
I have no clear steps, is I missing something?How can I format it to mount and use .... ??

Regards

---

### Post by oldfred on 2018-03-21
I am surprised a new drive is 512, not 4K.

But you created an extended partition, and then have to create logical partitions inside the extended partition.
With MBR you can have 4 primary partitions, any one can be an extended partition and contain an unlimited number of logical partitions.
Primary partitions must be sda1 thru sda4. Logical partitions must start at sda5 or higher.

But if not ever installing Windows to drive in BIOS boot mode (which requires MBR/msdos partitions), better to use the newer gpt partitioning.
That has 128 primary partitions. Is the standard for UEFI boot. And gpt is required for drives over 2TiB.
Ubuntu can boot in either UEFI or BIOS from gpt partitioned drives if correct supporting partitions are on drive. Either ESP - efi system partition or bios_grub partition.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[URL="http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"]http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface
[/URL]
 GPT fdisk Tutorial 
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/) 

I use gparted to create gpt partitioned drives. And use gpt for all my larger flash drives.
Before creating partitions:

 Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or if drive is sdc:
sudo parted /dev/sdc mklabel gpt 

[URL="http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"]
[/URL]

---

