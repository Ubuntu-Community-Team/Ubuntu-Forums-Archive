---
title: "Defrag windows volumes from Live Ubuntu Flash Drive"
date: 2010-01-20
forum: The Cafe
---

### Post by brucehobson on 2010-01-20
Would it be possible to boot a Live Ubuntu Flash drive and then delete my Windows page-file(s) and then defragment my NTFS drives before rebooting back into windows? Where windows will recreate the page-files.

I ask because I would like to move the unmovable files like page-files for contigus file space and page-files.

In other-words is the NTFS support in Ubuntu good enough for this? And is their a defrag program in Ubuntu that will do the work?

Thanks ahead of time.

Bruce

---

### Post by k64 on 2010-01-20
> **brucehobson said:**
> Would it be possible to boot a Live Ubuntu Flash drive and then delete my Windows page-file(s) and then defragment my NTFS drives before rebooting back into windows? Where windows will recreate the page-files.

I ask because I would like to move the unmovable files like page-files for contigus file space and page-files.

In other-words is the NTFS support in Ubuntu good enough for this? And is their a defrag program in Ubuntu that will do the work?

Thanks ahead of time.

Bruce

You could use fsck to scan your Windows volume, but I doubt if you can defrag it.

You could, however, run Windows Defrag Command Line under Wine, and probably do a good job of it.

---

