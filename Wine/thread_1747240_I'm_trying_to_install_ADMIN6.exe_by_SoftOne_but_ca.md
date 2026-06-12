---
title: "I'm trying to install ADMIN6.exe by SoftOne but can't launch it (missing dll's)"
date: 2011-05-02
forum: Wine
---

### Post by gunnarflax on 2011-05-02
I'm trying to install SoftOne's accounting program on ubuntu 11.04, wine 1.2.2, but when I try to launch I get a missing dll error. This is the output from the terminal:

```

niklas@ubuntu:~$ wine 'C:\Program Files\SoftOne\ADMIN6.exe'
fixme:font:WineEngCreateFontInstance Untranslated charset 255
wine: Call from 0x7bc4a440 to unimplemented function iertutil.dll.653, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
wine: Call from 0x7bc4a440 to unimplemented function iertutil.dll.653, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100

```

I found the required dll on dll-files.com but I don't know how to get it into the wine installation so that it works as it should... Any help?

---

### Post by cogadh on 2011-05-02
That DLL is part of Internet Explorer. Just adding it to Wine may not be enough and IE doesn't really work in Wine. You can try using [winetricks]("http://wiki.winehq.org/winetricks") to install IE, but there are no guarantees that it will work.

---

### Post by gunnarflax on 2011-05-02
I've been doing the best I can with winetricks to get the program to work but I still get these error dialogues when trying to launch the application:

```
Can't create object: ADOCommand

An exception occured

Failed to create object.
OLE returned error: H"80004005".
Reason: ...

Exception 24 not trapped;
the class nilobject (object reference: 00000003)
Does not understand: getdataset

Exception 24 not trapped;
the class nilobject (object reference: 00000003)
Does not understand: getx

Exception 24 not trapped;
the class nilobject (object reference: 00000003)
Does not understand: getm

Exception 24 not trapped;
the class nilobject (object reference: 00000003)
Does not understand: getoptions

Exception 24 not trapped;
the class nilobject (object reference: 00000003)
Does not understand: getcolumns

Exception 24 not trapped;
the class nilobject (object reference: 00000003)
Does not understand: getfont

Execution error : file 'sgmen01qcx'
error code: 240, pc=0, call=1, seg=0
240 Object reference not valid

```

Do they have anything to do with any dll or are they components missing from the program itself?

---

### Post by cogadh on 2011-05-03
I've never seen error codes like that with winetricks, but I can say for certain they have nothing to do with your missing DLL. Winetricks is simply a tool for configuring and adding additional functionality to Wine, but it does not run in Wine itself. How are you running winetricks, as in, specifically what commands are you running?

---

### Post by gunnarflax on 2011-05-03
No the error's aren't with winetricks, they are with the application. I've just been using winetricks to install dll's. Maybe I was a bit unclear with that :/

---

### Post by cogadh on 2011-05-03
Ah, yes, I misunderstood. Did you use winetricks to install IE or have you just added DLLs (and which DLLs did you add)? As I said before, it is likely that your application is looking for the full IE, not just a DLL. Also, those appear to be error messages from the application, not Wine. Error messages from the application are mostly meaningless when trying to troubleshoot Wine. We need the error output from Wine itself, like you had in your initial post.

---

### Post by gunnarflax on 2011-05-03
I installed IE from winetricks and I don't know if I still have those iertutil.dll related errors, I will check first thing tomorrow!

---

