---
title: "dll library problem makes application crash"
date: 2011-06-25
forum: Wine
---

### Post by 5PUTN|K on 2011-06-25
I am trying to run a game using wine but i get this error in the terminal and the game crashes I believe this is caused because of some dll file anyway this is the error message i keep getting

> deniz@deniz-laptop:~$ wine "/home/deniz/.wine/dosdevices/c:/Program Files/Gravity/Ragnarok Online/Ragnarok.exe"
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x110fb0 0
err:module:import_dll Loading library MFC42.DLL (which is needed by L"C:\\Program Files\\Gravity\\Ragnarok Online\\Ragnarok.exe") failed (error c000007b).
err:module:import_dll Loading library MSVCP60.dll (which is needed by L"C:\\Program Files\\Gravity\\Ragnarok Online\\Ragnarok.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Gravity\\Ragnarok Online\\Ragnarok.exe" failed, status c0000135
deniz@deniz-laptop:~$ err:menubuilder:write_freedesktop_mime_type_entry error writing file /home/deniz/.local/share/mime/packages/x-wine-extension-/bzw.xml
err:menubuilder:write_freedesktop_association_entry error writing association file "/home/deniz/.local/share/applications/wine-extension-/bzw.desktop"

i think module:import_dll Loading library means that theres a problem in wine library

---

### Post by An Sanct on 2011-06-25
MFC42 and MSVCP60 are both dlls, you can load with wine.

Take a look at this FAQ and search for "MFC42" and "MSVCP60" - more exact location [here]("http://wiki.winehq.org/FAQ#head-d10f6828f4c34da2ef34f0bf8a9d576ae78bb2aa"). Use WineTricks to initialize those dlls.

---

### Post by 5PUTN|K on 2011-06-26
Im still getting the same error

> deniz@deniz-laptop:~$ wine "/home/deniz/.wine/dosdevices/c:/Program Files/Gravity/Ragnarok Online/Ragnarok.exe"
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x110fb0 0
err:module:import_dll Loading library MFC42.DLL (which is needed by L"C:\\Program Files\\Gravity\\Ragnarok Online\\Ragnarok.exe") failed (error c000007b).
err:module:import_dll Loading library MSVCP60.dll (which is needed by L"C:\\Program Files\\Gravity\\Ragnarok Online\\Ragnarok.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Gravity\\Ragnarok Online\\Ragnarok.exe" failed, status c0000135
deniz@deniz-laptop:~$ err:menubuilder:write_freedesktop_mime_type_entry error writing file /home/deniz/.local/share/mime/packages/x-wine-extension-/bzw.xml
err:menubuilder:write_freedesktop_association_entry error writing association file "/home/deniz/.local/share/applications/wine-extension-/bzw.desktop"

---

### Post by 5PUTN|K on 2011-06-26
some people say this error means "bad image" but the same dll file works fine on windows so i guess this problem is related with loading the dll file but not the file itself

---

### Post by cwwilson721 on 2011-06-26
After a VERY fast Google search (which I assume you did)for mfc42.dll :

INSTALL VCRUN6 THROUGH WINETRICKS

Google is your friend.

And read the stickies in this forum BEFORE asking for help. If you would have, you would have SEEN THIS in wine hq DB:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=928](http://appdb.winehq.org/objectManager.php?sClass=version&iId=928)

Or, even better:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=928&iTestingId=62377](http://appdb.winehq.org/objectManager.php?sClass=version&iId=928&iTestingId=62377)

---

### Post by An Sanct on 2011-06-26
The [Wine FAQ]("http://wiki.winehq.org/FAQ#head-d10f6828f4c34da2ef34f0bf8a9d576ae78bb2aa") I posted should have helped (mentioning those two and other similar libraries...)

---

### Post by cwwilson721 on 2011-06-26
> **An Sanct said:**
> The [Wine FAQ]("http://wiki.winehq.org/FAQ#head-d10f6828f4c34da2ef34f0bf8a9d576ae78bb2aa") I posted should have helped (mentioning those two and other similar libraries...)Thus, the reason I said to

READ THE STICKIES.

It states in there to look in the app db, and I did, and THERE IT WAS.

---

