---
title: "Fallout3 &amp; Issues with xlive.dll"
date: 2009-03-03
forum: Wine
---

### Post by Sugi on 2009-03-03
I tried installing Fallout3 in a compiled version of wine 1.1.8 and I couldn't get anywhere.  The installation went well and I got regedit up and running, but everytime I try running fallout 3 I get an error with xlive.dll.

fixme:win:EnumDisplayDevicesW ((null),0,0xa7f954,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0xa7f71c,0x00000000), stub!
err:dialog:EndDialog got invalid window handle ((nil)); buggy app !?
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x192d50,0x1b71b0): stub
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
[email]midori@midori:~/.bin[/email]/wine1.1.8_fallout3/drive_c/Program Files/Bethesda Softworks/Fallout 3$ err:module:import_dll Loading library xlive.dll (which is needed by L"C:\\Program Files\\Bethesda Softworks\\Fallout 3\\Fallout3.exe") failed (error c0000020).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Bethesda Softworks\\Fallout 3\\Fallout3.exe" failed, status c0000135


I have xlive.dll installed within windows/system and Fallout3's directory.  Is there anything else I am missing?

Thank you,
Sugi

---

### Post by Sugi on 2009-03-11
bump

---

### Post by ario on 2009-03-22
I have the same problem in try to installing GTA IV on wine 1.1.16 under ubuntu 8.10.
I have copied xlive.dll to system32 directory of wine. but nothing happened. it still tells me that xlive.dll not found.
also sometimes i can see that wine needs a DLL library MSVCR90.DLL or MSVCP90.DLL. Which i can not find it in any of my windows Vista directories.:(

---

### Post by NightMKoder on 2009-03-22
Sugi:
Install it from [http://www.microsoft.com/downloads/details.aspx?FamilyID=05013300-5d14-4dc9-9145-991ea1b8e4b0&DisplayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=05013300-5d14-4dc9-9145-991ea1b8e4b0&DisplayLang=en) . Also please make sure you delete the xlive.dll you put in, otherwise it will think it is installed.

Ario:
You really shouldn't copy those (MSVC*) files from windows. These are runtime files, and you can use winetricks to get them. [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) . What you need is vcrun2008.

---

