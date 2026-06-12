---
title: "mdadm raid 6 not starting anymore after adding two new drives"
date: 2014-01-10
forum: Server Platforms
---

### Post by neoid2 on 2014-01-10
Hi,

I've had a raid6 (ext4) running for quite some time with no problems. Yesterday I wanted to expand it with two new drives, but this didn't seems to go quite well. I've now removed them again from the array, but now I'm getting stranges errors like this:

My mdadm -D /dev/md0 says that the array is not active and the size is suddently unknown:
> root@moto:/home/neoid# mdadm --detail /dev/md0/dev/md0:
        Version : 1.2
  Creation Time : Tue Dec 10 00:40:14 2013
     Raid Level : raid6
  **Used Dev Size : unknown**
   Raid Devices : 8
  Total Devices : 8
    Persistence : Superblock is persistent


    Update Time : Fri Jan 10 12:44:01 2014
          **State : clean, Not Started**
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : moto:0  (local to host moto)
           UUID : 8ea273b0:58c9ae80:0301897c:52cb2f94
         Events : 26038


    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       81        1      active sync   /dev/sdf1
       2       8       97        2      active sync   /dev/sdg1
       3       8      113        3      active sync   /dev/sdh1
       4       8      129        4      active sync   /dev/sdi1
       8       8      145        5      active sync   /dev/sdj1
       6       8      161        6      active sync   /dev/sdk1
       7       8      177        7      active sync   /dev/sdl1


mdadm --examine --scan gived me:
> 
root@moto:/home/neoid# mdadm --examine --scan
ARRAY /dev/md/0 metadata=1.2 UUID=8ea273b0:58c9ae80:0301897c:52cb2f94 name=moto:0
   spares=2




I can still mount it and it seems to be working, but the matter of fact that mdadm says it's not started and the size is unknown scares me...
Any ideas?

---

### Post by Kirk Schnable on 2014-01-11
I've been using mdadm for awhile on a server at home and have not encountered anything like this, but I did a bit of digging and found two similar threads here on the forums:
[http://ubuntuforums.org/showthread.php?t=2131134](http://ubuntuforums.org/showthread.php?t=2131134)
[http://ubuntuforums.org/showthread.php?t=1887913](http://ubuntuforums.org/showthread.php?t=1887913)

In these threads, they poke around in the SMART data for the drives for a bit, and in the end he seems to conclude that mounting the RAID volume fixed his issues...  His original issue was a power outage I think, but your situation could have caused similar symptoms on the array I suppose, since you were adding and removing drives from your array, expanding the array, etc when you encountered a problem.

On a side note, can you provide us with the output of **cat /proc/mdstat** as well?

Thanks

---

### Post by neoid2 on 2014-01-11
I am pretty sure that something wrong happened to my ext4 partition table when I tried to grow it after adding the two hard drives...

I mentioned that I was able to get to my files, but that is not correct. Even though I manage to mount the array and see my directories, for some reason I only can get access to the top level directories. Trying to browse them does not show any files.

cat /proc/mdstat
> 
root@ubuntu:/home/ubuntu# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid6 sdf1[0] sdm1[7] sdl1[9] sdk1[8] sdj1[4] sdi1[3] sdh1[2] sdg1[1]
      0 blocks super 1.2 level 6, 512k chunk, algorithm 2 [8/8] [UUUUUUUU]
unused devices: <none>


---

### Post by Kirk Schnable on 2014-01-11
From your mdstat output, the array looks active.  Curious that the mdadm command you showed earlier says it's inactive.

If your filesystem is damaged, you may need to run an fsck to repair it.

```
sudo umount /dev/md0
sudo fsck /dev/md0
```

But, use your best judgement.  Running an fsck could cause more harm than good, or it could fix the filesystem problems entirely...

---

