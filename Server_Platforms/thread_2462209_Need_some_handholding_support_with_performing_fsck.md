---
title: "Need some handholding support with performing fsck command."
date: 2021-05-16
forum: Server Platforms
---

### Post by mortalkorona on 2021-05-16
Hi, so I have previously shutdown my home server build by physically pressing the OFF button on the machine on many occasions. I was forced to do so because of alarms coming from my RAID card. This little maneuver seems to have damaged my operating system.

Can somebody help walk me through which options I should select when performing the **fsck** command?
Also considering which partition is damaged I'm afraid I will break the boot functionality If I choose the wrong options for **/dev/sdb1**.

I'm trying to follow this tutorial but it doesn't show which options I should select for my situation.
[https://net2.com/using-fsck-to-check-or-repair-the-file-system-in-ubuntu/](https://net2.com/using-fsck-to-check-or-repair-the-file-system-in-ubuntu/)

```

$ dmesg

EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.

# _____________________________________________________________________________

$ df -h

Filesystem                         Size  Used Avail Use% Mounted on
/dev/sdb2                          976M  201M  709M  23% /boot
/dev/sdb1                          511M  7.9M  504M   2% /boot/efi

$ sudo umount /boot/efi

# _____________________________________________________________________________

$ sudo fsck /dev/sdb1

fsck from util-linux 2.34
fsck.fat 4.1 (2017-01-24)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action

? 2


There are differences between boot sector and its backup.
This is mostly harmless. Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action

? 3


/dev/sdb1: 11 files, 2005/130812 clusters


```

---

### Post by TheFu on 2021-05-16
There aren't any options for fsck.

I'd try to use the HW-RAID to get the devices working, though we stopped using HW-RAID in 2008. SW-RAID is much more flexible. You need a battery-backed RAID card or it really isn't worth using them.

"some data may be corrupt" doesn't mean that the data **is** corrupt.  I'd start with 2 - and see how far I got.

Sometimes, the best answer to RAID issues is to wipe the array and start over.  You do have backups, right? RAID never replaces backups. NEVER.

---

### Post by mortalkorona on 2021-05-16
**Description**
Hi @TheFu, it's my first time building a home server, using consumer grade components. I just wanted to be able to fill up my PC chassi with 18 HDD disks in the future, whenever my budget would allow for it. Today my home server build only has 1 HDD disk connected to my HBA RAID expansion card.

**Adaptec ASR 71605 1GB 16Port HBA RAID PCIe Controller Card w/ Battery 4x Cables**
[https://www.ebay.com/itm/Adaptec-ASR-71605-1GB-16Port-HBA-RAID-PCIe-Controller-Card-w-Battery-4x-Cables/353020685999](https://www.ebay.com/itm/Adaptec-ASR-71605-1GB-16Port-HBA-RAID-PCIe-Controller-Card-w-Battery-4x-Cables/353020685999)

My HBA RAID order came from some unknown seller/shop so the product didn't come in an original packaging from the manufacturer. No manual was included with my shipment, so I don't really know what kind of beginner setup I need to perform in BIOS menu for my RAID card.

.................................................

**Question-1**
_ Do I need to perform some kind of setup for my RAID via BIOS menu?_ I just want to be able to connect 18 HDD disks separated from eachother to my motherboard in the future. Without any fancy RAID hocus pocus.

.................................................

** Questions-2**
This is the YouTube build tutorial I'm roughly following. In the video Caleb Curry removed the battery pack from the HBA RAID card. Is it necessary for the battery pack to be connected? Isn't it enough that the HBA RAID card get its power from the PCIexpress slot?

YouTuber: Coin Breakthrough, Caleb Curry
** COMPLETE Build for Chia Farming (360TB Capacity Hard Drive Mining)** - TimeIndex 31 minutes
[https://youtu.be/BQ6zM1izXQs?t=1861]("https://youtu.be/BQ6zM1izXQs?t=1861")

.................................................

---

### Post by rsteinmetz70112 on 2021-05-16
You can get the documentation for your card here:
[https://storage.microsemi.com/en-us/support/raid/sas_raid/sas-71605/](https://storage.microsemi.com/en-us/support/raid/sas_raid/sas-71605/)

---

### Post by mortalkorona on 2021-05-17
> **rsteinmetz70112 said:**
> You can get the documentation for your card here:
[https://storage.microsemi.com/en-us/support/raid/sas_raid/sas-71605/](https://storage.microsemi.com/en-us/support/raid/sas_raid/sas-71605/)

Thanks will take a look at their manuals.

---

