---
title: "XP Folder Permissions"
date: 2008-11-10
forum: Security
---

### Post by cowboy.bebop on 2008-11-10
Is it possible to set Folder permissions in XP using the ubuntu Live CD so that I can access the XP from a different drive using another HDD with XP on it that I have access to. That...

Or does Ubuntu have a backup utility that I can backup my XP media rather than copying individual folders one by one?

---

### Post by cariboo on 2008-11-10
XP doesn't use unix like permissions, just use sudo to run file operations on an NTFS partition. You can use:

```
gksu nautilus
```

To run multiple file operations. Gksu runs nautilus as root, so youshould be able to do anything you need.

Jim

---

### Post by randy78 on 2008-11-11
Also, [http://gparted.sourceforge.net/larry/move/move.htm]("http://gparted.sourceforge.net/larry/move/move.htm")GParted has a copy/clone feature...

---

