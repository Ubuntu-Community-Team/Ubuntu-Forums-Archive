---
title: "Hardware/FakeRAID won't activate"
date: 2011-08-01
forum: Server Platforms
---

### Post by cbuxton1984 on 2011-08-01
I'm using **Ubuntu Server 11.04**

I have a HP Microserver which uses what I thought was a hardware RAID. It now turns out that it is fakeRAID.

I'm moving from Windows 2008 so currently I have 2x2TB disks in a RAID1 and formatted to NTFS. The RAID was working fine on Windows but it doesn't seem to work on Ubuntu. I have over 1.3TB of data currently on the RAID so I cannot format and start again. I need to find some way of getting Ubuntu to mount this RAID without having to format and create a software raid.

I'm unsure why it presents itself to Ubuntu as two separate disks as the RAID was setup on the RAID Array controller before it starts to load the operating system. Windows sees the RAID as a single disk and not two separate disks (although it can if I use a disk manager).

After some digging I have found out that the RAID format is PDC because Ubuntu can see the two disks and knows that they should be in a RAID but does not want to activate them. I don't want to go any further and experiment with commands until someone responds because I'd rather not risk my data.

```

chris@Chris-Server:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000da35d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29897   240142336   83  Linux
/dev/sda2           29897       30402     4054017    5  Extended
/dev/sda5           29897       30402     4054016   82  Linux swap / Solaris

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f5e268f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243194  1953446912    7  HPFS/NTFS

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f5e268f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243194  1953446912    7  HPFS/NTFS


chris@Chris-Server:~$ sudo dmraid -r
[sudo] password for chris:
/dev/sdb: pdc, "pdc_becghiehhe", mirror, ok, 8201865344 sectors, data@ 0
/dev/sdc: pdc, "pdc_becghiehhe", mirror, ok, 8201865344 sectors, data@ 0

chris@Chris-Server:~$ sudo dmraid -s -s pdc_becghiehhe
*** Set
name   : pdc_becghiehhe
size   : 8201865344
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0

chris@Chris-Server:~$ sudo dmraid -ay
RAID set "pdc_becghiehhe" was not activated

chris@Chris-Server:~$ sudo dmraid -an
[sudo] password for chris:
RAID set "pdc_becghiehhe" is not active


```

Let me know if you need any more commands running for additional outputs.


Thanks
Chris

---

### Post by bakegoodz on 2011-08-01
Here are a couple of guides if your DMraid supports your hardware. 

[http://www.howtoforge.com/creating-a-dual-boot-system-on-raid10-ubuntu-windows](http://www.howtoforge.com/creating-a-dual-boot-system-on-raid10-ubuntu-windows)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

