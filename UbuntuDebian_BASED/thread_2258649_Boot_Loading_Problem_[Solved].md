---
title: "Boot Loading Problem [Solved]"
date: 2014-12-29
forum: Ubuntu/Debian BASED
---

### Post by Mel_Blakey on 2014-12-29
_OS: Ubuntu 14.10_

I decide to install Linux Lite 2.2 as a Dual Boot. Stupidly, I left a USB Hard Drive plugged in and it has installed the new OS to that (I assume because it is bigger than my internal HDD).
Now my machine will not boot up without the external HDD plugged in. It then gives a choice of the 2 operating systems (so, it is installed OK).
However, if I try to boot up without the external HD plugged in it tells me that the drive is missing and threatens to go into Grub Rescue, but doesn't do anything.

How can I tell my lappy that there is only one OS on its Hard Drive & it needs to bood up from that?


Thanks!

---

### Post by Bashing-om on 2014-12-29
Mel_Blakey; Hi ! Welcome to the forum .

Sounds like all that is required is to install grub (GRand Unified Bootloader) to the hard drive you want to boot from.
Show us what we are working with :
```

sudo fdisk -lu
sudo parted -l

```
and we can direct you how to install 'buntu's boot loader .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by sandyd on 2014-12-29
> **Mel_Blakey said:**
> _OS: Ubuntu 14.10_

I decide to install Linux Lite 2.2 as a Dual Boot. Stupidly, I left a USB Hard Drive plugged in and it has installed the new OS to that (I assume because it is bigger than my internal HDD).
Now my machine will not boot up without the external HDD plugged in. It then gives a choice of the 2 operating systems (so, it is installed OK).
However, if I try to boot up without the external HD plugged in it tells me that the drive is missing and threatens to go into Grub Rescue, but doesn't do anything.

How can I tell my lappy that there is only one OS on its Hard Drive & it needs to bood up from that?


Thanks!
*Moved to Other OS*

Sounds like

a) The boot loader is installed on the computer
b) The boot loader files (/boot) are installed on the external HDD
c) The OS is installed on the external HDD

If you do a reinstall of Linux Lite, it should reinstall the bootloader properly.

---

### Post by Mel_Blakey on 2014-12-29
Thanks for the help...
```
mel@Laptopdancer:~$ sudo fdisk -lu


Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0009ce2d

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 344438474 344436427 164.2G 83 Linux
/dev/sda2       344438782 625141759 280702978 133.9G  5 Extended
/dev/sda5       621778944 625141759   3362816   1.6G 82 Linux swap / Solaris
/dev/sda6       344438784 621778943 277340160 132.3G 83 Linux

Partition table entries are not in disk order.
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe24c0e94

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1             2048  586884527  586882480 279.9G  7 HPFS/NTFS/exFAT
/dev/sdb2        586887166 1953523711 1366636546 651.7G  5 Extended
/dev/sdb5        586887168  607858687   20971520    10G  7 HPFS/NTFS/exFAT
/dev/sdb6        607860736 1950160895 1342300160 640.1G 83 Linux
/dev/sdb7       1950162944 1953523711    3360768   1.6G 82 Linux swap / Solaris

mel@Laptopdancer:~$ sudo parted -l
Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  176GB  176GB   primary   ext4            boot
 2      176GB   320GB  144GB   extended
 6      176GB   318GB  142GB   logical   ext4
 5      318GB   320GB  1722MB  logical   linux-swap(v1)


Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  300GB   300GB   primary   ntfs
 2      300GB   1000GB  700GB   extended
 5      300GB   311GB   10.7GB  logical   ntfs
 6      311GB   998GB   687GB   logical   ext4
 7      998GB   1000GB  1721MB  logical   linux-swap(v1)
```

---

### Post by Mel_Blakey on 2014-12-29
Hi Sandy..
I think that you are right.... Sounds like

a) The boot loader is installed on the computer
b) The boot loader files (/boot) are installe on the external HDD
c) The OS is installed on the external HDD]

[*If you do a** reinstall of Linux Lite, it should reinstall the bootloader properly***]

Thats exactly what I did before I came on here, and it hasn't worked.

---

### Post by Bashing-om on 2014-12-29
Mel_Blakey; Hi !

Several linux installs -as well as Windows.. but I only see one with boot code .

What is installed to the drive 'sda' and in it's 1st (sda1) partition ? As only 1 linux can control the boot process ; which install do you want it to be that controlling entity ?

[INDENT][INDENT]hey, we can do that 
[/INDENT][/INDENT]

---

### Post by Mel_Blakey on 2014-12-29
Shouldn't be Windows on there..... it was wiped 10 months ago!

I found  Boot Repair  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)  and it seems to have fixed it.

Thanks for your help!

Regards
Mel.

---

### Post by Bashing-om on 2014-12-30
Mel_Blakey; Great !

Pleased you are up and running.
There is this to consider:
> 
Shouldn't be Windows on there..... it was wiped 10 months ago!

As fdisk and parted show:
> 
/dev/sdb1             2048  586884527  586882480 279.9G  7 HPFS/NTFS/exFAT
 1      1049kB  300GB   300GB   primary   ntfs

/dev/sdb5        586887168  607858687   20971520    10G  7 HPFS/NTFS/exFAT
 5      300GB   311GB   10.7GB  logical   ntfs

Where 'NTFS' is Windows partitions - maybe they are but data partitions.

In any case as the original problem has resolution;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]I wish
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mel_Blakey on 2014-12-30
Hi
Sorry, I don't understand the fdisk and parted information.
Are you suggesting that Windows is still on my Hard Drive?

Thanks for getting back to me.

---

### Post by Bashing-om on 2014-12-31
Mel_Blakey; Well, ....

> **Mel_Blakey said:**
> Hi
Sorry, I don't understand the fdisk and parted information.
Are you suggesting that Windows is still on my Hard Drive?

Thanks for getting back to me.

Presently all I can say is that there are those 2 partitions in the 2nd (sdb) drive formatted Windows file system.
IF you do not know what they are, one can investigate further .. and see if they are Windows' operating system and/or data partitions.

But be aware, I am no longer Windows literate .

[INDENT][INDENT]when inquiring minds want to know
[/INDENT][/INDENT]

---

