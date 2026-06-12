---
title: "Samba &amp; Alphabetical Order"
date: 2011-12-12
forum: Server Platforms
---

### Post by cphuntington97 on 2011-12-12
Apparently, samba sends lists of files in a miscellaneous order (optimized for performance). We have some vba code that expects file lists in alphabetical order, just as they would be delivered from a Windows server.

Is there any way to get samba to send file lists in alphabetical order? Performance is not an issue in this environment; functionality absolutely is.

Thanks...

---

### Post by cphuntington97 on 2011-12-14
For anyone who cares: [http://www.samba.org/samba/docs/man/manpages-3/vfs_dirsort.8.html](http://www.samba.org/samba/docs/man/manpages-3/vfs_dirsort.8.html)

Sort directories for all shares:

        [global]
	vfs objects = dirsort


No noticeable performance hit on my Core i5 system.

---

