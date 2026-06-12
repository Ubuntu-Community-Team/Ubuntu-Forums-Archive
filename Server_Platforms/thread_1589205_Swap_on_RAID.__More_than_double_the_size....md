---
title: "Swap on RAID.  More than double the size...?"
date: 2010-10-06
forum: Server Platforms
---

### Post by mucho_maze on 2010-10-06
Strange swap size...

I've tried this with Ubuntu Lucid 64 bit (machine 1), Ubuntu Hardy 64 bit (machine 1) and Ubuntu Lucid 32 bit (machine 2).

All raid refereed to here is RAID1.

Consider this for Ubuntu Lucid 64 bit (machine 1):

maze@machine1:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda5[0] sdc5[1]
      9764800 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdc1[1]
      975808 blocks [2/2] [UU]
      
md3 : active raid1 sda7[0] sdc7[1]
      20506560 blocks [2/2] [UU]
      
md2 : active raid1 sda6[0] sdc6[1]
      8787904 blocks [2/2] [UU] <----this is the SWAP device
      
unused devices: <none>
maze@machine1:~$ free
             total       used       free     shared    buffers     cached
Mem:       2056284     898692    1157592          0      63592     639864
-/+ buffers/cache:     195236    1861048
Swap:     18562448          0   18562448
maze@machine1:~$ 

A bit of calculation: 8787904*2 = 17575808 < 18562448.

First of all, the swap should be around 8787904. Okay I though, something went wrong so swap is not as raid. But the calculation shows, that the swap space is larger than the sum of space from both partitions?

Is swap on raid or not? How is this behaviour possible at all?

My set up on machine2 works perfect and looks perfect:

maze@machine2:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdb2[1] sda2[0]
      3906496 blocks [2/2] [UU] <------ this is the SWAP device
      
md0 : active raid1 sdb1[1] sda1[0]
      20506560 blocks [2/2] [UU]
      
unused devices: <none>
maze@machine2:~$ free
             total       used       free     shared    buffers     cached
Mem:       2060680     124908    1935772          0      16420      57088
-/+ buffers/cache:      51400    2009280
Swap:      3906488          0    3906488
maze@machine2:~$

---

### Post by mucho_maze on 2010-10-07
I finally localised the problem!!! It was because I had another drive connected to the bus. This drive contained a swap partition (it was a hard drive I just found among some stuff at my room, and accidentally it contained an old Ubuntu installation). Ubuntu auto-mounts this per-default, so even though I haven't touched this drive during installation, the swap partition was nonetheless enabled.

This also explains why I wasn't able to find anything about this swap issues on the net... it was just to specific for my setup!

---

### Post by P4man on 2010-10-07
You probably have more than one swap partition. Try this

```
sudo swapon -l
```

To see which devices are being swapped to.

edit: how can I be 2 hours late? lol.

---

