---
title: "compressed filesystems on ubuntu?"
date: 2011-10-05
forum: The Cafe
---

### Post by keastes on 2011-10-05
has anyone had any experence with [ZFS-FUSE]("http://zfs-fuse.net/") or [FuseCompress]("http://miio.net/wordpress/projects/fusecompress/")? planing on running rsync to an external HDD for backup and seeing which works best or period for that matter

---

### Post by LowSky on 2011-10-05
ZFS is pretty nice, but why do you need file compression?

---

### Post by keastes on 2011-10-05
> **LowSky said:**
> ZFS is pretty nice, but why do you need file compression?

for the simple reason that my main and backup HDDs are the same size, plus i want some kind of versioning for differential and incremental backups.

---

### Post by mips on 2011-10-05
Why not use rsync with compression of the files?

---

### Post by keastes on 2011-10-05
> **mips said:**
> Why not use rsync with compression of the files?


KISS(Keep It Simple, Stupid or Keep It Super Simple), and compression before backing up is impractical at best seeing as i will be using those files frequently, after backup would make file comparisons more processor intensive, and CPU cycles will be at a premium seeing as im not running new Hardware

---

