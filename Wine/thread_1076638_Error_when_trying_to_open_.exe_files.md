---
title: "Error when trying to open .exe files"
date: 2009-02-21
forum: Wine
---

### Post by PwnCakes193 on 2009-02-21
I get this whenever I try to run a .exe file.

[/home/tom/Desktop/utorrent.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/tom/Desktop/utorrent.exe or
          /home/tom/Desktop/utorrent.exe.zip, and cannot find /home/tom/Desktop/utorrent.exe.ZIP, period.


how do I fix this?

---

### Post by cogadh on 2009-02-21
It appears that EXEs are not properly associated with Wine. Try right-clicking on the exectuable and choosing "open with Wine".

---

