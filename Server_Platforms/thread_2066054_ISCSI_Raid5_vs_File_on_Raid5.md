---
title: "ISCSI Raid5 vs File on Raid5"
date: 2012-10-03
forum: Server Platforms
---

### Post by drakesword on 2012-10-03
So I ran into an interesting situation. I setup a raid 5 with 6+1 drives. ~9.5tb total. each drive is 2TB. File system is on a seperate 500gb drive over sata 1 as well as the hot-swap. the rest are on sata 3.

So when the server was setup the raid was set to /dev/md127

I setup an iscsi target with md127 as the target in fileio mode.

DD to the disk in 10G blocks averaged 175 MB/s
DD from the disk averaged 3 GB/s

iowait 1%

Both had block size set to the cache of the drive (64M)

ISCSI write to the raid was 20 MB/s
ISCSI read from the raid was 25 MB/s

iowait 79%

I was floored at the degraded speed and the iowait. In another test I stopped the iscsi service, mounted the partition on the raid (formatted with a gpt part table fyi) and created a cifs share. 

CIFS Write 120 MB/s
CIFS Read 200 MB/s

iowait 1%

Problem is in the final implementation we cannot use cifs. So we ruled out network transfer speed.

On an identical device we created a bock file on the raid partition. 20 GB. Setup ISCSI to point to that.

ISCSI Write to block 300 MB/s
ISCSI Read from block 400 MB/s
iowait 1%

At this point I figure I am reading and writing to cache (32G available)

So is there any particular potential cause I should look into as to why the bad IO speeds and high IO wait on the raid?

---

