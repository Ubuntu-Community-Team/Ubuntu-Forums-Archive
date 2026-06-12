---
title: "Windows bootmanager"
date: 2008-12-09
forum: Windows
---

### Post by ronnielsen1 on 2008-12-09
What I'm wondering is I have grub running with an option to kick in Vista bootloader for Vista or XP. Now if I drag hdb5 (XP) over and get rid of hdb2 (Vista) this will (I assume) get rid of vistas bootloader. Now, where would windows xp loader be? Will I be able to point grub in the right direction for xp to take over or will this knockout xp? Is XP smart enough to not freak out about more space?

---

### Post by caljohnsmith on 2008-12-09
> **ronnielsen1 said:**
> What I'm wondering is I have grub running with an option to kick in Vista bootloader for Vista or XP. Now if I drag hdb5 (XP) over and get rid of hdb2 (Vista) this will (I assume) get rid of vistas bootloader. Now, where would windows xp loader be? Will I be able to point grub in the right direction for xp to take over or will this knockout xp? Is XP smart enough to not freak out about more space?
I'm not understanding, what exactly do you mean by "drag hdb5 (XP) over and get rid of hdb2 (Vista)"? Would this be in Ubuntu's partition editor gparted? Or are you going to copy all of XP's files over into the Vista partition? What exactly is your ultimate goal? How about first opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
So I can get an idea of what your setup is.

---

### Post by ronnielsen1 on 2008-12-09
I tried to post a screenshot of gparted but it wouldn't let me earlier. Yes I was talking about gparted. I'm trying to get rid of vista and make xp bigger but I'[m not sure of where windows stores it's boot files.

[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/snapshot5.png[/IMG]


> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00039ec7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   412083315   415408769     1662727+  82  Linux swap / Solaris
/dev/sda2       415408770   488392064    36491647+   5  Extended
/dev/sda3              63   412083314   206041626   83  Linux
/dev/sda5       415408833   488392064    36491616   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      411647      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2          411648    46540304    23064328+   7  HPFS/NTFS
/dev/sdb3        46540305   156232124    54845910    f  W95 Ext'd (LBA)
/dev/sdb5        46540368   156232124    54845878+   7  HPFS/NTFS


Vista is on sdb2 and xp is on sdb5

---

### Post by caljohnsmith on 2008-12-09
Since you installed Windows XP to a logical partition (sdb5), XP would have put its boot files in a primary NTFS/FAT partition, which would be either sdb1 or sdb2. But did you install XP after or before Vista? Also, I would definitely not recommend moving the XP partition, because if you move the beginning point of the XP partition, XP for sure won't boot after that. I have a friend who once moved the beginning of a Windows partition, and to get Windows booting again he had to fix the XP boot sector and also modify a bunch of XP's registry entries; I don't know how reliable that process is, so I would definitely not recommend trying to move XP's starting sector.

What you could do though is restore XP's boot files to the sdb5 partition, and then boot XP from sdb5 via your Grub menu. That takes just a little work usually, because you have to modify XP's boot.ini file to point to the correct logical partition (sdb5), and sometimes you have to fix XP's boot sector. That's not a big deal though, and I can help you do that if you want. So if you want to make XP bigger, I think your best bet might be to keep it where it is and just turn the Vista partition into a storage partition for all your personal documents; then the current 11 GB XP partition should be adequate I would guess just for XP's programs and system files. Let me know what you would like to do if you would like some help.

---