### Post by gunnarflax on 2011-05-04
This is the output I'm getting now when I try to launch the application:
```

niklas@ubuntu:~$ env WINEPREFIX=~/.PlayOnLinux/wineprefix/admin6 wine 'C:\Program Files\SoftOne\ADMIN6.exe'
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\mscoree.dll" (error=80)
err:setupapi:create_dest_file failed to create L"C:\\windows\\system32\\shlwapi.dll" (error=80)
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
err:shell:ReadCabinetState Initializing shell cabinet settings
err:rebar:REBAR_WindowProc unknown msg 200b wp=00000000 lp=711888bc
fixme:toolbar:TOOLBAR_CheckStyle [0x100de] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x100de] TBSTYLE_REGISTERDROP not implemented
fixme:shell:NTSHChangeNotifyRegister (0x100de,0x00008003,0x00008000,0x0000c068,0x00000001,0x33dcf0):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x100de, wParam=0x00000000, size.cx=1857, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x100de] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_Unkwn464 hwnd=0x400e4 wParam 00000001 lParam 00000000
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x400fe, wParam=0x00000000, size.cx=1857, size.cy=1076 stub!
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {5836fb00-8187-11cf-a12b-00aa004ae837} (unknown)
fixme:shell:NTSHChangeNotifyRegister (0x400fe,0x00008003,0x0c02b7ff,0x0000c068,0x00000001,0x33dd30):semi stub.
fixme:wininet:GetUrlCacheEntryInfoExA Undocumented flag(s): 200
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
err:ole:apartment_getclassobject DllGetClassObject returned error 0x8007000e
err:ole:create_server class {9ba05972-f6a8-11cf-a442-00a0c90a8f39} not registered
err:ole:CoGetClassObject no class object {9ba05972-f6a8-11cf-a442-00a0c90a8f39} could be created for context 0x5
fixme:shell:NTSHChangeNotifyRegister (0x10080,0x00008003,0x0003f5f4,0x00000410,0x00000001,0x33e9d8):semi stub.
fixme:shell:SignalFileOpen (0x00000000):stub.
fixme:shell:DllGetClassObject failed for CLSID={871c5380-42a0-1069-a2ea-08002b30309d} (unknown)
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=0.0.0.0 length=7
fixme:msimtf:DllGetClassObject ({50d5107a-d278-4871-8989-f4ceaaf59cfc} {00000001-0000-0000-c000-000000000046} 0x33bb0c)
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {50d5107a-d278-4871-8989-f4ceaaf59cfc} could be created for context 0x401
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:shell:DllGetClassObject failed for CLSID={871c5380-42a0-1069-a2ea-08002b30309d} (unknown)
fixme:win:GetProcessDefaultLayout ( 0x33d054 ): No BiDi
fixme:win:GetProcessDefaultLayout ( 0x33d054 ): No BiDi
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {062e1261-a60e-11d0-82c2-00c04fd5ae38} (unknown)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
err:ole:ITypeInfo_fnInvoke did not find member id -525, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -525, flags 0x2!
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {5836fb00-8187-11cf-a12b-00aa004ae837} (unknown)
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {5836fb00-8187-11cf-a12b-00aa004ae837} (unknown)
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {5836fb00-8187-11cf-a12b-00aa004ae837} (unknown)
fixme:win:GetProcessDefaultLayout ( 0x33e9ec ): No BiDi
fixme:win:GetProcessDefaultLayout ( 0x33e9ec ): No BiDi
fixme:shell:SHFlushClipboard stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_END_BROWSER_SESSION: STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
fixme:wininet:InternetSetOptionW Option 76 STUB
err:ole:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
wine: configuration in '/home/niklas/.PlayOnLinux/wineprefix/admin6' has been updated.
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:storage:create_storagefile Storage share mode not implemented.

```

---

### Post by cogadh on 2011-05-04
Looks like your application requires some .NET functionality (the mscoree.dll error). You should find out which version of .NET the app requires then use winetricks to install that version (NOTE: both .NET 3.5 and 4.0 do not work in Wine at all and .NET 3.0 has problems. The .NET 1.0 through 2.0 packages should work fine). 

The shlwapi.dll error is troubling. That DLL is already part of Wine, so the application should not need or even try to create it. You didn't happen to manually delete or replace any DLLs in Wine's system32 directory, did you?

---

### Post by gunnarflax on 2011-05-04
> **cogadh said:**
> 
The shlwapi.dll error is troubling. That DLL is already part of Wine, so the application should not need or even try to create it. You didn't happen to manually delete or replace any DLLs in Wine's system32 directory, did you?
Not that I know off, I will look and see if it's missing as soon as I get the time. I will also try installing .NET 3.0. If the installation should fail, would it be possible to download the real 3.0 installer and put in winetricks cache and maybe work around it that way?

---

### Post by cogadh on 2011-05-04
Not sure, but letting winetricks do its thing is really the only way I know to get it installed correctly.

---

### Post by gunnarflax on 2011-05-04
I managed to install .NET 3.0 and now when I launch it I get up the  program's boot splash but it freezes shortly afterwards. Now this is the  only output I get:

```
niklas@ubuntu:~$ env WINEPREFIX=~/.PlayOnLinux/wineprefix/admin6 wine 'C:\Program Files\SoftOne\ADMIN6.exe'
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:storage:create_storagefile Storage share mode not implemented.
```

---

### Post by cogadh on 2011-05-04
The "fixme" errors are simply developer notes about unimplemented functions in Wine, there's really nothing you can do to fix them except wait for Wine to be further developed. I'm thinking that second fixme is the one that is causing the issue.

---

