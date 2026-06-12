---
title: "Level 0 Raid??"
date: 2018-11-14
forum: Server Platforms
---

### Post by bambamm on 2018-11-14
Does the command "level0" in the following command line means it will create a RAID0? 
```
mdadm –create –verbose /dev/md0 –level0 –raid-devices=2 /dev/sda1 /dev/sdb1
```
If so can I change the level0 to level1 for Raid level 1?

---

### Post by slickymaster on 2018-11-14
Thread moved to **Server Platforms** for a better fit

---

### Post by TheFu on 2018-11-14
The mdadm manpage has this:
```
       -l, --level=
              Set  RAID  level.  When used with --create, options are: linear,
              raid0, 0, stripe, raid1, 1, mirror, raid4, 4, raid5,  5,  raid6,
              6, raid10, 10, multipath, mp, faulty, container.  Obviously some
              of these are synonymous.

              When a CONTAINER metadata type is requested, only the  container
              level is permitted, and it does not need to be explicitly given.

              When  used  with  --build, only linear, stripe, raid0, 0, raid1,
              multipath, mp, and faulty are valid.

              Can be used with --grow to change the RAID level in some  cases.
              See LEVEL CHANGES below.
```

---

### Post by bambamm on 2018-11-14
Thank you.

---

