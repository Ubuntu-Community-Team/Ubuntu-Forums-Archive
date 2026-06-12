---
title: "raid 5 data recovery help - etx3 bad superblock"
date: 2009-03-05
forum: Server Platforms
---

### Post by Atanvarno on 2009-03-05
I have a linux raid-5 array (partitions: sda2, sdb2, sdc2, sdd2) which has been working for months. Using Ubuntu 8.04 server (fully updated).

I think the server then got turned off at the wall without a shutdown. After it booted again mdadm reported sdc as having failed. mdstat then spend ~3 hours recovering it (it did this automatically). Now the array is heathly (no errors from sdc), however when I try to mount it I'm informed the ext3 file system is corrupted.

```

~$ sudo mount /dev/md0 /mnt/raid
[ 1411.906999] EXT3-fs error (device md0): ext3_check_descriptors: Block bitmap 
for group 0 not in group (block 62914560)!
[ 1411.954495] EXT3-f: group descriptors corrupted!
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail or so

```

```

~$ dmsg | tail
[...]
[   98.681506] EXT3-fs error (device md0): ext3_check_descriptors: Block bitmap 
for group 0 not in group (block 62914560)!
[   98.790470] EXT3-fs: group descriptors corrupted!
[ 1411.906999] EXT3-fs error (device md0): ext3_check_descriptors: Block bitmap 
for group 0 not in group (block 62914560)!
[ 1411.954495] EXT3-f: group descriptors corrupted!

```

I used dumpe2fs to get a list of my backup superbocks.
```

~$ sudo dumpe2fs /dev/md0 | grep superblock
  Primary superblock at 0, Group descriptors at 1-87
  Backup superblock at 32768, Group descriptors at 32769-32855
  Backup superblock at 98304, Group descriptors at 98305-98319
[etc...]

```

However, I can't fix it with fsck (I think this is because it's a raid device, not a real disk).
```

~$ sudo fsck -b 32768 /dev/md0
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Device or resource busy while trying to open /dev/md0
File system mounted or opened exclusively by another program?

```

Don't know where to go from here.

Am I right in thinking my data is still recoverable? (Raid 5 has those parity stripes, so even if something is corrupted it should be rebuildable?)

---

### Post by khelben1979 on 2009-03-05
I think that [this old thread]("http://www.linuxquestions.org/questions/linux-software-2/debian-raid-5-rebuild-457098/") from LinuxQuestions.org might be of interest to you here.

---

### Post by Atanvarno on 2009-03-05
Are you saying I should delete the existing raid array definition, and then recreate the array?

Will this fix the file system problem?

---

### Post by khelben1979 on 2009-03-05
I have no knowledge myself on how to fix your problem here. I made a simple google search on your problem.

---

### Post by fjgaude on 2009-03-05
I trust your array is unmounted when you try to **fsck** it?

---

### Post by Atanvarno on 2009-03-05
Array is active but not mounted, according to webmin.

---

### Post by fjgaude on 2009-03-05
```
~$ sudo fsck -b 32768 /dev/md0
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Device or resource busy while trying to open /dev/md0
File system mounted or opened exclusively by another program?
```

Seems the array is mounted... what does **df -h** show?

In the **fsck** command line, what does the **-b** do... looking for higher superblock? /dev/md0 is a device, an array of drives.

You have actually done this:

```
sudo umount /dev/md0
```

Try it if you haven't, then do a simple:

```
sudo fsck /dev/md0
```

And let us know what happens.

---

### Post by Atanvarno on 2009-03-05
```
~$ df -h
Filesystem   Size  Used Avail Use% Mounted on
/dev/sdb2    2.8G  741M  2.0G  28% /
varrun       506M  180K  506M   1% /var/run
varlock      506M     0  506M   0% /var/lock
udev         506M   72K  506M   1% /dev
devshm       506M     0  506M   0% /dev/shm
/dev/sda2    2.8G   86M  2.7G   4% /boot

```
Using -b with fsck says Invalid non-numeric argument to -b ("/dev/md0").

unmounting /dev/md0 tells me it is not mounted.

```
~$ sudo fsck /dev/md0
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Group descriptors look bad... trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;

```

---

### Post by fjgaude on 2009-03-05
Gosh, it seems you have a very bad set, an array that cannot be fixed. Or can it?

Mount the array and show this:

```
sudo mdadm --detail /dev/md0
```

That might tell which drive is causing the issue. Then you examine each drive in the array:

```
sudo mdadm --examine /dev/sd[nn]
```

If we could take out the bad drive, fault it, remove it with **mdadm** then we might have a chance of getting it going again.

I guess you don't have backup of important data?

---

### Post by Atanvarno on 2009-03-05
Okay, here we go.
```

~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Mar  5 00:06:26 2009
     Raid Level : raid5
     Array Size : 1456356096 (1388.89 GiB 1491.31 GB)
  Used Dev Size : 485452032 (462.96 GiB 497.10 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Mar  5 20:09:56 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 4K

           UUID : 0c25f7d2:c3fd9e44:5fded89f:c0c2a7c2 (local to host george)
         Events : 0.36

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

```
Not sure which disk is gone from that, if any?

Oh, and no back-ups. None of it is strictly irriplacable, just inconvient, and I couldn't afford another 2TB of disks for backups.

---

### Post by fjgaude on 2009-03-05
Okay, there is data corruption, lost blocks... 

Try using different **-b** <superblock-address> with fsck, like 98304 and 163840 backups... I don't what else except a force check using the **-f** and **-v** options.

```
sudo tune2fs -l /dev/md0
```

Perhaps you try an assemble:

```
sudo mdadm --assemble --scan
```

And see what happens, see if you can mount.

What does the **/etc/mdadm/mdadm.conf** file look like?

---

