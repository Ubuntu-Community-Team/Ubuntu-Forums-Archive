---
title: "dpkg extremely slow"
date: 2011-12-04
forum: Server Platforms
---

### Post by Xianath on 2011-12-04
Recently (since natty?), dpkg has been extremely slow in extracting archives. I started an apt-get upgrade five hours ago and it is still unpacking. Here's a relevant line from iotop:

20926 be/4 root        0.00 B/s    7.84 K/s  0.00 %  0.00 % dpkg --force-unsafe-io --status-fd 59 --unpack -~/var/cache/apt/archives/id3v2_0.1.12-2_amd64.deb

Relevant mountpoints:

/dev/mapper/RAID6-System--Root on / type xfs (rw,noatime,relatime,allocsize=1048576,attr2,barrier,largeio,logbufs=8,logbsize=256k,swalloc)
/dev/mapper/RAID6-System--Var on /var type xfs (rw,noatime,relatime,allocsize=1048576,attr2,barrier,largeio,logbufs=8,logbsize=256k,swalloc)

Here's the actual storage:

ppopov@nas:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md11 : active raid6 sdj2[10] sdc2[3] sdb2[6] sdd2[0] sdf2[11] sda2[2] sde2[1] sdi2[7] sdl2[9] sdk2[8] sdg2[12] sdh2[13]
      9762616320 blocks super 1.2 level 6, 256k chunk, algorithm 2 [12/12] [UUUUUUUUUUUU]
      bitmap: 5/466 pages [20KB], 1024KB chunk

As you might imagine, I expect more than a few KB/sec from this array and indeed, in all other scenarios it churns up happily at a couple hundred MB/sec. It's just dpkg (or dpkg-deb?) that is so slow. I don't see this behavior on any other system I have, including live USB installations and virtual machines, but none of them use XFS for / and /var, and none of them use software RAID. Where should I start looking for the problem?

The system is a 64-bit natty server currently being upgraded to oneiric. It started as 8.04 and has not had this problem until sometime into natty.

Thanks,
Peter

---

