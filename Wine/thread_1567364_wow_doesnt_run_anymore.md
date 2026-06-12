---
title: "wow doesnt run anymore"
date: 2010-09-03
forum: Wine
---

### Post by grimd34th on 2010-09-03
it ran fine for about 3 weeks on wine 1.3, then it started crashing so i updated my graphics card drivers and switched to wine 1.2 and now it wont even start up.

wow error log:```
==============================================================================
World of WarCraft (build 12340)

Exe:      C:\users\Public\Games\World of Warcraft\Wow.exe
Time:     Sep  3, 2010  4:28:20.229 PM
User:     d34th
Computer: d34th-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:    C:\users\Public\Games\World of Warcraft\Wow.exe
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0073:72ED56C5

The instruction at "0x72ED56C5" referenced memory at "0xFFFFFFFF".
The memory could not be "read".


WoWBuild: 12340
Settings: 
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
SET locale "enUS"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=FFFFFFFF  EBX=00000000  ECX=7D08F550  EDX=00000001  ESI=7D269898
EDI=00000008  EBP=00000001  ESP=0196ED0C  EIP=72ED56C5  FLG=00210286
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 2/2 threads...

--- Thread ID: 49 ---
7B869911 01A6E9D4 0001:00058911 C:\windows\system32\KERNEL32.dll
7B869955 01A6E9F4 0001:00058955 C:\windows\system32\KERNEL32.dll
00438935 01A6EA14 0001:00037935 C:\users\Public\Games\World of Warcraft\Wow.exe
0044DF1A 01A6EA28 0001:0004CF1A C:\users\Public\Games\World of Warcraft\Wow.exe
0088C5DF 01A6EA60 0001:0048B5DF C:\users\Public\Games\World of Warcraft\Wow.exe
0088C684 01A6EA78 0001:0048B684 C:\users\Public\Games\World of Warcraft\Wow.exe
7BC70030 01A6EB48 0001:0005F030 C:\windows\system32\ntdll.dll
7BC78625 01A6F398 0001:00067625 C:\windows\system32\ntdll.dll
6802296E 01A6F498 0000:00000000 <unknown>

--- Thread ID: 12 [Current Thread] ---
72ED56C5 00000001 0000:00000000 <unknown>

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 2/2 threads...

--- Thread ID: 49 ---
7B869911 KERNEL32.dll SleepEx+65 (0x00000000,0x000000B0,0x000000B0,0xFFF0BDC0) (sync.c,111)
7B869911 KERNEL32.dll SleepEx+65 (0x00000000,0x00000000,0x00000000,0x00000000) (sync.c,111)
7B869955 KERNEL32.dll Sleep+37 (0x00000000,0x00000000,0x00000000,0x00000000) (sync.c,98)
00438935 Wow.exe      <unknown symbol>+0 (0x010A3B90,0x0088C605,0x7BC9BFF4,0x01A6EA34)
0088C5DF Wow.exe      <unknown symbol>+0 (0x7FFD4F10,0x010A3BF8,0x01A6EB48,0x0088C605)
0088C684 Wow.exe      <unknown symbol>+0 (0x0088C605,0x7BC9BFF4,0xFFFFFFFF,0x7B837140)
7BC70030 ntdll.dll    call_thread_entry_point+112 (0x0088C605,0x7BC9BFF4,0xFFFFFFFF,0x7B837140) (signal_i386.c,2477)
7BC70030 ntdll.dll    call_thread_entry_point+112 (0x00000000,0x00000000,0x00000000,0x00000000) (signal_i386.c,2477)
7BC78625 ntdll.dll    start_thread+245 (0x00000000,0x00000000,0x00000000,0x00000000) (thread.c,399)

--- Thread ID: 12 [Current Thread] ---



----------------------------------------
    Loaded Modules
----------------------------------------

DBG-MODULE<00400000 009FD000 "Wow.exe" "Wow.pdb" 0 {8805d059-f6a3-4565-a646aa69736d4efe} 1 1277448958>
DBG-MODULE<10000000 00069000 "DivxDecoder.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 1076466304>
DBG-MODULE<3D090000 0002F000 "d3d9.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<63000000 00070000 "WININET.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 924132383>
DBG-MODULE<681F0000 0008D000 "opengl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68400000 00117000 "user32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68520000 00082000 "gdi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<685B0000 0004D000 "advapi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68600000 00016000 "version.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68620000 0000A000 "lz32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68640000 0004C000 "shlwapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68690000 00029000 "ws2_32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<686C0000 00014000 "dinput8.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<686F0000 000E4000 "ole32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<687E0000 00069000 "rpcrt4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68860000 001C1000 "shell32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68A30000 000DC000 "comctl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68B10000 00022000 "msacm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68B40000 00050000 "setupapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68BA0000 00028000 "winspool.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68BD0000 0000D000 "hid.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68CD0000 00092000 "winex11.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<68D90000 0002E000 "uxtheme.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<6EC50000 0001F000 "imm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<71F20000 00133000 "wined3d.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<72490000 00030000 "dinput.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<76A90000 00006000 "psapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<795E0000 00048000 "dbghelp.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7AF00000 00085000 "winmm.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7B810000 00162000 "KERNEL32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7BC10000 000A8000 "ntdll.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>

----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 72ED56C5)

72ED56C5: FF D0 8B 54  24 1C 8D 46  10 89 44 24  04 8B 42 04  ...T$..F..D$..B.


Stack: 1024 bytes starting at (ESP = 0196ED0C)

* = addr                                         **                       *   
0196ED00: 08 00 00 00  01 00 00 00  AC 56 ED 72  00 00 00 00  .........V.r....
0196ED10: 50 F5 08 7D  98 98 26 7D  01 00 00 00  C0 D3 18 68  P..}..&}.......h
0196ED20: F4 BF 18 68  C0 D3 18 68  50 F5 08 7D  00 00 00 00  ...h...hP..}....
0196ED30: 01 00 00 00  01 00 00 00  00 00 00 00  98 98 26 7D  ..............&}
0196ED40: 5B 00 00 00  1C AC 10 7D  B6 5B ED 72  00 00 00 00  [......}.[.r....
0196ED50: 50 F5 08 7D  98 98 26 7D  01 00 00 00  18 89 01 00  P..}..&}........
0196ED60: 01 00 00 00  01 00 00 00  00 00 00 00  C0 05 27 7D  ..............'}
0196ED70: 01 00 00 00  01 00 00 00  00 00 00 00  48 14 05 7D  ............H..}
0196ED80: 1C 01 20 04  00 00 00 00  0D C8 27 79  00 00 00 00  .. .......'y....
0196ED90: 50 F5 08 7D  00 00 00 00  01 00 00 00  18 89 07 7D  P..}...........}
0196EDA0: 1C 01 20 04  80 00 00 00  D2 0B 28 79  1C 01 20 04  .. .......(y.. .
0196EDB0: 1C 01 20 04  80 00 00 00  F8 9B 25 79  10 F3 1B 7D  .. .......%y...}
0196EDC0: 1C 01 20 04  00 00 00 00  00 00 00 00  00 00 00 00  .. .............
0196EDD0: 58 64 0E 7D  00 10 96 7E  B7 AB 25 79  18 89 07 7D  Xd.}...~..%y...}
0196EDE0: 1C 01 20 04  00 00 00 00  E4 17 B8 72  68 74 26 7D  .. ........rht&}
0196EDF0: 00 00 00 00  00 00 00 00  01 00 00 00  68 46 26 7D  ............hF&}
0196EE00: 00 00 00 00  00 00 00 00  CC 35 BB 72  00 10 96 7E  .........5.r...~
0196EE10: 58 64 0E 7D  08 00 00 00  00 10 96 01  00 00 00 00  Xd.}............
0196EE20: 01 00 00 00  01 00 00 00  01 00 00 00  00 00 00 00  ................
0196EE30: 00 00 00 00  00 10 96 01  01 00 00 00  00 10 96 7E  ...............~
0196EE40: 00 00 00 00  08 EF 96 01  DA 1D B8 72  00 10 96 7E  ...........r...~
0196EE50: 30 A3 26 7D  01 00 00 00  01 00 00 00  00 00 00 00  0.&}............
0196EE60: 04 EF 96 01  01 00 00 00  98 B6 97 7E  8C B6 97 7E  ...........~...~
0196EE70: 80 74 16 01  01 00 00 00  20 AF D2 68  20 CA D5 68  .t...... ..h ..h
0196EE80: 00 00 00 00  00 00 00 01  F4 0F 05 72  DC 1C 13 00  ...........r....
0196EE90: 80 74 16 00  24 EF 96 01  5F 3E 01 72  01 00 00 00  .t..$..._>.r....
0196EEA0: 08 EF 96 01  E1 0D 00 00  01 00 00 00  00 00 00 00  ................
0196EEB0: 00 00 00 00  F4 86 00 00  02 14 00 00  00 00 00 00  ................
0196EEC0: 74 8B 26 7D  80 6C 14 7D  40 00 00 00  C0 D3 18 68  t.&}.l.}@......h
0196EED0: F4 BF 18 68  C0 D3 18 68  08 54 04 72  04 EF 96 01  ...h...h.T.r....
0196EEE0: CD 5E 0A 68  3E DE C7 7B  D6 8C 00 00  25 21 04 72  .^.h>..{....%!.r
0196EEF0: F0 6B 04 72  A4 21 05 72  D8 1C 00 00  0C F3 96 01  .k.r.!.r........
0196EF00: 01 00 00 00  01 00 00 00  01 00 00 00  20 CA D5 68  ............ ..h
0196EF10: CD 5E 0A 68  1B 31 01 72  F4 0F 05 72  30 01 00 00  .^.h.1.r...r0...
0196EF20: 00 00 07 00  C4 F5 96 01  03 5C F8 71  DC 1C 13 00  .........\.q....
0196EF30: DE 10 00 00  E1 80 00 00  67 83 00 00  0C F3 96 01  ........g.......
0196EF40: 04 00 00 00  E1 80 00 00  67 83 00 00  00 00 00 00  ........g.......
0196EF50: 00 00 00 00  00 00 00 00  00 00 00 00  A4 EF 96 01  ................
0196EF60: 64 9F 02 68  40 00 00 00  B0 F2 C6 7B  A8 F4 96 01  d..h@......{....
0196EF70: 4F F3 02 72  0C B0 02 72  88 F4 96 01  0F FD 02 72  O..r...r.......r
0196EF80: E0 1F 05 72  CD FD 02 72  9C F4 96 01  94 F4 96 01  ...r...r........
0196EF90: 90 F4 96 01  4C F4 96 01  C0 9B 62 73  00 00 07 00  ....L.....bs....
0196EFA0: DE 10 00 00  D0 1F 05 72  02 04 00 00  DC 1C 13 00  .......r........
0196EFB0: CC 1C 13 00  0C F3 96 01  B8 1C 13 00  00 00 00 00  ................
0196EFC0: 00 00 00 00  00 8C FD 7F  32 00 00 00  00 00 CD 68  ........2......h
0196EFD0: 01 00 00 00  74 F0 96 01  4A 58 FB 7F  BE 6E 73 DB  ....t...JX...ns.
0196EFE0: 34 00 00 C0  F8 49 27 7D  0E 01 00 00  F8 8B FD 01  4....I'}........
0196EFF0: C4 F0 96 01  24 F0 96 01  28 F0 96 01  CC 20 00 00  ....$...(.... ..
0196F000: 00 00 00 00  10 F0 96 01  01 ED C5 7B  3C F0 96 01  ...........{<...
0196F010: 00 00 00 00  00 00 00 00  12 00 13 00  C7 82 04 72  ...............r
0196F020: 00 00 00 00  3C 81 04 72  F4 BF C9 7B  32 00 00 00  ....<..r...{2...
0196F030: A4 F1 96 01  3C F0 96 01  32 00 00 00  34 00 00 C0  ....<...2...4...
0196F040: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0196F050: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0196F060: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0196F070: 00 00 00 00  1B F3 C6 7B  F4 BF C9 7B  FF FF FF FF  .......{...{....
0196F080: DC F0 96 01  24 F1 96 01  4A 5D C5 7B  9C F0 96 01  ....$...J].{....
0196F090: F4 BF C9 7B  F4 F0 96 01  A3 7B C4 7B  00 00 00 00  ...{.....{.{....
0196F0A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0196F0B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0196F0C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0196F0D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0196F0E0: 18 00 00 00  F8 8B FD 7F  00 00 00 00  00 00 00 00  ................
0196F0F0: 00 00 00 00  19 00 1A 00  50 E8 C3 7B  00 00 11 00  ........P..{....
0196F100: 00 00 00 00  7B 1C 5D 68  F4 6F 5F 68  01 00 00 80  ....{.]h.o_h....


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x3
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3853
Os Version:             6.0
Os Service Pack:        2.0

Percent memory used:    26
Total physical memory:  2109968384
Free Memory:            1550929920
Page file:              2735960064
Total virtual memory:   2147352575
```Terminal Log: ```
d34th@d34th-laptop:~/.wine/drive_c/users/Public/Games/World of Warcraft$ wine Wow.exe -opengl
err:menubuilder:write_freedesktop_mime_type_entry error writing file /home/d34th/.local/share/mime/packages/x-wine-extension-/bzw.xml
err:menubuilder:write_freedesktop_association_entry error writing association file "/home/d34th/.local/share/applications/wine-extension-/bzw.desktop"
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x1261f0, filter=0x73e9d4,flags=0x00000001) returns a fake device notification handle!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:service:EnumServicesStatusW 0x1266e8 type=30 state=3 (nil) 0 0x78e7e8 0x78e7f4 0x78e7f0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x78e5f8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x126030,(nil)): stub
fixme:netapi32:NetGetJoinInformation Stub (null) 0x78e688 0x78e690
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\enUS\patch-enUS-3.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\patch-3.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x195ee20,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195eaec,0x00000000), stub!
d34th@d34th-laptop:~/.wine/drive_c/users/Public/Games/World of Warcraft$ 

```

if anyone knows anything can you please help

---

