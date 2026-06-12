---
title: "Adding new HDDs to Ubuntu Server"
date: 2015-08-06
forum: Server Platforms
---

### Post by scott.bouch on 2015-08-06
Hi all,

I've given this my best shot with my limited Ubuntu know-how.. and I'm pretty sure I'm close, but need a little help..

I'm adding 2x sata 4TB Western Digital Red drives to my Ubuntu server.

I formatted them using a desktop Ubuntu machine to **ext4** using GParted and a USB adaptor. I've just installed them into my server, and edited **fstab**.

I've already pre-loaded files to them, so would rather not have to reformat again now they are installed... but if it comes to it, then so be it.

I think there is an issue with partition tables, either I've told **fstab** the wrong type of table, or I've formatted them with the wrong type of table, I used **GPT** based on the advice of a website I read for guidance when formatting.

The two new drives appear as **dev/sdc** and **dev/sdd**. I'd have expected them to be sdc1 and sdd1, but the **1**'s are missing.

**fdisk -l** returns this result:

```
scott@6FC:/etc$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c769e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   234440703   116969473    5  Extended
/dev/sda5          501760   234440703   116969472   8e  Linux LVM

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2199.0 GB, 2199023255040 bytes
255 heads, 63 sectors/track, 267349 cylinders, total 4294967295 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 2199.0 GB, 2199023255040 bytes
255 heads, 63 sectors/track, 267349 cylinders, total 4294967295 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d7be2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976773119   488385536   83  Linux

Disk /dev/mapper/6FC--vg-root: 113.3 GB, 113330094080 bytes
255 heads, 63 sectors/track, 13778 cylinders, total 221347840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/6FC--vg-root doesn't contain a valid partition table

Disk /dev/mapper/6FC--vg-swap_1: 6442 MB, 6442450944 bytes
255 heads, 63 sectors/track, 783 cylinders, total 12582912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/6FC--vg-swap_1 doesn't contain a valid partition table
scott@6FC:/etc$ 


```

My **fstab** looks like this, I'm trying to mount one drive in /media/family, and the other in /media/media. I just copied the formatting of the line above for sdb1 as that drive works, I dont know what defaults and 0 or 2 mean.

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/6FC--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=442ef4fd-bc9b-4e17-825e-27f5e7a1414d /boot           ext2    defaults        0       2
#/dev/mapper/6FC--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/sdb1/    /media/storage    ext4    defaults    0    2
[B]/dev/sdc/    /media/family    ext4    defaults    0    2
/dev/sdd/    /media/media    ext4    defaults    0    2[/B]
/media/storage/images /usr/share/zoneminder/images none defaults,bind 0 2
/media/storage/events /usr/share/zoneminder/events none defaults,bind 0 2
//192.168.1.75/volume_1 /mnt/nas cifs guest,uid=1000,iocharset=utf8    0    0
```

Above, I&#8217;ve highlighted my attempts at changing fstab..

**mount -a** returns this result:

```
scott@6FC:/etc$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdd,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

scott@6FC:/etc$ 


```

Many thanks for any tips as to what I've done wrong, Scott

---

### Post by TheFu on 2015-08-06
sda .... sdz are disks.
sda1.....99 are partitions.

GPT is applied to the "disk".  Then partitions are created.  parted or gparted are used for this part.

mkfs is applied to the "partition."  gparted can do this, if you elect NOT to use LVM.  On a server, using LVM is much, much, much more flexible.  LVM has pv, vg, and lv parts.  LVs relate to "partitions".

So - that error make me think you didn't create the file system on sdX1 .... Did you?

Remember, that Linux/Unix will let an administrator do whatever they say, even if it is wrong.  Could it be that you put the file system onto the disk without the partitioning?

Also - mounting things under /media is a really bad idea. That is where the OS puts things that are automatically mounted. For mounts that you cause, it is smarter to put those ****anywhere** except /media.**

These lines all look wrong to me.
```

/dev/sdb1/    /media/storage    ext4    defaults    0    2
/dev/sdc/    /media/family    ext4    defaults    0    2
/dev/sdd/    /media/media    ext4    defaults    0    2
```

Can't fix sdc or sdd - but perhaps you should use UUIDs - device names like sda, sdb, sdc .... change from time to time. That is why we use UUIDs and LABELs these days inside our fstabs.
```

/dev/sdb1   /media/storage    ext4    defaults    0    2
```
Notice how I removed the trailing slash.  I would also create the mount point (that is just an empty directory) somewhere outside /media.

Use the **sudo blkid** command to get the UUID for each partition/device.  [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID) has more details.

---

### Post by bab1 on 2015-08-06
> **scott.bouch said:**
> Hi all,

I've given this my best shot with my limited Ubuntu know-how.. and I'm pretty sure I'm close, but need a little help..

I'm adding 2x sata 4TB Western Digital Red drives to my Ubuntu server.

I formatted them using a desktop Ubuntu machine to **ext4** using GParted and a USB adaptor. I've just installed them into my server, and edited **fstab**.

I've already pre-loaded files to them, so would rather not have to reformat again now they are installed... but if it comes to it, then so be it.

I think there is an issue with partition tables, either I've told **fstab** the wrong type of table, or I've formatted them with the wrong type of table, I used **GPT** based on the advice of a website I read for guidance when formatting.

The two new drives appear as **dev/sdc** and **dev/sdd**. I'd have expected them to be sdc1 and sdd1, but the **1**'s are missing.

**fdisk -l** returns this result:

```
scott@6FC:/etc$ sudo fdisk -l
**[COLOR="#FF0000"]WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.[/COLOR]**

Disk /dev/sdc: 2199.0 GB, 2199023255040 bytes
255 heads, 63 sectors/track, 267349 cylinders, total 4294967295 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
[COLOR="#0000FF"][B]/dev/sdc1               1  4294967295  2147483647+  ee  GPT
[/B][/COLOR]

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdd: 2199.0 GB, 2199023255040 bytes
255 heads, 63 sectors/track, 267349 cylinders, total 4294967295 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
[COLOR="#0000FF"][B]/dev/sdd1               1  4294967295  2147483647+  ee  GPT
[/B][/COLOR]


