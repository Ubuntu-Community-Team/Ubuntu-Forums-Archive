---
title: "problems mounting external usb device with ext3"
date: 2009-01-19
forum: Server Platforms
---

### Post by fuzzy_4711 on 2009-01-19
Hello.

I have a problem mounting an external usb disk and I hope someone is able to help:

The device is /dev/sdc :
```
root@speernix:/# fdisk -l

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

```

I did its initialization like this:
```
mkfs.ext3 -L 500GB-USB-DISK /dev/sdc
```

My /etc/fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
# mounting backup hdd disk (image) also
/dev/sdb1       /mnt/backupdisk ext3    defaults,errors=remount-ro 0    2

# mounting backup usbdisk for daily cpio backup
LABEL=160GB_USBDISK     /mnt/usbdisk    ext3    defaults        0       0

# mounting the new 500 GB USB-Disk using its label
LABEL=500GB-USB-DISK    /mnt/500GB-USB-DISK     ext3    defaults,debug  0       0

```

If I do a:
```
mount -a
```
as root, everything works fine.

Now I started copying gigs of data to the new mounted partion. After a while, say after aprox. 45GB are copied, the bg-job says, it is done:
```
[1]+  Done                    cp -Rv /mnt/usbdisk/image-sda1.partimage.00* /mnt/500GB-USB-DISK/partimage_backup/
```

But verifying manually shows that one file, image-sda1.partimage.003 is missing and has not been copied.

Trying to do the following command:
```
root@speernix:/# cp -Rv /mnt/usbdisk/image-sda1.partimage.003 /mnt/500GB-USB-DISK/partimage_backup/ &
```
brings up the following error message:
```
cp: cannot create regular file `/mnt/500GB-USB-DISK/partimage_backup/image-sda1.partimage.003': Read-only file system
```

When trying to fix it that way:
```
umount /mnt/500GB-USB-DISK
mount -a 
```
my /var/log/messages shows something like this:
```
Jan 19 17:19:32 speernix kernel: [43133028.430000]
Jan 19 17:30:36 speernix kernel: [43133692.210000] kjournald starting.  Commit interval 5 seconds
Jan 19 17:30:36 speernix kernel: [43133692.210000] EXT3-fs warning (device sdc1): ext3_clear_journal_err: Filesystem error recorded from previous mount: IO failure
Jan 19 17:30:36 speernix kernel: [43133692.210000] EXT3-fs warning (device sdc1): ext3_clear_journal_err: Marking fs in need of filesystem check.
Jan 19 17:30:36 speernix kernel: [43133692.210000] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
Jan 19 17:30:36 speernix kernel: [43133692.210000] [EXT3 FS bs=4096, gc=3727, bpg=32768, ipg=16384, mo=10808]
Jan 19 17:30:36 speernix kernel: [43133692.210000] EXT3 FS on sdc1, internal journal
Jan 19 17:30:36 speernix kernel: [43133692.210000] EXT3-fs: recovery complete.
Jan 19 17:30:36 speernix kernel: [43133692.210000] EXT3-fs: mounted filesystem with ordered data mode.

```

I have been running the e2fsck several times like recommended. When I do that, everything is fine as long I do not start to copy my big image files again. By doing so, I will run in the same trouble again. I also re-partioned the disk and initialized it again the way I described it. No way to get it running.

My file systems block size:
```
root@speernix:/# dumpe2fs /dev/sdc1 | grep -ir "Block size"
dumpe2fs 1.38 (30-Jun-2005)
Block size:               4096

```
So I think the max file size can be up to 2TB and the Filesystem's size up to 16TB which is more than enough.

Also, I do not get the point, why I am told that the file system is read-only, since I do declare different in fstab without getting any error.

I assume that there will be an internal mount process again after an error occures and because of the error it is mounted read-only again. But not sure here.

Anybody got the same behavior or any ideas? I am kinda stuck.
Any help would be highly appreciated.

Thanks.

-fuz

p.s.: This box runs an LTS 6.0.6 ubuntu server version.

---

### Post by fjgaude on 2009-01-19
I don't have a clue except maybe the OS is old enough to not know about drives this large. Seems three years ago the idea of a 500GB drive wasn't in many folks dreams. How times change, eh!

Could you upgrade to Server 8.04?

---

### Post by fuzzy_4711 on 2009-01-19
```
Could you upgrade to Server 8.04?
```

