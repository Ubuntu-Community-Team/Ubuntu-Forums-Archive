---
title: "Running a distro from USB inside Windows"
date: 2011-04-27
forum: The Cafe
---

### Post by Camuflage on 2011-04-27
I have this big doubt, how can i run a USB distro, inside Windows? I would like just connect and disconnect a pendisk in any local and run the linux distro up-to-date where i could do for example homebanking safely without any worries or carry data ready to be shown.

I found this useful site: [http://www.pendrivelinux.com/run-a-live-linux-cd-from-within-windows/#more-232](http://www.pendrivelinux.com/run-a-live-linux-cd-from-within-windows/#more-232) but the scrip only runs if you get a cd or a dvd in the drive, my idea is to pick the the script and get it into the usb with the distro, só it can be really portable.

The code that batch uses is this:

```
REM Qemu file launcher ©2007 http://pendrivelinux.com
REM This file will start a CD from Windows using Qemu.
@ECHO OFF
cls
echo.
echo =====================================================================
echo Qemu CD Launcher Copyright 2007 http://pendrivelinux.com
echo =====================================================================
echo.
echo This file will launch the inserted CD from your Windows PC using QEMU
echo Please note that the CD will also be launched accelerated with Kqemu.
echo.
echo.
echo This utility is being offered for free with absolutely no warranty in
echo hopes that it will be useful. USE IT AT YOUR OWN RISK!
echo.
echo.
pause
cls

if exist c:\windows\system32\drivers\kqemu.sys ( 
goto launch) else (
echo.
echo STAGE 1: Checking for and installing accelerated driver . . .
echo Vista users need to allow permissions to install Kqemu if asked
goto kqemu) 
cls

:kqemu 
.\qemu\kqemu.exe
echo.
echo STAGE 2: The Kqemu accelerator has been offered for installation

:launch
echo. 
echo LINUX IS NOW RUNNING, Do not close this windows while Linux is running!
echo Close only once Linux has shutdown (after the prompt to eject CD)

.\qemu\qemu -L .\qemu -kernel-kqemu -std-vga -localtime -soundhw all -m 512 -cdrom /dev/cdrom -boot d
```

By the way this Qemu verion is very old, where can i find an update for it?
Basically the script and the Qemu file need an update.

Is someone available to update this thingie and put it running?

Thanks!

---

