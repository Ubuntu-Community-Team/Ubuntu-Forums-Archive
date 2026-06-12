---
title: "mounting multiple drives on one mount point"
date: 2010-05-23
forum: Server Platforms
---

### Post by tr333 on 2010-05-23
I have three 1TB drives formatted as XFS and I would like to mount them all on the same mount point.  Is this possible?

---

### Post by new_tolinux on 2010-05-23
I guess not. If mounted to a location, the drive acts as that folder (so, you can put files there etc.).
Putting two or more drives at that same point, the computer should get confused about where to put that file you'll want to save.

I guess the only way to do it, is to configure those drives as one software-raid drive and then mount it. Or (ofcourse) something like this:
drive 1: /path/to/folder1
drive 2: /path/to/folder2
drive 3: /path/to/folder3
Maybe also possible:
drive1: /path/to
drive2: /path/to/folder
drive3: /path/to/folder/otherfolder

---

### Post by tr333 on 2010-05-23
What if the drives are mounted read-only?

---

### Post by new_tolinux on 2010-05-23
Probably not. And I guess it has a simple reason.
Say 2 drives both have /some/folder on them, with in them partly the same files (e.g. documents), only different dates and sizes.

Which folder/fileset should be shown if you access it using Nautilus, ls, gedit, nano or even cat?

---

### Post by koenn on 2010-05-23
> **new_tolinux said:**
> I guess not. If mounted to a location, the drive acts as that folder (so, you can put files there etc.).
Putting two or more drives at that same point, the computer should get confused about where to put that file you'll want to save.

I guess the only way to do it, is to configure those drives as one software-raid drive and then mount it. Or (ofcourse) something like this:
drive 1: /path/to/folder1
drive 2: /path/to/folder2
drive 3: /path/to/folder3
Maybe also possible:
drive1: /path/to
drive2: /path/to/folder
drive3: /path/to/folder/otherfolder

yes, something like that.
or bundle all disks in one logical vulume, with LVM 
[http://users.telenet.be/mydotcom/howto/linux/disks2.htm](http://users.telenet.be/mydotcom/howto/linux/disks2.htm)

---

### Post by frostschutz on 2010-05-23
You can mount multiple filesystems into one folder, however, only the last filesystem you mounted will be shown. Since when you mount something in a folder, the mount hides the contents of this folder (although usually the folder would be empty anyways).

There are some meta filesystems (like unionfs) that can combine filesystems, but they won't really do what you want. Their purpose is also different (for example make a read only mounted filesystem behave as if it was read-write, i.e. you can change files but the changes are not actually written on disk).

If you simply want to put a 3TB large single file system on 3x 1TB drives, use LVM. You're in trouble though if one of the disks dies, as the entire filesystem becomes pretty much unusable if it has an 1TB chunk missing... ;)

---

### Post by tr333 on 2010-05-23
Thanks for the info.  I might take a look at LVM.

---

### Post by Perkins on 2010-05-31
mhddfs is a new (I believe slightly experimental still) implementation of a union file system that supposedly allows what you wish to do.  There is a FUSE module for it in the repository.  If I recall correctly it has a variety of algorithms for how to deal with writes, including putting new files on whichever disk has the most space.


That said, were I you, assuming that the three drives are not meant to be portable (id est, you are not going to arbitrarily want to unplug one and take it elsewhere)  I would probably set them up as a software RAID5.  That way you get them all under a single mountpoint, treated as a single volume, and when one of them burns out, you can simply replace it without losing any data.

---

### Post by new_tolinux on 2010-05-31
> **Perkins said:**
> you can simply replace it without losing any data.
As far as I've read that gives you probably big problems when you're going to reinstall or upgrade your system.
That's one of the major reasons I did not setup my usb-drives as a software-raid.
(Besides that I also use those drives in Windows, so a complete *nix solution will give me a big probem anyway)

---

