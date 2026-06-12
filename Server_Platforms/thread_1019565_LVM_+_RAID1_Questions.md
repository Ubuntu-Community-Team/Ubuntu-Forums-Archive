---
title: "LVM + RAID1 Questions"
date: 2008-12-23
forum: Server Platforms
---

### Post by thornomad on 2008-12-23
Hi -

I run an old ubuntu server box as an NAS in the basement (500mhz pre-2000 system).  It currently has two 320GB hard drives using [3ware] hardward RAID-1.  I have one partition for /home and another one for everything else.

I dream of upgrading to an entirely new system and, when I do, I want to move to software raid and lvm.  When I upgrade, I wanted to add two more hard drives that are greater than (or equal to) my 320s.

I think I understand the software raid component (creating the arrays), and I understand how lvm can make single larger volumes out of multiple arrays ... but is there a way to get some of the RAID-0 efficiency out of lvm if I am using mismatched sized drives ?  

For example, if I had two (2) 320s (RAID-1) and two (2) 750s (RAID-1) does LVM allow any striping of data between the two arrays to increase efficiency?  Or, would I have to go with four (4) 320s ?

Am curious for any advice you may have. 

Thanks,
Damon

---

### Post by Robstarusa on 2008-12-23
> **thornomad said:**
> Hi -

I run an old ubuntu server box as an NAS in the basement (500mhz pre-2000 system).  It currently has two 320GB hard drives using [3ware] hardward RAID-1.  I have one partition for /home and another one for everything else.

I dream of upgrading to an entirely new system and, when I do, I want to move to software raid and lvm.  When I upgrade, I wanted to add two more hard drives that are greater than (or equal to) my 320s.

I think I understand the software raid component (creating the arrays), and I understand how lvm can make single larger volumes out of multiple arrays ... but is there a way to get some of the RAID-0 efficiency out of lvm if I am using mismatched sized drives ?  

For example, if I had two (2) 320s (RAID-1) and two (2) 750s (RAID-1) does LVM allow any striping of data between the two arrays to increase efficiency?  Or, would I have to go with four (4) 320s ?

Am curious for any advice you may have. 

Thanks,
Damon

You can concatenate/stripe the volumes as follows:

0) sudo apt-get install lvm2
1) Backup your data somewhere! (We will need to copy it back to the logical volume later after we format it)
2) Umount the soft/hard raid, or disk devices that you'll use for lvm (if they are already mounted)
3) pvcreate /dev/[md0,or other device]
4) pvcreate /dev/[md1,or other device]
5) pvdisplay should show you how many "pe's" (Physical extents) there are
6) you can create a volume group
  vgcreate myvolumegroup /dev/md0 /dev/md1.  Replace /dev/md0 /dev/md1 with the device names you used for the pvcreate step.
  This will allocate the physical extents from the 2 pv's you created before, toward the volume group "myvolumegroup"
7) vgdisplay should then show you how many PE's you have.  PE's by default are 4MB each I think.
8) now you can create a volume!
  lvcreate -n 'volumename' -l [number] OR -L [number][units] -i 2 /dev/myvolumegroup

I have never used -i, but this is supposed to stripe over the pv's.  the 2 is for the number of pvdevices to stripe over.  use -l if you want to specify the physical extents.  Use -L if you want to specify the size in GB as "-L 10GB" and it will autodetermine the number of extents for how many GB you want to use. 

The above instructions will create a volume that you can use as a physical device:  /dev/myvolumegroup/volumename

Of course you don't have to use "myvolumegroup" or "myvolumename" -- name it however you want!

Now to actually put files on your volume:
mkfs -t ext3 -j /dev/myvolumegroup/volumename

mkdir /mnt/mylvm
mount /dev/myvolumegroup/volumename /mnt/mylvm

Now your logical volume is mounted at /mnt/mylvm and you can copy back the data that you backed up.

hope this helps!

Rob

---

### Post by fjgaude on 2008-12-23
What do you do if one drive fails? What happens to your data, how do you recover? <smile>

---

### Post by Robstarusa on 2008-12-23
> **fjgaude said:**
> What do you do if one drive fails? What happens to your data, how do you recover? <smile>

