---
title: "Excruciatingly slow RAID rebuild (MDADM)"
date: 2010-11-06
forum: Server Platforms
---

### Post by Chaosratt on 2010-11-06
Long is short:
I "upgraded" my 6 disk raid6 array by swapping each drive one at a time with a larger one and rebuilding the array. Each rebuild went at about 25-30mb per second and took about 3 hours which wasn't fantastic, but I could live it it.
I finally took the last magic step and "grew" the raid to the full size after the last drive and its rebuilding again, but this time at only 500kb/s. This causes a rebuild time of 7,000 hours.

Anyone familiar with MDADM rebuilds give me pointers on how to speed this up? I have the minimum rebuild speed set to 1000k/s and the maximum at 200000k/s but the rebuild still proceeds at exactly 550k/s (with very little deviation, 530-560). The enclosure I use (port multiplier enabled) has LEDs for each device and the activity LEDs are intermittent, blinking in waves. During the original rebuilds these would get pegged solid on.

I *really* dont want to have to wait 7000 hours again before this raid is usable (cant really expand the partition yet). Please Help.

---

### Post by ian dobson on 2010-11-07
Hi,

Try 

sudo echo 100000 > /proc/sys/dev/raid/speed_limit_min
sudo echo 400000 > /proc/sys/dev/raid/speed_limit_max

That'll increase the maximum rebuild rate to about 40Mb sec. And increase the min. If anything is using the array (writing to the fs) mdadm slows down the rebuild to the minimum value. Forcing the min to a higher value will speed up the rebuild but slowdown the fs.


Regards
Ian Dobson

---

### Post by Chaosratt on 2010-11-07
$ sudo echo 100000 > /proc/sys/dev/raid/speed_limit_min
-bash: /proc/sys/dev/raid/speed_limit_min: Permission denied
$ cat /proc/sys/dev/raid/speed_limit_min
1000


Correction, its now at 6000 **minuets** not hours, which is a *much* shorter time. I mounted the array under rebuild and tried to read something, seems to work if I can just deal with a 200kb/s transfer rates (usually get 80+mb/s).
I *suspect* that my last drive may have been bad. It was DOA and I RMA'd it and unlike my last WD RMA's I did NOT get a refurb back. I didn't check serial numbers. Its also one of those new "4k" drives while my other drives are not. I'll have to check if my partitioning could be causing this.
Is it alright to fail a drive during rebuild for a RAID6 array?

---

### Post by Chaosratt on 2010-11-20
No idea what the original problem was, but dmesg showed some issues with a drive (soft resets), so I waited for the raid to rebuild (several days) then failed that drive out and plastered it with "dd if=/dev/urandom" several times and then finally /dev/zero once. No more demesg errors, and no smart issues (allocated sectors, etc). Rebuilding now at 25mb/s with no issues yet.
Chaulk it up to random fluke?

---

### Post by ian dobson on 2010-11-21
Hi,

soft resets are usually caused by a dodgy cable/connection from my experiance.

Regards
Ian Dobson

---

### Post by Coder68 on 2010-12-17
Can you set the min and max to higher speeds?  My software RAID5 reads at 130MB/sec and writes at 95MB/sec.  Could I put the min at 40 and the max at 95?

Is this command something you give while it is rebuilding or does it set these speeds permanently? 

Thanks,

Coder68

---

### Post by rubylaser on 2010-12-17
How about turning the internal bitmap on for the rebuild?  Bitmaps optimize rebuild time after a crash, or after removing and re-adding a device. Turn it on by typing the following command:
```
mdadm --grow --bitmap=internal /dev/md0
```

Once array rebuild or fully synced, disable bitmaps:
```
mdadm --grow --bitmap=none /dev/md0
```

Also, you give the min/max commands when it's rebuilding, it will reset to defaults after a reboot.

---

### Post by Coder68 on 2011-02-21
I  have increased the min and max, which sped up the rebuild a little, but  not that much. I have a quad core with 8 gigs of RAM so that is not the issue.  I did notice that my CPU usage will float around 20-25% for a while and then drop to 0% for a short bit and then go back up. (See attached images.)

When I try the bitmap trick, I get an error:
[PHP]
sudo mdadm --grow --bitmap=internal /dev/md1
mdadm: failed to set internal bitmap.[/PHP]I googled this but did not find anything that made sense to me.

Here is my mdstat:

[PHP]cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda1[0] sdc1[1]
      149903296 blocks [2/2] [UU]
      