```

You shouldn't use fdisk on partitions larger then 2TB (see the warnings in red).  The proper tool is ***parted *** from the CLI or ***gparted*** with the GUI.  None the less the partitions you formatted are there in blue.
> 

```
# /etc/fstab: static file system information.
#
[COLOR="#FF0000"][B]# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).[/B][/COLOR]
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/6FC--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=442ef4fd-bc9b-4e17-825e-27f5e7a1414d /boot           ext2    defaults        0       2
#/dev/mapper/6FC--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/sdb1/    /media/storage    ext4    defaults    0    2
[B]/dev/sdc/    /media/family    ext4    defaults    0    2
/dev/sdd/    /media/media    ext4    defaults    0    2[/B]
/media/storage/images /usr/share/zoneminder/images none defaults,bind 0 2
/media/storage/events /usr/share/zoneminder/events none defaults,bind 0 2
//192.168.1.75/volume_1 /mnt/nas cifs guest,uid=1000,iocharset=utf8    0    0
```
My (above) **fstab** looks like this, I'm trying to mount one drive in /media/family, and the other in /media/media. I just copied the formatting of the line above for sdb1 as that drive works, I dont know what defaults and 0 or 2 mean.
Above, I&#8217;ve highlighted my attempts at changing fstab.
You should follow the advice above (in red) and use the UUID to mount sdb1, sdc1 and sdd1.  This means you need to find what the are the UUID's Post the output of this command from the CLI so we can advise you specifically```
sudo blkid -c /dev/null -o list
```
The proper format for the fstab file should be```
UUID=<some long number> <mountpoint> <file system type> <dump?> <fsck?>
```

All of the *fields * used in the fstab are explained in the man pages```
man fstab
```
The number two means that this is a partition that should be checked with fsck after the root file system is checked.

---

### Post by scott.bouch on 2015-08-07
Thank you guys for all your help, It's a big learning curve!

Ok, so **blkid** returned this result, the two new drives don't appear:

```
scott@6FC:~$ sudo blkid -c /dev/null -o list
[sudo] password for scott: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
device                          fs_type      label         mount point                         UUID
-----------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                       ext2                       /boot                               442ef4fd-bc9b-4e17-825e-27f5e7a1414d
/dev/sda5                       LVM2_member                (in use)                            cP6I40-148L-tXrh-w2bm-R1UT-YqLb-OZMHNQ
/dev/sdb1                       ext4         Storage       /media/storage                      1ecfb548-c745-49f5-b143-37965eea3fe9
/dev/mapper/6FC--vg-root        ext4                       /                                   7e34d6d4-0fa1-4ce3-9964-9e61b61fe322
scott@6FC:~$
```

I can see the logic in using the UUID instead of sd**xx** for mounting, as I guess the UUID is the physical drive serial number, or generated from it?

Also, now you mention it, I added a partition table when I formatted them, but forgot to add a partition... oops.. I didn't notice, as my desktop machine just treated it as a removable USB drive, and allowed me to add files. Root did claim ownership, which I had to adjust to me to allow the saving of files.

Is there an easy way to create a partition, and move my data into it? Or am I best to just start all over again?

Once sorted, I'll try mounting to my **mnt** directory instead of **media**, and also will use UUID's instead. I may also move the storage directory to **mnt** too (and use UUID), as I put that in **media** about a year ago. This is what  I get for "just having a go" - but you've got to learn somehow!

A project for this weekend...

Many thanks, Scott.

---

### Post by TheFu on 2015-08-07
UUID is connected to partitions or LVs (logical volumes) too.  

Remember when I said that Unix lets you do what you want, even when it is not normal?  You've seen that.  For disks in a RAID set, it is common not to bother with partitioning.

Root always gets ownership of new partitions, new file systems. That is normal.

I would start over. Also, since you are already using LVM, you might want to add these new disks to the existing VG.  It really comes down to how you backup the new storage.  I like to limit my partition sizes to whatever my backup storage can handle.  With LVM, I only expand available storage when needed.

A little history of mount points:
* /media is used by the OS for automatic mounting of external storage
* /mnt is used by root for temporary storage - basically a place to connect partitions before they are ready for public use
* /export is used for NFS mounts in many organizations - /export/home is commonly used for HOMEs that are available across many different systems. Each userid has 1 HOME, but it is mounted on every system they have a login on.

You can mount new partitions/LVs anywhere, onto any directory.  Why not take advantage of that? Of course, you can mount storage on directory structures that are full too - most people thing of this as a mistake because any files below that point cannot be accessed anymore, but it does work.  I use /D/.... as a place to add extra static storage and /misc/... for automounted, on-demand, storage (like for media files).

You should do what makes sense for you. Don't worry about the way I do it or anyone else does it, provided you have a reason for doing it the way you decide and it doesn't conflict with other parts of the system.

---

### Post by scott.bouch on 2015-08-07
Hi TheFu,

Thanks for your kind words on the matter..

I'm intent on keeping these as two separate 4TB drives, one for family stuff (photo albums, etc..), the other for media (music / films etc,..) not raiding them togehter..

However, this does bring me to another point... I'll have a NAS box (2 bay of max 2TB each) which I intend to use to take nightly backups of the family drive. If I configure it in raid 0 to make 4TB, this will be adequate for my family drive backups using one of the utilities listed here: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) - Do you have any advice on achieving this?

I have two reasons for wanting to use the NAS as a backup of the family stuff, rather than raid 1-ing the two new drives:

- I can keep it in a separate location to the server so that there's more chance of recovering data after a house fire / flood.
- I'd rather not have the NAS running all the time, to save power, and prolong the life of the drives... the NAS has as setting to go into standby mode a few minutes after the last use.

I'll get the drives out of the server tonight and re-format them. I'll make sure I can mount them properly first this time before filling them with data!

If I can mount them anywhere, I think I'll just place them (all three) in the root directory as /family, /media and /storage (renamed to cctv) reason being to just keep life simple. unless there is an issue with creating folders in the root directory?

Thanks, Scott.

---

### Post by TheFu on 2015-08-07
You can't use /media. That is already taken and a "special directory" as discussed above.

Do not use RAID0.  That is a fast way to lost all the data on both disks.  RAID0 should be used only by people with extreme performance needs for temporary storage only.  Think video editors. Most of those guys have switched to SSDs and run those in RAID0 to get even more performance for the file they are actively working on.  For you and I with spinning disks, RAID0 is a bad idea. If 1 disk in the set fails - all the data is gone on both. Sweet! NOT!

Rather than RAID, LVM is a viable alternative to merge disks - just be certain that you can backup at the partition level. That is key.

Power needs for a NAS are minimal. Spinning down and up the disk will cause more wear and tear on the drives than anything else.  Those RED drives are designed to spin 24/7/365 for 5+ yrs.  Let them do that.  Watch the temperatures so they don't over heat. The only drives that I allow to spin down are in a laptop. You can control spin down settings with hdparm.

Backups ... I've answered that question 20 times in these forums. Search a little.  i find the suggestions on that linked page to be simplistic and next to useless. Sorry.  I use **rsync** for media backups (as needed, usually weekly) and **rdiff-backup** for all others which happen nightly, automatically.

Of course there are other opinions about this stuff. I just know what works for me and that with 6 systems running 24/7 here the last 15 yrs, our power bill hasn't changed much.  I have been actively retiring 125W systems for 45W systems the last few years and never had a 165W AMD monster.  Down to 2 power sucking systems, but those run 10+ VMs each. Most of the time, they use less even with 6 disks and the connected external disk arrays.

---

### Post by scott.bouch on 2015-08-07
Oh, sorry, thanks for pointing out about /media... I'll think of a batter name.

Here is my idea on the backups.. I find it much easier to share ideas like this using a diagram, saves ideas getting mixed up.

I'm only concerned with backing up the Family drive... media, and operating system can be replaced easily. CCTV footage of next doors cat is no great loss either.

[ATTACH=CONFIG]263710[/ATTACH]

Main reason to have the NAS drives in RAID 0 is to make it up to 4TB to match the family drive capacity.. The box is limited to 2x 2TB.

Interesting to learn that the drives fail quicker due to cycles, so I'd have more reliability if I didn't use power-saving on the NAS and kept the disks spinning.

Thanks, Scott.

---

### Post by TheFu on 2015-08-07
Split the 4TB drive in half match your backup storage. 

DO NOT USE RAID0.  

There are many ways you can "merge" data on multiple partitions, when you get there. Or you can just use symlinks.  The key is to have a way to backup your data and not get screwed over something foolish like RAID0.

---

### Post by scott.bouch on 2015-08-07
Or idea #2 would suit the NAS drives being always on..

[ATTACH=CONFIG]263711[/ATTACH]

- NAS drives in raid 0 to make single 4TB volume.
- Family drive of server, and NAS volume in raid 1 together, if possible to raid over a network.

If a house fire takes out either the server or the NAS, our family photos are safe.

Cheers, Scott

Ok, back to the drive issue..

I've just formatted the family drive again, (last time I did actually create a partition on it, but reformatted it anyway). I formatted it on my desktop machine, and found out it's UUID.

I've now put it back in the server, edited **fstab** to use the UUID instead, and mount it to newly created directory /family:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/6FC--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=442ef4fd-bc9b-4e17-825e-27f5e7a1414d /boot           ext2    defaults        0       2
#/dev/mapper/6FC--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/sdb1/      /media/storage  ext4    defaults        0       2
UUID=ee009e34-d4b6-4c80-b129-af727c607e5b       /family ext4    defaults        0       2

/media/storage/images /usr/share/zoneminder/images none defaults,bind 0 2
/media/storage/events /usr/share/zoneminder/events none defaults,bind 0 2
//192.168.1.75/volume_1 /mnt/nas cifs guest,uid=1000,iocharset=utf8     0       0

```


Running **mount -a** returns:
```
scott@6FC:/$ sudo mount -a
mount: special device UUID=ee009e34-d4b6-4c80-b129-af727c607e5b does not exist

```


So then checking with **blkid** does not show the drives UUID at all:
```
scott@6FC:/$ sudo blkid -c /dev/null -o list
device                          fs_type      label         mount point                         UUID
-----------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                       ext2                       /boot                               442ef4fd-bc9b-4e17-825e-27f5e7a1414d
/dev/sda5                       LVM2_member                (in use)                            cP6I40-148L-tXrh-w2bm-R1UT-YqLb-OZMHNQ
/dev/sdb1                       ext4         Storage       /media/storage                      1ecfb548-c745-49f5-b143-37965eea3fe9
/dev/mapper/6FC--vg-root        ext4                       /                                   7e34d6d4-0fa1-4ce3-9964-9e61b61fe322

```

Cheers, Scott.

---

### Post by bab1 on 2015-08-07
Are you formatting the partition (the HDD) on one machine and then moving it to another machine?  If so,  are you sure it is connected to a known good port?

---

### Post by TheFu on 2015-08-07
Sounds like the disk controller or USB ports aren't working with Ubuntu.
Check **dmesg** output to see is the controller is known.
[B]
sudo lshw -C storage[/B] will show which controllers are known and which drivers they are using, if any.

---

### Post by scott.bouch on 2015-08-07
Hi both[B],

[/B]Thank you - I hope that the server is capable of using all four drive ports... would this be a bios config perhaps? It's a DELL CS24-SC server computer.

Yes, I got the UUID from plugging it into another computer, the desktop machine that I formatted it with.
[B]
dmesg[/B] output:

