---
title: "WINE Doesn't seem to work with my laptop"
date: 2009-07-13
forum: Wine
---

### Post by mrblaineng on 2009-07-13
Hi guys, I recently got WINE running on my desktop computer and was impressed and decided to put WINE on my laptop too. I typed the command sudo apt-get install wine and wine installed without any errors or anything. Next I put in my Warcraft 3 CD and tried to install it, but when I click on the install.exe file I get this error.

[/media/RALLY2/War/install.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/RALLY2/War/install.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/RALLY2/War/install.exe or
          /media/RALLY2/War/install.exe.zip, and cannot find /media/RALLY2/War/install.exe.ZIP, period.

The laptop is a Dell Inspirion E1505 if that helps.

---

### Post by Tibuda on 2009-07-13
It looks like File Roller is trying to open the exe file. Try right-clicking the exe file to open it with Wine.

---

### Post by mrblaineng on 2009-07-14
> **danielrmt said:**
> It looks like File Roller is trying to open the exe file. Try right-clicking the exe file to open it with Wine.

Yup that was the problem alright. Thanks!!!

---

