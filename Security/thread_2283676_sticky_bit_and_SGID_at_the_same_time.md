---
title: "sticky bit and SGID at the same time ?"
date: 2015-06-23
forum: Security
---

### Post by fkkroundabout on 2015-06-23
i've been feeling especially confused today.

can you think of a reason to use SGID and sticky bit on a directory at the same time ??

i figured it could definitely help with accidents and preserves directories entirely, but has no effect on users actually editing files, so cannot help with intentional damage, unless in combination with other features such as umasks or attributions. right ???

or is it simply better to choose the options other than sticky bit + SGID for security ???

---

### Post by bab1 on 2015-06-23
> **fkkroundabout said:**
> i've been feeling especially confused today.

can you think of a reason to use SGID and sticky bit on a directory at the same time ??

i figured it could definitely help with accidents and preserves directories entirely, but has no effect on users actually editing files, so cannot help with intentional damage, unless in combination with other features such as umasks or attributions. right ???

or is it simply better to choose the options other than sticky bit + SGID for security ???
No.  I don't see any reason to use the sticky bit for anything other than something Like /tmp where all users *_store_* data.  The sgid bit is used when users want to *_share ownership_* of data via a common user group.

The sgid bit allows Linux distros that are configured with User Private Groups (UPG) provide for group ownership inheritance, thereby allowing a specific user group to own a section of a file system (subdirectories).  This could allow a directory or file  to be owned by a user group (i.e. devs) with multiple users in the group.  Every user can create data that will be owned by the user group (devs).  It's not for security per se.

What exactly are your security concerns?

---

