---
title: "rsyncing rsnapshots takes up too much space"
date: 2012-08-30
forum: Server Platforms
---

### Post by silbro on 2012-08-30
Hi everybody

I use rsnapshot for my backups. I don't directly back up to an external disk. I backup my data locally via rsnapshot and then rsync the rsnapshot to the usb disk. The usb disk is always full though. I think it doesn't back up the rsnapshots like they are, instead  backs up all of the data every time. Is that possible ? If yes, what could I do instead? I don't want to rsnapshot to the usb disk directly.

Thanks for all answers :) 

cheers
):P

---

### Post by gyzer on 2012-08-30
Why don't you want to do the rsnapshot to the drive directly? I've been using rsnapshot for several years now to a USB connected drive without issues.

---

### Post by silbro on 2012-09-01
The reason I don't want to do that is because I will be switching the USB disk and I want the Backup of my data to be local as well.

---

### Post by silbro on 2012-09-03
Ok I believe this was my problem (yes I'm ashamed of myself):

* 04 * * * /root/backup/rsynctousb.sh

instead of

0 04 * * * /root/backup/rsynctousb.sh

](*,)

If it works now (which I believe I will close the thread)

---

### Post by silbro on 2012-09-06
rsyncing still fills up all the space on my usb disk. Anyone have any ideas ?

---

### Post by LHammonds on 2012-09-06
I have to ask....how large is the total amount of space you are wanting to sync to the USB and what size is the USB...and is it dedicated for just that backup?

---

### Post by silbro on 2012-09-09
Hi LHammonds,

Thanks for your reply.

The rsnapshot backup is 213GB. My usb disk is 1.8 TB and yes it is only used for backups. df -T outputs this:

/dev/sdi1  fuseblk   1953511420 1952793420    718000 100% /usb_backup

Could it be that the problem is the type? (fuseblk). I think i formatted it as ntfs so I could just plug it into either linux or windows if I need a backup.

---

### Post by LHammonds on 2012-09-11
fuseblk is how Linux reports NTFS mounted drives so that is probably no problem at all.  However, a big part of the puzzle is exactly how much space is being consumed.  The block size being used and the amount/size of the files being backed up may not be matching up very well (e.g. very large block size but tons of super tiny files)

Type the following so we can see how big the folder is:

```
du -sh /path/to/usb
```Then list the contents of the drive where the snapshot files are being stored in order to get a feel for the size of each file over time.

```
ls -lh /path/to/usb
```or if all the files are over a GB,
```
ls -l --blocksize=g /path/to/usb
```

---

### Post by silbro on 2012-09-11
Hi LHammonds

/data1/backup/rsnapshot is where the rsnapshot writes to locally

```

sudo du -sh /data1/backup/rsnapshot/
213G    /data1/backup/rsnapshot/

```

```

du -sh /data1/backup/rsnapshot/daily.0
201G    /data1/backup/rsnapshot/daily.0

du -sh /data1/backup/rsnapshot/daily.1
203G    /data1/backup/rsnapshot/daily.1

du -sh /data1/backup/rsnapshot/daily.2
203G    /data1/backup/rsnapshot/daily.2

du -sh /data1/backup/rsnapshot/daily.3
203G    /data1/backup/rsnapshot/daily.3

du -sh /data1/backup/rsnapshot/daily.4
203G    /data1/backup/rsnapshot/daily.4

du -sh /data1/backup/rsnapshot/daily.5
203G    /data1/backup/rsnapshot/daily.5

du -sh /data1/backup/rsnapshot/daily.6
203G    /data1/backup/rsnapshot/daily.6

```

```

ls -lh /data1/backup/rsnapshot/
total 208K
drwxr-xr-x 6 root root 4.0K 2012-09-11 03:30 daily.0
drwxr-xr-x 6 root root 4.0K 2012-09-10 03:30 daily.1
drwxr-xr-x 6 root root 4.0K 2012-09-09 03:30 daily.2
drwxr-xr-x 6 root root 4.0K 2012-09-08 03:30 daily.3
drwxr-xr-x 6 root root 4.0K 2012-09-07 03:30 daily.4
drwxr-xr-x 6 root root 4.0K 2012-09-06 03:30 daily.5
drwxr-xr-x 6 root root 4.0K 2012-09-05 03:30 daily.6
drwxr-xr-x 6 root root 4.0K 2012-07-30 03:30 monthly.0
-rw-r--r-- 1 root root 156K 2012-09-11 03:30 rsnapshot.log
drwxr-xr-x 6 root root 4.0K 2012-09-03 03:30 weekly.0
drwxr-xr-x 6 root root 4.0K 2012-08-27 03:30 weekly.1
drwxr-xr-x 6 root root 4.0K 2012-08-20 03:32 weekly.2
drwxr-xr-x 6 root root 4.0K 2012-08-10 03:30 weekly.3

```