```
[    0.324798] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.324801] system 00:09: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.324805] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.324876] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.324977] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.324982] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.324986] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.325044] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.325049] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.325218] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.325223] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.325227] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.325230] system 00:0d: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.325235] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.325350] pnp: PnP ACPI: found 14 devices
[    0.325353] ACPI: bus type PNP unregistered
[    0.332977] pci 0000:00:04.0: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.332980] pci 0000:00:04.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.332983] pci 0000:00:04.0: bridge window [mem 0x00100000-0x000fffff] to [bus 03] add_size 200000
[    0.333002] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 07] add_size 200000
[    0.333010] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 08] add_size 200000
[    0.333021] pci 0000:00:1f.0: BAR 13: [io  0x0800-0x087f] has bogus alignment
[    0.333026] pci 0000:00:04.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.333029] pci 0000:00:04.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.333031] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.333034] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.333036] pci 0000:00:04.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.333041] pci 0000:00:04.0: BAR 14: assigned [mem 0xc0000000-0xc01fffff]
[    0.333045] pci 0000:00:04.0: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.333050] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.333054] pci 0000:00:1c.4: BAR 15: assigned [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.333058] pci 0000:00:04.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.333063] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.333072] pci 0000:00:03.0: PCI bridge to [bus 02]
[    0.333079] pci 0000:00:04.0: PCI bridge to [bus 03]
[    0.333083] pci 0000:00:04.0:   bridge window [io  0x1000-0x1fff]
[    0.333088] pci 0000:00:04.0:   bridge window [mem 0xc0000000-0xc01fffff]
[    0.333092] pci 0000:00:04.0:   bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.333098] pci 0000:00:05.0: PCI bridge to [bus 04]
[    0.333106] pci 0000:00:06.0: PCI bridge to [bus 05]
[    0.333114] pci 0000:00:07.0: PCI bridge to [bus 06]
[    0.333121] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    0.333125] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.333131] pci 0000:00:1c.0:   bridge window [mem 0xdf200000-0xdf5fffff]
[    0.333136] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.333143] pci 0000:00:1c.4: PCI bridge to [bus 08]
[    0.333146] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.333152] pci 0000:00:1c.4:   bridge window [mem 0xdf600000-0xdf6fffff]
[    0.333157] pci 0000:00:1c.4:   bridge window [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.333164] pci 0000:00:1e.0: PCI bridge to [bus 09]
[    0.333168] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.333173] pci 0000:00:1e.0:   bridge window [mem 0xdf700000-0xdfffffff]
[    0.333182] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.333184] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.333186] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.333188] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.333191] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.333193] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xffffffff]
[    0.333195] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.333197] pci_bus 0000:03: resource 1 [mem 0xc0000000-0xc01fffff]
[    0.333199] pci_bus 0000:03: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.333202] pci_bus 0000:07: resource 0 [io  0xc000-0xcfff]
[    0.333204] pci_bus 0000:07: resource 1 [mem 0xdf200000-0xdf5fffff]
[    0.333206] pci_bus 0000:07: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[    0.333209] pci_bus 0000:08: resource 0 [io  0xd000-0xdfff]
[    0.333211] pci_bus 0000:08: resource 1 [mem 0xdf600000-0xdf6fffff]
[    0.333213] pci_bus 0000:08: resource 2 [mem 0xc0600000-0xc07fffff 64bit pref]
[    0.333215] pci_bus 0000:09: resource 0 [io  0xe000-0xefff]
[    0.333217] pci_bus 0000:09: resource 1 [mem 0xdf700000-0xdfffffff]
[    0.333219] pci_bus 0000:09: resource 4 [io  0x0000-0x0cf7]
[    0.333221] pci_bus 0000:09: resource 5 [io  0x0d00-0xffff]
[    0.333223] pci_bus 0000:09: resource 6 [mem 0x000a0000-0x000bffff]
[    0.333226] pci_bus 0000:09: resource 7 [mem 0x000d0000-0x000dffff]
[    0.333228] pci_bus 0000:09: resource 8 [mem 0xc0000000-0xdfffffff]
[    0.333230] pci_bus 0000:09: resource 9 [mem 0xf0000000-0xffffffff]
[    0.333266] NET: Registered protocol family 2
[    0.333526] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.333809] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.334200] TCP: Hash tables configured (established 65536 bind 65536)
[    0.334253] TCP: reno registered
[    0.334268] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.334333] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.334459] NET: Registered protocol family 1
[    0.335581] pci 0000:09:03.0: Video device with shadowed ROM
[    0.335584] PCI: CLS 64 bytes, default 64
[    0.335658] Trying to unpack rootfs image as initramfs...
[    0.792190] Freeing initrd memory: 24096K (ffff8800350e0000 - ffff880036868000)
[    0.792204] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.792208] software IO TLB [mem 0xbbfa0000-0xbffa0000] (64MB) mapped at [ffff8800bbfa0000-ffff8800bff9ffff]
[    0.792614] microcode: CPU0 sig=0x10676, pf=0x40, revision=0x60c
[    0.792626] microcode: CPU1 sig=0x10676, pf=0x40, revision=0x60c
[    0.792646] microcode: CPU2 sig=0x10676, pf=0x40, revision=0x60c
[    0.792663] microcode: CPU3 sig=0x10676, pf=0x40, revision=0x60c
[    0.792687] microcode: CPU4 sig=0x10676, pf=0x40, revision=0x60c
[    0.792718] microcode: CPU5 sig=0x10676, pf=0x40, revision=0x60c
[    0.792766] microcode: CPU6 sig=0x10676, pf=0x40, revision=0x60c
[    0.792788] microcode: CPU7 sig=0x10676, pf=0x40, revision=0x60c
[    0.792877] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.792889] Scanning for low memory corruption every 60 seconds
[    0.793224] Initialise system trusted keyring
[    0.793291] audit: initializing netlink socket (disabled)
[    0.793308] type=2000 audit(1438967534.792:1): initialized
[    0.824516] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.826052] zbud: loaded
[    0.826226] VFS: Disk quotas dquot_6.5.2
[    0.826288] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.826836] fuse init (API version 7.22)
[    0.826946] msgmni has been set to 11931
[    0.827024] Key type big_key registered
[    0.827688] Key type asymmetric registered
[    0.827692] Asymmetric key parser 'x509' registered
[    0.827733] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.827796] io scheduler noop registered
[    0.827800] io scheduler deadline registered (default)
[    0.827840] io scheduler cfq registered
[    0.828012] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.828081] pcieport 0000:00:03.0: irq 41 for MSI/MSI-X
[    0.828133] pcieport 0000:00:04.0: enabling device (0144 -> 0147)
[    0.828153] pcieport 0000:00:04.0: irq 42 for MSI/MSI-X
[    0.828227] pcieport 0000:00:05.0: irq 43 for MSI/MSI-X
[    0.828291] pcieport 0000:00:06.0: irq 44 for MSI/MSI-X
[    0.828358] pcieport 0000:00:07.0: irq 45 for MSI/MSI-X
[    0.828565] pcieport 0000:00:1c.0: irq 46 for MSI/MSI-X
[    0.828741] pcieport 0000:00:1c.4: irq 47 for MSI/MSI-X
[    0.828846] aer 0000:00:02.0:pcie02: service driver aer loaded
[    0.828866] aer 0000:00:03.0:pcie02: service driver aer loaded
[    0.828887] aer 0000:00:04.0:pcie02: service driver aer loaded
[    0.828907] aer 0000:00:05.0:pcie02: service driver aer loaded
[    0.828925] aer 0000:00:06.0:pcie02: service driver aer loaded
[    0.828950] aer 0000:00:07.0:pcie02: service driver aer loaded
[    0.828964] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
[    0.828970] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
[    0.828978] pcieport 0000:00:03.0: Signaling PME through PCIe PME interrupt
[    0.828982] pcie_pme 0000:00:03.0:pcie01: service driver pcie_pme loaded
[    0.828990] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
[    0.828995] pcie_pme 0000:00:04.0:pcie01: service driver pcie_pme loaded
[    0.829003] pcieport 0000:00:05.0: Signaling PME through PCIe PME interrupt
[    0.829007] pcie_pme 0000:00:05.0:pcie01: service driver pcie_pme loaded
[    0.829015] pcieport 0000:00:06.0: Signaling PME through PCIe PME interrupt
[    0.829020] pcie_pme 0000:00:06.0:pcie01: service driver pcie_pme loaded
[    0.829031] pcieport 0000:00:07.0: Signaling PME through PCIe PME interrupt
[    0.829035] pcie_pme 0000:00:07.0:pcie01: service driver pcie_pme loaded
[    0.829056] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.829060] pci 0000:07:00.0: Signaling PME through PCIe PME interrupt
[    0.829065] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.829085] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    0.829089] pci 0000:08:00.0: Signaling PME through PCIe PME interrupt
[    0.829094] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    0.829109] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.792021] tsc: Refined TSC clocksource calibration: 2333.415 MHz
[    2.428014] pciehp 0000:00:04.0:pcie04: HPC vendor_id 8086 device_id 65fa ss_vid 0 ss_did 0
[    2.792147] Switched to clocksource tsc
[    3.428016] pciehp 0000:00:04.0:pcie04: service driver pciehp loaded
[    3.428032] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 2940 ss_vid 8086 ss_did 2940
[    3.428085] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    3.428098] pciehp 0000:00:1c.4:pcie04: HPC vendor_id 8086 device_id 2948 ss_vid 8086 ss_did 2948
[    3.428160] pciehp 0000:00:1c.4:pcie04: service driver pciehp loaded
[    3.428181] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.428232] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    3.428235] vesafb: scrolling: redraw
[    3.428238] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    3.428634] vesafb: framebuffer at 0xdf800000, mapped to 0xffffc90010e80000, using 5120k, total 5120k
[    3.704336] Console: switching to colour frame buffer device 160x64
[    3.981915] fb0: VESA VGA frame buffer device
[    3.983286] intel_idle: does not run on family 6 model 23
[    3.983296] ipmi message handler version 39.2
[    3.984730] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    3.987266] ACPI: Sleep Button [SLPB]
[    3.988436] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    3.990967] ACPI: Power Button [PWRB]
[    3.992134] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    3.994423] ACPI: Power Button [PWRF]
[    4.000087] GHES: HEST is not enabled!
[    4.001332] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    4.023992] 00:05: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    4.046945] 00:06: ttyS1 at I/O 0x2f8 (irq = 3, base_baud = 115200) is a 16550A
[    4.050561] Linux agpgart interface v0.103
[    4.053316] brd: module loaded
[    4.055023] loop: module loaded
[    4.056148] ata_piix 0000:00:1f.2: version 2.13
[    4.056250] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    4.058691] scsi0 : ata_piix
[    4.059663] scsi1 : ata_piix
[    4.060600] ata1: SATA max UDMA/133 cmd 0xb080 ctl 0xb000 bmdma 0xa800 irq 19
[    4.062810] ata2: SATA max UDMA/133 cmd 0xac00 ctl 0xa880 bmdma 0xa808 irq 19
[    4.065337] libphy: Fixed MDIO Bus: probed
[    4.066699] tun: Universal TUN/TAP device driver, 1.6
[    4.068263] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.070210] PPP generic driver version 2.4.2
[    4.071571] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.073597] ehci-pci: EHCI PCI platform driver
[    4.075090] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    4.076713] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.079013] ehci-pci 0000:00:1a.7: debug port 1
[    4.084308] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    4.084323] ehci-pci 0000:00:1a.7: irq 21, io mem 0xdf1dec00
[    4.096013] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.097840] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    4.099941] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.102177] usb usb1: Product: EHCI Host Controller
[    4.103685] usb usb1: Manufacturer: Linux 3.13.0-43-generic ehci_hcd
[    4.105650] usb usb1: SerialNumber: 0000:00:1a.7
[    4.107185] hub 1-0:1.0: USB hub found
[    4.108355] hub 1-0:1.0: 2 ports detected
[    4.109778] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    4.194626] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.281287] ehci-pci 0000:00:1d.7: debug port 1
[    4.372028] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    4.372043] ehci-pci 0000:00:1d.7: irq 23, io mem 0xdf1de800
[    4.468011] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.556610] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    4.647090] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.715724] ata1.00: SATA link down (SStatus 0 SControl 300)
[    4.715749] ata1.01: SATA link down (SStatus 0 SControl 300)
[    4.727382] ata2.00: SATA link down (SStatus 0 SControl 300)
[    4.727407] ata2.01: SATA link down (SStatus 0 SControl 300)
[    5.090693] usb usb2: Product: EHCI Host Controller
[    5.176226] usb usb2: Manufacturer: Linux 3.13.0-43-generic ehci_hcd
[    5.261651] usb usb2: SerialNumber: 0000:00:1d.7
[    5.346876] hub 2-0:1.0: USB hub found
[    5.431048] hub 2-0:1.0: 6 ports detected
[    5.514062] ehci-platform: EHCI generic platform driver
[    5.596621] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.678931] ohci-pci: OHCI PCI platform driver
[    5.760315] ohci-platform: OHCI generic platform driver
[    5.841478] uhci_hcd: USB Universal Host Controller Interface driver
[    5.923392] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    6.005195] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    6.087390] uhci_hcd 0000:00:1a.0: irq 23, io base 0x0000b880
[    6.168292] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    6.249500] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    6.330552] usb usb3: Product: UHCI Host Controller
[    6.330554] usb usb3: Manufacturer: Linux 3.13.0-43-generic uhci_hcd
[    6.330555] usb usb3: SerialNumber: 0000:00:1a.0
[    6.411669] hub 3-0:1.0: USB hub found
[    6.411676] hub 3-0:1.0: 2 ports detected
[    6.411859] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    6.411864] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    6.411895] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b800
[    6.411944] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    6.411945] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    6.411947] usb usb4: Product: UHCI Host Controller
[    6.411948] usb usb4: Manufacturer: Linux 3.13.0-43-generic uhci_hcd
[    6.411950] usb usb4: SerialNumber: 0000:00:1d.0
[    6.412055] hub 4-0:1.0: USB hub found
[    6.412061] hub 4-0:1.0: 2 ports detected
[    6.412253] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    6.412258] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    6.412301] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000b480
[    6.412349] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    6.412351] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    6.412352] usb usb5: Product: UHCI Host Controller
[    6.412353] usb usb5: Manufacturer: Linux 3.13.0-43-generic uhci_hcd
[    6.412355] usb usb5: SerialNumber: 0000:00:1d.1
[    6.412452] hub 5-0:1.0: USB hub found
[    6.412458] hub 5-0:1.0: 2 ports detected
[    6.412667] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    6.412672] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    6.412703] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000b400
[    6.412753] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    6.412755] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    6.412756] usb usb6: Product: UHCI Host Controller
[    6.412757] usb usb6: Manufacturer: Linux 3.13.0-43-generic uhci_hcd
[    6.412759] usb usb6: SerialNumber: 0000:00:1d.2
[    6.412850] hub 6-0:1.0: USB hub found
[    6.412859] hub 6-0:1.0: 2 ports detected
[    6.413001] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    6.416104] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.416117] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.416284] mousedev: PS/2 mouse device common for all mice
[    6.416540] rtc_cmos 00:02: RTC can wake from S4
[    6.416733] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    6.416773] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    6.416879] device-mapper: uevent: version 1.0.3
[    6.416973] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    6.416982] ledtrig-cpu: registered to indicate activity on CPUs
[    6.417132] TCP: cubic registered
[    6.417236] NET: Registered protocol family 10
[    6.417446] NET: Registered protocol family 17
[    6.417460] Key type dns_resolver registered
[    6.417861] Loading compiled-in X.509 certificates
[    6.419004] Loaded X.509 cert 'Magrathea: Glacier signing key: 55ab2fe28ed5c60df9587150d1734c920ea7b818'
[    6.419019] registered taskstats version 1
[    6.421580] Key type trusted registered
[    6.423387] Key type encrypted registered
[    6.425194] AppArmor: AppArmor sha1 policy hashing enabled
[    6.425196] IMA: No TPM chip found, activating TPM-bypass!
[    6.425655] regulator-dummy: disabling
[    6.425730]   Magic number: 11:508:238
[    6.492281] rtc_cmos 00:02: setting system clock to 2015-08-07 17:12:21 UTC (1438967541)
[    6.572270] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.572270] EDD information not available.
[    6.572297] PM: Hibernation image not present or could not be loaded.
[    6.724012] usb 3-1: new low-speed USB device number 2 using uhci_hcd
[    7.037305] usb 3-1: New USB device found, idVendor=0b38, idProduct=0003
[    7.037307] usb 3-1: New USB device strings: Mfr=4, Product=20, SerialNumber=68
[    7.037309] usb 3-1: Product: USB MULTIMEDIA KEYBOARD
[    7.037311] usb 3-1: Manufacturer: VIRTUAL
[    7.037312] usb 3-1: SerialNumber: 20050606
[    7.152025] usb 4-2: new full-speed USB device number 2 using uhci_hcd
[    7.411947] usb 4-2: New USB device found, idVendor=413c, idProduct=1003
[    7.411949] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    7.411951] usb 4-2: Product: Dell USB Keyboard Hub
[    7.411953] usb 4-2: Manufacturer: Dell
[    7.481976] hub 4-2:1.0: USB hub found
[    7.482956] hub 4-2:1.0: 3 ports detected
[    7.897955] usb 4-2.1: new full-speed USB device number 3 using uhci_hcd
[    8.176949] usb 4-2.1: New USB device found, idVendor=413c, idProduct=2010
[    8.176951] usb 4-2.1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[    8.176953] usb 4-2.1: Product: Dell USB Keyboard
[    8.176954] usb 4-2.1: Manufacturer: Dell
[   12.480087] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[   12.562147] Write protecting the kernel read-only data: 12288k
[   12.646969] Freeing unused kernel memory: 796K (ffff880001739000 - ffff880001800000)
[   12.732276] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[   12.913922] systemd-udevd[153]: starting version 204
[   13.020729] pps_core: LinuxPPS API ver. 1 registered
[   13.050290] FDC 0 is a post-1991 82077
[   13.185510] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[   13.271503] hidraw: raw HID events driver (C) Jiri Kosina
[   13.271511] [drm] Initialized drm 1.1.0 20060810
[   13.443413] PTP clock support registered
[   13.528923] Fusion MPT base driver 3.04.20
[   13.613730] Copyright (c) 1999-2008 LSI Corporation
[   13.698859] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[   13.784202] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[   13.786500] usbcore: registered new interface driver usbhid
[   13.786501] usbhid: USB HID core driver
[   14.040848] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[   14.129801] e1000e 0000:00:19.0: irq 48 for MSI/MSI-X
[   14.130176] input: VIRTUAL USB MULTIMEDIA KEYBOARD as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input6
[   14.221106] Fusion MPT SAS Host driver 3.04.20
[   14.221183] hid-generic 0003:0B38:0003.0001: input,hidraw0: USB HID v1.10 Keyboard [VIRTUAL USB MULTIMEDIA KEYBOARD] on usb-0000:00:1a.0-1/input0
[   14.221414] input: VIRTUAL USB MULTIMEDIA KEYBOARD as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input7
[   14.221527] hid-generic 0003:0B38:0003.0002: input,hidraw1: USB HID v1.10 Mouse [VIRTUAL USB MULTIMEDIA KEYBOARD] on usb-0000:00:1a.0-1/input1
[   14.221780] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb4/4-2/4-2.1/4-2.1:1.0/input/input8
[   14.221849] hid-generic 0003:413C:2010.0003: input,hidraw2: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-2.1/input0
[   14.225046] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb4/4-2/4-2.1/4-2.1:1.1/input/input9
[   14.225179] hid-generic 0003:413C:2010.0004: input,hidraw3: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:1d.0-2.1/input1
[   14.434181] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:23:8b:8a:93:1d
[   14.434183] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[   14.434220] e1000e 0000:00:19.0 eth0: MAC: 7, PHY: 6, PBA No: FFFFFF-0FF
[   14.434407] e1000e 0000:08:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[   14.434444] e1000e 0000:08:00.0: irq 49 for MSI/MSI-X
[   14.556623] e1000e 0000:08:00.0 eth1: (PCI Express:2.5GT/s:Width x1) 00:23:8b:8a:93:1e
[   14.556625] e1000e 0000:08:00.0 eth1: Intel(R) PRO/1000 Network Connection
[   14.556804] e1000e 0000:08:00.0 eth1: MAC: 2, PHY: 2, PBA No: FFFFFF-0FF
[   15.788645] mptbase: ioc0: Initiating bringup
[   15.899357] [drm] AST 2000 detected
[   16.007179] [drm] dram 664000000 2 32 00800000
[   16.115692] [TTM] Zone  kernel: Available graphics memory: 3055810 kiB
[   16.225046] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   16.333664] [TTM] Initializing pool allocator
[   16.441830] [TTM] Initializing DMA pool allocator
[   16.616862] checking generic (df800000 500000) vs hw (df800000 800000)
[   16.616865] fb: conflicting fb hw usage astdrmfb vs VESA VGA - removing generic driver
[   16.725869] Console: switching to colour dummy device 80x25
[   16.726019] fbcon: astdrmfb (fb0) is primary device
[   16.808038] ioc0: LSISAS1064E B1: Capabilities={Initiator}
[   16.818107] Console: switching to colour frame buffer device 160x64
[   16.916787] ast 0000:09:03.0: fb0: astdrmfb frame buffer device
[   16.916815] ast 0000:09:03.0: registered panic notifier
[   16.916842] [drm] Initialized ast 0.1.0 20120228 for 0000:09:03.0 on minor 0
[   19.675232] scsi2 : ioc0: LSISAS1064E B1, FwRev=01140000h, Ports=1, MaxQ=511, IRQ=16
[   19.696629] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 0, phy 0, sas_addr 0x1221000000000000
[   19.699616] scsi 2:0:0:0: Direct-Access     ATA      Samsung SSD 840  BB6Q PQ: 0 ANSI: 5
[   19.701207] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   19.701937] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[   19.702522] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 1, phy 1, sas_addr 0x1221000001000000
[   19.705087] scsi 2:0:1:0: Direct-Access     ATA      ST3500312CS      SC13 PQ: 0 ANSI: 5
[   19.706714] sd 2:0:1:0: Attached scsi generic sg1 type 0
[   19.707977] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 2, phy 2, sas_addr 0x1221000002000000
[   19.708072] sd 2:0:1:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[   19.708286] sd 2:0:0:0: [sda] Write Protect is off
[   19.708323] sd 2:0:0:0: [sda] Mode Sense: 73 00 00 08
[   19.709570] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.710064] scsi 2:0:2:0: Direct-Access     ATA      WDC WD40EFRX-68W 0A82 PQ: 0 ANSI: 5
[   19.711770] sd 2:0:2:0: Attached scsi generic sg2 type 0
[   19.713472] sd 2:0:2:0: [sdc] 4294967295 512-byte logical blocks: (2.19 TB/1.99 TiB)
[   19.718518] sd 2:0:2:0: [sdc] Write Protect is off
[   19.718548] sd 2:0:2:0: [sdc] Mode Sense: 73 00 00 08
[   19.720085] sd 2:0:2:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.721770]  sda: sda1 sda2 < sda5 >
[   19.729534] sd 2:0:0:0: [sda] Attached SCSI disk
[   19.732678] sd 2:0:1:0: [sdb] Write Protect is off
[   19.732681] sd 2:0:1:0: [sdb] Mode Sense: 73 00 00 08
[   19.746482] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.750657]  sdc: unknown partition table
[   19.760510] sd 2:0:2:0: [sdc] Attached SCSI disk
[   19.817620]  sdb: sdb1
[   19.880718] sd 2:0:1:0: [sdb] Attached SCSI disk
[   19.912830] random: lvm urandom read with 93 bits of entropy available
[   20.036942] bio: create slab <bio-1> at 1
[   20.075637] random: nonblocking pool is initialized
[   25.300864] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[   25.300900] EXT4-fs (dm-0): write access will be enabled during recovery
[   25.482835] EXT4-fs (dm-0): recovery complete
[   25.484762] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   33.186454] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.186463] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   33.221713] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   33.229736] systemd-udevd[404]: starting version 204
[   33.263851] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.268625] lp: driver loaded but no devices found
[   33.280629] ppdev: user-space parallel port driver
[   33.289611] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   33.290484] EDAC MC: Ver: 3.0.0
[   33.295925] EDAC MC0: Giving out device to module i5100_edac.c controller i5100: DEV 0000:00:10.1 (POLLED)
[   33.299185] ACPI Warning: 0x0000000000000828-0x000000000000082f SystemIO conflicts with Region \PMRG 1 (20131115/utaddress-251)
[   33.299193] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   33.299197] ACPI Warning: 0x0000000000000480-0x00000000000004af SystemIO conflicts with Region \_SI_.SIOR 1 (20131115/utaddress-251)
[   33.299201] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   33.299228] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   33.306884] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   33.346636] FS-Cache: Loaded
[   33.369062] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   33.375224] type=1400 audit(1438967568.445:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=498 comm="apparmor_parser"
[   33.375234] type=1400 audit(1438967568.445:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=498 comm="apparmor_parser"
[   33.375239] type=1400 audit(1438967568.445:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=498 comm="apparmor_parser"
[   33.375721] type=1400 audit(1438967568.445:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=498 comm="apparmor_parser"
[   33.375728] type=1400 audit(1438967568.445:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=498 comm="apparmor_parser"
[   33.375973] type=1400 audit(1438967568.445:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=498 comm="apparmor_parser"
[   33.377941] type=1400 audit(1438967568.449:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=499 comm="apparmor_parser"
[   33.377948] type=1400 audit(1438967568.449:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=499 comm="apparmor_parser"
[   33.377953] type=1400 audit(1438967568.449:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=499 comm="apparmor_parser"
[   33.378425] type=1400 audit(1438967568.449:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=499 comm="apparmor_parser"
[   33.399437] gpio_ich: GPIO from 195 to 255 on gpio_ich
[   33.411023] FS-Cache: Netfs 'cifs' registered for caching
[   33.411169] Key type cifs.spnego registered
[   33.411182] Key type cifs.idmap registered
[   33.417090] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   33.428157] CIFS VFS: Error connecting to socket. Aborting operation.
[   33.428400] CIFS VFS: cifs_mount failed w/return code = -101
[   33.810020] e1000e 0000:00:19.0: irq 48 for MSI/MSI-X
[   33.912043] e1000e 0000:00:19.0: irq 48 for MSI/MSI-X
[   33.912205] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.588865] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   36.589003] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   39.912071] CIFS VFS: Error connecting to socket. Aborting operation.
[   39.912263] CIFS VFS: cifs_mount failed w/return code = -113
[   42.354677] audit_printk_skb: 6 callbacks suppressed
[   42.354678] type=1400 audit(1438967577.425:14): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=936 comm="apparmor_parser"
[   42.354685] type=1400 audit(1438967577.425:15): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=936 comm="apparmor_parser"
[   42.355162] type=1400 audit(1438967577.425:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=936 comm="apparmor_parser"
[   42.439006] Bluetooth: Core ver 2.17
[   42.439027] NET: Registered protocol family 31
[   42.439028] Bluetooth: HCI device and connection manager initialized
[   42.439041] Bluetooth: HCI socket layer initialized
[   42.439042] Bluetooth: L2CAP socket layer initialized
[   42.439046] Bluetooth: SCO socket layer initialized
[   42.452267] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   42.452268] Bluetooth: BNEP filters: protocol multicast
[   42.452275] Bluetooth: BNEP socket layer initialized
[   42.488295] Bluetooth: RFCOMM TTY layer initialized
[   42.488301] Bluetooth: RFCOMM socket layer initialized
[   42.488307] Bluetooth: RFCOMM ver 1.11
[   42.540601] init: cups main process (937) killed by HUP signal
[   42.540612] init: cups main process ended, respawning
[   42.653255] init: samba-ad-dc main process (974) terminated with status 1
[   45.912052] CIFS VFS: Error connecting to socket. Aborting operation.
[   45.913830] CIFS VFS: cifs_mount failed w/return code = -113
[   46.363749] init: failsafe main process (850) killed by TERM signal
[   46.732857] type=1400 audit(1438967581.805:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1182 comm="apparmor_parser"
[   46.732870] type=1400 audit(1438967581.805:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1182 comm="apparmor_parser"
[   46.732875] type=1400 audit(1438967581.805:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1182 comm="apparmor_parser"
[   46.733353] type=1400 audit(1438967581.805:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1182 comm="apparmor_parser"
[   46.733358] type=1400 audit(1438967581.805:21): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1182 comm="apparmor_parser"
[   46.733603] type=1400 audit(1438967581.805:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1182 comm="apparmor_parser"
[   46.733867] type=1400 audit(1438967581.805:23): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1186 comm="apparmor_parser"
[   46.815796] e1000e 0000:08:00.0: irq 49 for MSI/MSI-X
[   46.916139] e1000e 0000:08:00.0: irq 49 for MSI/MSI-X
[   46.917653] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   46.918613] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   51.912093] CIFS VFS: Error connecting to socket. Aborting operation.
[   51.913452] CIFS VFS: cifs_mount failed w/return code = -113
[   68.283062] init: plymouth-upstart-bridge main process ended, respawning
[   68.291556] init: plymouth-upstart-bridge main process (1807) terminated with status 1
[   68.291570] init: plymouth-upstart-bridge main process ended, respawning
[   72.425595] audit_printk_skb: 129 callbacks suppressed
[   72.425600] type=1400 audit(1438967607.497:67): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1865 comm="apparmor_parser"
[   72.425608] type=1400 audit(1438967607.497:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1865 comm="apparmor_parser"
[   72.426092] type=1400 audit(1438967607.497:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1865 comm="apparmor_parser"
[ 1473.031162] perf samples too long (2502 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
scott@6FC:/etc$ 


```


