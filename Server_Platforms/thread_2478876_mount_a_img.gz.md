---
title: "mount a img.gz"
date: 2022-09-07
forum: Server Platforms
---

### Post by Raymond Day on 2022-09-07
Hi I put my server on new PC. DD back up the 4TB boot but it was in LVM so the DD backup did not work very good at all to save things.

But I have a 2 year old backup and I wanted to see what I can restore from it.

I know a long time ago could mount a image.

Looked on line a lot and can not find out how.

I think had to get info on the image and then put some number in the mount command from what I remember.

The back up is named "rayday_backup_image.img.gz" can I just mount this to look at it? If so how?

I backed it up with this command:

dd if=/dev/sdc conv=sync,noerror bs=64K | gzip -c >/media/500gb/rayday_backup_image.img.gz"

If that helps to mount it.

I don't want to copy it to some real drive just to look at it.

-Raymond Day

---

### Post by TheFu on 2022-09-07
Should be able to use a loop mount on the img file, not the img.gz. gunzip it first.

---

### Post by sudodus on 2022-09-07
It should be possible to use [FONT=Courier New]**kpartx**[/FONT] on the extracted img file.

```

# --- map
$ sudo kpartx -av t-3.5g.img
add map loop0p1 (253:0): 0 6293372 linear 7:0 503907
add map loop0p2 (253:1): 0 1954 linear 7:0 1953
add map loop0p3 (253:2): 0 500000 linear 7:0 3907

# --- delete map
$ sudo kpartx -d template-3.5GB.img

```

The loop devices can be seen by **[FONT=Courier New]lsblk[/FONT]** but the loop devices are hidden in the **[FONT=Courier New]mapper[/FONT]** subdirectory, found via find
```

$ sudo find /dev/ -name "*loop0*"

```

You can mount the loop devices with normal mount command lines for example
```

sudo mount /dev/mapper/loop0p1 /mnt/lp1

```

