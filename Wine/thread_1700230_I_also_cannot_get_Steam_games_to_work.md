---
title: "I also cannot get Steam games to work"
date: 2011-03-04
forum: Wine
---

### Post by Maheriano on 2011-03-04
I haven't played Day Of Defeat in about 2 years, maybe 3 so I figured I'd check it out again. How do I do this? I installed Steam using Wine and it worked fine, then I used that to install Day Of Defeat which worked fine. But when I try and run the game by clicking PLAY in the Steam window, it comes up with a window saying it's preparing the game, the box goes away and nothing happens. It won't run.

I checked the other threads, didn't see anything similar, they all got error messages. Do I need to install DirectX somehow? Am I missing a step? I know my hardware is good, it's a dual core Dell Studio 15 with the upgraded ATI HD3450 video card.

---

### Post by cogadh on 2011-03-04
Run Steam and the game from the terminal and post Wine's error output, it might explain what is happening. By all rights, DoD should work fine in Wine:

Original: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3620](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3620)
Source version: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4571](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4571)

---

### Post by Maheriano on 2011-03-04
Here you go.

> deemar@Clementine:~$ wine 'c:\Program Files\Steam\Steam.exe'
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 2, 0x32d334, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 3, 0x32d338, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1009a, 4, 0x32d33c, 4) stub
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 2, 0x32d804, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 3, 0x32d808, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100a2, 4, 0x32d80c, 4) stub
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer 0x4932670, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x42bbee8)
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 2, 0x32d80c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 3, 0x32d810, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100aa, 4, 0x32d814, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 2, 0x32d2e4, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 3, 0x32d2e8, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100b4, 4, 0x32d2ec, 4) stub
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 2, 0x32d94c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 3, 0x32d950, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x100d0, 4, 0x32d954, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1010c, 2, 0x32da8c, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1010c, 3, 0x32da90, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1010c, 4, 0x32da94, 4) stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ce24,0x00000000), stub!
fixme:dwmapi:DwmSetWindowAttribute (0x200a2, 2, 0x32d564, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x200a2, 3, 0x32d568, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x200a2, 4, 0x32d56c, 4) stub
fixme:advapi:RegisterTraceGuidsW (0x3884fa0, 0x3edb720, {3dada31d-19ef-4dc1-b345-037927193422}, 1, 0x3eb3b24, (null), (null), 0x3edb738,)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd 0x10124
fixme:win:EnumDisplayDevicesW ((null),0,0x33dfec,0x00000000), stub!
Using breakpad crash handler
Setting breakpad minidump AppID = 300
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561197986967065 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561197986967065
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x17ec18, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e114)
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:avifile:AVIFileExit (): stub!
err:ntdll:RtlpWaitForCriticalSection section 0x7d7794 "?" wait timed out in thread 001e, blocked by 001f, retrying (60 sec)
fixme:dwmapi:DwmSetWindowAttribute (0x20156, 2, 0x32d824, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x20156, 3, 0x32d828, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x20156, 4, 0x32d82c, 4) stub
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd 0x20150
^Cfixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported


---

### Post by Maheriano on 2011-03-05
nobody?

---

