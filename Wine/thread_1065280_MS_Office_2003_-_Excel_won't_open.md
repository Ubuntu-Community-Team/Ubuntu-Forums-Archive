---
title: "MS Office 2003 - Excel won't open"
date: 2009-02-09
forum: Wine
---

### Post by Aidan James on 2009-02-09
hi there,

i'm running ubuntu 8.10, wine version 1.1.14, and recently installed microsoft office 2003. every application works great, bar excel, which doesn't really load. the excel load screen comes up, then, immediately after, a popup box appears, saying excel has encountered a problem, and needs to close. even running excel in safe mode, and detect and repair does nothing. sometimes, when i attempt to run excel, this message appears "unable to load dll C:\PROG~FBU\COMM~CP1\MI~EH8HH\DW\DW20.EXE->OLEACC.dll

here is the output, when i run wine excel.exe, from the terminal:

fixme:ole:CoInitializeSecurity (0x413ea8,-1,(nil),(nil),1,3,(nil),72,(nil)) - stub!
err:ole:CoGetClassObject class {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} not registered
err:ole:CoGetClassObject no class object {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} could be created for context 0x1
wine: could not load L"C:\\windows\\system32\\excel.exe": Module not found

does anyone know of a solution? i'd be very grateful for any help anyone can provide.

---

