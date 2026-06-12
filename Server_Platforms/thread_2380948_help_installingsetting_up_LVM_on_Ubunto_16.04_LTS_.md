---
title: "help installing/setting up LVM on Ubunto 16.04 LTS server with 2 HDDs?"
date: 2017-12-24
forum: Server Platforms
---

### Post by zoldos on 2017-12-24
Greetings.  I have a fully dedicated Ubunto 16.04 LTS server with 2 physical HDDs, 2TB each.  I'd like to use LVM to make it one big 4TB drive.  I contacted my host and they can't do it themselves as my account is un-managed, but I have full root access and the ability to put my server in "Recovery Mode" and then run the "rescue disk" via SSH.  Thus enabling the use of LVM.

How hard is this?  I don't recall ever successfully using SSH to my manage my server and simply use Putty to open the console.

Is this task something that a more experienced person can/should do?  I can pay a little bit for anyone's time.

Comment please?  Thanks!

---

### Post by volkswagner on 2017-12-25
Putty is an ssh client. If you have used putty to connect and manage your server
than you have used ssh.

Are these two hard drives the only two drives in the system?
If your operating system is installed already you'll want to be
understanding the risks involved.

please provide output of the following commands:
```
df -h
```
```
df -i
```
```
fdisk -l
```
```
cat /etc/fstab
```

Why do you want to combine the two 2TB disks into
one logical volume?

---

### Post by darkod on 2017-12-26
How I see it, to do this you need to have access to some kind of console. You probably do if the service is unmanaged and they asked you to reinstall the OS yourself.

If there is no important data on the server yet, I would simply reinstall creating manually 2GB /boot partition and the rest into one big Volume Group.

If there is data on the server, it becomes much more complicated if you want to move the whole root onto the LVM.

---

### Post by LHammonds on 2017-12-26
If you have the option, I'd re-create the server.  Check my signature on how I install the OS which uses LVM and shows you how to add additional drives into the LVM.

LHammonds

---

### Post by zoldos on 2017-12-27
Thanks for all the replies!  Basically, I have the OS/server installed and everything is running perfectly on the first 2TB HDD.  My concern is this:  What happens if I somehow use up the existing 2TB drive?  I'm only using like 7% right now, but I'm annoyed that I have potential access to a SECOND 2TB HDD but apparently can't use it unless I combine them.

What's the point of having two drives (both recognized by df -h) but I really only have the ability to use one?  That doesn't make any sense to me.

My host said I can use "recovery mode" to combine them as that way the system will NOT be accessed at the time since it's the same as booting from a CD, but I honestly have no idea how to actually use LVM to combine the drives.