If one drive fails, as long as the pv's are on top of the soft raid device, they shouldn't be affected.

You rebuild the raid using mdadm "underneath" the lvm.

No problems.

---

### Post by fjgaude on 2008-12-23
Okay, the raid goes first... now to build, create the raid. <smile>

---

### Post by thornomad on 2008-12-23
> **Robstarusa said:**
> I have never used -i, but this is supposed to stripe over the pv's.  the 2 is for the number of pvdevices to stripe over.  use -l if you want to specify the physical extents.  Use -L if you want to specify the size in GB as "-L 10GB" and it will autodetermine the number of extents for how many GB you want to use. 

Hi Rob - 

Wow!  Thanks for those detailed instructions -- not only does that answer my question but shows me *exactly* how to do it.  Smile.  I really appreciate it.

I took a look at the [man page for lvcreate]("http://linux.die.net/man/8/lvcreate") as well ... I am going to try and find some more info about how the striping works when it comes to disks with different sizes ... is interesting though.

I am still learning about lvm and mdadm, so I appreciate your detailed help.  I assume I would, in the future, be able to add other drives to this volume group in order to increase the available file size?

And, would it make the most sense to have / and /boot and all that on a different physical drive (or partition, at least) than all of this other stuff? [edit]Maybe with vgextend?[/edit]

Thanks again.
Damon

---

### Post by Robstarusa on 2008-12-23
> **thornomad said:**
> Hi Rob - 

Wow!  Thanks for those detailed instructions -- not only does that answer my question but shows me *exactly* how to do it.  Smile.  I really appreciate it.

I took a look at the [man page for lvcreate]("http://linux.die.net/man/8/lvcreate") as well ... I am going to try and find some more info about how the striping works when it comes to disks with different sizes ... is interesting though.

I am still learning about lvm and mdadm, so I appreciate your detailed help.  I assume I would, in the future, be able to add other drives to this volume group in order to increase the available file size?

And, would it make the most sense to have / and /boot and all that on a different physical drive (or partition, at least) than all of this other stuff? [edit]Maybe with vgextend?[/edit]

Thanks again.
Damon