/usb_backup/backup is where the local rsnapshots I made are being rsynced to

```

du -sh /usb_backup/backup/rsnapshot/
1.6T    /usb_backup/backup/rsnapshot/

```

```

ls -lh /usb_backup/backup/rsnapshot/
total 160K
drwxrwxrwx 1 root root    0 2012-09-11 03:30 daily.0
drwxrwxrwx 1 root root    0 2012-09-10 03:30 daily.1
drwxrwxrwx 1 root root    0 2012-09-09 03:30 daily.2
drwxrwxrwx 1 root root    0 2012-09-08 03:30 daily.3
drwxrwxrwx 1 root root    0 2012-09-07 03:30 daily.4
drwxrwxrwx 1 root root    0 2012-09-06 03:30 daily.5
drwxrwxrwx 1 root root    0 2012-09-05 03:30 daily.6
drwxrwxrwx 1 root root 4.0K 2012-07-30 03:30 monthly.0
-rwxrwxrwx 1 root root 156K 2012-09-11 03:30 rsnapshot.log
drwxrwxrwx 1 root root    0 2012-09-04 04:00 weekly.0
drwxrwxrwx 1 root root    0 2012-09-04 04:00 weekly.1
drwxrwxrwx 1 root root    0 2012-09-04 04:00 weekly.2
drwxrwxrwx 1 root root    0 2012-09-04 04:00 weekly.3


```

```

du -sh /usb_backup/backup/rsnapshot/daily.0/
201G    /usb_backup/backup/rsnapshot/daily.0/

du -sh /usb_backup/backup/rsnapshot/daily.1
203G    /usb_backup/backup/rsnapshot/daily.1

du -sh /usb_backup/backup/rsnapshot/daily.2
203G    /usb_backup/backup/rsnapshot/daily.2

du -sh /usb_backup/backup/rsnapshot/daily.3
203G    /usb_backup/backup/rsnapshot/daily.3/

du -sh /usb_backup/backup/rsnapshot/daily.4
203G    /usb_backup/backup/rsnapshot/daily.4

du -sh /usb_backup/backup/rsnapshot/daily.5
203G    /usb_backup/backup/rsnapshot/daily.5

du -sh /usb_backup/backup/rsnapshot/daily.6
203G    /usb_backup/backup/rsnapshot/daily.6

```

I'm really starting to think, that rsyncing the rsnapshot somehow always copies all the files instead of just the links.

---

### Post by markbl on 2012-09-11
> **silbro said:**
> 
I'm really starting to think, that rsyncing the rsnapshot somehow always copies all the files instead of just the links.
Remember that rsnapshot works by using hardlinks to save space. Note that rsync does not preserve hardlinks by default with "-a". You must also specify "-H". See man rsync.

---

### Post by LHammonds on 2012-09-11
With the data you presented, it certainly looks like rsync is translating the links to physical files based on the sizes noted.

For this to work, you will need to pass the correct switches to rsync in order for it to preserve links.

Once you have it working right, make sure you can restore with what you have on USB and document it thoroughly and verify your documented procedure works as expected.  When (not if) disaster strikes and panic sets in, it is no time for guess work and crossing of fingers.  ;-)

LHammonds

---

### Post by silbro on 2012-09-12
Oh man!

This was my command with rsync:

```
if [ -e /usb_backup/usbbackup ];
then rsync -avz --delete /data1/backup/ /usb_backup/backup;
fi
```

So I forgot the -H option #-o

I will change this now and report back when the backup ran. Already a big thanks in advance for helping a newbie :)!!!

cheers

---

### Post by shreepads on 2012-09-12
Could you please share your full rsnapshot/ rsync scripts? Am planning something similar so would be useful for me!
Thanks!

---

