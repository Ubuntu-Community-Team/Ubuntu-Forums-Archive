---
title: "issue running setup.exe"
date: 2010-03-27
forum: Wine
---

### Post by dbowlin17 on 2010-03-27
I am being told that the file is not marked as a .exe and therefore wine won't run it. Im using 10.04 Beta 1, any help would be appreciated

---

### Post by ajgreeny on 2010-03-27
Is it an executable zip file as they have an .exe suffix?  If so, I'm not sure how you deal with it in ubuntu

---

### Post by dbowlin17 on 2010-03-27
I extracted the .exe from a .zip. Dunno if that helps.

---

### Post by ajgreeny on 2010-03-28
I that case I doubt if it's an executable zip, as there would be no point in zipping it again.

Unless, of course, it's just one of several files in the zip archive.

 However, again, I have to admit I have no idea how ubuntu handles executable zips, or even if it can.

---

### Post by asdfoo on 2010-03-28
files have read write and execute permission, to set the executable bit, do:

chmod +x setup.exe

---

### Post by krull677 on 2010-03-28
I have this problem. except i'm trying to run it of a cd. mounting an iso or copying the files to the hard drive is not an option. "setup.exe is not marked as executable" dialog box shows and i can't change it because it's read only. is there anyway  of disabling it?

---

### Post by a.walker on 2010-03-28
I got around this once by running the executable from the terminal with the command "wine blah.exe" instead of double-clicking on it.

---

