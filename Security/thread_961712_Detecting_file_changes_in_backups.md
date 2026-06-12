---
title: "Detecting file changes in backups"
date: 2008-10-28
forum: Security
---

### Post by dtoader on 2008-10-28
How can I detect file changes in backups from day to day?
I'm using my Ubuntu host for file storage.

My 
/home/* 
/etc/* 
are currently backed up to a USB connected hard drive 
with Sbackup.

My project:

I'd like to keep a trail of document changes from day to day.

Some files (binaries) are pretty large in size so I'd like
to see bitlevel changes or file corruption.

I'm not interested in changes to system files (i.e. /proc) or
log files (/var/log)

I'd like to see the file change history in
/etc
/home

I see two choices so far:
1. [archfs]("http://code.google.com/p/archfs/") with [rdiff-backup]("http://www.nongnu.org/rdiff-backup/")
2. [md5mon]("http://www.geocities.com/CapeCanaveral/Lab/5735/1/md5mon.html")

I'm leaning toward archfs with rdiff-backup as I can see file
diffs.  md5mon can tell me which files have changed but can
not provide me with file diffs.

Does anyone know of other utilities I can use to see
file change history?

I'm hesitant to use cvs/svn as they could conflict with
system operation and I estimate would probably be slow 
(i.e. imagine checking out and checking in a 
large sized /home directory)  cvs and svn are revision control
utilities for code and would probably pe problematic with what
I'm trying to do.

---

### Post by OpenSourceFuture on 2008-10-28
[http://md5deep.sourceforge.net/](http://md5deep.sourceforge.net/)

Not quite sure if thats as user friendly and pretty as what your looking for but it will detect changes.

---

