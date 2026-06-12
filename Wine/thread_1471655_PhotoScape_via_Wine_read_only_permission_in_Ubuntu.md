---
title: "PhotoScape via Wine: read only permission in Ubuntu 10.04"
date: 2010-05-03
forum: Wine
---

### Post by daquirm on 2010-05-03
Hello,

Please help me with following problem:
After installing Ubuntu 10.04, I'm unable to save any changes when editing images in PhotoScape. It's running withe read only permission. In Ubuntu 9.10 everything worked. I tried to run wine as root but it didn't help.
I have following configuration:

Ubuntu 10.04 64bit
Wine 1.1.42 (tried Windows XP and Windows 7 compatibility mode)
trying to run PhotoScape v3.40

This is the output from terminal:
```
env WINEPREFIX="/home/daquirm/.wine" wine "C:\Program Files\PhotoScape\PhotoScape.exe" 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC" (8.0.50608.0)
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 0 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 1 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 2 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 4 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 0 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 1 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 2 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 4 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 3 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 0 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 1 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 2 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 4 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 0 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 1 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 2 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 4 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 3 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 0 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 1 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 2 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 4 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 0 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 1 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 2 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 4 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 3 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 0 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 1 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 2 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 4 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 0 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 1 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 2 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 4 0x316054 stub!
fixme:gdiplus:GdipIsStyleAvailable 0x187d20 3 0x316054 stub!
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:gdiplus:GdipSetImageAttributesWrapMode not implemented
fixme:win:LockWindowUpdate (0x1006e), partial stub!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:gdiplus:GdipGetPropertySize not implemented
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x1006e), partial stub!
fixme:shell:SHGetDataFromIDListA SHGDFIL 3 stub
fixme:shell:SHGetDataFromIDListA SHGDFIL 3 stub
fixme:shell:SHGetDataFromIDListA SHGDFIL 3 stub
fixme:shell:SHGetDataFromIDListA SHGDFIL 3 stub
fixme:shell:SHGetDataFromIDListA SHGDFIL 3 stub
fixme:shell:SHGetDataFromIDListA SHGDFIL 3 stub
fixme:shell:SHGetDataFromIDListA SHGDFIL 3 stub
fixme:shell:SHGetDataFromIDListA SHGDFIL 3 stub
fixme:shell:SHGetDataFromIDListA SHGDFIL 3 stub
fixme:shell:SHGetDataFromIDListA SHGDFIL 3 stub
fixme:shell:SHGetDataFromIDListA SHGDFIL 3 stub
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x1006e), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
```

---

### Post by cogadh on 2010-05-03
First of all NEVER, EVER RUN WINE AS ROOT! It not only screws up the permissions on your .wine directory, it opens your system up to potential damage from malicious Windows software.

As for the problem, I ran into a similar issue when trying to patch a Windows game running in Wine. I had to go into the game's install directory and set the permission on all files associated with the game to allow both read and write permissions. The new default appears to be read only. You might try doing the same in the PhotoScape directory.

---

### Post by daquirm on 2010-05-03
Thanks for your reply. I'm the owner of .wine directory, subdirectories and all files that I'm trying to edit. But it just doesn't work. I have no idea what's the difference between Ubuntu 9.10 and 10.04, in Karmic it just works out of box.

---

### Post by cogadh on 2010-05-04
You can be the owner of a directory and still only have read permissions. Check what rights the owner account has on those files, it's probably only "read and execute", not full read, execute and *write* permissions.

---

### Post by daquirm on 2010-05-05
Actually I set the permission of .wine directory and the edited files (and all subdirectories and files) to read and write permission for all users via nautilus just to make sure there's no permission violation.

Still no success. Are there any permissions, that can't be set via nautilus (running with root access), or is the problem in something else?

---

### Post by szprott on 2010-05-05
I have the same problem ;(

---

### Post by daquirm on 2010-05-05
I tried to downgrade Wine to version 1.1.31 which I'm using in Ubuntu 9.10 and it works for 10.04 too. So it looks like a Wine bug. Anyway the problem is solved for me...

---