**lshw -C storage** output:
```
scott@6FC:/etc$ sudo lshw -C storage
[sudo] password for scott: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
  *-scsi                  
       description: SCSI storage controller
       product: SAS1064ET PCI-Express Fusion-MPT SAS
       vendor: LSI Logic / Symbios Logic
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: scsi2
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: scsi pm pciexpress msi msix bus_master cap_list rom scsi-host
       configuration: driver=mptsas latency=0
       resources: irq:16 ioport:c000(size=256) memory:df5fc000-df5fffff memory:df5e0000-df5effff memory:df200000-df3fffff
  *-ide
       description: IDE interface
       product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list
       configuration: driver=ata_piix latency=0
       resources: irq:19 ioport:b080(size=8) ioport:b000(size=4) ioport:ac00(size=8) ioport:a880(size=4) ioport:a800(size=16) ioport:a480(size=16)
scott@6FC:/etc$ 


```

I could use my USB-sata adaptor to conenct this drive to the server's USB socket, and see i fit mounts to the right place...

---

### Post by bab1 on 2015-08-07
```
19.750657]  sdc: unknown partition table
[   19.760510] sd 2:0:2:0: [sdc] Attached SCSI disk
```
It doesn't look like you are formatting the partition correctly.  I assume that you only have one of the HDD's in question attached at this point.  Also that this is the server we are looking at.

