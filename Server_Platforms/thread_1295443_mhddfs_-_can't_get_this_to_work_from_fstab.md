---
title: "mhddfs - can't get this to work from fstab"
date: 2009-10-19
forum: Server Platforms
---

### Post by gobbledigook on 2009-10-19
hi!

trying out [mhddfs]("http://manpages.ubuntu.com/manpages/karmic/man1/mhddfs.1.html") and can get it to work from cli fine.... but for some reason it just won't work from fstab :(

any ideas? am i just going blind!?!? 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=022570b1-427d-48ab-bed4-719133203358 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd5
UUID=3a2781bd-eace-4a90-a2a3-11b8b06eb4c6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sda1
#/dev/sda1      /media/movies-and-other-stuff   auto    defaults        0       0
# /dev/sdb1
#/dev/sdb1      /media/swap     auto    defaults        0       0
# /dev/sdc1
#/dev/sdc1      /media/series   auto    defaults        0       0
#mhddfs
mhddfs#/media/movies-and-other-stuff/movies-music-and-stuff,/media/swap/swap/,/media/series/series /media/server/ fuse logfile=/var/log/mhddfs.log 0 0

```

```
server@server:~$ sudo mount mhddfs
mount: can't find mhddfs in /etc/fstab or /etc/mtab

```

---

