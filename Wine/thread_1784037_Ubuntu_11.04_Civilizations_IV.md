---
title: "Ubuntu 11.04 Civilizations IV"
date: 2011-06-16
forum: Wine
---

### Post by Turtlicious on 2011-06-16
I am trying to play Civilizations IV and I've gotten all the DLL's using wine tricks and I got the msxml3r off the web
[hider= Terminal]
[PHP]justin@Ipod:~$ '/home/justin/Desktop/Link to Firaxis Games/Sid Meier'\''s Civilization 4/Civilization4.exe' -opengl
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:menubuilder:Process_Link unable to load L"Z:\\home\\justin\\Desktop\\Link to Firaxis Games\\Sid Meier's Civilization 4\\Logs.lnk"
err:menubuilder:wWinMain failed to build menu item for L"Z:\\home\\justin\\Desktop\\Link to Firaxis Games\\Sid Meier's Civilization 4\\Logs.lnk"
err:menubuilder:Process_Link unable to load L"Z:\\home\\justin\\Desktop\\Link to Firaxis Games\\Sid Meier's Civilization 4\\Saves.lnk"
err:menubuilder:wWinMain failed to build menu item for L"Z:\\home\\justin\\Desktop\\Link to Firaxis Games\\Sid Meier's Civilization 4\\Saves.lnk"
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x530424 0x00000000
err:menubuilder:Process_Link unable to load L"Z:\\home\\justin\\Desktop\\Link to Firaxis Games\\Sid Meier's Civilization 4\\CivilizationIV.ini.lnk"
err:menubuilder:wWinMain failed to build menu item for L"Z:\\home\\justin\\Desktop\\Link to Firaxis Games\\Sid Meier's Civilization 4\\CivilizationIV.ini.lnk"
'import site' failed; use -v for traceback
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ecb0,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f210,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f1f4,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed3c,0x00000000), stub!
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
wine: Unhandled page fault on read access to 0x00000005 at address 0x4bc310 (thread 0053), starting debugger...
Killed
justin@Ipod:~$ couldn't load main module (2)
Process of pid=0052 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000054    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000016    0
    00000013    0
    00000012    0
0000001b Adobe Flash CS4.exe
    0000003e    0
    0000003d    0
    00000023    0
0000001d explorer.exe
    0000001e    0
00000027 FNPLicensingService.exe
    00000030    0
    0000002f    0
    0000002e    0
    0000002b    0
    00000028    0
00000041 Adobe Flash CS4.exe
    00000015    0
    00000022    0
    0000000b    0
00000056 winedevice.exe
    0000005c    0
    00000045    0
    00000055    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'
[/PHP][/hider]

And the screen looks like this. 

[IMG]http://img715.imageshack.us/img715/2382/screenshotzu.png[/IMG]

Can you make this runnable PLEASE?

I am on an Asus EEE-PC 1001PX

with

1GB Ram
1.9 GHZ Processor

Don't know the rest.

---

### Post by Turtlicious on 2011-06-17
Bump

---

### Post by Turtlicious on 2011-06-17
Sorry one more thing, No-one on WineHQ has my problem, and a 2 hour search of the forum proved useless.

---

### Post by Turtlicious on 2011-06-18
A 24 hour search has proven even worse.

Can someone please help me?

---

### Post by Boris-- on 2011-06-18
try playonlinux

---

### Post by Turtlicious on 2011-06-18
I did still have the same screen

---

### Post by Turtlicious on 2011-06-18
Bumped

---

### Post by jacksaff on 2011-06-23
I very much doubt your eeepc is powerful enough to play civ4. It needs a reasonable video card to run.

---

