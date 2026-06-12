---
title: "zfs on Ubuntu 12.04 file system needed?"
date: 2012-06-21
forum: Server Platforms
---

### Post by djroketboy on 2012-06-21
So i've installed zfs support on my Ubuntu 12.04 server. I have created my first RAID2Z pool, but have one question that I can't seem to find the answer to.

Do I need another filesystem on top of the pool? I've seen conflicting threads and how-to's, some create their pool with ext4, some say its not needed.

After I created my pool, it automatically mounted off root (/) and I can copy files to/from it. I just want to make sure that i'm doing it right as I really wouldn't like to lose any data because of something stupid i've done.

```
  pool: xraid
 state: ONLINE
 scan: none requested
config:

	NAME        STATE     READ WRITE CKSUM
	xraid       ONLINE       0     0     0
	  raidz2-0  ONLINE       0     0     0
	    sdc     ONLINE       0     0     0
	    sdd     ONLINE       0     0     0
	    sde     ONLINE       0     0     0
	    sdf     ONLINE       0     0     0
	    sdg     ONLINE       0     0     0
	    sdh     ONLINE       0     0     0
	    sdi     ONLINE       0     0     0
	    sdj     ONLINE       0     0     0
	    sdk     ONLINE       0     0     0
	    sdl     ONLINE       0     0     0
	    sdm     ONLINE       0     0     0
	    sdn     ONLINE       0     0     0
	    sdo     ONLINE       0     0     0
	    sdp     ONLINE       0     0     0

errors: No known data errors
```

---

### Post by ian dobson on 2012-06-21
Hi,

What do you see when you type mount?

You should see something like:-
```

/dev/md0 on / type ext3 (rw,noatime,nodiratime,commit=30)
udev on /dev type devtmpfs (rw,mode=0755)
/dev/md1 on /data type ext4 (rw,noatime,nodiratime,commit=30,barrier=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

bur with type zfs rather than ext4

Under linux there is usually several layers (drive/block device, mapper lvm or md, file system ext3/4). ZFS combines the upper two layers (mapper and fs) into one monolithic block. As the file system knows exactly how the drives are layed out in theory zfs should be quicker than the layered linux model.

Regards
Ian Dobson

---

### Post by rubylaser on 2012-06-21
No, ZFS is a RAID system, volume, and filesystem all in one.  Putting ext4 on top of it wouldn't make any sense, unless you where exporting a portion of it for ISCSI (you're not doing this) :)  

Everything looks good with your array. I'd just setup periodic snapshots, and make sure you have a backup system in place, because even the most robust fileystem/RAID setup does not replace a backup.

---

### Post by djroketboy on 2012-06-21
x

---

### Post by djroketboy on 2012-06-21
x

---

### Post by rubylaser on 2012-06-21
No you don't.  The Ubuntu mountall install in the ubuntu-zfs package will automount your array for you.  So, you're all set.  Enjoy your new array :)

---

### Post by djroketboy on 2012-06-21
x

---

### Post by thnewguy on 2012-06-24
I was wondering about the mount thing too. I found ZFS volumes/pools mount automatically, which is great. Really liking ZFS on Ubuntu Server.

---

### Post by herot on 2012-06-25
I am having trouble with getting ZFS working. I was able to install and create my pools, etc... here is what I have:

```

root@herot-ubu:/home/herot# zpool status
  pool: chalice
 state: ONLINE
 scan: none requested
config:

        NAME        STATE     READ WRITE CKSUM
        chalice     ONLINE       0     0     0
          raidz1-0  ONLINE       0     0     0
            sdb     ONLINE       0     0     0
            sdc     ONLINE       0     0     0

errors: No known data errors
root@herot-ubu:/home/herot#

root@herot-ubu:/home/herot# zpool list
NAME      SIZE  ALLOC   FREE    CAP  DEDUP  HEALTH  ALTROOT
chalice  59.5G   183K  59.5G     0%  1.00x  ONLINE  -

root@herot-ubu:/home/herot# zpool iostat
               capacity     operations    bandwidth
pool        alloc   free   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
chalice      183K  59.5G      0      0      0      0




Disk /dev/sdc: 500 GB, 500105249280 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux
Warning: Partition 1 does not end on cylinder boundary.
/dev/sdc9           60801       60802        8032   83  Linux
Warning: Partition 9 does not end on cylinder boundary.
root@herot-ubu:/home/herot#

Disk /dev/sdb: 32 GB, 32070366720 bytes
255 heads, 63 sectors/track, 3899 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3899    31318686   83  Linux
Warning: Partition 1 does not end on cylinder boundary.
/dev/sdb9            3899        3900        8032   83  Linux
Warning: Partition 9 does not end on cylinder boundary.

```

So, everything looks good I think. BUT when I try to do a :
```
root@herot-ubu:/chalice# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             230G  7.3G  211G   4% /
udev                  1.5G  4.0K  1.5G   1% /dev
tmpfs                 605M  860K  604M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.5G  148K  1.5G   1% /run/shm
/home/herot/.Private  230G  7.3G  211G   4% /home/herot

```

shouldn't /chalice show up?

---

### Post by rubylaser on 2012-06-25
It doesn't look like it's mounting.  If you're having a problem with the automount script not working, you can add the startup script to /etc/rc.local.

```
nano /etc/rc.local
```
and paste
```
zfs mount -a
```

reboot and it should automount for you.

---

### Post by djroketboy on 2012-06-25
x

---

### Post by herot on 2012-06-25
Yeah, that must be it. I typed:
```
automount
```

And it mounted. It was doing some wierd things earlier like becoming completely unresponsive after doing a simple ```
ls
```
It seems to be working fine now. Thanks.

---

### Post by herot on 2012-06-25
> **djroketboy said:**
> I could be wrong, but let zfs do everything for you. It prefers full disks. Wipe your type 83 partitions, and re-create your array. zfs will partition your drive, create the zfs filesystem, and mount it automatically.

Those disks had no partitions when I started. I think ZFS did that to them...?

---

### Post by djroketboy on 2012-06-25
x

---

### Post by herot on 2012-06-25
I'm still having problems with the ZFS pool. It stops responding and I can't copy files to it or even ls in it. It just locks up and I have to start a new terminal session.

```


herot@herot-ubu:/var/log$ dmesg |grep sdb
[    2.998122] sd 6:0:0:0: [sdb] 62652416 512-byte logical blocks: (32.0 GB/29.8 GiB)
[    2.998738] sd 6:0:0:0: [sdb] Write Protect is off
[    2.998744] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    2.999236] sd 6:0:0:0: [sdb] No Caching mode page present
[    2.999241] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.001986] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.001992] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.014818]  sdb: sdb1 sdb9
[    3.017343] sd 6:0:0:0: [sdb] No Caching mode page present
[    3.017349] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.017355] sd 6:0:0:0: [sdb] Attached SCSI removable disk
herot@herot-ubu:/var/log$ dmesg |grep sdc
[    3.160071] sd 7:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.160852] sd 7:0:0:0: [sdc] Write Protect is off
[    3.160860] sd 7:0:0:0: [sdc] Mode Sense: 00 38 00 00
[    3.161601] sd 7:0:0:0: [sdc] Asking for cache data failed
[    3.161607] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[    3.163980] sd 7:0:0:0: [sdc] Asking for cache data failed
[    3.163986] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[    3.196322]  sdc: sdc1 sdc9
[    3.200863] sd 7:0:0:0: [sdc] Asking for cache data failed
[    3.200869] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[    3.200875] sd 7:0:0:0: [sdc] Attached SCSI disk

```

---

### Post by djroketboy on 2012-06-25
x

---

