---
title: "How to clean my /"
date: 2009-01-21
forum: Server Platforms
---

### Post by NarsilAnduril on 2009-01-21
Hello,

I have a small home server running hardy 386 server that has been build a long time ago with the folowing "orthodox" partitioning policy :

```

        /dev/sda1    pri    ext3    1GB    /
        /dev/sda2    ext    ext3    1GB    /boot
        /dev/sda3    ext    ext3    4GB    /var
        /dev/sda4    ext    ext3    10GB   /usr
        /dev/sda5    ext    ext3    10GB   /tmp
        /dev/sda6    ext    etx3    5GB    /opt
        /dev/sda7    ext    ext3    50Gb   /home
        /dev/sda8    pri    swap    4GB

```

/home is on a few other disks

My problem is quiet easy to find :

```

diego@pinguin:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sde1             950M  902M     0 100% /
varrun                760M  228K  760M   1% /var/run
varlock               760M  4.0K  760M   1% /var/lock
udev                  760M   84K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
/dev/sde5             950M   29M  873M   4% /boot
/dev/sde9              47G  5.3G   39G  12% /home
/dev/sde8             9.3G  150M  8.7G   2% /tmp
/dev/sde7             9.3G  689M  8.2G   8% /usr
/dev/sde6             3.7G  2.9G  676M  82% /var

```

the 950 M /dev/sde1 is a bit full ... but as far as I know, it contains 
/
/bin            3.7 M
/dev            125.1 k
/etc            6.4 M
/lib            76.6 M
/lost+found     16.0 k
/root           14.2 k
/sbin           9.6 M
/srv            4.0 k

that's only 88 M, so where are the 860 M missing ????

Could somebody help me to recover my server ? Any suggestion would be very appreciated !

Thanks

Diego

---

### Post by yoyoned on 2009-01-21
there may be a large file living in the root directory.  
```

cd /
ls -la

```

---

### Post by NarsilAnduril on 2009-01-21
No ...

```
diego@pinguin:/$ ls -la
total 92
drwxr-xr-x  21 root root  4096 2008-09-28 16:02 .
drwxr-xr-x  21 root root  4096 2008-09-28 16:02 ..
drwxr-xr-x   2 root root  4096 2009-01-17 21:29 bin
drwxr-xr-x   4 root root  4096 2009-01-20 22:43 boot
lrwxrwxrwx   1 root root    11 2008-09-28 15:59 cdrom -> media/cdrom
drwxr-xr-x  14 root root 14740 2009-01-17 21:35 dev
drwxr-xr-x  86 root root  4096 2009-01-20 23:11 etc
drwxr-xr-x   5 root root  4096 2008-10-05 11:19 home
drwxr-xr-x   2 root root  4096 2008-09-28 16:00 initrd
lrwxrwxrwx   1 root root    32 2008-09-28 16:02 initrd.img -> boot/initrd.img-2.6.24-19-server
drwxr-xr-x  13 root root 12288 2009-01-17 21:29 lib
drwx------   2 root root 16384 2008-09-28 15:59 lost+found
drwxr-xr-x   4 root root  4096 2008-09-28 15:59 media
drwxr-xr-x   6 root root  4096 2008-10-06 18:13 mnt
drwxr-xr-x   2 root root  4096 2008-10-11 22:47 opt
dr-xr-xr-x 115 root root     0 2009-01-17 21:34 proc
drwxr-xr-x   2 root root  4096 2008-11-26 06:49 root
drwxr-xr-x   2 root root  4096 2009-01-17 21:29 sbin
drwxr-xr-x   2 root root  4096 2008-09-28 16:00 srv
drwxr-xr-x  12 root root     0 2009-01-17 21:34 sys
drwxrwxrwt   8 root root  4096 2009-01-21 22:23 tmp
drwxr-xr-x  13 root root  4096 2008-10-05 21:12 usr
drwxr-xr-x  15 root root  4096 2008-09-28 16:04 var
lrwxrwxrwx   1 root root    29 2008-09-28 16:02 vmlinuz -> boot/vmlinuz-2.6.24-19-server

```

---

### Post by koenn on 2009-01-21
try
```
sudo du -h --max-depth=1 /

```

---

