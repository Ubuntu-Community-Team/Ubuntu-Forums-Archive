---
title: "Can't install or run PhotoPlusX2 from .exe"
date: 2010-04-14
forum: Wine
---

### Post by myMindsAvatar on 2010-04-14
Hi everyone,

First off, thanks for showing me the light with GNU/Linux, Ubuntu in particular.

Anyway, to point. I'm trying to install some software I had bought before I knew of Linux and am trying to install it through PlayOnLinux v3.7.3 (PhotoPlus X2, from Serif UK Ltd). Only trouble is, once I select manual install or autorun, the correct setup.exe file is selected but nothing happens (the POL window says "Please press Next only when installation is fully complete" but it doesn't do anything). I've left it for several minutes and nothing happens, the CD-ROM doesn't even stir, nothing.

Odd thing, is that I can't even get it to install through Nautilus (Open with Wine Windows Program Loader), so I don't think it's necessarily a POL or Wine thing...but I don't know what else it could be...help?

(I have already successfully installed Office 2007 via POL, didn't know if this titbit would help but there you go)

Many thanks
Richard ~

---

### Post by asdfoo on 2010-04-14
> **myMindsAvatar said:**
> Hi everyone,

First off, thanks for showing me the light with GNU/Linux, Ubuntu in particular.

Anyway, to point. I'm trying to install some software I had bought before I knew of Linux and am trying to install it through PlayOnLinux v3.7.3 (PhotoPlus X2, from Serif UK Ltd). Only trouble is, once I select manual install or autorun, the correct setup.exe file is selected but nothing happens (the POL window says "Please press Next only when installation is fully complete" but it doesn't do anything). I've left it for several minutes and nothing happens, the CD-ROM doesn't even stir, nothing.

Odd thing, is that I can't even get it to install through Nautilus (Open with Wine Windows Program Loader), so I don't think it's necessarily a POL or Wine thing...but I don't know what else it could be...help?

(I have already successfully installed Office 2007 via POL, didn't know if this titbit would help but there you go)

Many thanks
Richard ~

To work out what's going on, we need to first establish that you are using the latest version of Wine.

open a terminal and type:

wine --version

it should say 1.1.42.

With the cd in the drive, at the console:

cd /media/cdrom 
wine setup.exe


Post the terminal output back here.

---

### Post by myMindsAvatar on 2010-04-15
Thanks for getting back to me. I've done as requested and it's certainly raised an interesting issue with regards to the wine version (I thought I had 1.1.42, but this is saying 1.0.1, see below). Saying that, I have both Wine and POL installed on here and POL definitely says 1.1.42 (I realise POL is just the frontend package to Wine, so I guess either it's lying or most likely has been installed as a completely separate package)...

Many thanks,
Richard ~


richard@tilde:~$ wine --version
wine-1.0.1
richard@tilde:~$ cd /media/cdrom
richard@tilde:/media/cdrom$ wine setup.exe
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"D:\\setup.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"D:\\setup.exe" failed, status c0000135

---

