---
title: "opengl32.dll error"
date: 2010-07-22
forum: Wine
---

### Post by daz1uk on 2010-07-22
Hi I've got a problem with Wow, it doesn't start when I try to run it, here is an output:


wine "C:\Program Files\World of Warcraft\WoW.exe"
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000005

---

### Post by asdfoo on 2010-07-22
> **daz1uk said:**
> Hi I've got a problem with Wow, it doesn't start when I try to run it, here is an output:


wine "C:\Program Files\World of Warcraft\WoW.exe"
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000005

which version of Wine are you using? 
open a terminal and type `wine --version`

It should print wine-1.2

Do you have the correct video drivers installed?

---

### Post by daz1uk on 2010-07-23
Yes I'm using 1.2, not sure on video drivers because I have another error:

darryl@darryl-laptop:~$ fglrxinfo
Segmentation fault

darryl@darryl-laptop:~$ dmesg | grep fglrx
[  571.285417] fglrxinfo[1504]: segfault at 4 ip 00e1def6 sp bfeaa8d0 error 4 in libGL.so.1.2[db8000+a7000]

---

### Post by cogadh on 2010-07-23
That ain't right, both Wine and fglrxinfo reporting an OpenGL related problem? Sounds like you need to re-install your drivers.

---

### Post by daz1uk on 2010-07-23
I've just installed the drivers from the ATI website, still no change, same errors. you got any ideas?

Thanks for your help

---

### Post by asdfoo on 2010-07-23
maybe you should ask in a different subforum because this isn't related to Wine

---

