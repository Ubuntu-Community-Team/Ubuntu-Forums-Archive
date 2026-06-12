---
title: "Setup with 4*4TB HDDs in RAID 10 boot issues"
date: 2016-10-12
forum: Server Platforms
---

### Post by saatomic on 2016-10-12
I'm slowly getting frustrated with this Ubuntu server setup here. I have four 4TB drives, that I want to operate with RAID 10.
Due to the disk size GPT is used.

Following numerous hints, guide and what-not I've set up the server a couple of times and always had issues, either with booting (booted to grub_rescue) or installing grub in the first place.
Ever approach was done twice. Booted USB drive (Ubuntu Server 16.04.1) in UEFI mode and in legacy mode.
Server BIOS is set to legacy+UEFI.

I've tried to following:

4 * 4GB in RAID10, for one 8GB SWAP partition
4* ~4TB in RAID10, for one 8TB root partition
1* 1MB Reserved BIOS boot area

Failed when installing grub.

I've tried the same with reserved BIOS boot areas on all disks, which also failed.
I've tried again with an explicit /boot partition and a reserved BIOS boot area, which also failed.

Can someone give me a hint how, to get my Ubuntu server up and running with 4*4TB in RAID10?

---

### Post by darkod on 2016-10-12
Try this:
1. Set mobo to legacy boot only.
2. Create the 1MB bios grub partition on each disk, set the bios_grub flag on it, and make it be the first partition.
3. Create 2GB on each disk for a raid1 /boot array. Dont use raid10 because boot files dont like being split.
4. Create the root and swap partitions/arrays.

See if it works like that.

One thing that happened to me recently is that a nuc6 device didnt play nice with legacy boot and gpt table. I only had a small ssd so I changed to msdos and it worked fine. You might be in similar situation.
In case you have to use uefi boot so it can work with gpt, you will need the efi partition to, and it has to be first one and fat32. But I dont use uefi boot so you will need to investigate further. What I have seen mentioned is that for uefi you will need both the efi fat32 partition and the bios_grub partition (with no filesystem).

---

### Post by Vegan on 2016-10-12
get a small SSD for the system, then use the disks for storage and mount them under /JBOD

use another server for backups

---

### Post by QIII on 2016-10-12
The OP asked about RAID 10.  Please answer appropriately and stay on topic.

---

### Post by saatomic on 2016-10-13
I can't change the hardware, but I got it running with Ubuntu server 16.04.1 yesterday. I have to re-do it with 14.04.4, because of some third-party software issues.

If I recall correctly I did:

Booted USB flash drive in UEFI mode.
1MB* Reserved BIOS boot area* on each disk.
The rest on each disk as *physical volume for RAID, *which is then configured as RAID10.
The resulting 8TB partition was configured as an LVM group, with two volumes. One for SWAP the other as root.
Grub will then ask to be installed to the MBR (yes).

I'll see if that works again or if I got lucky for some reason.

**edit: **I can confirm that it works like this with Ubuntu Server 16.04.1 and 14.04.4.

---

