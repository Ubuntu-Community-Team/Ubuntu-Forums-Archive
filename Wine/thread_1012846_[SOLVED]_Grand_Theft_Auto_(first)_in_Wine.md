---
title: "[SOLVED] Grand Theft Auto (first) in Wine"
date: 2008-12-16
forum: Wine
---

### Post by noway on 2008-12-16
Ubuntu 8.10 AMD64
Wine Version: 1.0.1-0ubuntu2

I downloaded the free *and updated* version of Grand Theft Auto from [http://www.rockstargames.com/classics/gta.html](http://www.rockstargames.com/classics/gta.html) and I'm trying to install it in Wine but when I run SETUP.EXE I get a black window with the title "C:\windows\system32\winevdm.exe" (see attachment).

I have tried setting Wine to Windows 95, Windows 2000 and Windows XP, still no luck. 

winedgb shows me this:
WineDbg starting on pid 003f
0x7b879023: movl %edi,0x0(%esp)

---

### Post by noway on 2008-12-18
bump

---

### Post by noway on 2008-12-20
bump

---

### Post by DirtDawg on 2008-12-20
Run it from the command line. There will usually be an error message that might help solve your problem.
```
wine ~/path/to/GTA.exe
```

---

### Post by noway on 2008-12-22
I had deleted the files but when you replied I unpacked them again and then it just worked. Not sure why it wouldn't start earlier. After that all I had to do was to download MFC42.DLL from some site and put it in ~/.wine/drive_c/windows/system32 to start setup. The game is running fine. Thanks for trying to help.

---

