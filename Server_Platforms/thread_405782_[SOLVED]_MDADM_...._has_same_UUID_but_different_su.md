---
title: "[SOLVED] MDADM: .... has same UUID but different superblock to ...."
date: 2007-04-10
forum: Server Platforms
---

### Post by djamu on 2007-04-10
I consider following -until further notice- as a bug since 'm able to reproduce it.

A couple of months ago it was the first time I ran into this particular problem - 1 x RAID 5 + usb ipod -edgy 2.6.17-10-generic

I use RAID's on about every computer I own, usually RAID 5 / 6 for servers RAID 0 for the desktops. 

Short story & current situation: 
Desktop with 1 array RAID 5 + 1array RAID 0. running edgy -2.6.17-11-generic-
+ automounted ( usb ) disk ( any )
Raid5 = 4 x 160gb > 2 x PATA + 2 x SATA     (sda1 + sdb1 + hdg1 + hdh1)
Raid0 = 2 x 80gb PATA                                  (hdc1 + hdd1
all single partitions 
+ 40 gb system HD
(hda 1-6 )     1=ntfs      2=/      3=swap      4=logical      5=/home      6=/geexbox  


**Chronology**

Boot without USB disk into Desktop > attach USB disk ( automount ) > shutdown > remove USB disk > reboot > mdadm error.......

The automount of the USB-disk causes a shift in UUID mdadm identifiers.


**dmesg | grep md**
```

root@ubuntu:/home/jan# dmesg | grep md
[17179574.684000] ata1: SATA max UDMA/133 cmd 0xA000 ctl 0xA402 bmdma 0xB000 irq 177
[17179574.684000] ata2: SATA max UDMA/133 cmd 0xA800 ctl 0xAC02 bmdma 0xB008 irq 177
[17179579.824000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179579.824000] md: bitmap version 4.39
[17179579.824000] md: raid0 personality registered for level 0
[17179579.940000] md: raid5 personality registered for level 5
[17179579.940000] md: raid4 personality registered for level 4
[17179580.548000] md: md0 stopped.
[17179580.584000] md: bind<hdd1>
[17179580.588000] md: bind<hdc1>
[17179580.592000] md0: setting max_sectors to 128, segment boundary to 32767
[17179580.596000] raid0 : md_size is 156296192 blocks.
[17179580.624000] md: md1 stopped.
[17179580.644000] md: bind<sdb1>
[17179580.644000] md: hdg1 has same UUID but different superblock to sdb1
[17179580.644000] md: hdg1 has different UUID to sdb1
[17179580.644000] md: export_rdev(hdg1)
[17179580.644000] md: hdh1 has same UUID but different superblock to sdb1
[17179580.644000] md: hdh1 has different UUID to sdb1
[17179580.644000] md: export_rdev(hdh1)
[17179580.644000] md: sda1 has same UUID but different superblock to sdb1
[17179580.644000] md: sda1 has different UUID to sdb1
[17179580.644000] md: export_rdev(sda1)
[17179580.656000] md: md1 stopped.
[17179580.656000] md: unbind<sdb1>
[17179580.656000] md: export_rdev(sdb1)
[17179580.676000] md: bind<sdb1>
[17179580.676000] md: hdg1 has same UUID but different superblock to sdb1
[17179580.676000] md: hdg1 has different UUID to sdb1
[17179580.676000] md: export_rdev(hdg1)
[17179580.676000] md: hdh1 has same UUID but different superblock to sdb1
[17179580.676000] md: hdh1 has different UUID to sdb1
[17179580.676000] md: export_rdev(hdh1)
[17179580.676000] md: sda1 has same UUID but different superblock to sdb1
[17179580.676000] md: sda1 has different UUID to sdb1
[17179580.676000] md: export_rdev(sda1)
[17179580.688000] md: md1 stopped.
[17179580.688000] md: unbind<sdb1>
[17179580.688000] md: export_rdev(sdb1)
[17179580.708000] md: bind<sdb1>
[17179580.708000] md: hdg1 has same UUID but different superblock to sdb1
[17179580.708000] md: hdg1 has different UUID to sdb1
[17179580.708000] md: export_rdev(hdg1)
[17179580.708000] md: hdh1 has same UUID but different superblock to sdb1
[17179580.708000] md: hdh1 has different UUID to sdb1
[17179580.708000] md: export_rdev(hdh1)
[17179580.708000] md: sda1 has same UUID but different superblock to sdb1
[17179580.708000] md: sda1 has different UUID to sdb1
[17179580.708000] md: export_rdev(sda1)
[17179580.724000] md: md1 stopped.
[17179580.724000] md: unbind<sdb1>
[17179580.724000] md: export_rdev(sdb1)
[17179580.740000] md: bind<sdb1>
[17179580.740000] md: hdg1 has same UUID but different superblock to sdb1
[17179580.740000] md: hdg1 has different UUID to sdb1
[17179580.740000] md: export_rdev(hdg1)
[17179580.740000] md: hdh1 has same UUID but different superblock to sdb1
[17179580.740000] md: hdh1 has different UUID to sdb1
[17179580.740000] md: export_rdev(hdh1)
[17179580.740000] md: sda1 has same UUID but different superblock to sdb1
[17179580.740000] md: sda1 has different UUID to sdb1
[17179580.740000] md: export_rdev(sda1)
[17179592.412000] md: md1 stopped.
[17179592.412000] md: unbind<sdb1>
[17179592.412000] md: export_rdev(sdb1)
[17179592.988000] md: md1 stopped.


```
huh?

now here comes the fun

**mdadm -E /dev/hdc1** -do mind that i'm queriing hdc1
```

root@ubuntu:/# mdadm -E /dev/hdc1
/dev/hdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 23d10d44:d59ed967:79f65471:854ffca8
  Creation Time : Mon Apr  9 21:21:13 2007
     Raid Level : raid0
    Device Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1

    Update Time : Mon Apr  9 21:21:13 2007
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2e17ac36 - correct
         Events : 0.1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0      34        1        0      active sync   **/dev/hdg1**

   0     0      34        1        0      active sync   **/dev/hdg1**
   1     1      34       65        1      active sync   **/dev/hdh1**


```

mmm great..
root@ubuntu:/# mdadm -E /dev/hdd1  gives the same result..

**mdadm -E /dev/hdg1**
**mdadm -E /dev/hdh1**
**mdadm -E /dev/sda1**
all give
```

          Magic : a92b4efc
        Version : 00.90.03
           UUID : 8d754c1d:5895bb70:c89ffdee:815a6cef
  Creation Time : Sun Sep 10 22:51:43 2006
     Raid Level : raid5
    Device Size : 156288256 (149.05 GiB 160.04 GB)
     Array Size : 468864768 (447.14 GiB 480.12 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Tue Apr 10 06:27:47 2007
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 6da64f0f - correct
         Events : 0.138537

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2      22        1        2      active sync   **/dev/hdc1**

   0     0       8        1        0      active sync   **/dev/sda1**
   1     1       0        0        1      faulty removed
   2     2      22        1        2      active sync   **/dev/hdc1**
   3     3      22       65        3      active sync   **/dev/hdd1**
root@ubuntu:/# 

```

**mdadm -E /dev/sdb1**
```
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.03
           UUID : 8d754c1d:5895bb70:c89ffdee:815a6cef
  Creation Time : Sun Sep 10 22:51:43 2006
     Raid Level : raid5
    Device Size : 156288256 (149.05 GiB 160.04 GB)
     Array Size : 468864768 (447.14 GiB 480.12 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 1

    Update Time : Tue Apr 10 03:33:36 2007
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 6da62247 - correct
         Events : 0.138011

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       0        0        0      removed
   1     1       8       17        1      active sync   /dev/sdb1
   2     2      34        1        2      active sync   /dev/hdg1
   3     3      34       65        3      active sync   /dev/hdh1

```

the UUID of the MD arrays are correct

**mdadm -Es**
```
root@ubuntu:/# mdadm -Es
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=23d10d44:d59ed967:79f65471:854ffca8
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=8d754c1d:5895bb70:c89ffdee:815a6cef

```
```

root@ubuntu:/# vim /etc/mdadm/mdadm.conf 

DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=8d754c1d:5895bb70:c89ffdee:815a6cef
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=23d10d44:d59ed967:79f65471:854ffca8

```

**/bin/ls -lF /dev/disk/by-uuid/**
```
root@ubuntu:/# /bin/ls -lF /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2007-04-10 13:57 06A8AAD0A8AABD95 -> ../../hda1
lrwxrwxrwx 1 root root 10 2007-04-10 13:57 9b4b2558-8dde-465b-9f65-1284fdd2ff3c -> ../../hda3
lrwxrwxrwx 1 root root 10 2007-04-10 13:57 d1d98405-e8b7-49ea-85e2-561948df039d -> ../../hda6
lrwxrwxrwx 1 root root  9 2007-04-10 13:57 d9f37014-fb31-4f17-8199-923cd2f97afb -> ../../md0
lrwxrwxrwx 1 root root 10 2007-04-10 13:57 dff589e8-2ec8-4dd5-bc79-37a859abfcfb -> ../../hda2
lrwxrwxrwx 1 root root 10 2007-04-10 13:57 eb19f899-a80d-48e5-9216-a0c7838e3594 -> ../../hda5

```

fstab UUID's are ok to ( I did comment out both md0 + md1 to get rid of all error messages )

**root@ubuntu:/# vim /etc/fstab**
```

root@ubuntu:/# vim /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hde2
UUID=dff589e8-2ec8-4dd5-bc79-37a859abfcfb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hde5
UUID=eb19f899-a80d-48e5-9216-a0c7838e3594 /home           reiserfs defaults        0       2
# /dev/md1
#UUID=d9f37014-fb31-4f17-8199-923cd2f97afb /media/160gb-stripe reiserfs defaults        0       2
# /dev/md0
#UUID=37a6443d-102e-4de7-86a8-d5710272533e /media/480gb-raid reiserfs defaults        0       2
# /dev/hde6
UUID=d1d98405-e8b7-49ea-85e2-561948df039d /media/rescue   ext3    defaults        0       2
# /dev/hde1
UUID=06A8AAD0A8AABD95 /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hde3
UUID=1ed13d0d-fbaa-4d21-be84-48ef91baca0a none            swap    sw              0       0
/dev/hdf        /media/cdrom0   udf,iso9660 user,noauto     0       0


```

What am I missing here ?  
-a fix is reinstalling ubuntu , RAID is just fine after reinstall

Thanks in advance

Jan

---

### Post by glenstewart on 2007-04-23
Have you seen [this bug report]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497/")?

---

### Post by djamu on 2007-04-24
Ok. thanks glenstewart,


Meanwhile I've stumbled upon a similar yet different resolved problem here.

[http://ubuntuforums.org/showthread.php?t=410136]("http://ubuntuforums.org/showthread.php?t=410136")

---

