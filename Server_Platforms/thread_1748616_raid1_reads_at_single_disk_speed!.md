---
title: "raid1 reads at single disk speed!"
date: 2011-05-03
forum: Server Platforms
---

### Post by saibaggins on 2011-05-03
im on 10.10(desktop) and mdadm was v2.8.1 from 2008, very out of date so i tried 3.2.1 -> no change.

mdadm raid1 read speeds are the same as single disk. note i used the tests in the disk utility benchmarking tool at first --these showed raid 5 atleast to be much better but when i tried dd reads raid5 dropped off with larger data to almost the same (slow) speed as raid1. 

compare:

this is an mdadm raid0 created with :
mdadm -C --level=raid0 --raid-devices=4 /dev/sda1 /dev/sdc1 /dev/sdd1 /dev/sde1


dd if=/dev/md0 of=/dev/null bs=1M count=1000
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 1.96314 s, 534 MB/s

then i change it to a 4 disk raid1 

mdadm --stop /dev/md0
mdadm: stopped /dev/md0
root@Shankara:/home/zoizoi# mdadm --zero-superblock /dev/sda1root@Shankara:/home/zoizoi# mdadm --zero-superblock /dev/sdc1root@Shankara:/home/zoizoi# mdadm --zero-superblock /dev/sdd1
root@Shankara:/home/zoizoi# mdadm --zero-superblock /dev/sde1
root@Shankara:/home/zoizoi# mdadm -C /dev/md0 --level=raid1 --raid-devices=4 /dev/sda1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
root@Shankara:/home/zoizoi# dd if=/dev/md0 of=/dev/null bs=1M count=10001000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 7.24557 s, 145 MB/s


is it just me, can anyone else verify? 
using two partitions will be enough to show raid1 performs at single disk speed. 

I dont really want to use a 4 disk raid0 just to get the read speed i should be able to get with raid1 as i dont really care about the size loss. I would of course use raid10 but i have found this suffers from the same problem (achieve same read speed as 2 disk stripe). 

So whilst im shocked others aren't reporting this, unless there is some obscure reason why my system would give these results i think raid1 in not behaving as it should. please tell me im wrong...

---

### Post by YesWeCan on 2011-05-03
You are wrong. :P

What did you expect? RAID1 is a mirroring configuration.
You may be thinking it should read multiple cylinders concurrently across all disks and buffer the data thus potentially giving faster read speeds. I dont think mdadm works that way. I thinkit just chooses one disk of the mirrored set and reads it. This actually has some reliability advantages but no speed advantages. You need to do striping to speed it up. And to do striping with decent reliability you will want RAID10 or possibly RAID6.

---

### Post by a2j on 2011-05-04
imho, the only way to get higher read speed with mirroring is RAID10, even with 2 drives.

---

### Post by dtfinch on 2011-05-04
Reading many files in parallel is pretty fast on raid 1. It's just with single-threaded benchmarks and write benchmarks where there's no visible improvement.

[Relevant benchmark](http://www.freebsdwiki.net/index.php/RAID,_performance_tests#High_Performance_RAID). Though it's a FreeBSD related page, the Linux/MD raid 1 won the parallel read benchmarks by a long shot. Granted, it used 5 disks, but so did the raid 4 & 5.

---

### Post by saibaggins on 2011-05-04
ok, so ive looked into this a bit and am satisfied that raid1 (atleast in mdadm) isnt supposed to be as fast as raid0 for read. The main problem being that the seek time to skip data being read from other drives in the array is significant. 

I still think for larger files it should be possible to utilise multiple disk to get significantly improved read speeds, but clear this isn't implemented in mdadm (an im no expert so maybe there are argument why these wouldnt work). 

so im left with a dilema for the natty system im about to assemble. 

put my system on a 4 (new) disk raid0 can flies at 540MB/s 
or go for a raid10 at 220MB/s (but with little penalty for 2 threads reading)?

4disk raid0 maybe suicide, but i could backup my system regularly (rsync?) an hopefully have very little down time when the first disk pops... 

i think ill go for raid10, though i did observe some strange behaviour (maybe due to lucids out of date mdadm). I might do a test and unplug a drive and see how well raid10 copes.

---

### Post by saibaggins on 2011-05-04
my answer may be raid 4, 400MB/s though no multiple threads read advantage.

---

### Post by saibaggins on 2011-05-04
some useful things ive found out:

If your disk is more heavily used for read than write you should use the f2 (far) layout. just add --layout=f2 to the mdadm create command. 
For me this gets me 400MB/s instead of 220MB/s 

also originally i was getting very slow reads with raid5. changing my disk readahead parameter brought it up to 400MB/s. 

use 

blockdev --getra /dev/md0

to find the readahead

mine was 768. 
i multiplied by 8 as advised at set with 

blockdev --setra 6144 /dev/md0

and reads went from 160 -> 400 MB/s with raid5. how cool is that?

---