If I do not have to I would be glad to avoid this. Also I do not know all the implications of an update which would probably cause some work and investigations to get an idea on that.

-fuz

---

### Post by aaron.d on 2009-01-19
> I assume that there will be an internal mount process again after an error occures and because of the error it is mounted read-only again. But not sure here.

that's the key.

```
Filesystem error recorded from previous mount: IO failure
```

Looks like the USB connection was/is flakey and bailed out while you were writing. Since it is marked as having errors, and YOU remounted it, you were given the warning to fsck and it was mounted RO.

Before running fsck, PLEASE unmount the partition FIRST. run (as root):
```

 fsck -y /dev/sdc1 


```(make sure this device is still the correct one) and let it rip. 
It is likey you will have some lost files. (check lost+found on that partition after it is mounted.)

It doesnt sound like you have anything SOLELY on this partition, so a quicker way would be to re-format it, if you want to start from scratch.

Try another USB port next time, and keep an eye on the output of:

```
$dmesg
```

edit: Im sorry but suggesting a complete OS upgrade in this case is a bad solution. We dont run windows here. :D
 TB (RAID) partitions have been prevalent for much longer than 3 years. Since we know he is using the ext3 FS, we can even check our facts:

[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

EXT3 has been around since 2001, and supports anywhere from 2TB - 16TB, depending on block size. Furthermore, he happens to have given us his block Size:

```
root@speernix:/# dumpe2fs /dev/sdc1 | grep -ir "Block size"
dumpe2fs 1.38 (30-Jun-2005)
Block size:               4096
```

which, according to wikipedia, will result in:


4KiB Block size = 2TiB Max file size,<8TiB Max filesystem size

---

### Post by fuzzy_4711 on 2009-01-19
```
Before running fsck, PLEASE unmount the partition FIRST. run (as root): fsck -y /dev/sdc1 
```

That is what I did. I unmounted the device first and then I run the file check utility /sbin/fsck.ext3 -y /dev/sdc1

Please understand - I am through all this before. I reformatted the disk, tried to repair the file system and - yes I have been reading a few man pages :P but nothing had helped so far.

So I will try using another usb port. What else do you see as a possible solution? Could it be a broken disk? Or what else could cause this? I hope I do not have to install the kernel source package an grep the source for the constant definitions to see when they are risen...

Should I check the entire disk for defect clusters or bad sectors? If that is the way to go: Which tool should I use for that purpose?

Thanks again.

-fuz

---

### Post by aaron.d on 2009-01-19
I think this is probably an interface issue (USB) and not the disk proper, but I have been wrong before.

If you could take it out of the housing and toss it in a computer to run the makers diagnostic tools, that would be good practice. What kind of drive is it (make, model, size (full size or laptop drive). Most manufacturers have tools for this.
But as for the USB, check the cable and make sure it is not going through any hubs etc. If all is good, for sure try different ports.

---

### Post by fuzzy_4711 on 2009-01-19
I did it all again, just to make sure...

The same failure appears again. Here is the output of dmesg:
```
[43147133.370000] EXT3-fs error (device sdc1): ext3_free_blocks_sb: bit already cleared for block 108331968z2 39 fifo 0
[43147133.390000] Aborting journal on device sdc1.
[43147133.390000] EXT3-fs error (device sdc1): ext3_free_blocks_sb: bit already cleared for block 108331969
[43147133.410000] EXT3-fs error (device sdc1): ext3_free_blocks_sb: bit already cleared for block 108331970
[43147133.440000] EXT3-fs error (device sdc1): ext3_free_blocks_sb: bit already cleared for block 108331971
[43147133.450000] EXT3-fs error (device sdc1): ext3_free_blocks_sb: bit already cleared for block 108331972
[43147133.470000] EXT3-fs error (device sdc1): ext3_free_blocks_sb: bit already cleared for block 108331973
[43147133.490000] EXT3-fs error (device sdc1): ext3_free_blocks_sb: bit already cleared for block 108331974
[43147133.510000] EXT3-fs error (device sdc1) in ext3_free_blocks_sb: Journal has aborted
[43147133.540000] EXT3-fs error (device sdc1) in ext3_reserve_inode_write: Journal has aborted
[43147133.560000] EXT3-fs error (device sdc1) in ext3_truncate: Journal has aborted
[43147133.580000] EXT3-fs error (device sdc1) in ext3_reserve_inode_write: Journal has aborted
[43147133.590000] EXT3-fs error (device sdc1) in ext3_orphan_del: Journal has aborted
[43147133.610000] EXT3-fs error (device sdc1) in ext3_reserve_inode_write: Journal has aborted
[43147133.630000] EXT3-fs error (device sdc1) in ext3_delete_inode: Journal has aborted
[43147133.630000] __journal_remove_journal_head: freeing b_committed_data
[43147133.650000] ext3_abort called.
[43147133.660000] EXT3-fs error (device sdc1): ext3_journal_start_sb: Detected aborted journal
[43147133.680000] Remounting filesystem read-only

```

Any more insights after this?

I do not want to run away from the prob, but it looks like a ext3 - problem to me. Maybe I should use another filesystem.
What do you think?

Thanks.

-fuz

---

### Post by aaron.d on 2009-01-19
you reformatted and got this again?

can you give a bit more info as to when it "failed" this time (like what you were doing etc)? I really don't think there is an ext3 issue, but there could be an issue with the HD. OF course, you could have better luck with a different file system. Try reiserFS if you want to use something different. If you still have issues, then you know you have a drive or interface issue. Is this drive in an enclosure? that could also be the issue.

---

### Post by cteneyck on 2009-01-19
have you tried.

sudo mkdir /mnt/yourusbdrive

sudo chmod -R 777 /mnt/yourusbdrive

edit fstab to look like this

/dev/sdc1     /mnt/yourusbdrive    ext3     suid,dev,exec        0       0

then 

mount -a

---

### Post by cteneyck on 2009-01-19
sorry for double posting 

so i pulled out my 160 gig usb drive and here is what i did and it seems to be working

also add sudo before every command. i was rooted


```

root@parmetheus:/# mkdir /media/usbdrive
root@parmetheus:/# chmod -R 777 /media/usbdrive
root@parmetheus:/# fdisk /dev/sdc

The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): d
Selected partition 1

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
root@parmetheus:/# fdisk /dev/sdc

The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-19457, default 1):
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-19457, default 19457):
Using default value 19457

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
root@parmetheus:/# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe239e239

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9353    75127941   83  Linux
/dev/sda2            9354        9729     3020220    5  Extended
/dev/sda5            9354        9729     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19929   160079661   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1189c96c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux
root@parmetheus:/#


root@parmetheus:/# mkfs.ext3 /dev/sdc1
mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
9773056 inodes, 39072080 blocks
1953604 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1193 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 27 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
root@parmetheus:/#vim /etc/fstab


#uid,dev,exec/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a48705de-9731-49d0-85f3-5107c404465f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=927ad85c-8747-4949-bc4b-7fb88e522fac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1  /media/samba-shares  ext3  suid,dev,exec  0  0
/dev/sdc1  /media/usbdrive  ext3  suid,dev,exec  0  0
```

Then reboot

I don't know if it this supports hot plugging but i would unmount before unpluging the usb too.

---

### Post by fuzzy_4711 on 2009-01-22
Hello again.

I got it fixed and just wanted to thank everybody involved in finding the solution. Also I want to provide the solution here and hope someone is able to participate on it.

Well what I did is delete the partition again using fdisk. Then I reallocated a new partition and gave it the reiser file system using mkfs.reiserfs. The same story happened again with the new file system on it - the partition was mounted read-only again and flagged with an error code.

dmesg gave me the information that there have been errors when mounting.

I run fsck.reiserfs which came up with the message that there a lot of bad sectors on the hdd I was trying to check. Bad sectors are just areas where, whatever reason, the magnetism on the disk is not working any more. Most people think that once a disk starts to have those bad sectors, it usually will get more quickly. Because it was a new disk I didnt like to accept these circumstances and went to the dealer to get a new one.

As arron.d mentioned - it could be the enclosure also - I tested the new disk right at the dealer's place using vista. I run into a new problem: The new couldnt be formatted. So we tested a new enclosure also. Finally I ended up with a new disk and a new closure - just to be sure. Could have changed the enclosure only, which caused this strang behaviour.

One last word about the bad sectors (for everybody interested): Usually the file system holds a table, where the location of all bad sectors is saved. Before new data is committed to disk, this table is queried to avoid writting data to the sectors marked as bad.

Thanks to everybody.

-fuz

---

