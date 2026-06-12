---
title: "Problems with RAID5"
date: 2012-01-15
forum: Server Platforms
---

### Post by MikeDanger on 2012-01-15
We have a webserver with a RAID5 setup. A disk failed recently, and we opened up the case to remove it.

After identifying the disk and removing it, we received a message that no boot devices were available. We put the drive back in and got the machine to boot.

However, we now have an unusual problem: the webserver is functioning normally, but when we attempt to interact with the RAID array, we get the following messages:

```
melliott@babbage:~$ sudo mdadm -D /dev/md3
[sudo] password for melliott: 
mdadm: md device /dev/md3 does not appear to be active.
melliott@babbage:~$ sudo mdadm -A /dev/md3
mdadm: no devices found for /dev/md3

```

When we looked in the syslog, we found a recent message stating:

```
Jan 15 15:31:16 babbage kernel: [  380.295791] md: md3 still in use.
```

It seems strange that we can read data off the array (the site is being served normally), but that we can't interact with the array through the mdadm tool.

---

### Post by mattxhand on 2012-01-15
Well, this is a perfect defense to my argument against exotic RAID arrays on production systems.

It looks like your boot partition is on the dead drive and it isn't used for much else. It may be able to function and serve normally, but it's a time bomb. 

Your best bet imho is to get all of the data from the dead disk and copy it over to a new disk.

---

### Post by rubylaser on 2012-01-15
> **mattxhand said:**
> Well, this is a perfect defense to my argument against exotic RAID arrays on production systems.

It looks like your boot partition is on the dead drive and it isn't used for much else. It may be able to function and serve normally, but it's a time bomb. 

Your best bet imho is to get all of the data from the dead disk and copy it over to a new disk.

How is RAID5 "exotic" in a production environment?  It is a very common in enterprise environments to deploy on RAID arrays both for throughput and redundancy.

OP, what's the output of this.
```
cat /proc/mdstat
```
and
```
mount
```
and
```
mdadm --detail /dev/md0
mdadm --detail /dev/md1
mdadm --detail /dev/md2
mdadm --detail /dev/md3
```

I'm assuming since your device is /dev/md3, you have 3 other arrays on this machine, but this assumption could obviously be wrong.

---

### Post by a2j on 2012-01-16
boot on RAID5? grub was installed to one of the drives in that raid array? what *fdisk -l* says?

---

### Post by MikeDanger on 2012-01-16
Yes, we are booting from the RAID. (In our defense, this was a server we inherited.)

Output of cat /proc/mdstat:
```
melliott@babbage:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : inactive sdb[0](S) sdc[3](S)
      17852352 blocks
       
unused devices: <none>
```

Output of mount:
```
melliott@babbage:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
140.232.101.133:/home on /home type nfs (rw,nosuid,nodev,nfsvers=3,addr=140.232.101.133)
```

Output of mdadm --detail /dev/md3 (the other md devices do not, in fact, exist):
```
melliott@babbage:~$ sudo !!
sudo mdadm --detail /dev/md3
[sudo] password for melliott: 
mdadm: md device /dev/md3 does not appear to be active.
```

Output of fdisk -l:
```
melliott@babbage:~$ sudo fdisk -l

Disk /dev/sda: 73.4 GB, 73407820800 bytes
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b7c12

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8797    70661871   83  Linux
/dev/sda2            8798        8924     1020127+  82  Linux swap / Solaris

Disk /dev/sdb: 9105 MB, 9105018880 bytes
64 heads, 32 sectors/track, 8683 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x000bbd7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8683     8891376   fd  Linux raid autodetect

Disk /dev/sdc: 9175 MB, 9175979520 bytes
255 heads, 63 sectors/track, 1115 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00002396

   Device Boot      Start         End      Blocks   Id  System
```

Does anything stick out to anyone? Thanks for your time and attention.

---

### Post by a2j on 2012-01-16
is that full output of *fdisk -l* ?
and what about *df -hT* ?

---

### Post by MC1000 on 2012-01-16
Did you actually remove the disk via the console (as detailed here, first reply: [http://ubuntuforums.org/showthread.php?t=1639651](http://ubuntuforums.org/showthread.php?t=1639651)) before physically removing the failed disk?

---

### Post by MikeDanger on 2012-01-16
We did not remove the disk via the console as the disk was removed when the computer was shut off.

That is the full output of fdisk -l. The output of df -hT follows:

```

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3     67G  7.4G   56G  12% /
udev         tmpfs    1.3G  224K  1.3G   1% /dev
none         tmpfs    1.3G     0  1.3G   0% /dev/shm
none         tmpfs    1.3G   84K  1.3G   1% /var/run
none         tmpfs    1.3G     0  1.3G   0% /var/lock
none         tmpfs    1.3G     0  1.3G   0% /lib/init/rw
140.232.101.133:/home
               nfs    677G  246G  397G  39% /home
```

---

### Post by rubylaser on 2012-01-16
> **MC1000 said:**
> Did you actually remove the disk via the console (as detailed here, first reply: [http://ubuntuforums.org/showthread.php?t=1639651](http://ubuntuforums.org/showthread.php?t=1639651)) before physically removing the failed disk?

I like seeing my own directions linked to :) But, in this case, you don't have to use mdadm to remove the disk first for it to still work correctly.

To MikeDanger, your /etc/fstab does not show the RAID array being mounted anywhere and it doesn't show up under mounts, so it's not mounted. Also, it's not active as can be seen by the output of cat /proc/mdstat.

What's the output of this?
```
cat /etc/mdadm/mdadm.conf
```

Assuming your web directory is in /var/www (the default directory for Apache to serve from), that is on /dev/sda1.  If it's in /home, it's mounted via NFS from the other machine that shows up in /etc/fstab (140.232.101.133).  Sounds like you need to do a little more research to really understand how this is setup and working.

---

### Post by MC1000 on 2012-01-16
This may sound silly but, are you sure this is a RAID5 array? And are you sure it's even being used?

Because if /dev/sdc is the failed drive and what you posted is indeed the full output of "cat /proc/mdstat", then I don't see how it could be a RAID5 array?!

<edit> As above, i think more investigation may be required...</edit>

*Edit:* Beaten to it and described far more eloquently by rubylaser

---

### Post by a2j on 2012-01-17
> **rubylaser said:**
>   Sounds like you need to do a little more research to really understand how this is setup and working.

this :)

---

