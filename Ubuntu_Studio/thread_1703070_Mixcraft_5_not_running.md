---
title: "Mixcraft 5 not running"
date: 2011-03-08
forum: Ubuntu Studio
---

### Post by RichardC400 on 2011-03-08
I have Ubuntu Desktop 10.10
I recently installed Mixcraft 5 using wine
I have a file on my desktop now Mixcraft 5.desktop (which as i understand it is a shortcut.)
I go into my .wine folder and find the folder where it has the exe file and run that through wine on my terminal.
I get these errors:

> err:module:import_dll Library WMVCore.DLL (which is needed by L"C:\\Program Files\\Acoustica Mixcraft 5\\acuvidtl.dll") not found
err:module:import_dll Library acuvidtl.dll (which is needed by L"C:\\Program Files\\Acoustica Mixcraft 5\\sndengine.dll") not found
err:module:import_dll Library sndengine.dll (which is needed by L"C:\\Program Files\\Acoustica Mixcraft 5\\mixcraft5.exe") not found
err:module:import_dll Library WMVCore.DLL (which is needed by L"C:\\Program Files\\Acoustica Mixcraft 5\\acuvidtl.dll") not found
err:module:import_dll Library acuvidtl.dll (which is needed by L"C:\\Program Files\\Acoustica Mixcraft 5\\mixcraft5.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Acoustica Mixcraft 5\\mixcraft5.exe" failed, status c0000135


what is going on here and how can i get mixcraft working properly through wine?

---

### Post by Pablo_F on 2011-03-09
Sorry I don't know how to help but I suggest you ask in the winehq forums or mailing list. 

Cheers! Pablo

---

### Post by cchhrriiss121212 on 2011-03-09
It's saying you need those dll's in order to run the program. If you have the program installed on Windows, you can just copy them over.

Wine doesn't work at all for many Windows programs, and seeing as Mixcraft 5 does not have a page at the WineHQ database, I'm guessing it won't work very well even if it does start up. Try looking at some of the Linux native programs before using Wine.

---

