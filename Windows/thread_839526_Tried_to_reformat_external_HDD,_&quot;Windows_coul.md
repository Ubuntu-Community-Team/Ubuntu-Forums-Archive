---
title: "Tried to reformat external HDD, &quot;Windows could not complete formatting&quot;"
date: 2008-06-24
forum: Windows
---

### Post by Redrazor39 on 2008-06-24
And now I can't mount this drive into openSUSE and Windows Vista will not recognize it. Is there a way to format this drive? I would like to do it in NTFS.

I'm not running ubuntu, I switched to openSUSE, but I do have the 8.04 live CD if that might work.

---

### Post by NilsE on 2008-06-24
Boot to the live cd and use the partition editor under System > Administration.  It may not be there (I don't remember) so go into a terminal and run gparted

---

### Post by LaRoza on 2008-06-24
> **Redrazor39 said:**
> And now I can't mount this drive into openSUSE and Windows Vista will not recognize it. Is there a way to format this drive? I would like to do it in NTFS.

I'm not running ubuntu, I switched to openSUSE, but I do have the 8.04 live CD if that might work.

Use gparted to wipe it (or go into the Disk Manager of Vista) and try again.

---

