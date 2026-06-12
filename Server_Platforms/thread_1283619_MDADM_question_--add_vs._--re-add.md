---
title: "MDADM question --add vs. --re-add"
date: 2009-10-05
forum: Server Platforms
---

### Post by joeinbend on 2009-10-05
Does anyone know the difference between the --add and --re-add functions in mdadm?

My theory was, --add was just when you're adding in a new disk to your array, which makes sense, and that --re-add would allow you to pop a RAID array disk member back into the array without it kicking off the whole recovery process (which on 1TB drives, takes several hours).

The reason I ask is, for this scenario:
Let's say you have a 5 disk RAID5 array, and one of the disks drops offline. not sure why, and the disk checks out with all tests, so want to just add it back in. It seems logical to me that you should be able to just "--re-add" the disk back in, and it will just check out. Probably have to sync up a few missing parity blocks, but that's about it, not a full-fledged recovery.

Is it the case that even a single block of data written on the array that the missing disk "missed", constitutes a full recovery? Ok, I could buy that. But, to test that theory, I unmounted and remounted my RAID5 in read-only, failed a disk, removed it, then "--re-add" and it still kicks off a full recovery.

Thoughts?

---

### Post by fjgaude on 2009-10-05
All I can add to the discussion is a man page paragraph:

> INCREMENTAL MODE
       Usage: mdadm --incremental [--run] [--quiet] component-device

       Usage: mdadm --incremental --rebuild

       Usage: mdadm --incremental --run --scan

       This mode is designed to be used in conjunction with a device discovery
       system.   As devices are found in a system, they can be passed to mdadm
       --incremental to be conditionally added to an appropriate array.

       mdadm performs a number of tests to determine if the device is part  of
       an  array,  and  which  array  it should be part of.  If an appropriate
       array is found, or can be created, mdadm adds the device to  the  array
       and conditionally starts the array...

You can read all the rest. As you can see we are dealing with a very complex system. Many of us have had little experience dealing with all the issues that come up. I keep a full backup to my array and have on at times have used it to play around with my four-drive raid5 array, even test raid0 arrays for speed, etc.

Good luck in finding a solution to what you seek.

---

### Post by Xianath on 2009-10-06
The main difference is that --re-add is intended for devices that have been recently removed. For example, if you have a RAID5 and you pop a drive out, you should --add a replacement, but --re-add the same drive. The latter should not kick in a full resync provided your array has an intent bitmap.

One possible use of this feature is when one disk gives you a bad sector or unrecoverable bit error, but is otherwise readable. If you need to replace it and keep your array up in the process, you could pop the drive out, mirror it completely to another drive using dd conv=noerror, then --re-add the new drive back in. It should, in theory, save you from rebuilding the whole array because of a single bad sector, thus significantly lowering the chance of dual failure.

HTH,
Peter

---

### Post by joeinbend on 2009-10-06
I'm with you both on those theories. Unfortunately fjgaude, that one didnt work :(  That appears to be more of a troubleshooting/diagnostic function, where you are having trouble getting the RAID to assemble. 

Xianath, that was exactly my theory of --re-add as well, but it doesnt pan out that way. In that theory, I should be able to fail: (sudo mdadm /dev/md0 -f /dev/sda), remove: (sudo mdadm /dev/md0 -r /dev/sda) then re-add (sudo mdadm /dev/md0 --re-add /dev/sda) and have the "sda" drive re-join the RAID, with no recovery/rebuild needed.

I am of course doing all of this in my virtual-machine, not my "live" server! I'll try upgrading from mdadm 2.6.8 to 3.0 to see if I get different results.

EDIT: I upgraded to mdadm 3.0.2, and get the same results.

---

### Post by Xianath on 2009-10-06
Do your arrays have bitmaps? You can easily tell from mdstat:

```
ppopov@nas:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md11 : active raid6 sdd2[10] sda2[8] sdf2[5] sde2[11] sdb2[7] sdc2[9] sdk2[3] sdl2[4] sdi2[1] sdj2[2] sdg2[0] sdh2[6]
      9762616320 blocks super 1.2 level 6, 256k chunk, algorithm 2 [12/12] [UUUUUUUUUUUU]
**      bitmap: 4/466 pages [16KB], 1024KB chunk**

md10 : active raid1 sdd1[2] sdb1[5] sdf1[4] sde1[1] sda1[0] sdc1[3] sdk1[7] sdl1[6] sdj1[8] sdi1[9] sdg1[10] sdh1[11]
      497856 blocks [12/12] [UUUUUUUUUUUU]

unused devices: <none>

```

Without an intent bitmap, md has no way of knowing what parts have changed since the disk was kicked out, so it will rebuild everything. If your array doesn't have one, do 'sudo mdadm -G <array> -b internal' and try your tests again. If memory serves, the last time I did this it worked. On the off-chance that my memory fails me, I'd rather not try it on a 12TB RAID6 :)

Cheers,
Peter

---

### Post by joeinbend on 2009-10-07
Peter:
That did the trick! 

I checked my array for a bitmap with (cat /proc/mdstat) and there was no sign of said bitmap. I bitmapped my test array with that command (sudo mdadm -G /dev/md0 -b internal). Checked again with (cat /proc/mdstat) and it shows a bitmap now.

Running my test, I am able to fail, remove, then re-add array disks and have it return to a clean state without a resync/recovery process starting.

With answers comes more questions: Is there any disadvantage to having the array bitmapped, and if not, why wouldn't it be done by default when creating an array? If it is recommended to be done on all arrays in general, then I will update my documentation to include this, because this will be a life-saver for many others.

Secondly, I am noticing as I am testing here, that the disk does go back in without a resync, using either the -a or --re-add switch, however if I reboot the server with the disk missing, when I re-add it, it does start a full recovery. Why does a reboot affect the bitmap, and is there a way around this?

I find another interesting behavior of the bitmap: after failing and re-adding a disk, the bitmap data in (cat /proc/mdstat) shows "0/128 pages [0kb]" which sounds to me like something's not quite right. I tried to force it by removing the bitmap (sudo mdadm -G /dev/md0 -b none) and re-adding it (sudo mdadm -G /dev/md0 -b internal), at which point it now displays (cat /proc/mdstat) "128/128 pages [512kb]". 

I then failed and removed a disk, rebooted, re-added, with the same results: resync initiated after a reboot.

---

### Post by Xianath on 2009-10-07
Actually, the disk *does* resync even with bitmaps on, it just resyncs the parts that have been marked dirty since the drive has been kicked. As to why they are not on by default, it's for (write) performance reasons. With an internal bitmap, every write to the device would also require two writes to the bitmap -- that's a LOT of seek overhead.

I am not sure whether or not bitmaps are subject to pdflush mechanics. I don't see why they shouldn't, but who knows? Anyway, it seems that you can counter most of that overhead with proper (read: huge) write behind and stripe caches. Personally, I have dirty_ratio and dirty_background_ratio at 35, read_ahead_kb at 65536, and stripe_cache_size at 2048, and with that, my array sustains between 150 and 200MB/sec total throughput (eg. copying a file at 80MB/sec), and is very quiet. With those tunables at default levels, I get between 20 and 50MB/sec total throughput and a LOT of thrashing. YMMV but it's certainly worth a try. Needless to say, so much write-behind cache poses some risk, but the system seems stable and the UPS so far has been holding its ground (fingers crossed :) )

Cheers,
Peter

---

### Post by fjgaude on 2009-10-10
Thanks, Peter, for bringing your wisdom and knowledge to the **mdadm** software raid platform.

---

