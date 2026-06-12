---
title: "Copy protection for a folder"
date: 2008-06-22
forum: Security
---

### Post by Debajyoti on 2008-06-22
Dear All,

Can u help me out to find out a way to 'Copy Protect' a folder in Ubuntu 8.04 . But there will be a executable file inside the folder which will run using WINE.


Regards

Debajyoti

---

### Post by p_quarles on 2008-06-22
Well, at a very basic level, it is physically impossible to read-protect and file and then make it executable. That would like trying to read a book that's been destroyed in a fire.

If you're talking about write-protecting the directory, though, that's easy enough:
```
chmod -R -w /path/to/dir
```
That will prevent anyone (apart from root, of course) from writing anything to that directory.

---

### Post by Debajyoti on 2008-07-03
The Folder is getting copy protected but the executable file inside the folder is not running. Please help.
:confused:

---

