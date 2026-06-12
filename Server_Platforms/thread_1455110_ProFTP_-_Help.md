---
title: "ProFTP - Help"
date: 2010-04-15
forum: Server Platforms
---

### Post by BarryDocks on 2010-04-15
Hi there,

I have managed to set up ProFTP server with TLS on my Ubuntu 8.03 box.  I would like to contain the users to their home directory but allow access to a few select directories.  If I put a symlink to the directory in the user home directory then I have to comment out the line ```
DefaultRoot	~
``` to allow it to work but then the user also has access to all directories.

I understand there are per-directory options but I am really struggling to understand a simple method to achieve what I want.

Any help would be gratefully received.

---

### Post by richardjh on 2010-04-15
I haven't looked into the proftpd configuration but you could achive what you want by mounting the directories under the users home directory.

For example suppose you was to restrict user rob to his home directory /home/rob but also allow him access to /home/shared/files/

You could mount /home/shared/files/ under /home/rob/files/ like this.

1. Create a mount point ( a directory ) in /home/rob
mkdir /home/rob/files/

2. Mount the other directory under this mount point
mount --bind /home/shared/files /home/rob/files/

It will now appear that those files are actually under /home/rob/ so will be available even if you restrict the user rob to his home directory.

You can remount /home/shared/files in as many home directories as you like to share them to more users, without having to play with symlinks or reconfiguring proftpd each time you want to make a change.

If you want to add more directories to /home/rob it is easy to do repeating the same method.

---

### Post by BarryDocks on 2010-04-16
Richard,

Thanks for your reply, I didn't think of that.  It now leads to 2 other questions:
1.  To make the mount permanent I assume I would have to add a line to fstab?
2.  Would that also work for any samba shares?

Thanks again
A

---

### Post by richardjh on 2010-04-16
Yes, to make it persistent you would need to add it to /etc/fstab. Something along these lines

```
/home/shared/files/      /home/rob/files/   none defaults,bind 0 0
```

Any filesystems that are accessible can be remounted using the bind option, including smb shares.

---

### Post by BarryDocks on 2010-04-16
Thanks again for your help.  I have just one more question sort of on the same lines, which I think I already know the answer to but clarification would be great.
My server is currently configured with 2 RAID arrays, one RAID 0 and one RAID 1.  I have partitioned the RAID 1 array with 4 partitions:
MD0 OS - 20GB
MD1 swap - 1GB
MD2 home - 100GB
MD3 data - what ever is left over from 1TB
(MD4 and MD5 - other data on a RAID 0 array)

I am thinking that 100GB is slightly restrictive and would like to loose the partition but mount a directory on the data partition as /homes.  I assume this is possible ie to mount a directory rather than a disc partition as /homes?

Also what does the bind option do in fstab?

thanks
Adrian

my current fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=2d25b010-9117-428f-9d97-95758cee253f /               ext3    relatime,errors=remount-ro 0       1

# /dev/md1
UUID=926ed4e7-5a5b-481a-bc6e-94e588bd3359 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/md2  /home  ext3  defaults  0  0
/dev/md3  /media/raid1  ext3  defaults  0  0
/dev/md5  /media/raid0  ext3  defaults  0  0
/dev/md4  /media/raid0_proxy_cache  ext3  defaults  0  0
```

---

### Post by richardjh on 2010-04-19
You are correct that this is along the same lines.

Mount is generally used for mounting a block device under a mount point (directory). Although with [fuse]("http://fuse.sourceforge.net/"), all sorts of things are possible.

The bind option on the command line of in fstab, is a way that allows you to remount an existing directory somewhere else.
The previous replies show you how to do this already but in the example where you are concerned you will run out of disk space on your 100GB, you can remount directories from a bigger partition under a nearly full partition to make it appear as if you have much more space.

I would warn that it does start to get confusing if you use this a lot. It is better to configure the partitions correctly to begin with and use LVM at the outset to allow you to resize partitions in the event that your initial setup needs changing later.

In real life though it is handy to have alternatives. You sometimes need them.

---

### Post by BarryDocks on 2010-04-20
thanks for your help

---

### Post by BarryDocks on 2010-05-03
one other quick question, I have now decided to completely do away with windows altogether and have just installed Ubuntu 10 on my laptop.  I have partition the hard disc into 4 bits:
```
adrian@adrian-laptop:~$ sudo fdisk -l
[sudo] password for adrian: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00087b50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9764864   83  Linux
/dev/sda2            1216        1703     3906560   82  Linux swap / Solaris
/dev/sda3            1703       19458   142616577    5  Extended
/dev/sda5            1703        2918     9764864    b  W95 FAT32
/dev/sda6            2919       19458   132850688   83  Linux

```
sda6 is mounted on boot as /media/data, I would like to move my home folder to a folder on that mount but don't know how.  I have done a google search but they all move the home folder to use an entire partition.  Any suggestions?

Thanks

---

### Post by richardjh on 2010-05-04
The home folder can be anywhere and is defined in /etc/passwd.
My entry in my /etc/passwd looks like this

```
richardjh:x:1000:1000:Richard Holloway,,,:/home/richardjh:/bin/bash
```So my home directory is /home/richardjh

To manually move my home folder to /media/data/richardjh you could do

```
cd /home
sudo mv richardjh /media/data/

sudo vim /etc/passwd
and replace /home/richardjh with /media/data/richardjh 

```

**However you can usermod to do this for you**

```
sudo usermod -m -d /media/data/richardjh richardjh
```More details on usermod can be found by typing 
```

man usermod
```And the relevant section is

```
       -d, --home HOME_DIR
           The users new login directory.

           If the -m option is given, the contents of the current home
           directory will be moved to the new home directory, which is created
           if it does not already exist.
```

---

### Post by BarryDocks on 2010-05-05
Thankyou Richard, you are a gent.

know anything about NFS shares?:
[http://ubuntuforums.org/showthread.php?t=1472799]("http://ubuntuforums.org/showthread.php?t=1472799")

---

### Post by Xinerama on 2010-07-22
Thanks Richard!!

---

### Post by christhegoth on 2010-08-15
Nice tip for mount folders under folders, danke :)

I have another woe.  Just added a user on a proftpd.  Normally it's fine, but this one won't let me log in.  Keeps saying the password is incorrect.

All other proftpd accounts work.

What I'd like to do is change the password by terminal command-line.  Any idea how to do it?

---

### Post by BarryDocks on 2010-08-18
> **christhegoth said:**
> Nice tip for mount folders under folders, danke :)

I have another woe.  Just added a user on a proftpd.  Normally it's fine, but this one won't let me log in.  Keeps saying the password is incorrect.

All other proftpd accounts work.

What I'd like to do is change the password by terminal command-line.  Any idea how to do it?
I think you just change the password for the corresponding unix user, see:
[http://www.cyberciti.biz/faq/linux-set-change-password-how-to/]("http://www.cyberciti.biz/faq/linux-set-change-password-how-to/")

---

### Post by christhegoth on 2010-08-18
Cheers Barry.

I did crack it in the end.  I was dropping into an NTFS based folder, and it wouldn't have it.  So I did a work-around ;)

---

### Post by BarryDocks on 2010-12-06
Any idea how to modify the fstab to mount a directory in every users home folder?  I suspect it is very simple.

Thanks

---

