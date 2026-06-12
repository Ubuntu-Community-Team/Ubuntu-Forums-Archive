---
title: "PhotoShop 7.0 cannot initialize because &quot;scratch disks are full&quot;"
date: 2010-04-04
forum: Wine
---

### Post by ubdime on 2010-04-04
Adobe Photoshop 7.0 (relative insists on using old 7.0) installs fine. It comes with 2 programs, PhotoShop and ImageReady. IR seems to work fine. When starting PhotoShop, it throws an error "Could not initialize Photoshop because the scratch disks are full."

I hold down control and alt when starting and set 1st scratch disk to C:\, then 2nd to Z:\. Doesn't work. I create Y:\ to point to /tmp and throw that in there too (in all permutable orders). I tried holding down shift too and deleted settings. None of this works. (Computer has over 1.5tb free and 4gb memory.)

shirley@ss:~$ env WINEPREFIX="/home/shirley/.wine" wine "C:\Program Files\Adobe\Photoshop 7.0\Photoshop.exe"
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:font:WineEngRemoveFontResourceEx (L"C:\\Program Files\\Adobe\\Photoshop 7.0\\Required\\ADMUI3.fon", 0, (nil)): stub
err:twain:twain_add_onedriver Source->(DG_CONTROL,DAT_IDENTITY,MSG_GET) failed!
err:twain:twain_add_onedriver Source->(DG_CONTROL,DAT_IDENTITY,MSG_GET) failed!
fixme:font:WineEngRemoveFontResourceEx (L"C:\\Program Files\\Adobe\\Photoshop 7.0\\Required\\ADMUI3.fon", 0, (nil)): stub
fixme:font:WineEngRemoveFontResourceEx (L"C:\\Program Files\\Adobe\\Photoshop 7.0\\Photoshop.fon", 0, (nil)): stub

Tried googling for hours and could not find any other wine users with this issue.

---

### Post by asdfoo on 2010-04-05
> **ubdime said:**
> Adobe Photoshop 7.0 (relative insists on using old 7.0) installs fine. It comes with 2 programs, PhotoShop and ImageReady. IR seems to work fine. When starting PhotoShop, it throws an error "Could not initialize Photoshop because the scratch disks are full."

I hold down control and alt when starting and set 1st scratch disk to C:\, then 2nd to Z:\. Doesn't work. I create Y:\ to point to /tmp and throw that in there too (in all permutable orders). I tried holding down shift too and deleted settings. None of this works. (Computer has over 1.5tb free and 4gb memory.)

shirley@ss:~$ env WINEPREFIX="/home/shirley/.wine" wine "C:\Program Files\Adobe\Photoshop 7.0\Photoshop.exe"
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:font:WineEngRemoveFontResourceEx (L"C:\\Program Files\\Adobe\\Photoshop 7.0\\Required\\ADMUI3.fon", 0, (nil)): stub
err:twain:twain_add_onedriver Source->(DG_CONTROL,DAT_IDENTITY,MSG_GET) failed!
err:twain:twain_add_onedriver Source->(DG_CONTROL,DAT_IDENTITY,MSG_GET) failed!
fixme:font:WineEngRemoveFontResourceEx (L"C:\\Program Files\\Adobe\\Photoshop 7.0\\Required\\ADMUI3.fon", 0, (nil)): stub
fixme:font:WineEngRemoveFontResourceEx (L"C:\\Program Files\\Adobe\\Photoshop 7.0\\Photoshop.fon", 0, (nil)): stub

Tried googling for hours and could not find any other wine users with this issue.

a) you should cd to the install directory and then run the program
b) which version of Wine are you using? 1.1.42 is the most recent

---

