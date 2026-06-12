---
title: "software raid woes"
date: 2009-04-11
forum: Server Platforms
---

### Post by nex9 on 2009-04-11
I'm trying to get a software raid 10 set up in ubuntu 8.10 and having some issues. This is for a non-boot/system set of drives.

I was able to create the raid with:
mdadm -v --create /dev/md0 --level=raid10 --raid-devices=4 /dev/sda1 /dev/sdc1 /dev/sdd1 /dev/sde1

Then mkfs.ext3 and mount it. The array fully sync'ed according to /proc/mdstat.

The problem is that it is not working after I reboot the box. After reboot, /proc/mdstat shows:
Personalities : [raid10]
unused devices: <none>
mdadm --detail /dev/md0

and
mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.

At this point, I have to do a

mdadm --assemble --verbose --run /dev/md0

which seems to fix things. Any idea why this is happening?

Thanks!

---

### Post by fjgaude on 2009-04-12
I think you have to auto mount the array with a line in your /etc/fstab file:

```
/dev/md0 /mountpoint ext3 defaults 0 2
```

You do have a mountpoint?

---

### Post by nex9 on 2009-04-12
Thanks for the response, but I've just been trying to manually mount it. Behaviour following a reboot is as follows:

cat /proc/mdstat
Personalities : [raid10] 
unused devices: <none>
root@linux-quad:~# mount /dev/md0 /data -t ext3
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@linux-quad:~# mdadm --assemble --scan
mdadm: /dev/md0 has been started with 4 drives.
root@linux-quad:~# mount /dev/md0 /data -t ext3


I would expect /proc/mdstat to show an active raid device right after reboot, but it's not doing that. My raid partitions are of type "FD" (Linux raid autodetect), so I would expect everything to be auto-detected & started upon reboot, but that's not happening. Very frustrating. Any other ideas?

Thanks!

---

### Post by fjgaude on 2009-04-13
Well, place this line as the last one in your /etc/fstab file:

```
/dev/md0 /data ext3 defaults 0 2
```

That should have the array mount at boot up.

I believe just because you have an array setup it is not auto mounted without a line to do so in the fstab file.


Also after mounting what does this show:

```
sudo mdadm -D /dev/md0
```

---

### Post by nex9 on 2009-04-18
I get this during a reboot if I have that line in /etc/fstab:

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Invalid argument while trying to open /dev/md0^M
/dev/md0:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Also:

mdadm -D /dev/md0
mdadm: md device /dev/md0 does not appear to be active.

mdadm --assemble --scan
mdadm: /dev/md0 has been started with 4 drives.
root@linux-quad:/var/log/fsck# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Apr 12 16:24:14 2009
     Raid Level : raid10
     Array Size : 16048768 (15.31 GiB 16.43 GB)
  Used Dev Size : 8024384 (7.65 GiB 8.22 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Apr 13 07:23:28 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2, far=1
     Chunk Size : 64K

           UUID : 465177d9:168e40e8:134a5b84:9888814b (local to host linux-quad)
         Events : 0.6

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1

---

### Post by fjgaude on 2009-04-18
Gosh, everything looks fine... do you have a mountpoint at /raid? If not do this:

```
sudo mkdir /raid
```

That should do it, if your array is formatted to ext3 filesystem.

---

### Post by Underpants on 2009-04-18
I have a lot of good MDADM info in this thread: [http://ubuntuforums.org/showthread.php?t=998389](http://ubuntuforums.org/showthread.php?t=998389)

---

