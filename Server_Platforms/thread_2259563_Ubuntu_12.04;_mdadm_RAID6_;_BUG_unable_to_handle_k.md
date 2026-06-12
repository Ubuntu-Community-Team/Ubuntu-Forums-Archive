---
title: "Ubuntu 12.04; mdadm RAID6 ; BUG unable to handle kernel NULL pointer dereference"
date: 2015-01-05
forum: Server Platforms
---

### Post by fermulator on 2015-01-05
Hey raid/mdadm/server/kernel experts;

I'm running Ubuntu server 12.04 w/ mdadm software RAIDs. Recently, one of the drives (sdj) is failing in md2000 array. At first I was trying to "get it back into the array", not realizing how "failed" it is. The system detects it fine, and mdadm starts rebuilding with it no problem. I leave it rebuilding for hours ...

But suddenly at some point later my server is locked up/hung, non-responsive. I Have to force a reboot.

For example: unable to handle kernel NULL pointer dereference

Take last night for example: [http://paste.ubuntu.com/9676667/](http://paste.ubuntu.com/9676667/)

@ around 12:30AM, this morning, I noticed the system was hung :( sigh.
I go down and reboot it. The logs shown there are from that point.

Due to the hung system, occasionally some other array needs to resync. (I don't see any "disk failures" in the logs about any of the drives contained within non-md2000 arrays).

So this time, the system boots, and starts repairing md250, AND md2000. I let it run, sleep time.

This morning I wake up, and again the system was hung :( sigh.

Check this out:
{{{
```
Jan  5 02:04:03 fermmy-server kernel: [ 5804.222842] md: md250: resync done.
Jan  5 02:04:03 fermmy-server kernel: [ 5804.364982] RAID1 conf printout:
Jan  5 02:04:03 fermmy-server kernel: [ 5804.368724]  --- wd:2 rd:2
Jan  5 02:04:03 fermmy-server kernel: [ 5804.371151]  disk 0, wo:0, o:1, dev:sdh3
Jan  5 02:04:03 fermmy-server kernel: [ 5804.373609]  disk 1, wo:0, o:1, dev:sdg3
```
}}}

Clearly, the system was working well for at least 1.5hrs. md250 completes its rebuild.

Yet this morning it's locked up. The last message we see is:
{{{
```
Jan  5 06:39:10 fermmy-server kernel: [22311.374866] EXT4-fs (md250): Unaligned AIO/DIO on inode 6817061 by AioMgr0-N; performance will be poor.
```
}}}

syslog the last message in syslog.0 before my reboot this morning is:
```
Jan  5 06:43:02 fermmy-server ntop[2298]:   **WARNING** packet truncated (8742->8232)
Jan  5 06:43:05 fermmy-server ntop[2298]:   **WARNING** packet truncated (13654->8232)
Jan  5 06:43:06 fermmy-server ntop[2298]:   **WARNING** packet truncated (15014->8232)
Jan  5 06:43:16  ntop[2298]: last message repeated 4 times
Jan  5 06:43:16 fermmy-server ntop[2298]:   **WARNING** packet truncated (13654->8232)
Jan  5 06:43:29  ntop[2298]: last message repeated 5 times
Jan  5 06:43:29 fermmy-server ntop[2298]:   **WARNING** packet truncated (15014->8232)
Jan  5 06:43:31 fermmy-server ntop[2298]:   **WARNING** packet truncated (13654->8232)
Jan  5 06:43:35  ntop[2298]: last message repeated 2 times
Jan  5 06:43:35 fermmy-server rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1433" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
```

Also, full dmesg output from the above "time": [http://paste.ubuntu.com/9676728/](http://paste.ubuntu.com/9676728/)

Doesn't seem interesting...

NOW, it's even worse, TWO drives are popped out of the RAID6 array. I risk data loss now :(
{{{
```
** WARNING: There appears to be one or more degraded RAID devices **

The system may have suffered a hardware fault, such as a disk drive
failure.  The root device may depend on the RAID devices being online. One
or more of the following RAID devices are degraded:
Personalities : [raid1] [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid10] 
md2000 : active raid6 sdo1[3] sdi1[4] sdn1[2] sdk1[0] sdl1[6] sdp1[7]
      11721080448 blocks super 1.1 level 6, 64k chunk, algorithm 2 [8/6] [U_UU_UUU]
      
md1002 : active raid1 sdg2[1] sdh2[0]
      1952704 blocks [2/2] [UU]
      
md250 : active raid1 sdh3[0] sdg3[1]
      233392960 blocks [2/2] [UU]
      
md1001 : active raid1 sdg1[1] sdh1[0]
      9764800 blocks [2/2] [UU]
      
md1000 : active raid5 sdd1[2] sdc1[1] sdb1[0] sda1[3]
      2930279808 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
md640 : active raid1 sde1[1] sdf1[0]
      625130708 blocks super 1.1 [2/2] [UU]
```
}}}

What should I do?
--> I'm MOST concerned about the system/kernel lockup in the middle of mdadm RAID resyncs :( -- this shouldn't be happening but I can't find any hints in the logs as to why
--> I'd like to understand/resolve this before proceeding with repairing md2000 missing disk (and ... why TWO disks now :(...)

EDIT: In the meantime during the day (while I'm at work); I've re-added the other drive into md2000 that (as far as I know) is NOT bad
```

Every 1.0s: cat /proc/mdstat                                                                                                   Mon Jan  5 09:17:03 2015

Personalities : [raid1] [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid10]
md2000 : active raid6 sdm1[8] sdo1[3] sdi1[4] sdn1[2] sdk1[0] sdl1[6] sdp1[7]
      11721080448 blocks super 1.1 level 6, 64k chunk, algorithm 2 [8/6] [U_UU_UUU]
      [>....................]  recovery =  0.8% (16927992/1953513408) finish=695.8min speed=46381K/sec


```

-

fermulator@fermmy-server:/var/log$ uname -a
Linux fermmy-server 3.2.0-74-generic-pae #109-Ubuntu SMP Tue Dec 9 17:00:00 UTC 2014 i686 i686 i386 GNU/Linux
fermulator@fermmy-server:/var/log$ cat /etc/issue
Ubuntu 12.04.4 LTS \n \l

fermulator@fermmy-server:/var/log$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise

fermulator@fermmy-server:/var/log$ dpkg --list | grep mdadm
ii  mdadm                                3.2.5-1ubuntu0.3                            tool to administer Linux MD arrays (software RAID)

---

### Post by MAFoElffen on 2015-01-05
This is what I saw:
```

md640  RAID1, 2 members sde1, sdf1;  Active
md1000 RAID5, 4 devices, sda1, sdb1, sdc1, sdd1; Active
md1001 RAID1, 2 members, sdg1, sdh1; Active, but had filesystem ext4 errors, recovery done on filesystem
md1002 RAID1, 2 members, sdg2, sdd2; Active
md2000 RAID6, 7 members, sdm1, sdo1, sdi1, sdn1, sdk1, , sdl1, sdp1; Active; sdm1, sdl1 now missing
md250  RAID1  2 members, sdh3, sdg3; Not clean -- starting background reconstruction , rsync done

```
md640, md1000, md1002 and md2000 came up Active. md250 was not clean and had to resysnc.

Besides the RAID Assemblies, the filesystem on md1001 had ext4 errors and did it's own filesystem recovery.

sdl1 and sdm1 dropped out of md2000... but the put looked like a crash, so those 2 disks probably got boinked and where not synceed at the time... So the cause of that would be what I would be curious on.

Not sure that the errors you showed were actual errors. The first ones were just normal  TCP retries(?) and most people ignore those via filters. The last showed was the log being rotated. But there might have been something else after that?

If you look at /var/crash/ and look for any file similar to linux-image-3.2.0-74-generic-pae.0.crash... Please post that dump file. If there isn't a dump file there, check to see if the kernel crash dump mechanism is enabled. Look at 
```

cat /proc/sys/kernel/sysrq

```
If it is 0, then 
```

sudo sysctl -w kernel.sysrq=1

```
(More info requested)

---

### Post by fermulator on 2015-01-05
Thanks for the detailed response  MAFoElffen,

Everything in the originally posted log/pastes should contain the full information. I agree it's surprising that there aren't any extra logs or hints as to why the system haults.

SysRq key is set:
```
fermulator@fermmy-server:/var/log$ cat /proc/sys/kernel/sysrq
1
```

There are no interesting cores though
```
fermulator@fermmy-server:/var/crash$ ls -al
total 684
drwxrwsrwt  2 root whoopsie   4096 Jan  5 06:25 .
drwxr-xr-x 14 root root       4096 Jan  4 12:19 ..
-rw-r-----  1 root whoopsie  11869 Jan  1 06:29 _usr_bin_deluge-web.0.crash
-rw-r-----  1 root whoopsie 678650 Jan  4 16:35 _usr_sbin_ntop.0.crash
```

NOTE: The /dev/md2000 array is in a really bad state now ([http://www.linuxquestions.org/questions/linux-server-73/mdadm-raid6-active-with-spares-and-failed-disks%3B-need-help-4175530127/](http://www.linuxquestions.org/questions/linux-server-73/mdadm-raid6-active-with-spares-and-failed-disks%3B-need-help-4175530127/)), but that isn't really the focus of this discussion.

I'm trying to focus this thread/discussion on why the OS is hanging during rebuilds sometimes.

---

