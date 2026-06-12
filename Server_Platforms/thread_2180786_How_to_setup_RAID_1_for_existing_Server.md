---
title: "How to setup RAID 1 for existing Server"
date: 2013-10-14
forum: Server Platforms
---

### Post by lingpanda on 2013-10-14
I currently have a non raid mail server that I would like to move to Raid1. I plan to purchase new hardware for this server to function. My question is how do I migrate this existing server over to the new box? Not sure how to clone the drive and move it to the new hardware with out errors.  

    I currently use this software for my Windows Images [http://www.drive-image.com/](http://www.drive-image.com/) but am uncertain if this damage my linux file system in any way. I open to any and all suggestions. Thanks.

---

### Post by CharlesA on 2013-10-14
Depends on how you want to do the RAID. Are you planning on using hardware (RAID card) or software (mdadm or something else) RAID?

---

### Post by lingpanda on 2013-10-14
> **CharlesA said:**
> Depends on how you want to do the RAID. Are you planning on using hardware (RAID card) or software (mdadm or something else) RAID?

I plan to use mdadm as I've had recent success with it.

---

### Post by CharlesA on 2013-10-15
This might help:
[https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID](https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID)

**Note: It is a bit old, but it should give you an idea of what needs to be done.**

I've never done a migration like this before as I have always ran the OS drive off a single disk and had the RAID array for data.

As far as cloning goes, I use clonezilla most of the time and have found it works wonderfully.

---

### Post by SeijiSensei on 2013-10-15
If you are planning on buying a new pair of drives, I'd take the same route Charles describes.  Put the two drives into the machine and build at least two arrays after partitioning the disks.  Depending on the size, I'd create one partition of, say, 40-100 GB on each drive and bind them together as RAID1.  (I'll call that array /dev/md0 below.)  I'd mount that array as /var.  You might also want to create a partition that will become swap, again using RAID1.  This isn't for data integrity but to benefit from the higher read speeds that RAID1 offers.  The swap partition should be in the range of 2-8 GB.  Use "top" on your current machine to see how much swap is in use.

Now create a partition that encompasses the remainder of each drive and create another array.  You'll be mounting that as /home (/dev/md1 below).

All together this provides additional data integrity to the two parts of the OS that get the most activity, /var and /home.  

To migrate the data in this method, first create two temporary mount points, say /mnt/home and /mnt/var.  Boot Ubuntu, choose "recovery mode," and follow these steps:

```

# mount -o remount,rw /
# mkdir /mnt/home /mnt/var
# mount /dev/md0 /mnt/var
# mount /dev/md1 /mnt/home
# cd /
# rsync -av home/* /mnt/home
# rsync -av var/* /mnt/var

```

Run the rsync commands with "-avn" first to make sure it will be writing the files to the proper locations.  If so, remove the "n" switch and run rsync again.

Now add entries to /etc/fstab to mount /dev/md0 as /var and /dev/md1 as /home.  Reboot.

---

### Post by lingpanda on 2013-10-15
Thanks for all the feedback so far. It looks like our budget isn't going to allow all new hardware like I had planned. I'm going to make do with what I have but using two new drives. Will clonezilla allow me to make an image that I can apply to the new drives? I going to have to clone the existing HD and remove. Install two new drives and setup Raid. Then somehow put the image on the new Raid. Sounds possible?

---

### Post by CharlesA on 2013-10-16
You would need another drive as a go-between to get the data on the array.

---

### Post by lingpanda on 2013-10-16
> **CharlesA said:**
> You would need another drive as a go-between to get the data on the array.

On the same physical machine or will a network share work?

---

### Post by CharlesA on 2013-10-16
I think you'd need it on the same machine, but I'm not sure. You basically just need to copy the data off the old drive and onto the RAID array like Seiji suggested. A network share would probably work, but disk-to-disk would be easier to deal with.

---

