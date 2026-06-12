---
title: "e2fsck reports device as busy with -b parameter"
date: 2008-05-10
forum: Server Platforms
---

### Post by karlmk on 2008-05-10
Hi

I will try to explain my problem here.

I got a LVM LV that is formated with ext3 ( think it actually is ext2 after I ran e2fsck the first time). My problem is that this LV is corruped. When I run e2fsck I get this:

```

root@Server100:~# e2fsck /dev/Data_VG/Data 
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Group descriptors look bad... trying backup blocks...
Superblock has an invalid ext3 journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

Corruption found in superblock.  (blocks_count = 0).

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 32768 <device>

```

Ok, I got a bad superblock. bad for me, so let's see if I got a backup somewhere on the partition then:

```

root@Server100:~# mke2fs -n /dev/Data_VG/Data 
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
54943744 inodes, 219774976 blocks
10988748 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
6707 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848

```

So e2fsck was correct, I got a backup on 32768 that I can try:

```

root@Server100:~# e2fsck -b 32768 /dev/Data_VG/Data 
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/Data_VG/Data
Filesystem mounted or opened exclusively by another program?

```

Now it reports that it is busy?!

If I try to mount the file system I get this:

```

root@Server100:~# mount /dev/Data_VG/Data /data/
mount: wrong fs type, bad option, bad superblock on /dev/mapper/Data_VG-Data,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Ok, then let me try to mount it a bit more specific:

```

root@Server100:~# mount -t ext3 -o sb=32768 /dev/Data_VG/Data /data/
mount: wrong fs type, bad option, bad superblock on /dev/mapper/Data_VG-Data,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@Server100:~# mount -t ext2 -o sb=32768 /dev/Data_VG/Data /data/
mount: wrong fs type, bad option, bad superblock on /dev/mapper/Data_VG-Data,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Same message.


Here is some info about stuff, if you need anything else, just tell me.

```

root@Server100:~# uname -r
2.6.24-16-server

root@Server100:~# dpkg -l |grep e2fsprogs
ii  e2fsprogs                                  1.40.8-2ubuntu2               ext2 file system utilities and libraries

root@Server100:~# mount --version
mount (util-linux-ng 2.13.1)

root@Server100:~# mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


root@Server100:~# pvscan 
  PV /dev/sdb1   VG Data_VG   lvm2 [232.88 GB / 0    free]
  PV /dev/sdd1   VG Data_VG   lvm2 [186.30 GB / 0    free]
  PV /dev/sde1   VG Data_VG   lvm2 [186.30 GB / 0    free]
  PV /dev/sdc1   VG Data_VG   lvm2 [232.88 GB / 0    free]
  Total: 4 [838.38 GB] / in use: 4 [838.38 GB] / in no VG: 0 [0   ]

root@Server100:~# vgscan 
  Reading all physical volumes.  This may take a while...
  Found volume group "Data_VG" using metadata type lvm2

root@Server100:~# lvscan 
  ACTIVE            '/dev/Data_VG/Data' [838.38 GB] inherit

root@Server100:~# dmesg |tail
[  560.684971] EXT2-fs error (device dm-0): ext2_check_descriptors: Block bitmap for group 128 not in group (block 0)!
[  560.685012] EXT2-fs: group descriptors corrupted!
[  570.609727] EXT3-fs error (device dm-0): ext3_check_descriptors: Block bitmap for group 128 not in group (block 0)!
[  570.610463] EXT3-fs: group descriptors corrupted!
[ 1032.715629] VFS: Can't find an ext2 filesystem on dev dm-0.
[ 1043.963282] VFS: Can't find ext3 filesystem on dev dm-0.
[ 3616.220601] EXT3-fs error (device dm-0): ext3_check_descriptors: Block bitmap for group 128 not in group (block 0)!
[ 3616.221367] EXT3-fs: group descriptors corrupted!
[ 3678.622513] VFS: Can't find ext3 filesystem on dev dm-0.
[ 3690.372891] VFS: Can't find an ext2 filesystem on dev dm-0.


```

