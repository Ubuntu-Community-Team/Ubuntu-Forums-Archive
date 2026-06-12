---
title: "Adding A New HDD To A Running System"
date: 2010-03-08
forum: Server Platforms
---

### Post by Blakstar26 on 2010-03-08
I am hoping someone can help with my issue. 

I currently have an Ubuntu Server setup with a CF card that has / and /boot on their own partitions. I also have a single 1TB drive that is dedicated to the /home partition, however it's a drive that I have run out of space on.

I just purchased a 1.5TB drive to throw in the server, but I am not sure how to set this drive up so that it's seamlessly integrated with the 1TB drive. I would like it setup so that my /home partition is expanded from 1Tb to 2.5TB. I know what I am explaining is similar to raid 0, of which I am not opposed to, except that everything I have searched for online solely explains a raid setup during installation, and I don't have the time (due to school) to reinstall and reconfigure my system.

So in a nutshell, is there a way to setup raid 0 without doing a re-install or is there a way to setup 'fstab' to accomadate my request?

Pointing me in the right direction would be really appreciated.

Thanks.with

---

### Post by bab1 on 2010-03-08
> **Blakstar26 said:**
> I am hoping someone can help with my issue. 

I currently have an Ubuntu Server setup with a CF card that has / and /boot on their own partitions. I also have a single 1TB drive that is dedicated to the /home partition, however it's a drive that I have run out of space on.

I just purchased a 1.5TB drive to throw in the server, but I am not sure how to set this drive up so that it's seamlessly integrated with the 1TB drive. I would like it setup so that my /home partition is expanded from 1Tb to 2.5TB. I know what I am explaining is similar to raid 0, of which I am not opposed to, except that everything I have searched for online solely explains a raid setup during installation, and I don't have the time (due to school) to reinstall and reconfigure my system.

So in a nutshell, is there a way to setup raid 0 without doing a re-install or is there a way to setup 'fstab' to accomadate my request?

Pointing me in the right direction would be really appreciated.

Thanks.with

You do not want to use RAID 0 in the situation you describe.  You will only end up with 2TB.  Why loose the 500GB?

> *A RAID 0 can be created with disks of differing sizes, but the storage space added to the array by each disk is limited to the size of the smallest disk.*

[[SIZE="2"][COLOR="Blue"]_*Wikipedia*_[/COLOR][/SIZE]]("http://en.wikipedia.org/wiki/Standard_RAID_levels")

I would look into how I could use [_**[COLOR="DarkGreen"]LVM [/COLOR]**_]("http://en.wikipedia.org/wiki/Logical_volume_management")(Logical Volume Management)

---

### Post by srs5694 on 2010-03-08
bab1 is correct; you should use LVM, not RAID. What I'd do is this:


[list=1]
[*]Create at least one partition on the new disk. (I might do more than one, to simplify future changes -- say, throw in a couple of ~200MB partitions to be used as future /boot partitions in case I wanted to experiment with a future Linux distribution.) The MBR type code for LVM is 8e, so make them that; or if you use GPT, set it with an appropriate code (details vary depending on the partitioning software). If you create multiple partitions, they can all be LVM, unless you want to use one for something else in the near future.
[*]Set up your logical volumes. You'll need to use a handful of tools, such as pvcreate, vgcreate, and lvcreate. Create one volume to hold /home, and make it at least as large as your current /home partition.
[*]Put a filesystem on your to-be-/home volume and mount it.
[*]Copy your current /home to the new to-be-/home volume.
[*]Unmount /home and to-be-/home.
[*]Edit /etc/fstab to mount the new /home logical volume at /home and (as root) type "mount -a" to be sure it works.
[*]Verify that your /home files were all copied OK. Take your time. You can use the system like this for a while, if necessary, before you wipe out the original /home partition.
[*]Using fdisk or some other partitioning tool, change the partition type code on your original /home partition.
[*]Using the LVM tools, add your original /home partition to the LVM.
[*]Using the LVM tools, expand the size of the /home logical volume. I'd leave at least a little free space in the volume group, in case you want to create a volume for some other purpose (swap space, say, or a separate /tmp directory). You can always expand /home to fill the entire volume later, should the need arise. Some filesystems don't permit easy shrinking, though.
[*]Using whatever resize utility is appropriate (resize2fs, resize_reiserfs, etc.), resize the filesystem to fill the /home logical volume.

