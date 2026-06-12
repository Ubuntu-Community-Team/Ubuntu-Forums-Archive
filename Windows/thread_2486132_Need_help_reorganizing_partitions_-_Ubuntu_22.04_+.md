---
title: "Need help reorganizing partitions - Ubuntu 22.04 + Windows 10 &amp; 11 - two hard drives"
date: 2023-04-20
forum: Windows
---

### Post by lord-tatien on 2023-04-20
Hi,

I need help reorganizing my partitions. I have a 512Gb drive  (drive 1 - /dev/nvme0n1) with Windows 11; and a 1Tb drive (drive 2 - /dev/nvme1n1) with a dual Windows 10 + Ubuntu 22.04 install.

What I would like would be to:
- erase Windows 10 on drive 2
- replace it with the Windows 11 from drive 1
- format drive 1 as ext4 to use as an extra drive

I only use Windows sporadically so the 139.4G partition with my Windows 10 on it is plenty.
I tried copying the Windows 11 partition over the Windows 10 partition using dd but it crashed upon boot, so I wonder if there is something to adjust in the EFI partition.

How should I do this?

Here are outputs of fdisk and lsblk (there were a lot of loop partitions which were created by snap, I chose not to include them here for clarity).

```

% fdisk -lu
Disk /dev/nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: INTEL SSDPEKNU512GZ                     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: DBE52380-99A1-42EB-9ABE-E99FAC357C38

Device             Start        End   Sectors   Size Type
/dev/nvme0n1p1      2048     534527    532480   260M EFI System
/dev/nvme0n1p2    534528     567295     32768    16M Microsoft reserved
/dev/nvme0n1p3    567296  952232590 951665295 453.8G Microsoft basic data
/dev/nvme0n1p4 952233984  953667583   1433600   700M Windows recovery environment
/dev/nvme0n1p5 953667584  999804927  46137344    22G Microsoft basic data
/dev/nvme0n1p6 999804928 1000214527    409600   200M Windows recovery environment


Disk /dev/nvme1n1: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk model: WDC PC SN720 SED SDAQNTW-1T00           
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 63F9EA36-146E-4406-B8F9-E335107C63F7

Device              Start        End    Sectors   Size Type
/dev/nvme1n1p1       2048     206847     204800   100M EFI System
/dev/nvme1n1p2     206848     239615      32768    16M Microsoft reserved
/dev/nvme1n1p3     239616  292486328  292246713 139.4G Microsoft basic data
/dev/nvme1n1p4  292487168  293859327    1372160   670M Windows recovery environment
/dev/nvme1n1p5  293861376 1998295039 1704433664 812.7G Linux filesystem
/dev/nvme1n1p6 1998295040 2000392191    2097152     1G Windows recovery environment


```

```

% lsblk -f -m
nvme0n1                                                                                                                         476.9G root  disk  brw-rw----
&#9500;&#9472;nvme0n1p1 vfat     FAT32 SYSTEM    32C1-3C1B                                                                                     260M root  disk  brw-rw----
&#9500;&#9472;nvme0n1p2                                                                                                                        16M root  disk  brw-rw----
&#9500;&#9472;nvme0n1p3 ntfs           OS        34C2C31CC2C2E16A                                                                            453.8G root  disk  brw-rw----
&#9500;&#9472;nvme0n1p4 ntfs           RECOVERY  0ABC8ABEBC8AA3B3                                                                              700M root  disk  brw-rw----
&#9500;&#9472;nvme0n1p5 ntfs           RESTORE   38D46912D468D3A2                                                                               22G root  disk  brw-rw----
&#9492;&#9472;nvme0n1p6 vfat     FAT32 MYASUS    F869-3A4C                                                                                     200M root  disk  brw-rw----
nvme1n1                                                                                                                         953.9G root  disk  brw-rw----
&#9500;&#9472;nvme1n1p1 vfat     FAT32 ESP       961F-ADBB                                23M    76%  /boot/efi                                100M root  disk  brw-rw----
&#9500;&#9472;nvme1n1p2                                                                                                                        16M root  disk  brw-rw----
&#9500;&#9472;nvme1n1p3 ntfs           OS        34C2C31CC2C2E16A                                                                            139.4G root  disk  brw-rw----
&#9500;&#9472;nvme1n1p4 ntfs                     44B2DD7EB2DD7540                                                                              670M root  disk  brw-rw----
&#9500;&#9472;nvme1n1p5 ext4     1.0             7e939baa-c704-4ef9-81fd-4deaaee448a1   67.3G    86%  /var/snap/firefox/common/host-hunspell 812.7G root  disk  brw-rw----
&#9474;                                                                                        /                                                         
&#9492;&#9472;nvme1n1p6  ntfs           Recovery  141622D61622B91E                                                                                1G root  disk  brw-rw----

```

---

### Post by oldfred on 2023-04-20
Moved to Windows sub-forum, since really Windows issues.
You may do better in a Windows forum.

Do not know Windows.
But dd is for same size to same size or larger. 
Also with gpt it is difficult to use dd to copy a partition. The gpt partition table has GUID in primary partition table, partition & backup partition table. So if you attempt to image copy one partition you get GUIDs out of sync.  May be repairable, but not sure how. (gdisk?)

UEFI boot uses GUID of ESP to know which partition to boot. With Ubuntu then the ESP has more boot code, mostly grub to load the full grub.cfg in your install. Not sure Windows boot process but it has files in ESP. Probably BCD has the detail UUID & GUID type info that Windows uses.

---

