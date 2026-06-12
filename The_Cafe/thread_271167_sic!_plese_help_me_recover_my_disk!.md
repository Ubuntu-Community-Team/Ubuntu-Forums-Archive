---
title: "sic! plese help me recover my disk!"
date: 2006-10-04
forum: The Cafe
---

### Post by garba on 2006-10-04
hello gents today i mistakenly hosed my linux disk when setting up freebsd... now my linux disk is a dedicated bsd partition, i issued the commit command without thinking twice, too bad the disk which was plugged in wasnt exactly the disk i meant to set up on bsd on... anybody got a clue as to how i could possibly recoved my data? what about fdisking my disk again using the previous partition layout? any help would be greatly appreciated, thanks in advance

---

### Post by Polygon on 2006-10-04
you would most likely want to find some program that can recover files from deleted/formatted partitions (ext3 ones particulary)... i cant help you there as the only ones i know are for FAT and NTFS

---

### Post by garba on 2006-10-04
phew! i just fdisk'ed it again using my old partitioning schema and everything is ok now, cheers :mrgreen:

---

### Post by jdong on 2006-10-04
I was gonna say, as long as you didn't get as far as the mkfs command, fdisk should be able to write a good partition table back on :)

---

### Post by garba on 2006-10-04
yep luckily i didn't go that far, i issued the command to repartition my disk, then i slowly turned my head to my pc (well that is, the pc pieces i got laying about on my desk) and lo and behold the hd that was plugged in was my linux sata disk ](*,) luckily though the partition schema was easy to remember in terms of sectors and the like since i always partition my disks so that partitions end up being n*gibibytes in size, i have a fetish for numbers being a power of 2 :mrgreen:

---

