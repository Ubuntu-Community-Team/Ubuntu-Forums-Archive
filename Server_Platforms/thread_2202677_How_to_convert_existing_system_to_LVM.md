---
title: "How to convert existing system to LVM"
date: 2014-01-30
forum: Server Platforms
---

### Post by AmbiguousOutlier on 2014-01-30
I have 5 disks in my current server which are just mounted separately in fstab. 

ubuntu server install is on sda, ext4

And then I have four xfs drives that are used as NFS and samba storage on my network; 

sdb mounted on /mnt/afs
sdc mounted on /mnt/bfs
sdd mounted on /mnt/cfs
sde mounted on /mnt/dfs

A single partition on each, I have enough space to copy all data onto 3 drives giving me a completely spare drive if necessary. 
 
What I would like to do is convert sdb - sde to LVM and bring them all into one logical drive. Primarily to make file sharing easier. 

So I'm thinking I need to run the following, to bring each drive under LVM control, -Zn will preserve all my existing data;

```
pvcreate --metadatacopies 0 -Zn /dev/sdb1
pvcreate --metadatacopies 0 -Zn /dev/sdc1
pvcreate --metadatacopies 0 -Zn /dev/sdd1
pvcreate --metadatacopies 0 -Zn /dev/sde1
```


Create a new volume group using the newly created pvs

```
vgcreate vg0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1/
```

Create the logical volume;

```
lvcreate -Zn vg0 /dev/sdb1
```

I would then mount sdb1 in fstab

Do I need to change my physical extents?

I would also prefer not to strip my data, is it necessary for me to force this option?

To add a new drive in the future;
```
vgextend vg0 /dec/sdf
```

Have I understood google correctly? This is something I don't want to use trial and error on.
Thanks

---

### Post by TheFu on 2014-01-30
Don't know how, but you might want to read up on what happens if 1 drive in the LVM set fails. What happens to the data on all the other drives? Can it still be accessed? [https://serverfault.com/questions/241659/do-you-lose-everything-when-you-have-a-hard-disk-failure-in-a-multi-hard-disk-lv](https://serverfault.com/questions/241659/do-you-lose-everything-when-you-have-a-hard-disk-failure-in-a-multi-hard-disk-lv)

As another option - you migh t or might not like - perhaps just merging the existing storage into a single "view" would meet your requirements?  People with lots of media use these all the time.
* aufs
* UnionFS
* mhddfs
Anyway, thought you might like these options to consider. Sorry, don't have a good answer to the real question - which is still an option.

---

