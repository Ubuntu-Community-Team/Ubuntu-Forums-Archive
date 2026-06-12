---
title: "Proper Backup Solution"
date: 2008-12-11
forum: Server Platforms
---

### Post by psusi on 2008-12-11
Up until now I have been just using tar to backup my system in a cron job doing a full backup once a week, and incremental backups nightly.  I have recently been re-evaluating if this is the best idea, so I was wondering if anyone knows of a better setup.

There are two significant problems with using GNU tar as a backup system I have found:

1)  It does not quite provide for bare metal recover.  Specifically you have to use a working system to (re)format the disk, mount it, then use tar to extract all of the files, then install grub so the system boots.
2)  It STILL does  not support extended attributes and/or access control lists and/or SELinux contexts, so you will loose these when you restore.
3)  Does not respect the do not backup flag of chattr or save/restore any of the ext2 attributes.
4)  Modifies the atime ( or ctime ) of files as they are backed up unless you remount with noatime.

As an alternative, I have considered using partimage.  As far as I understand, this works just like dd except that it parses the allocation bitmaps and for blocks which are not allocated, it skips reading them and outputs either all zeros for the block, or otherwise indicates that the block is omitted and empty in the output stream.  This means that:

1)  You can not restore to a disk of a different size
2)  Any fragmentation in the original filesystem is preserved on restore
3)  The entire filesystem must be restored, not just any specific files you want to recover
4)  Any files on the disk you are restoring to are lost
5)  Can't back up a filesystem while it is mounted for write access
6)  Can't back up TO the filesystem being backed up
7)  Can't restore to a filesystem formatted with different parameters, like inode size

Another alternative I have considered is dump.  Its problems are:

1)  Can't back up a filesystem while it is mounted for write access
2)  Can't back up TO the filesystem being backed up
3)  Like tar, does not quite provide for full bare metal recovery

Are there any other alternatives?  Which do you use and why?

---

### Post by Traumadog on 2008-12-11
I've been backing up nightly to a terabyte hard drive using cron jobs, rsync, and BASH scripts.  I do three backups each night....  one for the operating system (primarily the root directory) one for the home directory, and one for my web server.  I don't know if this is the best solution for you, however, especially if you are concerned about having a backup that you can boot from.  From my perspective, I figured if worse came to worse, I could reinstall the operating system from a live CD and then update it from the root file system backup.  My real concern is for the information in the home directory and web server which would be almost impossible to replace if lost.  Using this method also allows me to rapidly replace specific files if lost or corrupted without having to copying the entire backup to the disk.  This has been useful a couple of times when individual files have been accidentally deleted.

The other nice thing about rsync is that it doesn't care a hoot about the size of the drive you're transferring the information to, as long as the drive or partition is large enough to hold the data. 

Just something to consider...

Best wishes, :)

Traumadog.

---

### Post by m_l17 on 2008-12-12
I use rsnapshot:

> snapshot is a filesystem snapshot utility for making backups of local and remote systems.

Using rsync and hard links, it is possible to keep multiple, full backups instantly available. The disk space required is just a little more than the space of one full backup, plus incrementals.

Depending on your configuration, it is quite possible to set up in just a few minutes. Files can be restored by the users who own them, without the root user getting involved.

There are no tapes to change, so once it's set up, your backups can happen automatically untouched by human hands. And because rsnapshot only keeps a fixed (but configurable) number of snapshots, the amount of disk space used will not continuously grow.


[http://www.rsnapshot.org/]("http://www.rsnapshot.org/")

How to:

[http://www.rsnapshot.org/howto/]("http://www.rsnapshot.org/howto/")

[http://www.debianhelp.co.uk/rsnapshot.htm]("http://www.debianhelp.co.uk/rsnapshot.htm")

List of backup solutions:

[http://www.debianhelp.co.uk/backup.htm]("http://www.debianhelp.co.uk/backup.htm")

---

### Post by psusi on 2008-12-13
The problem with rsync type backups is that they can't be compressed or go onto tape.  You also can't do incremental backups across multiple disks  or onto cds.

I tried experimenting with dump to see if it would be faster than tar since it accesses the disk directly, but it crashes partway through the backup.

I'm now studying a utility called dar that looks promising.  It looks like it mostly works like tar but does support extended attributes, acls, and respects the nodump chattr flag, as well as having several other features.

Does anyone have any thoughts on this utility?

---

