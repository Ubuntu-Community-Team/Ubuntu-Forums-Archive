---
title: "ZFS corruption after reboot"
date: 2013-02-22
forum: Server Platforms
---

### Post by platinumpt on 2013-02-22
I rebooted my home server this morning, and it didn't automatically mount the ZFS pool I have had running for quite a while, so I exported, and tried to import it.

There's no errors on boot, just loads up the ZFS module as normal:
ZFS: Loaded module v0.6.0.97-rc14, ZFS pool version 5000, ZFS filesystem version 5

I get this when I try to import it:

> sudo zpool import
   pool: tank
     id: 8409724759773078346
  state: FAULTED
 status: One or more devices contains corrupted data.
 action: The pool cannot be imported due to damaged devices or data.
   see: [http://zfsonlinux.org/msg/ZFS-8000-5E](http://zfsonlinux.org/msg/ZFS-8000-5E)
 config:

	tank        FAULTED  corrupted data
	  raidz1-0  ONLINE
	    sda     UNAVAIL  corrupted data
	    sdb     UNAVAIL  corrupted data
	    sdc     UNAVAIL  corrupted data
	    sdd     UNAVAIL  corrupted data

ZFS on linux suggests it's fatal, but is ZFS really that fragile?

---

### Post by rubylaser on 2013-02-23
If you've lost more disks than you have parity, then any RAID system will fail no matter how robust.  I don't think that's the case here, but you need to do more investigation. First, I would check each of those disks with smartctl first to determine if any of them have failed (or has a reallocated or pending sectors, or a bunch of UDMA CRC errors).

```
apt-get install smartmontools
smartctl -a /dev/sda
smartctl -a /dev/sdb
smartctl -a /dev/sdc
smartctl -a /dev/sdd
```

Then, I would try to remove the /etc/zfs/zpool.cache file, and try to import using disk-by-id like this
```
zpool import -d /dev/disk/by-id -f tank
```

---

### Post by Alvinator9000 on 2013-03-05
I think what may be happening is you are using the /sda .. b ... c things instead of pointing to drives using the /dev/disk/by-id/xxxxxxxxxxxxx <<(long name that is unique to each drive)
The by-id name will stay across reboots, the /sda values may change across reboots because of which drive your mobo decides to address first.  This shouldn't matter if you have JUST zfs going and NO other drives, but say you have another file system that is two disks, and you have a 3 disk raid z1 across /sda /sdb /sdc and your other fs is /sdd /sde, well across reboots your mobo may just feel like addressing the other fs first and it'll be /sda /sdb and zfs later as /sdc /sdd /sde, well now when zfs loads, it'll see that /sda and /sdb are NOT zfs, well then it'll freak out and say "hey, um, I'm faulted".

Here is the best guide I know around for ubuntu zfs, you can add your emails to your comments too on his site, he won't spam you but you may get some VERY useful info if he decides to email you as he once did me.  
[http://pthree.org/2012/04/17/install-zfs-on-debian-gnulinux/](http://pthree.org/2012/04/17/install-zfs-on-debian-gnulinux/)

...and more specific about your /sda vs /by-id lists: 
[http://pthree.org/2012/12/06/zfs-administration-part-iii-the-zfs-intent-log/](http://pthree.org/2012/12/06/zfs-administration-part-iii-the-zfs-intent-log/) right under the heading of "Adding a SLOG", um the "\" between devices is not necessary, it just marks on his page that the text line continues to the next line but is wrapped because it doesn't fit because its so long.

Hope this helps some :)

...ps, using the by-id, you can usually switch a disk between controllers at will, even moving them to external enclosures if you feel so inclined.

---

### Post by Alvinator9000 on 2013-03-05
...oh and show us the output of "zpool status", that'll help
In the terminal you can select and right click and copy

For example, here's mine: To use the code box, add "[ c o d e ]" in front (without the spaces or quotes) and "[ / c o d e ]" after also without spaces or quotes, just figured out that now :)
```

root@Desktop-Ubuntu:~# zpool status
  pool: DJAlvinT
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


Um, as you can see, my speeds are at a VERY slow pace and I'm troubleshooting that as best I can, don't want to hijack the thread though so don't mention it :)

---

