---
title: "steam games do not launch x86_64"
date: 2011-02-28
forum: Wine
---

### Post by mons00n on 2011-02-28
Hi Everyone,

I'm running Ubuntu 10.04 64bit with the standard nVidia drivers (gtx260) and wine 1.3.14 (from the ppa or compiled by hand).  I'm having quite the time trying to get steam games (TF2 in particular) to start, here's the error it spits out when I hit play:

```

err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd 0x2015e
fixme:win:EnumDisplayDevicesW ((null),0,0x33e1e4,0x00000000), stub!
Using breakpad crash handler
Setting breakpad minidump AppID = 440
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561197963511199 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561197963511199
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d:debug_d3dformat Unrecognized 0x434f5441 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x434f5441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x41415353 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x41415353) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x434f5441 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x434f5441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x41415353 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x41415353) in the format lookup table
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x14c0a8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e114)
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:avifile:AVIFileExit (): stub!
err:ntdll:RtlpWaitForCriticalSection section 0x7d7784 "?" wait timed out in thread 0056, blocked by 0057, retrying (60 sec)

```

I am using '-dxlevel 81 -nointro' for the TF2 launch options as well.  I tried this on a 32bit installation of 10.10 on the same machine last night and got it to work so I believe it has something to do with the architecture.  I haven't found any threads telling me something new to try so I was hoping someone could help out =)

---