Is it really that complicated?  And what are some thoughts on space?  Is 2TB enough for a small site that allows videos etc.?  My site is almost 3 years old and currently uses 110GB (that's with over 1500 videos).

Thanks!

---

### Post by volkswagner on 2017-12-27
You don't need to use LVM to utilize all of your drives.

In Linux you mount partitions in directories. So if you
have a website at /home/usera/site1, you could mount a large
partition at /home/user/site1/bigData to add additional items to this directory.

If you'd like help, posting the previously requested commands would
be necessary.

If you've only used 110GB in three years, with the same growth... 2TB wouldn't 
fill up until another ten years or so.

---

### Post by LHammonds on 2017-12-27
volkswagner said the same thing I was about to mention.

I have experience setting up LVM at the time of initial setup but I have never converted a system that isn't using LVM to use LVM.  If this is the only way you see to make use of it rather than just mount a folder as the 2nd drive, then I'd suggest using Oracle VirtualBox to install the server like you originally did without any LVM and work out the procedure to convert it to LVM before ever trying to do it on your live system.  And before you do it on your live system, make sure you have a backup to restore the entire server if something goes sideways...and make sure it is a good backup.  Nothing sucks worse than needing a backup only to find out you cannot use the backup.

Google search results:
[Setting up LVM without a clean install]("https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall") - [Original source of the info to the left]("https://wiki.gentoo.org/wiki/LVM")

[Blocks utility]("https://github.com/g2p/blocks#readme")

[Migrate from Direct Partitions to LVM Volumes](https://www.linux.com/learn/weekend-project-migrate-direct-partitions-lvm-volumes)

[Potential but unverified steps to convert to LVM]("https://ubuntuforums.org/showthread.php?t=2202677")

[Warren Togami's tutorial on remote conversion]("http://togami.com/~warren/guides/remoteraidcrazies/") - Has good info on modifying fstab and grub

From what I've been seeing, it may be possible to use the 2nd (blank) disk to create an LVM on it, then rsync your entire OS onto the new LVM and modify grub to boot the LVM on the 2nd disk.  Once you are running on the 2nd disk, destroy the 1st disk and add it to the LVM.  Not sure how this would work step-by-step though.

If you cannot use the 2nd disk, you'd have to shrink the existing partition (if you had the space) and create an LVM on it, then copy the data, modify grub and such.

LHammonds

---

### Post by zoldos on 2017-12-28
So I can mount a drive at a certain sub folder, and moves files there?  That would be great.  The bulk of the 110GB is videos.  Would it be hard to "match" the new folder "name" to the old one and then just copy the files?  Also see below for the various console output. you requested.

Thanks to everyone else as well! :)

> **volkswagner said:**
> You don't need to use LVM to utilize all of your drives.

In Linux you mount partitions in directories. So if you
have a website at /home/usera/site1, you could mount a large
partition at /home/user/site1/bigData to add additional items to this directory.

If you'd like help, posting the previously requested commands would
be necessary.

If you've only used 110GB in three years, with the same growth... 2TB wouldn't 
fill up until another ten years or so.

```
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  154M  1.5G  10% /run
/dev/sda4       1.8T  115G  1.6T   7% /
tmpfs           7.9G  4.0K  7.9G   1% /dev/shm
tmpfs           5.0M   20K  5.0M   1% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sdb1       1.8T   68M  1.7T   1% /mnt/disk1
/dev/sda2       473M   55M  394M  13% /boot
tmpfs           1.6G     0  1.6G   0% /run/user/0


Filesystem        Inodes  IUsed     IFree IUse% Mounted on
udev             2033031    486   2032545    1% /dev
tmpfs            2045932    722   2045210    1% /run
/dev/sda4      121569280 565006 121004274    1% /
tmpfs            2045932      2   2045930    1% /dev/shm
tmpfs            2045932     25   2045907    1% /run/lock
tmpfs            2045932     16   2045916    1% /sys/fs/cgroup
/dev/sdb1      122101760     11 122101749    1% /mnt/disk1
/dev/sda2         124928    300    124628    1% /boot
tmpfs            2045932      4   2045928    1% /run/user/0


Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: EE9BD72F-54BF-424A-AAC7-E4A01D5B0BB3

Device        Start        End    Sectors  Size Type
/dev/sda1      2048       4095       2048    1M BIOS boot
/dev/sda2      4096    1003519     999424  488M Linux filesystem
/dev/sda3   1003520   17004543   16001024  7.6G Linux swap
/dev/sda4  17004544 3907028991 3890024448  1.8T Linux filesystem


Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 087D6B2E-0E88-41BE-8622-7D44110ACBA3

Device     Start        End    Sectors  Size Type
/dev/sdb1     34 3907029134 3907029101  1.8T Linux filesystem

Partition 1 does not start on physical sector boundary


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=afc763db-a351-429d-a45e-16bad42c825c /               ext4    errors=remount-ro,usrquota 0       1
# /boot was on /dev/sda2 during installation
UUID=88e5ac5c-d49a-43d0-af39-07f3cbbb2758 /boot           ext2    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=7b97e7fd-68ae-4390-988b-ad403a9373a6 none            swap    sw              0       0
/dev/sdb1               /mnt/disk1              ext4    defaults        0 0

```

:D

---

### Post by volkswagner on 2017-12-28
Yes you can move things around a bit to keep your folder name.
What folder would you like to relocate to the larger drive?

---

### Post by darkod on 2017-12-28
One important limitation: the mount folder has to be empty at the start.

Later you will move/copy files to it, but at the moment when you are setting up and mounting the /dev/sdb1 partition to it, it has to be empty. So if you already have files in there you have to temporarily move them, and then move them back.

Just think very good about which folder structure works for you best before you begin. It's best to get it right the first time... :) You shouldn't rush with the decision which folder to use as mount point. Think long term...

---

### Post by zoldos on 2017-12-28
> **volkswagner said:**
> Yes you can move things around a bit to keep your folder name.
What folder would you like to relocate to the larger drive?

Okay, these are the two largest folders, I'd like to "move" them to the second 2TB drive, but it would have to appear to be the same folder as before or it will break my site. I'm not sure how to tell my forum to use a different folder to save data:

/var/www/vhosts/xxxxxx.net/httpdocs/data/videos
/var/www/vhosts/xxxxxx.net/httpdocs/data/attachments

Thanks!

---

### Post by zoldos on 2017-12-28
> **darkod said:**
> One important limitation: the mount folder has to be empty at the start.

Later you will move/copy files to it, but at the moment when you are setting up and mounting the /dev/sdb1 partition to it, it has to be empty. So if you already have files in there you have to temporarily move them, and then move them back.

Just think very good about which folder structure works for you best before you begin. It's best to get it right the first time... :) You shouldn't rush with the decision which folder to use as mount point. Think long term...

So sdb1 has to be empty?  Isn't that my boot drive?  Wow, I don't want to mess anything up..

---

### Post by darkod on 2017-12-28
First, sda is your boot drive, not sdb.

Second, I said the FOLDER that you plan to use for mount point (for example /data) has to be empty. Not the partition sdb1 of the disk. There is a big difference.

---

### Post by zoldos on 2017-12-28
> **darkod said:**
> First, sda is your boot drive, not sdb.

Second, I said the FOLDER that you plan to use for mount point (for example /data) has to be empty. Not the partition sdb1 of the disk. There is a big difference.

Okay I got ya. So /dev/sdb1 is the second drive...

---

### Post by zoldos on 2018-01-01
So it looks like I can mount the second 2TB drive and then map a folder to it?  I'd like to put some of my larger folders on it, but without having to change anything on my site as to where things are stored.

Is this possible?  Thanks!

---

### Post by darkod on 2018-01-01
Well, you can't mount the same partition at two different mount points. So, you either need to make two partitions on sdb instead of one, and mount them at ../data/videos and ../data/attachments. Or mount the existing single partition sdb1 at ../data.

But befor starting with all of this, I would really consider if it is worth doing it. You seem to have very little linux experience despite of running your own server. You also have plenty of space on the current 2TB disk and it is not filling up very fast. That means (like others have commented here) that it will probably pass years before it is close to full. Maybe you will even to decide to migrate to another server/provider by then. I know the second HDD just sits there unused, but since you don't really need to do all this migration of data, is it really worth the risk of something going wrong??? Think practical, not just because you have new disk to use... That is not a reason enough.

If you do decide to go forward, like I said above you need to decide if you will use one or two partitions on sdb and where to mount accordingly (one or two mount points).

Then you will need to move the data from those folders (the mount points) because they need to be empty, and then mount the new partitions. You can move data directly to the new partitions so that you don't need to move it twice. After you mount the partitions at the correct mount points, the data is already there where you need it.

This operation does need a short stop of services of course. The websites will not be working while you are doing this...

---

### Post by zoldos on 2018-01-01
Yes I'm starting to agree, it does seem silly to do all this when I'm barely using the first 2TB.  I think I'll just keep things the way they are.  There is a higher server plan that has 2x4TB that I'll probably migrate to down the road (plus it has more CPU power and more ram).

Thanks to everyone!! :D

---

