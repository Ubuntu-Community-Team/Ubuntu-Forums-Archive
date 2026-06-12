---
title: "[SOLVED] Dell MD1000 Storage partition disappearing!"
date: 2008-02-22
forum: Server Platforms
---

### Post by insect on 2008-02-22
Hi,

I'm managing numerious Dell servers for my company. One has an MD1000 External enclosure with a Perc5e Raid controller... It has 15 of 500Gb sata drives in raid5. The OS is an Ubuntu Gutsy. I had a lot problem creating huge partitions, but finally i've managed to make them as it should be... The raid has two logical disks a 2Tb with one partition (sdb1) and a 4Tb with two (sdd1 - 100Gb, sdd2 - 4Tb)... Everything is all right with the smaller ones, but when i reboot, the 4Tb /dev/sdd2 partition just disappear... When i run cfdisk, it says FREE SPACE... I recreate the partition, mount it and everything is fine, no data loss, but if i reboot, it disappears again... Why is that? is there a limitation to the size, or what am i doing wrong? i'm really confused :s

---

### Post by faulkes on 2008-02-22
When you next reboot issue a:

```

sudo fdisk -l

```

and paste the output back here.

Would also be handy to see your /etc/fstab file.

Faulkes

---

### Post by insect on 2008-02-23
Hi,

so, here is the contents of my fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=cd0b0575-146e-488a-b55c-456bbeead2fe /               ext3    defaults,errors=remount-ro 0       1
# /dev/md1
UUID=c5713eb1-4a12-49f1-8e84-5643f9606819 /boot           ext3    defaults        0       2
# /dev/sdb1
UUID=b12e2bb0-b6fa-4a90-b604-db8aadc1f024 /tmp            ext3    defaults        0       2
# /dev/md2
UUID=d5974384-442f-45e3-bb34-c2ee61fc3664 /var            ext3    defaults        0       2
# /dev/sda1
UUID=5076771b-f63e-4cb4-b3c9-ade51352243f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sdc1	/mnt/MD1000/backup	reiserfs	defaults	0	0
/dev/sdd2	/mnt/MD1000/store	reiserfs	defaults	0	0
```


its almost the default except the last two lines...
and here is the fdisk -l output right now, when the 4T partition is alive:

```
Disk /dev/sda: 320 GB, 320070320640 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1         608     4883728   82  Linux swap
/dev/sda2             609        6201    44917740   fd  Lnx RAID auto
/dev/sda3            6202        6809     4875727   fd  Lnx RAID auto
/dev/sda4            6810       38913   257867347   fd  Lnx RAID auto

Disk /dev/sdb: 320 GB, 320070320640 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1         608     4883728   83  Linux
/dev/sdb2             609        6201    44917740   fd  Lnx RAID auto
/dev/sdb3            6202        6809     4875727   fd  Lnx RAID auto
/dev/sdb4            6810       38913   257867347   fd  Lnx RAID auto

Disk /dev/sdc: 1998 GB, 1998233072640 bytes
255 heads, 63 sectors/track, 242938 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1      242938  1951399453   83  Linux

Disk /dev/sdd: 4496 GB, 4496020300800 bytes
255 heads, 63 sectors/track, 546610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdd1               1       11912    95683108   83  Linux

Disk /dev/md2: 264 GB, 264056163840 bytes
255 heads, 63 sectors/track, 32103 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/md2p1               1       32104   257875348   83  Linux 

Disk /dev/md1: 4 GB, 4992744960 bytes
255 heads, 63 sectors/track, 607 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/md1p1               1         608     4883728   83  Linux 

Disk /dev/md0: 45 GB, 45995765760 bytes
255 heads, 63 sectors/track, 5592 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/md0p1               1        5593    44925741   83  Linux 

```

I can't just reboot, becouse of the peoples working on it right now, but you can imagine the same output... As you can see (or can't see) the /dev/sdd2 is already missing... but it's mounted:

```
/dev/md0 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/md1 on /boot type ext3 (rw)
/dev/sdb1 on /tmp type ext3 (rw)
/dev/md2 on /var type ext3 (rw)
/dev/sdc1 on /mnt/MD1000/backup type reiserfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/sdd2 on /mnt/MD1000/store type reiserfs (rw)
```

so it's wierd. the only tip is some incompatibility with huge filesystems, but i can't imagine how can i solve it... perhaps a 64bit version of the OS would do the trick?

---

### Post by faulkes on 2008-02-23
Although it shouldn't be needed what you may want to try is adding a specific UUID entry
for /dev/sdd2

You can find the uuid with the following command:
```

udevinfo -q env -n /dev/sdd2

```

That will spit out a line like ID_FS_UUID=b9bb1c3f-249d-4cca-ab90-3df74467463b

In /etc/fstab, comment out the /dev/sdd2 line and add a line which looks like

```

#/dev/sdd2	/mnt/MD1000/store	reiserfs	defaults	0	0
UUID=<ID_FS_UUID from udevinfo command>  /mnt/MD1000/store reiserfs defaults 0 0

```

Faulkes

---

### Post by insect on 2008-02-23
I've already tried that before, with no change... The point is, that the partition is not visible for the OS, dispite the cfdisk command create the device node, so i can mount it, after the reboot, the device node disappear becouse of evident reasons... now i backed up the data and tried to mkfs to the whole /dev/sdd without any partitions... the server is rebooting, we'll see what happens...

---

### Post by insect on 2008-02-23
Hmm, it seems, that this solved the problem... It's a bit strange, that the fdisk -l shows me this:

```
Disk /dev/sdd: 4496 GB, 4496020300800 bytes
255 heads, 63 sectors/track, 546610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdd1               1      546611    95685530   83  Linux 
```

but i don't have /dev/sdd1 as written, only the whole device /dev/sdd... i can mount it, i can write it, even after reboot... 
```
/dev/sdd on /mnt/MD1000/store type reiserfs (rw)

```

i hope it'll be fine... thanks for the help!

---

### Post by jbaxley14 on 2008-04-09
> **insect said:**
> Hmm, it seems, that this solved the problem... It's a bit strange, that the fdisk -l shows me this:

```
Disk /dev/sdd: 4496 GB, 4496020300800 bytes
255 heads, 63 sectors/track, 546610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdd1               1      546611    95685530   83  Linux 
```

but i don't have /dev/sdd1 as written, only the whole device /dev/sdd... i can mount it, i can write it, even after reboot... 
```
/dev/sdd on /mnt/MD1000/store type reiserfs (rw)

```

i hope it'll be fine... thanks for the help!

Hey, i am having a similar issue.  I am also using Gusty server, with a MD1000 external RAID array, i have all the drives in it setup to be one RAID 5 virtual disk.

I can see the vd with parted and with fdisk, i was wondering if you could go through your creation steps, as i am getting unreadable super blocks on boot.  note the vd of the MD1000 isn't the boot partition, it is just being used for data.

any help you could give would be great!

---

### Post by insect on 2008-04-09
hi! as i remember, i didn't even created a partition table to that harddrive... i've only removed the whole partition table with fdisk, and did an ```
mkfs.reiserfs /dev/sdd
``` (without any numeral arguments for the device)... so i've got a pure filesystem without the possibility to create more than one filesystem to that device... i hope this helps ;)

---