md1 : active raid5 sde[4] sdf[2] sdg[3] sdd[1] sdb[0]
      5860543488 blocks super 0.91 level 5, 4k chunk, algorithm 2 [5/5] [UUUUU]
      [===========>.........]  reshape = 56.2% (1099626508/1953514496) finish=561.7min speed=25335K/sec
      
unused devices: <none>[/PHP]Any ideas why I can't run the bitmap command?

Thanks, 

C68

---

### Post by rubylaser on 2011-02-21
Can you paste in the output of
```
mdadm -D /dev/md0
```

---

### Post by Coder68 on 2011-02-21
It is my md1 that I am having issues with. Here is what you ask for.

[PHP]/dev/md1:
        Version : 00.91
  Creation Time : Sat Feb 19 22:07:42 2011
     Raid Level : raid5
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon Feb 21 13:50:42 2011
          State : clean, recovering
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 4K

 Reshape Status : 71% complete
  Delta Devices : 1, (4->5)

           UUID : e509485d:97ef7ead:d14ee5ec:eb91e22c (local to host us104)
         Events : 0.13548

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       48        1      active sync   /dev/sdd
       2       8       80        2      active sync   /dev/sdf
       3       8       96        3      active sync   /dev/sdg
       4       8       64        4      active sync   /dev/sde
[/PHP]Thanks,

C68

Additional:
It suddenly sped up... not sure why.

[PHP]md1 : active raid5 sde[4] sdf[2] sdg[3] sdd[1] sdb[0]
      5860543488 blocks super 0.91 level 5, 4k chunk, algorithm 2 [5/5] [UUUUU]
      [=================>...]  reshape = 87.2% (1704715672/1953514496) finish=51.8min speed=79979K/sec
      
unused devices: <none>[/PHP]

I did not do anything.  I did notice that md1_reshape is now using a lot more CPU then before.

---

### Post by rubylaser on 2011-02-21
It looks like you're expanding from a 4 -> 5 disk RAID5.  You would have wanted to set the bitmap before you started the growing.  Future versions of mdadm will support adding this at any time. 
[http://neil.brown.name/blog/20110216044002#9]("http://neil.brown.name/blog/20110216044002#9")

---

### Post by Coder68 on 2011-02-21
So why would I ever turn off bitmaping then? (As Rubylaser suggested.)

Thanks,

C68

---

### Post by rubylaser on 2011-02-21
Good question :)  Here's your answer from the mdadm wiki
> Bitmaps optimise rebuild time after a crash, or after removing and re-adding a device. They do not improve normal read/write performance, and may well cause a **small degradation in performance.**

Can you run with it all the time? Yes. But, if you enable it before you make changes, it be in place when you do your mdadm management.

---

### Post by Coder68 on 2011-02-21
Opps missed that.

Thanks!

C68

---

### Post by tylersontag on 2011-08-30
I'm having the same issue, except mine is coming after having to trash a raid configuration and start over.  Formated/zeroed everything and tried building from scratch.

Well heres what i'm looking at

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdf1[3] sdg1[1] sdh1[0]
      3907022848 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [UU_]
      [>....................]  recovery =  0.0% (655744/1953511424) finish=142129.2min speed=228K/sec
      bitmap: 0/466 pages [0KB], 2048KB chunk

