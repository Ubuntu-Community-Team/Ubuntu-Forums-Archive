---
title: "tf2 issue"
date: 2009-06-14
forum: Wine
---

### Post by ForMar on 2009-06-14
Hello,

I am attempting to run tf2 (Steam app) but im getting a lot of errors. The game starts loading but just hangs there. Steam does work for me. Also I am very "noobish" when it comes to wine so please instruct accordingly . I also apologies in advance if I do not give enough information.


    **Wine version** 1.1.23
    **Terminal output** - 
```
formar@toaster:~/Desktop$ padsp env WINEPREFIX="/home/formar/.wine" wine "C:\\Program Files\\Steam\\steam.exe" -applaunch 440
CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
CellID: CSDS returned 173 servers.
CellID: Connecting to 202.80.110.130:27031. . .
CellID: Connect to 202.80.110.130:27031 took 179 MS
CellID: Nothing beat our old best time of 23 MS
err:ntdll:RtlpWaitForCriticalSection section 0xbd72cc "?" wait timed out in thread 001d, blocked by 001e, retrying (60 sec)
fixme:shdocvw:ViewObject_SetAdvise (0x1874a8)->(1 00000002 0x15dcb88)
fixme:shdocvw:PersistStreamInit_InitNew (0x1874a8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1874a8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1874a8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x187e08)->(1 00000002 0x15dcc28)
fixme:shdocvw:PersistStreamInit_InitNew (0x187e08)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x187e08)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x187e08)->(ffffffff)
fixme:win:RegisterDeviceNotificationA (hwnd=0x10092, filter=0x32de60,flags=0x00000004),
	returns a fake device notification handle!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x32c1ac,0x00000000), stub!
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x1a3048)->(1 00000002 0x15df918)
fixme:shdocvw:PersistStreamInit_InitNew (0x1a3048)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1a3048)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1a3048)->(ffffffff)
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1a3048)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1a3048)
fixme:shdocvw:OleObject_Close (0x1a3048)->(1)
fixme:win:EnumDisplayDevicesW ((null),0,0x33e1d4,0x00000000), stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d:debug_d3dformat Unrecognized 1129272385 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1129272385) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table

```
    there is actually more but its just different variations of   the last few

    **Wine configuration** -
          * OS version: Ubuntu 9.04
          * Library overrides: winetricks but I must admit I cant  remember which :/
          * Sound settings: launch with padsp
          * Graphics settings, using emulated desktop
      
   4. Hardware specs/drivers - 
8800 GTS
Intel Core 2 Duo E8400 Wolfdale 3.0GHz LGA 775 65W Dual-Core 
 Patriot Viper 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 
usb headest
   5. Other Wine applications - 
winetricks 
I had playonlinux but I "sudo apt-get remove" ed it.

Ive checked the hq but I have no idea what the problem is so I dont know where to start


Thanks for your help and time

Anthony

---

### Post by romyboat on 2009-06-14
I have the exact same problem but this problem has been very recent. I was able to get tf2 running for a while but my terminal spits these few lines of code before crashing:

```
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ntdll:RtlpWaitForCriticalSection section 0xbe72d4 "?" wait timed out in thread 001d, blocked by 001e, retrying (60 sec)

```Sometimes the terminal tells me to do a coredump by typing the code 'ulimit -c unlimited'...
Hope someone knows a fix. And yes I have removed pulseaudio and my wine version is uptodate.

---

### Post by 8Kuula on 2009-06-15
Wineserver crash?
[http://bugs.winehq.org/show_bug.cgi?id=18900](http://bugs.winehq.org/show_bug.cgi?id=18900)

---

### Post by ForMar on 2009-06-15
> **8Kuula said:**
> Wineserver crash?
[http://bugs.winehq.org/show_bug.cgi?id=18900](http://bugs.winehq.org/show_bug.cgi?id=18900)

No :/

---

### Post by Jcink on 2009-06-16
Same problem.

```
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
```

I don't think it's the wineserver crash bug because that's the first thing I looked over. Seems totally new with absolutely no solution yet.

---

