---
title: "[64 bit] Changing Hard Drive"
date: 2011-08-08
forum: Server Platforms
---

### Post by Beto on 2011-08-08
Hi everyone,

I have a notebook which I use as my personal server. Its hard drive capacity is reaching its limit so I want to change the hard disk (the notebook has only one bay) but I don't want to install ubuntu server from zero.

These are the current partitions.
```
[FONT="Courier New"]Mounted as            Type                                  Location                        Used  In use?  Saved?    
/(Root filesystem)    New Linux Native Filesystem (ext4)    LVM VG mapper, LV VG0-root   44% Yes Yes 
/home                 New Linux Native Filesystem (ext4)    LVM VG mapper, LV VG0-home   11% Yes Yes 
/var                  New Linux Native Filesystem (ext4)    LVM VG mapper, LV VG0-var    94% Yes Yes 
Virtual Memory Virtual Memory (swap)                        LVM VG mapper, LV VG0-swap                          No Yes[/FONT]
```

As you can see, the 'var' partition is almost full.
I want to copy this exact same partitions and contents to a new hard disk and then expand the 'var' partition to use the extra space.

First of all, is this feasible? if it is, Can you give me a small explanation of what to do? 

Best Regards,
--
Beto

---

### Post by ruffEdgz on 2011-08-08
You will have to backup your current system to then setup your new harddrive with your backup. I would read this tutorial on how to backup:

[http://ubuntuforums.org/showthread.php?t=81311&highlight=backup](http://ubuntuforums.org/showthread.php?t=81311&highlight=backup)

*The nice thing about the tutorial above is it talks about backing up and how to restore which can help if you can restore what you have backed up into a new hard drive before deleting your current hard drive.

I have also found that some of these methods given by TechRepublic are also good to look into as well:

[http://www.techrepublic.com/blog/10things/10-outstanding-linux-backup-utilities/895](http://www.techrepublic.com/blog/10things/10-outstanding-linux-backup-utilities/895)

---

