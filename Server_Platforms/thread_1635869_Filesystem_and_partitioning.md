---
title: "Filesystem and partitioning"
date: 2010-12-02
forum: Server Platforms
---

### Post by Powderking on 2010-12-02
Hi all

I am planning to set up an Ubuntu server with a MythTV backend.

Because I read here ([https://help.ubuntu.com/9.10/installation-guide/i386/directory-tree.html](https://help.ubuntu.com/9.10/installation-guide/i386/directory-tree.html)) and heard from friends that there should be separate partitions for boot, usr, etc. and I always had my /home on a separate partition that it will still be there after reinstalling the OS. Therefore I thought of how I should partition the harddisk in my new server.

I want to have the system on a 500 GB 2.5 inch HD (WD AV-25) that consumes very vew power.
I will record to a 2 TB HD and keep my media on four 1.5 TB HDs in RAID5.

For the system HD I planned to create the following partitions:
/boot, 1 GB, EXT4, primary
swap, 8 GB, swap, primary (double the size of the installed memory)
/, 1 GB, EXT4, primary
/usr, 10 GB, EXT4, extended
/var, 5 GB, EXT4, extended
/var/lib/mythtv, 250 GB, JFS / XFS / EXT4 ???, extended
/tmp, 1 GB, EXT4, extended
/home, 224 GB (the rest), EXT4, extended

Recordings HD (2 TB):
/var/lib/mythtv/Recordings, 2 TB, JFS / XFS / EXT4 ???, primary
 
Media HD (4 x 1.5 TB in RAID5 ==> 4.5 TB):
/mnt.media, 4.5 TB, JFS / XFS / EXT4 ???, RAID5

I was told that it isn't a good idea to store the mythtv related stuff in /var/lib because it doesn't belong there even though the standard in the mythbackend setup is exactly this place to store it?

He told me as well that modern distros don't like to have different partitions.
What advice can you give me about that?

The third question is about the filesystem: what is better for handling big files JFS, XFS or EXT4?
I thought EXT4 was much slower in deleting big files and JFS is best doing that.
Does Ubuntu like JFS or mabe better XFS?

---

