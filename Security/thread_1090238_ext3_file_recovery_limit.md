---
title: "ext3 file recovery limit"
date: 2009-03-08
forum: Security
---

### Post by JoBangles on 2009-03-08
Hi,
I have used Shred to delete personal files some containing password lists. It seems these files can be restored in the ext3 file system. How long do these files stay in the journaling system before they are no longer recoverable?
Many Thanks.

---

### Post by Tubes6al4v on 2009-03-08
Before I begin, let me say that I am not experienced in this. But as far as I can tell, journeling file systems store parts of files throughout the partition to make seeking easier and defragmenting not an issue. You may be able to recover most of the information, but the longer you wait, the less chance there is.

Hopefully someone can confirm or deny this.

---

### Post by JoBangles on 2009-03-09
> **Tubes6al4v said:**
> Before I begin, let me say that I am not experienced in this. But as far as I can tell, journeling file systems store parts of files throughout the partition to make seeking easier and defragmenting not an issue. You may be able to recover most of the information, but the longer you wait, the less chance there is.

Hopefully someone can confirm or deny this.

Thanks for taking the time to reply, I hope I get more in depth advice.

---

### Post by lensman3 on 2009-03-09
Seems to me that once a "sync" is done, the journal would be forced to zero.

Also since ext3 is nothing but ext2 with journaling, that mounting the file system as an ext2 filesystem, all journaling would go away.

One way to insure, I think, that journaling transactions would be flushed to the disk is to force a "umount".  Once a file system is dismounted, the OS should guarantee that it is up to date.

If anyone knows differently, let us know.

---

### Post by JoBangles on 2009-03-09
Thanks, lensman3 & Tubes6al4v

---