So what I wonder is why do e2fsck report the device as busy just when I give it the -b parameter? I am a bit lost here, and any help would be appreciated.

Thanks alot for taking the time to read all this :)

Karl

---

### Post by grytpype on 2008-05-12
I am having the same problem right now, so I hope someone out there has an answer!

---

### Post by edwardecl on 2008-05-18
I am also having the same problem, I have a suspected bad superblock although I can mount my drive after numerous attempts but am not able to recover some data, when i use the -b parameter is says the device is busy... even though it is not mounted and works just fine without the -b parameter.

Someone has to know a solution to this ^^. Oh and it is a SATA 500GB drive on a PCI SATA card.

---

### Post by EtniesBMX on 2008-05-31
I'm also having the same problem. :confused:

I have a 30 GB Samsung IDE.

---

### Post by windependence on 2008-05-31
Make sure you are not in the directory you are trying to fsck. It will be busy if you are in the mount. You can also try unmounting it with umount -l. The file system does not have to be mounted to fsck.

-Tim

---

### Post by don_xvi on 2008-06-07
Same basic problem as the OP with a RAID (which is itself built on top of an LVM disk).
I had a system lockup and on the reboot it's now refusing to recognize the RAID array, same problems with telling me to re-run e2fsck -b with a backup location and then says the device is busy or mounted, although it's not mounted.  Very similar outputs to what's in the first post.

---

### Post by monge13 on 2008-08-11
Hi all,
I have the same problem, anybody has found some solution?
Thanks!

---

### Post by mbannach on 2008-09-09
Hi, try adding the blocksize specification (e.g. -B 4096). Guess e2fck does not do the fancy block size guessing once you get specific regarding the supblock location.

Have fun.

Matthias

---

### Post by tytso on 2008-09-09
Turns out the fact that "e2fsck -b 32768 /dev/XXX" didn't work was a bug that I accidentally introduced in e2fsprogs 1.40.7 when I was trying to make the error messages printed ext2fs_open() failed more descriptive.  Oops.   I've fixed this in the e2fsprogs git repository, and it will be fixed in the next maintenance release of e2fsprogs, which is e2fsprogs 1.41.2.  For now, the workaround is to manually specify the blocksize.  My apologies for the bug and not catching it earlier.   Many thanks to Matthias for pointing this thread out to me; I might have missed it otherwise!

P.S.  If you're not sure if something is a bug, feel free to post a query in the e2fsprogs's SourceForge forums or as a bug in SourceForge's bug trackkers.  I do try to pay attention to Debian BTS, SourceForge bug tracker, and Ubuntu's Launchpad --- although to be honest Launchpad gets lower priority since there are too many Ubuntu Launchpad bugs that are obviously either user error or kernel errors, and there is not enough Launchpad triage going on, so as a result I tend to give more priority to Debian BTS and SourceForge Bug Tracker bugs.  Usually the submitters at BTS and SF tend to give more information that is useful in tracking down the bug, and there are fewer bugs that are obviously the fault of some other package.  In general, though, a well formed, easily reproducible bug report is one I'll pay attention no matter how it comes to my attention.  It's just unfortunate that proportionally speaking there are much fewer of those coming in via Launchpad, and not enough help with the bug triage on Launchpad....

---

### Post by tytso on 2008-09-09
P.P.S.  If someone had brought this to my attention even three weeks earlier, the fix would have made it into e2fprogs 1.41.1, and if the May 2008 question had been made to e2fsprogs's SF forums or SF Bug Tracker (or even Ubuntu Launchpad) at that time, it would have been fixed in e2fsprogs 1.41.0, and it would have been fixed in time for Ubuntu Intrepid.  

Ah, well....  Thanks again to Matthias for bringing this thread to my attention.

---

