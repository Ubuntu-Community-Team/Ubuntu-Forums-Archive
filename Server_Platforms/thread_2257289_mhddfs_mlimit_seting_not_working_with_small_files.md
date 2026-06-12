---
title: "mhddfs mlimit seting not working with small files"
date: 2014-12-18
forum: Server Platforms
---

### Post by MakOwner on 2014-12-18
I had so many things in that last thread, I thought it better to start another.
This seems to be an ongoing exchange with RubyLaser anyway :P)

I have been using rsync as a non-privileged user to fill this mhddfs volume, source is coming from an NFS mount.  Up to /dev/sdg1, the files were all 4.5GB and larger ISO/MKV files.
Once it hits /dev/sg1, it started transferring other files, like audio books and music.

So, using the same rsync command and an mlimit=20G, with small files the free space at the end of the volumes starts to disappear.
Is there any fix to this?  Is this because of the way rsync behaves? anyway to force mlimit to be honored?



```

/dev/sda1	459G	11G	401G	3%	/
/dev/sdb1	1.8T	1.7T	17G	100%	/mhds1/WD_WCAVY5517644d01
/dev/sdc1	1.8T	1.7T	17G	100%	/mhds1/WD_WCAVY5517752d02
/dev/sdd1	1.8T	1.7T	19G	99%	/mhds1/WD_WCAVY5530016d03
/dev/sde1	1.8T	1.7T	18G	99%	/mhds1/WD_WCAVY5901109d04
/dev/sdf1	1.8T	1.7T	17G	100%	/mhds1/WD_WCAVY5526791d05
/dev/sdg1	1.8T	1.8T	0	100%	/mhds1/WD_WCAVY5979240d06
/dev/sdh1	1.8T	666G	1.1T	39%	/mhds1/WD_WCAVY5517521d07
/dev/sdi1	1.8T	68M	1.7T	1%	/mhds1/WD_WCAVY5517351d08
/dev/sdj1	1.8T	68M	1.7T	1%	/mhds1/WD_WCAVY5530008d09

```

---

### Post by rubylaser on 2014-12-19
mlimit should be honored if a non-root user is performing the write. Unless you get to the point where all disks in the pool have less space than the threshold, then the disk with the most free space should be written to.

---

### Post by MakOwner on 2014-12-19
So, I'm filling this mhddfs volume using rsync and starting and stopping snapraid sync every once in while to not let the sync get too far behind.

In the last few hours, when I stop the sync and run snapraid diff to see how many new files are added, I'm starting to see "restored /path/file.name" instead of "add /path/file.name".

What would cause that change?

---

### Post by rubylaser on 2014-12-20
> **MakOwner said:**
> So, I'm filling this mhddfs volume using rsync and starting and stopping snapraid sync every once in while to not let the sync get too far behind.

In the last few hours, when I stop the sync and run snapraid diff to see how many new files are added, I'm starting to see "restored /path/file.name" instead of "add /path/file.name".

What would cause that change?

I would assume that rsync re-scanning and syncing is updating a timestamp or metadata on previously synced file and that is what is causing the restored message.

---

