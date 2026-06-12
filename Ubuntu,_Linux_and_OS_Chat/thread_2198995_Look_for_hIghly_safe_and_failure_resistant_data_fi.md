---
title: "Look for hIghly safe and failure resistant data file storage format."
date: 2014-01-11
forum: Ubuntu, Linux and OS Chat
---

### Post by gschwind on 2014-01-11
Hello,

I trying to find a software that able to package/encode a file that will be recoverable in most case if data on disk are readable.

My main concern is, if you delete the file (without secure delete) or your file system become corrupted, you will be able to rebuild this data by scaning the data on disk.

If it could have some duplication and some other safety features I'm alos interreser. Size ratio is not a big issue.

This file will be store on "standard file system" like ext2/3/4 or fat.

Thank by avance for help.

---

### Post by tgalati4 on 2014-01-11
Look at the features of zfs.  I know you want an ext4 or fat file system, but zfs provides a more comprehensive file protection system.  Otherwise, write a script using *rsync* and copy the file to several places using the 3-2-1 method.  3 copies of critical files, on 2 separate devices, with 1 offsite.

---

### Post by ssam on 2014-01-12
you could use BTRFS, it has data checksumming and a range of RAID options. (Compared to ZFS it is included in pretty much all current linux distros). You can also use snapshotting to avoid accidental deletion.

Also multiple back ups stored in different places is a good idea. Assuming you don't have more than a few TB of data, get a few external hard drives, make several back ups and have 1 at home, 1 at work, 1 at a friend/relatives, etc.

---

### Post by The Cog on 2014-01-12
BTRFS might be an interesting idea. You could perhaps partition your disk and run a btrfs raid over the two partitions. And use snapshotting to protect against accidental deletes.

But then, given the stated requirement for  "standard file system" which doesn't include btrfs in the list, maybe two partitions and regular rsync to replicate might be the way to go.

Edit:
You could save yourself some grief by accepting that hard disks die, sometimes instantly and catasrtophically, and make sure you have backups on separate disks, one of which is not normally connected. Think of a PSU failure that destroys all electronics in the box including mouse and keyboard. I've known that happen.

---

### Post by gschwind on 2014-01-12
I'm already thinked to use several disk to save data, and I think I will use this way. Finaly this it probably the safest way :)

In first place, I thinked about some software that encapsulate data like tar, by block of data, witch allow to find data without file system like:

by 512 Byte block :
[header with signature + checksum + block number + total block + file id + file name] [encrypted/signed data] then another block...

with this you can find all block of your file on disk without filesystem working, but if you use both hard drive with 2 diferent file system this should be fine.

(I just say 2 diferent filesystem is important, because if theire is a bug in the file system driver this will also affect you backup)

Thank you

---

### Post by tgalati4 on 2014-01-12
What you are looking for is a hybrid file system that incorporates all of those features.  I don't think it exists.  If I understand correctly, each data block would have the complete header information--that is a lot of overhead.  Disk drives are reliable enough to simply have multiple copies of files to improve recovery.  If you were to inscribe data on a gold plate and shoot it into space, then maybe that type of file system would work--to help the aliens decipher the data.

Perhaps this has been done as a computer science research project.  You will have to continue your search.

---

### Post by porcini_m.2 on 2014-01-13
Check out the "par2" utility - it encodes redundancy data for a file - good for tar'd archives, etc.

---

