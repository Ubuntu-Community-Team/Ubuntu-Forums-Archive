---
title: "RAID-5, fdisk and unable to partion?"
date: 2013-02-08
forum: Server Platforms
---

### Post by Joezorry on 2013-02-08
I've set up a home server and I've set-up RAID-5 with 3 drives, mostly by following the guides here ([http://www.howtogeek.com/51873/how-to-setup-software-raid-for-a-simple-file-server-on-ubuntu/](http://www.howtogeek.com/51873/how-to-setup-software-raid-for-a-simple-file-server-on-ubuntu/)) and here ([http://ubuntuforums.org/showthread.php?t=517282](http://ubuntuforums.org/showthread.php?t=517282)).

I had some problems setting up the array but finally got i working (seemed to be a problem with how I had setup the config), but now I have a space that is called /dev/md0/.

I have a problem and a question:
First the problem, I run this in the terminal:
```
sudo mkfs.ext4 /dev/md0
```

Which seems to do nothing, it creates no partion which can be mounted or anything, although the output seems ok:

```
mke2fs 1.42.5 (29-Jul-2012)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=128 blocks, Stripe width=256 blocks
244178944 inodes, 976690944 blocks
48834547 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
29807 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848, 512000000, 550731776, 644972544

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done    
```


And now for the question:
fdisk -l command shows two "swap" which is roughly the size of the array, which is listed under /dev/mapper/ 
What exactly is those drives and should they be there?
When I do sudo fdisk -l the output is:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   312581807   156290903+  ee  GPT

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
63 heads, 63 sectors/track, 984386 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001315a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
63 heads, 63 sectors/track, 984386 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000264b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
63 heads, 63 sectors/track, 984386 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00052515

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/md0: 4000.5 GB, 4000526106624 bytes
2 heads, 4 sectors/track, 976690944 cylinders, total 7813527552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/mapper/ServerWatcher-root: 155.6 GB, 155608678400 bytes
255 heads, 63 sectors/track, 18918 cylinders, total 303923200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ServerWatcher-root doesn't contain a valid partition table

Disk /dev/mapper/ServerWatcher-swap_1: 3972 MB, 3972005888 bytes
231 heads, 4 sectors/track, 8395 cylinders, total 7757824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ed23834

                            Device Boot      Start         End      Blocks   Id  System
/dev/mapper/ServerWatcher-swap_1p1            2048     7757823     3877888   fd  Linux raid autodetect

Disk /dev/mapper/ServerWatcher-swap_1p1: 3970 MB, 3970957312 bytes
255 heads, 63 sectors/track, 482 cylinders, total 7755776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ServerWatcher-swap_1p1 doesn't contain a valid partition table
```

---

### Post by darkod on 2013-02-08
You don't partition the md devices. That's why you need to create separate md arrays/devices for all partitions you want separate.

For example, if you want a system running root, swap and /home on separate partitions, you create md0, md1 and md2.

You don't split md0 to three partitions.

As for /dev/mapper/... devices they usually mean fakeraid array or LVM system. Make sure you didn't do any of that, unless you really want LVM.

Also, the first tutorial you linked uses fdisk to partition but in reality that is a poor choice (although many people keep using it). For command line partitioning tools I prefer parted or cfdisk, instead of fdisk. For GUI, you have Gparted.

If you still have no data on the server, I suggest you redo it again, but this time with better planning:
1. How many partitions do you want? Just root and swap or also /home?

If this server will be like a network server with shares, i guess you don't need separate /home folder because there will be no users to guard things directly in /home on the server. A better choice might be making separate /data partition for the data.

What I would do is:
raid1 md0 device for /
raid5 md1 device for /data
swap partitions outside of the raid

Swap can easily be outisde of the raid, it will use how many swap partitions you tell it to use.

Do you plan to use that 160GB disk? For what?

---

### Post by Joezorry on 2013-02-08
Great , you answered some of my concerns.
I use the 160 gb drive for the OS and then then three separate 2TB drives for a RAID-5 array which will be a network drive.

Sorry for being a noob on this, but I've not defined the swap for any of the drives, is this something that is created on reboot (it appeared after reboot on the RAID for me). I've not used fakearray but software raid, which I guess should make it a LVM drive (although I don't remember choosing that for the RAID). I know I chose it for the OS drive.

md0 in my case should be the raid array.

I can recreate the RAID drives because they are still empty.
I could recreate the OS drive too, but I would rather not.

Other than the tips you mentioned do you have any other tips if I should recreate them.

---

### Post by Joezorry on 2013-02-08
Oh, and yes. Since it is a server without GUI I used fdisk to format and partion the drives. Set the devices to linux raid auto detect as mentioned in the guide.

And I want to grow the array at a later point, can I do that without LVM?
Why is chdisk better?

---

### Post by darkod on 2013-02-08
OK, one thing at a time. :)

I have seen threads that fdisk sometimes created the partitions with faults, especially for software raid. It doesn't mean it will happen every time, but cfdisk and parted seem more recommended.

LVM is not the same with SW raid. In fact, they are very different. If you used LVM for the OS setup, that's why you are seeing the /dev/mapper/... devices.
You can have LVM on top of SW raid for example. If you want to do that, start planning from now when you are creating your data storage.

In your place, I would consider getting rid of the 160GB disk and put the OS on the raid too, but as raid1 (mirror). For example, create small 15GB partitions on the start of each disk and use them for raid1 root device. You can set all three partition in raid1, so even if two fail the OS will still be running. Of course, with two disks failed your data array will not activate because raid5 can't work without two members.

Even if you don't use LVM you can grow SW raid array later. That is the benefit compared to fakeraid where in most cases you need to destroy the array and make a new one. So, if the LVM was only for future growing, you can do it without it. Don't forget that LVM adds another layer of complexity to the system.

If you choose to move the OS to the array, you could do something like:
```
sda      sdb      sdc
15GB      15GB      15GB      md0 raid1 /
 2GB       2GB       2GB      swap
xxGB      xxGB      xxGB      md1 raid5 /data
```

If you think you need more than 15GB for / make the partitions bigger.

You might even be able to copy the current / content to the newly created md0 and it should be able to start working after you run few commands.

The first decision you have to take is: SW raid only, or LVM on top of SW raid.

---

### Post by Joezorry on 2013-02-08
If one can grow the SW raid without LVM I really don't see the point of using LVM?

I was thinking of either create a scheduled snapshot command or make the OS on a RAID-1 array, because I have a  spare 160 GB HDD, so I always have an exact copy in case the drive fails.

I would almost prefer a weekly complete backup, since then, if something goes wrong with the OS I have a backup (but that is another problem).

But if I understand you correctly then the swap of the RAID appears because I have LVM on the OS drive?

---

### Post by Joezorry on 2013-02-08
But I still actually don't get why I can't partion the RAID with the command.

---

### Post by darkod on 2013-02-08
Because you don't partition mdX device. It is designed to be assembled of partitions, so you don't partition it further. You plan the partitions (array) sizes in advance, and when you assemble it it has the size you wanted.

As for the swap, I don't think it's actually on the raid. In fdisk the /dev/mapper/... devices show at the end, if that's confusing you. Also, sda has a gpt table and fdisk doesn't work with gpt.

Try this to list sda and I think you will see LVM member partition on it (flag lvm):
sudo parted /dev/sda unit MiB print

If you look in the fdisk output for sdb, sdc and sdd, there is no LVM partition mentioned so swap can't be there. On those disks you have only Linux raid partitions, which is correct.

EDIT PS: If you want to keep the OS on the 160GB disk, no problem. All you have to do now is plan your raid5 array, and don't forget that mdX devices are not partitioned further, so if you want more than one mdX device (to use with different mount points), you have to create more than one Linux raid partition on sdb, sdc and sdd. After that you assemble (create) the mdX devices, make a filesystem on them and use them with the corresponding mount points.

---

### Post by darkod on 2013-02-08
I'm not at home right now and can't post you the layout of my home server, maybe that will help you a bit. If you are patient for about 4hrs I can do it. :)

---

### Post by Joezorry on 2013-02-08
That actually helped a lot.
I think I messed up the terminology, I always thought you partitioned a RAID, but that's not true, you just make a filesystem on top of them. That makes so much sense.
And the sudo parted /dev/sda unit MiB print command showed me a very crucial point which might hinder my raid to actually create the filesystem.

Model: ATA WDC WD20EFRX-68A (scsi)
Disk /dev/sdc: 1907729MiB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start    End         Size        Type     File system  Flags
 1      1.00MiB  1907729MiB  1907728MiB  primary  fat32        raid

The filesystem on the drive is fat32 which obviously is wrong. And it's fat32 on all the raid HDD:s.
It should be Ext4 since I want to make the filesystem ext4 for the raid.

I have the patience to wait. I probably will have the time to sit and fix the problem on sunday.
But so far it's been very helpful.

---

### Post by darkod on 2013-02-08
Very weird. I wonder if that fat32 is a left over. It shouldn't say ext4, because the filesystem is created on md0, not on sdb1/sdc1/sdd1.

For raid partitions, the parted printed listing should show the number of the partition, start/end/size, primary/logical (for msdos tables) and flags. No filesystem actually. You will also see that in my screenshot later.

Another thought, you can actually use gpt tables on the 2TB disks even though you don't need to. For larger than 2.2GB you have to, but with 2TB you can still do msdos like you have.

But many people say gpt has some advantages. Note that if you do decide to do this, it's best to create small 1MiB partition with NO filesystem (don't format it with anything, that's very important) so that grub2 can use it if you even want to add it on the MBR. This is because on gpt disks the MBR is smaller compared to msdos and grub2 can't fit. That partition needs a flag bios_grub and with that flag grub2 knows to use it, without filesystem.

I usually use parted to create it since parted by default doesn't create a filesystem. On a new disk, making a clan gpt table, you would do for example:
```
sudo parted /dev/sdX #(select the correct disk you want to manipulate)
unit MiB #(change unit to easily create partition of exactly 1MiB)
mklabel gpt #(new blank gpt table)
mkpart GRUB 1 2
set 1 bios_grub on #(set the flag of partition #1 to On)
quit
```

Before exiting parted you can continue doing partitions for the raid, and marking them with the raid flag too.

The syntax of mkpart for gpt tables is:
mkpart <label> <start> <end>

With gpt you have no primary/logical, so instead of specifying the type, you specify label. Using precise start/end you have excellent control where you want partitions created.

Always leave the first 1MiB free (unpartitioned), that's a standard these days.

---

### Post by darkod on 2013-02-08
OK, here it is. I attached two images, first one is parted listing and the second is the fstab.

As you can see, I have two 2TB disks for raid1 and I used gpt table on them (msdos would have worked too for 2TB disks). Since I used gpt and want to have grub2 on the MBRs, as first partition on both disks I created a 1MiB partition with no filesystem and with the bios_grub flag active. Note in the parted listing that sda1 and sdb1 don't have filesystem.

After that, since I wanted 15GiB / partition and the rest for /data, I created 15GiB sda2 and sdb2 partitions with the raid flag (again, no need to create filesystem on them).

The rest of the big space goes to sda3 and sdb3 which will be the big device for /data, except 2GiB at the end for swap.

I decided not to put swap on the array, instead to use the partitions directly, that's why parted shows sda4 and sdb4 as linux-swap filesystem.

If you look at the parted listing for md0 and md1, this is where you can see the ext4 filesystem because /dev/md0 and /dev/md1 are formatted, not sda2, sdb2, etc.

I also posted the fstab so you can see the md0 entry for /, md1 for /data and both swap partitions which are used in paralel.

You need as many physical partitions as you want different mount points. You will have to create separate mdX devices for each mount point.

Another alternative, is to have a single md0 device and use LVM so that you can create several LVs. But as mentioned, LVM will add another layer, and there is really no great benefit.

---

### Post by Joezorry on 2013-02-14
Thank you so much for all the help, and I have everything working now which is awesome.
I did not make it GPT, maybe I will regret it later, but I don't think so, although everything else is up to speed. Thanks once again.

---

### Post by darkod on 2013-02-14
No problem, msdos still works for 2TB. Glad you got it going.

Please support my memebership application, the link is in my signature.

---

