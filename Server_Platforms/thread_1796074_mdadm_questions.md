---
title: "mdadm questions"
date: 2011-07-03
forum: Server Platforms
---

### Post by gus_zernial on 2011-07-03
i have kubuntu Natty, with two software RAID devices, /boot
on RAID1 and / on RAID0. The system works for a while, then
it fails to boot and goes into grub rescue. I then boot with 
the Live rescue CD to check things out, and one thing I notice
is that the metadevice numbers may change - I configured them
as /dev/md2 and /dev/md3, but one or both may show up as 
/dev/md126 and/or/dev/md127 respectively.

-What can cause the metadevice numbers to change between boots, and how do I prevent this? Is it because one or more of the mdadm superblocks is wrong? 

-Is there a method to zero out the mdadm superblocks on the disks, recreate the metadevices correctly, and rewrite all mdadm superblocks, without destroying the data on the metadevices? I think I need to do this from the Live rescue CD, making sure the metadevices are stopped first, right?

-Are the mdadm superblocks on the underlying sdX devices, the mdX devices, or both?

I've found other posts describing similar problems, but no solution giving me confidence that I will preserve my data, but if someone has a link to the correct procedure I'd be most appreciative

---

### Post by rubylaser on 2011-07-03
What do you have in your /etc/mdadm/mdadm.conf file?  This being incorrect is normally the root of almost all mdadm problems.

```
cat /etc/mdadm/mdadm.conf
```
and what's the output of 
```
cat /proc/mdstat
```


The superblock info is written to each disk (or partition) depending on how you set it up.  You can always view that info by examining the disk, something like this
```
mdadm -E /dev/sdb1
```

---

