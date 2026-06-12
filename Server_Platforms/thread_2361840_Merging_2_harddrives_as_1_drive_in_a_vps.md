---
title: "Merging 2 harddrives as 1 drive in a vps?"
date: 2017-05-21
forum: Server Platforms
---

### Post by thexnightmare on 2017-05-21
Dear,
I have a VPS with ubuntu amd 2 harddisks, the first is 50 GB, and thesecond is 50 GB.
Can I merger them together so I see them as 1 drtive for total 100GB without formatting it?
Thanks

---

### Post by slickymaster on 2017-05-21
*Thread moved to **Server Platforms*** for a better fit

---

### Post by darkod on 2017-05-21
I don't think you can. To merge multiple physical devices into one logical device, you use LVM. But the process involves adding partitions as physical volumes into the LVM, and then creating volume group and finally logical volumes, and format them.

I don't think you can deploy LVM without losing the existing data. That is why LVM is usually deployed during the initial OS installation.

PS. What you could do is use the second hdd mounted on a mount point (empty folder) which will allow you to use it's space. But the OS will not see 100GB single volume. It will still see the 50GB you have for the root partition, and then 50GB mounted in one folder, for example /data.

---

### Post by thexnightmare on 2017-05-21
isee, so, another quesiton, i had installed plesk to my ubuntu and iut sees my first hdd, but it dont see my second hdd, how to solve that then?

---

### Post by darkod on 2017-05-21
I don't know details about plesk. For how to use the second disk see the PS in the previous post.

---

### Post by thexnightmare on 2017-05-21
the problem is tha,t i cant format the vps, it is remotely accessible, and have ubuntu preinstalled on it

---

### Post by darkod on 2017-05-21
I am talking only about formatting and using the second disk, not the whole VPS. Decide how you want to call the mount point folder, create it, and then simply make a partition on the new disk, format it and mount it there.

There are loads of tutorials online... Pick the one that suits you most. :)

---

### Post by TheFu on 2017-05-21
Not without reformatting.

However, you can use symbolic links to make directories on 1 disk *appear* anywhere you like.  Just be careful if they become recursive.

Since it is at a VPS, I'll assume you need more web storage under /var/www/html. I had a similar issue. My solution was to mount an extra disk to /var/www.  See:

```
$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/vda1        7389384 3968816   3045272  57% /
/dev/vda2        2325684 1112212   1095260  51% /var/www
```
See how I mounted vda2 directly to /var/www and not in /var?  It would have been a hassle to relocation /var/log/ and /var/lib/.  I didn't want that hassle. Those files/directories are still on vda1, happily working.

If I need to use some storage that is on vda1, but want it under /var/www/whereever, then I'd use symbolic links to seamlessly join a new directory.  If you need everything in a single directory, there isn't a good option. Symlinks really work best for subdirectories. 

As Darkod says, in the future, using LVM would be strongly recommended when you setup a new OS. It can add some complexity, but it can also provide lots and lots of flexibility and help with backups.

**ln -s source target**

---

### Post by thexnightmare on 2017-05-21
tried but didnt worked

---

### Post by TheFu on 2017-05-22
> **thexnightmare said:**
> tried but didnt worked

There are multiple techniques above.
If you want help, we need info.

What did you try, exactly? 
What exactly didn't work?

So commands and output, please.  "didn't work" isn't enough to guess what you did.

---

### Post by thexnightmare on 2017-05-27
# df
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             3984080        8   3984072   1% /dev
tmpfs             798236     1712    796524   1% /run
/dev/vda1       41251136 13536860  26005836  35% /
none                   4        0         4   0% /sys/fs/cgroup
none                5120       20      5100   1% /run/lock
none             3991164       80   3991084   1% /run/shm
none              102400       16    102384   1% /run/user



~# fdisk -l


Disk /dev/vda: 42.9 GB, 42949672960 bytes
4 heads, 32 sectors/track, 655360 cylinders, total 83886080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00096ccc


   Device Boot      Start         End      Blocks   Id  System
/dev/vda1   *        2048    83886079    41942016   83  Linux


Disk /dev/vdb: 53.7 GB, 53687091200 bytes
7 heads, 22 sectors/track, 680893 cylinders, total 104857600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb3ce16a1


   Device Boot      Start         End      Blocks   Id  System
/dev/vdb1            2048   104857599    52427776   83  Linux


