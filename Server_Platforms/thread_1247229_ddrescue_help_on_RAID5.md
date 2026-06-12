---
title: "ddrescue help on RAID5"
date: 2009-08-22
forum: Server Platforms
---

### Post by adlabens on 2009-08-22
I've got a 4 drive RAID5 array.  One of the drives quit working quite some time ago.  Another drive (/dev/sdc)just started developing read errors so that now the array will not mount.

I've got a new drive (same model# as the ones in the RAID5 - 250 gb) and want to copy the data from /dev/sdc to the new drive.  I've got ddrescue ready to execute.  Running Ubuntu Server 8.10 with the OS on /dev/sdd - a dedicated 80 gb hdd.

[list][*]Can I disconnect the other drives in the RAID5 so that the only one connected is /dev/sdc (the source for the copy)?
[*]Can I simply connect the new drive to one of the newly emptied slots and run ddrescue?  
[*]Or, do I have to issue some kind of commands to do a low-level format and designate the drive something unused (such as /dev/sdf)?  
[*]What is the process for installing the virgin hdd and copying the data to it?[/list]

Thanks,
David

---