### Post by NarsilAnduril on 2009-01-22
```
diego@pinguin:~$ sudo du -h --max-depth=1 /
5.1G	/home
733G	/mnt
4.0M	/bin
104K	/dev
538M	/usr
12M	/boot
40K	/tmp
293M	/var
12K	/media
du: cannot access `/proc/20431/task/20431/fd/3': No such file or directory
du: cannot access `/proc/20431/task/20431/fdinfo/3': No such file or directory
du: cannot access `/proc/20431/fd/3': No such file or directory
du: cannot access `/proc/20431/fdinfo/3': No such file or directory
0	/proc
4.0K	/initrd
0	/sys
24K	/root
4.0K	/srv
16K	/lost+found
9.1M	/etc
9.0M	/sbin
4.0K	/opt
83M	/lib
739G	/

```

Hoho ! What's that : 
```
739G	/
```

---

### Post by koenn on 2009-01-22
I'd have a look at

733G	/mnt

---

### Post by aaron.d on 2009-01-22
the mnt is huge, but I assume another medium is mounted in there, since this is a small drive in a 386, no?

use the -x option with du to exclude file system traversal (it wont add to the tally any filesystem(partition) other than the one specified: i.e. '/')

```
sudo du -hx --max-depth=1 /
```

My GUESS is that you didnt mount one of your partitions when you created them, and so those directories are really on your root filesystem.

can you show us the results of:

```
cat /etc/fstab
```

and 

```
mount
```

---

### Post by NarsilAnduril on 2009-01-22
You're right, I have a local RAID volume and a distant NAS mounted in /mnt.

```
diego@pinguin:~$ sudo du -hx --max-depth=1 /
4.0K	/home
72K	/mnt
4.0M	/bin
0	/dev
4.0K	/usr
4.0K	/boot
4.0K	/tmp
4.0K	/var
12K	/media
0	/proc
4.0K	/initrd
0	/sys
24K	/root
4.0K	/srv
16K	/lost+found
9.1M	/etc
9.0M	/sbin
4.0K	/opt
83M	/lib
105M	/

```

So, that's in the 950M from /dev/sda1
72K	/mnt
4.0M	/bin
0	/dev
12K	/media
0	/proc
4.0K	/initrd
0	/sys
24K	/root
4.0K	/srv
16K	/lost+found
9.1M	/etc
9.0M	/sbin
83M	/lib
105M	/

105M in total (I guess the 105M from / are not to be added ?), nothing in /mnt

