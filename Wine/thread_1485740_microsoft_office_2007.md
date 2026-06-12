---
title: "microsoft office 2007"
date: 2010-05-17
forum: Wine
---

### Post by Drenriza on 2010-05-17
When trying to install microsoft office 2007 (from cd) i double tab the setup.exe and then i get this error

Archive:  /media/OFFICE12/setup.exe
[/media/OFFICE12/setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/OFFICE12/setup.exe or
          /media/OFFICE12/setup.exe.zip, and cannot find /media/OFFICE12/setup.exe.ZIP, period.

Microsoft office has platinum rating, what am i doing wrong? i'm not used to using wine so hopefully somebody can help me.

Thanks on advance

---

### Post by Drenriza on 2010-05-17
Bump.

---

### Post by Drenriza on 2010-05-17
The file '/home/cristian/Skrivebord/downloads/dotnetfx3setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

cristian@cristian-desktop:~$ wine --version
wine-1.1.42

What can you do?

---

### Post by Arkish0 on 2010-05-28
i been trying to install office 2007 on my computer for 3 weeks now hahaha i found this page .. i did it.. [this]("http://www.mikesouthby.co.uk/2009/11/ubuntu-9-10-installing-microsoft-office-2007/") is how i did it and it all went perfect..

a friend did [this]("http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-9-04/") and it also went nice

one step is to change your current version of wine to an older one ... they recommend 1.1.14.. if you already have things running on your wine .. you might want to try installing several versions of wine at the same time... i have not done this but ive found many information on forums... 

by the way im running ubuntu 10.04 but its pretty much the same process as in 9.10.. good luck!

the only thing missing for now is to get all the fonts since the default is kinda weird =) but word, power point, excel ALL completely functional for me

---

