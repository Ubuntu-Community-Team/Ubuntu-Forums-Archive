---
title: "Why can't launch mspaint.exe with WIne?"
date: 2010-04-13
forum: Wine
---

### Post by rva1945 on 2010-04-13
I know there are replacements in Ubuntu, but I need to launch it in Ubuntu. When I right-click and select Open with Wine..., nothing happens.

Thanks

---

### Post by JDShu on 2010-04-13
this came up on google

[http://ubuntuforums.org/showthread.php?t=660408](http://ubuntuforums.org/showthread.php?t=660408)

It would help if you tried running mspaint from the command line though so that we can get some error messages and figure out what the problem is. (to do this, locate the exe file in the command line and type "wine mspaint.exe" or whatever the filename is)

---

### Post by rva1945 on 2010-04-13
> **JDShu said:**
> this came up on google

[http://ubuntuforums.org/showthread.php?t=660408](http://ubuntuforums.org/showthread.php?t=660408)

It would help if you tried running mspaint from the command line though so that we can get some error messages and figure out what the problem is. (to do this, locate the exe file in the command line and type "wine mspaint.exe" or whatever the filename is)

Ok, now what do you mean by command line? the Windows CMD command? Did it and nothing happens.

---

### Post by JDShu on 2010-04-13
1. Go to Applications->Accessories->Terminal
2. In the terminal, cd to the directory that contains mspaint.exe (or whatever the name of the executable is) Navigation is similar to a windows command prompt.
3. Once in the correct directory, type "wine mspaint.exe".

---

### Post by asdfoo on 2010-04-14
from memory, mspaint requires mfc42u.dll, it should complain about that if you run it from the terminal

---

### Post by rva1945 on 2010-04-14
> **asdfoo said:**
> from memory, mspaint requires mfc42u.dll, it should complain about that if you run it from the terminal


THANKS!! I just copied mfc42u.dll to .wine/drive_c/windows/system32 and now it mspaint launches successfully from the Terminal (wine mspaint) or by double-click in .wine/drive_c/windows/system32; it doesn't launch if I right-click on c:\windows\system32\mspaint.exe (the WXP partition), but who cares!

Thanks again.

---

### Post by Propulami on 2010-09-15
I cant open a setup.exe file with wine , I have copied a cd on my desktop so as to change it pemissions which was impossible on cd it self, when i try to open it with wine it just does nothing!:-({|=
I installed ubuntu with wubi inside ms windows , thats my problem?
any help?:roll:

---

