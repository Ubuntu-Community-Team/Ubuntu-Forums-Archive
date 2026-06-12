---
title: "Error burning ISO DVDs"
date: 2009-02-24
forum: Ubuntu Studio
---

### Post by Cha0tik on 2009-02-24
I tried burning 2 different ISO images on 2 different brands of blank media (Verbatim and BenQ) using 2 different applications (Brasero and K3B).

This is the error I get with K3B:

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-11-generic
Devices
-----------------------
BENQ DVD DD DW1620 B7W9 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R, Restricted Overwrite]

Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 12.3x1352KBps.
   25788416/4119920640 ( 0.6%) @5.4x, remaining 13:13 RBU 100.0% UBU   9.5%
   57049088/4119920640 ( 1.4%) @6.8x, remaining 10:40 RBU 100.0% UBU  85.7%
   88801280/4119920640 ( 2.2%) @6.9x, remaining 9:04 RBU 100.0% UBU  85.7%
  121077760/4119920640 ( 2.9%) @7.0x, remaining 8:15 RBU 100.0% UBU  85.7%
  153812992/4119920640 ( 3.7%) @7.1x, remaining 8:09 RBU 100.0% UBU  85.7%
  187006976/4119920640 ( 4.5%) @7.2x, remaining 7:42 RBU 100.0% UBU  85.7%
  220725248/4119920640 ( 5.4%) @7.3x, remaining 7:21 RBU 100.0% UBU  85.7%
  254935040/4119920640 ( 6.2%) @7.4x, remaining 7:19 RBU 100.0% UBU  85.7%
  289570816/4119920640 ( 7.0%) @7.5x, remaining 7:03 RBU 100.0% UBU  85.7%
  324763648/4119920640 ( 7.9%) @7.6x, remaining 6:49 RBU 100.0% UBU  85.7%
  360349696/4119920640 ( 8.7%) @7.7x, remaining 6:46 RBU 100.0% UBU  76.2%
  396492800/4119920640 ( 9.6%) @7.8x, remaining 6:34 RBU 100.0% UBU  85.7%
  433160192/4119920640 (10.5%) @7.9x, remaining 6:23 RBU 100.0% UBU  85.7%
  470220800/4119920640 (11.4%) @8.0x, remaining 6:20 RBU 100.0% UBU  85.7%
  486834176/4119920640 (11.8%) @3.6x, remaining 6:28 RBU 100.0% UBU  85.7%
  515276800/4119920640 (12.5%) @6.2x, remaining 6:24 RBU 100.0% UBU  85.7%
  553418752/4119920640 (13.4%) @8.2x, remaining 6:20 RBU 100.0% UBU  85.7%
  592019456/4119920640 (14.4%) @8.4x, remaining 6:09 RBU 100.0% UBU  85.7%
  631144448/4119920640 (15.3%) @8.5x, remaining 5:59 RBU 100.0% UBU  85.7%
  671055872/4119920640 (16.3%) @8.6x, remaining 5:54 RBU 100.0% UBU  85.7%
  687865856/4119920640 (16.7%) @3.6x, remaining 5:59 RBU 100.0% UBU  76.2%
  687865856/4119920640 (16.7%) @0.0x, remaining 6:14 RBU 100.0% UBU 100.0%
  687865856/4119920640 (16.7%) @0.0x, remaining 6:34 RBU 100.0% UBU 100.0%
  687865856/4119920640 (16.7%) @0.0x, remaining 6:49 RBU 100.0% UBU 100.0%
  687865856/4119920640 (16.7%) @0.0x, remaining 7:04 RBU 100.0% UBU 100.0%
  714506240/4119920640 (17.3%) @5.8x, remaining 7:04 RBU 100.0% UBU  85.7%
  755105792/4119920640 (18.3%) @8.8x, remaining 6:49 RBU 100.0% UBU  85.7%
  796262400/4119920640 (19.3%) @8.9x, remaining 6:36 RBU 100.0% UBU  85.7%
  837812224/4119920640 (20.3%) @9.0x, remaining 6:27 RBU 100.0% UBU  76.2%
  879853568/4119920640 (21.4%) @9.1x, remaining 6:15 RBU 100.0% UBU  85.7%
  879853568/4119920640 (21.4%) @0.0x, remaining 6:26 RBU 100.0% UBU 100.0%
  879853568/4119920640 (21.4%) @0.0x, remaining 6:41 RBU 100.0% UBU 100.0%
  879853568/4119920640 (21.4%) @0.0x, remaining 6:52 RBU 100.0% UBU 100.0%
  879853568/4119920640 (21.4%) @0.0x, remaining 7:03 RBU 100.0% UBU 100.0%
  879853568/4119920640 (21.4%) @0.0x, remaining 7:18 RBU 100.0% UBU 100.0%
  879853568/4119920640 (21.4%) @0.0x, remaining 7:29 RBU 100.0% UBU 100.0%
  879853568/4119920640 (21.4%) @0.0x, remaining 7:40 RBU 100.0% UBU 100.0%
  879853568/4119920640 (21.4%) @0.0x, remaining 7:55 RBU 100.0% UBU 100.0%
  879853568/4119920640 (21.4%) @0.0x, remaining 8:06 RBU 100.0% UBU 100.0%
  879853568/4119920640 (21.4%) @0.0x, remaining 8:17 RBU 100.0% UBU 100.0%
  921600000/4119920640 (22.4%) @9.0x, remaining 8:02 RBU 100.0% UBU  85.7%
  964624384/4119920640 (23.4%) @9.3x, remaining 7:44 RBU 100.0% UBU  85.7%
  976486400/4119920640 (23.7%) @2.6x, remaining 7:46 RBU 100.0% UBU  42.9%
  976486400/4119920640 (23.7%) @0.0x, remaining 7:59 RBU 100.0% UBU 100.0%
  976486400/4119920640 (23.7%) @0.0x, remaining 8:09 RBU 100.0% UBU 100.0%
  976486400/4119920640 (23.7%) @0.0x, remaining 8:22 RBU 100.0% UBU 100.0%
  976486400/4119920640 (23.7%) @0.0x, remaining 8:31 RBU 100.0% UBU 100.0%
  976486400/4119920640 (23.7%) @0.0x, remaining 8:41 RBU 100.0% UBU 100.0%
  976486400/4119920640 (23.7%) @0.0x, remaining 8:54 RBU 100.0% UBU 100.0%
  976486400/4119920640 (23.7%) @0.0x, remaining 9:04 RBU 100.0% UBU 100.0%
  976486400/4119920640 (23.7%) @0.0x, remaining 9:13 RBU 100.0% UBU 100.0%
  976486400/4119920640 (23.7%) @0.0x, remaining 9:26 RBU 100.0% UBU 100.0%
  976486400/4119920640 (23.7%) @0.0x, remaining 9:36 RBU 100.0% UBU 100.0%
  981794816/4119920640 (23.8%) @1.1x, remaining 9:41 RBU 100.0% UBU  85.7%
  981794816/4119920640 (23.8%) @0.0x, remaining 9:54 RBU 100.0% UBU 100.0%
  981794816/4119920640 (23.8%) @0.0x, remaining 10:04 RBU 100.0% UBU 100.0%
  981794816/4119920640 (23.8%) @0.0x, remaining 10:13 RBU 100.0% UBU 100.0%
  981794816/4119920640 (23.8%) @0.0x, remaining 10:26 RBU 100.0% UBU 100.0%
 1022361600/4119920640 (24.8%) @8.8x, remaining 10:02 RBU 100.0% UBU  85.7%
 1063780352/4119920640 (25.8%) @9.0x, remaining 9:40 RBU 100.0% UBU  76.2%
 1063780352/4119920640 (25.8%) @0.0x, remaining 9:51 RBU 100.0% UBU 100.0%
 1063780352/4119920640 (25.8%) @0.0x, remaining 10:00 RBU 100.0% UBU 100.0%
 1100873728/4119920640 (26.7%) @8.0x, remaining 9:41 RBU 100.0% UBU  85.7%
 1138393088/4119920640 (27.6%) @8.1x, remaining 9:25 RBU 100.0% UBU  66.7%
 1138393088/4119920640 (27.6%) @0.0x, remaining 9:33 RBU 100.0% UBU 100.0%
 1164017664/4119920640 (28.3%) @5.5x, remaining 9:23 RBU 100.0% UBU  85.7%
 1209663488/4119920640 (29.4%) @9.9x, remaining 9:03 RBU 100.0% UBU  81.0%
 1255866368/4119920640 (30.5%) @10.0x, remaining 8:42 RBU 100.0% UBU  85.7%
 1302495232/4119920640 (31.6%) @10.1x, remaining 8:21 RBU 100.0% UBU  47.6%
 1313079296/4119920640 (31.9%) @2.3x, remaining 8:24 RBU 100.0% UBU  85.7%
 1313079296/4119920640 (31.9%) @0.0x, remaining 8:30 RBU 100.0% UBU 100.0%
 1313079296/4119920640 (31.9%) @0.0x, remaining 8:37 RBU 100.0% UBU 100.0%
 1345814528/4119920640 (32.7%) @7.1x, remaining 8:27 RBU 100.0% UBU  85.7%
 1393426432/4119920640 (33.8%) @10.3x, remaining 8:07 RBU 100.0% UBU  81.0%
 1441464320/4119920640 (35.0%) @10.4x, remaining 7:48 RBU 100.0% UBU  76.2%
 1489993728/4119920640 (36.2%) @10.5x, remaining 7:31 RBU 100.0% UBU  85.7%
 1539112960/4119920640 (37.4%) @10.6x, remaining 7:14 RBU 100.0% UBU  66.7%
 1588592640/4119920640 (38.6%) @10.7x, remaining 6:57 RBU 100.0% UBU  66.7%
 1638596608/4119920640 (39.8%) @10.8x, remaining 6:42 RBU 100.0% UBU  76.2%
 1689321472/4119920640 (41.0%) @10.9x, remaining 6:27 RBU 100.0% UBU  85.7%
 1740275712/4119920640 (42.2%) @11.0x, remaining 6:11 RBU 100.0% UBU  61.9%
 1780809728/4119920640 (43.2%) @8.8x, remaining 6:02 RBU 100.0% UBU  76.2%
 1780809728/4119920640 (43.2%) @0.0x, remaining 6:06 RBU 100.0% UBU 100.0%
 1785266176/4119920640 (43.3%) @1.0x, remaining 6:08 RBU 100.0% UBU  85.7%
 1837105152/4119920640 (44.6%) @11.2x, remaining 5:55 RBU 100.1% UBU  81.0%
 1872723968/4119920640 (45.5%) @7.7x, remaining 5:46 RBU 100.0% UBU  71.4%
 1872723968/4119920640 (45.5%) @0.0x, remaining 5:50 RBU 100.0% UBU 100.0%
 1872723968/4119920640 (45.5%) @0.0x, remaining 5:55 RBU 100.0% UBU 100.0%
 1872723968/4119920640 (45.5%) @0.0x, remaining 5:58 RBU 100.0% UBU 100.0%
 1872723968/4119920640 (45.5%) @0.0x, remaining 6:03 RBU 100.0% UBU 100.0%
 1872723968/4119920640 (45.5%) @0.0x, remaining 6:07 RBU 100.0% UBU 100.0%
 1872723968/4119920640 (45.5%) @0.0x, remaining 6:10 RBU 100.0% UBU 100.0%
 1872723968/4119920640 (45.5%) @0.0x, remaining 6:15 RBU 100.0% UBU 100.0%
 1917747200/4119920640 (46.5%) @9.7x, remaining 6:02 RBU 100.0% UBU  76.2%
 1970864128/4119920640 (47.8%) @11.5x, remaining 5:47 RBU 100.0% UBU  85.7%
 1971617792/4119920640 (47.9%) @0.2x, remaining 5:51 RBU 100.0% UBU  57.1%
 1971617792/4119920640 (47.9%) @0.0x, remaining 5:55 RBU 100.0% UBU 100.0%
 1971617792/4119920640 (47.9%) @0.0x, remaining 5:58 RBU 100.0% UBU 100.0%
 1971617792/4119920640 (47.9%) @0.0x, remaining 6:02 RBU 100.0% UBU 100.0%
 1971617792/4119920640 (47.9%) @0.0x, remaining 6:06 RBU 100.0% UBU 100.0%
 1971617792/4119920640 (47.9%) @0.0x, remaining 6:09 RBU 100.0% UBU 100.0%
 1971617792/4119920640 (47.9%) @0.0x, remaining 6:13 RBU 100.0% UBU 100.0%
 1971617792/4119920640 (47.9%) @0.0x, remaining 6:17 RBU 100.0% UBU 100.0%
 1973288960/4119920640 (47.9%) @0.4x, remaining 6:19 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @2.8x, remaining 6:19 RBU 100.0% UBU  85.7%
 1986166784/4119920640 (48.2%) @0.0x, remaining 6:22 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 6:25 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 6:29 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 6:33 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 6:36 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 6:40 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 6:43 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 6:47 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 6:51 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 6:54 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 6:57 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 7:02 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 7:05 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 7:08 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 7:12 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 7:16 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 7:19 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 7:23 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 7:26 RBU 100.0% UBU 100.0%
 1986166784/4119920640 (48.2%) @0.0x, remaining 7:30 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=ecc50h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
:-[ FLUSH CACHE failed with SK=2h/MEDIUM NOT PRESENT]: No medium found
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=2h/MEDIUM NOT PRESENT]: No medium found

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2011680 -dvd-compat -speed=12 -use-the-force-luke=bufsize:32m 


Any idea what it could be?

Thanks

---

### Post by Cha0tik on 2009-03-06
Bump

---

