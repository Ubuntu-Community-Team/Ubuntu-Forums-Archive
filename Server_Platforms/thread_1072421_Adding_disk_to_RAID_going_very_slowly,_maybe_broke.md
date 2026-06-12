---
title: "Adding disk to RAID going very slowly, maybe broken disk"
date: 2009-02-17
forum: Server Platforms
---

### Post by seepage87 on 2009-02-17
I added another HD to my RAID6 thus:
```

mdadm --add /dev/md0 /dev/sde1
mdadm --grow /dev/md0 --raid-devices=6

```

At first it was going at ~10000K/sec and would take about 15 hours.  This was ok, and in line with what I've noticed before.  But now it's going at a very small fraction of that speed, often less than 100K/sec:

```

Every 2.0s: cat /proc/mdstat                                                     Tue Feb 17 10:52:21 2009

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sde1[5] sda1[0] sdf1[4] sdd1[3] sdc1[2] sdb1[1]
      1465159296 blocks super 0.91 level 6, 64k chunk, algorithm 2 [6/6] [UUUUUU]
      [==========>..........]  reshape = 51.2% (250068864/488386432) finish=11584.8min speed=342K/sec

unused devices: <none>

```

My guess is there's something physically wrong with one of my disks.  I played around with the disk I added before adding it, created a partition, added a file system, ran fsck.ext3 on it, everything fine.  

But another disk the other day got "removed" at the same time another had some sort of error.  I thought the latter might have resulted from the former, that cause by a lose cable.  When I tightened the cables and restarted, the errored disk was just fine and the removed disk needed to be rebuilt.

So maybe any of the three could be broken?  Is there a good way to check each for defects while they're in the array?

Thanks in advance.

---

### Post by songshu on 2009-02-17
you could try to look at S.M.A.R.T. if the disks support it.

its not 100% guarenteed on the reporting but it might give you an indication if one is behaving badly

---

### Post by seepage87 on 2009-02-17
I'll definitely check it out, I'm pretty sure they do the whole S.M.A.R.T thing.

I'm a little worried about the reshaping process though.  It's now estimated to take as long as 50 days.  I'm not even sure I could stop it without losing all my data (probably not), though I can still read data off it while it's working.  

Logically I could probably take out one or two of the potentially defective disks and it should still have enough information to reshape the array, but who knows during the reshape. Ideally I'd send the lot of them back to the manufacturer and get them replaced :-/

I seem to be stuck in the mean time, unless anyone has a guess on how best to proceed, or a way to make the reshaping take a reasonable amount of time.

---