```
diego@pinguin:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eb30a021-7dd2-4b4b-b942-7222d2c005b5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e7bbad4a-0e12-4bba-bacf-3c695dd46cec /boot           ext3    relatime        0       2
# /dev/sda9
UUID=c45ac900-8957-43aa-9e73-da0dafa36500 /home           ext3    relatime        0       2
# /dev/sda8
UUID=dd3edb52-1cd3-48dc-82de-0c554bdaa4ed /tmp            ext3    relatime        0       2
# /dev/sda7
UUID=c5d4210c-1911-48cc-9234-168da4f79b5e /usr            ext3    relatime        0       2
# /dev/sda6
UUID=9237a544-1302-4ed3-bcbf-fb30dfc348b9 /var            ext3    relatime        0       2
# /dev/sda2
UUID=65efcd32-620f-45af-a66d-86a3108cf1c6 none            swap    sw              0       0

#RAID 5 local

# /dev/RAID5/movies
/dev/RAID5/movies	/mnt/movies	jfs	users	0	0

# /dev/RAID5/records
/dev/RAID5/records	/mnt/records	jfs	users	0	0

# /dev/RAID5/downloads
/dev/RAID5/downloads	/mnt/downloads	ext3	rw,noatime	0	0

# Partages smb cifs (NAS2)
//172.26.155.7/downloads /mnt/NAS2/downloads cifs credentials=/home/diego/.smbpasswd,uid=diego,gid=diego 0 0
//172.26.155.7/photos /mnt/NAS2/photos cifs credentials=/home/diego/.smbpasswd,uid=diego,gid=diego 0 0
//172.26.155.7/backup /mnt/NAS2/backup cifs credentials=/home/diego/.smbpasswd,uid=diego,gid=diego 0 0
//172.26.155.7/music /mnt/NAS2/music cifs iocharset=utf8,credentials=/home/diego/.smbpasswd,uid=diego,gid=diego,file_mode=0444,dir_mode=0555 0 0
//172.26.155.7/video /mnt/NAS2/video cifs iocharset=utf8,credentials=/home/diego/.smbpasswd,uid=diego,gid=diego,file_mode=0444,dir_mode=0555 0 0
//172.26.155.7/public /mnt/NAS2/public cifs credentials=/home/diego/.smbpasswd,uid=diego,gid=diego 0 0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

```
/dev/sde1 on / type ext3 (rw,relatime,errors=remount-ro)
proc diego@pinguin:~$ mount
on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
udev on /dev type tmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sde8 on /tmp type ext3 (rw,relatime)
/dev/sde7 on /usr type ext3 (rw,relatime)
/dev/sde6 on /var type ext3 (rw,relatime)
/dev/mapper/RAID5-movies on /mnt/movies type jfs (rw,noexec,nosuid,nodev)
/dev/sde5 on /boot type ext3 (rw,relatime)
/dev/sde9 on /home type ext3 (rw,relatime)
/dev/mapper/RAID5-records on /mnt/records type jfs (rw,noexec,nosuid,nodev)
/dev/mapper/RAID5-downloads on /mnt/downloads type ext3 (rw,noatime)
//172.26.155.7/downloads on /mnt/NAS2/downloads type cifs (rw,mand)
//172.26.155.7/photos on /mnt/NAS2/photos type cifs (rw,mand)
//172.26.155.7/backup on /mnt/NAS2/backup type cifs (rw,mand)
//172.26.155.7/music on /mnt/NAS2/music type cifs (rw,mand)
//172.26.155.7/video on /mnt/NAS2/video type cifs (rw,mand)
//172.26.155.7/public on /mnt/NAS2/public type cifs (rw,mand)

```

---

### Post by koenn on 2009-01-22
ok, i still don't see it. 
what does this show:
```
sudo fdisk -l
```

---

### Post by NarsilAnduril on 2009-01-22
```
diego@pinguin:/$ sudo fdisk -l
[sudo] password for diego: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c16d87a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a0ce5d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079b4b

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x561da6e7

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/md0: 1500.3 GB, 1500323119104 bytes
255 heads, 63 sectors/track, 182403 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c16d87a

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ac39d38

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         122      979933+  83  Linux
/dev/sde2            9244        9729     3903795   82  Linux swap / Solaris
/dev/sde3             123        9243    73264432+   5  Extended
/dev/sde5             123         244      979933+  83  Linux
/dev/sde6             245         730     3903763+  83  Linux
/dev/sde7             731        1946     9767488+  83  Linux
/dev/sde8            1947        3162     9767488+  83  Linux
/dev/sde9            3163        9243    48845601   83  Linux

Partition table entries are not in disk order

```

---

### Post by aaron.d on 2009-01-22
for one thing you have 50MB of reserve blocks, even the df output showed that:

```
/dev/sde1             950M  902M     0 100% /
```

notice the size difference, this is standard for ext3.

use tune2fs to fix this (and dumpe2fs to verify first):

```
sudo dumpe2fs /dev/sdXX | grep -i 'reserved block count'
``` where XX is the drive and partition #. (be careful to double check this is still sde1, or whatever.


then
```

sudo tune2fs -m0 /dev/sdXX 
``` where '0' is 0% reserved ... you can use a different number if you still want to reserve some blocks.

This still doesnt explain the rest, but I havent really had time to check the rest of your followups.

---

### Post by aaron.d on 2009-01-22
before following the advice above, I would actually recommend booting into single user mode and running an fsck on the / partition. Unless Im retarded, or too tired, it doesnt look like you are missing anything there. Try it and see anyway.

Also, have you deleted any files that would have been resident on the / fs? I have read that deleting files while an app still has the handle will not relinquish the space until the file handle is released (the process is restarted, generally). I would think this would NOT be the case for you since you have such a rigid partitioning scheme (and the usually suspects for this issue are log files, normally kept in /var), but you never know.

---

### Post by NarsilAnduril on 2009-01-23
The fsck is the next thing I was planing to try, but it's not so easy on a headless server ! I'll have to connect a screen and a keyboard first.

I did'nt delete anything in / and as far as I know, logs are located in /var. I do monitor /var for this and I don't have any problem there.

Could you explain me a little bit more about the dumpe2fs / tune2fs thing ? I don't understand it and understand is the initial condition to try something on my server :P

```
diego@pinguin:~$ sudo dumpe2fs /dev/sde1 | grep -i 'reserved block count'
dumpe2fs 1.40.8 (13-Mar-2008)
Reserved block count:     12249

