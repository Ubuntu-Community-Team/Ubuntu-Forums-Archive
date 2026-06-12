---
title: "File System Exam Question"
date: 2007-10-15
forum: The Cafe
---

### Post by ShareBuntu on 2007-10-15
Hey everyone,

I was looking through some past exam papers for operating system theory and stumbled upon this one. Needless to say it's baffled me a bit. Does anyone know how to approach it?

Consider an ext2-like file system that has the folowing characteristics:
  • Time to read a block: 1 millisecond
  • Time to find a (random) block: 5 milliseconds
  • Time to find the next adjacent block: instant
  • Processing Time: instant
  • Inode size: one block
  • Number of direct pointers to data blocks in an inode: 50
  • Number of disk block pointers that fit in a block: 50.
After a directory entry has been read from disk, the inode for the file is known. How long would it then take on average to read one randomly chosen block of data from a file that takes up 100 disk blocks?

Any help would be greatly appreciated.

---

