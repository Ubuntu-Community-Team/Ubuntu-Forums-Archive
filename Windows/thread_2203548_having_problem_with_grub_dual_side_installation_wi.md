---
title: "having problem with grub dual side installation with windows 8"
date: 2014-02-04
forum: Windows
---

### Post by vamshikrishna072 on 2014-02-04
hi,
i recently tried to install pinguy os alongside with windows 8, after installing when i restart the system the following image is shown .while installing it showed me an error to leave atleast 1 gb space for boot .here are the images 
.[ATTACH=CONFIG]250077[/ATTACH][ATTACH=CONFIG]250078[/ATTACH]

plz help me out.

pinguy@pinguy:~$ _**sudo fdisk -l**_

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x550bad2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8166 MB, 8166703104 bytes
255 heads, 63 sectors/track, 992 cylinders, total 15950592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       10648    15950590     7969971+   b  W95 FAT32

pinguy@pinguy:~$ [U][B]sudo blkid
[/B][/U]/dev/sda1: LABEL="Recovery" UUID="F6D899B7D8997699" TYPE="ntfs" 
/dev/sda2: UUID="1A9B-5995" TYPE="vfat" 
/dev/sda4: UUID="18CEA4E2CEA4B980" TYPE="ntfs" 
/dev/sda5: UUID="6a56a34b-3925-43e0-a679-a1b769798723" TYPE="ext4" 
/dev/sda6: UUID="2e8a617a-3b4a-4a97-884c-c0ee4108ab52" TYPE="swap" 
/dev/sda7: UUID="00144202-2da8-4d89-bf5e-8b175c63f293" TYPE="ext4" 
/dev/sda8: UUID="d74d0052-546c-4e43-991d-b18b124474e7" TYPE="ext4" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="UUI" UUID="F685-2B20" TYPE="vfat" 
/dev/zram0: UUID="32b8693a-9cc6-41b2-a0b2-f7a49a3f713f" TYPE="swap" 
/dev/zram1: UUID="cbc03908-2b79-4d86-8465-eb07f34b19f2" TYPE="swap" 
/dev/zram2: UUID="2cbcd063-f2b8-43b5-9269-252c8ad0bbdb" TYPE="swap" 
/dev/zram3: UUID="fc8fb375-c4b9-492b-8522-a6b6adc39a8c" TYPE="swap"

---

### Post by fantab on 2014-02-04
You should check this out with Pinguy forums. Though Pinguy is based on Ubuntu, not sure about its installer.
Meanwhile you can read through this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Bucky Ball on 2014-02-04
*Thread moved to **Other OS/Distro Support**.*

---

### Post by oldfred on 2014-02-04
The request for a 1 or 2MB bios_grub partition is for BIOS based booting on a gpt partitioned drive. 
But most gpt partitioned drives are UEFI boot and best not to mix BIOS & UEFI boot. 
See fantab's link on UEFI booting.

If mixed boot modes you can only dual boot from UEFI menu not from grub as UEFI & BIOS are not really compatible and once you start booting in one mode you cannot change to another install in the other mode.

---

