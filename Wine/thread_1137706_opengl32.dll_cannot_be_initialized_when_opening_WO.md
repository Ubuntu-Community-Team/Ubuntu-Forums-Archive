---
title: "opengl32.dll cannot be initialized when opening WOW"
date: 2009-04-25
forum: Wine
---

### Post by balusk on 2009-04-25
I have recently bought a computer and installed 64 bit ubuntu 9.04 on it.  I used envy to install my nvidia driver, then used wine to install World of Warcraft.  The launcher will open fine, but when it goes to load the WOW program, it stalls a moment and then does nothing.  I ran it in a terminal to see what was happening, and got the error

[EMAIL="balusk@ubuntudesktop:%7E/.wine"]balusk@ubuntudesktop:~/.wine[/EMAIL]/drive_c/Program Files/World of Warcraft$ wine Wow.exe -opengl
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\Wow.exe" failed, status c0000005

I am running Wine version 1.1.19, and my graphics card is an nvidia gtx295

I have searched all over the place trying to find a solution, but nothing has helped.  I've only started using linux in the last few weeks, so I'm not extremely familiar with it.  Any help would be appreciated

---

### Post by NightMKoder on 2009-04-25
If you have other things installed under wine, they may end up doing this. Especially if you have any dll overrides.

Start with a fresh wine prefix.

---

### Post by balusk on 2009-04-26
I tried moving the .wine folder to .wine_backup, then running wine cfg, then moving the wow folder over to the new c_drive folder, but it still gives me the same error.

I can see the dll in the system32 folder.  I was wondering if it had anything to do with the fact I'm using 64 bit.

---

### Post by asdfoo on 2009-04-26
> **balusk said:**
> I tried moving the .wine folder to .wine_backup, then running wine cfg, then moving the wow folder over to the new c_drive folder, but it still gives me the same error.

I can see the dll in the system32 folder.  I was wondering if it had anything to do with the fact I'm using 64 bit.

no. Wine works fine on 64bit, it sounds like your video drivers aren't configured or are not installed properly

please show the output of: glxinfo | grep -v 0x

---

### Post by balusk on 2009-04-27
sure enough, I ran that, and it said something like no driver, so I installed the video driver manually and it fixed it.  It seems Envy does not install the correct driver for a gtx295.  Thanks for all of the help

---

