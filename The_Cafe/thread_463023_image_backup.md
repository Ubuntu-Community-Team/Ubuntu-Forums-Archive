---
title: "image backup"
date: 2007-06-03
forum: The Cafe
---

### Post by papa53921 on 2007-06-03
Being new to Ubuntu, i downloaded the latest (fawn) system, but can't find out how to do an image backup.  need assistance.

---

### Post by jgrabham on 2007-06-03
So do you have an ISO file that you want to put on a CD?

download this - [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

(MAKE SURE YOU ONLY BURN AT 8X (go on properties the main screen))

---

### Post by reacocard on 2007-06-03
You mean to backup the system after install? Partimage is probably the best image-based system, but you have to run it from the livecd as it can't work on mounted partitions. 

My solution to backup is to use rsync to keep a mirror of all the files on my system on my external harddrive. Then if anything goes wrong, I can just boot the livecd and copy the backup in, reinstall grub and I'm good to go. Best part is is that restoring doesn't need any tools other than what Ubuntu already provides, so I don't even need an Internet connection to restore! It also backs up extremely fast since it only transfers changed files, usually less than 10 minutes.

---

### Post by jgrabham on 2007-06-03
Oh right read it again, understand now!

---

### Post by PetePete on 2007-06-03
something like Norton Ghost I presume you mean?

---

### Post by Polygon on 2007-06-03
partimage is really good. ive used it to make backups of my bros ntfs partitions, but of course it works for all of the standard linux filesystems as well

---

### Post by mech7 on 2007-06-03
Is there also something like acronis true image under linux? So you can make a image while continue to work?

---

### Post by Polygon on 2007-06-03
you can make a image of a disk/partition while you still use the computer, you just have to have to unmount the disk or partition that your making the image of... or else it wont work

and partimage is just a console program with a little GUI... you can run it on a live cd and surf the internet or whatever while it makes the image of your disk (if your wanting to make a image of the partition that contains the root directory or something)

---

### Post by reacocard on 2007-06-03
> **Polygon said:**
> you can make a image of a disk/partition while you still use the computer, you just have to have to unmount the disk or partition that your making the image of... or else it wont work

And therein lies the problem. What if you want to backup /, while using it? Partimage can't do that, which is why I use rsync. rsync works perfectly on mounted partitions, is fast and easy to use, and can also do backups across a network. What's not to like?

---

### Post by runningwithscissors on 2007-06-04
> **reacocard said:**
> And therein lies the problem. What if you want to backup /, while using it? Partimage can't do that, which is why I use rsync. rsync works perfectly on mounted partitions, is fast and easy to use, and can also do backups across a network. What's not to like?
It's not a backup "image". Just a copy of the files on the FS.

@ OP: to back a partition up to an image:
dd if=<partition_device_file> of=<target_image_file>

---

### Post by daz4126 on 2007-12-01
> **runningwithscissors said:**
> It's not a backup "image". Just a copy of the files on the FS.

@ OP: to back a partition up to an image:
dd if=<partition_device_file> of=<target_image_file>


I used
```
dd if=/dev/sda1 of=/home/daz/hard_drive.img
```

and it seemed to make an image file.

... but how do I restore this?

DAZ

---

### Post by x0as on 2007-12-01
I use dd from a live cd

```
dd if=/dev/sda1 of=/mnt/backups/sda1-image
```

and to restore

```
dd if=/mnt/backups/sda1-image of=/dev/sda1
```

I gzip the images for storage, / partition compresses from 3.5gb to 1.9gb.

---

