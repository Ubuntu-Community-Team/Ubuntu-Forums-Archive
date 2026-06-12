---
title: "Problem installing program from CD using WINE"
date: 2010-03-21
forum: Wine
---

### Post by WhiteSphinx on 2010-03-21
I am currently running Ubuntu 10.4 (Updated 2/20/2010).  How can I install a program from a CD using WINE?  Ubuntu will not allow the program to execute.  I get the following error: ---> Setup.exe is not marked as executable. <---  There seems to be no way to change the permissions here.

---

### Post by Toffeeapple on 2010-03-21
Are you doing, in a terminal ...
```
wine /path to where ever you CD is mounted/Setup.exe
```
?

---

### Post by WhiteSphinx on 2010-03-21
**That did get the installer to start** - but then it crashed.  I am trying to install PrintMaster Platinum 11.  I had it working perfectly in Ubuntu 8.10.  I can't seem to get it even installed in Ubuntu 10.4 however.

---

### Post by phibxr on 2010-03-21
> **WhiteSphinx said:**
> I am currently running Ubuntu 10.4 (Updated 2/20/2010).  How can I install a program from a CD using WINE?  Ubuntu will not allow the program to execute.  I get the following error: ---> Setup.exe is not marked as executable. <---  There seems to be no way to change the permissions here.

Have you tried copying all of the content on the CD to a directory on your harddrive and then running it? In some cases, that might help.

---