```

Thanks

Diego

---

### Post by NarsilAnduril on 2009-01-23
Wait a minute !

I've just checked one more time :

```
diego@pinguin:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sde1             950M  123M  780M  14% /
varrun                760M  228K  760M   1% /var/run
udev                  760M   84K  760M   1% /dev
/dev/sde8             9.3G  150M  8.7G   2% /tmp
/dev/sde7             9.3G  687M  8.2G   8% /usr
/dev/sde6             3.7G  364M  3.2G  11% /var
/dev/sde5             950M   29M  873M   4% /boot
/dev/sde9              47G  5.3G   39G  12% /home

```

It looks like asking for free blocks just updated the count ! I now have 14% used in /dev/sde1, Did I find a bug in df ?

Anyway, I still would very appreciate explanations on dumpe2fs / tune2fs.

---

### Post by aaron.d on 2009-01-23
its hard to tell, but im thinking there was a file that got removed (cronjob?) at some point after your df and before all this, OR it was removed but still held by some process, which eventually died and freed your space.

dumpe2fs will "dump" all the info about an ext filesystem.

I would try to avoid running it with no arguments as really the most useful stuff is at the top and will pass you by pretty quick. This is why we either grep for strings we know we are looking for, or if you want all of the info right away try:
```

sudo dumpe2fs /dev/sdXX | head -n 45
``` (45 lines should get you the bulk of the info that is relevant before starting to describe all the group/block/inodes of the entire fs)

in the previous example I wanted you to figure out if you had a "Reserved block count", which I basically knew already from the first df.

you found:

```
Reserved block count:     12249
```

So we know some are "reserved". If you want to know how much real space those blocks really comprise, you need to also know your block size.

this can be obtained by doing:
```

sudo dumpe2fs /dev/sdXX |grep "Block size"

```
(the info will all be available in the "head", as i show above)

I dont know your block size, but it doesnt really matter. I know you were missing about 50 MB of space, and I know the most common block size is 4096B (or ~4kB). If I do the math, 12249 blocks x 4 = 48996kB free or ~48MB.

To FREE that space you have to use tune2fs. This can do a lot of powerful stuff so best to do some homework first:
```

man tune2fs
```

basically the only option you'll want right now is:

>        -m reserved-blocks-percentage
              Set the percentage of reserved filesystem blocks.

or if you want to set the actual block count:
> 
       -r reserved-blocks-count
              Set the number of reserved filesystem blocks.


 (in the case of wanting to get rid of them all, it would be basically the same '-m 0' OR '-r 0')

like I said, tune2fs is not something you want to play around with, so make sure you are only using one of the above options, and read the man pages.

as for why reserved blocks, well they are generally to stop your system from totally barfing if root cant do anything, write or touch small files etc.

see [http://ubuntuforums.org/showpost.php?p=1254271&postcount=4](http://ubuntuforums.org/showpost.php?p=1254271&postcount=4)

---

### Post by NarsilAnduril on 2009-01-23
Thanks aaron for your explanations, thanks everybody for your help.

Diego

---

### Post by aaron.d on 2009-01-23
np.

Honestly, since your root fs will generally not be near full, you can leave the reserved block as they are, it's certainly a good precaution to have in place. At best I would try lowering to 3%.

It's up to you, but I think fixing your original issue resolves any real space dilemma you may have had.

---

### Post by NarsilAnduril on 2009-01-23
I didn't tune the fs, just dumped it. Reserved block count is still 12249 and I'm going to keep this size (12249 x 4K = 48M, is that right ?)

---

### Post by aaron.d on 2009-01-24
yep.

---

