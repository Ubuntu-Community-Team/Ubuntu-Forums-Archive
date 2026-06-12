---
title: "Game crashes: fatal IO error 11 on Xserver"
date: 2010-01-20
forum: Wine
---

### Post by echoforever on 2010-01-20
[SIZE="1"]Hi,

I am trying my first windows game on Ubuntu using Wine. It's a demo version of Superbike 2001 by EA Sports.

If I double click on exe, my session is gone and logon screen appears. 

When I run from command prompt, the following message pops-up:

[IMG]http://i.imgur.com/q0qyS.png[/IMG]

Here are the last few lines of "WINEDEBUG=+reg wine '/home/anil/.wine/dosdevices/c:/Program Files/EA Sports/Superbike 2001 Demo/SBK2001.exe' 2> wintrtrace.txt"

```
trace:reg:NtOpenKey (0x1c,L"Software\\Wine\\AppDefaults",f003f,0x32f044)
trace:reg:NtOpenKey <- (nil)
get fences failed: -1 [22]
param: 6, val: 0
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32efd0,0x00000000), stub!
trace:reg:GetSystemInfo si=0x0x32f0cc
fixme:d3d:IWineD3DDeviceImpl_Release (0x13d158) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x13d7d0 with type 1,WINED3DRTYPE_SURFACE
trace:reg:NtOpenKey (0x44,L"Software\\EA SPORTS\\Superbike 2001 Demo\\Shiba",f003f,0x32f61c)
trace:reg:NtOpenKey <- 0x7c
trace:reg:NtSetValueKey (0x7c,L"LastDxVersion",4,0x32f634,4)
trace:reg:NtOpenKey (0x7c,L"DriverList",f003f,0x32f620)
trace:reg:NtOpenKey <- 0x90
trace:reg:RegQueryValueExA (0x7c,"DriverNumber",(nil),0x32f638,0x32f624,0x32f640=4)
trace:reg:NtQueryValueKey (0x7c,L"DriverNumber",2,0x32f4d8,256)
trace:reg:RegQueryValueExA (0x90,"Driver0",(nil),0x32f648,0x32f75c,0x32f644=64)
trace:reg:NtQueryValueKey (0x90,L"Driver0",2,0x32f4d8,256)
trace:reg:RegQueryValueExA (0x90,"VideoMem0",(nil),0x32f638,0x505ec0,0x32f640=4)
trace:reg:NtQueryValueKey (0x90,L"VideoMem0",2,0x32f4d8,256)
trace:reg:RegQueryValueExA (0x90,"TextMem0",(nil),0x32f638,0x505f20,0x32f640=4)
trace:reg:NtQueryValueKey (0x90,L"TextMem0",2,0x32f4d8,256)
trace:reg:RegQueryValueExA (0x90,"DeviceID0",(nil),0x32f650,0x505f80,0x32f654=16)
trace:reg:NtQueryValueKey (0x90,L"DeviceID0",2,0x32f4d8,256)
trace:reg:NtOpenKey (0x7c,L"DriverList",10000,0x32f4e0)
trace:reg:NtOpenKey <- 0x90
trace:reg:NtDeleteKey (0x90)
trace:reg:RegDeleteKeyA "DriverList" ret=00000000
trace:reg:NtCreateKey (0x7c,L"DriverList",L"DriverList",0,f003f,0x32f620)
trace:reg:NtCreateKey <- 0x90
trace:reg:NtSetValueKey (0x7c,L"DriverNumber",4,0x505e5c,4)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 21 requests (13 known processed) with 0 events remaining.
```

I have tried running wine in windows 98 and XP modes; the result is same. I use winetricks.[/SIZE]

---

### Post by echoforever on 2010-01-21
I have tried the instructions in [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine) ([http://ubuntuforums.org/showthread.php?t=649283](http://ubuntuforums.org/showthread.php?t=649283)), but they did not work.
Any ideas?

---

### Post by echoforever on 2010-09-16
I guess games designed for Windows ought to be played in Windows.

---

