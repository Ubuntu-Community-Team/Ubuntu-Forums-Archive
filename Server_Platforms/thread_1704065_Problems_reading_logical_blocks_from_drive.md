---
title: "Problems reading logical blocks from drive"
date: 2011-03-10
forum: Server Platforms
---

### Post by lotharz0r on 2011-03-10
Hi.
I've got a problem with one of my hard drives.
I've got a 4disk raid5 array /dev/md0, which is missing one disk and is degraded.
I've got a new one I want to add, I do this and the device starts rebuilding.

I watch /proc/mdstat and when it comes to about 99% it fails, and dmesg reveals that there are some unreadable blocks on /dev/sdd which is one of the disks in /dev/md0.
> root@terra:~# dmesg | grep "Buffer I/O error on device sdd"
[486113.481177] Buffer I/O error on device sdd, logical block 485848714
[486113.481184] Buffer I/O error on device sdd, logical block 485848715
[486113.481187] Buffer I/O error on device sdd, logical block 485848716
[486113.481191] Buffer I/O error on device sdd, logical block 485848717
[486113.481194] Buffer I/O error on device sdd, logical block 485848718
[486113.481198] Buffer I/O error on device sdd, logical block 485848719
[486113.481201] Buffer I/O error on device sdd, logical block 485848720
[486113.481205] Buffer I/O error on device sdd, logical block 485848721
[486113.481208] Buffer I/O error on device sdd, logical block 485848722
[486113.481211] Buffer I/O error on device sdd, logical block 485848723
[486301.481024] Buffer I/O error on device sdd, logical block 485848746
[486301.481029] Buffer I/O error on device sdd, logical block 485848747
[486301.481032] Buffer I/O error on device sdd, logical block 485848748
[486301.481036] Buffer I/O error on device sdd, logical block 485848749
[486301.481039] Buffer I/O error on device sdd, logical block 485848750
[486301.481043] Buffer I/O error on device sdd, logical block 485848751
[486301.481046] Buffer I/O error on device sdd, logical block 485848752
[486301.481049] Buffer I/O error on device sdd, logical block 485848753
[486301.481053] Buffer I/O error on device sdd, logical block 485848754
[486301.481056] Buffer I/O error on device sdd, logical block 485848755
[486590.760743] Buffer I/O error on device sdd, logical block 485848778
[486590.760748] Buffer I/O error on device sdd, logical block 485848779
[486590.760752] Buffer I/O error on device sdd, logical block 485848780
[486590.760755] Buffer I/O error on device sdd, logical block 485848781
[486590.760759] Buffer I/O error on device sdd, logical block 485848782
[486590.760762] Buffer I/O error on device sdd, logical block 485848783
[486590.760765] Buffer I/O error on device sdd, logical block 485848784
[486590.760768] Buffer I/O error on device sdd, logical block 485848785
[486590.760772] Buffer I/O error on device sdd, logical block 485848786
[486590.760775] Buffer I/O error on device sdd, logical block 485848787
[486875.489103] Buffer I/O error on device sdd, logical block 485848810
[486875.489108] Buffer I/O error on device sdd, logical block 485848811
[486875.489111] Buffer I/O error on device sdd, logical block 485848812
[486875.489114] Buffer I/O error on device sdd, logical block 485848813
[486875.489118] Buffer I/O error on device sdd, logical block 485848814
[486875.489121] Buffer I/O error on device sdd, logical block 485848815
[486875.489124] Buffer I/O error on device sdd, logical block 485848816
[486875.489128] Buffer I/O error on device sdd, logical block 485848817
[486875.489131] Buffer I/O error on device sdd, logical block 485848818
[486875.489134] Buffer I/O error on device sdd, logical block 485848819
[487166.760714] Buffer I/O error on device sdd, logical block 485848844
[487166.760718] Buffer I/O error on device sdd, logical block 485848845
[487166.760722] Buffer I/O error on device sdd, logical block 485848846
[487166.760725] Buffer I/O error on device sdd, logical block 485848847
[487166.760729] Buffer I/O error on device sdd, logical block 485848848
[487166.760732] Buffer I/O error on device sdd, logical block 485848849
[487166.760735] Buffer I/O error on device sdd, logical block 485848850
[487166.760739] Buffer I/O error on device sdd, logical block 485848851
[487166.760742] Buffer I/O error on device sdd, logical block 485848852
[487166.760746] Buffer I/O error on device sdd, logical block 485848853


When this happens /dev/sdd is marked as a failed drive, and my 4 disk raid5 array only consists of 2 clean disks.
I can get it back up and running if I stop /dev/md0 and use this command:
> mdadm --create /dev/md0 --assume-clean --level=5 --verbose --raid-devices=4 /dev/sda1 missing /dev/sdc1 /dev/sdd1

I tried using dd_rescue to copy the entire /dev/sdd drive onto my new drive of same size, and it managed to copy it.
I still got errors in the dmesg log, but after several retries it managed to get through and the final output of dd_rescue was:

> dd_rescue: (info): /dev/sdd (1953514584.0k): EOF
Summary for /dev/sdd -> /dev/sdb:
dd_rescue: (info): ipos:1953514584.0k, opos:1953514584.0k, xferd:1953514584.0k
                   errs:      0, errxfer:         0.0k, succxfer:1953514584.0k
             +curr.rate:    66667kB/s, avg.rate:    43417kB/s, avg.load:  1.5%



Now comes the weird part.
I checked dmesg, and found the first and last block which had read errors.
I then used smartctl -select FIRSTLBA,LASTLBA. I expected to get errors from this test, as it tests only the area which I've had problems with before, but the test completed without error:

> # 1  Selective offline   Completed without error



Now I'm wondering what my next steps would be.
I have tried adding a new disk to my /dev/md0 array two times now, and it fails on the same spot.

dd_rescue did work, and smartctl reports no errors on the LBAs which mdadm could not read when adding a new disk to the array.



Now I'd just like some advice on what to do next.
Would it work to stop the LV and VG, stop > /dev/md0 and use mdadm --create --assume-clean /dev/sda missing /dev/sdc /dev/sdbto create the array again and replace /dev/sdd (*the disk with read errors*) with /dev/sdb (*the disk I copied sdd onto with dd_rescue*)?

What can I do to find out if /dev/sdd really has read errors on those LBAs? I'm wondering if this drive is qualified for RMA?

---

### Post by lotharz0r on 2011-03-10
I have also run a reiserfsck now, it reports everything is OK.
> Replaying journal: Done.
Reiserfs journal '/dev/raid5/safe' in blocks [18..8211]: 127 transactions replayed
Checking internal tree.. finished
Comparing bitmaps..finished
Checking Semantic tree:
finished
No corruptions found
There are on the filesystem:
        Leaves 1526015
        Internal nodes 10134
        Directories 73074
        Other files 875426
        Data block pointers 1377038635 (577257 of them are zero)
        Safe links 0
###########
reiserfsck finished at Thu Mar 10 13:59:59 2011
###########


After this test was done, I found no I/O error messages in dmesg from the period which the test ran.

---

