---
title: "windows read ext3 -- or -- ubuntu read ntfs/fat32?"
date: 2010-03-03
forum: Server Platforms
---

### Post by davidshere on 2010-03-03
If I had a choice, which is better, having a Windows server reading/writing ext3 filesystems, or having an Ubuntu server reading/writing ntfs/fat32 filesystems?

I'm asking mainly becuase with my current setup, I'm having [this problem]("http://ubuntuforums.org/showthread.php?t=1410891").

---

### Post by Jekshadow on 2010-03-05
Windows has virtually no support for anything above ext2 (and that is with a 3rd party driver), and Ubuntu has near 100% support for FAT32 and NTFS OOTB. I would go with Ubuntu reading NTFS/FAT32.

---