[list]

The worst of this process will be learning about the LVM tools. I wrote a three-part piece on RAID and LVM for [Linux Magazine](http://www.linux-mag.com/id/2453) about four years ago. (Registration required to read it.) Read parts 1 and 3; part 2 covers RAID, which you don't need.

An entirely different option, or so I gather, is to switch to the new Btrfs from whatever filesystem you're currently using. Btrfs is supposed to support LVM-like features, so you should be able to format the new disk's main partition for Btrfs, move contents to it, then reformat the current/old /home partition for Btrfs and link the two together. I've not studied the details of what Btrfs supports along these lines, though. Also, Btrfs is still very new; the last I heard, it was considered experimental. Depending on the importance of your data, you might not want to risk using Btrfs.

Oh, one other point: If by chance your new drive is a Western Digital Green drive with the new "Advanced Format" technology (4KB sectors masquerading as 512-byte sectors), be sure to align your partitions on 4KB boundaries. If you don't, you'll see some *serious* performance degradation, particularly when writing small files. (I've benchmarked it and gotten write speeds that are slower by as much as 30x for some filesystems and operations when partitions are misaligned. Yes, that's right: thirty times slower.)

---

### Post by bab1 on 2010-03-08
> **srs5694 said:**
> 

An entirely different option, or so I gather, is to switch to the new Btrfs from whatever filesystem you're currently using. Btrfs is supposed to support LVM-like features, so you should be able to format the new disk's main partition for Btrfs, move contents to it, then reformat the current/old /home partition for Btrfs and link the two together. I've not studied the details of what Btrfs supports along these lines, though. Also, Btrfs is still very new; the last I heard, it was considered experimental. Depending on the importance of your data, you might not want to risk using Btrfs.

BtrFS is the way Linux is moving to large data drives.  It is experimental at this point.  It is more lke Sun's ZFS in that you create ***data pools*** that incorporate muliple drives.> 

Oh, one other point: If by chance your new drive is a Western Digital Green drive with the new "Advanced Format" technology (4KB sectors masquerading as 512-byte sectors), be sure to align your partitions on 4KB boundaries. 
I believe that the ***very latest*** WD drives are now set at 4k sectors (no 512B emulation).  You have to realign them **[COLOR="Red"]only to be used by non-aware OS's [/COLOR]**and that would be XP.  Linux, MAC OSX and MS Vista/7 are all 4k sector aware.  Read the data at WD site for clarification.  These drives are just being released (as of January 2010) and you have to be very careful that you don't have an early drive which does need alignment as **@srs5694** states.

See:
[**_[COLOR="DarkSlateGray"]Advanced Format[/COLOR]_**]("http://www.google.com/search?hl=en&q=wd+green+4k+Advanced+Format&aq=f&aqi=&aql=&oq=")

---

### Post by Blakstar26 on 2010-03-08
Well, I suppose LVM it is. I have never used the LVM method before, but I suppose now is as best a time as any.

I am not using WD drives, they are both Seagate. 

Thanks for all the help guys and I will be sure to study those links you provided.

---

### Post by bab1 on 2010-03-08
> **Blakstar26 said:**
> Well, I suppose LVM it is. I have never used the LVM method before, but I suppose now is as best a time as any.

I am not using WD drives, they are both Seagate. 

Thanks for all the help guys and I will be sure to study those links you provided.

You do realize that you can just mount the new partitions on the new drives anywhere in the original file system.  There is no absolute need for either RAID or LVM.

---

