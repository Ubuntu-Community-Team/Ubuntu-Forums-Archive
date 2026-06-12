---
title: "ZFS native installed and working but s.l.o.w..."
date: 2011-01-20
forum: Server Platforms
---

### Post by pneumatic on 2011-01-20
[http://zfsonlinux.org/](http://zfsonlinux.org/)

I have everything up and running.  My zpool clocks in at over a gigabyte per second reads initially but then slows down to less than 10 megabytes per second.

I've tried reducing /sys/module/zfs/parameters/zfs_vdev_max_pending per this suggestion:

[http://letsgetdugg.com/2009/10/21/zfs-slow-performance-fix/](http://letsgetdugg.com/2009/10/21/zfs-slow-performance-fix/)

But this didn't do anything either.  I am using WD Velociraptors and the TLER is properly set.  I realize that most people don't even know that this is available but I thought that I would get this thread started so that google can index it (the zfsonlinux.org website does not have a forum and I have learned my lesson with mailing lists and spammers).

---

### Post by samosamo on 2011-01-22
ZFS linux port?  When did this happen?

Tell us about your disk controller.  And since you mention TLER, let me quote a post in a well respected forum that gives you a little more of a clue and what it is and when to use it:

> 
[http://hardforum.com/showthread.php?t=1500505](http://hardforum.com/showthread.php?t=1500505)

Do i need to use TLER or RAID edition harddrives?
No and if you use TLER you should disable it when using ZFS. TLER is only useful for mission-critical servers who cannot afford to be frozen for 10-60 seconds, and to cope with bad quality RAID controller that panic when a drive is not responding for multiple seconds because its performing recovery on some sector. Do not use TLER with ZFS!

Instead, allow the drive to recover its errors. ZFS will wait, the wait time can be configured. You won't have broken RAID arrays, which is common with Windows-based FakeRAID arrays.

---

### Post by pneumatic on 2011-02-06
samosamo,

I've tried both TLER-enabled and disabled with no luck.  Sorry for the delay - not much time to deal with this right now.  I'll just wait for others to sort it out.

I am using MVSAS controllers in a 36-bay Supermicro enclosure, for the record.  I've tried sticking a single drive on the onboard Intel ICH10 and that does the same thing so I am assuming that there must be some bugs in the code still.

For anyone who wants the native port, you need to get it here:

[http://kqstor.com/Home.aspx?page=home](http://kqstor.com/Home.aspx?page=home)

The one at the site above does not have a posix layer yet.  So you can't mount the file system in kernel mode.

---

### Post by Alvinator9000 on 2013-03-05
Mine is running slow too :/

```
root@Desktop-Ubuntu:~# zpool status  pool: DJAlvinT
 state: ONLINE
status: One or more devices has experienced an unrecoverable error.  An
	attempt was made to correct the error.  Applications are unaffected.
action: Determine if the device needs to be replaced, and clear the errors
	using 'zpool clear' or replace the device with 'zpool replace'.
   see: http://zfsonlinux.org/msg/ZFS-8000-9P
  scan: scrub in progress since Tue Mar  5 18:54:20 2013
    14.6G scanned out of 2.49T at 2.33M/s, 309h32m to go
    0 repaired, 0.57% done
config:


	NAME                                                      STATE     READ WRITE CKSUM
	DJAlvinT                                                  ONLINE       0     0     0
	  raidz1-0                                                ONLINE       0     0     0
	    ata-ST33000651AS_Z290ZVRW                             ONLINE       0     0     0
	    ata-WDC_WD10TPVT-00HT5T1_WD-WX41AA0V3007              ONLINE       0     0     0
	    ata-WDC_WD5000BEVT-22A0RT0_WD-WX31A2075245            ONLINE       0     0     0
	    ata-WDC_WD5000BEVT-22A0RT0_WD-WX61A80W0385            ONLINE       0     0     0
	    ata-ST95005620AS_5YX043EJ                             ONLINE       0     0     0
	    ata-ST33000651AS_Z290ZJND                             ONLINE       0     0     1
	logs
	  mirror-1                                                ONLINE       0     0     0
	    usb-LEXAR_JD_FIREFLY_0A4E9708210326050707-0:0-part1   ONLINE       0     0     0
	    usb-Kingston_DataTraveler_2.0_5B771A8000E9-0:0-part1  ONLINE       0     0     0


errors: No known data errors
```

And 
```
root@Desktop-Ubuntu:~# zpool iostat -v                                                             capacity     operations    bandwidth
pool                                                      alloc   free   read  write   read  write
--------------------------------------------------------  -----  -----  -----  -----  -----  -----
DJAlvinT                                                  2.50T   223G    101    161  12.3M  12.2M
  raidz1                                                  2.50T   223G    101    161  12.3M  12.2M
    ata-ST33000651AS_Z290ZVRW                                 -      -     26     51  2.26M  2.45M
    ata-WDC_WD10TPVT-00HT5T1_WD-WX41AA0V3007                  -      -     22     44  2.26M  2.45M
    ata-WDC_WD5000BEVT-22A0RT0_WD-WX31A2075245                -      -     24     50  2.26M  2.45M
    ata-WDC_WD5000BEVT-22A0RT0_WD-WX61A80W0385                -      -     24     50  2.26M  2.45M
    ata-ST95005620AS_5YX043EJ                                 -      -     25     49  2.26M  2.45M
    ata-ST33000651AS_Z290ZJND                                 -      -     22     44  2.26M  2.45M
logs                                                          -      -      -      -      -      -
  mirror                                                      0   460M      0      0      0      0
    usb-LEXAR_JD_FIREFLY_0A4E9708210326050707-0:0-part1       -      -      0      0      7      7
    usb-Kingston_DataTraveler_2.0_5B771A8000E9-0:0-part1      -      -      0      0      7      7
--------------------------------------------------------  -----  -----  -----  -----  -----  -----
```



I have tried WITH and WITHOUT both a SLOG and a Cache, neither of them help.

I have fast read/writes at 300MB/s but any more than my ram and it'll bog down to 4MB/s
If I restart the computer, I get back my 300MB/s but after I copy 10G (ram limit) I'll have no luck at all copying anything at any speed other than what a snail could do.

---

