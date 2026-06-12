---
title: "Logical Volume Manager Mirror Woes"
date: 2007-02-05
forum: Server Platforms
---

### Post by grendelkhan on 2007-02-05
Got LVM up and running, had two 250gb drives that my plan was to carve up into 3 logical volumes and have them mirrored between the two hard drives.

I create the vg, add the two hard drives to it, make my logical volumes on one of the hard drives and when I try to do the lvextend to add the mirrors on the other file system and it yells at me that I need to be increasing the size of the lv.

So, I add in a size increase with the command and then I get this errror:

```
root@agatha:~# lvextend -L +1G -m 1 /dev/vg01/lvol1 /dev/hdg
  Cannot vary number of mirrors in LV yet.
  lvextend: Add space to a logical volume
```

Anyone have any ideas?  I can't find anything about mirroring in the lvm howto, but it's there in the context help:

```
lvextend
        [-A|--autobackup y|n]
        [--alloc AllocationPolicy]
        [-d|--debug]
        [-h|--help]
        [-i|--stripes Stripes [-I|--stripesize StripeSize]]
        {-l|--extents [+]LogicalExtentsNumber |
         -L|--size [+]LogicalVolumeSize[kKmMgGtT]}
        [-m|--mirrors Mirrors]
        [-n|--nofsck]
        [-r|--resizefs]
        [-t|--test]
        [--type VolumeType]
        [-v|--verbose]
        [--version]
        LogicalVolume[Path] [ PhysicalVolumePath... ]

```

I'm stuck here.

---

### Post by jaton on 2008-06-16
Did you find a solution for this?

I'm trying to do the same with no luck. I have been working with HPUX for many years and there it is one of the most useful online SAN migration features.

---

