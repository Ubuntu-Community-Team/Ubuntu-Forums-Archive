---
title: "Media folder contents replaced by /tmp"
date: 2013-10-13
forum: Server Platforms
---

### Post by Mustafa_Khan on 2013-10-13
Hi,
I have a Media folder in my /home/user/ directory where all of the media on my servers system is held.  The server recently had a problem where filesystem had to be fixed on boot (fsck I believe) but during the check it threw up some errors like this: Inode 3542294 was part of the orphaned inode list.  IGNORED.
After fixing however, the Media folders contents are no longer there but there is a /tmp folder present.  I am wondering if its possible to recover all the media files somehow?  Is there a way to figure out what the problem is?

---

### Post by TheFu on 2013-10-13
Sometimes a file system gets confused. Lazy bits, failing sectors, corruption from a flaky cable, controller, etc.  The best solution I know is backups - versioned backups, not just a mirror.  Probably not what you want to hear. Sorry.

fsck is the best option - might try testrec too, but that tool isn't really meant to "find" hundreds or more files. It will be painful. I have an HDD with media files that was part of a 3-disk LVM setup. 1 of the drives failed and all the data on the other 2 became unavailable. It was NOT RAID0/striped.  I should try to use testrec on those non-failed HDDs. Spending a Sunday afternoon looking over old TV recordings sounds delightful ... er... not.

---

