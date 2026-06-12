---
title: "LVM pvmove gone bad"
date: 2013-10-09
forum: Server Platforms
---

### Post by NypefzL on 2013-10-09
Recently needed to refresh the drives of 2 of 8 RAID6 arrays that are managed by LVM.  I attached two temporary arrays, migrated the extents (via pvmove /dev/src /dev/dest), refreshed and recreated the original arrays, and attempted to move the data back (via pvmove /dev/dest /dev/src).  When moving over the final extents from the temporary drive to the last refreshed array, the pvmove operation failed.  Fortunately, there was only a single logical volume associated with this physical volume, and I have a backup somewhere else.  Unfortunately since the pvmove failure, LVM has been in limbo and I am unable to do much with the volume group since I can't manipulate the volume group while physical volumes are missing.  I'd like to abort the move now stuck in-progress, remove the problematic physical volume, and migrate to a new physical volume.

I attempted to abort the current pvmove operation, but ended up going around in circles.  It would be helpful if someone could offer any insight into my current path of troubleshooting and perhaps direct me in the right direction.

```

$ sudo pvmove --abort
  Cannot change VG data1 while PVs are missing.
  Consider vgreduce --removemissing
$ vgreduce --removemissing data1
  WARNING: Partial LV newdata needs to be repaired or removed.
  WARNING: Partial LV pvmove2 needs to be repaired or removed.
  There are still partial LVs in VG data1
  To remove them unconditionally use: vgreduce --removemissing --force.
  Proceeding to remove empty missing PVs.
$ vgreduce --removemissing data1 --force
  Removing partial LV newdata
  Can't remove locked LV newdata
$ lvs -a -o +devices
  LV                   VG    Attr     LSize    Pool Origin Data%  Move       Log Copy%  Convert Devices
  ...
  newdata              data1 -wI-----   21.48t                                                  pvmove2(0)
  newdata              data1 -wI-----   21.48t                                                  /dev/md132(3576822)
  newdata              data1 -wI-----   21.48t                                                  /dev/md134(0)
  [pvmove2]            data1 p-C---m-   13.64t                    /dev/md132                    /dev/md132(0),/dev/md131(0)
$ pvs -a -v -d /dev/md-source
    Using physical volume(s) on command line
    There are 1 physical volumes missing.
    There are 1 physical volumes missing.
  PV          VG      Fmt  Attr
  /dev/md131  data1   lvm2 a-m
$ pvs -a -v -d /dev/md131
    Using physical volume(s) on command line
    There are 1 physical volumes missing.
    There are 1 physical volumes missing.
  PV          VG      Fmt  Attr
  /dev/md132  data1   lvm2 a--

```

Alternatively, I've also looked at replacing the metadata on the problematic physical volume via: [http://www.centos.org/docs/5/html/Cluster_Logical_Volume_Manager/mdatarecover.html](http://www.centos.org/docs/5/html/Cluster_Logical_Volume_Manager/mdatarecover.html), and have seen others migrate their data to a new volume group in order to resolve this.  I'm a little hesitant on replacing metadata out of fear of losing data, and migrating will take a significant amount of time, but currently appears to be my best option.

Suggestions/Help is greatly appreciated!

---

### Post by NypefzL on 2013-10-18
A quick update -

After stopping the RAID array in question (mdadm --stop /dev/md131), I was able to remove perform the vgreduce --removemissing command, which destroyed the logical volume associated with it (newdata) but didn't impact the rest of the data on the other physical volumes.  Since then, I was able to add a new physical volume to the volume group to that I'm using to recreate newdata from an external backup.  So, ultimately, I'm in pretty good standing.

There is a possibility that replacing the metadata may have initially resolved the issue, but I was unable to confirm.  However, through my troubleshooting I encountered errors such as "inconsistent pre-commit metadata copies for volume group" and when I was able to perform the vgreduce, it complained about a missing mirror.  Since I didn't use LVM mirroring on any of my volumes, I assume it was related to the defunct pvmove.

While not an overall pleasant experience, it could have been a lot worse.  It appears that having a "bad" physical volume available prevents operations on the volume group, including removal of the physical volume.  If the problematic physical volume is removed (or dismantled) then lvm is able to succeed in maintenance operations, such as removing the physical volume.

I hope someone else finds this useful.

---

