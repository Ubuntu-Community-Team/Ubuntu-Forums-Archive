---
title: "How can I restore MySQL db from files?"
date: 2006-10-09
forum: Server Platforms
---

### Post by Laterix on 2006-10-09
hi,

My harddisk crashed and I was able to save mysql files from /var/lib/mysql directory. Those files are *.MYI, *.MYD and *.frm.

Now I have installed Ubuntu and MySQL to the new disk and I'm trying to restore those databases, but it doesn't seem to be possible just replace that directory (/var/lib/mysql) with the old one.

What should I do to get my databases back? This is very important because my work is depending on those database.

---

### Post by shreko on 2006-10-09
I had a failure this summer on win2k machine running MySQL and I was able to restore everything just by restoring files from my file system backup.All my tables are MyISAM type tables. InnoDB might be a little different. Check MySQL forums for help on this. Good luck

---