There are more details at [this link](https://askubuntu.com/questions/1022633/mount-dd-image-for-my-usb/1102212#1102212)

---

### Post by Raymond Day on 2022-09-07
I don't want to extracted it.

I know I did it along time ago. Mount a backup and I think I had to use fdisk to see were some numbers of were.

I think it was in loop. So I know it can do it.

-Raymond Day

---

### Post by sudodus on 2022-09-08
When you recall how to do it without extracting to an img file, please share the method with us.

---

### Post by TheFu on 2022-09-08
> **sudodus said:**
> When you recall how to do it without extracting to an img file, please share the method with us.

Don't some file systems support compression natively?  ZFS, brtfs, and ext4 come to mind, though I think only ZFS is probably safe enough for production use and I have doubts that snagging a image of a ZFS setup would really work on the other end.

---

### Post by MAFoElffen on 2022-09-08
Yes & No. Not the way you remember... 
> **Raymond Day said:**
> I don't want to extracted it.

I know I did it along time ago. Mount a backup and I think I had to use fdisk to see were some numbers of were.

I think it was in loop. So I know it can do it.

-Raymond Day
What you are remembering is how to mount an uncompressed image file... Where you mount the whole image file, use 'fdisk -l' to see and calculate the offsets of the partitions within the image, to use those offsets to mount the partitions of the mounted image in loop devices... Where you can do the same with (on a standard image file, uncompressed) with 'kpartx...

If you had compressed it with squashfs (instead of gzip), then you can use kpartx to mount it while still compressed with squashfs...

### BUT... ###
Now the other side of that... You can do it on the fly while compressed with gzip (sort of). You would have to install extra utilities to do it... and you have to have enough free resources to do it:  [https://askubuntu.com/questions/836217/how-to-mount-a-compressed-disk-image](https://askubuntu.com/questions/836217/how-to-mount-a-compressed-disk-image) (Answer #7)

---

### Post by Raymond Day on 2022-09-08
I [found a post here that talks about how I remember it.]("https://www.aptgetlife.co.uk/mount-disk-image-created-dd-using-ubuntu/")

But I guess some how have to add a | in the line to say it's a compressed image.

If I do it now it looks like this:

> root@rayday:/media/500gb-2# fdisk -b512 -l rayday_backup_image.img.gz
Disk rayday_backup_image.img.gz: 120.12 GiB, 128979455488 bytes, 251912999 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
root@rayday:/media/500gb-2#

-Raymond Day

---

### Post by MAFoElffen on 2022-09-08
> **Raymond Day said:**
> I [found a post here that talks about how I remember it.]("https://www.aptgetlife.co.uk/mount-disk-image-created-dd-using-ubuntu/") <<https://www.aptgetlife.co.uk/mount-disk-image-created-dd-using-ubuntu/>>
<<EDITED>>
-Raymond Day
LOL. That post is how I described in my last post "for mounting an uncompressed" image file... using 'fidisk -l' to get the sectors of the partition to figure out the offsets to mount the contained partitions...

Your commands did not show the internal partitions of your image file because it is compressed.... Rather in your link, that is like I said (on uncompressed), after they did the "math":
```

Device         Boot     Start       End   Sectors   Size Id Type
backup_sata.img1 *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
backup_sata.img2         206848 237185023 236978176   113G  7 HPFS/NTFS/exFAT
backup_sata.img3      237185024 588070911 350885888 167.3G  f W95 Ext'd (LBA)
backup_sata.img4      588070912 625137663  37066752  17.7G 27 Hidden NTFS WinRE
backup_sata.img5      [COLOR=#008000]237187072[/COLOR] 588070911 350883840 167.3G  7 HPFS/NTFS/exFAT
```
Your link didn't show the math how they got that number for the offset, but here "IS" the math for that:
```

[COLOR=#008000]237187072[/COLOR] * 512 = [COLOR=#ff0000]121439780864[/COLOR]

```
```

mount -o ro,loop,[COLOR=#ff0000]offset=121439780864[/COLOR] backup_sata.img /backup_sata

```
Note that is not a compressed image file... That is how I mount my full image backups. I do not compress them, just so I can easily mount and access them... 

Please look at the second half of my last post, to answer what you are looking for (mounting a gzip compressed image file).

---

### Post by TheFu on 2022-09-08
kpartx makes much of this stuff really easy.

---

### Post by MAFoElffen on 2022-09-09
+1 with TheFu!!!. No math involved. the mount command changes to get the named device (the partition /dev path) and it gets it.

Example to the same img file used in last example...
```

sudo kpartx -a ./backup_sata.img

```
It will assign a loop devices to it, which you can then mount to... Where you then can then mount to those loop devices... And 'kpartx' is a default installed application with all Ubuntu flavors.
```

mkdir /mnt/part5
sudo mount /dev/mapper/loop0p5 /mnt/part5

```

---

### Post by TheFu on 2022-09-09
Actually, sudodus posted the reminder.  I suspect we've all  used kpartx, but not really often enough to remember the command off the top of our heads. I probably used it 3 yrs ago to find partitions inside a virtual machine's block device (I use LVM, so it was nested as 
disk--> partition --> PV --> VG --> LV (this to the VM) - partitions (from inside the VM).

The trick for all these things is that "everything is a file" on Unix systems.

---

### Post by Raymond Day on 2022-09-10
I [found a post here that talks about how I remember it.]("https://www.aptgetlife.co.uk/mount-disk-image-created-dd-using-ubuntu/")

But I guess some how have to add a | in the line to say it's a compressed image.

If I do it now it looks like this:

> root@rayday:/media/500gb-2# fdisk -b512 -l rayday_backup_image.img.gz
Disk rayday_backup_image.img.gz: 120.12 GiB, 128979455488 bytes, 251912999 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
root@rayday:/media/500gb-2#

-Raymond Day

---

### Post by MAFoElffen on 2022-09-10
> **Raymond Day said:**
> I [found a post here that talks about how I remember it.]("https://www.aptgetlife.co.uk/mount-disk-image-created-dd-using-ubuntu/")

But I guess some how have to add a | in the line to say it's a compressed image.

If I do it now it looks like this:

-Raymond Day
This is the same post you posted in [#8]("https://ubuntuforums.org/showthread.php?t=2478876&p=14111485#post14111485")... I guess you didn't read posts #9 through #12(?) <-- Those posts talked about that.

You may want to read those... :idea:

---

