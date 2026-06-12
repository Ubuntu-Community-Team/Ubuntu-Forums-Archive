---
title: "Ubuntu Netbook installation problem after two failed installation attempts"
date: 2010-09-28
forum: Ubuntu Moblin Remix
---

### Post by rebelsoul on 2010-09-28
Hello, 

I am newbie to Ubuntu, i was trying to install ubuntu on my EEE PC 1005HA. I used Ubuntu netbook and followed every procedure and in the end managed to run a dual boot system (Wind xp and Ubuntu). While working on ubuntu i allowed updates, after updates and reboot when i tried to logged in to the system, it gave me Unknown device Grub Rescue message. I tried to run EEE PC recovery mode, but it was not working. So after spending many hours and trying to solve the problem. i did another installation on one of the other partitioned through live cd. While doing that i selected option Where Ubuntu and other OS could work together. That installation was successful and i was able to log on two Ubuntus and one win xp. However, tempted by my curiosity i tried to revert the whole system back by EE PC recovery tool, which was working at that time. The end result of all this step was that my whole system crashed again, as grub is corrupted and this time error message is Unknown file system. I tried to follow the solution provided on this forum but no avail and now my system after getting boot from live cd become busy after few minutes. I could see a huge number of my partitions which is impossible as i have only 160 GB and there are almost 60 partition of 34 GB each 
Here is a result after fdisk.[HTML]ubuntu@ubuntu:~$ sudo fdisk -lu
Warning: omitting partitions after #60.
They will be deleted if you save this partition table.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0261f0b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81160201    40580069+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        81162238   302230844   110534303+   f  W95 Ext'd (LBA)
/dev/sda3       302230845   312480314     5124735    c  W95 FAT32 (LBA)
/dev/sda4       312480315   312576704       48195   ef  EFI (FAT-12/16/32)
/dev/sda5       151123518   188512263    18694373    7  HPFS/NTFS
/dev/sda6       224845741   291837868    33496064   83  Linux
/dev/sda7       148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda8        81162240   148154367    33496064   83  Linux
/dev/sda9       148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda10       81162240   148154367    33496064   83  Linux
/dev/sda11      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda12       81162240   148154367    33496064   83  Linux
/dev/sda13      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda14       81162240   148154367    33496064   83  Linux
/dev/sda15      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda16       81162240   148154367    33496064   83  Linux
/dev/sda17      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda18       81162240   148154367    33496064   83  Linux
/dev/sda19      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda20       81162240   148154367    33496064   83  Linux
/dev/sda21      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda22       81162240   148154367    33496064   83  Linux
/dev/sda23      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda24       81162240   148154367    33496064   83  Linux
/dev/sda25      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda26       81162240   148154367    33496064   83  Linux
/dev/sda27      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda28       81162240   148154367    33496064   83  Linux
/dev/sda29      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda30       81162240   148154367    33496064   83  Linux
/dev/sda31      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda32       81162240   148154367    33496064   83  Linux
/dev/sda33      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda34       81162240   148154367    33496064   83  Linux
/dev/sda35      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda36       81162240   148154367    33496064   83  Linux
/dev/sda37      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda38       81162240   148154367    33496064   83  Linux
/dev/sda39      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda40       81162240   148154367    33496064   83  Linux
/dev/sda41      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda42       81162240   148154367    33496064   83  Linux
/dev/sda43      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda44       81162240   148154367    33496064   83  Linux
/dev/sda45      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda46       81162240   148154367    33496064   83  Linux
/dev/sda47      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda48       81162240   148154367    33496064   83  Linux
/dev/sda49      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda50       81162240   148154367    33496064   83  Linux
/dev/sda51      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda52       81162240   148154367    33496064   83  Linux
/dev/sda53      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda54       81162240   148154367    33496064   83  Linux
/dev/sda55      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda56       81162240   148154367    33496064   83  Linux
/dev/sda57      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda58       81162240   148154367    33496064   83  Linux
/dev/sda59      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda60       81162240   148154367    33496064   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf49f8b33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     2015231     1007600    b  W95 FAT32[/HTML]

Kindly help me to restore my system to it previous state and restore Grub.

---

### Post by coolman98 on 2010-09-28
admin move to general help please he will get more help.

---

### Post by rebelsoul on 2010-09-29
Hello coolman98, 
I have moved my post to Gen area however still i haven't got any reply. Could you please help me in solving my problem?

---

