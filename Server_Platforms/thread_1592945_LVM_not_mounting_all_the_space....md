---
title: "LVM not mounting all the space..."
date: 2010-10-11
forum: Server Platforms
---

### Post by s_raghu20 on 2010-10-11
Hi,

I am very very new to LVM, though Ubuntu is not that new to me. (I am currently running ubtunu-10.04 server kernel, with ubuntu-desktop installed on top).

I created a group and a volume on friday, added 300G space there. All looked good and started emptying other partitions to this volume in order to add them to this group/volume as well.

Now, over the weekend, the movement of data is done and I am ready to get two more partitions (around 200 Gigs) to this volume.

I am using system-config-lvm for managing the lvm here.  I used the interface for adding the two partitions to the group and to the volume.

After adding the two partitions to the volume group, it shows the capacity as 500 GB. And since I have allocated all the space to the single volume, the volume also shows the 500GB.

However, when I mount the volume, the available space is only 300 GBs (the exact size which was there before I added these two partitions). 

Further, since I havent added any data after adding these two partitions, I thought that I would take them down and perhaps add them again, may be i made some mistake. But that doesnt work either. The system says that the data is too much to allow removing the physical partition from the volume.

1. did I miss some step ? did i do something wrong ?
2. how can i get my old state back (without these two partitions) ? I dont want to lose my data ... :( pls

---

### Post by s_raghu20 on 2010-10-13
bumping... anybody.. help please...

---

### Post by sanicki on 2010-11-11
bump...same situation. using system-config-lvm tool i combined two 500gb physical drives into a 1tb logical volume. however nautilus shows only 500gb.

not sure if any of this is related but at boot i also briefly see "error: no such disk" and when i do 'sudo fdisk -l' for the main drive I see:
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       60802   488135681    5  Extended
/dev/sda5              32       60802   488135680   8e  Linux LVM

---

### Post by dapperdanny77 on 2010-11-11
did you grow your filesystem ? I'm not sure if this lvm tool is doing this implicitly.

if you have ext3 or ext4 you can grow your filesystem with resize2fs command

```

>resize2fs /dev/<volumegroup>/<logicalvolume>

```

without options resize2fs is using the whole logical volume.

---

### Post by dapperdanny77 on 2010-11-11
if you add another physical volume you will see another volume in linux - sda, sdb, sdc ....

maybe your disk is not recognized or not configured properly - is  this disks connected to a raid controller?

---

### Post by psusi on 2010-11-11
Yes, you need to run resize2fs to grow the filesystem after the logical volume.  Also, if you are creating a single logical volume using all of the space in the volume group, then I'm not sure you get the point of using LVM.  You should keep your logical volume limited to the size you think you will need.  That way you can grow it later if you need to, or create more logical volumes if you decide you need them, for instance, to install another distribution.  You also need some free space if you want to use snapshots.

---

### Post by sanicki on 2010-11-11
> **dapperdanny77 said:**
> did you grow your filesystem ? I'm not sure if this lvm tool is doing this implicitly.

if you have ext3 or ext4 you can grow your filesystem with resize2fs command

```

>resize2fs /dev/<volumegroup>/<logicalvolume>

```

without options resize2fs is using the whole logical volume.

This worked perfectly. Thank you. I wonder why that isn't mentioned in the [documentation]("http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-system-config-lvm.html") for the GUI tool?

---

