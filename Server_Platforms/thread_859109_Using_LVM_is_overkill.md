---
title: "Using LVM is overkill?"
date: 2008-07-14
forum: Server Platforms
---

### Post by Shaoline on 2008-07-14
I have a rig consisting of not less than 12 hard drives, rangin from 120Gb IDE up to 750Gb SATA.

4x 74Gb SATA Raptors
1x 750 SATA
2x 250 SATA
1x 200 SATA
2x 200 IDE
1x 160 SATA
1x 120 IDE

My setup now is like this:

Ubuntu Hardy Heron 8.04.1 LTS

First raptor:```

/ (2Gb)
/boot (100Mb)
/swap (2Gb)
[INDENT]Extended:
/tmp (5Gb)
/var (5Gb)
/usr (15Gb)
/usr/local (15Gb) (why I now ended up with this I dont remember..)

All lines on separate partitions.
(Still got 26Gb of unpartitioned space left on disc)
[/INDENT]
```

Second raptor:```

/home 
```

Third raptor:```

/media/vm-images
```

Fourth raptor:```

/media/temp (junk files, partitially downloaded files etc)
```

So, wouldn't it be a wise idea to have /home on a LVM/Raid 1 setup with 2 raptors? Redundant and fast read? Maybe even pull it a bit further and add encryption while at it?
I used to have all the raptors in raid 0+1 back when I used Windows, but I didn't get the motherboard raid thing to work with Linux, so I trashed the array and split them up. But now I just have raptors basically sitting here "unused"; storage place for VM's, geez.. :(

I got the 750 SATA drive almost empty so temp-storage shouldn't be much of a problem I reckon.. even though there will be lots of disc activity for a while.

Also, would I be able to adjust the /usr/local partition using a Live CD? That way I could use those ~40 gb left on that raptor disc to store my VM's?

Bunching them all together in one giant LVM isn't really smart I guess, since one disc could fail and trash the rest..?

I would like some suggestions and comments on how to deal with this. Partition sizes etc, what you guys use and are set with..
Or just give me some hints and ideas; what would you do with these discs?

---

### Post by Robstarusa on 2008-07-14
> **Shaoline said:**
> I have a rig consisting of not less than 12 hard drives, rangin from 120Gb IDE up to 750Gb SATA.

4x 74Gb SATA Raptors
1x 750 SATA
2x 250 SATA
1x 200 SATA
2x 200 IDE
1x 160 SATA
1x 120 IDE

My setup now is like this:

Ubuntu Hardy Heron 8.04.1 LTS

First raptor:```

/ (2Gb)
/boot (100Mb)
/swap (2Gb)
[INDENT]Extended:
/tmp (5Gb)
/var (5Gb)
/usr (15Gb)
/usr/local (15Gb) (why I now ended up with this I dont remember..)

All lines on separate partitions.
(Still got 26Gb of unpartitioned space left on disc)
[/INDENT]
```

Second raptor:```

/home 
```

Third raptor:```

/media/vm-images
```

Fourth raptor:```

/media/temp (junk files, partitially downloaded files etc)
```

So, wouldn't it be a wise idea to have /home on a LVM/Raid 1 setup with 2 raptors? Redundant and fast read? Maybe even pull it a bit further and add encryption while at it?
I used to have all the raptors in raid 0+1 back when I used Windows, but I didn't get the motherboard raid thing to work with Linux, so I trashed the array and split them up. But now I just have raptors basically sitting here "unused"; storage place for VM's, geez.. :(

I got the 750 SATA drive almost empty so temp-storage shouldn't be much of a problem I reckon.. even though there will be lots of disc activity for a while.

Also, would I be able to adjust the /usr/local partition using a Live CD? That way I could use those ~40 gb left on that raptor disc to store my VM's?

Bunching them all together in one giant LVM isn't really smart I guess, since one disc could fail and trash the rest..?

I would like some suggestions and comments on how to deal with this. Partition sizes etc, what you guys use and are set with..
Or just give me some hints and ideas; what would you do with these discs?

You can add md(x) devices to lvm easily.

Why not do that?

---

### Post by Shaoline on 2008-07-14
Is that really good? Won't that trash the whole lot of my data stored in that md(x) should one disc fail?

---

### Post by Robstarusa on 2008-07-14
> **Shaoline said:**
> Is that really good? Won't that trash the whole lot of my data stored in that md(x) should one disc fail?

If you have data on your md device already, you'd have to take it off.

create pv on the md volume.  If one disk dies it should work just like any other raid.....the data should be there.

---

### Post by koenn on 2008-07-14
> **Shaoline said:**
> Is that really good? Won't that trash the whole lot of my data stored in that md(x) should one disc fail?

yes.
lvm has no redundancy and LV behaves as a single disk so if 1 physical disk fails, the whole LV goes with it. There will still be data left on the remaining (non-failed) disks, but as the filesystem spans multiple disks, it's going to be rather hard to recover that data. 
The main advantage of LVM is that you can span multiple disks so the size of directories/mountpoints is not limited to the size of a disk, and possibly add disks to a volume to increase its size so it's a bit more flexible than adding mount points (although by creatively mounting disks to subdirectories of eg your home directory, you can create extra disk space quite easily).

To my knowledge, there is no LVM Raid 1. You can create a striped set (~ Raid 0) but that's not redundant. 

Maybe you can build a software raid eg by mirroring all drives you have 2 of , and lay LVM on top of it to make it continuous. 
The rest could be used for backup copies maybe ? You could LVM those as well : if the LV fails, you only loose copies ... which is fine as long as the originals are intact.

---

### Post by Robstarusa on 2008-07-14
> **koenn said:**
> yes.
lvm has no redundancy and LV behaves as a single disk so if 1 physical disk fails, the whole LV goes with it. There will still be data left on the remaining (non-failed) disks, but as the filesystem spans multiple disks, it's going to be rather hard to recover that data. 
The main advantage of LVM is that you can span multiple disks so the size of directories/mountpoints is not limited to the size of a disk, and possibly add disks to a volume to increase its size so it's a bit more flexible than adding mount points (although by creatively mounting disks to subdirectories of eg your home directory, you can create extra disk space quite easily).

To my knowledge, there is no LVM Raid 1. You can create a striped set (~ Raid 0) but that's not redundant. 

Maybe you can build a software raid eg by mirroring all drives you have 2 of , and lay LVM on top of it to make it continuous. 
The rest could be used for backup copies maybe ? You could LVM those as well : if the LV fails, you only loose copies ... which is fine as long as the originals are intact.

Yes, I was suggesting exactly this: Create a raid1/5/6/10 and then add your MD device to the LVM.  If you add, say, a raid1 to an lvm, the raid1 "underneath" the lvm should keep the lvm good if one disk dies.

---

