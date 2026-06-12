---
title: "first ubuntu server build - question about raid rebuild"
date: 2014-03-01
forum: Server Platforms
---

### Post by jason63 on 2014-03-01
Hey guys, this is my first server build and first use of ubuntu. 

Currently testing the system, with 8 sata disks (of varying size and sata1/2 speeds).

Server spec;

Asus H87 MB
Intel i5-4570 
16gb Ram
Corsair hx750 psu

1x 36gb Raptor (OS on motherboard sata controller)

4x 200gb sata (on motherboard sata controller)

2x 320gb sata (on pci-e sata card)
2x 160gb sata (on same pci-e sata card)


I've created an mdadm 8 disk array in raid6, with 2 parity drives. Yes I know, this spans the array over the integrated sata controller and the pci controller. Im just testing right now. 

I tested a 2 drive "failure" by pulling one sata port off the mb, and one off the controller card. The system said 2 drives failed, and when I plugged them in and added the partitions, it started rebuilding the array.


```
watch /proc/mdstat

Every 2.0s: cat /proc/mdstat                                                        Sat Mar  1 12:25:37 2014


Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid6 sdg1[9](S) sdd1[8] sdf1[4] sdh1[6] sdi1[7] sdb1[1] sda1[0] sdc1[2]
      936940800 blocks super 1.2 level 6, 128k chunk, algorithm 2 [8/6] [UUU_U_UU]
      [======>..............]  recovery = 33.5% (52379420/156156800) finish=78.9min speed=21913K/sec


unused devices: <none>
```

I'm wondering if the speed (22MB/s) is decent considering its spanned over multiple different disks and different controllers?

I've done;

```
echo 60000 > /proc/sys/dev/raid/speed_limit_min
echo 2500000 > /proc/sys/dev/raid/speed_limit_max
```

as well as

```
echo 32768 > /sys/block/md0/md/stripe_cache_size
```


I'm only playing with these drives as they were sitting around and I can learn raid and ubuntu with them. I have 5x4tb WD reds coming in which will run off the onbaord controller.

---

### Post by CharlesA on 2014-03-01
Looks about right to me, but I've only had to do a "rebuild" with mdadm once and that was during the initial sync for my RAID 5.

---

### Post by jason63 on 2014-03-01
I can surely assume with 5 identical high end sata 6 drives on the same controller, Id get much better speed than this franken-raid I've concocted?

---

### Post by CharlesA on 2014-03-01
> **jason63 said:**
> I can surely assume with 5 identical high end sata 6 drives on the same controller, Id get much better speed than this franken-raid I've concocted?

Probably but rebuilding from parity always takes time. When I had to rebuild 2 drives from my RAID 6, it took about 48 hours or so. 3TB drives, 5 x 3TB drives in the array.

---

### Post by jason63 on 2014-03-01
> **CharlesA said:**
> Probably but rebuilding from parity always takes time. When I had to rebuild 2 drives from my RAID 6, it took about 48 hours or so. 3TB drives, 5 x 3TB drives in the array.

48 HOURS!!! oh man. 


so 1 x 3tb drive failed  and before you could replace it another one failed in your 5 disk array (effectively putting it into a critical but active state). And putting 2 new drives in and doing a rebuild took that long? Were the drives full or it doesn't matter?

I'm glad Im not using this server for storage, only backup.

---

### Post by CharlesA on 2014-03-01
Nah, I had a problem with the drive cage I was using and it caused 2 drives to drop out of the array. I got it fixed, but they still needed to rebuild. I guess it didn't matter that the drives were not new because they got initialized and rebuilt anyway. When you have a lot of data, and a large array, the rebuilding takes a long time.

I'm just glad I went to RAID6, otherwise I would have lost all of my data from the array (but I had backups).

---

### Post by sandyd on 2014-03-01
> **jason63 said:**
> I can surely assume with 5 identical high end sata 6 drives on the same controller, Id get much better speed than this franken-raid I've concocted?

Note that charlesA's rebuild time takes into effect that he is using pure HW raid (A LSI RAID controller if I remember correctly) and not software raid (mdadm) or fakeraid (dmraid)

---

### Post by jason63 on 2014-03-01
Yeah I hear you. This array is the backup of everything digital I own, the originals are still on their respective systems. Eventually a 2nd server/array will be added as a file server.
 
The guy that turned me on to Ubuntu/mdadm/software raid, manages millions of dollars of servers than run vm servers. I tend to trust what he tells me, and this is the direction hes pointing.

> **sandyd said:**
> Note that charlesA's rebuild time takes into effect that he is using pure HW raid (A LSI RAID controller if I remember correctly) and not software raid (mdadm) or fakeraid (dmraid)


HWraids take longer to rebuild ?

---

### Post by CharlesA on 2014-03-02
> **sandyd said:**
> Note that charlesA's rebuild time takes into effect that he is using pure HW raid (A LSI RAID controller if I remember correctly) and not software raid (mdadm) or fakeraid (dmraid)

Yeah, running an LSI 9260-8i.

> **jason63 said:**
> HWraids take longer to rebuild ?

Depends. It needed to rebuild 2 drives and I didn't have it set up fully at the time, so the rebuild times are probably not optimal.

Guess I'll find out how they look when one of the drives goes out. :lolflag:

---

