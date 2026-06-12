---
title: "Software Raid5 has fallen apart"
date: 2009-11-10
forum: Server Platforms
---

### Post by davereynoldz on 2009-11-10
Hi guys, I recently set up a software raid5 on ubuntu server using mdadm. I have three 1tb drives raided up, sdb1 sdc1 and sdd1. This is a recent upgrade to my fileserver and while I was migrating my data over from my old drives I had them plugged into the box, naturally. 

Now I finished migrating my data across and unplugged my old drives and accidentally unplugged the sata cable for one of the raid drives, then booted up without realizing. The raid obviously did not rebuild itself and I quickly found out what went wrong. I've plugged the drive back in but now the raid will not go back together.

I've tried: 

```
mdadm --atuo-detect /dev/sdb1 /dev/sdc1 /dev/sdd1 
```

but it says: 

```
could not bd_claim sdb1
```

Please help? This is highly frustrating

---

### Post by davereynoldz on 2009-11-10
Some possibly useful information:

Results of cat /proc/mdstat 

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdc1[1]
      976759936 blocks

md_d0 : inactive sdb1[0](S)
      976759936 blocks

unused devices: <none>

```

Results of dmesg tail

```
[   70.978479] md: Autodetecting RAID arrays.
[   70.978494] md: could not bd_claim sdb1.
[   70.978994] md: Scanned 3 and added 2 devices.
[   70.978997] md: autorun ...
[   70.979000] md: considering sdc1 ...
[   70.979010] md:  adding sdc1 ...
[   70.979017] md:  adding sdd1 ...
[   70.979022] md: created md0
[   70.979025] md: bind<sdd1>
[   70.979049] md: bind<sdc1>
[   70.979065] md: running: <sdc1><sdd1>
[   70.979080] md: kicking non-fresh sdd1 from array!
[   70.979088] md: unbind<sdd1>
[   70.979096] md: export_rdev(sdd1)
[   71.064985] raid5: device sdc1 operational as raid disk 1
[   71.065362] raid5: allocated 3228kB for md0
[   71.065408] raid5: not enough operational devices for md0 (2/3 failed)
[   71.065467] RAID5 conf printout:
[   71.065469]  --- rd:3 wd:1
[   71.065472]  disk 1, o:1, dev:sdc1
[   71.065681] raid5: failed to run raid set md0
[   71.065711] md: pers->run() failed ...
[   71.065734] md: do_md_run() returned -5
[   71.065736] md: md0 still in use.
[   71.065739] md: ... autorun DONE.

```

---

### Post by buntunoob on 2009-11-10
I,m not sure if this is your Problem, but in my fstab used the uuid= insted of /dev/sdb, due to moveing around the Drives Changes the /dev/sd**_X,_** and with the uuid it dosent matter what you do its being mounted with the drives id, 
probly the easy fix would be to put the old drives back in, now the fix im not sure about

---

