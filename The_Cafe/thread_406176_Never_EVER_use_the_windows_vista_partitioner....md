---
title: "Never EVER use the windows vista partitioner..."
date: 2007-04-10
forum: The Cafe
---

### Post by kragen on 2007-04-10
I cant believe it, windows has managed to destroy my fast, reliable, perfectly arranged Linux installation, and loose ALL of my data.... twice!

I used the vista partitioner to create partitions, and it decided to delete my linux ones while it was at it - it recognised them as partitions in the partitioner, but just decided to ignore them anyway.

The best bit is that my linux setup was using Linux software raid - I had the last 200 GB of both my partitions formatted identically as raid-0, and windows had only formatted one of my drives, so I managed to re-create the partitions and recover my lost data! :D, however I stupidly used the vista partitioner to create a second ntfs drive on the second disk, and it did the same thing all over again.

This time, recovery is a little harder, I know exactly where the partition was, and have created a new one in its place, but although mdadm assembles it nicely, it wont mount - this is what dmesg produces:

```
[  312.481904] md: md0 stopped.
[  312.554782] md: bind<sdb6>
[  312.555032] md: bind<sda6>
[  312.581569] md: raid0 personality registered for level 0
[  312.583594] md0: setting max_sectors to 128, segment boundary to 32767
[  312.584082] raid0: looking at sda6
[  312.584086] raid0:   comparing sda6(168266112) with sda6(168266112)
[  312.584089] raid0:   END
[  312.584091] raid0:   ==> UNIQUE
[  312.584092] raid0: 1 zones
[  312.584094] raid0: looking at sdb6
[  312.584097] raid0:   comparing sdb6(168266112) with sda6(168266112)
[  312.584100] raid0:   EQUAL
[  312.584102] raid0: FINAL 1 zones
[  312.584562] raid0: done.
[  312.584565] raid0 : md_size is 336532224 blocks.
[  312.584567] raid0 : conf->hash_spacing is 336532224 blocks.
[  312.584569] raid0 : nb_zone is 1.
[  312.584571] raid0 : Allocating 8 bytes for hash.
[  335.811402] EXT3-fs error (device md0): ext3_check_descriptors: Block bitmap for group 0 not in group (block 4194304)!
[  335.811927] EXT3-fs: group descriptors corrupted!

```

gah, so frustrated right now - vista is a steaming pile of manure anyway, so its not even like I gained anything from installing it :/

Any help is welcome, but it looks very much like I've lost all of my data this time... serves me right for not taking backups :(

---