```

Yup... 100 days to sync.  I tried forcing an internal mapping but it already had one, as i saw when i checked my system logs:

```
Aug 29 22:09:18 tagcenter kernel: [346540.166066]  sdh:
Aug 29 22:09:18 tagcenter kernel: [346540.892522]  sdg:
Aug 29 22:09:19 tagcenter kernel: [346541.458825]  sdf:
Aug 29 22:09:27 tagcenter kernel: [346549.232274] md: bind<sdh1>
Aug 29 22:09:27 tagcenter kernel: [346549.277348] md: bind<sdg1>
Aug 29 22:09:29 tagcenter kernel: [346551.224472] md: bind<sdf1>
Aug 29 22:09:29 tagcenter kernel: [346551.448922] raid5: device sdg1 operational as raid disk 1
Aug 29 22:09:29 tagcenter kernel: [346551.448925] raid5: device sdh1 operational as raid disk 0
Aug 29 22:09:29 tagcenter kernel: [346551.449274] raid5: allocated 3179kB for md0
Aug 29 22:09:29 tagcenter kernel: [346551.452226] 1: w=1 pa=0 pr=3 m=1 a=2 r=3 op1=0 op2=0
Aug 29 22:09:29 tagcenter kernel: [346551.452230] 0: w=2 pa=0 pr=3 m=1 a=2 r=3 op1=0 op2=0
Aug 29 22:09:29 tagcenter kernel: [346551.452235] RAID5 conf printout:
Aug 29 22:09:29 tagcenter kernel: [346551.452237]  --- rd:3 wd:2
Aug 29 22:09:29 tagcenter kernel: [346551.452239]  disk 0, o:1, dev:sdh1
Aug 29 22:09:29 tagcenter kernel: [346551.452241]  disk 1, o:1, dev:sdg1
Aug 29 22:09:29 tagcenter kernel: [346551.564199] md0: bitmap initialized from disk: read 30/30 pages, set 953863 bits
Aug 29 22:09:29 tagcenter kernel: [346551.564202] created bitmap (466 pages) for device md0
Aug 29 22:09:29 tagcenter kernel: [346551.660640] md0: detected capacity change from 0 to 4000791396352
Aug 29 22:09:29 tagcenter kernel: [346551.660872] RAID5 conf printout:
Aug 29 22:09:29 tagcenter kernel: [346551.660875]  --- rd:3 wd:2
Aug 29 22:09:29 tagcenter kernel: [346551.660876]  disk 0, o:1, dev:sdh1
Aug 29 22:09:29 tagcenter kernel: [346551.660878]  disk 1, o:1, dev:sdg1
Aug 29 22:09:29 tagcenter kernel: [346551.660880]  disk 2, o:1, dev:sdf1
Aug 29 22:09:29 tagcenter kernel: [346551.661202] md: recovery of RAID array md0
Aug 29 22:09:29 tagcenter kernel: [346551.661204] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Aug 29 22:09:29 tagcenter kernel: [346551.661206] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
Aug 29 22:09:29 tagcenter kernel: [346551.661210] md: using 128k window, over a total of 1953511424 blocks.
Aug 29 22:09:34 tagcenter kernel: [346551.662742]  md0: unknown partition table

```

I tried changing /proc/sys/dev/raid/speed_limit_min  to 50k but since it was running below the initial 1k threshold in the first place, it predictably had no affect.

Ive been working at this a while and i'm running out of ideas... i even tried physically rearranging the drives :-)

Any suggestions?

---

### Post by tylersontag on 2011-08-30
also forgot to mention, i ran extended SMART disk tests and benchmark tests on all 3 disks.  All three passed the SMART data tests and benchmarked all at around 80 MBs read and 45 MBs write times...  so i don't think i have one bad apple spoiling the bunch, so to speak...

---

### Post by rubylaser on 2011-08-30
I guess 100 days, might be a bit excessive ;)  This [script]("http://ubuntuforums.org/showthread.php?t=1494846") should improve your sync speeds, but I've never seen a sync speed that slow.  Have you confirmed via SMART that none of your disks have UDMA errors (bad SATA cables)?

Give that script a run if you don't mind and report back. It won't put your data at risk, so it's safe to run.

---

### Post by byb3 on 2011-08-30
Just to add I had a similar experience and in my case it was down to a faulty SATA cable.

Everything worked fast for a short amount of time, and then suddenly it would shoot down to speeds of 200kb/s.  It didn't make any sense, and a cable replacement fixed it.

YMMV.

---

### Post by tylersontag on 2011-08-30
i don't know what part of that magic script you linked to did it, but it fixed it, i'm back to syncing at a more respectable 23 Mb/s...  heres the output if you think you can make better sense of what the problem was then I... i originally think i didn't have the script running properly since i got some errors...

```
XXXX@YYYYY:~/Programs$ sudo ./RAIDFIXER.sh 
read ahead size per device: 6144 blocks (3072kb)
read ahead size of array: 18432 blocks (9216kb)
/dev/sd[]: No such file or directory
stripe cache size of devices: 768 pages (3072kb)
./RAIDFIXER.sh: line 83: echo: write error: Resource temporarily unavailable
setting max sectors kb to match chunk size
setting NCQ queue depth to 1
```

---

### Post by rubylaser on 2011-08-30
It sets the read ahead & stripe cache of your array, and turns off Native Command Queueing.  To get better results, you'll have more luck changing to the root user, then running the script.
```
sudo -i
``` enter your password, then re-run.

---

