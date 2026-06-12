---
title: "Wine won't run"
date: 2011-06-19
forum: Wine
---

### Post by JCM_Pico on 2011-06-19
I there,
I recently installed wine, and followed this document [https://help.ubuntu.com/community/CounterStrike](https://help.ubuntu.com/community/CounterStrike) to install steam.

After installing steam I logged into my account and installed Day of Defeat Source from my steam account.

After downloading and installing when I click play I got this error in my command line:  

```

```err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd 0x700a2
fixme:win:EnumDisplayDevicesW ((null),0,0x33dfec,0x00000000), stub!
err:module:import_dll Library binkw32.dll (which is needed by L"C:\\program files\\steam\\steamapps\\jcmteixeira\\day of defeat source\\bin\\video_bink.dll") not found
err:module:import_dll Library binkw32.dll (which is needed by L"C:\\Program Files\\Steam\\steamapps\\jcmteixeira\\day of defeat source\\bin\\video_bink.dll") not found
Using breakpad crash handler
Setting breakpad minidump AppID = 300
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198018732793 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561198018732793
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d:debug_d3dformat Unrecognized 1129272385 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1129272385) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1129272385 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1129272385) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x149cc0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e114)
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
err:ntdll:RtlpWaitForCriticalSection section 0x7d7734 "?" wait timed out in thread 001e, blocked by 001f, retrying (60 sec)

```

```

>Does any one knows how to solve this?

---

### Post by dino99 on 2011-06-19
search info on winehq and search/read steam's forum

[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)

note: you might post on wine subforum, not on the general forum

---

### Post by Elfy on 2011-06-19
Thread moved to Wine.

---

