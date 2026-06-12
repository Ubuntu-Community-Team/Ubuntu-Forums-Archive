---
title: "DLL install doesn't work"
date: 2009-03-20
forum: Wine
---

### Post by DrPepper836 on 2009-03-20
For some reason, Wine won't install DLL's for me. Every time that I need to install a dll to play a game, it doesn't take. It gives the same error message that it is supposed to before you add a dll. Other programs that don't require dll's, work perfectly. In Zoo Tycoon 2, for example, I get it to install perfectly. Then, I download the mfc42.dll file that it needs to run. I put it in both the system folder and the folder with the zt.exe file. I add the zt.exe file to the application list and add the override. Same error message as before! I've tried the override on every setting, with and without the file extension, and nothing works. The same thing happens with any program that requires a dll. What am I doing wrong?

---

### Post by cogadh on 2009-03-20
You need to put the DLL in the system32 directory, not the system directory or the app's directory, then apply a native override for it in winecfg. That being said, just adding and overriding a DLL does not guarantee that it will work, some apps just won't work, despite the addition of a native DLL.

---