The system sees the partition.  It just doesn't like what you have done.

---

### Post by scott.bouch on 2015-08-07
> **bab1 said:**
> ```
19.750657]  sdc: unknown partition table
[   19.760510] sd 2:0:2:0: [sdc] Attached SCSI disk
```
It doesn't look like you are formatting the partition correctly.  I assume that you only have one of the HDD's in question attached at this point.  Also that this is the server we are looking at.

The system sees the partition.  It just doesn't like what you have done.

Hi BAB, yes that's right, I only added one to simplify things a bit, and yes, this is from the server.. The Partition Table is GPT, do you think trying a different type may help?

[ATTACH=CONFIG]263712[/ATTACH][ATTACH=CONFIG]263713[/ATTACH][ATTACH=CONFIG]263714[/ATTACH]

I've just quickly checked, and internally all drive ports are connected up (red sata cables).

Thanks again, Scott.

---

### Post by bab1 on 2015-08-07
I can see (logically) that the HDD (and therefore the partition) has connectivity via the output.  The problem is your method of formatting (adding a FS to the partition).  What does parted say about the HDD on the server.  In this state, what do you get from this CLI command```
sudo parted -l
```

---

### Post by scott.bouch on 2015-08-07
I really do appreciate all this help you're giving, thank you...

From **parted -l**:

