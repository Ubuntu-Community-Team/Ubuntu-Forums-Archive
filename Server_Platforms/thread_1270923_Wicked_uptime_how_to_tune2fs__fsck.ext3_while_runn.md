---
title: "Wicked uptime: how to tune2fs / fsck.ext3 while running?"
date: 2009-09-20
forum: Server Platforms
---

### Post by frenchn00b on 2009-09-20
Hello

How can people fix and automatic fsck.ext3 their disk while runnning ?

---

### Post by Bachstelze on 2009-09-20
Unmount, fsck, remount.

---

### Post by sisco311 on 2009-09-20
if it's a data partition, then just unmount it an run e2fsck:
```

sudo umount /dev/sdXY
sudo e2fsck -C0 -f -p -v /dev/sdXY

```

NOTE: that's a 0 (zero) in the command,** not** an uppercase o. 

if it's your /home partition, then boot in recovery mode(single user mode)(*sudo init 1*), unmount the partition and run e2fsck.

if it's the root ("/") partition, then force a check on reboot
```
sudo tune2fs -C 40 /dev/sdXY
sudo reboot
```

or boot a live cd and check the partition.

[COLOR="Red"]WARNING!!!  Running e2fsck on a mounted filesystem may cause
**SEVERE** filesystem damage.[/COLOR]

---

### Post by frenchn00b on 2009-09-20
can we use smartmontools ?

[http://www.howtoforge.org/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu](http://www.howtoforge.org/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu)

to fix my harddrive when it needs 
/   is /dev/hf1
/home is  /dev/hdf3


   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1        3039    24410736   83  Linux
/dev/hdf2            3040        3161      979965   82  Linux swap / Solaris
/dev/hdf3            7909       19457    92767342+  83  Linux
/dev/hdf4            3162        3191      240975    b  W95 FAT32


how to it work, so that it does fix my /home ?

---

### Post by KiLaHuRtZ on 2009-09-20
> **sisco311 said:**
> if it's your /home partition, then boot in recovery mode(single user mode)(*sudo init 1*), unmount the partition and run e2fsck.

You don't have to boot to single user for this, just 'cd' out of your home directory, unmount it, fsck it and re-mount.

```
cd /
sudo umount /home
sudo fsck -t [FS-TYPE] /dev/hdf3
sudo mount -a
cd ~
```

Where '[FS-TYPE]' is the file system type, most likely ext3.  But you can check in '/etc/fstab'.

---

### Post by frenchn00b on 2009-09-20
> **KiLaHuRtZ said:**
> You don't have to boot to single user for this, just 'cd' out of your home directory, unmount it, fsck it and re-mount.

```
cd /
sudo umount /home
sudo fsck -t [FS-TYPE] /dev/hdf3
sudo mount -a
cd ~
```

Where '[FS-TYPE]' is the file system type, most likely ext3.  But you can check in '/etc/fstab'.

seems that there isnt much solutions, but let's continue dreaming.

I found this:

> EXAMPLES
       smartctl -a /dev/hda
       Print all SMART information for drive /dev/hda (Primary Master).

       smartctl -s off /dev/hdd
       Disable SMART on drive /dev/hdd (Secondary Slave).

       smartctl --smart=on --offlineauto=on --saveauto=on /dev/hda
       Enable  SMART on drive /dev/hda, enable automatic offline testing every
       four hours, and enable autosaving of SMART Attributes.  This is a  good
       start-up line for your system´s init files.  You can issue this command
       on a running system.

       smartctl -t long /dev/hdc
       Begin an extended self-test of drive /dev/hdc.  You can issue this com&#8208;
       mand on a running system.  The results can be seen in the self-test log
       visible with the ´-l selftest´ option after it has completed.

       smartctl -s on -t offline /dev/hda
       Enable SMART on the disk, and begin an immediate offline test of  drive
       /dev/hda.  You can issue this command on a running system.  The results
       are only used to update the SMART Attributes,  visible  with  the  ´-A´
       option.  If any device errors occur, they are logged to the SMART error
       log, which can be seen with the ´-l error´ option.

       smartctl -A -v 9,minutes /dev/hda
       Shows the vendor Attributes, when the disk  stores  its  power-on  time
       internally in minutes rather than hours.

       smartctl -q errorsonly -H -l selftest /dev/hda
       Produces  output only if the device returns failing SMART status, or if
       some of the logged self-tests ended with errors.

       smartctl -q silent -a /dev/hda
       Examine all SMART data for device /dev/hda, but produce no printed out&#8208;
       put.  You must use the exit status (the $?  shell variable) to learn if
       any Attributes are out of bound, if the SMART  status  is  failing,  if
       there  are errors recorded in the self-test log, or if there are errors
       recorded in the disk error log.

       smartctl -a -d 3ware,0 /dev/sda
       Examine all SMART data for the first ATA disk connected to a 3ware RAID
       controller card.


[B]- are smartctl  and fsck.ext3 similar ?

- I think instead of EXT3, it could be use the FUSE. 
this one is extendable and it can be fixed, no?

- an idea:
some have experience with ?
in order to have your partitions checked at boot time, with placing a file called "forcefsck" in / and reboot.

- I know that google have a special format for their all disks, not ext3. Considering linux/or nix we have something in that direction
but dont recall what it is ... :( 

- Actually with the by including the ZFS filesystem BSD has an edge on Linux there.
That wont help with the driver situation though.

[/B]

- the choice could be UFS, or UFS with soft-updates?


Google have even their own partition type Fs. Looks that it works for google.
 

I think that solaris ZFS is better, but well why we still uses ext3/ext4
its old, out of fashion?
[http://en.wikipedia.org/wiki/List_of_file_systems](http://en.wikipedia.org/wiki/List_of_file_systems)

Come on, those BSD servers are a lot, what do they use to run their servers? 

Linux Server = problems
*BSD = what people are using for servers , real stuff,
no?

ext3, advanced:
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

---

### Post by sisco311 on 2009-09-21
> **KiLaHuRtZ said:**
> You don't have to boot to single user for this, just 'cd' out of your home directory, unmount it, fsck it and re-mount.

```
cd /
sudo umount /home
sudo fsck -t [FS-TYPE] /dev/hdf3
sudo mount -a
cd ~
```

Where '[FS-TYPE]' is the file system type, most likely ext3.  But you can check in '/etc/fstab'.

Theoretically yes, you have to stop all processes (including the X server) that are accessing the home directory.

Sometimes this is a real PITA, hence i suggested the single user mode. 

> **frenchn00b said:**
> seems that there isnt much solutions, but let's continue dreaming.


did you try to unmount the home partition in single user mode?

> **frenchn00b said:**
> 
- an idea:
some have experience with ?
in order to have your partitions checked at boot time, with placing a file called "forcefsck" in / and reboot.


when i last tried nether
```
> /forcefsck
```
nor
```
shutdown -rF now
```
worked for me.

from *man fstab*:
> [noparse]The  sixth field, (fs_passno), is used by the fsck(8) program to deter&#8208;
       mine the order in which filesystem checks are done at reboot time.  The
       root  filesystem  should  be specified with a fs_passno of 1, and other
       filesystems should have a fs_passno of 2.[/noparse]

you can set the mount count to <30 to force a filesystem check:
```

man tune2fs  # :)  
sudo tune2fs -C 99 /dev/sdXY
sudo reboot
```

---