Disk /dev/mapper/docker-253:1-1713716-pool: 107.4 GB, 107374182400 bytes
255 heads, 63 sectors/track, 13054 cylinders, total 209715200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 65536 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/docker-253:1-1713716-pool doesn't contain a valid partition table

---

### Post by TheFu on 2017-05-27
Please edit the last post to add "code tags" - hard to read otherwise.
> However, you can use symbolic links to make directories on 1 disk appear anywhere you like. Just be careful if they become recursive.
But **df** and **fdisk** AREN'T going to help.  Those don't merge or link anything.  You need to use **ln -s** or mount or edit the fstab or wipe everything and use LVM to make changes.  

Those are choices to a solution. Without knowing WHAT it is you want, we really cannot help.  What do you want from those choices?

[B]Option 1 - downtime required.
[/B]I see you have another raw virtual disk added.  The most elegant solution is to wipe everything on vda-whatever and use LVM to merge the disks. This will require an OS reinstall, so backup anything you want to keep.  During the install, tell the installer to use LVM for at least 1 of the disks. Ignore the other for now.  Finish the install, check that everything is working and the **lsblk** shows that everything is fine.  Then create a new partition that uses the entire vdb disk, vdb1.  Inside vdb1, create as large a PV, physical volume, as you can. Add the PV to the existing VG that vda1 is using.  then extend the LV used already.  lvdispla, vgdisplay, pvdisplay are the commands to see what is going on.  pvcreate, vgcreate, and lvcreate are the commands to create each of those LVM storage containers.  You can think of an LV as a partition, but an extremely flexible partition.  Use vgextend and lvextend to increase the sizes of a VG and an LV.   Do not use all the storage for the LV. Leave some for other uses, like snapshots.  It is very easy to extend an LV - even on a running system. Take advantage of that by only allocating what you need now. Be flexible.
**Beware, if your LV spans multiple disks and 1 of those disks fails, you can lose all data. Backups are the only prevention for total data loss.** I lost 80% of my data in 2002 because I didn't have backup religion then and used LVM in this way - spanning drives. It was a rough lesson to learn.

If you are smart, you can move data around between the 2 disks and avoid wiping, but still end up with LVM after a fresh install on vda and add vdb back into the LVM setup. 

I'd practice this on a VM running on my home PC a few times before touching a production system. Howtoforge has an LVM tutorial which could be helpful.

**Option 2**
Mount the new storage where needed, move all the files over.
[LIST=1]
[*]Partition vdb
[*]Create a Linux file system on one of the newly created partitions
[*]Mount the new partition (probably vdb1) somewhere - I'd use a directory right next to the current directory unless I had a good reason to do something different.  If I wanted to move /var/www/* data, then I'd mount vdb1 to /var/www-new/
[*]Stop any use of that storage/directory by the system (top any services using it); service apache2 stop; service mariadb stop ... etc.
[*]Move all the files, using sudo mv, from the vda? to vdb1 (cd /var/www-new/; mv ../www/* ./)
[*]After the move finishes, umount vdb1 ....
[*]And mount it to the empty directory where everything was moved from. 
[*]Does everything look like it did before? Do all the directory paths look correct? Yes/No?
[*]If No, umount the vdb1 storage and try again. It needs to appear on the file system as it did BEFORE all this was started.
[*]If Yes, update the /etc/fstab to mount the vdb1 storage to the same directory you did with the manual mount command
[/LIST]
Simple.

**Option 3**
The least elegant - just make it work solution is to do everything in option 2, but don't change the mount location back.  They use ln -s /var/www-new /var/www; need to delete the /var/www before that will work, so be very certain it is empty.  The key is that cd /var/www/ should take you to the top level and everything should "appear" to be where it was before under /var/www/.  Simple, ugly, but effective.

Since only you know the exact places that will be dealt with, only you can use the correct commands and inputs and options.  It is too hard to get everything perfect from here. Plus, that is *work*, not something my volunteer-self is too interested in.

Again, the key is that all the files need to appear to be in the exact same place they were before you started.  If the directories look the same with the same owners, permissions, etc, then the OS and programs will be happy.

Option 1 will make adding new storage the next time much, much, easier.  You'd just add the new disk to the VG and extend the LV as needed. That could all be done while the system is up and running.  LVM is amazing and highly flexibly, for the cost of a little extra complexity up front.  After that, it is a joy to have and unless you are doing storage stuff, you can forget about it.  Oh ... and LVM will allow you to use snapshots for part of your backups. No need to bring down a DB or dump the DB contents just to have a clean backup. Use an LVM snapshot.

Clear at mud?

---

