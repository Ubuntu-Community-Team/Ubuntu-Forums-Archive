---
title: "Where is Raid Drive?"
date: 2005-08-04
forum: Server Platforms
---

### Post by MicroRacer on 2005-08-04
First off I am an extreme newby, but I am working a very difficult task. With no knowledge of Linux our company decided to integrate a Linux Server into our NT4.0 environment and eventually have it take over our file server which also runs the old NT4.0 Postoffice for internal mail.

I have tried Fedora Core 3 and SuSe 9.2 without total success (I'm learning as I go). I got to a point to where I realize I need help (I really do:)) and I found a CINLUG (Central Indiana Linux Users Group) boot camp is going to be held in 2 weeks. I found that the boot camp is going to use Ubuntu as their distro.

I decided to learn as much about Ubuntu as I could and I must say so far I am very impressed. I have been able to install Ubuntu, get the server on our network and get the server on the Internet. (typing from it now). The problem I am having is that I have a 360GB Raid 5 drive that I cannot see in order to share it. I know Ubuntu sees it because of the following fdisk -l command:

********@*********:~$ sudo fdisk -l
Password: **********

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9399    75497436   83  Linux
/dev/hda2            9400        9729     2650725    5  Extended
/dev/hda5            9400        9729     2650693+  82  Linux swap / Solaris

[b]Disk /dev/sda: 360.0 GB, 360099151872 bytes
255 heads, 63 sectors/track, 43779 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       43779   351654786   83  Linux[/b]
********@*********V:~$


I assume that under "COMPUTER" "Filesystem” is where I should find the drive. Under "Filesystem" is where I find my main drive with a "HOME" folder that I have been able to successfully share. 

Should the Raid drive appear separately under "COMPUTER" or will it be listed under "Filesystem"? I appreciate any help that I can get and I assure you that I am reading the forums diligently. This is my first post, but I think I have made good progress already.

Thanks Ahead

Bill

---

### Post by GrumpySmurf on 2005-08-04
Hello Bill,

I see you have a partition created, did you also create a filesystem on the device?

```

$ sudo mkfs.ext3 /dev/sda1

```
Will create an ext3 filesystem on the partition. Then, you'll need to mount it somewhere.  For example,

```

$ sudo mkdir /export
$ sudo mount -t ext3 /dev/sda1 /export

```
/export above can be any directory you want to mount the filesystem under. 

You will also need an entry in your /etc/fstab file to make sure this filesystem mounts on boot.  You can copy another entry in that file, or use one similar to this:

```

/dev/sda1 /export      ext3 defaults              1 2

```
I don't use the GUI in Linux for managing filesystems and disks, so I don't know where it would show up for you.  I imagine it would be under 'COMPUTER' somewhere though.

---

### Post by MicroRacer on 2005-08-04
[QUOTE=GrumpySmurf]Hello Bill,

I see you have a partition created, did you also create a filesystem on the device?[/quote]

The partition and filesystem was created under SuSe 9.2. Will the code that you gave me overwrite the data or do I just need to mount the drive? The data that is on the drive is not important so reformatting is a possibility.

[QUOTE=GrumpySmurf]
I don't use the GUI in Linux for managing filesystems and disks, so I don't know where it would show up for you.  I imagine it would be under 'COMPUTER' somewhere though.[/QUOTE]

As a newby to Linux the GUI interface keeps me from asking a million questions. Ubuntu requires enough Command line structure that I am learning Linux albeit slowly. I'm slowly beginning to understand that if I really want to understand Linux, that I had better learn the command line.

Thanks

Bill

---

### Post by GrumpySmurf on 2005-08-04
[QUOTE=MicroRacer]The partition and filesystem was created under SuSe 9.2. Will the code that you gave me overwrite the data or do I just need to mount the drive? The data that is on the drive is not important so reformatting is a possibility.[/quote]
If the filesystem is already there, you should just need to mount the drive. You may need to specify the filesystem type (ext3, reiserfs, etc) on the mount command.

> As a newby to Linux the GUI interface keeps me from asking a million questions. Ubuntu requires enough Command line structure that I am learning Linux albeit slowly. I'm slowly beginning to understand that if I really want to understand Linux, that I had better learn the command line.
You seem to want to know more and work closer with your system than the typical computer user.  The commandline is great for that as it removes the GUI abstraction layer from the picture.  Personally I just use the GUI as a way to open many more terminal windows to the servers I work on. :-)

Good luck

---

### Post by MicroRacer on 2005-08-05
I managed to mount the drive, and when I reboot I have to remount the drive every time. I did try adding the following line to my fstab file:

/dev/sda1 /export      ext3 defaults              1 2

This is my fstab file:

***********************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1	/ENG		ext3	defaults                  1       2
******************************

When ever I add this line to my fstab file I get the following boot error :

*******************************
Checking all filesystems

fsck.ext3: No such file or directory while trying to open /dev/sda1 /dev/sdaq:

The superblock could not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (not sswap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with and alternate superblock:

e2fsck -b 8193 <device>

[fail]

*fsck failed. Please repair manually.

*Control-D will exit from this shell and continue system startup.

Give root password for maintenance (or Control -D to continue);
******************************

I remove that line from my fstab file and everything boots normally..  Any ideas.

---

### Post by GrumpySmurf on 2005-08-09
> /dev/sda1 /export ext3 defaults 1 2

This is my fstab file:
# ...
/dev/sda1 /ENG ext3 defaults 1 2
Are you using /ENG or /export?  Make sure this is consistent.

> 
When ever I add this line to my fstab file I get the following boot error :
#...
I remove that line from my fstab file and everything boots normally.. Any ideas.

When the system is booted can you mount the filesystem manually?  If so, change the fstab entry to
```
/dev/sda1 /ENG ext3 defaults 0 0
```

---