```
scott@6FC:/etc$ sudo parted -l
[sudo] password for scott: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   120GB  120GB  extended
 5      257MB   120GB  120GB  logical                lvm


Model: ATA ST3500312CS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ext4


Error: Invalid argument during seek for read on /dev/sdc                  
Retry/Ignore/Cancel? r                                                    
Error: Invalid argument during seek for read on /dev/sdc                  
Retry/Ignore/Cancel? i                                                    
Error: The backup GPT table is corrupt, but the primary appears OK, so that will be used.
OK/Cancel? ok                                                             
Backtrace has 8 calls on stack:
  8: /lib/x86_64-linux-gnu/libparted.so.0(ped_assert+0x31) [0x7f90c6cdc4b1]
  7: /lib/x86_64-linux-gnu/libparted.so.0(+0x3f5f6) [0x7f90c6d0c5f6]
  6: /lib/x86_64-linux-gnu/libparted.so.0(ped_disk_new+0x49) [0x7f90c6ce1f99]
  5: parted() [0x406dff]
  4: parted() [0x407bda]
  3: parted(main+0x154b) [0x4065cb]
  2: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf5) [0x7f90c64b9ec5]
  1: parted() [0x406617]
                                                                          

You found a bug in GNU Parted! Here's what you have to do:

Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:

Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:

    http://ftp.gnu.org/gnu/parted/

Please check this version prior to bug reporting.

If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:

    http://www.gnu.org/software/parted

for further information.

Your report should contain the version of this release (2.3)
along with the error message below, the output of

    parted DEVICE unit co print unit s print

and the following history of commands you entered.
Also include any additional information about your setup you
consider important.

Assertion (last_usable <= disk->dev->length) at ../../../libparted/labels/gpt.c:994 in function _parse_header() failed.

scott@6FC:/etc$
```

It had an issue with **sdc**, I initially gave it a retry, then ignore, as you'll see above..

Thanks, Scott.

---

### Post by TheFu on 2015-08-07
Did you wipe the disk before starting over?

