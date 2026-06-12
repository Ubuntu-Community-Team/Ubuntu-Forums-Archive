---
title: "zpool files corrupted?"
date: 2011-08-05
forum: Server Platforms
---

### Post by gratou on 2011-08-05
I replaced a dead disk in my Z1 pool (zpool replace) and while the resilvering was taking place, status -v was giving me :
[SIZE="1"]
status: One or more devices has experienced an error resulting in data
	corruption.  Applications may be affected.
action: Restore the file in question if possible.  Otherwise restore the
	entire pool from backup.
   see: [http://www.sun.com/msg/ZFS-8000-8A](http://www.sun.com/msg/ZFS-8000-8A)
 scrub: resilver in progress for 0h51m, 58.65% done, 0h36m to go
config:

	NAME                                                            STATE     READ WRITE CKSUM
	tank                                                            ONLINE       0     0     0
	  raidz1-0                                                      ONLINE       0     0     0
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806394-part1    ONLINE       0     0     3  5.62M resilvered
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806579-part1    ONLINE       0     0     0
	    disk/by-id/scsi-SATA_WDC_WD20EARX-00_WD-WCC1H0148286-part1  ONLINE       0     0  226K  1.26G resilvered
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2H7J90B106586-part1    ONLINE       0     0     0
	    disk/by-id/scsi-SATA_ST2000DL003-9VT_5YD2TYRF-part1         ONLINE       0     0     0

errors: Permanent errors have been detected in the following files:
[/SIZE]

followed by a long list of files.



Now that the resilvering is finished, I get:
[SIZE="1"][FONT="Courier New"]
status: One or more devices has experienced an unrecoverable error.  An
	attempt was made to correct the error.  Applications are unaffected.
action: Determine if the device needs to be replaced, and clear the errors
	using 'zpool clear' or replace the device with 'zpool replace'.
   see: [http://www.sun.com/msg/ZFS-8000-9P](http://www.sun.com/msg/ZFS-8000-9P)
 scrub: resilver completed after 1h28m with 0 errors on Sat Aug  6 00:11:22 2011
config:

	NAME                                                            STATE     READ WRITE CKSUM
	tank                                                            ONLINE       0     0     0
	  raidz1-0                                                      ONLINE       0     0     0
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806394-part1    ONLINE       0     0     3  7.88M resilvered
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806579-part1    ONLINE       0     0     0
	    disk/by-id/scsi-SATA_WDC_WD20EARX-00_WD-WCC1H0148286-part1  ONLINE       0     0  373K  1.33G resilvered
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2H7J90B106586-part1    ONLINE       0     0     0
	    disk/by-id/scsi-SATA_ST2000DL003-9VT_5YD2TYRF-part1         ONLINE       0     0     0

errors: No known data errors[/FONT][/SIZE]

So the obvious question is: are some files corrupted or did zpool just display this list to scare me and managed to fix them as more resilvering took place?

A message like "Errors were corrected" would be more helpful than "An attempt was made to correct the error". If files need to be replaced, where do I get the list? If they don't need to be replaced, the "Permanent errors" and "unrecoverable error" messages are needlessly misleading and worrying.

Thanks a lot.

PS: I can't get a fixed-sized font to work on the forum.

---

### Post by blind2314 on 2011-08-06
> **gratou said:**
> I replaced a dead disk in my Z1 pool (zpool replace) and while the resilvering was taking place, status -v was giving me :
[SIZE="1"]
status: One or more devices has experienced an error resulting in data
	corruption.  Applications may be affected.
action: Restore the file in question if possible.  Otherwise restore the
	entire pool from backup.
   see: [http://www.sun.com/msg/ZFS-8000-8A](http://www.sun.com/msg/ZFS-8000-8A)
 scrub: resilver in progress for 0h51m, 58.65% done, 0h36m to go
config:

	NAME                                                            STATE     READ WRITE CKSUM
	tank                                                            ONLINE       0     0     0
	  raidz1-0                                                      ONLINE       0     0     0
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806394-part1    ONLINE       0     0     3  5.62M resilvered
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806579-part1    ONLINE       0     0     0
	    disk/by-id/scsi-SATA_WDC_WD20EARX-00_WD-WCC1H0148286-part1  ONLINE       0     0  226K  1.26G resilvered
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2H7J90B106586-part1    ONLINE       0     0     0
	    disk/by-id/scsi-SATA_ST2000DL003-9VT_5YD2TYRF-part1         ONLINE       0     0     0

errors: Permanent errors have been detected in the following files:
[/SIZE]

followed by a long list of files.



Now that the resilvering is finished, I get:
[SIZE="1"][FONT="Courier New"]
status: One or more devices has experienced an unrecoverable error.  An
	attempt was made to correct the error.  Applications are unaffected.
action: Determine if the device needs to be replaced, and clear the errors
	using 'zpool clear' or replace the device with 'zpool replace'.
   see: [http://www.sun.com/msg/ZFS-8000-9P](http://www.sun.com/msg/ZFS-8000-9P)
 scrub: resilver completed after 1h28m with 0 errors on Sat Aug  6 00:11:22 2011
config:

	NAME                                                            STATE     READ WRITE CKSUM
	tank                                                            ONLINE       0     0     0
	  raidz1-0                                                      ONLINE       0     0     0
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806394-part1    ONLINE       0     0     3  7.88M resilvered
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806579-part1    ONLINE       0     0     0
	    disk/by-id/scsi-SATA_WDC_WD20EARX-00_WD-WCC1H0148286-part1  ONLINE       0     0  373K  1.33G resilvered
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2H7J90B106586-part1    ONLINE       0     0     0
	    disk/by-id/scsi-SATA_ST2000DL003-9VT_5YD2TYRF-part1         ONLINE       0     0     0

errors: No known data errors[/FONT][/SIZE]

So the obvious question is: are some files corrupted or did zpool just display this list to scare me and managed to fix them as more resilvering took place?

A message like "Errors were corrected" would be more helpful than "An attempt was made to correct the error". If files need to be replaced, where do I get the list? If they don't need to be replaced, the "Permanent errors" and "unrecoverable error" messages are needlessly misleading and worrying.

Thanks a lot.

PS: I can't get a fixed-sized font to work on the forum.

I'm going to assume since this is in the Ubuntu forum that this is using ZFS-FUSE, and not a "proper' ZFS pool on a Sun/Oracle box. What does ```
 zpool scrub tank 
``` return? Note: That may take awhile depending on the size of your pool.

---

### Post by gratou on 2011-08-06
This does not look good. A scrub normally takes 6 hours.

```
status: One or more devices has experienced an unrecoverable error.  An
	attempt was made to correct the error.  Applications are unaffected.
action: Determine if the device needs to be replaced, and clear the errors
	using 'zpool clear' or replace the device with 'zpool replace'.
   see: http://www.sun.com/msg/ZFS-8000-9P
 scrub: scrub in progress for 10h55m, 23.91% done, 34h46m to go
config:

	NAME                                                            STATE     READ WRITE CKSUM
	tank                                                            ONLINE       0     0     0
	  raidz1-0                                                      ONLINE       0     0     0
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806394-part1    ONLINE       0     0     0
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806579-part1    ONLINE       0     0     0
	    disk/by-id/scsi-SATA_WDC_WD20EARX-00_WD-WCC1H0148286-part1  ONLINE       0     0 10.7M  339G repaired
	    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2H7J90B106586-part1    ONLINE       0     0     0
	    disk/by-id/scsi-SATA_ST2000DL003-9VT_5YD2TYRF-part1         ONLINE       0     0     0

errors: No known data errors
```

While no data errors are found so far, the whole thing seems to be a mess. Furthermore, I would expect no errors to be found on the disk just after a replace since the disk has just been freshly written to. 

I think what was written by the replace command should have no parity errors, but might still not be an exact replica of the replaced disk considering the messages during resilvering. In other words, the resilvering would find data errors, but would not write those errors; rather it would write its best guess and write correct (in the scrub and parity senses) data.

That's why I'd like to know what these resilvering messages exactly imply.

Thanks for your insight.

---

### Post by gratou on 2011-08-06
Oh, and yes it is Ubuntu. 
If I recall correctly, solaris has /dev/dsk, not /dev/disk and no /dev/disk/by-id at all. :)

---

### Post by blind2314 on 2011-08-07
> **gratou said:**
> Oh, and yes it is Ubuntu. 
If I recall correctly, solaris has /dev/dsk, not /dev/disk and no /dev/disk/by-id at all. :)

Yes, of course. Sigh. The pathetic part is I'm a current Unix administrator, with our primary systems running Sol8-10. This is what happens when you don't sleep.

The resilvering messages are very unhelpful, I agree with that...and sadly, even in Solaris 11, they don't get any more useful. Out of curiosity, have you tried clearing the errors on the pool? I know the general consensus most people have with "clear" commands is that they don't ever work..but I have personally had to deal with a situation similar to yours. After being on the phone with Oracle support for 2+ hours, I decided to give it a try, and turns out that's all that was needed. It's worth a shot.

Ok, so besides that, one more command for me.

```
zpool iostat -v tank
```  (you might need to grep out only the effected disk, this can produce a LOT of output)

---

### Post by gratou on 2011-08-08
No that much output:
```
                                          capacity     operations    bandwidth
pool                                    alloc   free   read  write   read  write
--------------------------------------  -----  -----  -----  -----  -----  -----
tank                                    6.94T  2.12T    270      4  32.3M  13.6K
  raidz1                                6.94T  2.12T    270      4  32.3M  13.6K
    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806394-part1      -      -    142      3  8.24M  3.70K
    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806579-part1      -      -    142      3  8.24M  3.70K
    disk/by-id/scsi-SATA_WDC_WD20EARX-00_WD-WCC1H0148286-part1      -      -     70     84  8.25M  8.03M
    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2H7J90B106586-part1      -      -    142      3  8.24M  3.70K
    disk/by-id/scsi-SATA_ST2000DL003-9VT_5YD2TYRF-part1      -      -    139      2  8.24M  3.71K
--------------------------------------  -----  -----  -----  -----  -----  -----

```

If I had your knowledge, I'd use nexenta or opensolaris or openindiana, but I couldn't find easy-to-use interfaces like Disk Utility. This fuse-ZFS stuff does not inspire me confidence at all. I think I am screwed and will never know if I lost data until I try to use it. :(

---

### Post by blind2314 on 2011-08-08
> **gratou said:**
> No that much output:
```
                                          capacity     operations    bandwidth
pool                                    alloc   free   read  write   read  write
--------------------------------------  -----  -----  -----  -----  -----  -----
tank                                    6.94T  2.12T    270      4  32.3M  13.6K
  raidz1                                6.94T  2.12T    270      4  32.3M  13.6K
    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806394-part1      -      -    142      3  8.24M  3.70K
    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806579-part1      -      -    142      3  8.24M  3.70K
    disk/by-id/scsi-SATA_WDC_WD20EARX-00_WD-WCC1H0148286-part1      -      -     70     84  8.25M  8.03M
    disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2H7J90B106586-part1      -      -    142      3  8.24M  3.70K
    disk/by-id/scsi-SATA_ST2000DL003-9VT_5YD2TYRF-part1      -      -    139      2  8.24M  3.71K
--------------------------------------  -----  -----  -----  -----  -----  -----

```If I had your knowledge, I'd use nexenta or opensolaris or openindiana, but I couldn't find easy-to-use interfaces like Disk Utility. This fuse-ZFS stuff does not inspire me confidence at all. I think I am screwed and will never know if I lost data until I try to use it. :(

Something else that came to mind. Did you format the disk and/or lay down a fresh VTOC before you tried to attach it to your pool? If not, that could be where your problems are coming from; ZFS expects a disk with only 2 slices, slice 0 and slice 2, to have any size (and they must both be identical, i.e., the entire capacity of the disk), and the rest of the slices to be 0 size. Zpool replace and zpool attach don't lay this down for you, it must be done ahead of time.

---

### Post by gratou on 2011-08-08
Yes, I always format the disk and then use gparted to create a partition:
>unit s                      

>mkpart primary ext4 2048 3906248704 
so all disks are the very same (and start aligned on 4K blocks).



Also, I'll open a new thread on nexenta. If you don't mind, I'd love it that you answered a couple of questions. :)

---

