---
title: "Ubuntu Server 8.10 Add New Harddrive - Existing RAID implications?"
date: 2010-02-12
forum: Server Platforms
---

### Post by asimons999 on 2010-02-12
Hi.

I setup a Ubuntu 8.10 Server at work. It has two 640 Gig hard drives in raid (the type copies the same data onto both drive). 

I probably followed [https://help.ubuntu.com/8.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/8.10/serverguide/C/advanced-installation.html). But basically tried to use default / basic settings. I know it's working because a cable came loose somehow and I didn't find out until a restart. 

What does this imply for adding new separate hard drives for file storage? Where will guides differ for adding new hard drives? Does this 3rd drive have to be raid now, or safer to because it would complete configuration?

---

### Post by linorics on 2010-02-12
Are you wanting to add the new drive to your current raid?

Copy's some data to both? Do the to drives make a bigger drive or do the drives put together make a raid disk the same size as a single drive?

---

### Post by asimons999 on 2010-02-12
> **linorics said:**
> Are you wanting to add the new drive to your current raid?? well no in the sense, we are running out of room, not looking to add more fail safe. So want to add a new drive to make more room. 

> **linorics said:**
> Copy's some data to both? Do the to drives make a bigger drive or do the drives put together make a raid disk the same size as a single drive?

Two drives with the size of just one of them. The 'duplicate', don't interrupt me if a drive fails one.

---

### Post by linorics on 2010-02-12
Well you have some choices. 

1.) Just plug the drive in to your server. Then you'll have your raid drive and another drive. eg. md0 & sdc

2.) Raid5 is better for starting out small and expanding. Raid five takes 3 or more disks and has the space of 2. So if we have disk1 disk2 and disk3 each at 100gb, the total size of your raid would be 200gb. If you have five drives like this the raid size would be 400gb. So n-1 is the space. If one drive fails the others will work. If two fail your data is gone(importance of incremental backups). You also will gain some speed compared to your current raid.

Also raid6 is like this only you have two backup drives, so n-2. So four is the min. So you can loose two drives w/o data loss.

Does this help at all?

---

### Post by asimons999 on 2010-02-12
So take a guide like [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

-Does the existing RAID change the process? 
-Any guides on creating a new raid on two separate drives?

---

### Post by asimons999 on 2010-02-14
We'll probably order the hard drives this week. So any help is much appreciated.

---

### Post by asimons999 on 2010-02-21
Keen to know if there are any specific implications 'how to' wise, when installing the new hard drives.

-Is the process exactly the same? (if I were to just add a non raided drive?)
- Any guides for adding a seperate new raid?

---

### Post by asimons999 on 2010-02-22
I may just get a RAID card to not complicate things with adding a new array. 

But if someone could explain or link to a source for adding a new array and mounting it to /mnt/newdrive. 

If I just need to create two indentical partitions before hand, I can get to that point. But need to know how to create a new raid array without affecting the existing one.

---

### Post by asimons999 on 2010-02-26
This was pretty helpful.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Configuring_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Configuring_Software_RAID)
I'm up to the step of updating the mdadm config (which I believe is in /etc/mdadm/mdadm.conf not /etc/mdadm.conf like in tutorial). 

There are settings and stuff that I would be worried about echo-ing the command output 'into' or 'over' the existing config file. 

Here is the out put of the command they suggest, **but placed carefully into the existing config file:**

 
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=60cc6cee:6ea043c9:6c2486b3:19c9858a
   devices=/dev/sda1,/dev/sdb1
ARRAY /dev/md1 level=raid1 num-devices=2 metadata=00.90 UUID=aad62074:36f0ea46:585caa93:66c2189c
   devices=/dev/sda2,/dev/sdb2
ARRAY /dev/md2 level=raid1 num-devices=2 metadata=00.90 UUID=8ade5f82:decdd914:c8b7a962:43265f6b
   devices=/dev/sdc1,/dev/sdd1
# This file was auto-generated on Tue, 24 Feb 2009 15:53:47 +0000
# by mkconf $Id$"]
```

**Here is the out put of /usr/share/mdadm/mkconf**

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=60cc6cee:6ea043c9:6c2486b3:19c9858a
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=aad62074:36f0ea46:585caa93:66c2189c
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=8ade5f82:decdd914:c8b7a962:43265f6b
```


**And here is my current file (see how it's different then the guide suggested command's ouput?)**

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=60cc6cee:6ea043c9:6c2486b3:19c9858a
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=aad62074:36f0ea46:585caa93:66c2189c

# This file was auto-generated on Tue, 24 Feb 2009 15:53:47 +0000
# by mkconf $Id$
```


What do you suggest I use? Are those UUID's of the raids or the source hard drives? Because I have concerns (a drive cable came loose one day and wouldn't boot, which would change the drive letters. **Would ubuntu try to sync /dev/sda with the current /dev/sdc if /dev/sdb came out?**

---

