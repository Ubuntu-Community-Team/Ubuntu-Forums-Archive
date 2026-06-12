---
title: "Partition Additional Disks"
date: 2008-09-17
forum: Server Platforms
---

### Post by vegas588 on 2008-09-17
I want to add a new disk to my Ubuntu 8.04 server. I am new, so I am not sure of the correct procedure. How do I install/partition the new disk? Basically, I want to use it for file storage, so I just want 1 big partition on the new disk.

Is there a partitioning tool? I have read about partman, but not sure of that is correct.

Thanks.

---

### Post by renzokuken on 2008-09-17
simply plug the disc in, and then load a live CD such as Ubuntu Live or Gparted Live CD cd.

gparted is an excellent GUI partitioning tool. just use it from the live cd to partition and format the whole drive (make sure you format the new one and not your original harddrive by mistake)

---

### Post by renzokuken on 2008-09-17
EDIT: double post, sorry

---

### Post by Krupski on 2008-09-17
> **vegas588 said:**
> I want to add a new disk to my Ubuntu 8.04 server. I am new, so I am not sure of the correct procedure. How do I install/partition the new disk? Basically, I want to use it for file storage, so I just want 1 big partition on the new disk.

Is there a partitioning tool? I have read about partman, but not sure of that is correct.

Thanks.

OK, do this:

(1) Get a listing of the drives currently in your computer:

```

sudo ls -l /dev/disk/by-id | sort

```

You will see a listing something like this:

```

root@storage:/# ls -l /dev/disk/by-id | sort
lrwxrwxrwx 1 root root 10 2008-09-16 00:40 ata-Sony_NCFC4G_011910H0207P2150-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-09-16 00:40 ata-Sony_NCFC4G_011910H0207P2150-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 2008-09-16 00:40 edd-int13_dev80-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-09-16 00:40 edd-int13_dev80-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 2008-09-16 00:40 scsi-1ATA_Sony_NCFC4G_011910H0207P2150-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-09-16 00:40 scsi-1ATA_Sony_NCFC4G_011910H0207P2150-part2 -> ../../sdc2
lrwxrwxrwx 1 root root  9 2008-09-16 00:40 ata-Sony_NCFC4G_011910H0207P2150 -> ../../sdc
lrwxrwxrwx 1 root root  9 2008-09-16 00:40 ata-WDC_WD10EACS-00D6B0_WD-WCAU40312948 -> ../../sda
lrwxrwxrwx 1 root root  9 2008-09-16 00:40 ata-WDC_WD10EACS-00D6B0_WD-WCAU40433302 -> ../../sdb
lrwxrwxrwx 1 root root  9 2008-09-16 00:40 edd-int13_dev80 -> ../../sdc
lrwxrwxrwx 1 root root  9 2008-09-16 00:40 md-uuid-433488b9:a6d1d00f:2e29483d:f114274d -> ../../md0
lrwxrwxrwx 1 root root  9 2008-09-16 00:40 scsi-1ATA_Sony_NCFC4G_011910H0207P2150 -> ../../sdc
lrwxrwxrwx 1 root root  9 2008-09-16 00:40 scsi-1ATA_WDC_WD10EACS-00D6B0_WD-WCAU40312948 -> ../../sda
lrwxrwxrwx 1 root root  9 2008-09-16 00:40 scsi-1ATA_WDC_WD10EACS-00D6B0_WD-WCAU40433302 -> ../../sdb
total 0

```

(2) Physically install the new hard drive in your computer.

(3) Boot up. Find out what the **new** drive is named:

```

sudo ls -l /dev/disk/by-id | sort

```

It will be the same kind of listing as above, PLUS the new drive. Write down it's name or copy it to the clipboard. For example, MY /dev/sda drive is called:

"/dev/disk/by-id/ata-WDC_WD10EACS-00D6B0_WD-WCAU40312948"

(4) Partition the new drive: (note the example below is MY drive, replace the line with YOUR drive name!)

```

sudo cfdisk /dev/disk/by-id/ata-WDC_WD10EACS-00D6B0_WD-WCAU40312948

```

CFDISK is intuitive. Just use "n" for new partition, select the default size (all of it), hit "W" (uppercase W for "write"), say "yes" (not just "y") and finally "q" to quit. You MAY get an error saying that Linux cannot re-read the partition table. If so, this simply means you have to reboot to get it updated.

Your new partition will be called "/dev/disk/by-id/ata-WDC_WD10EACS-00D6B0_WD-WCAU40312948**[COLOR="Red"]-part1[/COLOR]**" (again, this is an example!)

(5) Reboot if necessary to make Linux read the partition table.

(6) Format the new partition:

```

sudo mkfs.ext3 /dev/disk/by-id/ata-WDC_WD10EACS-00D6B0_WD-WCAU40312948-part1 

```

(7) Decide where you wish to have the new drive appear. Assume you want a directory called "big-disk" in your root and "/big-disk" will be your new hard drive. Make the directory:

```

sudo mkdir /big-disk

```

(8 ) Add it to your /etc/fstab file so that it auto-mounts on boot. Edit the fstab file by ADDING this line (again, replace the name with the name of YOUR new drive):

```

/dev/disk/by-id/ata-WDC_WD10EACS-00D6B0_WD-WCAU40312948-part1    /big-disk    ext3    defaults    0    2

```

Now, mount your new drive:

```

sudo mount -a

```

Lastly, see if it's there:

```

sudo df -H

```

You will see a listing of "Filesystem  Size  Used  Avail  Use%  Mounted on" and one of them should be your new "/big-disk" and it's size should be the same size as your new hard drive.

