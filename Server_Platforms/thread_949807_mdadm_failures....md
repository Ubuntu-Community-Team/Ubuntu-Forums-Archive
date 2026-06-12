---
title: "mdadm failures..."
date: 2008-10-16
forum: Server Platforms
---

### Post by bexamous on 2008-10-16
Rebuild degraded RAID1 or RAID5 no problem, rebuild degraded RAID10 fails.

Here is basic problem, one drive fails leaving RAID10 array and degraded.  Add hot spare.  Drive shows up as hot spare yet auto-rebuild does not start.  Only seems to occur with RAID10 array.  I try removing the spare drive, delete its super block, and then readd it.  Do the same thing with RAID1/RAID5 and auto-rebuild starts on its own.

Any way to even tell array to rebuild?  I've never heard of this having to be done, I don't even think its possible.

```

bexamous@nine:~/bin$ sudo mdadm /dev/md4 --remove /dev/sdb4
mdadm: hot removed /dev/sdb4
bexamous@nine:~/bin$ sudo mdadm --zero-superblock /dev/sdb4
bexamous@nine:~/bin$ sudo mdadm /dev/md4 --add /dev/sdb4
mdadm: added /dev/sdb4
bexamous@nine:~/bin$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid0 sdb2[0] sdd2[2] sdc2[1]
      733767168 blocks 512k chunks
      
md3 : active raid5 sdb3[0] sdc3[1] sdd3[6] sdh3[5] sdg3[4] sdf3[3] sde3[2]
      4300824576 blocks level 5, 512k chunk, algorithm 2 [7/7] [UUUUUUU]
      
md4 : active raid10 sdb4[7](S) sdc4[1] sdh4[6] sdg4[5] sdf4[4] sde4[3] sdd4[2]
      53781280 blocks 32K chunks 2 near-copies [7/6] [_UUUUUU]
      
unused devices: <none>
bexamous@nine:~/bin$ 

```

Here is --detail information on the RAID10 array.

```

/dev/md4:
        Version : 00.90
  Creation Time : Mon Oct 13 02:01:54 2008
     Raid Level : raid10
     Array Size : 53781280 (51.29 GiB 55.07 GB)
  Used Dev Size : 15366080 (14.65 GiB 15.73 GB)
   Raid Devices : 7
  Total Devices : 7
Preferred Minor : 4
    Persistence : Superblock is persistent

    Update Time : Thu Oct 16 11:52:39 2008
          State : clean, degraded
 Active Devices : 6
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 1

         Layout : near=2, far=1
     Chunk Size : 32K

           UUID : c16f9559:800b499b:18ceddb4:39b7cf2e (local to host nine)
         Events : 0.32

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       36        1      active sync   /dev/sdc4
       2       8       52        2      active sync   /dev/sdd4
       3       8       68        3      active sync   /dev/sde4
       4       8       84        4      active sync   /dev/sdf4
       5       8      100        5      active sync   /dev/sdg4
       6       8      116        6      active sync   /dev/sdh4

       7       8       20        -      spare   /dev/sdb4

```


Clean,degraded and it sits there with spare device?

BTW This is with up-to-date Ubuntu 8.10 with mdadm 2.6.7-3ubuntu7.

---

### Post by fjgaude on 2008-10-16
Is it not true that for raid10 you can only use an even number of drives?

---

### Post by bexamous on 2008-10-16
Nope, since 2.6.9 the new raid10 module can use odd number of devices. 
[http://cgi.cse.unsw.edu.au/~neilb/01093607424](http://cgi.cse.unsw.edu.au/~neilb/01093607424)

Plus I can create the array fine, it works perfect... but if I a drive is removed it won't rebuild itself.

BTW Most modern RAID controllers support odd number of drives with RAID10, I use both Areca and LSI and they both do... LSI calls it 1E but they just think they're special :). 

For example:  5/4 drives, all raid10 really means is two copies of all data:
```

Raid10 5 Drive:
1 2 3 4 5
a a b b c
c d d e e
f f g g h
h i i j j

Raid10 4 drives
1 2 3 4
a a b b
c c d d
e e f f
g g h h 
i i j j

```

---

### Post by fjgaude on 2008-10-17
Okay, I guess mdadm is not up to that level yet. Time for a bug report, eh?

---

### Post by bexamous on 2008-10-17
:/  Hope there was some work around or something, this isn't limted to arrays with odd number of drives, any raid10 fails like this:

```

root@nine:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md9 : active raid10 loop4[3] loop3[2] loop2[1] loop1[0]
      40832 blocks 64K chunks 2 near-copies [4/4] [UUUU]
     
unused devices: <none>
root@nine:~# mdadm /dev/md9 -f /dev/loop3
mdadm: set /dev/loop3 faulty in /dev/md9
root@nine:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md9 : active raid10 loop4[3] loop3[4](F) loop2[1] loop1[0]
      40832 blocks 64K chunks 2 near-copies [4/3] [UU_U]
root@nine:~# mdadm /dev/md9 --remove /dev/loop3
mdadm: hot removed /dev/loop3
root@nine:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md9 : active raid10 loop4[3] loop2[1] loop1[0]
      40832 blocks 64K chunks 2 near-copies [4/3] [UU_U]
root@nine:~# mdadm --zero-superblock /dev/loop3
root@nine:~# mdadm /dev/md9 --add /dev/loop3
mdadm: added /dev/loop3
root@nine:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md9 : active raid10 loop3[4](S) loop4[3] loop2[1] loop1[0]
      40832 blocks 64K chunks 2 near-copies [4/3] [UU_U]
root@nine:~# 

```

Only RAID10 fails, RAID1 for example works:
```

root@nine:~# mdadm -S /dev/md9
mdadm: stopped /dev/md9
root@nine:~# mdadm --zero-superblock /dev/loop1
root@nine:~# mdadm --zero-superblock /dev/loop2
root@nine:~# mdadm --zero-superblock /dev/loop3
root@nine:~# mdadm --zero-superblock /dev/loop4
root@nine:~# mdadm -C --level=raid1 -n 4 /dev/md9 /dev/loop1 /dev/loop2 /dev/loop3 /dev/loop4
mdadm: array /dev/md9 started.
root@nine:~# cat /proc/mdstat 
md9 : active raid1 loop4[3] loop3[2] loop2[1] loop1[0]
      20416 blocks [4/4] [UUUU]
root@nine:~# mdadm /dev/md9 -f /dev/loop3
mdadm: set /dev/loop3 faulty in /dev/md9
root@nine:~# mdadm /dev/md9 --remove /dev/loop3
mdadm: hot removed /dev/loop3
root@nine:~# mdadm /dev/md9 --zero-superblock /dev/loop3
root@nine:~# mdadm /dev/md9 --add /dev/loop3
mdadm: added /dev/loop3
root@nine:~# cat /proc/mdstat 
md9 : active raid1 loop3[2] loop4[3] loop2[1] loop1[0]
      20416 blocks [4/4] [UUUU]

```

SIGH

---

### Post by fjgaude on 2008-10-17
If memory serves raid10 is a late additon to mdadm... file a bug report...

---

