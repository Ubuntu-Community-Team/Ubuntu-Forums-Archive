---
title: "RAID 5 mdadm superblock and mount on boot help!"
date: 2008-11-15
forum: Server Platforms
---

### Post by Mercedes300 on 2008-11-15
Hi there. I have a software RAID 5 created with mdadm, I set up a file system with ```
mke2fs -j /dev/md0
``` Also edited /etc/fstab to mount /dev/md0 at boot, and edited /etc/mdadm/mdadm.conf to assemble the array. when I reboot, I get an error saying ```
fsck.ext3: Invalid argument while trying to open /dev/md0
/dev/md0
The superblock could not be read or does not describe a correct ext2 filesystem. 
If the device is valid and it really contains an ext2 filesystem (and not swap or ufs 
or something else), then the superblock is corrupt, and you might try running e2fsck 
with an alternate superblock:
    e3fsck -b 8193 <device>

fsck died with exit status 8
```

Once booted, I can assemble the array by hand with: ```
sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
``` 

however, that throws an error: 
```
Failed to mount "3T Volume"
mount: only root can mount /dev/md0 on /jestermount.
```
/jestermount is a directory I created and has 777 premisions, but I also ran the command with sudo, so I don't understand this error!
I just say "close" to the error and mount it on my own with: ```
sudo mount /dev/md0
```

after which the line for /dev/md0 in df -k looks like this:
```
 /dev/md0           2884298328     205940  2737578400     1%  /jestermount
```


So my questions are:

1. How do I fix the superblock problem?
2. How do I get it to mount on boot? Or is the superblock problem the only thing in the way.

thanks,

Ed.

---

### Post by djamu on 2008-11-15
hi there

1st check if your md device is properly assembled before checking the FS on it ..

do 
```
sudo mdadm --detail /dev/md0
```

and see if it is assembled ( post the results when in doubt )

also keep in mind that each block device has it's own superblocks 
> the MD superblocks reside on the individual physical devices 
> the FS super blocks reside on the MD device 
( and if you're using LVM / EVMS ) then these have their own superblocks aswell )

...
let me know if the MD is ok .. then I'll post some more ... ( I'm pretty good with RAID's check my other posts )

---

### Post by fjgaude on 2008-11-15
I think you have a few errors in how you have your array listed in the fstab:

```
/dev/md0 /jestermount ext3 defaults 0 2
```

I think this is what you want in the fstab file as the last line.

I assume you have alread made the mountpoint this way:

```
sudo mkdir /jestermount
```

Yes, what does

```
sudo mdadm -D /dev/md0
```

show?

And what does your /etc/mdadm/mdadm.conf show?

---

### Post by Mercedes300 on 2008-11-17
after replacing the line in fstab and a reboot, running the mdadm code gave this:
```
sudo mdadm -D /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
```

hmmmm... what now?

---

### Post by fjgaude on 2008-11-17
Gosh, here's what I'd do, exactly. Delete the **/etc/mdadm/mdadm.conf** file, remove mdadm using apt-get, reboot. Re-install mdadm, then run this:

```
sudo mdadm --assemble --scan
```

That will auto re-create the mdadm.conf file and you should be good to go. If your line in the fstab file is not right, see if the mount will work:

```
sudo mount -a
```

That should mount the array, if you have the mountpoint correctly made.

Let us know how things go.

---

### Post by Mercedes300 on 2008-11-17
Sweet! Thanks guys, looks like the auto built /etc/mdadm/mdadm.conf file is a lot better than the one I had before! 

Old:
```
DEVICES partitions
```
```

New:
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=4b07316a:8cd2d897:3abe3a51:4abf35bf

# This file was auto-generated on Mon, 17 Nov 2008 11:26:07 -0500
# by mkconf $Id$

```

When in doubt, reinstall, reboot! :KS

---

### Post by fjgaude on 2008-11-17
You mean things are normal, with mounted array?

---

### Post by Mercedes300 on 2008-11-17
Yeah, everything looks normal. I don't receive any errors on boot, and md0 is mounted on /jestermount with 2700GB of storage available! I am actualy trying to set up NFS now, if you have any links you can point me in the direction of, that would be great!

Thanks for all your help!

Ed

---

