---
title: "'Program Files'"
date: 2010-07-01
forum: Wine
---

### Post by Skitsnygg on 2010-07-01
Hi,

I'm tring to install FL Studio 9 using Wine and need to check a couple of the files which would appear in the program files folder.

I've had a look through this forum, and resultantly in the bin/lib folders, but for the life of me can't find what I'm after.

Does anyone know how I can access these files and try to complete the installation?

Any help would be greatly appreciated :D

---

### Post by Skitsnygg on 2010-07-01
Hi,

I am currently trying to install FL Studio 9 through Wine and need to check a couple of files which would normally be located in program files on Windows.

Having looked through previous posts on here, I have search the bin and lib folders but for the life of me can't find anything!

Does anyone know how I would be able to locate these?

Any help would be greatly appreciated :)

---

### Post by Skitsnygg on 2010-07-01
Hi,

I am currently trying to install FL Studio 9 through Wine and need to  check a couple of files which would normally be located in program files  on Windows.

Having looked through previous posts on here, I have search the bin and  lib folders but for the life of me can't find anything!

Does anyone know how I would be able to locate these?

Any help would be greatly appreciated :)

---

### Post by The Cog on 2010-07-01
Wine maintains a dummy drive C in your home folder in a hidden folder called **.wine**. Open nautilus and press Ctrl-H to turn on showing of hidden files and look for .wine/drive_c.

---

### Post by s.fox on 2010-07-01
Hello,

Program files should be located:

```
/home/**$username**/.wine/drive_c/Program Files
```Replace $username with your username

-Silver Fox

---

### Post by sisco311 on 2010-07-02
> **Skitsnygg said:**
> Hi,

I am currently trying to install FL Studio 9 through Wine and need to check a couple of files which would normally be located in program files on Windows.

Having looked through previous posts on here, I have search the bin and lib folders but for the life of me can't find anything!

Does anyone know how I would be able to locate these?

Any help would be greatly appreciated :)

~/.wine/drive_c/Program\ Files

.wine is a hidden directory in your home. You may have to press Ctrl+H to list hidden files/directories.

---

### Post by frodon on 2010-07-02
Moved to Wine forum, threads merged.

Please do not open more than one thread per support request.

---