### Post by silbro on 2012-09-12
Sure I'll share them once it's working fine. But remember that my scripts are very simple and basic ;) but I will share what I have done and if I have time I'll also take a look at how to mount the usb disks to the same place every time i plug them in :)

cheers

---

### Post by shreepads on 2012-09-13
> **silbro said:**
> Sure I'll share them once it's working fine. But remember that my scripts are very simple and basic ;) but I will share what I have done and if I have time I'll also take a look at how to mount the usb disks to the same place every time i plug them in :)

cheers

Well I have a solution to that bit (how to mount the usb disks to the same place every time i plug them in ), posted here:

[http://ubuntuforums.org/showpost.php?p=12221805&postcount=73](http://ubuntuforums.org/showpost.php?p=12221805&postcount=73)

Just add 'nofail' to the fstab mount options already listed there if you aren't going to leave it plugged in all the while. Won't break anything if you don't, will just hold up boot if the USB drive is not connected at boot, need to skip by hitting 'S'.

BTW what are you using for the USB drive? I've got a external USB 3.0 capable WD MyBook 2TB but my ancient mobo only supports USB 2.0 so have got a PCIe card (Transcend) for USB 3.0 support (fingers crossed that it works!).

---

### Post by silbro on 2012-09-13
> You must also specify "-H"

This did solve my problem. I'm so glad that this was it :) Thank you all again for helping me. 

If I have time I'll post all my scripts etc. this weekend.

---

### Post by silbro on 2012-09-16
Hey

I was sick this weekend and even had to work :( so I didn't have any time to post my scripts. I will do this sometime soon though. I always think it's fair to share the knowledge if you were helped :)

cheers

---

### Post by shreepads on 2012-09-25
OK did my own simples script...

Mounted WD MyBook 2TB external USB 3.0 drive (connected to Transcend PDU3 PCIe USB 3.0 expansion card), as follows in fstab

```
UUID=<insert UUID>	/media/WDMyBook	ext4	noauto,nodev,noatime,noexec,nosuid,rw,nouser	0	2
```

And then this script, just does a simple incremental backup, nothing fancy...

Must be run as root/ with sudo..

```

#!/bin/sh

# Simple rsync backup from SOURCE directories to TARGET mount point
# Excluding EXCLUDE, use OPTIONS
# Needs to be run as root, will fail with error if not
# Needs TARGET to be unmounted at start, will fail with error if not
# TARGET is mounted and subsequently unmounted once rsync completes

# Source directories
SOURCE="/home/user";

# Target mount point
TARGET="/media/WDMyBook";

# Exclude
EXCLUDE="/home/user/.thumbnails/*";

# Rsync options, other than SOURCE, TARGET, EXCLUDE, LOGFILE
# Just archive, verbose and stats. Can add --delete if needed
# Initially include test mode (--list-only) as well, remove once tested to work
OPTIONS='-av --stats --list-only';


#---- The script itself ---------------------------

# Make sure we're running as root
ID=`id -u`;
if [ $ID != 0 ]; then 
	echo "rsbackup.sh: `date` Sorry, must be root, current user id is $ID, exiting...";
	exit 1;
fi;


# Check if TARGET mounted, if yes, print error and exit
mountpoint $TARGET;
if [ $? = 0 ]; then
	echo "rsbackup.sh: `date` $TARGET is already mounted, exiting...";
	exit 1;
fi;

echo "rsbackup.sh: `date` $TARGET is not mounted, mounting..."

# Mount TARGET, stop if mount fails
mount -v $TARGET;
if [ $? != 0 ]; then
	echo "rsbackup.sh: `date` Failed mounting $TARGET, return code $?, exiting...";
	exit 1;
fi;

echo "rsbackup.sh: $TARGET is mounted, starting rsync"

# Rsync it
rsync $OPTIONS --exclude=$EXCLUDE $SOURCE $TARGET
if [ $? != 0 ]; then
	echo "rsbackup.sh: `date` Rsync failed, return code $?, exiting after unmount...";
else
	echo "rsbackup.sh: `date` Rsync succeeded, unmounting $TARGET..."
fi;


# Unmount TARGET
umount -v $TARGET
if [ $? != 0 ]; then
	echo "rsbackup.sh: `date` Error unmounting $TARGET, return code $?, exiting...";
	exit 1;
fi;

echo "rsbackup.sh: `date` $TARGET unmounted..."

exit 0;


```

---

