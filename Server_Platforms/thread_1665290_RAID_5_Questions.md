---
title: "RAID 5 Questions"
date: 2011-01-12
forum: Server Platforms
---

### Post by expatCM on 2011-01-12
Ok so it appears I am about to set up a RAID 5.  Trouble is that all I know I have read in various threads and I still have a few things that I do not understand.

Is it correct that whilst there need to be three drives or more to initially set up, none may be more than 2TB?  (just thinking forward)

If there are three hdd's, would 2 x 2TB and 1 x 500GB be ok?  Seems to me not due to the difference in volume sizes but it is still  three drives.

If a hdd fails, how easy is it to remove the failed drive and bring a new drive into service (I hear that it takes a day to reconfigure the RAID)? Do you power down / hot swap or what ...  

Is it easy to add more drives?  

How is the RAID managed, is it a GUI or command line?  

Where a drive fails, do you need to replace with the same size or can you add larger (or smaller) drive?

Is there any way to use power management to keep a RAID lean with power use?

I was reading this blog and for setting up it says "as root, issue issue an fdisk -l to bring up a list of available disks." So does that imply that the operating system is installed and running on another drive the RAID will simply manage extra drives?  Or that you have the o/s running on one of the drives and it gets trashed as part of the process?
[http://blog.swapnil.me/2011/01/simple-recipe-to-create-raid5-under.html](http://blog.swapnil.me/2011/01/simple-recipe-to-create-raid5-under.html)

Is there a good "how to" anywhere?

---

### Post by sj1410 on 2011-01-12
> Ok so it appears I am about to set up a RAID 5.  Trouble is that all I know I have read in various threads and I still have a few things that I do not understand.

Is it correct that whilst there need to be three drives or more to initially set up, none may be more than 2TB?  (just thinking forward)

If there are three hdd's, would 2 x 2TB and 1 x 500GB be ok?  Seems to me not due to the difference in volume sizes but it is still  three drives.


You can have harddisk of more than 2TB, but, you need to have all hard disk of equal sizes.

> If a hdd fails, how easy is it to remove the failed drive and bring a new drive into service (I hear that it takes a day to reconfigure the RAID)? Do you power down / hot swap or what ...  


if you have hot swap hdd than you don't need to poweroff the system, just replace the hdd. its raid5, your working wont be interrupted if one hdd fails. and it wont take much time to resync.

> Is it easy to add more drives?  

How is the RAID managed, is it a GUI or command line?  


With the release of kernel 2.6.17, there&#8217;s new functionality to add a device (partition) to a RAID 5 array and make this new device part of the actual array rather than a spare.

its all command line, but you can use webmin to manage mdm

> Where a drive fails, do you need to replace with the same size or can you add larger (or smaller) drive?


same size is recommended, smaller is not allowed, larger can be used.


> Is there any way to use power management to keep a RAID lean with power use?

I was reading this blog and for setting up it says "as root, issue issue an fdisk -l to bring up a list of available disks." So does that imply that the operating system is installed and running on another drive the RAID will simply manage extra drives?  Or that you have the o/s running on one of the drives and it gets trashed as part of the process?
[http://blog.swapnil.me/2011/01/simple-recipe-to-create-raid5-under.html](http://blog.swapnil.me/2011/01/simple-recipe-to-create-raid5-under.html)

Is there a good "how to" anywhere?

This guide details setting up software RAID 5 on Ubuntu / Debian using mdadm post install. It does not cover everything you need to know about RAID and the knowledge in this document is by no means extensive

please remember that no RAID solution is a viable replacement for good backups! If your data is so valuable that you can&#8217;t afford to loose it (either due to hardware, or user error) then make damn sure it&#8217;s backed up on a remote machine / device.

---

### Post by trundlenut on 2011-01-12
Using 2x2tb and 1x500gb would give you a raid 5 array of 1tb (actually a bit less) and a load of empty space on the 2tb drives (1.5tb per drive).

Using mdadm raid you could proabably set up more than one 500gb partition? on each of the larger drives but that would just kill the array is one of the large drives failed.

I would get hold of another 2tb drive, then you could have a 4tb raid5 array.

If you can't get any more drives for now I would use the 500gb to install ubuntu server on and then use the 2x2tb drives in a mirrored raid 1 array for storage of files/data.

---

### Post by expatCM on 2011-01-13
good to open the thread ...  I am learning things that I had overlooked ...

So basically if there is a five drive RAID and the drives are a mix of 2TB, 1TB and 500GB, the volume of the RAID will be 5 x 500GB less 1 x 500 GB = 2TB.  The actual available space will then be that figure less the space needed by the partition table.

Not quite what I had understood that at the outset but if that is the reality of life then that is the way it is.  

So I may need to wait to either buy a set of dedicated drives all of the same size or set up a RAID with smaller volume than anticipated.

I guess this also has an impact on future maintenance since you really need to replace like with like or larger (with waste).

---

### Post by trundlenut on 2011-01-13
Yes, raid 5 gives total storage of (n-1) x smallest capacity drive, where n is the number of drives.

You could set up a 1tb raid 5 and a 1.5tb raid 1 array with the disks you have but that seems rather a faff.  Another 2tb drive is probably the way forward to give you 4tb as raid 5 for storage and then install the OS on the 500gb drive.

I have a setup with 2x36gb as raid 1 for my OS and then 4x72gb as raid 5 for storage of files on my server.  That's running hardware raid as well.

---

### Post by rubylaser on 2011-01-13
Another option would be to build your 1TB array now, and when you have the money, fail the 500GB disk, and replace it with another 2TB disk.  All you'll need to do after that is grow the filesystem.  Here's how you'd remove the disk...
```
mdadm --manage /dev/md0 --remove /dev/sdc1
```
Then add the new 2TB disk
```
mdadm --manage /dev/md0 --add /dev/sdc1
```
As a precaution, before you grow the filesystem you'd need to unmount the raid array:
```
sudo umount /dev/md0
```
Now that it is unmounted we can run a filesystem check to make sure everything is in order:
```
sudo fsck.ext4 -f /dev/md0
```
If any issues arise, let it attempt to fix them for you.

Once the filesystem has been checked we can perform the resize. If you decided to use something other than ext2/3/4 this may be done differently, but for the ext2/3/4 filesystems we use the resize2fs tool.

```
sudo resize2fs /dev/md0
```
This will automatically grow the filesystem to the new size of the device.

You can now remount the drive and start filling it up again!

---

