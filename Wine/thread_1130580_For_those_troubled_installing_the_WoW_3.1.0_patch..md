---
title: "For those troubled installing the WoW 3.1.0 patch..."
date: 2009-04-19
forum: Wine
---

### Post by ptn107 on 2009-04-19
So nobody else wastes three days trying to figure this out...

If your trying to launch WoW after patching to 3.1.0 and you get file corruption errors, check your filesystem type on the partition WoW and Wine are on.  Each time I launched WoW it would be a different file that [it claimed] was corrupt.  Turns out it was because the partition was ext4.  For whatever reason WoW doesn't like it.  Reformatting the partition back to ext3 fixed it.  Just fyi.

---

