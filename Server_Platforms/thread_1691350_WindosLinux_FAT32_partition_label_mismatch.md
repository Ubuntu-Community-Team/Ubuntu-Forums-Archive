---
title: "Windos/Linux FAT32 partition label mismatch"
date: 2011-02-19
forum: Server Platforms
---

### Post by sbrbot on 2011-02-19
Where is partition label stored?

I have external HDD with several FAT32 partitions. The problem is that for first partition (/dev/sdb1) Windows reads label "DOCS" while Ubuntu for the same partition reads label "txref^M^J116".

According to article on Wikipedia about Volumes, partition label is stored as an entry within a disk's root directory with a special volume-label attribute bit set, and also copied to an 11-byte field within the Extended BIOS Parameter Block of the disk's boot sector. It seems that Windows reads this label from one location and linux from another!

This mismatching appeared after resizing first partition with GParted in Ubuntu!

---

