---
title: "Has anyone tried installing xp to ext2 using the xp ext2 driver?"
date: 2007-07-29
forum: The Cafe
---

### Post by kurty_77 on 2007-07-29
I have recently installed the [http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html") driver on my xp install, and it works great. Now i am wondering, if I were to re-install windows, is there a way to load this driver at install time, and install windows to a pre-fromatted ext2/3 partition? or a way to move my install to ext 2/3, this way I would never need ntfs again, and it would simplify a lot of things in linux.

thanks,

Kurt

---

### Post by mips on 2007-07-29
To my knowledge this cannot be done.

Being able to read/write to a certain filesystem does not mean that an OS will install to that filesystem. This is not only the case in Windows but also in Linux & Unix etc

See [http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)
> This software does not achieve booting a Windows operating system from an Ext2 volume.

---

### Post by Lolicon on 2007-07-31
However, you can have it install itself using n-lite.

---