Better to follow this [http://www.thegeekstuff.com/2012/08/2tb-gtp-parted/](http://www.thegeekstuff.com/2012/08/2tb-gtp-parted/)

If you aren't positive - use the parted *print* command to see what happened.

*deleted steps which were not complete. *

The only reason to limit the partitions to 2T is to match the backup location disk areas. Actually, it may be smart to use less.  Personally, I'd use LVM and start with much smaller LVs, only growing when necessary.  If you use LVM, make 1 large partition and use that for the PEs.

If the GPT errors are seen again, run badblocks and look for disk failures.  I would enter thinking the HDD is failing and look for reasons to return it ASAP, before it becomes a hassle.

Make sense?  Hope I didn't forget anything important.

---

### Post by bab1 on 2015-08-07
What were you using to format the partition; what commands exactly?  Are you trying to use fdisk?

---

### Post by scott.bouch on 2015-08-07
Hi BAB,

I was using GParted Partition Editor GUI on the desktop machine.. I'd not done any of the drive formatting from the command line, not fdisk or parted.

Am I best to try performing the above actions with the drive installed in the server (all command line), or, taking it out and using my desktop machine (GParted GUI)?

TheFu: When you say about formatting to 2GB, do you mean 2TB? - just checking before I have a go...

Thanks, Scott.

Sorry about all the really basic questions, but you've got to start somewhere!

---

### Post by bab1 on 2015-08-07
I'm assuming he meant 2TB.  2GB makes no sense.  While we are talking about partition size, I'll just say that you want the simplest plan you can go with. Figure out what your needs are and use the appropriate tools.  I don't see where you need LVM.  You are not trying to aggregate a bunch of partitions into one large space.  LVM would just add a layer of unnecessary complication.  The same thing for RAID.  I have a multi HDD, multi partition LV so I have a single large space that has one mount point.  It works, but it's not something you need to manage [COLOR="#0000FF"]at this time.[/COLOR]

I always add the physical disk to the chassis and use the tools that the OS provides.  In your situation it would eliminate one variable (the other machine).  As @TheFu mentioned, the commands are simple.  I would start by seeing if you can reformat the FS (ext4) and see if that works.  If not then you will need to delete the partition and then reformat the disk.  I've never had to "wipe clean" a disk.  Once you "reformat" or "delete the partition and reformat" the disk function. The old data might be there (in fragments), but not normally accessible.  It will not be calculated as "used space".

Basic questions are definitely welcomed.  They're best asked before starting.  ;-)

---

### Post by scott.bouch on 2015-08-07
Thanks again,

I'll try to progress this tomorrow night by formatting the drive in the server with **parted** at the command line via ssh.

I'm ok to just re-load all the data rather than trying to recover it.. just got to get it working first...

It's a shame, I know a few people locally who are good with IT, however, none are into Linux, so I have nobody to call over to have a look! The help given by you two is very much appreciated, many thanks indeed..

Thanks again, Scott.

---

### Post by TheFu on 2015-08-07
You are correct - my mistake - s/2G/2T/g. Sorry.

If you don't know and love LVM already - don't start today. It isn't needed.

---

### Post by scott.bouch on 2015-08-11
Hmm... this learning curve is just frustrating now.. I've had a stab, but thought I'd post my results now before digging myself deeper into a messy hole.

One of the new 4TB drives is in the server at **/dev/sdc**, all the following is via** ssh**.

I had a go with **parted** at the command line, but it wouldn&#8217;t let me create a 4TB partition (I wanted just one big partition per drive, which shouldn't be a problem with GPT), so I tried incrementally reducing partition size, until I got to 3TB, where upon **parted** decided to allow a 2.2TB partition:
```
scott@6FC:~$ sudo parted /dev/sdc
GNU Parted 2.3
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel gpt                                                      
(parted) unit TB                                                          
(parted) mkpart primary 0.00TB 4.00TB
Error: The location 4.00TB is outside of the device /dev/sdc.             
(parted) mkpart primary 0.00TB 3.80TB                                   
Error: The location 3.80TB is outside of the device /dev/sdc.             
(parted) mkpart primary 0.00TB 3.60TB                                    
Error: The location 3.60TB is outside of the device /dev/sdc.             
(parted) mkpart primary 0.00TB 3.50TB                                    
Error: The location 3.50TB is outside of the device /dev/sdc.             
(parted) mkpart primary 0.00TB 3.00TB                                    
(parted) print                                                            
Model: ATA WDC WD40EFRX-68W (scsi)
Disk /dev/sdc: 2.20TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      0.00TB  2.20TB  2.20TB               primary

(parted) mkpart logical 2.20TB 4.00TB
Error: The location 4.00TB is outside of the device /dev/sdc.             
(parted) mkpart logical 2.20TB 3.60TB                                   
Error: The location 3.60TB is outside of the device /dev/sdc.             
(parted) mkpart logical 2.20TB 3.00TB                                    
Warning: The resulting partition is not properly aligned for best performance.
Ignore/Cancel? c                                                          
(parted) mkpart logical 2.20TB 2.80TB                                   
Warning: The resulting partition is not properly aligned for best performance.
Ignore/Cancel? c                                                          
(parted) quit
Information: You may need to update /etc/fstab.
```

I then had a stab at making a second partition to use the rest of the HDD space, but it wasn't too happy about it:
```
(parted) mkpart logical 2.20TB 4.00TB
Error: The location 4.00TB is outside of the device /dev/sdc.             
(parted) mkpart logical 2.20TB 3.60TB                                   
Error: The location 3.60TB is outside of the device /dev/sdc.             
(parted) mkpart logical 2.20TB 3.00TB                                    
Warning: The resulting partition is not properly aligned for best performance.
Ignore/Cancel? c                                                          
(parted) mkpart logical 2.20TB 2.80TB                                   
Warning: The resulting partition is not properly aligned for best performance.
Ignore/Cancel? c                                                          
(parted) quit
Information: You may need to update /etc/fstab.
```

I gave up on that one.

Then I tried formatting my new 2.2TB partition to EXT4 using **mkfs**:
```
scott@6FC:~$ sudo mkfs -t ext4 /dev/sdc1
mke2fs 1.42.9 (4-Feb-2014)
/dev/sdc1 is not a block special device.
Proceed anyway? (y,n) y
mkfs.ext4: No such device or address while trying to determine filesystem size
scott@6FC:~$
```

I made the first partition **primary** and tried to make the second **logical**, as I didn't really know what I was doing at the time, (still clutching at straws), would it work better if it was one **logical**? Is there a way to get it to just make one partition to the maximum space available without having to specify the start and finish (as in *[I hate to say]* Windows, "just format the drive")?

Have I done anything wrong? Am I being daft? Can you see any errors in what I've done?

Many Thanks, Scott

---

### Post by TheFu on 2015-08-11
**I was wrong!  mklabel DOES make a GPT partition table.**

With GPT disks, there isn't any "logical" partitions. There is only primary partitions and over 100 of those are allowed.  Extended and Logical are a kludge for MBR/MSDOS partition tables.

The 2.2T limit seems ominous.  That is the limit for MBR partition tables.  Some disk controllers don't understand larger disks. Nothing you can do except swap them out if there isn't a firmware update.

Whenever there is any doubt - check your work with **sudo parted -l** - please post a current one for just this 4T disk so we can see what has happened so far.  If all those errors still exist - it is a bad disk, bad controller, bad cable or some other issue.  Was this disk brand new or did you get it from someone else or was it in a RAID set previously?

---

### Post by scott.bouch on 2015-08-11
Thanks dude, here is is:

```
Model: ATA WDC WD40EFRX-68W (scsi)
Disk /dev/sdc: 2199GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  2199GB  2199GB               primary


```

The drive is a brand new WD Red 4TB. It did work nicely on my desktop machine when I formatted it with GParted to Ext4 via a USB adaptor.. to a size greater than 3TB.. I think I got something like 3.7 / 3.8 out of it, that was GPT.

Thanks, Scott

---

### Post by TheFu on 2015-08-11
I have a few 2TB WD-Reds ... ```

Model: ATA WDC WD20EFRX-68A (scsi)
Disk /dev/sdf: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  132MB   132MB                      
 2      132MB   1371GB  1371GB  ext4               
 3      1371GB  2000GB  629GB   ext4
```

And a few 4TB Hitachis:

```
Model: ATA HGST HMS5C4040AL (scsi)
Disk /dev/sdc: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  258MB   256MB   ext2               msftdata
 3      258MB   4001GB  4001GB                     lvm
```

There are a few LVs (think "partitions") inside the LVM partition.

Ah - found a WD Red 4T - it is purely for backups, so no LVM there.
```
Model: WDC WD40 EFRX-68WT0N0 (scsi)
Disk /dev/sdd: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  62.9GB  62.9GB  ext4
 2      62.9GB  4001GB  3938GB  ext4
```

It has been awhile since I set these up.
Anyway - figured seeing some examples would be helpful.  Note that I was wrong in the posts above. Memory failure. Sorry.

---

### Post by bab1 on 2015-08-11
The rules seem pretty straightforward to me.  Since the disk has been partitioned by you unsuccessfully already, I would remove the partitions (using parted)```

# list the partitions
(parted) print
# This lists the partitions (*minor* (number))

#remove existing partitions
(parted) rm minor
# as many times as there are partitions
# I would check the partition number (minor) as these can change if one of them is a msdos logical partition

# create a new partition label (partition type) 
(parted) mklabel gpt
 
# set the default unit to TB.
(parted) unit TB

# Create a 4TB partition size.
(parted) mkpart primary 0.00TB 4.00TB

# list the current partition.
(parted) print

```

After that you can add the file system using parted or directly using mkfs.

Although I have never created a partition as large as 4TB I can't see any reason that parted can't do the job.  As you have already stated you have done so using the GUI equivalent.

See [here]("http://linoxide.com/file-system/parted-command-to-create-partition-greater-than-2tb/") and [here]("http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC8") for reference.

---

### Post by scott.bouch on 2015-08-12
Hi both, (dotted lines [----------] segregate merged messages)

Thanks again for your time on this, it's really appreciated!

I've followed the instructions given by bab1, but made a minor change... I found that you can specify the amount of drive to be used by the partition by percentage, instead of TB / GB. As I wanted one partition to fill the whole drive, I told parted to add a partition from 0% to 100%, thinking this would ace it.

Disappointing results:
```
(parted) mkpart primary 0% 100%
(parted) print                                                            
Model: ATA WDC WD40EFRX-68W (scsi)
Disk /dev/sdc: 2.20TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      0.00TB  2.20TB  2.20TB               primary
```

Could it be a limitation of my server, being that I bought it second hand, it could pre-date the use of **GPT** partition tables, and hence, impose the limit of 2.2TB?

Reading [here]("http://en.community.dell.com/support-forums/servers/f/906/t/19538567") about the DELL CS24-SC it may well be a limitation of the server...

So I'll live with this partition of 2.2TB (if I now can get it working & mounted that is) and use the rest of the drive as another partition. 

Would I now be wise to use LVM / Raid to stick these two partitions back together to form one drive?

Cheers, Scott (now off to try creating the file system).

--------------------------------------------------------------------------------------------------------

Strangely, I'm kind of forced by **parted** to only be able to create 2.20TB partitions, even when I specified 2.00TB.. 

hey-ho I thought, lets' try an EXT4 file system...

```
(parted) mklabel gpt                                                      
Warning: The existing disk label on /dev/sdc will be destroyed and all data on this disk
will be lost. Do you want to continue?
Yes/No? y                                                                 
(parted) print                                                            
Model: ATA WDC WD40EFRX-68W (scsi)
Disk /dev/sdc: 2199GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

(parted) unit TB
(parted) mkpart primary 0.00TB 2.00TB                                     
(parted) print                                                            
Model: ATA WDC WD40EFRX-68W (scsi)
Disk /dev/sdc: 2.20TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      0.00TB  2.20TB  2.20TB               primary
```


```
(parted) mkfs                                                             
WARNING: *blaah blaah blaa*h. Do you want to continue?
Yes/No? y                                                                 
Partition number? 1                                                       
File system type?  [ext2]? ext4                                           
No Implementation: Support for creating ext4 file systems is not implemented yet.
(parted) 
```

So, there's a problem with creating an EXT4 filesystem.. using **mkfs** from within **parted** gave more helpful information than doing it just running it from the command line.

This is Ubuntu 14.04 (using kernel 3.13.0-43-generic), so I wouldn't have thought would have an issue with ext4..?

However, it has just allowed me to create an **ext2** filesystem.. took about 5 minutes.

Tried then re-creating the filesystem as **ext3**, but same result as **ext4**.

There's a limitation somewhere.. maybe I need up update **parted** or **mkfs**, but as I said above, this is a fairly recent install, so perhaps it's a server hardware limitation?? 

```
(parted) print                                                            
Model: ATA WDC WD40EFRX-68W (scsi)
Disk /dev/sdc: 2.20TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      0.00TB  2.20TB  2.20TB  ext2         primary

(parted)  
```

Strange thing is, I have a 500GB **ext4** drive installed and working fine, but that has an **msdos** partition table.

If there are any more ideas, I'll be happy to try them, if not, I'll have to  use it as **ext2**, or buy another NAS box to take these two 4TB drives, as it's a bit of a waste of drives currently.

Through this experience, I've gone from total bafflement, to gaining some understanding and a little confidence! Many thanks got to **bab1** and **TheFu** for all the help!

Cheers, Scott.

--------------------------------------------------------------------------------------------------------

Oh no... the latest instalment in the tale of woe... 

Just went to get the newn 2.2TB ext2 partitions **UUID** to mount the drive by **fstab**, and **blkid** can't see **sdc** or **sdc1** that I've just created and _can_ see with **parted**.

```
scott@6FC:/$ sudo blkid -c /dev/null -o list
device                   fs_type    label       mount point                  UUID
------------------------------------------------------------------------------------------------------------------
/dev/sda1                ext2                   /boot                        442ef4fd-bc9b-4e17-825e-27f5e7a1414d
/dev/sda5                LVM2_member            (in use)                     cP6I40-148L-tXrh-w2bm-R1UT-YqLb-OZMHNQ
/dev/sdb1                ext4       Storage     /media/storage               1ecfb548-c745-49f5-b143-37965eea3fe9
/dev/mapper/6FC--vg-root ext4                   /                            7e34d6d4-0fa1-4ce3-9964-9e61b61fe322
scott@6FC:/$ 
```

Just when you think you're getting somewhere, it all falls apart again...

--------------------------------------------------------------------------------------------------------

ARGHH!!!

Just tried adding **sdc1** to **fstab** regardless of what **blkid** said, and it's not worked. (surprise, surprise).

**fstab **entry:
```
/dev/sdc1       /family ext2    defaults        0       2
```

Result:
```
scott@6FC:/etc$ sudo mount -a
mount: /dev/sdc1 is not a block device
scott@6FC:/etc$ 
```

Plenty of swearing.. off for a coffee.

Are there any clues in what a "block device" is? *or isn't *in this case?

---

### Post by TheFu on 2015-08-12
I think you have a broken disk controller or broken BIOS.
[http://www.tomshardware.com/forum/295845-32-external-limit](http://www.tomshardware.com/forum/295845-32-external-limit)

How is the disk connected to the system?

What does **ls -al  /dev/sdc*** show?

---

### Post by scott.bouch on 2015-08-12
Hi TheFu,

Here's the result:

```

scott@6FC:~$ ls -al /dev/sdc*
brw-rw---- 1 root disk 8, 32 Aug 12 13:03 /dev/sdc
cr-------- 1 root root 8, 33 Aug  7 19:19 /dev/sdc1
```


Thanks, Scott.

---

### Post by TheFu on 2015-08-12
Ok - so the permissions **cannot** be correct.
What are the permissions for the other disk devices? See the difference?

I still think there is a HW limitation to overcome the 2.2T limit.

---

### Post by scott.bouch on 2015-08-12
Hi TheFu,

The drive is internally connected via a SATA connection, as per the working drives (4x red cables in the wonky image). It's in a proper caddy I recently bought and fitted in the proper hole in the front, in the third bay.

[ATTACH=CONFIG]263795[/ATTACH]

Here's the result for all of the drives:

```

scott@6FC:~$ ls -al /dev/sda*
brw-rw---- 1 root disk 8, 0 Aug 12 13:03 /dev/sda
brw-rw---- 1 root disk 8, 1 Aug  7 18:12 /dev/sda1
brw-rw---- 1 root disk 8, 2 Aug  7 18:12 /dev/sda2
brw-rw---- 1 root disk 8, 5 Aug  7 18:12 /dev/sda5
scott@6FC:~$ ls -al /dev/sdb*
brw-rw---- 1 root disk 8, 16 Aug 12 13:03 /dev/sdb
brw-rw---- 1 root disk 8, 17 Aug  7 18:12 /dev/sdb1
scott@6FC:~$ ls -al /dev/sdc*
brw-rw---- 1 root disk 8, 32 Aug 12 13:03 /dev/sdc
cr-------- 1 root root 8, 33 Aug  7 19:19 /dev/sdc1
scott@6FC:~$ 


```

Yes, **sdc1** is different to the others (**cr** instead of **brw-rw**) and **root root** instead of **root disk**. I don't quite know exactly what these differences mean right now though..

Thanks, Scott.

---

### Post by bab1 on 2015-08-12
> **scott.bouch said:**
> Hi TheFu,

The drive is internally connected via a SATA connection, as per the working drives (4x red cables in the wonky image). It's in a proper caddy I recently bought and fitted in the proper hole in the front, in the third bay.

[ATTACH=CONFIG]263795[/ATTACH]

Here's the result for all of the drives:

```

scott@6FC:~$ ls -al /dev/sda*
brw-rw---- 1 root disk 8, 0 Aug 12 13:03 /dev/sda
brw-rw---- 1 root disk 8, 1 Aug  7 18:12 /dev/sda1
brw-rw---- 1 root disk 8, 2 Aug  7 18:12 /dev/sda2
brw-rw---- 1 root disk 8, 5 Aug  7 18:12 /dev/sda5
scott@6FC:~$ ls -al /dev/sdb*
brw-rw---- 1 root disk 8, 16 Aug 12 13:03 /dev/sdb
brw-rw---- 1 root disk 8, 17 Aug  7 18:12 /dev/sdb1
scott@6FC:~$ ls -al /dev/sdc*
brw-rw---- 1 root disk 8, 32 Aug 12 13:03 /dev/sdc
**[COLOR="#FF0000"]c[/COLOR]**r-------- 1 root root 8, 33 Aug  7 19:19 /dev/sdc1
scott@6FC:~$ 


```

Yes, **sdc1** is different to the others (**cr** instead of **brw-rw**) and **root root** instead of **root disk**. I don't quite know exactly what these differences mean right now though..

Thanks, Scott.
The sdc1 is listed as a character device (listed in red above), but not formatted as a block device).  All the others have been successfully formatted so they are listed as block devices.

Earlier on you said you had 2 of these 4TB HDD's.  Have you tried to partition and add an ext4 file system to that HDD?  The disk controller that @TheFu is referring to is the electronics on the HDD itself, so trying the other disk will help in diagnosing the problem.  I doubt that both HDD's would have the same problem.   If you have the same problem with the other drive, I would think the host machine is at fault in some way.

---

### Post by TheFu on 2015-08-12
I think the issue is with the disk controller on the motherboard.  
Please try swapping some SATA cables around to see if the issue is related the port. 

Also, please lookup the MB to see if there is firmware updates available - look through the change list for anything related to 2.2T drive limits.

---

### Post by scott.bouch on 2015-08-12
Great advice guys, many thanks indeed.

I'll have a look at the motherboard later when I'm home, and also will try the other drive, and try swapping cables around.

As it's an unsupported server type (as I keep on finding DELL tech-support comments stating so on forums / help pages etc..) I doubt if I'll be able to find much in the way of a firmware upgrade, unless it's common to other server computers too.

I seem to have to pick an oddball server here, the CS24-SC: the CS stands for Custom Server, so very little literature is around for it. I did find one website that stated that Facebook recently upgraded from this type of server, a whole 10,000 of them, so there's a chance that these may have originally been ordered by Facebook, and used for a few years, before being sold on to people like me via ebay.

If tonight’s experimentation if fruitless, I'll just buy a NAS enclosure capable of taking these two 4TB drives, then my problems will hopefully go away... If anything has come out of this, it's improved my confidence at the command line, and has exposed me to functions / software I'd never used before - I can put it down as a worthwhile learning exercise. It'll also be good to know it's the machine that's got issues, not me! ;)

Thanks again to both of you, Scott.

---

### Post by bab1 on 2015-08-12
Googling "CS24-SC" gets lots of information re: the built in 2TB limit for partitions on this server.  It's a hardware limitation.  If you really want to have 4TB data stores on this machine you will have to use LVM to combine the 2TB partitions.  Extra work, but if you need a contiguous 4TB then it is worth while.

---

### Post by scott.bouch on 2015-08-12
Oh blimey, you're right...

Well, after all that work (big thank-you by the way) we've gone right round and back to the fundamentals!

Solution: £40 NAS enclosure... and all problems go away.. I'll put this down as a good learning experience in Ubuntu, drives, formatting, and hardware, and move on.

I'll remember all of this in case I want to add some _**2**_TB drives in the future to the spare slots. It's been one  heck of a learning curve, and one I'm glad to have had great tech-support through. Can't say enough thank-you's!!

Fantastic help received, I may even get round to writing myself a little aide mémoire on my website for the next time I have a go at formatting drives! 

Thanks again, Scott.

---

