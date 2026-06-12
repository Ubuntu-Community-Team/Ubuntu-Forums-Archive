---
title: "Administering/monitoring windows environments from Ubuntu"
date: 2010-06-17
forum: Server Platforms
---

### Post by Loyd Gravitt on 2010-06-17
I am a Database Administrator who manages both Oracle databases on Solaris and SQL Server databases on Windows.  I use one Ubuntu workspace to keep multiple tabbed gnome terminal sessions into each of my database servers (windows filesystems are mounted as Linux mountpoints using cifs).

To keep a constant watch on my Unix/Oracle logs is easy using tail -f to watch error messages come in throughout the day.  But for windows, even though I can use tail -f, the log files do not refresh real time like they do in UNIX land.  Is there any way I can use some tool or package to replicate the functionality of unix tail -f on a windows ntfs file system mounted on Ubuntu?

My current version is Ubuntu 9.10.

Thanks in advance!!!!

---

