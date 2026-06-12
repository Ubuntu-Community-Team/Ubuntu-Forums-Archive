---
title: "[SOLVED] md5 putting raid together wrongly"
date: 2009-01-05
forum: Server Platforms
---

### Post by Exarch on 2009-01-05
I'm having a weird issue here. I upgraded Ubuntu from 7.10 to 8.10 over the new year. Everything went pretty fine, however after the installation one of the disks in my three disk raid 5 was marked as "failed". Even though I found it rather strange that a not even 1 year old disk should fail exactly during an upgrade I checked it with fsck and smartutils and found no errors.

Anyway, I let the disk rebuild and everything worked fine until the moment the rebuild had finished, when now another disk was failed. Again, checks found nothing.

I removed and readded the broken disk and let it rebuild. After the next rebuild, two disks were failed and the raid was hosed.

At that point I checked all three disks to be sure (no errors on any), deleted the raid and created a new one, then copied the data back from backup while it was rebuilding.

Again, everything worked perfectly until the raid was done rebuilding. The very second the rebuild was done, the entire raid broke again with two failed disks.

I checked mdadm.conf and the strange thing is that there's no assemble line at the bottom. However, when I reboot the computer, a raid is automatically created with the correct disks, however in stopped state.
If I manually stop that raid and assemble it, I get this error
```
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
```

Does anyone have an idea what could be happening here and how I get mdadm to act normally again? I suspect it's somehow mixing up incompatible configuration data from before and after the upgrade but how do I reset those (especially the UUID cache)?

Edit: stupid mistype in the title, and you can't edit titles here :(

---

### Post by fjgaude on 2009-01-05
What I would do is this: re-name or delete the /etc/mdadm/mdadm.conf file, remove **mdadm**, re-boot. Then reinstall mdadm then run this command:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file will be auto created.

If this doesn't work all I can think of is you actually have drives going bad. Let's hope not!

Please let us know how things work out.

---

### Post by Exarch on 2009-01-05
I removed mdadm with apt-get purge, and reinstalled it with apt-get install. During the installation I get pages of error messages like
```
mknod: `md0-': Read-only file system
rm: cannot remove `md0-': Read-only file system
rm: cannot remove `md1-': Read-only file system
```
which I definitely didn't get the first install. Did the uninstall go wrongly?

Anyway, mdadm still looks like it works, but the scan assemble only gives the old error message
```
root@shodan:~# mdadm --verbose --assemble --scan
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sda6: Device or resource busy
mdadm: /dev/sda6 has wrong uuid.
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: /dev/sda5 has wrong uuid.
mdadm: no RAID superblock on /dev/sda2
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 0.
mdadm: added /dev/sdc to /dev/md0 as 1
mdadm: added /dev/sdd to /dev/md0 as 2
mdadm: added /dev/sdb to /dev/md0 as 0
**mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.**
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda6: Device or resource busy
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: no recogniseable superblock on /dev/sda2
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
```

I had mdadm monitor running all the time before the upgrade so I know I didn't accidentially run with defective drive for months. It seems really unlikely that two drives would die at once, especially in a way that neither fsck nor smartutils would find...

---

### Post by fjgaude on 2009-01-05
During the last process you did re-name or delete the **mdadm.conf** file?

What makes you think the array is working?

Also could you show what **sudo fdisk -l** looks like?

And let us see [B]sudo mdadm -D /dev/md0
[/B]

---

### Post by Exarch on 2009-01-05
I tried to delete the /etc/mdadm folder with "rm -rf" but found out that "apt-get purge" apparently did it first.

The array was just created yesterday and worked perfectly while it was synching. Then on the second when the sync finished, it broke.

```
root@shodan:~$ fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008675d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9354    75135973+  83  Linux
/dev/sda2            9355       60801   413248027+   5  Extended
/dev/sda5           59464       60801    10747485   82  Linux swap / Solaris
/dev/sda6            9355       59463   402500479+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table
```

and a rather disappointing

```
root@shodan:~$ sudo mdadm -D /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
```

---

### Post by fjgaude on 2009-01-05
Okay, please show us the mdadm.conf file and your fstab file.

I'm sure there is something crossed here one way or the other.

---

### Post by Exarch on 2009-01-05
```
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
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=09c3207a:b38d74a8:964de427:e20f7b82

# This file was auto-generated on Mon, 05 Jan 2009 21:59:53 +0100
# by mkconf $Id$
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1d04ef6f-f839-4dd7-8414-88aad14edf28 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda6       /media/data     ext3    defaults        0       0
# /dev/sda5
UUID=132fe3fc-c47d-4779-905e-c340224f4d07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/md0        /media/raid     ext3    defaults        0       0
```

That's the two. But unless I'm really mistaken on how Unix disks work, the fstab can't really be at fault here, can't it?

---

### Post by fjgaude on 2009-01-05
All this looks normal.

Now try this:

```
sudo mdadm -E /dev/sdb
```

and see if the UUID is:

UUID=09c3207a:b38d74a8:964de427:e20f7b82

It should be the same for all drives of the array.

If it is then you might try to force the assemble of the array:

```
sudo mdadm --assemble -f /dev/md0
```

Oh, and you do have a mountpoint, /home/raid, for the array?

---

### Post by Exarch on 2009-01-06
The UUIDs are all correct. The forced assembly is rather disconcerting however
```
root@shodan:~$ mdadm --assemble --force /dev/md0
mdadm: forcing event count in /dev/sdc(1) from 21119 upto 21132
Segmentation fault
```

I'm beginning to think the 8.10 upgrade ruined something completely. I'll probably just use the Windows ME solution and reformat/reinstall.

---

### Post by fjgaude on 2009-01-06
Segmentation fault sounds like a disk issue, eh?

I have the same array from 7.04 through 8.10 without issue.

---

### Post by Exarch on 2009-01-06
Segmentation fault means that a protected mode application is trying to read or write to memory that doesn't belong to it. It usually means there's an uncaught bug in the application that causes it to write to some random address (most often 0x00000000) and doesn't have exception handling catch it.

If it was an error on the disk I'd expect mdadm to think it possible and wrap a try/catch around the code that might crash...

---

### Post by fjgaude on 2009-01-06
Well, still make sure all the drives are good. Try and see if there are any bad blocks on the drives:

```
sudo badblocks -sv /dev/sd[n][n]
```

If there are try to correct with:

```
sudo e2fsck -CO -p -f -v /dev/sd[n][n]
```

Make sure from the man pages my memory is accurate about the options. <smile>

I can't think of anything else.

---

### Post by Exarch on 2009-01-09
I did the drive checks at the first sign of trouble and they were all peachy.

So I now zeroed out the superblocks, formatted my system drive and reinstalled 8.04 on it, then put mdadm on it and recreated the array. This time it synched perfectly and has been working for two days.

I'm assuming it was some issue maybe with the kernel or libc. I know that Ibex hasn't exactly received the most thorough beta testing so I'd guess it was an incompatibility somewhere. I'll wait for 9.04 and see if that turns out better. But the next time I'll definitely image my system drive before doing an upgrade :D

Anyway, thanks for the help in this thread!

---

### Post by fjgaude on 2009-01-09
Well, sometimes it is hard to say what is wrong and we re-install everything then it all works.

I've had no trouble with **mdadm** since I started using it with 6.04. Still using the same array, if you can believe that.

Learned as I went along by testing odd drives off-line, but always with full backups, in fact three backups.

Happy you have things working fully now.

---

