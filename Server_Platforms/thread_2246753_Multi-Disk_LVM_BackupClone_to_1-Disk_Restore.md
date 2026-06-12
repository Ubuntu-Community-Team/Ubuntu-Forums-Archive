---
title: "Multi-Disk LVM Backup/Clone to 1-Disk Restore"
date: 2014-10-03
forum: Server Platforms
---

### Post by Marc-NJ on 2014-10-03
I have an Ubuntu Server installation that spans 3 IDE HD's via LVM.  The total storage space in use is only about 11 or so GB (plenty of free space since I cleaned it up) and I want to move it all to one 500 GB HD.  What is the best way to do this?  I was messing around a little with Clonezilla, and it says it supports LVM2, but couldn't find anywhere in beginner mode to do an LVM backup (much less a restore to a different number of disks).  Any help is greatly appreciated.  Thanks!

---

### Post by oldfred on 2014-10-03
I do not know servers but will be shortly.

But I just built new system, so I plugged old drive (that will be in old system as server drive) into new system and used rsync to copy data. I always have issues understanding trailing / which puts it inside the mount and no trailing / which copies it. But then how you specify copy makes a difference. I started incorrectly once and had a lot to delete.

I already had created partition as ext4 with gparted. So I mounted it and gave myself owership & permissions.

sudo mkdir /mnt/data
sudo mount /dev/sdc4 /mnt/data
sudo chmod a+rwX,o-w /mnt/data
sudo chown $USER:$USER /mnt/data

I had two shared data partitions, one NTFS and the other ext3. I did not have any folders with overlapping names, so I could just copy.
rsync -aruvlP /media/fred/Data/ /mnt/data
rsync -aruvlP /media/fred/Shared/ /mnt/data

Because I copied from NTFS, I did have to go back & reset ownership & permissions for all those files. The -R means recursion or all lower levels also. Do not ever run on system partitions or you may damage system.
sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data

My understanding is rsync was/is more for network type copies, but you can use it instead of cp -a on local drives. In my case I could have used cp command.

---

### Post by Marc-NJ on 2014-10-03
Thanks for your response oldfred, but unfortunately I don't understand a lot of what you posted.  I feel like there has to be an easier way to just clone the entire logical volume and then push it to one drive (from the 3 drives it's spanned across), or is there really no easy way to do this?

---

### Post by oldfred on 2014-10-03
Is new drive plugged into server or is it on anther system?

Have you created partition(s) on new drive?
Have you mounted new drive?

Post this:
sudo parted -l
sudo fdisk -lu
mount

---

### Post by Marc-NJ on 2014-10-03
Sorry - I should have been clearer in my original post.  This thread might give some background ([http://ubuntuforums.org/showthread.php?t=2245154](http://ubuntuforums.org/showthread.php?t=2245154)).  Basically, I have a Dell Dimension 2400 (not the original system that Ubuntu Server was installed on; that was a Dell Dimension 8100 that got partially fried in a power surge apparently) that I have an LVM with three drives connected to it.  Two are connected via IDE cables directly (1 x 500 GB and 1 x 20 GB), and a third 500 GB HD is connected via an IDE to USB cable (since for some reason connecting it via IDE was causing the system to not recognize it).  A CD-ROM drive is also a slave on one of the IDE cables (via cable select).  Amazingly enough, it boots up fine and works pretty much fine.  The 20 GB HD is apparently failing though, but so far this hasn't seemed to impact anything aside from throwing up some errors and warnings.

Unfortunately, that's it for cables, so I think I need to figure out a way to shrink the LVM (it's around 1 TB - consisting of 2 x 500 GB hard drives and 1 x 20 GB hard drive), and then image/clone it to a file if possible, and then image/clone that to a 500 GB hard drive (I have an extra one) and then ensure that all the space on the "new" 500 GB HD containing the LVM is available to Ubuntu - even though right now the LVM is only about 11 GB or so).  Does that make sense?

Thanks!

---

### Post by oldfred on 2014-10-03
I do not know clonezilla, so cannot help.

Is CD a DVD or just CD. I do quarterly backup my most critical data to two DVDs or about 8GB. 

Many years ago I backed up to compressed images on floppy drives. But they were unreliable and any bit error prevented reading entire floppy. Since then I do not use compression even though it takes a lot more space. But now space is pretty inexpensive.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)

Another that others have mentioned:

 fsarchiver
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page) 
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

Old school is tar and perhaps compression.
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

 HowTo: Full backup with tar (older but tar has not changed)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
/home with tar - matthew
[http://ubuntuforums.org/showthread.php?t=1964130](http://ubuntuforums.org/showthread.php?t=1964130)

[https://help.ubuntu.com/community/FileCompression#GNU_Tar_GZ_.28.tar.gz_.tgz.29](https://help.ubuntu.com/community/FileCompression#GNU_Tar_GZ_.28.tar.gz_.tgz.29)

---

### Post by Marc-NJ on 2014-10-04
Through a lot of trial and error, I managed to solve my issue.  I booted into a Live CD and installed system-config-lvm which gave me a GUI for managing LVM.  I then was able to shrink the size of my VG, get rid of two of the three drives (and just keep the one 500 GB drive) by moving all the data (extants ?) to that drive and then removing the other drives, and then expanded the VG to the full size of the 500 GB drive.  After rebooting with just that one drive, I got nothing, so I used Boot-Repair (off of a Boot-Repair-Disk that I burned) to repair GRUB and voila - I'm good to go.  Didn't end up needing to do any cloning/restoring.

---

