---
title: "Mdadm/RAID5 problems. Please help!!"
date: 2009-02-19
forum: Server Platforms
---

### Post by Aenima99x on 2009-02-19
So here's the situation.....4 drives in a 1.5 TB RAID5 array. I'm not sure if I've lost data or not at this point. I won't get into why, but I don't have access to my backup, so if the data on my RAID is gone, then I'm screwed. There was about 500 GB of movies, music and ALL my pictures. I can re-rip my movies and cd's, but the pictures obviously are not replaceable.

I've already tried removing mdadm & mdadm.conf, rebooting, and reinstalling mdadm. During the mdadm install, I was greeted with these "lovely" messages -
```
Setting up mdadm (2.6.7-3ubuntu8) ...
Generating array device nodes... rm: cannot remove `md0-': Read-only file system
mknod: `md0-': Read-only file system
rm: cannot remove `md0-': Read-only file system
rm: cannot remove `md1-': Read-only file system
mknod: `md1-': Read-only file system
rm: cannot remove `md1-': Read-only file system
rm: cannot remove `md2-': Read-only file system
mknod: `md2-': Read-only file system
rm: cannot remove `md2-': Read-only file system
rm: cannot remove `md3-': Read-only file system
mknod: `md3-': Read-only file system
rm: cannot remove `md3-': Read-only file system
rm: cannot remove `md4-': Read-only file system
mknod: `md4-': Read-only file system
rm: cannot remove `md4-': Read-only file system
rm: cannot remove `md5-': Read-only file system
mknod: `md5-': Read-only file system
rm: cannot remove `md5-': Read-only file system
rm: cannot remove `md6-': Read-only file system
mknod: `md6-': Read-only file system
rm: cannot remove `md6-': Read-only file system
rm: cannot remove `md7-': Read-only file system
mknod: `md7-': Read-only file system
rm: cannot remove `md7-': Read-only file system
rm: cannot remove `md8-': Read-only file system
mknod: `md8-': Read-only file system
rm: cannot remove `md8-': Read-only file system
rm: cannot remove `md9-': Read-only file system
mknod: `md9-': Read-only file system
rm: cannot remove `md9-': Read-only file system
rm: cannot remove `md10-': Read-only file system
mknod: `md10-': Read-only file system
rm: cannot remove `md10-': Read-only file system
rm: cannot remove `md11-': Read-only file system
mknod: `md11-': Read-only file system
rm: cannot remove `md11-': Read-only file system
rm: cannot remove `md12-': Read-only file system
mknod: `md12-': Read-only file system
rm: cannot remove `md12-': Read-only file system
rm: cannot remove `md13-': Read-only file system
mknod: `md13-': Read-only file system
rm: cannot remove `md13-': Read-only file system
rm: cannot remove `md14-': Read-only file system
mknod: `md14-': Read-only file system
rm: cannot remove `md14-': Read-only file system
rm: cannot remove `md15-': Read-only file system
mknod: `md15-': Read-only file system
rm: cannot remove `md15-': Read-only file system
rm: cannot remove `md16-': Read-only file system
mknod: `md16-': Read-only file system
rm: cannot remove `md16-': Read-only file system
rm: cannot remove `md17-': Read-only file system
mknod: `md17-': Read-only file system
rm: cannot remove `md17-': Read-only file system
rm: cannot remove `md18-': Read-only file system
mknod: `md18-': Read-only file system
rm: cannot remove `md18-': Read-only file system
rm: cannot remove `md19-': Read-only file system
mknod: `md19-': Read-only file system
rm: cannot remove `md19-': Read-only file system
rm: cannot remove `md20-': Read-only file system
mknod: `md20-': Read-only file system
rm: cannot remove `md20-': Read-only file system
rm: cannot remove `md21-': Read-only file system
mknod: `md21-': Read-only file system
rm: cannot remove `md21-': Read-only file system
rm: cannot remove `md22-': Read-only file system
mknod: `md22-': Read-only file system
rm: cannot remove `md22-': Read-only file system
rm: cannot remove `md23-': Read-only file system
mknod: `md23-': Read-only file system
rm: cannot remove `md23-': Read-only file system
rm: cannot remove `md24-': Read-only file system
mknod: `md24-': Read-only file system
rm: cannot remove `md24-': Read-only file system
rm: cannot remove `md25-': Read-only file system
mknod: `md25-': Read-only file system
rm: cannot remove `md25-': Read-only file system
rm: cannot remove `md26-': Read-only file system
mknod: `md26-': Read-only file system
rm: cannot remove `md26-': Read-only file system
rm: cannot remove `md27-': Read-only file system
mknod: `md27-': Read-only file system
rm: cannot remove `md27-': Read-only file system
rm: cannot remove `md28-': Read-only file system
mknod: `md28-': Read-only file system
rm: cannot remove `md28-': Read-only file system
rm: cannot remove `md29-': Read-only file system
mknod: `md29-': Read-only file system
rm: cannot remove `md29-': Read-only file system
rm: cannot remove `md30-': Read-only file system
mknod: `md30-': Read-only file system
rm: cannot remove `md30-': Read-only file system
rm: cannot remove `md31-': Read-only file system
mknod: `md31-': Read-only file system
rm: cannot remove `md31-': Read-only file system
done.

```

