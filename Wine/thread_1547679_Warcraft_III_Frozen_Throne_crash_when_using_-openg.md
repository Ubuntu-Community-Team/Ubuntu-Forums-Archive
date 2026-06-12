---
title: "Warcraft III Frozen Throne crash when using -opengl"
date: 2010-08-07
forum: Wine
---

### Post by ALF102 on 2010-08-07
I try to run Warcraft III uusing the -opengl command but it seems it crashed and it gives me the "Fatal Error" message. But if I try to run it without the opengl command, it runs well but yeah..laggy. Has this got anything to do with compiz or my graphic driver?

I'm running Wine 1.2
Ubuntu 10.04
Mobile Intel 4 Series

---

### Post by asdfoo on 2010-08-07
graphic driver probably:

[http://wiki.winehq.org/FAQ#get_log](http://wiki.winehq.org/FAQ#get_log)

---

### Post by ALF102 on 2010-08-07
Well, here's the thing that came out after I run:

env WINEPREFIX="/home/username/.wine" wine "/home/username/war3/Frozen Throne.exe" -opengl
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f108,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f60c,0x00000000), stub

---

### Post by thenellt on 2010-08-07
Looks to me like you're still using the mesa driver which is not going to work. Have you tried getting drivers from here [[COLOR="Blue"]http://intellinuxgraphics.org/[/COLOR]]("http://intellinuxgraphics.org/") ?

---

### Post by ALF102 on 2010-08-07
ok, I clicked the link an I don't know what to do from there.

---

### Post by thenellt on 2010-08-07
Under the download section they offer the source code for the latest drives but as I do not have this graphics chipset I can't help you with compiling it though I do know the basic commands to compile things from source. There are definitely people in this forum that are more qualified to help you through compiling things especially things as tricky as graphics drives and doing xorg configs.

---

