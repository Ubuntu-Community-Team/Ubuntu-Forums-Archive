---
title: "Can't run anything on wine I get an error message"
date: 2009-07-28
forum: Wine
---

### Post by babujbf on 2009-07-28
Hey guys Ive been trying to run apps such as utorrent and rapidownload and I always get the same error message.

[/home/babu/Desktop/utorrent.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/babu/Desktop/utorrent.exe or
          /home/babu/Desktop/utorrent.exe.zip, and cannot find /home/babu/Desktop/utorrent.exe.ZIP, period.

Has this happen to any of you?

---

### Post by DOS4dinner on 2009-07-28
Your OS is trying to open it with the archive manager. You have to tell it to open with wine.

Run the command with "wine" before it. ex:

wine utorrent.exe

Also, you can right click on the file, go to properties, and set what to open with; select "Wine, windows program loader"

---

