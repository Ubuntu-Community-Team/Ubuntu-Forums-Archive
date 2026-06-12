---
title: "problem moving large files to samba share"
date: 2009-12-18
forum: Server Platforms
---

### Post by mendo on 2009-12-18
every time i try to move a large file (greater than 1GB) over the network to a samba share, the process stops and i get an error telling me that there is not enough space to finish the operation.  there is plenty of space - 100's of GBs, so what' up?

this has happened trying to move .VOB files and hd image files created by Norton Ghost 9.0.

any ideas?

thanks.

---

### Post by kadeous on 2009-12-18
Does the drive support a partition with large file support?

---

### Post by mendo on 2009-12-18
i guess i assumed so, but how can i find out?

---

### Post by kadeous on 2009-12-18
What is the partition on the drive storing the information?

---

### Post by mendo on 2009-12-18
how is it formatted? vfat

---

### Post by kadeous on 2009-12-18
Try 

sudo fdisk -l | more

It will list out drives and partitions, not sure how to check if it's ext3 or such.

Doing some google reading atm to try and help you solve it. :)

---

### Post by mendo on 2009-12-18
it's fat32, mounted in fstab as vfat.

i have googled, but haven't found anything helpful yet.

---

### Post by KeLa on 2009-12-18
So here is some info of the problem.
First of all FAT32 is not problem in here because it has this limit : max file size = 4 [GB]("http://en.wikipedia.org/wiki/Gigabyte") minus 1 byte (or block size if smaller)
But in samba client when you mount a file share you must add lfs parameter to mount command or fstab for _l_arge _f_ile _s_upport.
At least bigger than 2GB (i know OP mentioned 1 GB but i hope this help a little)

---

### Post by mendo on 2009-12-18
i'm having trouble mounting the drive with the lfs option.

this entry in fstab works fine:

/dev/sda1/   /mnt/data   vfat   users,auto,exec,umask=000

but if i put lfs anywhere in the options, the drive won't mount.  what am i doing wrong?

thanks.

---

