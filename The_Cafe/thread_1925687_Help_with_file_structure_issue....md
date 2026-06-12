---
title: "Help with file structure issue..."
date: 2012-02-15
forum: The Cafe
---

### Post by Nixarter on 2012-02-15
So I'm trying to learn how file systems work, and I need some hel pwith calculations.

ATM I'm working with FAT32.  For instance, with a file that is 132kb, what is the number of sectors that it takes up?  I've tried a few ways to calculate it, but I don't think they are right...

Thanks in advance :)

---

### Post by Bachstelze on 2012-02-15
Depends on your cluster size. Files are allocated in units of clusters, so with a 64kb cluster size, that would take 192kb.

*EDIT:* 64kb is a lot though, generally you will have clusters of 4 or 8kb. That also depends on the sector size of the disk (clusters are allocated in units of sectors, 512 bytes per sector but 8 or 16 sectors per cluster gives 4 or 8kb).

---

