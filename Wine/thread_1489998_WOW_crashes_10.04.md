---
title: "WOW crashes 10.04"
date: 2010-05-21
forum: Wine
---

### Post by jhnlambert on 2010-05-21
I have installed wine wow and patched it. I open wow up and the 10 years movie plays and the movie with the map and then an error message saying
```
==============================================================================
World of WarCraft (build 11723)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     May 21, 2010  4:58:33.430 PM
User:     john
Computer: john-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00644A87

The instruction at "0x00644A87" referenced memory at "0xFFD22284".
The memory could not be "written".


WoWBuild: 11723
Settings: 
SET locale "enUS"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET hwDetect "0"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "3"
SET movie "0"
SET Gamma "1.000000"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "550.000000"
SET specular "1"
SET particleDensity "0.4"
SET groundEffectDensity "24"

----------------------------------------
               GxInfo
----------------------------------------
GxApi: D3D9
Adapter Count: 1

Adapter 0 (primary):
  Driver: nv4_disp.dll
  Version: 4.15.0011.7516
  Description: NVIDIA GeForce FX 5600
  DeviceName: \\.\DISPLAY1

------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00BB89E0  EBX=08ACB330  ECX=3F7FFFFF  EDX=01D1FA18  ESI=08ACB330
EDI=80000000  EBP=003AF858  ESP=003AF84C  EIP=00644A87  FLG=00210286
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 20/20 threads...

--- Thread ID: 52 ---
7BC76263 096BE5E8 0001:00065263 C:\windows\system32\ntdll.dll
7BC76553 096BE628 0001:00065553 C:\windows\system32\ntdll.dll
7B869E56 096BE778 0001:00058E56 C:\windows\system32\KERNEL32.dll
68D1179C 096BE7B8 0001:0003079C C:\windows\system32\winex11.drv
683A95F8 096BE7F8 0001:000985F8 C:\windows\system32\user32.dll
6836FD9A 096BE9B8 0001:0005ED9A C:\windows\system32\user32.dll
6836FDEF 096BE9E8 0001:0005EDEF C:\windows\system32\user32.dll
0044C3E6 096BEA14 0001:0004B3E6 C:\Program Files\World of Warcraft\Wow.exe
0044D35A 096BEA28 0001:0004C35A C:\Program Files\World of Warcraft\Wow.exe
0093236F 096BEA60 0001:0053136F C:\Program Files\World of Warcraft\Wow.exe
00932414 096BEA78 0001:00531414 C:\Program Files\World of Warcraft\Wow.exe
7BC6F750 096BEB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 096BF398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 096BF498 0000:00000000 <unknown>

--- Thread ID: 51 ---
7BC76263 0925E868 0001:00065263 C:\windows\system32\ntdll.dll
7BC76553 0925E8A8 0001:00065553 C:\windows\system32\ntdll.dll
7B869E56 0925E9F8 0001:00058E56 C:\windows\system32\KERNEL32.dll
7B869F6C 0925EA28 0001:00058F6C C:\windows\system32\KERNEL32.dll
008EE4B5 0925EA44 0001:004ED4B5 C:\Program Files\World of Warcraft\Wow.exe
008AD949 0925EA54 0001:004AC949 C:\Program Files\World of Warcraft\Wow.exe
008ADF90 0925EA68 0001:004ACF90 C:\Program Files\World of Warcraft\Wow.exe
7BC6F584 0925EA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 0925EB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 0925F398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 0925F498 0000:00000000 <unknown>

--- Thread ID: 50 ---
7BC76263 090EE5E8 0001:00065263 C:\windows\system32\ntdll.dll
7BC76553 090EE628 0001:00065553 C:\windows\system32\ntdll.dll
7B869E56 090EE778 0001:00058E56 C:\windows\system32\KERNEL32.dll
68D1179C 090EE7B8 0001:0003079C C:\windows\system32\winex11.drv
683A95F8 090EE7F8 0001:000985F8 C:\windows\system32\user32.dll
6836FD9A 090EE9B8 0001:0005ED9A C:\windows\system32\user32.dll
6836FDEF 090EE9E8 0001:0005EDEF C:\windows\system32\user32.dll
0044C3E6 090EEA14 0001:0004B3E6 C:\Program Files\World of Warcraft\Wow.exe
0044D35A 090EEA28 0001:0004C35A C:\Program Files\World of Warcraft\Wow.exe
0093236F 090EEA60 0001:0053136F C:\Program Files\World of Warcraft\Wow.exe
00932414 090EEA78 0001:00531414 C:\Program Files\World of Warcraft\Wow.exe
7BC6F750 090EEB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 090EF398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 090EF498 0000:00000000 <unknown>

--- Thread ID: 49 ---
7BC76263 08F7E868 0001:00065263 C:\windows\system32\ntdll.dll
7BC76553 08F7E8A8 0001:00065553 C:\windows\system32\ntdll.dll
7B869E56 08F7E9F8 0001:00058E56 C:\windows\system32\KERNEL32.dll
7B869F6C 08F7EA28 0001:00058F6C C:\windows\system32\KERNEL32.dll
008EE4B5 08F7EA44 0001:004ED4B5 C:\Program Files\World of Warcraft\Wow.exe
008AD949 08F7EA54 0001:004AC949 C:\Program Files\World of Warcraft\Wow.exe
008ADF90 08F7EA68 0001:004ACF90 C:\Program Files\World of Warcraft\Wow.exe
7BC6F584 08F7EA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 08F7EB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 08F7F398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 08F7F498 0000:00000000 <unknown>

--- Thread ID: 46 ---
7BC76263 08E0E988 0001:00065263 C:\windows\system32\ntdll.dll
7BC76553 08E0E9C8 0001:00065553 C:\windows\system32\ntdll.dll
7BC765AC 08E0E9F8 0001:000655AC C:\windows\system32\ntdll.dll
7BC7B67F 08E0EA68 0001:0006A67F C:\windows\system32\ntdll.dll
7BC6F584 08E0EA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 08E0EB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 08E0F398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 08E0F498 0000:00000000 <unknown>

--- Thread ID: 45 ---
7BC76263 08C9E988 0001:00065263 C:\windows\system32\ntdll.dll
7BC76553 08C9E9C8 0001:00065553 C:\windows\system32\ntdll.dll
7BC765AC 08C9E9F8 0001:000655AC C:\windows\system32\ntdll.dll
7BC7B67F 08C9EA68 0001:0006A67F C:\windows\system32\ntdll.dll
7BC6F584 08C9EA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 08C9EB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 08C9F398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 08C9F498 0000:00000000 <unknown>

--- Thread ID: 44 ---
7BC76263 0875E5E8 0001:00065263 C:\windows\system32\ntdll.dll
7BC76553 0875E628 0001:00065553 C:\windows\system32\ntdll.dll
7B869E56 0875E778 0001:00058E56 C:\windows\system32\KERNEL32.dll
68D1179C 0875E7B8 0001:0003079C C:\windows\system32\winex11.drv
683A95F8 0875E7F8 0001:000985F8 C:\windows\system32\user32.dll
6836FD9A 0875E9B8 0001:0005ED9A C:\windows\system32\user32.dll
6836FDEF 0875E9E8 0001:0005EDEF C:\windows\system32\user32.dll
0044C3E6 0875EA14 0001:0004B3E6 C:\Program Files\World of Warcraft\Wow.exe
0044D35A 0875EA28 0001:0004C35A C:\Program Files\World of Warcraft\Wow.exe
0093236F 0875EA60 0001:0053136F C:\Program Files\World of Warcraft\Wow.exe
00932414 0875EA78 0001:00531414 C:\Program Files\World of Warcraft\Wow.exe
7BC6F750 0875EB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 0875F398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 0875F498 0000:00000000 <unknown>

--- Thread ID: 43 ---
7BC76263 0757E61C 0001:00065263 C:\windows\system32\ntdll.dll
7BC76553 0757E65C 0001:00065553 C:\windows\system32\ntdll.dll
7B869E56 0757E7AC 0001:00058E56 C:\windows\system32\KERNEL32.dll
7B869ECA 0757E7DC 0001:00058ECA C:\windows\system32\KERNEL32.dll
00468D1B 0757EA34 0001:00067D1B C:\Program Files\World of Warcraft\Wow.exe
004683CE 0757EA40 0001:000673CE C:\Program Files\World of Warcraft\Wow.exe
0055AD7B 0757EA68 0001:00159D7B C:\Program Files\World of Warcraft\Wow.exe
7BC6F584 0757EA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 0757EB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 0757F398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 0757F498 0000:00000000 <unknown>

--- Thread ID: 42 ---
7BC76263 0740E84C 0001:00065263 C:\windows\system32\ntdll.dll
7BC76553 0740E88C 0001:00065553 C:\windows\system32\ntdll.dll
7B869E56 0740E9DC 0001:00058E56 C:\windows\system32\KERNEL32.dll
7B869F6C 0740EA0C 0001:00058F6C C:\windows\system32\KERNEL32.dll
0055F4D0 0740EA1C 0001:0015E4D0 C:\Program Files\World of Warcraft\Wow.exe
00468505 0740EA34 0001:00067505 C:\Program Files\World of Warcraft\Wow.exe
00468671 0740EA40 0001:00067671 C:\Program Files\World of Warcraft\Wow.exe
0055AD7B 0740EA68 0001:00159D7B C:\Program Files\World of Warcraft\Wow.exe
7BC6F584 0740EA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 0740EB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 0740F398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 0740F498 0000:00000000 <unknown>

--- Thread ID: 41 ---
7BC76263 0729E864 0001:00065263 C:\windows\system32\ntdll.dll
7BC76553 0729E8A4 0001:00065553 C:\windows\system32\ntdll.dll
7B869E56 0729E9F4 0001:00058E56 C:\windows\system32\KERNEL32.dll
7B869F6C 0729EA24 0001:00058F6C C:\windows\system32\KERNEL32.dll
0055F4D0 0729EA34 0001:0015E4D0 C:\Program Files\World of Warcraft\Wow.exe
007FAF3B 0729EA68 0001:003F9F3B C:\Program Files\World of Warcraft\Wow.exe
7BC6F584 0729EA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 0729EB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 0729F398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 0729F498 0000:00000000 <unknown>

--- Thread ID: 40 ---
7B869FE1 0682EA28 0001:00058FE1 C:\windows\system32\KERNEL32.dll
7B86A025 0682EA48 0001:00059025 C:\windows\system32\KERNEL32.dll
008AD7AD 0682EA54 0001:004AC7AD C:\Program Files\World of Warcraft\Wow.exe
008ADFCC 0682EA68 0001:004ACFCC C:\Program Files\World of Warcraft\Wow.exe
7BC6F584 0682EA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 0682EB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 0682F398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 0682F498 0000:00000000 <unknown>

--- Thread ID: 39 ---
7B869FE1 065AEA28 0001:00058FE1 C:\windows\system32\KERNEL32.dll
7B86A025 065AEA48 0001:00059025 C:\windows\system32\KERNEL32.dll
008AD7AD 065AEA54 0001:004AC7AD C:\Program Files\World of Warcraft\Wow.exe
008ADFCC 065AEA68 0001:004ACFCC C:\Program Files\World of Warcraft\Wow.exe
7BC6F584 065AEA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 065AEB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 065AF398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 065AF498 0000:00000000 <unknown>

--- Thread ID: 38 ---
2014EF5B 05E7E9C8 0001:0000DF5B C:\windows\system32\winepulse.drv
2014A148 05E7EA68 0001:00009148 C:\windows\system32\winepulse.drv
7BC6F584 05E7EA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 05E7EB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 05E7F398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 05E7F498 0000:00000000 <unknown>

--- Thread ID: 37 ---
7B869FE1 0643EA28 0001:00058FE1 C:\windows\system32\KERNEL32.dll
7B86A025 0643EA48 0001:00059025 C:\windows\system32\KERNEL32.dll
008AD7AD 0643EA54 0001:004AC7AD C:\Program Files\World of Warcraft\Wow.exe
008ADFCC 0643EA68 0001:004ACFCC C:\Program Files\World of Warcraft\Wow.exe
7BC6F584 0643EA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 0643EB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 0643F398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 0643F498 0000:00000000 <unknown>

--- Thread ID: 36 ---
7B869FE1 062CEA28 0001:00058FE1 C:\windows\system32\KERNEL32.dll
7B86A025 062CEA48 0001:00059025 C:\windows\system32\KERNEL32.dll
008AD7AD 062CEA54 0001:004AC7AD C:\Program Files\World of Warcraft\Wow.exe
008ADFCC 062CEA68 0001:004ACFCC C:\Program Files\World of Warcraft\Wow.exe
7BC6F584 062CEA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 062CEB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 062CF398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 062CF498 0000:00000000 <unknown>

--- Thread ID: 34 ---
6AA5F817 05FEEA68 0001:0001E817 C:\windows\system32\winmm.dll
7BC6F584 05FEEA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 05FEEB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 05FEF398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 05FEF498 0000:00000000 <unknown>

--- Thread ID: 32 ---
7BC76263 02B0E858 0001:00065263 C:\windows\system32\ntdll.dll
7BC76553 02B0E898 0001:00065553 C:\windows\system32\ntdll.dll
7B869E56 02B0E9E8 0001:00058E56 C:\windows\system32\KERNEL32.dll
7B869F6C 02B0EA18 0001:00058F6C C:\windows\system32\KERNEL32.dll
0055F4D0 02B0EA28 0001:0015E4D0 C:\Program Files\World of Warcraft\Wow.exe
0048DAD2 02B0EA40 0001:0008CAD2 C:\Program Files\World of Warcraft\Wow.exe
0055AD7B 02B0EA68 0001:00159D7B C:\Program Files\World of Warcraft\Wow.exe
7BC6F584 02B0EA78 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 02B0EB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 02B0F398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 02B0F498 0000:00000000 <unknown>

--- Thread ID: 31 ---
7B869FE1 0163E5F4 0001:00058FE1 C:\windows\system32\KERNEL32.dll

--- Thread ID: 30 ---
7B869FE1 013FE9D4 0001:00058FE1 C:\windows\system32\KERNEL32.dll
7B86A025 013FE9F4 0001:00059025 C:\windows\system32\KERNEL32.dll
00437635 013FEA14 0001:00036635 C:\Program Files\World of Warcraft\Wow.exe
0044D35A 013FEA28 0001:0004C35A C:\Program Files\World of Warcraft\Wow.exe
0093236F 013FEA60 0001:0053136F C:\Program Files\World of Warcraft\Wow.exe
00932414 013FEA78 0001:00531414 C:\Program Files\World of Warcraft\Wow.exe
7BC6F750 013FEB48 0001:0005E750 C:\windows\system32\ntdll.dll
7BC77F35 013FF398 0001:00066F35 C:\windows\system32\ntdll.dll
703FF96E 013FF498 0000:00000000 <unknown>

--- Thread ID: 27 [Current Thread] ---
00644A87 003AF858 0001:00243A87 C:\Program Files\World of Warcraft\Wow.exe
0064210A 003AF878 0001:0024110A C:\Program Files\World of Warcraft\Wow.exe
0048F1C4 003AF8A8 0001:0008E1C4 C:\Program Files\World of Warcraft\Wow.exe
00499C1A 003AF8B4 0001:00098C1A C:\Program Files\World of Warcraft\Wow.exe
0049AADF 003AF8D8 0001:00099ADF C:\Program Files\World of Warcraft\Wow.exe
0049E068 003AF9AC 0001:0009D068 C:\Program Files\World of Warcraft\Wow.exe
0049E304 003AFA88 0001:0009D304 C:\Program Files\World of Warcraft\Wow.exe
008587DE 003AFB60 0001:004577DE C:\Program Files\World of Warcraft\Wow.exe
0080C2AB 003AFB84 0001:0040B2AB C:\Program Files\World of Warcraft\Wow.exe
0084C7F8 003AFC44 0001:0044B7F8 C:\Program Files\World of Warcraft\Wow.exe
0086A9F7 003AFC60 0001:004699F7 C:\Program Files\World of Warcraft\Wow.exe
0086AEEB 003AFC7C 0001:00469EEB C:\Program Files\World of Warcraft\Wow.exe
0083CB72 003AFD48 0001:0043BB72 C:\Program Files\World of Warcraft\Wow.exe
0088DA29 003AFD78 0001:0048CA29 C:\Program Files\World of Warcraft\Wow.exe
0088AB09 003AFDA0 0001:00489B09 C:\Program Files\World of Warcraft\Wow.exe
0088C11A 003AFDF4 0001:0048B11A C:\Program Files\World of Warcraft\Wow.exe
0088C161 003AFE0C 0001:0048B161 C:\Program Files\World of Warcraft\Wow.exe
00406D7D 003AFEA8 0001:00005D7D C:\Program Files\World of Warcraft\Wow.exe
7B858534 003AFEE8 0001:00047534 C:\windows\system32\KERNEL32.dll
7BC6F584 003AFEF8 0001:0005E584 C:\windows\system32\ntdll.dll
7BC6F750 003AFFC8 0001:0005E750 C:\windows\system32\ntdll.dll
7BC4B0AA 003AFFE8 0001:0003A0AA C:\windows\system32\ntdll.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 20/20 threads...

--- Thread ID: 52 ---
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000003,0x00000004,0x00000000,0x00000000)
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000003,0x00000000,0x00000000,0x00000000)
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000003,0x00000000,0x00000000,0x00000000)
68D1179C winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+268 (0x00000003,0xFFFFFFFF,0x00000000,0x00000000)
683A95F8 user32.dll   <unknown symbol>+0 (0x00000003,0xFFFFFFFF,0x00000000,0x7BC99FF4)
6836FD9A user32.dll   MsgWaitForMultipleObjectsEx+250 (0x00000002,0xFFFFFFFF,0x00000000,0x0044C1C7)
6836FDEF user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x00000000,0x00000000,0x08AC9780)
0044C3E6 Wow.exe      <unknown symbol>+0 (0x00AE79F8,0x08AC9DE0,0x0093236F,0xBBABB635)
0044D35A Wow.exe      <unknown symbol>+0 (0x08AC9780,0x00932395,0x7BC99FF4,0x096BEA34)
0093236F Wow.exe      <unknown symbol>+0 (0x7FF88F10,0x08AC9DE0,0x096BEB48,0x00932395)
00932414 Wow.exe      <unknown symbol>+0 (0x00932395,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x00932395,0x00000000,0x00000000,0x7FF881BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FF88FB8,0x096BFB70,0x096BF454,0x00000000)
703FF96E              start_thread+190 (0x096BFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 51 ---
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x7BC354D1)
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x00000000,0x0859B900)
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x00000000)
7B869F6C KERNEL32.dll WaitForSingleObject+60 (0x00002214,0x008ADF50,0x7BC99FF4,0x008AD949)
008EE4B5 Wow.exe      <unknown symbol>+0 (0x08ABAD30,0x0925EA68,0x08ABAD30,0x00000033)
008AD949 Wow.exe      <unknown symbol>+0 (0x08ABAD30,0x00000033,0x7BC6F584,0x7FF8CF10)
008ADF90 Wow.exe      <unknown symbol>+0 (0x08ABAD9C,0x0925EB48,0x008ADF50,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x008ADF50,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x008ADF50,0x00000000,0x00000000,0x7FF8C1BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FF8CFB8,0x0925FB70,0x0925F454,0x00000000)
703FF96E              start_thread+190 (0x0925FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 50 ---
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000003,0x00000004,0x00000000,0x00000000)
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000003,0x00000000,0x00000000,0x00000000)
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000003,0x00000000,0x00000000,0x00000000)
68D1179C winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+268 (0x00000003,0xFFFFFFFF,0x00000000,0x00000000)
683A95F8 user32.dll   <unknown symbol>+0 (0x00000003,0xFFFFFFFF,0x00000000,0x7BC99FF4)
6836FD9A user32.dll   MsgWaitForMultipleObjectsEx+250 (0x00000002,0xFFFFFFFF,0x00000000,0x0044C1C7)
6836FDEF user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x00000000,0x00000000,0x08A8E240)
0044C3E6 Wow.exe      <unknown symbol>+0 (0x00AE7998,0x08A91030,0x0093236F,0xBBCEB635)
0044D35A Wow.exe      <unknown symbol>+0 (0x08A8E240,0x00932395,0x7BC99FF4,0x090EEA34)
0093236F Wow.exe      <unknown symbol>+0 (0x7FF90F10,0x08A91030,0x090EEB48,0x00932395)
00932414 Wow.exe      <unknown symbol>+0 (0x00932395,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x00932395,0x00000000,0x00000000,0x7FF901BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FF90FB8,0x090EFB70,0x090EF454,0x00000000)
703FF96E              start_thread+190 (0x090EFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 49 ---
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x00000001)
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x00000000,0x00000000)
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x00000000)
7B869F6C KERNEL32.dll WaitForSingleObject+60 (0x000021DC,0x008ADF50,0x7BC99FF4,0x008AD949)
008EE4B5 Wow.exe      <unknown symbol>+0 (0x085898F0,0x08F7EA68,0x085898F0,0x00000031)
008AD949 Wow.exe      <unknown symbol>+0 (0x085898F0,0x00000031,0x7BC6F584,0x7FF94F10)
008ADF90 Wow.exe      <unknown symbol>+0 (0x0858888C,0x08F7EB48,0x008ADF50,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x008ADF50,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x008ADF50,0x00000000,0x00000000,0x7FF941BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FF94FB8,0x08F7FB70,0x08F7F454,0x00000000)
703FF96E              start_thread+190 (0x08F7FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 46 ---
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x08E0E9C8)
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x08E0EA48,0x00000000)
7BC765AC ntdll.dll    NtWaitForSingleObject+60 (0x000021C8,0x08E0EA48,0x00111650,0x08E0EB08)
7BC7B67F ntdll.dll    <unknown symbol>+0 (0x00000000,0x08E0EB48,0x7BC7B540,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x7BC7B540,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x7BC7B540,0x00000000,0x00000000,0x7FF981BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FF98FB8,0x08E0FB70,0x08E0F454,0x00000000)
703FF96E              start_thread+190 (0x08E0FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 45 ---
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x08C9E9C8)
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x08C9EA48,0x00000000)
7BC765AC ntdll.dll    NtWaitForSingleObject+60 (0x000021C8,0x08C9EA48,0x68794150,0x08C9EB08)
7BC7B67F ntdll.dll    <unknown symbol>+0 (0x00000000,0x08C9EB48,0x7BC7B540,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x7BC7B540,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x7BC7B540,0x00000000,0x00000000,0x7FF9C1BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FF9CFB8,0x08C9FB70,0x08C9F454,0x00000000)
703FF96E              start_thread+190 (0x08C9FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 44 ---
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000003,0x00000004,0x00000000,0x00000000)
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000003,0x00000000,0x00000000,0x00000000)
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000003,0x00000000,0x00000000,0x00000000)
68D1179C winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+268 (0x00000003,0xFFFFFFFF,0x00000000,0x00000000)
683A95F8 user32.dll   <unknown symbol>+0 (0x00000003,0xFFFFFFFF,0x00000000,0x7BC99FF4)
6836FD9A user32.dll   MsgWaitForMultipleObjectsEx+250 (0x00000002,0xFFFFFFFF,0x00000000,0x0044C1C7)
6836FDEF user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x00000000,0x00000000,0x085300B0)
0044C3E6 Wow.exe      <unknown symbol>+0 (0x00AE7950,0x08531AF0,0x0093236F,0xBAB5B635)
0044D35A Wow.exe      <unknown symbol>+0 (0x085300B0,0x00932395,0x7BC99FF4,0x0875EA34)
0093236F Wow.exe      <unknown symbol>+0 (0x7FFA0F10,0x08531AF0,0x0875EB48,0x00932395)
00932414 Wow.exe      <unknown symbol>+0 (0x00932395,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x00932395,0x00000000,0x00000000,0x7FFA01BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFA0FB8,0x0875FB70,0x0875F454,0x00000000)
703FF96E              start_thread+190 (0x0875FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 43 ---
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x7FFA4000)
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x0757E78C,0x00000000)
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x7B8696FA)
7B869ECA KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x00000000,0x0000002B,0x04D2F618)
00468D1B Wow.exe      <unknown symbol>+0 (0x070C8FC0,0x0055AD7B,0x0055ACE0,0x7BC99FF4)
004683CE Wow.exe      <unknown symbol>+0 (0x04D2F618,0x7FFA4F10,0x000021A4,0x04D2F618)
0055AD7B Wow.exe      <unknown symbol>+0 (0x00B78EF0,0x0757EB48,0x0055ACE0,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x0055ACE0,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x0055ACE0,0x00000000,0x00000000,0x7FFA41BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFA4FB8,0x0757FB70,0x0757F454,0x00000000)
703FF96E              start_thread+190 (0x0757FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 42 ---
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x7BC6EBBE)
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x0740E9BC,0x7BC99FF4)
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x009747F1)
7B869F6C KERNEL32.dll WaitForSingleObject+60 (0x00002114,0x0740EA34,0x000003E8,0x070C8FE0)
0055F4D0 Wow.exe      <unknown symbol>+0 (0x000003E8,0x070C8FE0,0x0740EA40,0x00000000)
00468505 Wow.exe      <unknown symbol>+0 (0x00000000,0x0055AD7B,0x0055ACE0,0x7BC99FF4)
00468671 Wow.exe      <unknown symbol>+0 (0x04D2F628,0x7FFA8F10,0x000021A0,0x04D2F628)
0055AD7B Wow.exe      <unknown symbol>+0 (0x00B78ED0,0x0740EB48,0x0055ACE0,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x0055ACE0,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x0055ACE0,0x00000000,0x00000000,0x7FFA81BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x0740FB70,0x0740F454,0x00000000)
703FF96E              start_thread+190 (0x0740FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 41 ---
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x00000000)
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x00000000,0x00000001)
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x0729EA24)
7B869F6C KERNEL32.dll WaitForSingleObject+60 (0x00002078,0x0729EA68,0xFFFFFFFF,0x0055AD7B)
0055F4D0 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x0055AD7B,0x0055ACE0,0x7BC99FF4)
007FAF3B Wow.exe      <unknown symbol>+0 (0x00B78EB0,0x0729EB48,0x0055ACE0,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x0055ACE0,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x0055ACE0,0x00000000,0x00000000,0x7FFAC1BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x0729FB70,0x0729F454,0x00000000)
703FF96E              start_thread+190 (0x0729FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 40 ---
7B869FE1 KERNEL32.dll SleepEx+65 (0x0000000A,0x0682EA54,0x7B86A009,0x0682EA54)
7B86A025 KERNEL32.dll Sleep+37 (0x0000000A,0x008ADFCC,0x7FFB0F10,0x0682EA78)
008AD7AD Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000028,0x7BC6F584,0x7FFB0F10)
008ADFCC Wow.exe      <unknown symbol>+0 (0x04C37FD8,0x0682EB48,0x008ADF50,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x008ADF50,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x008ADF50,0x00000000,0x00000000,0x7FFB01BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x0682FB70,0x0682F454,0x00000000)
703FF96E              start_thread+190 (0x0682FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 39 ---
7B869FE1 KERNEL32.dll SleepEx+65 (0x0000000A,0x00000000,0x7B86A009,0x065AEA54)
7B86A025 KERNEL32.dll Sleep+37 (0x0000000A,0x008ADFCC,0x7FFB4F10,0x065AEA78)
008AD7AD Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000027,0x7BC6F584,0x7FFB4F10)
008ADFCC Wow.exe      <unknown symbol>+0 (0x0356C3B0,0x065AEB48,0x008ADF50,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x008ADF50,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x008ADF50,0x00000000,0x00000000,0x7FFB41BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x065AFB70,0x065AF454,0x00000000)
703FF96E              start_thread+190 (0x065AFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 38 ---
2014EF5B winepulse.drv PULSE_WaitRingMessage+59 (0x00150EFC,0x05E7EA48,0x05E7E9E8,0x7BC6EAEB)
2014A148 winepulse.drv <unknown symbol>+0 (0x00150E00,0x05E7EB48,0x2014A0C0,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x2014A0C0,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x2014A0C0,0x00000000,0x00000000,0x7FFC81BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x05E7FB70,0x05E7F454,0x00000000)
703FF96E              start_thread+190 (0x05E7FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 37 ---
7B869FE1 KERNEL32.dll SleepEx+65 (0x0000000A,0x0643EA54,0x7B86A009,0x0643EA54)
7B86A025 KERNEL32.dll Sleep+37 (0x0000000A,0x008ADFCC,0x7FFB8F10,0x0643EA78)
008AD7AD Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000025,0x7BC6F584,0x7FFB8F10)
008ADFCC Wow.exe      <unknown symbol>+0 (0x0368A360,0x0643EB48,0x008ADF50,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x008ADF50,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x008ADF50,0x00000000,0x00000000,0x7FFB81BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x0643FB70,0x0643F454,0x00000000)
703FF96E              start_thread+190 (0x0643FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 36 ---
7B869FE1 KERNEL32.dll SleepEx+65 (0x0000000A,0x00000000,0x7B86A009,0x062CEA54)
7B86A025 KERNEL32.dll Sleep+37 (0x0000000A,0x008ADFCC,0x7FFBCF10,0x062CEA78)
008AD7AD Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000024,0x7BC6F584,0x7FFBCF10)
008ADFCC Wow.exe      <unknown symbol>+0 (0x0351E598,0x062CEB48,0x008ADF50,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x008ADF50,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x008ADF50,0x00000000,0x00000000,0x7FFBC1BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x062CFB70,0x062CF454,0x00000000)
703FF96E              start_thread+190 (0x062CFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 34 ---
6AA5F817 winmm.dll    <unknown symbol>+0 (0x00000000,0x05FEEB48,0x6AA5F640,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x6AA5F640,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x6AA5F640,0x00000000,0x00000000,0x7FFC41BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFC4FB8,0x05FEFB70,0x05FEF454,0x00000000)
703FF96E              start_thread+190 (0x05FEFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 32 ---
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x7FFCC000)
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x00000000,0x02B0E9C8)
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x7B86974A)
7B869F6C KERNEL32.dll WaitForSingleObject+60 (0x00002068,0x02B0EA40,0xFFFFFFFF,0x00000020)
0055F4D0 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x00000020,0x02B0EA68,0x00AEF040)
0048DAD2 Wow.exe      <unknown symbol>+0 (0x00AEF040,0x7FFCCF10,0x000020C8,0x00AEF040)
0055AD7B Wow.exe      <unknown symbol>+0 (0x00B78E90,0x02B0EB48,0x0055ACE0,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x0055ACE0,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x0055ACE0,0x00000000,0x00000000,0x7FFCC1BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x02B0FB70,0x02B0F454,0x00000000)
703FF96E              start_thread+190 (0x02B0FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 31 ---
7B869FE1 KERNEL32.dll SleepEx+65 (0x00000001,0x0163E614,0x7B86A009,0x0163E620)
7B86A025 KERNEL32.dll Sleep+37 (0x00000001,0x0082C3ED,0x0120A170,0x000020C4)
0000207C <unknown module> <unknown symbol>+0 (0x00000001,0x0000001F,0x00000000,0x00000000)
0082C3ED Wow.exe      <unknown symbol>+0 (0x0120A190,0x7FFD0F10,0x000020C4,0x0120A190)
0055AD7B Wow.exe      <unknown symbol>+0 (0x00B78E70,0x0163EB48,0x0055ACE0,0x7BC99FF4)
7BC6F584 ntdll.dll    call_thread_func+12 (0x0055ACE0,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x0055ACE0,0x00000000,0x00000000,0x7FFD01BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFD0FB8,0x0163FB70,0x0163F454,0x00000000)
703FF96E              start_thread+190 (0x0163FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 30 ---
7B869FE1 KERNEL32.dll SleepEx+65 (0x00000064,0x013FE9F4,0x7B86A009,0x013FEA14)
7B86A025 KERNEL32.dll Sleep+37 (0x00000064,0x7BC99FF4,0x00020000,0x013FEA28)
00437635 Wow.exe      <unknown symbol>+0 (0x00000000,0x01203980,0x0093236F,0xB3FFB635)
0044D35A Wow.exe      <unknown symbol>+0 (0x01202320,0x00932395,0x7BC99FF4,0x013FEA34)
0093236F Wow.exe      <unknown symbol>+0 (0x7FFD4F10,0x01203980,0x013FEB48,0x00932395)
00932414 Wow.exe      <unknown symbol>+0 (0x00932395,0x7BC99FF4,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x00932395,0x00000000,0x00000000,0x7FFD41BC)
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x013FFB70,0x013FF454,0x00000000)
703FF96E              start_thread+190 (0x013FFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 27 [Current Thread] ---
00644A87 Wow.exe      <unknown symbol>+0 (0x00000006,0x00000006,0x08ACB330,0x003AF8A8)
0064210A Wow.exe      <unknown symbol>+0 (0x08ACB330,0x00000000,0x08ACB520,0x00000000)
0048F1C4 Wow.exe      <unknown symbol>+0 (0x00000B70,0x0049AADF,0x00000000,0x003AF8D4)
00499C1A Wow.exe      <unknown symbol>+0 (0x00000000,0x003AF9CC,0x0048E31E,0x003AF9AC)
0049AADF Wow.exe      <unknown symbol>+0 (0x00000000,0x085B2E70,0x80000000,0x80000000)
0049E068 Wow.exe      <unknown symbol>+0 (0x00000000,0x08ACB520,0x00000001,0x3F77FE41)
0049E304 Wow.exe      <unknown symbol>+0 (0x00000000,0x3F800000,0x00000000,0x00000000)
008587DE Wow.exe      <unknown symbol>+0 (0xFF000000,0x08AC9D80,0x00000014,0x41A33333)
0080C2AB Wow.exe      <unknown symbol>+0 (0xFF000000,0x08560570,0x0084C16C,0x00000002)
0084C7F8 Wow.exe      <unknown symbol>+0 (0x085605EC,0x00000006,0x08544490,0x0086AEEB)
0086A9F7 Wow.exe      <unknown symbol>+0 (0x0127FD10,0x08544690,0x00000000,0x0083CB72)
0086AEEB Wow.exe      <unknown symbol>+0 (0x00000000,0x085446A8,0x01263780,0x0120A550)
0083CB72 Wow.exe      <unknown symbol>+0 (0x00000000,0x0000676C,0x01263780,0x0000676C)
0088DA29 Wow.exe      <unknown symbol>+0 (0x0120A3D0,0x00000000,0x00000565,0x00000001)
0088AB09 Wow.exe      <unknown symbol>+0 (0x00000000,0x00000002,0x3120656E,0x7B869930)
0088C11A Wow.exe      <unknown symbol>+0 (0x00000000,0x00000001,0x003AFEA8,0x0040B979)
0088C161 Wow.exe      <unknown symbol>+0 (0x0040B979,0x00000000,0x0000000A,0x00401000)
00406D7D Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B858534 KERNEL32.dll <unknown symbol>+0 (0x7FFDF000,0x003AFFC8,0x7B8584E0,0x00000000)
7BC6F584 ntdll.dll    call_thread_func+12 (0x7B8584E0,0x00000000,0xFFFFFFFF,0x7B836E60)
7BC6F750 ntdll.dll    call_thread_entry_point+112 (0x7B8584E0,0x00000000,0x00000000,0x00000000)
7BC4B0AA ntdll.dll    <unknown symbol>+0 (0x7B8584E0,0x00000000,0x00000001,0x73676F4C)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00D9C000  C:\Program Files\World of Warcraft\Wow.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x20010000 - 0x20136000  C:\windows\system32\wined3d.dll
0x20140000 - 0x20153000  C:\windows\system32\winepulse.drv
0x202A0000 - 0x202B4000  C:\windows\system32\msacm32.drv
0x202C0000 - 0x202CA000  C:\windows\system32\midimap.dll
0x5BD40000 - 0x5BD6B000  C:\windows\system32\d3d9.dll
0x66550000 - 0x6659F000  C:\windows\system32\dbghelp.dll
0x68310000 - 0x6840A000  C:\windows\system32\user32.dll
0x68420000 - 0x68494000  C:\windows\system32\gdi32.dll
0x684A0000 - 0x68505000  C:\windows\system32\rpcrt4.dll
0x68520000 - 0x685AA000  C:\windows\system32\opengl32.dll
0x68750000 - 0x68761000  C:\windows\system32\imm32.dll
0x68770000 - 0x687BA000  C:\windows\system32\wininet.dll
0x687E0000 - 0x687F2000  C:\windows\system32\mpr.dll
0x68800000 - 0x68851000  C:\windows\system32\shlwapi.dll
0x68860000 - 0x689E5000  C:\windows\system32\shell32.dll
0x689F0000 - 0x68AB3000  C:\windows\system32\comctl32.dll
0x68AC0000 - 0x68ADF000  C:\windows\system32\ws2_32.dll
0x68AE0000 - 0x68AFA000  C:\windows\system32\dinput8.dll
0x68B00000 - 0x68B33000  C:\windows\system32\dinput.dll
0x68B40000 - 0x68B8C000  C:\windows\system32\setupapi.dll
0x68B90000 - 0x68BC2000  C:\windows\system32\winspool.drv
0x68BD0000 - 0x68BDB000  C:\windows\system32\version.dll
0x68BE0000 - 0x68BEF000  C:\windows\system32\lz32.dll
0x68BF0000 - 0x68C04000  C:\windows\system32\hid.dll
0x68CE0000 - 0x68D70000  C:\windows\system32\winex11.drv
0x68DA0000 - 0x68DC7000  C:\windows\system32\uxtheme.dll
0x68DD0000 - 0x68DE7000  C:\windows\system32\localspl.dll
0x68DF0000 - 0x68E00000  C:\windows\system32\spoolss.dll
0x6AA40000 - 0x6AAC1000  C:\windows\system32\winmm.dll
0x6EDE0000 - 0x6EE2C000  C:\windows\system32\advapi32.dll
0x72B60000 - 0x72C3C000  C:\windows\system32\ole32.dll
0x74950000 - 0x74964000  C:\windows\system32\psapi.dll
0x75540000 - 0x7555A000  C:\windows\system32\msacm32.dll
0x79800000 - 0x79842000  C:\windows\system32\dsound.dll
0x7B810000 - 0x7B93A000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCB6000  C:\windows\system32\ntdll.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 00644A87)

00644A87: 89 B4 8A 70  28 00 00 8B  08 8B 38 81  C1 79 02 00  ...p(.....8..y..


Stack: 1024 bytes starting at (ESP = 003AF84C)

* = addr                                         **                       *   
003AF840: 10 29 5B 08  60 B3 AC 08  10 29 5B 08  0C 00 00 00  .)[.`....)[.....
003AF850: 98 C2 9F 00  30 B3 AC 08  78 F8 3A 00  0A 21 64 00  ....0...x.:..!d.
003AF860: 06 00 00 00  E0 89 BB 00  06 00 00 00  20 87 D6 03  ............ ...
003AF870: 30 B3 AC 08  10 29 5B 08  A8 F8 3A 00  C4 F1 48 00  0....)[...:...H.
003AF880: 30 B3 AC 08  0C 00 00 00  00 00 00 00  CC F9 3A 00  0.............:.
003AF890: 20 B5 AC 08  D0 2D 00 00  00 00 00 00  01 00 00 00   ....-..........
003AF8A0: 20 87 D6 03  3D 00 00 00  B4 F8 3A 00  1A 9C 49 00   ...=.....:...I.
003AF8B0: 70 0B 00 00  D8 F8 3A 00  DF AA 49 00  00 00 00 00  p.....:...I.....
003AF8C0: 00 00 00 00  CC F9 3A 00  D4 F8 3A 00  1E E3 48 00  ......:...:...H.
003AF8D0: 10 29 5B 08  AC F9 3A 00  AC F9 3A 00  68 E0 49 00  .)[...:...:.h.I.
003AF8E0: 00 00 00 00  00 00 00 00  70 2E 5B 08  41 FE 77 3F  ........p.[.A.w?
003AF8F0: 00 00 00 80  00 00 00 00  00 00 00 80  00 00 00 80  ................
003AF900: AF FE 39 3F  00 00 00 80  00 00 00 00  00 00 00 00  ..9?............
003AF910: 00 00 00 80  00 00 00 00  00 00 80 3F  00 00 00 80  ...........?....
003AF920: 00 00 00 00  0D FD 8F C0  FF FF 8F 40  3D 9F 49 AC  ...........@=.I.
003AF930: 26 77 89 B7  00 00 80 BF  00 00 00 00  00 00 80 3F  &w.............?
003AF940: 2E BD 3B B4  00 00 00 00  00 00 00 00  2E BD 3B 34  ..;...........;4
003AF950: 00 00 80 3F  26 77 89 B7  00 00 00 00  00 00 00 00  ...?&w..........
003AF960: 00 00 00 00  00 00 00 00  00 00 80 3F  F6 21 84 3F  ...........?.!.?
003AF970: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AF980: 49 2D B0 3F  00 00 00 00  00 00 00 00  00 00 00 00  I-.?............
003AF990: 00 00 00 00  9F 02 80 3F  00 00 80 3F  00 00 00 00  .......?...?....
003AF9A0: 00 00 00 00  E2 92 63 BE  00 00 00 00  88 FA 3A 00  ......c.......:.
003AF9B0: 04 E3 49 00  00 00 00 00  30 1B 07 10  20 B5 AC 08  ..I.....0... ...
003AF9C0: 02 00 00 00  01 00 00 00  14 AE 61 05  41 FE 77 3F  ..........a.A.w?
003AF9D0: 00 00 00 80  00 00 00 00  00 00 00 80  00 00 00 80  ................
003AF9E0: AF FE 39 3F  00 00 00 80  00 00 00 00  00 00 00 00  ..9?............
003AF9F0: 00 00 00 80  00 00 00 00  00 00 80 3F  00 00 00 80  ...........?....
003AFA00: 00 00 00 00  0D FD 8F C0  FF FF 8F 40  70 2E 5B 08  ...........@p.[.
003AFA10: 40 F0 AE 00  30 00 76 08  00 00 00 00  C0 24 07 10  @...0.v......$..
003AFA20: 00 00 00 00  00 00 00 00  FF FF FF FF  20 C0 8A 08  ............ ...
003AFA30: 00 00 00 00  10 29 5B 08  00 00 00 00  F4 C1 8A 08  .....)[.........
003AFA40: 00 00 00 00  01 00 00 00  00 00 00 00  01 00 00 00  ................
003AFA50: FF FF FF FF  20 A5 68 05  00 00 00 00  28 46 B0 05  .... .h.....(F..
003AFA60: 00 00 00 00  B4 36 7F 08  00 00 00 00  60 20 50 08  .....6......` P.
003AFA70: 00 DD 50 08  B0 72 12 07  20 4E 4F 08  50 24 4F 08  ..P..r.. NO.P$O.
003AFA80: D0 00 50 08  00 00 00 00  60 FB 3A 00  DE 87 85 00  ..P.....`.:.....
003AFA90: 00 00 00 00  14 AE 61 05  00 00 80 3F  00 00 00 00  ......a....?....
003AFAA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 80 3F  ...............?
003AFAB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFAC0: 00 00 80 3F  00 00 00 00  CD CC CC BE  99 99 99 BE  ...?............
003AFAD0: 00 00 00 00  00 00 80 3F  00 00 20 40  00 00 00 00  .......?.. @....
003AFAE0: 00 00 00 00  00 00 00 00  00 00 00 00  56 55 55 40  ............VUU@
003AFAF0: 00 00 00 00  00 00 00 00  00 00 00 80  00 00 00 80  ................
003AFB00: 6F 12 03 BB  00 00 00 00  6F 12 03 BA  6E 12 03 3A  o.......o...n..:
003AFB10: 00 00 00 80  00 00 80 3F  CC 8D 24 C1  1D 7F 0F BD  .......?..$.....
003AFB20: 58 41 1C 40  C0 97 13 00  00 00 00 00  C0 DF 31 41  XA.@..........1A
003AFB30: 1D 7F 0F BD  17 47 1C 40  00 00 00 00  00 00 00 00  .....G.@........
003AFB40: 00 00 80 3F  00 00 00 00  00 00 80 3F  00 00 80 3F  ...?.......?...?
003AFB50: 00 00 00 00  00 00 00 00  00 00 80 3F  00 00 80 3F  ...........?...?
003AFB60: 84 FB 3A 00  AB C2 80 00  00 00 00 FF  EC 05 56 08  ..:...........V.
003AFB70: 80 9D AC 08  00 00 00 00  14 00 00 00  00 00 00 00  ................
003AFB80: 33 33 A3 41  44 FC 3A 00  F8 C7 84 00  00 00 00 FF  33.AD.:.........
003AFB90: 01 00 00 00  70 05 56 08  EC 05 56 08  6C C1 84 00  ....p.V...V.l...
003AFBA0: 70 7E A3 08  02 00 00 00  04 00 00 00  E4 70 6D 05  p~...........pm.
003AFBB0: 44 71 6D 05  00 00 00 00  00 00 00 00  06 00 00 00  Dqm.............
003AFBC0: BC F2 A9 00  D0 90 20 01  DC D7 60 05  02 00 00 00  ...... ...`.....
003AFBD0: FE FF FF FF  3E 11 41 00  CF 93 55 00  F0 9C AC 08  ....>.A...U.....
003AFBE0: 2C 4E 57 08  E0 9C 6A 05  0C FC 3A 00  C8 CF 84 00  ,NW...j...:.....
003AFBF0: 10 00 00 00  2C F3 A9 00  FE FF FF FF  08 00 00 00  ....,...........
003AFC00: 0C 88 AC 08  10 FC 3A 00  25 C8 84 00  04 70 6D 05  ......:.%....pm.
003AFC10: 28 FC 3A 00  76 0D 86 00  0C 88 AC 08  6C 88 AC 08  (.:.v.......l...
003AFC20: 6C 88 AC 08  90 87 AC 08  00 00 00 00  66 A6 86 00  l...........f...
003AFC30: 6C 88 AC 08  77 A6 86 00  05 00 00 00  06 00 00 00  l...w...........
003AFC40: 90 44 54 08  60 FC 3A 00  F7 A9 86 00  EC 05 56 08  .DT.`.:.......V.


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
Processor Revision:     7170
Os Version:             4.0
Os Service Pack:        6.0

Percent memory used:    44
Total physical memory:  1041612800
Free Memory:            578940928
Page file:              4093149184
Total virtual memory:   2147352575
===================================================================
```
then it shuts down. I have tried the opengl thing and it still doesn't work

My computer is a dell mini 10v
dual core 1.60GHz
1GB ram
Mobile 945GME Express Integrated Graphics Controller

---

### Post by asdfoo on 2010-05-21
make sure you are using the most recent version of wine which is 1.2rc1 (released less than 1 day ago)

You may find that you will not have a very good experience with an intel video card, Intel does not provide proper support for them on linux.  Most people find that nvidia is the most stable, followed by ati and then intel.

---

### Post by Drastic2010 on 2010-05-21
You must config the rendering options by adding:

SET gxApi "opengl"

to your wow build.

---

### Post by jhnlambert on 2010-05-22
> **Drastic2010 said:**
> You must config the rendering options by adding:

SET gxApi "opengl"

to your wow build.

how exactly would I do That?

---

### Post by jhnlambert on 2010-05-22
OK im downloading the newest version of wine!!!! hope this works:-)
Thanks for all the help already guys!!

---

### Post by hikaricore on 2010-05-22
Probably won't on that hardware, but good luck.

---

### Post by jhnlambert on 2010-05-22
OK wow works after i redownloaded everything. it only get 2-3 fps and if i try using opengl it gives me the error message:(

---

### Post by hikaricore on 2010-05-22
You'll probably get a real video card or dual boot then.

---

### Post by jhnlambert on 2010-05-22
> **hikaricore said:**
> You'll probably get a real video card or dual boot then.

Sorry dumb question but can you upgrade the video card on a netbook?

---

### Post by Munk3y on 2010-05-22
> **jhnlambert said:**
> Sorry dumb question but can you upgrade the video card on a netbook?

Nope :(

---

### Post by hikaricore on 2010-05-23
I'm amazed that you can even run Wow on a netbook in windows.  O.o
Those little things are getting beefier every day aren't they?

---

### Post by mellowtothemax on 2010-05-23
> **jhnlambert said:**
> how exactly would I do That?

edit config.wtf located in wow installation folder and add it to the end

---

### Post by zmoky on 2010-07-27
I have the same problem.
I have a quad core, 4gb RAM and 2x8800gt in SLi and WoW crashes at start with the memory write error exception:
```
==============================================================================
World of WarCraft (build 12340)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Jul 27, 2010  8:57:54.170 PM
User:     zmoky
Computer: zmoky-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:    C:\Program Files\World of Warcraft\Wow.exe
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0023:7EBCDE1A

The instruction at "0x7EBCDE1A" referenced memory at "0x79A7DA7C".
The memory could not be "read".


WoWBuild: 12340
Settings: 
SET locale "enUS"
SET realmList "realm.*******.com"
SET coresDetected "1"
SET hwDetect "0"
SET gxResolution "1280x1024"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET gxApi "opengl"
SET videoOptionsVersion "3"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "0"
SET Sound_OutputDriverName "System Default"
SET farclip "1277"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET groundEffectDist "140"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET gxTripleBuffer "1"
SET textureFilteringMode "5"
SET movieSubtitle "1"
SET Sound_NumChannels "64"
SET Sound_EnableHardware "1"
SET readTerminationWithoutNotice "-1"
SET readScanning "-1"
SET readContest "-1"
SET mouseSpeed "1.25"
SET installType "Retail"
SET patchlist "us.version.worldofwarcraft.com"
SET accounttype "LK"
SET particleDensity "1"
SET weatherDensity "3"
SET environmentDetail "1.5"
SET realmName "Divine"
SET gameTip "8"
SET gxWindow "1"
SET gxMultisample "4"
SET componentTextureLevel "9"
SET shadowLevel "0"
SET specular "1"
SET groundEffectDensity "64"
SET projectedTextures "1"

----------------------------------------
               GxInfo
----------------------------------------
GxApi: OpenGL
Vendor: NVIDIA Corporation
Renderer: GeForce 8800 GT/PCI/SSE2
Version: 2.1.2 NVIDIA 173.14.22

------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000000  EBX=79A7D950  ECX=00000000  EDX=79A7D918  ESI=0192EDD0
EDI=00000000  EBP=0192ED98  ESP=0192ECA0  EIP=7EBCDE1A  FLG=00010246
CS =0023      DS =002B      ES =002B      SS =002B      FS =0063      GS =006B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 19/19 threads...

--- Thread ID: 47 ---
7BC77603 0622E868 0001:00066603 C:\windows\system32\ntdll.dll
7BC778F3 0622E8A8 0001:000668F3 C:\windows\system32\ntdll.dll
7B86A376 0622E9F8 0001:00059376 C:\windows\system32\KERNEL32.dll
7B86A48C 0622EA28 0001:0005948C C:\windows\system32\KERNEL32.dll
008E4FA5 0622EA44 0001:004E3FA5 C:\Program Files\World of Warcraft\Wow.exe
008D2029 0622EA54 0001:004D1029 C:\Program Files\World of Warcraft\Wow.exe
008E51D0 0622EA68 0001:004E41D0 C:\Program Files\World of Warcraft\Wow.exe
7BC707F4 0622EA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 0622EB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 0622F398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 0622F498 0000:00000000 <unknown>

--- Thread ID: 45 ---
7BC77603 081FE988 0001:00066603 C:\windows\system32\ntdll.dll
7BC778F3 081FE9C8 0001:000668F3 C:\windows\system32\ntdll.dll
7BC7794C 081FE9F8 0001:0006694C C:\windows\system32\ntdll.dll
7BC7CACF 081FEA68 0001:0006BACF C:\windows\system32\ntdll.dll
7BC707F4 081FEA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 081FEB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 081FF398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 081FF498 0000:00000000 <unknown>

--- Thread ID: 44 ---
7BC77603 0808E5E8 0001:00066603 C:\windows\system32\ntdll.dll
7BC778F3 0808E628 0001:000668F3 C:\windows\system32\ntdll.dll
7B86A376 0808E778 0001:00059376 C:\windows\system32\KERNEL32.dll
7D38D02C 0808E7B8 0001:0002C02C C:\windows\system32\winex11.drv
7DD69FA8 0808E7F8 0001:00098FA8 C:\windows\system32\user32.dll
7DD300DA 0808E9B8 0001:0005F0DA C:\windows\system32\user32.dll
7DD3012F 0808E9E8 0001:0005F12F C:\windows\system32\user32.dll
0044CFA6 0808EA14 0001:0004BFA6 C:\Program Files\World of Warcraft\Wow.exe
0044DF1A 0808EA28 0001:0004CF1A C:\Program Files\World of Warcraft\Wow.exe
0088C5DF 0808EA60 0001:0048B5DF C:\Program Files\World of Warcraft\Wow.exe
0088C684 0808EA78 0001:0048B684 C:\Program Files\World of Warcraft\Wow.exe
7BC709C0 0808EB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 0808F398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 0808F498 0000:00000000 <unknown>

--- Thread ID: 43 ---
7BC77603 07F1E868 0001:00066603 C:\windows\system32\ntdll.dll
7BC778F3 07F1E8A8 0001:000668F3 C:\windows\system32\ntdll.dll
7B86A376 07F1E9F8 0001:00059376 C:\windows\system32\KERNEL32.dll
7B86A48C 07F1EA28 0001:0005948C C:\windows\system32\KERNEL32.dll
008E4FA5 07F1EA44 0001:004E3FA5 C:\Program Files\World of Warcraft\Wow.exe
008D2029 07F1EA54 0001:004D1029 C:\Program Files\World of Warcraft\Wow.exe
008E51D0 07F1EA68 0001:004E41D0 C:\Program Files\World of Warcraft\Wow.exe
7BC707F4 07F1EA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 07F1EB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 07F1F398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 07F1F498 0000:00000000 <unknown>

--- Thread ID: 42 ---
7BC77603 07DAE988 0001:00066603 C:\windows\system32\ntdll.dll
7BC778F3 07DAE9C8 0001:000668F3 C:\windows\system32\ntdll.dll
7BC7794C 07DAE9F8 0001:0006694C C:\windows\system32\ntdll.dll
7BC7CACF 07DAEA68 0001:0006BACF C:\windows\system32\ntdll.dll
7BC707F4 07DAEA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 07DAEB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 07DAF398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 07DAF498 0000:00000000 <unknown>

--- Thread ID: 41 ---
7BC77603 07C3E988 0001:00066603 C:\windows\system32\ntdll.dll
7BC778F3 07C3E9C8 0001:000668F3 C:\windows\system32\ntdll.dll
7BC7794C 07C3E9F8 0001:0006694C C:\windows\system32\ntdll.dll
7BC7CACF 07C3EA68 0001:0006BACF C:\windows\system32\ntdll.dll
7BC707F4 07C3EA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 07C3EB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 07C3F398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 07C3F498 0000:00000000 <unknown>

--- Thread ID: 40 ---
7BC77603 077FE5E8 0001:00066603 C:\windows\system32\ntdll.dll
7BC778F3 077FE628 0001:000668F3 C:\windows\system32\ntdll.dll
7B86A376 077FE778 0001:00059376 C:\windows\system32\KERNEL32.dll
7D38D02C 077FE7B8 0001:0002C02C C:\windows\system32\winex11.drv
7DD69FA8 077FE7F8 0001:00098FA8 C:\windows\system32\user32.dll
7DD300DA 077FE9B8 0001:0005F0DA C:\windows\system32\user32.dll
7DD3012F 077FE9E8 0001:0005F12F C:\windows\system32\user32.dll
0044CFA6 077FEA14 0001:0004BFA6 C:\Program Files\World of Warcraft\Wow.exe
0044DF1A 077FEA28 0001:0004CF1A C:\Program Files\World of Warcraft\Wow.exe
0088C5DF 077FEA60 0001:0048B5DF C:\Program Files\World of Warcraft\Wow.exe
0088C684 077FEA78 0001:0048B684 C:\Program Files\World of Warcraft\Wow.exe
7BC709C0 077FEB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 077FF398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 077FF498 0000:00000000 <unknown>

--- Thread ID: 39 ---
7BC77603 06D6E61C 0001:00066603 C:\windows\system32\ntdll.dll
7BC778F3 06D6E65C 0001:000668F3 C:\windows\system32\ntdll.dll
7B86A376 06D6E7AC 0001:00059376 C:\windows\system32\KERNEL32.dll
7B86A3EA 06D6E7DC 0001:000593EA C:\windows\system32\KERNEL32.dll
004699CB 06D6EA34 0001:000689CB C:\Program Files\World of Warcraft\Wow.exe
0046906E 06D6EA40 0001:0006806E C:\Program Files\World of Warcraft\Wow.exe
0076FFCB 06D6EA68 0001:0036EFCB C:\Program Files\World of Warcraft\Wow.exe
7BC707F4 06D6EA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 06D6EB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 06D6F398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 06D6F498 0000:00000000 <unknown>

--- Thread ID: 38 ---
7BC77603 06BFE84C 0001:00066603 C:\windows\system32\ntdll.dll
7BC778F3 06BFE88C 0001:000668F3 C:\windows\system32\ntdll.dll
7B86A376 06BFE9DC 0001:00059376 C:\windows\system32\KERNEL32.dll
7B86A48C 06BFEA0C 0001:0005948C C:\windows\system32\KERNEL32.dll
007746A0 06BFEA1C 0001:003736A0 C:\Program Files\World of Warcraft\Wow.exe
004691A5 06BFEA34 0001:000681A5 C:\Program Files\World of Warcraft\Wow.exe
00469311 06BFEA40 0001:00068311 C:\Program Files\World of Warcraft\Wow.exe
0076FFCB 06BFEA68 0001:0036EFCB C:\Program Files\World of Warcraft\Wow.exe
7BC707F4 06BFEA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 06BFEB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 06BFF398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 06BFF498 0000:00000000 <unknown>

--- Thread ID: 37 ---
7BC77603 067DE864 0001:00066603 C:\windows\system32\ntdll.dll
7BC778F3 067DE8A4 0001:000668F3 C:\windows\system32\ntdll.dll
7B86A376 067DE9F4 0001:00059376 C:\windows\system32\KERNEL32.dll
7B86A48C 067DEA24 0001:0005948C C:\windows\system32\KERNEL32.dll
007746A0 067DEA34 0001:003736A0 C:\Program Files\World of Warcraft\Wow.exe
004F12CB 067DEA68 0001:000F02CB C:\Program Files\World of Warcraft\Wow.exe
7BC707F4 067DEA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 067DEB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 067DF398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 067DF498 0000:00000000 <unknown>

--- Thread ID: 36 ---
7B86A501 0650EA28 0001:00059501 C:\windows\system32\KERNEL32.dll
7B86A545 0650EA48 0001:00059545 C:\windows\system32\KERNEL32.dll
008D1E8D 0650EA54 0001:004D0E8D C:\Program Files\World of Warcraft\Wow.exe
008E520C 0650EA68 0001:004E420C C:\Program Files\World of Warcraft\Wow.exe
7BC707F4 0650EA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 0650EB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 0650F398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 0650F498 0000:00000000 <unknown>

--- Thread ID: 35 ---
7B86A501 0639EA28 0001:00059501 C:\windows\system32\KERNEL32.dll
7B86A545 0639EA48 0001:00059545 C:\windows\system32\KERNEL32.dll
008D1E8D 0639EA54 0001:004D0E8D C:\Program Files\World of Warcraft\Wow.exe
008E520C 0639EA68 0001:004E420C C:\Program Files\World of Warcraft\Wow.exe
7BC707F4 0639EA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 0639EB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 0639F398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 0639F498 0000:00000000 <unknown>

--- Thread ID: 32 ---
7B86A501 060BEA28 0001:00059501 C:\windows\system32\KERNEL32.dll
7B86A545 060BEA48 0001:00059545 C:\windows\system32\KERNEL32.dll
008D1E8D 060BEA54 0001:004D0E8D C:\Program Files\World of Warcraft\Wow.exe
008E520C 060BEA68 0001:004E420C C:\Program Files\World of Warcraft\Wow.exe
7BC707F4 060BEA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 060BEB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 060BF398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 060BF498 0000:00000000 <unknown>

--- Thread ID: 31 ---
7B86A501 05F4EA28 0001:00059501 C:\windows\system32\KERNEL32.dll
7B86A545 05F4EA48 0001:00059545 C:\windows\system32\KERNEL32.dll
008D1E8D 05F4EA54 0001:004D0E8D C:\Program Files\World of Warcraft\Wow.exe
008E520C 05F4EA68 0001:004E420C C:\Program Files\World of Warcraft\Wow.exe
7BC707F4 05F4EA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 05F4EB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 05F4F398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 05F4F498 0000:00000000 <unknown>

--- Thread ID: 30 ---
7D5FDB37 05BCEA68 0001:0001CB37 C:\windows\system32\winmm.dll
7BC707F4 05BCEA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 05BCEB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 05BCF398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 05BCF498 0000:00000000 <unknown>

--- Thread ID: 29 ---
7BC77603 0274E858 0001:00066603 C:\windows\system32\ntdll.dll
7BC778F3 0274E898 0001:000668F3 C:\windows\system32\ntdll.dll
7B86A376 0274E9E8 0001:00059376 C:\windows\system32\KERNEL32.dll
7B86A48C 0274EA18 0001:0005948C C:\windows\system32\KERNEL32.dll
007746A0 0274EA28 0001:003736A0 C:\Program Files\World of Warcraft\Wow.exe
0081C042 0274EA40 0001:0041B042 C:\Program Files\World of Warcraft\Wow.exe
0076FFCB 0274EA68 0001:0036EFCB C:\Program Files\World of Warcraft\Wow.exe
7BC707F4 0274EA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 0274EB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 0274F398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 0274F498 0000:00000000 <unknown>

--- Thread ID: 28 ---
7B86A501 0252E5F4 0001:00059501 C:\windows\system32\KERNEL32.dll
7B86A545 0252E614 0001:00059545 C:\windows\system32\KERNEL32.dll
0086B28D 0252E620 0001:0046A28D C:\Program Files\World of Warcraft\Wow.exe
004BA8BD 0252EA40 0001:000B98BD C:\Program Files\World of Warcraft\Wow.exe
0076FFCB 0252EA68 0001:0036EFCB C:\Program Files\World of Warcraft\Wow.exe
7BC707F4 0252EA78 0001:0005F7F4 C:\windows\system32\ntdll.dll
7BC709C0 0252EB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 0252F398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 0252F498 0000:00000000 <unknown>

--- Thread ID: 27 ---
7B86A501 01A2E9D4 0001:00059501 C:\windows\system32\KERNEL32.dll
7B86A545 01A2E9F4 0001:00059545 C:\windows\system32\KERNEL32.dll
00438935 01A2EA14 0001:00037935 C:\Program Files\World of Warcraft\Wow.exe
0044DF1A 01A2EA28 0001:0004CF1A C:\Program Files\World of Warcraft\Wow.exe
0088C5DF 01A2EA60 0001:0048B5DF C:\Program Files\World of Warcraft\Wow.exe
0088C684 01A2EA78 0001:0048B684 C:\Program Files\World of Warcraft\Wow.exe
7BC709C0 01A2EB48 0001:0005F9C0 C:\windows\system32\ntdll.dll
7BC79315 01A2F398 0001:00068315 C:\windows\system32\ntdll.dll
F761396E 01A2F498 0000:00000000 <unknown>

--- Thread ID: 9 [Current Thread] ---
7EBCDE1A 0192ED98 0000:00000000 <unknown>

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 19/19 threads...

--- Thread ID: 47 ---
7BC77603 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x0622E97C)
7BC778F3 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x00000000,0x10E59DA8)
7B86A376 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x00000000)
7B86A48C KERNEL32.dll WaitForSingleObject+60 (0x00002230,0x008E5190,0x7BC99FF4,0x008D2029)
008E4FA5 Wow.exe      <unknown symbol>+0 (0x10724E60,0x0622EA68,0x10724E60,0x0000002F)
008D2029 Wow.exe      <unknown symbol>+0 (0x10724E60,0x0000002F,0x7BC707F4,0x7FFBCF10)
008E51D0 Wow.exe      <unknown symbol>+0 (0x108EC724,0x0622EB48,0x008E5190,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x008E5190,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x008E5190,0x00000000,0x00000000,0x7FFBC1BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x0622FB70,0x0622F454,0x00000000)
F761396E              start_thread+190 (0x0622FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 45 ---
7BC77603 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x081FE9C8)
7BC778F3 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x081FEA48,0x00000000)
7BC7794C ntdll.dll    NtWaitForSingleObject+60 (0x000021DC,0x081FEA48,0x00111788,0x081FEB08)
7BC7CACF ntdll.dll    <unknown symbol>+0 (0x00000000,0x081FEB48,0x7BC7C990,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x7BC7C990,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x7BC7C990,0x00000000,0x00000000,0x7FF901BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FF90FB8,0x081FFB70,0x081FF454,0x00000000)
F761396E              start_thread+190 (0x081FFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 44 ---
7BC77603 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000003,0x00000004,0x00000000,0x00000000)
7BC778F3 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000003,0x00000000,0x00000000,0x00000000)
7B86A376 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000003,0x00000000,0x00000000,0x00000000)
7D38D02C winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+268 (0x00000003,0xFFFFFFFF,0x00000000,0x00000000)
7DD69FA8 user32.dll   <unknown symbol>+0 (0x00000003,0xFFFFFFFF,0x00000000,0x7BC99FF4)
7DD300DA user32.dll   MsgWaitForMultipleObjectsEx+250 (0x00000002,0xFFFFFFFF,0x00000000,0x0044CD87)
7DD3012F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x00000000,0x00000000,0x10E5B798)
0044CFA6 Wow.exe      <unknown symbol>+0 (0x00B339A0,0x10E5BFB0,0x0088C5DF,0x3FECE912)
0044DF1A Wow.exe      <unknown symbol>+0 (0x10E5B798,0x0088C605,0x7BC99FF4,0x0808EA34)
0088C5DF Wow.exe      <unknown symbol>+0 (0x7FF94F10,0x10E5BFB0,0x0808EB48,0x0088C605)
0088C684 Wow.exe      <unknown symbol>+0 (0x0088C605,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x0088C605,0x00000000,0x00000000,0x7FF941BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FF94FB8,0x0808FB70,0x0808F454,0x00000000)
F761396E              start_thread+190 (0x0808FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 43 ---
7BC77603 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x07F1E97C)
7BC778F3 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x00000000,0x00000000)
7B86A376 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x00000000)
7B86A48C KERNEL32.dll WaitForSingleObject+60 (0x000021F0,0x008E5190,0x7BC99FF4,0x008D2029)
008E4FA5 Wow.exe      <unknown symbol>+0 (0x10C4ABE8,0x07F1EA68,0x10C4ABE8,0x0000002B)
008D2029 Wow.exe      <unknown symbol>+0 (0x10C4ABE8,0x0000002B,0x7BC707F4,0x7FF98F10)
008E51D0 Wow.exe      <unknown symbol>+0 (0x10C4AA54,0x07F1EB48,0x008E5190,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x008E5190,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x008E5190,0x00000000,0x00000000,0x7FF981BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FF98FB8,0x07F1FB70,0x07F1F454,0x00000000)
F761396E              start_thread+190 (0x07F1FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 42 ---
7BC77603 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x07DAE9C8)
7BC778F3 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x07DAEA48,0x00000000)
7BC7794C ntdll.dll    NtWaitForSingleObject+60 (0x000021DC,0x07DAEA48,0x00111788,0x07DAEB08)
7BC7CACF ntdll.dll    <unknown symbol>+0 (0x00000000,0x07DAEB48,0x7BC7C990,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x7BC7C990,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x7BC7C990,0x00000000,0x00000000,0x7FF9C1BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FF9CFB8,0x07DAFB70,0x07DAF454,0x00000000)
F761396E              start_thread+190 (0x07DAFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 41 ---
7BC77603 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x07C3E9C8)
7BC778F3 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x07C3EA48,0x00000000)
7BC7794C ntdll.dll    NtWaitForSingleObject+60 (0x000021DC,0x07C3EA48,0x7DB0B280,0x07C3EB08)
7BC7CACF ntdll.dll    <unknown symbol>+0 (0x00000000,0x07C3EB48,0x7BC7C990,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x7BC7C990,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x7BC7C990,0x00000000,0x00000000,0x7FFA01BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFA0FB8,0x07C3FB70,0x07C3F454,0x00000000)
F761396E              start_thread+190 (0x07C3FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 40 ---
7BC77603 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000003,0x00000004,0x00000000,0x00000000)
7BC778F3 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000003,0x00000000,0x00000000,0x00000000)
7B86A376 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000003,0x00000000,0x00000000,0x00000000)
7D38D02C winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+268 (0x00000003,0xFFFFFFFF,0x00000000,0x00000000)
7DD69FA8 user32.dll   <unknown symbol>+0 (0x00000003,0xFFFFFFFF,0x00000000,0x7BC99FF4)
7DD300DA user32.dll   MsgWaitForMultipleObjectsEx+250 (0x00000002,0xFFFFFFFF,0x00000000,0x0044CD87)
7DD3012F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x00000000,0x00000000,0x105625B8)
0044CFA6 Wow.exe      <unknown symbol>+0 (0x00B33958,0x10562630,0x0088C5DF,0x309BE912)
0044DF1A Wow.exe      <unknown symbol>+0 (0x105625B8,0x0088C605,0x7BC99FF4,0x077FEA34)
0088C5DF Wow.exe      <unknown symbol>+0 (0x7FFA4F10,0x10562630,0x077FEB48,0x0088C605)
0088C684 Wow.exe      <unknown symbol>+0 (0x0088C605,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x0088C605,0x00000000,0x00000000,0x7FFA41BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFA4FB8,0x077FFB70,0x077FF454,0x00000000)
F761396E              start_thread+190 (0x077FFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 39 ---
7BC77603 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x7FFA8000)
7BC778F3 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x06D6E78C,0x00000000)
7B86A376 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x7B869C1A)
7B86A3EA KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x00000000,0x00000027,0x103178A8)
004699CB Wow.exe      <unknown symbol>+0 (0x1015AE20,0x0076FFCB,0x0076FF30,0x7BC99FF4)
0046906E Wow.exe      <unknown symbol>+0 (0x103178A8,0x7FFA8F10,0x000021B8,0x103178A8)
0076FFCB Wow.exe      <unknown symbol>+0 (0x00CAC860,0x06D6EB48,0x0076FF30,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x0076FF30,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x0076FF30,0x00000000,0x00000000,0x7FFA81BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x06D6FB70,0x06D6F454,0x00000000)
F761396E              start_thread+190 (0x06D6FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 38 ---
7BC77603 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x7BC6FE2E)
7BC778F3 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x06BFE9BC,0x7BC99FF4)
7B86A376 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x0086D6F1)
7B86A48C KERNEL32.dll WaitForSingleObject+60 (0x00002128,0x06BFEA34,0x000003E8,0x1015AE08)
007746A0 Wow.exe      <unknown symbol>+0 (0x000003E8,0x1015AE08,0x06BFEA40,0x00000000)
004691A5 Wow.exe      <unknown symbol>+0 (0x00000000,0x0076FFCB,0x0076FF30,0x7BC99FF4)
00469311 Wow.exe      <unknown symbol>+0 (0x103178B8,0x7FFACF10,0x000021B4,0x103178B8)
0076FFCB Wow.exe      <unknown symbol>+0 (0x00CAC840,0x06BFEB48,0x0076FF30,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x0076FF30,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x0076FF30,0x00000000,0x00000000,0x7FFAC1BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x06BFFB70,0x06BFF454,0x00000000)
F761396E              start_thread+190 (0x06BFFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 37 ---
7BC77603 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x00000000)
7BC778F3 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x00000000,0x00000001)
7B86A376 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x067DEA24)
7B86A48C KERNEL32.dll WaitForSingleObject+60 (0x0000207C,0x067DEA68,0xFFFFFFFF,0x0076FFCB)
007746A0 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x0076FFCB,0x0076FF30,0x7BC99FF4)
004F12CB Wow.exe      <unknown symbol>+0 (0x00CAC820,0x067DEB48,0x0076FF30,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x0076FF30,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x0076FF30,0x00000000,0x00000000,0x7FFB01BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x067DFB70,0x067DF454,0x00000000)
F761396E              start_thread+190 (0x067DFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 36 ---
7B86A501 KERNEL32.dll SleepEx+65 (0x0000000A,0x0650EA54,0x7B86A529,0x0650EA54)
7B86A545 KERNEL32.dll Sleep+37 (0x0000000A,0x008E520C,0x7FFB4F10,0x0650EA78)
008D1E8D Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000024,0x7BC707F4,0x7FFB4F10)
008E520C Wow.exe      <unknown symbol>+0 (0x0476CD70,0x0650EB48,0x008E5190,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x008E5190,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x008E5190,0x00000000,0x00000000,0x7FFB41BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x0650FB70,0x0650F454,0x00000000)
F761396E              start_thread+190 (0x0650FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 35 ---
7B86A501 KERNEL32.dll SleepEx+65 (0x0000000A,0x00000000,0x7B86A529,0x0639EA54)
7B86A545 KERNEL32.dll Sleep+37 (0x0000000A,0x008E520C,0x7FFB8F10,0x0639EA78)
008D1E8D Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000023,0x7BC707F4,0x7FFB8F10)
008E520C Wow.exe      <unknown symbol>+0 (0x04928438,0x0639EB48,0x008E5190,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x008E5190,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x008E5190,0x00000000,0x00000000,0x7FFB81BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x0639FB70,0x0639F454,0x00000000)
F761396E              start_thread+190 (0x0639FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 32 ---
7B86A501 KERNEL32.dll SleepEx+65 (0x0000000A,0x060BEA54,0x7B86A529,0x060BEA54)
7B86A545 KERNEL32.dll Sleep+37 (0x0000000A,0x008E520C,0x7FFC0F10,0x060BEA78)
008D1E8D Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000020,0x7BC707F4,0x7FFC0F10)
008E520C Wow.exe      <unknown symbol>+0 (0x04AE7020,0x060BEB48,0x008E5190,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x008E5190,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x008E5190,0x00000000,0x00000000,0x7FFC01BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFC0FB8,0x060BFB70,0x060BF454,0x00000000)
F761396E              start_thread+190 (0x060BFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 31 ---
7B86A501 KERNEL32.dll SleepEx+65 (0x0000000A,0x00000000,0x7B86A529,0x05F4EA54)
7B86A545 KERNEL32.dll Sleep+37 (0x0000000A,0x008E520C,0x7FFC4F10,0x05F4EA78)
008D1E8D Wow.exe      <unknown symbol>+0 (0x0000000A,0x0000001F,0x7BC707F4,0x7FFC4F10)
008E520C Wow.exe      <unknown symbol>+0 (0x0476EBF8,0x05F4EB48,0x008E5190,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x008E5190,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x008E5190,0x00000000,0x00000000,0x7FFC41BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFC4FB8,0x05F4FB70,0x05F4F454,0x00000000)
F761396E              start_thread+190 (0x05F4FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 30 ---
7D5FDB37 winmm.dll    <unknown symbol>+0 (0x00000000,0x05BCEB48,0x7D5FD960,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x7D5FD960,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x7D5FD960,0x00000000,0x00000000,0x7FFC81BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x05BCFB70,0x05BCF454,0x00000000)
F761396E              start_thread+190 (0x05BCFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 29 ---
7BC77603 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x7FFCC000)
7BC778F3 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x00000000,0x0274E9C8)
7B86A376 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x7B869C6A)
7B86A48C KERNEL32.dll WaitForSingleObject+60 (0x00002088,0x0274EA40,0xFFFFFFFF,0x0000001D)
007746A0 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x0000001D,0x0274EA68,0x00D3FCF0)
0081C042 Wow.exe      <unknown symbol>+0 (0x00D3FCF0,0x7FFCCF10,0x000020E8,0x00D3FCF0)
0076FFCB Wow.exe      <unknown symbol>+0 (0x00CAC800,0x0274EB48,0x0076FF30,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x0076FF30,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x0076FF30,0x00000000,0x00000000,0x7FFCC1BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x0274FB70,0x0274F454,0x00000000)
F761396E              start_thread+190 (0x0274FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 28 ---
7B86A501 KERNEL32.dll SleepEx+65 (0x00000001,0x0252E614,0x7B86A529,0x0252E620)
7B86A545 KERNEL32.dll Sleep+37 (0x00000001,0x004BA8BD,0x01CA65E0,0x000020E4)
0086B28D Wow.exe      <unknown symbol>+0 (0x00000001,0x0000001C,0x00000000,0x00000000)
004BA8BD Wow.exe      <unknown symbol>+0 (0x01CA65C0,0x7FFD0F10,0x000020E4,0x01CA65C0)
0076FFCB Wow.exe      <unknown symbol>+0 (0x00CAC7E0,0x0252EB48,0x0076FF30,0x7BC99FF4)
7BC707F4 ntdll.dll    call_thread_func+12 (0x0076FF30,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x0076FF30,0x00000000,0x00000000,0x7FFD01BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFD0FB8,0x0252FB70,0x0252F454,0x00000000)
F761396E              start_thread+190 (0x0252FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 27 ---
7B86A501 KERNEL32.dll SleepEx+65 (0x00000064,0x00000000,0x7B86A529,0x01A2EA14)
7B86A545 KERNEL32.dll Sleep+37 (0x00000064,0x7BC99FF4,0x00DCD9C9,0x01A2EA28)
00438935 Wow.exe      <unknown symbol>+0 (0x00000000,0x01071888,0x0088C5DF,0x3646E912)
0044DF1A Wow.exe      <unknown symbol>+0 (0x01071840,0x0088C605,0x7BC99FF4,0x01A2EA34)
0088C5DF Wow.exe      <unknown symbol>+0 (0x7FFD4F10,0x01071888,0x01A2EB48,0x0088C605)
0088C684 Wow.exe      <unknown symbol>+0 (0x0088C605,0x7BC99FF4,0xFFFFFFFF,0x7B837000)
7BC709C0 ntdll.dll    call_thread_entry_point+112 (0x0088C605,0x00000000,0x00000000,0x7FFD41BC)
7BC79315 ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x01A2FB70,0x01A2F454,0x00000000)
F761396E              start_thread+190 (0x01A2FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 9 [Current Thread] ---
7EBCDE1A              <unknown symbol>+0 (0x00000811,0x00000000,0x00000000,0x00000000)



----------------------------------------
    Loaded Modules
----------------------------------------

DBG-MODULE<00400000 009FD000 "Wow.exe" "Wow.pdb" 0 {8805d059-f6a3-4565-a646aa69736d4efe} 1 1277448958>
DBG-MODULE<10000000 00069000 "DivxDecoder.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 1076466304>
DBG-MODULE<79A30000 0004E000 "dbghelp.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7B810000 0012A000 "KERNEL32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7BC10000 000A6000 "ntdll.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7C060000 0005E000 "msvcrt.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7C760000 00012000 "psapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7C7A0000 00007000 "midimap.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7CA90000 00024000 "winealsa.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7CAC0000 0003C000 "dsound.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7CE40000 00009000 "msacm32.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D2B0000 0002B000 "uxtheme.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D360000 0008B000 "winex11.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D510000 00013000 "hid.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D530000 00029000 "winspool.drv" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D560000 00052000 "setupapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D5C0000 00018000 "msacm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D5E0000 0007F000 "winmm.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D680000 000DB000 "ole32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D760000 00034000 "dinput.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D7A0000 00020000 "ws2_32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D7D0000 000BE000 "comctl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7D8A0000 00182000 "shell32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DA30000 00051000 "shlwapi.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DA90000 00014000 "mpr.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DAC0000 00018000 "dinput8.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DAE0000 00051000 "wininet.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DB40000 00012000 "imm32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DB60000 00006000 "lz32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DB70000 00067000 "rpcrt4.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DBE0000 00050000 "advapi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DC40000 0007A000 "gdi32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7DCD0000 000F9000 "user32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7ED80000 00014000 "version.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>
DBG-MODULE<7EDB0000 0008B000 "opengl32.dll" "" 0 {00000000-0000-0000-0000000000000000} 0 0>

----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 7EBCDE1A)

7EBCDE1A: F6 83 2C 01  00 00 02 0F  85 DA 03 00  00 8B 6C 24  ..,...........l$


Stack: 1024 bytes starting at (ESP = 0192ECA0)

* = addr  **                                                  *               
0192ECA0: 67 5C 5E F7  F8 A3 60 F7  53 5B 5E F7  41 5E 5E F7  g\^...`.S[^.A^^.
0192ECB0: C8 EC 92 01  18 00 00 00  01 00 00 00  08 00 00 00  ................
0192ECC0: C0 A3 60 F7  20 00 00 00  F0 A3 60 F7  F4 8F 60 F7  ..`. .....`...`.
0192ECD0: C0 A3 60 F7  00 00 00 00  21 00 00 00  6C 3C 52 F7  ..`.....!...l<R.
0192ECE0: C0 A3 60 F7  F4 8F 60 00  00 00 00 00  00 00 00 00  ..`...`.........
0192ECF0: 00 00 92 01  9D 3B 52 F7  18 ED 92 01  00 00 00 00  .....;R.........
0192ED00: 00 00 00 00  D9 4B 58 F7  F4 8F 60 F7  00 D0 A7 00  .....KX...`.....
0192ED10: 30 4C 2F 7D  B4 00 00 00  00 00 00 00  08 03 00 00  0L/}............
0192ED20: B4 00 00 00  00 00 00 00  98 ED 92 01  78 66 BD 7E  ............xf.~
0192ED30: A0 95 51 7C  00 00 00 00  00 00 00 00  98 ED 92 01  ..Q|............
0192ED40: 18 D9 A7 79  00 00 00 00  00 00 00 00  F4 D9 B9 04  ...y............
0192ED50: 8F BD 94 00  18 D9 A7 79  00 00 00 00  3C 00 00 00  .......y....<...
0192ED60: 02 00 00 00  00 00 00 00  00 00 00 00  A0 F0 92 01  ................
0192ED70: 10 00 E0 0E  98 ED 92 01  78 A7 68 7C  2A B8 BF 7E  ........x.h|*..~
0192ED80: A0 95 51 7C  A0 F0 92 01  08 03 00 00  E0 1B 54 7C  ..Q|..........T|
0192ED90: 00 00 00 00  D4 ED 92 01  01 00 00 00  B4 00 00 00  ................
0192EDA0: 11 08 00 00  23 00 00 00  00 00 00 00  00 00 00 00  ....#...........
0192EDB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EDC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EDD0: FF FF FF FF  FF FF FF FF  FF FF FF FF  00 00 00 00  ................
0192EDE0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EDF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EE00: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EE10: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EE20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EE30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EE40: FF FF FF FF  FF FF FF FF  00 00 00 00  00 00 00 00  ................
0192EE50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EE60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EE70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EE80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EE90: 08 00 00 00  08 00 00 00  08 00 00 00  00 00 00 00  ................
0192EEA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EEB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EEC0: 36 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  6...............
0192EED0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EEE0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EEF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EF00: FF FF FF FF  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EF10: 08 00 00 00  08 00 00 00  00 00 00 00  00 00 00 00  ................
0192EF20: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EF30: 00 00 00 00  00 00 00 00  FF FF FF FF  FF FF FF FF  ................
0192EF40: FF FF FF FF  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EF50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EF60: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EF70: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EF80: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EF90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EFA0: 00 00 00 00  00 00 00 00  FF FF FF FF  FF FF FF FF  ................
0192EFB0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EFC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EFD0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EFE0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192EFF0: 00 00 00 00  00 00 00 00  08 00 00 00  08 00 00 00  ................
0192F000: 08 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192F010: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192F020: 00 00 00 00  00 00 00 00  36 00 00 00  00 00 00 00  ........6.......
0192F030: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192F040: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192F050: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192F060: 00 00 00 00  00 00 00 00  FF FF FF FF  00 00 00 00  ................
0192F070: 00 00 00 00  00 00 00 00  08 00 00 00  08 00 00 00  ................
0192F080: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0192F090: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0xf
Number of Processors:   4
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3851
Os Version:             5.1
Os Service Pack:        3.0

Percent memory used:    20
Total physical memory:  4156592127
Free Memory:            3284041727
Page file:              4156592128
```

---

### Post by zmoky on 2010-08-31
fixed that by installing the linux drivers from nvidia.com but the result is just awful

World of Warcraft works very slowly comparing to windows 7 on ubuntu on a quad core 4gb ddr2 and 2x8800Gt SLI .... is just purely awful

I think I will stick to windows when playing WOW

---

### Post by zmoky on 2011-05-22
it works great now having:

wine-1.3.18
NVIDIA-Linux-x86_64-270.41.06
on Ubuntu 10.04 & 11.04

:)

---

