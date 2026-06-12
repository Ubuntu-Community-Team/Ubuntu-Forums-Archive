---
title: "server directory can't delete directory"
date: 2011-07-09
forum: Server Platforms
---

### Post by leonv12 on 2011-07-09
Ubuntu server recently had issues with a disk.  fsck seemed to correct everything, but I have one directory that I can't delete, chown, chgrp, chmod, etc.

Here's the listing for the directory
dr-x-wxrwt 2  16709  25134  8192 2020-08-23 22:34 UDLEDATB.DBF

Note the sticky bit is set and the uid is a number that does not appear in /etc/passwd.

Even as root, any attempt to delete, chmod, chown, etc. gives "Operation not permitted".

Since sticky bit on a directory restricts delete to the owner and the owner is invalid, I am stuck.  I need to delete this directory.  

How can I fix this?

Thanks,
Leon

---

### Post by karlson on 2011-07-09
By the looks of things you may have a corrupted inode on your file system.

If you are using the EXT2/3/4 you might want to look at debugfs to see if you can clear the inode manually.

But before reserving to it I would look running fsck on the system again

---

### Post by matt_symes on 2011-07-09
Hi

I concur with karlson. As long as you have the inode you shouod be able to delete the directory. I had a similar problem the other day.

```
ls -i
```to get the inode for the directory.

Unmount the partition.

```
sudo umount /dev/sdXY
```or boot from a live cd.

Start debug fs

```
sudo debugfs -w /dev/sdXY
```Delete the inode.

```
clri <inode_number>
```Keep the angled brackets.

exit debugfs

```
quit
```Run fsck on the partition.

```
sudo fsck /dev/sdXY
```Remount the partition if not running from the liveCD.

This fixed my issue.

Kind regards

---

### Post by leonv12 on 2011-07-10
Thanks to Karlson and Matt for the solution (Special thanks to Matt for the detailed procedure).

One item, the command is clri, not crli.

Best regards and thanks again!
Leon

---

### Post by matt_symes on 2011-07-10
Hi

> **leonv12 said:**
> Thanks to Karlson and Matt for the solution (Special thanks to Matt for the detailed procedure).

One item, the command is clri, not crli.

Best regards and thanks again!
Leon

I'm glad it's fixed. :) I will also fix my typo. Should have been clri as you mentioned (clear inode)

Kind regards

---

