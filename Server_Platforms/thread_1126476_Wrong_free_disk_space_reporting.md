---
title: "Wrong free disk space reporting"
date: 2009-04-15
forum: Server Platforms
---

### Post by glauco.b on 2009-04-15
Hello all

After a lot of work and no real solution, I eventually decided to ask your help ;)

Here is my problem.

I have a server running ubuntu 7.10 (ok, ok, I know it's old, but works well and I don't need to update it) which started reporting "disk full" on the root partition.

The root partition runs on a mdadm raid0 array.

The system reports 9.5G of space occupation with 0% free, but when I actually run kdirstat or du the calculated used disk space is 2.5G.

I tried the following:
-rebuild journal files
-chkfs
-remove old logs
-du and kdirstat to try to find something strange
-uninstalled several packages

The problem is still there: df reports nearly 100% full, du reports at most 30% full.

What am I doing wrong? Is there a hidden automagic option in du that excludes hidden files from the counting? Is there a way to understand what's actually happening?

thanks in advance :popcorn:

---

### Post by fjgaude on 2009-04-15
I always trust **df -m** for disk space. How is **du** calculating what is free on the array? What command are you using for du?

---

### Post by cariboo on 2009-04-15
Check for archived packages in /var/cache/apt/archives. apt stores all the downloaded packages there and depending on how often you clean the cache there could be quite a few files there.

Jim

---

### Post by drs305 on 2009-04-15
A couple of points about "du" and "df".

"du" reports only usage on *mounted* devices. Also, if an external device is mounted on a mount point, and that mount point already contains data, that data  will be hidden and only the recently mounted data will be reported. Therefore, it is often useful to unmount all unnecessary partitions before investigating system partitions. 

Often disappearing space in the system partition is the result of a backup that is supposed to be written to another device but instead is written to the system disk. This happens when the backup device isn't mounted, so the data is written to the actual mount point on the system partition instead. If you umount non-system partitions and still find a large amount of data in your /media folder this is often a good indication of this.

Run both commands with "sudo" to ensure you are seeing all the files, including those not owned by you.

---

### Post by glauco.b on 2009-04-16
> **drs305 said:**
>  ...

Often disappearing space in the system partition is the result of a backup that is supposed to be written to another device but instead is written to the system disk. This happens when the backup device isn't mounted, so the data is written to the actual mount point on the system partition instead. If you umount non-system partitions and still find a large amount of data in your /media folder this is often a good indication of this.

...


Man, you are a GENIUS! :D  :popcorn:

In fact i had an NFS share mounted under /media that was supposed to act as backup folder for rsnapshot.

During a power shortage the link between the two server went down so a full backup was done in the system disk.

When the link went up, the NFS share was remounted hiding the REAL content of the mount directory. After reading your post,  the problem suddendly appeared to my eyes! Deleted the wrong backup and ta-da: 6GB freed.

Obviously that data was not visible to du...

Marked as SOLVED

---

### Post by drs305 on 2009-04-16
Glad you found the cause of your problem. 

For others reading this post with similar problems, I've now posted a guide for finding and recovering 'lost' free space:

[_HOWTO: Recover Lost Disk Space_]("http://ubuntuforums.org/showthread.php?t=1122670")

---

