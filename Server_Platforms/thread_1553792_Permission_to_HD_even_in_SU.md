---
title: "Permission to HD even in SU?"
date: 2010-08-15
forum: Server Platforms
---

### Post by 1serveyou on 2010-08-15
I'm trying to mount my 1tb hitachi sata hd, and I had the same exact one that automatically mounted a few months ago. One day, I turned off the server with the power button as I was in a rush, and I could never get the server to recognize that hard drive again. Luckily, I bought 2 of them and hadn't installed the other, but when I tried to install the other HD, it wouldn't recognize it either(I hadn't formatted it or anything as I thought I could do that with ubuntu). Then I plugged in the original(and the backup) into an enclosure and my ubuntu desktop recognizes it. I thought it might have been the computer Mac G5 running 9.04 with 7gb of ram, so I swapped the HD and ram into a different case and still the same problems. 

I have the the backup in right now, and I can see if it I use ls -l /dev/disk/by-id/

total 0
lrwxrwxrwx 1 root root  9 2010-08-14 15:21 ata-Hitachi_HDS721010CLA332_JP2911HQ1V7HXA -> ../../sdb
lrwxrwxrwx 1 root root 10 2010-08-14 15:21 ata-Hitachi_HDS721010CLA332_JP2911HQ1V7HXA-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 2010-08-14 15:21 ata-ST3160023AS_5MT0RPAR -> ../../sda
lrwxrwxrwx 1 root root 10 2010-08-14 15:21 ata-ST3160023AS_5MT0RPAR-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-08-14 15:21 ata-ST3160023AS_5MT0RPAR-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-08-14 15:21 ata-ST3160023AS_5MT0RPAR-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2010-08-14 15:21 ata-ST3160023AS_5MT0RPAR-part4 -> ../../sda4
lrwxrwxrwx 1 root root  9 2010-08-14 15:21 scsi-SATA_Hitachi_HDS7210_JP2911HQ1V7HXA -> ../../sdb
lrwxrwxrwx 1 root root 10 2010-08-14 15:21 scsi-SATA_Hitachi_HDS7210_JP2911HQ1V7HXA-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 2010-08-14 15:21 scsi-SATA_ST3160023AS_5MT0RPAR -> ../../sda
lrwxrwxrwx 1 root root 10 2010-08-14 15:21 scsi-SATA_ST3160023AS_5MT0RPAR-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-08-14 15:21 scsi-SATA_ST3160023AS_5MT0RPAR-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-08-14 15:21 scsi-SATA_ST3160023AS_5MT0RPAR-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2010-08-14 15:21 scsi-SATA_ST3160023AS_5MT0RPAR-part4 -> ../../sda4

When I type /dev/sdb1 or /dev/sdb, both say permission denied even when I use SU and/or sudo.

Any help would greatly be appreciated. I'm really confused as when I installed the first hard drive(that errored) I didn't have any problems.

---

### Post by 1serveyou on 2010-08-15
I ran fsck, and I received: bad magic number in superblock while trying to open /dev/sdb1

This drive has never been used other than when I tried to format it on my ubuntu laptop with disk utility. What is the best way to fix this?

Thank you in advance and I appreciate any advice!

---