Yes, when you add disks, (I would suggest raiding them under LVM2 as well) you do a pvcreate on them.  Then you can either do a new volume group or do a "vgextend" (see the vgextend man page).  Once you have extended the volume group with more Physical extents (PE's), you can create additional volumes, or expand your existing ones.  If you have made the existing volumes ext3, you can do "lvextend" and then use "resize2fs" to expand the filesystem as well.

You do not need to unmount before using resize2fs, lvextend, vgextend, etc.

---

### Post by Robstarusa on 2008-12-23
> **fjgaude said:**
> Okay, the raid goes first... now to build, create the raid. <smile>

NOTE: (....) convention means, choose the one appropriate for your situation.


mdadm -D /dev/md(012345...) shows the status of the device

mdadm /dev/md(012345...) -f /dev/sda(bcdefg) will "fail" the device.

mdadm /dev/md(012345...) -r /dev/sda(bcdefg) will "remove" the device.

Put the new disk into your computer connected to the same cable as the failed device ( you may need to shut down unless you have hot swap bays...I assume you are not using iscsi, san volumes, multipathing,  etc, as that is beyond the scope of my advice) 

now

sfdisk -R /dev/sda(bcdefg) will tell the kernel to re-read the partition table of the new disk.

you will need to do a "sudo fdisk /dev/sd(abcdefgh)" 

then do the following:

n for new partition (I'm assuming the disk you put in doesn't have 4 
primary parititons already)

p for primary partition

1-4? 1

"t" (to change partition type)
"fd" for linux raid autodetect.

w to write changes (may need q to quit as well)

if this disk was previously part of another software raid, you should do

(The following assumes you just created partition "1" on the replacement disk.)

mdadm --zero-superblock /dev/sd(abcdefg)1 This removes the old "raid identifier" if the partition previously belonged to a different raid array

then do

mdadm /dev/md(012345...) -a /dev/sd(abcdefg...)1

I believe this should start rebuilding the array

You can check with mdadm -D /dev/md(012345...)

It should show a percent complete.

If you'd like to continuously monitor it you can try

"watch -n 30 mdadm -D /dev/md(012345...)"
This will "watch"(update the screen) with the output of "mdadm -D /dev/md(012345...)" every 30 seconds

Post here if you have issues.

---

### Post by thornomad on 2008-12-23
> **Robstarusa said:**
> Yes, when you add disks, (I would suggest raiding them under LVM2 as well) you do a pvcreate on them.  Then you can either do a new volume group or do a "vgextend" (see the vgextend man page).  Once you have extended the volume group with more Physical extents (PE's), you can create additional volumes, or expand your existing ones.  If you have made the existing volumes ext3, you can do "lvextend" and then use "resize2fs" to expand the filesystem as well.

Thanks again - so, do I need to do the partitioning of the physical disk before I do the raid ?  I got a little confused about that ... so, the first time through it would be: 

DISK[1,2] --> PARTITION[1,2] --> RAID ARRAY (MD[1]) --> VOLUMEGROUP [*vgcreate*] --> LOGICAL VOLUME --> FORMAT FILE SYSTEM --> MOUNT

Then the second set of disks I add it would just be:

DISK[3,4] --> PARTITION[3,4] --> RAID ARRAY (MD[2]) --> VOLUMEGROUP [*vgextend*] 

Am I on the right track?  As I understood you explain it, I wouldn't have to "recreate" the LVM2 part ... I am just adding to it with vgextend ... right?  Thanks again!

---

### Post by Robstarusa on 2008-12-24
> **thornomad said:**
> Thanks again - so, do I need to do the partitioning of the physical disk before I do the raid ?  I got a little confused about that ... so, the first time through it would be: 

DISK[1,2] --> PARTITION[1,2] --> RAID ARRAY (MD[1]) --> VOLUMEGROUP [*vgcreate*] --> LOGICAL VOLUME --> FORMAT FILE SYSTEM --> MOUNT

Then the second set of disks I add it would just be:

DISK[3,4] --> PARTITION[3,4] --> RAID ARRAY (MD[2]) --> VOLUMEGROUP [*vgextend*] 

Am I on the right track?  As I understood you explain it, I wouldn't have to "recreate" the LVM2 part ... I am just adding to it with vgextend ... right?  Thanks again!

For originally creating the array or recovering, it's basically:

Stick disk in
partition disk
Create/repair raid (using nomenclature: /dev/[sh]d[abcefg][1234567]

(take one option from each bracket as appropriate:
/dev/hda1 would be the first ide disk partition one
/dev/sdc3 would be the 3rd scsi/sata disk, partition 3)
)

Does that help?

Rob

---

### Post by thornomad on 2008-12-24
> **Robstarusa said:**
> Stick disk in
partition disk
Create/repair raid (using nomenclature: /dev/[sh]d[abcefg][1234567]

(take one option from each bracket as appropriate:
/dev/hda1 would be the first ide disk partition one
/dev/sdc3 would be the 3rd scsi/sata disk, partition 3)
)

Yea - that does help.  Thanks again for the details.  You've been very helpful.

---

### Post by aimeesonfl on 2011-01-11
> **thornomad said:**
> Hi -I run an old ubuntu server box as an NAS in the basement (500mhz pre-2000 system). It currently has two 320GB hard drives using [3ware] hardward RAID-1. I have one partition for /home and another one for everything else.I dream of upgrading to an entirely new system and, when I do, I want to move to software raid and lvm. When I upgrade, I wanted to add two more hard drives that are greater than (or equal to) my 320s.I think I understand the [[COLOR=#000000]software[/COLOR]](http://www.****************.com/h264-video-format/convert-avi-video-to-h264-format.html) raid component (creating the arrays), and I understand how lvm can make single larger volumes out of multiple arrays ... but is there a way to get some of the RAID-0 efficiency out of lvm if I am using mismatched sized drives ? For example, if I had two (2) 320s (RAID-1) and two (2) 750s (RAID-1) does LVM allow any striping of data between the two arrays to increase efficiency? Or, would I have to go with four (4) 320s ?Am curious for any advice you may have. Thanks,DamonThanks for your explanation! This is what I'm looking for.

---