**However I still ran**```
sudo mdadm --assemble --scan
``` **and got the following message** ```
mdadm: /dev/md0 has been started with 4 drives.
```

**Ok next tried to mount /dev/md0**
```

sudo mount /dev/md0 /storage
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```**NOT good.**

```
dmesg | tail
[  428.516490] EXT2-fs error (device md0): ext2_check_descriptors: Block bitmap for group 6016 not in group (block 0)!
[  428.516499] EXT2-fs: group descriptors corrupted!

```

[B]
But the array looks fine as below....[/B]
```
 
sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Feb 18 09:11:38 2009
     Raid Level : raid5
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Feb 19 06:49:21 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : bc466bff:b1da7077:4b3af59d:ee0da17e (local to host xbmc-linux)
         Events : 0.938

    Number   Major   Minor   RaidDevice State
       0       8       81        0      active sync   /dev/sdf1
       1       8       97        1      active sync   /dev/sdg1
       2       8      113        2      active sync   /dev/sdh1
       3       8      129        3      active sync   /dev/sdi1

```

```

sudo fdisk -l /dev/md0

Disk /dev/md0: 1500.3 GB, 1500315451392 bytes
2 heads, 4 sectors/track, 366287952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

```

sudo mdadm --examine /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : bc466bff:b1da7077:4b3af59d:ee0da17e (local to host xbmc-linux)
  Creation Time : Wed Feb 18 09:11:38 2009
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Feb 19 06:50:02 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : eba542 - correct
         Events : 938

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       81        0      active sync   /dev/sdf1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8       97        1      active sync   /dev/sdg1
   2     2       8      113        2      active sync   /dev/sdh1
   3     3       8      129        3      active sync   /dev/sdi1

```

**Any suggestions where to go from here? Thanks in advance.**

---

### Post by Aenima99x on 2009-02-19
More info

```
sudo /sbin/dumpe2fs /dev/md0
dumpe2fs 1.41.3 (12-Oct-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          2a369bce-0965-4fe0-9ef0-e636f4b4f9ed
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      ext_attr resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
**Filesystem state:         not clean with errors**
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              61054976
Block count:              244190000
Reserved block count:     12209500
Free blocks:              240333705
Free inodes:              61054965
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      965
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Filesystem created:       Wed Feb 18 09:04:28 2009
Last mount time:          n/a
Last write time:          Thu Feb 19 06:49:21 2009
Mount count:              0
Maximum mount count:      22
Last checked:             Wed Feb 18 09:04:28 2009
Check interval:           15552000 (6 months)
Next check after:         Mon Aug 17 10:04:28 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Default directory hash:   half_md4
Directory Hash Seed:      29686c9f-cbbb-470e-8d57-211c8e452238
Journal backup:           inode blocks
**Bad blocks: 7962963, 11239763, 20480339, 23888211, 71663955, 78676307, 102400339, 214991187**
```

---

### Post by fjgaude on 2009-02-19
What does the **mdadm.conf** file show?

Also, if you wish, **umount** the array for sure, and do a file check on it:

```
sudo umount /dev/md0
```

```
sudo fsck -t ext3 /dev/md0
```

Let us know how you are doing.

---

### Post by Aenima99x on 2009-02-19
```
cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=bc466bff:b1da7077:4b3af59d:ee0da17e

# This file was auto-generated on Thu, 19 Feb 2009 06:44:14 -0800
# by mkconf $Id$

```

array is unmounted.

Currently running ```
e2fsck -y -b 98304 /dev/md0
```

---

### Post by fjgaude on 2009-02-19
Looks fine... notice my editing of the last post... do a file check on the unmounted array and see if repair is possible.

---

### Post by Aenima99x on 2009-02-19
> **fjgaude said:**
> Looks fine... notice my editing of the last post... do a file check on the unmounted array and see if repair is possible.

Haha...notice my edit of my last post. It's already running.

---

### Post by Aenima99x on 2009-02-19
:::fingers crossed::: 
I currently see A LOT of "Clone multiply claimed blocks" and dates that look good.

---

### Post by Aenima99x on 2009-02-19
Now showing a ton of Directory Corruption, but it appears to be salvaging/repairing it.

---

### Post by Aenima99x on 2009-02-19
Now connecting unattached inodes to lost+found......looking good I think \\:D/

---

### Post by fjgaude on 2009-02-19
Seems you had a drive that just about crashed... but see what happens after the check is fully over, if you can mount the array.

---

### Post by Aenima99x on 2009-02-19
Good & Bad news....

Good - e2fsck finished the repair and says everything is now clean. 
Good - Mdadm reports all is good. 
Good - /dev/md0 mounted on reboot. 
Good - The array shows 870 GB free out of 1.5 TB.

Bad? - There is only a Lost+Found folder in my array, but it lists almost 628,000 items in it.
Bad - Almost all of the items/folders show as 0 bytes in size.
Bad - The items that aren't folders are listed as either pipe, socket, character device, or block device???

Is my data dust? Any ideas on where to go from here?

[IMG]http://i101.photobucket.com/albums/m72/aenima99x/htpc/Folders.png[/IMG]

[IMG]http://i101.photobucket.com/albums/m72/aenima99x/htpc/Files.png[/IMG]

---

### Post by fjgaude on 2009-02-20
I don't know what to suggest other than start over, rebuild the array. But I would test each drive first, for likely one or more of them is bad.

---