Hope this helps!

-- Roger

---

### Post by Krupski on 2008-09-17
> **renzokuken said:**
> simply plug the disc in, and then load a live CD such as Ubuntu Live or Gparted Live CD cd.


Since the OP said he's using SERVER, I gave him CLI instructions. Oh well... :)

---

### Post by renzokuken on 2008-09-17
> **Krupski said:**
> Since the OP said he's using SERVER, I gave him CLI instructions. Oh well... :)

yeah my bad, didnt notice the **server** part. hehe. 

probably easier to follow Krupski's method

---

### Post by vegas588 on 2008-09-17
That's Alot! 

OK, I will go through those steps. If I run into problems, I will post any output here.

I am using Ubuntu Server and therefore I am doing everything via command line.

Thanks for your help.

---

### Post by Krupski on 2008-09-17
> **renzokuken said:**
> yeah my bad, didnt notice the **server** part. hehe. 

probably easier to follow Krupski's method

I suggested that he use the /dev/disk/by-id method to avoid grief when Ubuntu switches device names around.

What's /dev/sdc now might be /dev/sda later!!!

Thinking about it... *by-uuid* might have been better...?

---

### Post by vegas588 on 2008-09-17
This is what I have done so far. I have not yet placed the new disk in because I wanted to format the remainder of the first disk. So I followed your instructions and they were very clear. cfdisk is a straightforward utility to use. I formatted the remainder of the first disk, created a new directory named /DATA1.

Now, when I go to the /etc/fstab file to add it in, I am presented with the following info. Do I need to use this UUID number as opposed to the method you suggested? How would I find the UUID number of the new partition I just made?

---

### Post by Krupski on 2008-09-17
> **vegas588 said:**
> This is what I have done so far. I have not yet placed the new disk in because I wanted to format the remainder of the first disk. So I followed your instructions and they were very clear. cfdisk is a straightforward utility to use. I formatted the remainder of the first disk, created a new directory named /DATA1.

Now, when I go to the /etc/fstab file to add it in, I am presented with the following info. Do I need to use this UUID number as opposed to the method you suggested? How would I find the UUID number of the new partition I just made?

Sounds good so far.

Yes, you can identify the partition or new disk with UUID... in fact, it's probably the best way to do it.

First, find out what the UUID of your partition or new disk IS:

```

sudo ls -l /dev/disk/by-uuid

```

You will get something that looks like this:

```

root@storage:/# ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-09-16 00:40 [COLOR="Red"]**4349b5fc-6cd6-43eb-bcb5-7b774fa4ed00**[/COLOR] -> ../../sdc2
lrwxrwxrwx 1 root root 10 2008-09-16 00:40 [COLOR="Red"]**6fd8ed9d-4521-4d13-9e98-cb76f947486e**[/COLOR] -> ../../sdc1

```

See what's highlighted in red? THAT is the UUID of each partition.

Find the one that's your new partition.

HINT: If you can't tell which is which, look in your "/boot/grub/menu.lst" file. The boot device is specified with a UUID. Your new partition is, then, obviously, the OTHER UUID.


Next, add THIS into your "/etc/fstab" file:

```

UUID=[COLOR="Red"]**xxxxxxxx-xxxx-YOUR-UUID-xxxxxxxxxxxx**[/COLOR]    /DATA1    ext3    defaults    0    2

```

Mount the new drive:

```

sudo mount -a

```

See if it's "there":

```

sudo df -H

```

Lastly... you may wish to use lowercase for your directory... "/data1" instead of "/DATA1". You won't have to use the shift key all the time!  :)

Good luck!

-- Roger

---

### Post by vegas588 on 2008-09-17
Thats great. I am beginning to see how this all works. By the way, what do these settings mean?

defaults 0 2

I appreciate the assistance.

---

### Post by Krupski on 2008-09-17
> **vegas588 said:**
> Thats great. I am beginning to see how this all works. By the way, what do these settings mean?

defaults 0 2

I appreciate the assistance.

"defaults" means mount the filesystem with rw, suid, dev, exec, auto, nouser, and async.

These mean:

rw - read / write
suid -  allow set-user-identifier or set-group-identifier bits to take effect
dev - interpret character or block special devices on the file system
exec - permit execution of binaries
auto - can be mounted with the "mount -a" option
nouser - forbid an ordinary (i.e., non-root) user to  mount  the  file  system
async - all I/O to the file system should be done asynchronously


Full info can be had by reading "man mount".


The next ones are for "dump" and "fsck". The second one is not a pseudo-spelling of a nasty word... it's short for (f)ile (s)ystem (c)hec(k). :)

From: **[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)**

[B]
< 5th and 6th columns: Dump and fsck options >

Dump and, uh, what options? Well, dump is a backup utility and fsck is a filesystem check utility. I won't discuss them in great length here (they would both need their own tuXfile), but I'll mention them, because otherwise you'd spend the rest of the day wondering what on God's green Earth do these things mean.

The 5th column in /etc/fstab is the dump option. Dump checks it and uses the number to decide if a filesystem should be backed up. [COLOR="Red"]If it's zero, dump will ignore that filesystem.[/COLOR] If you take a look at the example fstab, you'll notice that the 5th column is zero in most cases.

The 6th column is a fsck option. fsck looks at the number in the 6th column to determine in which order the filesystems should be checked. [COLOR="Red"]If it's zero, fsck won't check the filesystem.[/COLOR]
[/B]

Additional info: The ROOT filesystem should be 1 (one), any other filesystems should be 2 (two) and if you don't ever want them checked, use 0 (zero).

Fun? Wow!

-- Roger

---

