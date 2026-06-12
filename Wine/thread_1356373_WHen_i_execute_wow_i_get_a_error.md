---
title: "WHen i execute wow i get a error"
date: 2009-12-16
forum: Wine
---

### Post by LordAllucard on 2009-12-16
Hi im new in this community and using wow and my english is really limited,
im a world of warcraft lover is my fav mmorpg but my hard drive doesnt work on windows format either in ext 2 , ext 3 , jfs or any linux format it only work on ext 4 i dont know why and im using xubuntu karmic koala my laptop is a acer aspire 5050 and i has a video card but ati doesnt support it anymore [ ATi XPRESS 1100 ] but i found a tutorial online and i got 3D acceleration soo i think that the software is ok cuz i can also play openarena and enemy territory but when i run wow i can only heard the sound but not the game i get this using the console i get this:

fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x3aed40,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3aea54,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af244,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af384,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af51c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3aef9c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af0d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af4a4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af494,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3aef9c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af0d4,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x158ab8,0x1589b8): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x3af7a0): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x3af7a0): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x3ade80,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adeb8,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37404484) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

and when i close the game this appear:
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 681 requests (681 known processed) with 0 events remaining.
 

but a windows appear showing this

[http://www.gameagon.com/crash1.JPG](http://www.gameagon.com/crash1.JPG) ( sorry i dont know how to screen shots cuz im using fluxbox as desktop enviorement and i found this pictures online is the same error as mine ) 

and this too:

==============================================================================
World of WarCraft (build 9947)

Exe:      Z:\home\mich\Desktop\wow\Wow -opengl.exe
Time:     Dec 16, 2009  1:53:43.944 AM
User:     mich
Computer: mich-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:    Z:\home\mich\Desktop\wow\Wow -opengl.exe
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0073:BF7FFFFF

The instruction at "0xBF7FFFFF" referenced memory at "0xBF7FFFFF".
The memory could not be "read".


WoWBuild: 9947
Settings: 
SET realmList "rtkgaming.com"
SET coresDetected "1"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET M2UseShaders "0"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "2"
SET textureFilteringMode "0"
SET movie "0"
SET Gamma "0.900000"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "40"
SET particleDensity "0.10000000149012"
SET environmentDetail "0.1"
SET weatherDensity "0"
SET mouseSpeed "1.2000000476837"
SET accounttype "LK"
SET realmName "RTK - Aftermath"
SET baseMip "1"
SET locale "enUS"
SET gxVSync "0"
SET horizonfarclip "1305"
SET showfootprints "0"
SET groundEffectDist "0"
SET hwPCF "0"
SET shadowLOD "0"
SET ffx "0"
SET showfootprintparticles "0"
SET checkAddonVersion "0"
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000001  EBX=0849F7CC  ECX=00000004  EDX=00000001  ESI=0849F7B8
EDI=02B337A8  EBP=003AF858  ESP=003AF840  EIP=BF7FFFFF  FLG=00210202
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 16/16 threads...

--- Thread ID: 41 ---
7BC74043 0B05E868 0001:00063043 C:\windows\system32\ntdll.dll
7BC74333 0B05E8A8 0001:00063333 C:\windows\system32\ntdll.dll
7B88D676 0B05E9F8 0001:0006C676 C:\windows\system32\KERNEL32.dll
7B88D78C 0B05EA28 0001:0006C78C C:\windows\system32\KERNEL32.dll
00895FF5 0B05EA44 0001:00494FF5 Z:\home\mich\Desktop\wow\Wow -opengl.exe
0085547A 0B05EA54 0001:0045447A Z:\home\mich\Desktop\wow\Wow -opengl.exe
00855AD0 0B05EA68 0001:00454AD0 Z:\home\mich\Desktop\wow\Wow -opengl.exe
7BC6D514 0B05EA78 0001:0005C514 C:\windows\system32\ntdll.dll
7BC6D6E0 0B05EB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 0B05F398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 0B05F498 0000:00000000 <unknown>

--- Thread ID: 39 ---
7BC74043 0AB5E988 0001:00063043 C:\windows\system32\ntdll.dll
7BC74333 0AB5E9C8 0001:00063333 C:\windows\system32\ntdll.dll
7BC7438C 0AB5E9F8 0001:0006338C C:\windows\system32\ntdll.dll
7BC795AF 0AB5EA68 0001:000685AF C:\windows\system32\ntdll.dll
7BC6D514 0AB5EA78 0001:0005C514 C:\windows\system32\ntdll.dll
7BC6D6E0 0AB5EB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 0AB5F398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 0AB5F498 0000:00000000 <unknown>

--- Thread ID: 38 ---
7BC74043 0A9EE614 0001:00063043 C:\windows\system32\ntdll.dll
7BC74333 0A9EE654 0001:00063333 C:\windows\system32\ntdll.dll
7B88D676 0A9EE7A4 0001:0006C676 C:\windows\system32\KERNEL32.dll
68C0191C 0A9EE7E4 0001:0003091C C:\windows\system32\winex11.drv
6825E1FA 0A9EE9B4 0001:0006D1FA C:\windows\system32\user32.dll
6825E26F 0A9EE9E4 0001:0006D26F C:\windows\system32\user32.dll
004415D9 0A9EEA14 0001:000405D9 Z:\home\mich\Desktop\wow\Wow -opengl.exe
004425DA 0A9EEA28 0001:000415DA Z:\home\mich\Desktop\wow\Wow -opengl.exe
008D967F 0A9EEA60 0001:004D867F Z:\home\mich\Desktop\wow\Wow -opengl.exe
008D9724 0A9EEA78 0001:004D8724 Z:\home\mich\Desktop\wow\Wow -opengl.exe
7BC6D6E0 0A9EEB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 0A9EF398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 0A9EF498 0000:00000000 <unknown>

--- Thread ID: 37 ---
7BC74043 0A87E868 0001:00063043 C:\windows\system32\ntdll.dll
7BC74333 0A87E8A8 0001:00063333 C:\windows\system32\ntdll.dll
7B88D676 0A87E9F8 0001:0006C676 C:\windows\system32\KERNEL32.dll
7B88D78C 0A87EA28 0001:0006C78C C:\windows\system32\KERNEL32.dll
00895FF5 0A87EA44 0001:00494FF5 Z:\home\mich\Desktop\wow\Wow -opengl.exe
0085547A 0A87EA54 0001:0045447A Z:\home\mich\Desktop\wow\Wow -opengl.exe
00855AD0 0A87EA68 0001:00454AD0 Z:\home\mich\Desktop\wow\Wow -opengl.exe
7BC6D514 0A87EA78 0001:0005C514 C:\windows\system32\ntdll.dll
7BC6D6E0 0A87EB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 0A87F398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 0A87F498 0000:00000000 <unknown>

--- Thread ID: 36 ---
7BC74043 0A70E988 0001:00063043 C:\windows\system32\ntdll.dll
7BC74333 0A70E9C8 0001:00063333 C:\windows\system32\ntdll.dll
7BC7438C 0A70E9F8 0001:0006338C C:\windows\system32\ntdll.dll
7BC795AF 0A70EA68 0001:000685AF C:\windows\system32\ntdll.dll
7BC6D514 0A70EA78 0001:0005C514 C:\windows\system32\ntdll.dll
7BC6D6E0 0A70EB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 0A70F398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 0A70F498 0000:00000000 <unknown>

--- Thread ID: 35 ---
7BC74043 080AE614 0001:00063043 C:\windows\system32\ntdll.dll
7BC74333 080AE654 0001:00063333 C:\windows\system32\ntdll.dll
7B88D676 080AE7A4 0001:0006C676 C:\windows\system32\KERNEL32.dll
68C0191C 080AE7E4 0001:0003091C C:\windows\system32\winex11.drv
6825E1FA 080AE9B4 0001:0006D1FA C:\windows\system32\user32.dll
6825E26F 080AE9E4 0001:0006D26F C:\windows\system32\user32.dll
004415D9 080AEA14 0001:000405D9 Z:\home\mich\Desktop\wow\Wow -opengl.exe
004425DA 080AEA28 0001:000415DA Z:\home\mich\Desktop\wow\Wow -opengl.exe
008D967F 080AEA60 0001:004D867F Z:\home\mich\Desktop\wow\Wow -opengl.exe
008D9724 080AEA78 0001:004D8724 Z:\home\mich\Desktop\wow\Wow -opengl.exe
7BC6D6E0 080AEB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 080AF398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 080AF498 0000:00000000 <unknown>

--- Thread ID: 34 ---
7BC74043 0703E628 0001:00063043 C:\windows\system32\ntdll.dll
7BC74333 0703E668 0001:00063333 C:\windows\system32\ntdll.dll
7B88D676 0703E7B8 0001:0006C676 C:\windows\system32\KERNEL32.dll
7B88D6EA 0703E7E8 0001:0006C6EA C:\windows\system32\KERNEL32.dll
0046293B 0703EA40 0001:0006193B Z:\home\mich\Desktop\wow\Wow -opengl.exe
004620CE 0703EA4C 0001:000610CE Z:\home\mich\Desktop\wow\Wow -opengl.exe
0053BBE7 0703EA68 0001:0013ABE7 Z:\home\mich\Desktop\wow\Wow -opengl.exe
7BC6D514 0703EA78 0001:0005C514 C:\windows\system32\ntdll.dll
7BC6D6E0 0703EB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 0703F398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 0703F498 0000:00000000 <unknown>

--- Thread ID: 33 ---
7BC74043 06ECE858 0001:00063043 C:\windows\system32\ntdll.dll
7BC74333 06ECE898 0001:00063333 C:\windows\system32\ntdll.dll
7B88D676 06ECE9E8 0001:0006C676 C:\windows\system32\KERNEL32.dll
7B88D78C 06ECEA18 0001:0006C78C C:\windows\system32\KERNEL32.dll
00540210 06ECEA28 0001:0013F210 Z:\home\mich\Desktop\wow\Wow -opengl.exe
00462125 06ECEA40 0001:00061125 Z:\home\mich\Desktop\wow\Wow -opengl.exe
00462291 06ECEA4C 0001:00061291 Z:\home\mich\Desktop\wow\Wow -opengl.exe
0053BBE7 06ECEA68 0001:0013ABE7 Z:\home\mich\Desktop\wow\Wow -opengl.exe
7BC6D514 06ECEA78 0001:0005C514 C:\windows\system32\ntdll.dll
7BC6D6E0 06ECEB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 06ECF398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 06ECF498 0000:00000000 <unknown>

--- Thread ID: 32 ---
7B88D801 06D5EA28 0001:0006C801 C:\windows\system32\KERNEL32.dll
7B88D845 06D5EA48 0001:0006C845 C:\windows\system32\KERNEL32.dll
008552DD 06D5EA54 0001:004542DD Z:\home\mich\Desktop\wow\Wow -opengl.exe
00855B0C 06D5EA68 0001:00454B0C Z:\home\mich\Desktop\wow\Wow -opengl.exe
7BC6D514 06D5EA78 0001:0005C514 C:\windows\system32\ntdll.dll
7BC6D6E0 06D5EB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 06D5F398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 06D5F498 0000:00000000 <unknown>

--- Thread ID: 31 ---
7B88D801 06BEEA28 0001:0006C801 C:\windows\system32\KERNEL32.dll
7B88D845 06BEEA48 0001:0006C845 C:\windows\system32\KERNEL32.dll
008552DD 06BEEA54 0001:004542DD Z:\home\mich\Desktop\wow\Wow -opengl.exe
00855B0C 06BEEA68 0001:00454B0C Z:\home\mich\Desktop\wow\Wow -opengl.exe
7BC6D514 06BEEA78 0001:0005C514 C:\windows\system32\ntdll.dll
7BC6D6E0 06BEEB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 06BEF398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 06BEF498 0000:00000000 <unknown>

--- Thread ID: 30 ---
7B88D801 06A7EA28 0001:0006C801 C:\windows\system32\KERNEL32.dll
7B88D845 06A7EA48 0001:0006C845 C:\windows\system32\KERNEL32.dll
008552DD 06A7EA54 0001:004542DD Z:\home\mich\Desktop\wow\Wow -opengl.exe
00855B0C 06A7EA68 0001:00454B0C Z:\home\mich\Desktop\wow\Wow -opengl.exe
7BC6D514 06A7EA78 0001:0005C514 C:\windows\system32\ntdll.dll
7BC6D6E0 06A7EB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 06A7F398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 06A7F498 0000:00000000 <unknown>

--- Thread ID: 29 ---
7B88D801 0690EA28 0001:0006C801 C:\windows\system32\KERNEL32.dll
7B88D845 0690EA48 0001:0006C845 C:\windows\system32\KERNEL32.dll
008552DD 0690EA54 0001:004542DD Z:\home\mich\Desktop\wow\Wow -opengl.exe
00855B0C 0690EA68 0001:00454B0C Z:\home\mich\Desktop\wow\Wow -opengl.exe
7BC6D514 0690EA78 0001:0005C514 C:\windows\system32\ntdll.dll
7BC6D6E0 0690EB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 0690F398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 0690F498 0000:00000000 <unknown>

--- Thread ID: 28 ---
6D008637 0679EA68 0001:00017637 C:\windows\system32\winmm.dll
7BC6D514 0679EA78 0001:0005C514 C:\windows\system32\ntdll.dll
7BC6D6E0 0679EB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 0679F398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 0679F498 0000:00000000 <unknown>

--- Thread ID: 27 ---
7B88D801 0308E600 0001:0006C801 C:\windows\system32\KERNEL32.dll
7B88D845 0308E620 0001:0006C845 C:\windows\system32\KERNEL32.dll
0046E92D 0308E62C 0001:0006D92D Z:\home\mich\Desktop\wow\Wow -opengl.exe
007DAAD5 0308EA4C 0001:003D9AD5 Z:\home\mich\Desktop\wow\Wow -opengl.exe
0053BBE7 0308EA68 0001:0013ABE7 Z:\home\mich\Desktop\wow\Wow -opengl.exe
7BC6D514 0308EA78 0001:0005C514 C:\windows\system32\ntdll.dll
7BC6D6E0 0308EB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 0308F398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 0308F498 0000:00000000 <unknown>

--- Thread ID: 26 ---
7B88D801 01CCE9E0 0001:0006C801 C:\windows\system32\KERNEL32.dll
7B88D845 01CCEA00 0001:0006C845 C:\windows\system32\KERNEL32.dll
004245E4 01CCEA28 0001:000235E4 Z:\home\mich\Desktop\wow\Wow -opengl.exe
008D967F 01CCEA60 0001:004D867F Z:\home\mich\Desktop\wow\Wow -opengl.exe
008D9724 01CCEA78 0001:004D8724 Z:\home\mich\Desktop\wow\Wow -opengl.exe
7BC6D6E0 01CCEB48 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC75C35 01CCF398 0001:00064C35 C:\windows\system32\ntdll.dll
6815D80E 01CCF498 0000:00000000 <unknown>

--- Thread ID: 9 [Current Thread] ---
BF7FFFFF 003AF858 0000:00000000 <unknown>
00624F18 003AF878 0001:00223F18 Z:\home\mich\Desktop\wow\Wow -opengl.exe
00478CA2 003AF8AC 0001:00077CA2 Z:\home\mich\Desktop\wow\Wow -opengl.exe
00483A42 003AF8D4 0001:00082A42 Z:\home\mich\Desktop\wow\Wow -opengl.exe
00486AF8 003AF9A8 0001:00085AF8 Z:\home\mich\Desktop\wow\Wow -opengl.exe
00486D75 003AFA78 0001:00085D75 Z:\home\mich\Desktop\wow\Wow -opengl.exe
007FEC01 003AFB50 0001:003FDC01 Z:\home\mich\Desktop\wow\Wow -opengl.exe
007BC180 003AFB7C 0001:003BB180 Z:\home\mich\Desktop\wow\Wow -opengl.exe
007F996A 003AFC3C 0001:003F896A Z:\home\mich\Desktop\wow\Wow -opengl.exe
008158A7 003AFC58 0001:004148A7 Z:\home\mich\Desktop\wow\Wow -opengl.exe
00815D9B 003AFC74 0001:00414D9B Z:\home\mich\Desktop\wow\Wow -opengl.exe
007E953C 003AFD40 0001:003E853C Z:\home\mich\Desktop\wow\Wow -opengl.exe
008356B9 003AFD70 0001:004346B9 Z:\home\mich\Desktop\wow\Wow -opengl.exe
00833E2F 003AFDF4 0001:00432E2F Z:\home\mich\Desktop\wow\Wow -opengl.exe
00833F11 003AFE0C 0001:00432F11 Z:\home\mich\Desktop\wow\Wow -opengl.exe
00406C7D 003AFEA8 0001:00005C7D Z:\home\mich\Desktop\wow\Wow -opengl.exe
7B8774D4 003AFEE8 0001:000564D4 C:\windows\system32\KERNEL32.dll
7BC6D514 003AFEF8 0001:0005C514 C:\windows\system32\ntdll.dll
7BC6D6E0 003AFFC8 0001:0005C6E0 C:\windows\system32\ntdll.dll
7BC49D7A 003AFFE8 0001:00038D7A C:\windows\system32\ntdll.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 16/16 threads...

--- Thread ID: 41 ---
7BC74043 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x0B05E8D8,0x00000004,0x00000000)
7BC74333 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x0B05E8D8,0x00000000,0x00000000)
7B88D676 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x0B05EA30,0x00000000,0xFFFFFFFF)
7B88D78C KERNEL32.dll WaitForSingleObject+60 (0x00002224,0xFFFFFFFF,0x00855A90,0x081B44DC)
00895FF5 Wow -opengl.exe <unknown symbol>+0 (0x081F1278,0xFFFFFFFF,0x0B05EA68,0x00855AD0)
0085547A Wow -opengl.exe <unknown symbol>+0 (0x081F1278,0x7FF98F10,0x00000029,0x0B05EA7
00855AD0 Wow -opengl.exe <unknown symbol>+0 (0x081B44DC,0x7FF98F10,0x0B05EB48,0x7BC6D6E0)
7BC6D514 ntdll.dll    call_thread_func+12 (0x00855A90,0x081B44DC,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x00855A90,0x081B44DC,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FF98FB8,0x0B05FB70,0x0B05FB70,0x0B05FB70)
6815D80E              start_thread+190 (0x0B05FB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 39 ---
7BC74043 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x0AB5EA00,0x00000004,0x0AB5EA4
7BC74333 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x0AB5EA00,0x00000000,0x00000000)
7BC7438C ntdll.dll    NtWaitForSingleObject+60 (0x000021D4,0x00000000,0x0AB5EA48,0x7BC97FF4)
7BC795AF ntdll.dll    <unknown symbol>+0 (0x00000000,0x7FFA0F10,0x0AB5EB48,0x7BC6D6E0)
7BC6D514 ntdll.dll    call_thread_func+12 (0x7BC79470,0x00000000,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x7BC79470,0x00000000,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFA0FB8,0x0AB5FB70,0x0AB5FB70,0x0AB5FB70)
6815D80E              start_thread+190 (0x0AB5FB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 38 ---
7BC74043 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000003,0x0A9EE684,0x00000004,0x00000000)
7BC74333 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000003,0x0A9EE684,0x00000000,0x00000000)
7B88D676 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000003,0x0A9EE828,0x00000000,0xFFFFFFFF)
68C0191C winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+268 (0x00000003,0x0A9EE828,0xFFFFFFFF,0x00000000)
6825E1FA user32.dll   MsgWaitForMultipleObjectsEx+282 (0x00000002,0x0A9EEA0C,0xFFFFFFFF,0x00000000)
6825E26F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x0A9EEA0C,0x00000000,0xFFFFFFFF)
004415D9 Wow -opengl.exe <unknown symbol>+0 (0x0106A218,0x008D96A5,0x080D2748,0x0A9EEA60)
004425DA Wow -opengl.exe <unknown symbol>+0 (0x0848F048,0x1C93A0C6,0x008D96A5,0x080D274
008D967F Wow -opengl.exe <unknown symbol>+0 (0x7FFA4F10,0x7BC6D514,0x080D2748,0x7FFA4F10)
008D9724 Wow -opengl.exe <unknown symbol>+0 (0x008D96A5,0x080D2748,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x008D96A5,0x080D2748,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFA4FB8,0x0A9EFB70,0x0A9EFB70,0x0A9EFB70)
6815D80E              start_thread+190 (0x0A9EFB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 37 ---
7BC74043 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x0A87E8D8,0x00000004,0x00000000)
7BC74333 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x0A87E8D8,0x00000000,0x00000000)
7B88D676 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x0A87EA30,0x00000000,0xFFFFFFFF)
7B88D78C KERNEL32.dll WaitForSingleObject+60 (0x000021D8,0xFFFFFFFF,0x00855A90,0x0848C7E4)
00895FF5 Wow -opengl.exe <unknown symbol>+0 (0x0848C0C8,0xFFFFFFFF,0x0A87EA68,0x00855AD0)
0085547A Wow -opengl.exe <unknown symbol>+0 (0x0848C0C8,0x7FFA8F10,0x00000025,0x0A87EA78)
00855AD0 Wow -opengl.exe <unknown symbol>+0 (0x0848C7E4,0x7FFA8F10,0x0A87EB48,0x7BC6D6E0)
7BC6D514 ntdll.dll    call_thread_func+12 (0x00855A90,0x0848C7E4,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x00855A90,0x0848C7E4,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x0A87FB70,0x0A87FB70,0x0A87FB70)
6815D80E              start_thread+190 (0x0A87FB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 36 ---
7BC74043 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x0A70EA00,0x00000004,0x0A70EA4
7BC74333 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x0A70EA00,0x00000000,0x00000000)
7BC7438C ntdll.dll    NtWaitForSingleObject+60 (0x000021D4,0x00000000,0x0A70EA48,0x7BC93B1B)
7BC795AF ntdll.dll    <unknown symbol>+0 (0x00000000,0x7FFACF10,0x0A70EB48,0x7BC6D6E0)
7BC6D514 ntdll.dll    call_thread_func+12 (0x7BC79470,0x00000000,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x7BC79470,0x00000000,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x0A70FB70,0x0A70FB70,0x0A70FB70)
6815D80E              start_thread+190 (0x0A70FB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 35 ---
7BC74043 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000003,0x080AE684,0x00000004,0x00000000)
7BC74333 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000003,0x080AE684,0x00000000,0x00000000)
7B88D676 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000003,0x080AE828,0x00000000,0xFFFFFFFF)
68C0191C winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+268 (0x00000003,0x080AE828,0xFFFFFFFF,0x00000000)
6825E1FA user32.dll   MsgWaitForMultipleObjectsEx+282 (0x00000002,0x080AEA0C,0xFFFFFFFF,0x00000000)
6825E26F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x080AEA0C,0x00000000,0xFFFFFFFF)
004415D9 Wow -opengl.exe <unknown symbol>+0 (0x0106A1D0,0x008D96A5,0x06410600,0x080AEA60)
004425DA Wow -opengl.exe <unknown symbol>+0 (0x064105A0,0x1E07A0C6,0x008D96A5,0x06410600)
008D967F Wow -opengl.exe <unknown symbol>+0 (0x7FFB0F10,0x7BC6D514,0x06410600,0x7FFB0F10)
008D9724 Wow -opengl.exe <unknown symbol>+0 (0x008D96A5,0x06410600,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x008D96A5,0x06410600,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x080AFB70,0x080AFB70,0x080AFB70)
6815D80E              start_thread+190 (0x080AFB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 34 ---
7BC74043 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x0703E698,0x00000004,0x0703E798)
7BC74333 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x0703E698,0x00000000,0x00000000)
7B88D676 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x0703E90C,0x00000000,0x000001F4)
7B88D6EA KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x0703E90C,0x00000000,0x000001F4)
0046293B Wow -opengl.exe <unknown symbol>+0 (0x004620C0,0x0703EA68,0x0053BBE7,0x05DD983
004620CE Wow -opengl.exe <unknown symbol>+0 (0x05DD9838,0x0053BB90,0x7FFB4F10,0x7BC97FF4)
0053BBE7 Wow -opengl.exe <unknown symbol>+0 (0x000021B0,0x7FFB4F10,0x0703EB48,0x7BC6D6E0)
7BC6D514 ntdll.dll    call_thread_func+12 (0x0053BB90,0x05D729C0,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x0053BB90,0x05D729C0,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x0703FB70,0x0703FB70,0x0703FB70)
6815D80E              start_thread+190 (0x0703FB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 33 ---
7BC74043 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x06ECE8C8,0x00000004,0x06ECE9C
7BC74333 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x06ECE8C8,0x00000000,0x00000000)
7B88D676 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x06ECEA20,0x00000000,0x000003E
7B88D78C KERNEL32.dll WaitForSingleObject+60 (0x00002120,0x000003E8,0x06ECEA40,0x00462125)
00540210 Wow -opengl.exe <unknown symbol>+0 (0x000003E8,0x00000021,0x00462280,0x05DD984
00462125 Wow -opengl.exe <unknown symbol>+0 (0x00000000,0x06ECEA68,0x0053BBE7,0x05DD984
00462291 Wow -opengl.exe <unknown symbol>+0 (0x05DD9848,0x0053BB90,0x7FFB8F10,0x7BC97FF4)
0053BBE7 Wow -opengl.exe <unknown symbol>+0 (0x000021AC,0x7FFB8F10,0x06ECEB48,0x7BC6D6E0)
7BC6D514 ntdll.dll    call_thread_func+12 (0x0053BB90,0x05D729A8,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x0053BB90,0x05D729A8,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x06ECFB70,0x06ECFB70,0x06ECFB70)
6815D80E              start_thread+190 (0x06ECFB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 32 ---
7B88D801 KERNEL32.dll SleepEx+65 (0x0000000A,0x00000000,0x06D5EA54,0x00842D8A)
7B88D845 KERNEL32.dll Sleep+37 (0x0000000A,0x06D5EA68,0x00855B0C,0x0000000A)
008552DD Wow -opengl.exe <unknown symbol>+0 (0x0000000A,0x7FFBCF10,0x00000020,0x06D5EA7
00855B0C Wow -opengl.exe <unknown symbol>+0 (0x03E6B3D8,0x7FFBCF10,0x06D5EB48,0x7BC6D6E0)
7BC6D514 ntdll.dll    call_thread_func+12 (0x00855A90,0x03E6B3D8,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x00855A90,0x03E6B3D8,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x06D5FB70,0x06D5FB70,0x06D5FB70)
6815D80E              start_thread+190 (0x06D5FB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 31 ---
7B88D801 KERNEL32.dll SleepEx+65 (0x0000000A,0x00000000,0x00000000,0x0000000A)
7B88D845 KERNEL32.dll Sleep+37 (0x0000000A,0x06BEEA68,0x00855B0C,0x0000000A)
008552DD Wow -opengl.exe <unknown symbol>+0 (0x0000000A,0x7FFC0F10,0x0000001F,0x06BEEA7
00855B0C Wow -opengl.exe <unknown symbol>+0 (0x03CAAAA8,0x7FFC0F10,0x06BEEB48,0x7BC6D6E0)
7BC6D514 ntdll.dll    call_thread_func+12 (0x00855A90,0x03CAAAA8,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x00855A90,0x03CAAAA8,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFC0FB8,0x06BEFB70,0x06BEFB70,0x06BEFB70)
6815D80E              start_thread+190 (0x06BEFB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 30 ---
7B88D801 KERNEL32.dll SleepEx+65 (0x0000000A,0x00000000,0x06A7EA54,0x00842D8A)
7B88D845 KERNEL32.dll Sleep+37 (0x0000000A,0x06A7EA68,0x00855B0C,0x0000000A)
008552DD Wow -opengl.exe <unknown symbol>+0 (0x0000000A,0x7FFC4F10,0x0000001E,0x06A7EA7
00855B0C Wow -opengl.exe <unknown symbol>+0 (0x0558FFE8,0x7FFC4F10,0x06A7EB48,0x7BC6D6E0)
7BC6D514 ntdll.dll    call_thread_func+12 (0x00855A90,0x0558FFE8,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x00855A90,0x0558FFE8,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFC4FB8,0x06A7FB70,0x06A7FB70,0x06A7FB70)
6815D80E              start_thread+190 (0x06A7FB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 29 ---
7B88D801 KERNEL32.dll SleepEx+65 (0x0000000A,0x00000000,0x00000000,0x0000000E)
7B88D845 KERNEL32.dll Sleep+37 (0x0000000A,0x0690EA68,0x00855B0C,0x0000000A)
008552DD Wow -opengl.exe <unknown symbol>+0 (0x0000000A,0x7FFC8F10,0x0000001D,0x0690EA7
00855B0C Wow -opengl.exe <unknown symbol>+0 (0x03C234F8,0x7FFC8F10,0x0690EB48,0x7BC6D6E0)
7BC6D514 ntdll.dll    call_thread_func+12 (0x00855A90,0x03C234F8,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x00855A90,0x03C234F8,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x0690FB70,0x0690FB70,0x0690FB70)
6815D80E              start_thread+190 (0x0690FB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 28 ---
6D008637 winmm.dll    <unknown symbol>+0 (0x00000000,0x7FFCCF10,0x0679EB48,0x7BC6D6E0)
7BC6D514 ntdll.dll    call_thread_func+12 (0x6D008460,0x00000000,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x6D008460,0x00000000,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x0679FB70,0x0679FB70,0x0679FB70)
6815D80E              start_thread+190 (0x0679FB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 27 ---
7B88D801 KERNEL32.dll SleepEx+65 (0x00000001,0x00000000,0x0000001B,0x7B88D759)
7B88D845 KERNEL32.dll Sleep+37 (0x00000001,0x0308EA4C,0x007DAAD5,0x00000001)
0046E92D Wow -opengl.exe <unknown symbol>+0 (0x00000001,0x007DA900,0x02B3F438,0x0000001B)
007DAAD5 Wow -opengl.exe <unknown symbol>+0 (0x02B3F438,0x0053BB90,0x7FFD0F10,0x7BC97FF4)
0053BBE7 Wow -opengl.exe <unknown symbol>+0 (0x000020E8,0x7FFD0F10,0x0308EB48,0x7BC6D6E0)
7BC6D514 ntdll.dll    call_thread_func+12 (0x0053BB90,0x02B3F458,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x0053BB90,0x02B3F458,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFD0FB8,0x0308FB70,0x0308FB70,0x0308FB70)
6815D80E              start_thread+190 (0x0308FB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 26 ---
7B88D801 KERNEL32.dll SleepEx+65 (0x00000064,0x00000000,0x01CCEA00,0x7B8547C7)
7B88D845 KERNEL32.dll Sleep+37 (0x00000064,0x008D96A5,0x7BC97FF4,0x01AECB6
004245E4 Wow -opengl.exe <unknown symbol>+0 (0x01AECB68,0x17C1A0C6,0x008D96A5,0x01AECBC
008D967F Wow -opengl.exe <unknown symbol>+0 (0x7FFD4F10,0x7BC6D514,0x01AECBC8,0x7FFD4F10)
008D9724 Wow -opengl.exe <unknown symbol>+0 (0x008D96A5,0x01AECBC8,0x00000001,0x7BC49894)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x008D96A5,0x01AECBC8,0x00000000,0x00000000)
7BC75C35 ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x01CCFB70,0x01CCFB70,0x01CCFB70)
6815D80E              start_thread+190 (0x01CCFB70,0x00000000,0x00000000,0x00000000)
760977EE              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 9 [Current Thread] ---
BF7FFFFF <unknown module> <unknown symbol>+0 (0x0849F7B8,0x0A3F3020,0x08137DF0,0x00000000)
00624F18 Wow -opengl.exe <unknown symbol>+0 (0x0849ADC8,0x003AF9C8,0x00000001,0x00000000)
00478CA2 Wow -opengl.exe <unknown symbol>+0 (0x00000000,0x003AF9C8,0x082BC200,0x003AF9C
00483A42 Wow -opengl.exe <unknown symbol>+0 (0x00000000,0x00000000,0x06627A88,0x3F77FE41)
00486AF8 Wow -opengl.exe <unknown symbol>+0 (0x00000000,0x088DC188,0x082BC200,0x0000000F)
00486D75 Wow -opengl.exe <unknown symbol>+0 (0x00000000,0x0812B5D4,0x3F800000,0x00000000)
007FEC01 Wow -opengl.exe <unknown symbol>+0 (0xFF000000,0x00000003,0xFF000000,0x06625514)
007BC180 Wow -opengl.exe <unknown symbol>+0 (0xFF000000,0x00000001,0x06625498,0x06625514)
007F996A Wow -opengl.exe <unknown symbol>+0 (0x06625514,0x065034A8,0x00000006,0x065027B
008158A7 Wow -opengl.exe <unknown symbol>+0 (0x02C2C480,0x063CD0C0,0x063CD0A8,0x00000000)
00815D9B Wow -opengl.exe <unknown symbol>+0 (0x00000000,0x063CD0B0,0x063CD0C0,0x413AAC09)
007E953C Wow -opengl.exe <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x02B3D560)
008356B9 Wow -opengl.exe <unknown symbol>+0 (0x02B3D560,0x00000017,0x00000000,0x00000A2
00833E2F Wow -opengl.exe <unknown symbol>+0 (0x00000000,0x00406C02,0x00000001,0x00000001)
00833F11 Wow -opengl.exe <unknown symbol>+0 (0x0040AFD9,0x00400000,0x00000000,0x0013222A)
00406C7D Wow -opengl.exe <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B8774D4 KERNEL32.dll <unknown symbol>+0 (0x7FFDF000,0xBFE7FF94,0x003AFFC8,0x7BC6D6E0)
7BC6D514 ntdll.dll    call_thread_func+12 (0x7B877480,0x7FFDF000,0x00000000,0x00000000)
7BC6D6E0 ntdll.dll    call_thread_entry_point+112 (0x7B877480,0x7FFDF000,0x00000000,0x00000000)
7BC49D7A ntdll.dll    <unknown symbol>+0 (0x7B877480,0x00000000,0x00000000,0x00000000)
68024E9D              wine_call_on_stack+29 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x01758000  Z:\home\mich\Desktop\wow\Wow -opengl.exe
0x10000000 - 0x10069000  Z:\home\mich\Desktop\wow\DivxDecoder.dll
0x20010000 - 0x2004B000  C:\windows\system32\dsound.dll
0x20060000 - 0x20075000  C:\windows\system32\psapi.dll
0x681F0000 - 0x68316000  C:\windows\system32\user32.dll
0x68330000 - 0x683B6000  C:\windows\system32\gdi32.dll
0x683C0000 - 0x68424000  C:\windows\system32\rpcrt4.dll
0x68440000 - 0x684C1000  C:\windows\system32\opengl32.dll
0x686D0000 - 0x686FC000  C:\windows\system32\d3d9.dll
0x68700000 - 0x6871D000  C:\windows\system32\imm32.dll
0x68730000 - 0x68774000  C:\windows\system32\wininet.dll
0x68790000 - 0x687AD000  C:\windows\system32\mpr.dll
0x687C0000 - 0x6880A000  C:\windows\system32\shlwapi.dll
0x68820000 - 0x6899A000  C:\windows\system32\shell32.dll
0x689A0000 - 0x68A67000  C:\windows\system32\comctl32.dll
0x68A70000 - 0x68A91000  C:\windows\system32\ws2_32.dll
0x68AA0000 - 0x68AAB000  C:\windows\system32\dinput8.dll
0x68AB0000 - 0x68AC5000  C:\windows\system32\version.dll
0x68AD0000 - 0x68AD9000  C:\windows\system32\lz32.dll
0x68AE0000 - 0x68AEE000  C:\windows\system32\system.drv16
0x68BD0000 - 0x68C60000  C:\windows\system32\winex11.drv
0x68C80000 - 0x68CA7000  C:\windows\system32\winealsa.drv
0x68D70000 - 0x68D86000  C:\windows\system32\msacm32.drv
0x68D90000 - 0x68D9C000  C:\windows\system32\midimap.dll
0x68FC0000 - 0x68FF0000  C:\windows\system32\uxtheme.dll
0x6B860000 - 0x6B888000  C:\windows\system32\dinput.dll
0x6CFF0000 - 0x6D06A000  C:\windows\system32\winmm.dll
0x6F0B0000 - 0x6F18D000  C:\windows\system32\ole32.dll
0x738D0000 - 0x739EA000  C:\windows\system32\wined3d.dll
0x77A50000 - 0x77A9A000  C:\windows\system32\advapi32.dll
0x77C30000 - 0x77C54000  C:\windows\system32\msacm32.dll
0x7A7F0000 - 0x7A839000  C:\windows\system32\dbghelp.dll
0x7B820000 - 0x7B972000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCB4000  C:\windows\system32\ntdll.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = BF7FFFFF)

BF7FFFFF: <can't read from this address>


Stack: 1024 bytes starting at (ESP = 003AF840)

* = addr  **                                                  *               
003AF840: C5 4D 62 00  01 00 00 00  CC F7 49 08  C8 AD 49 08  .Mb.......I...I.
003AF850: B8 F7 49 08  00 00 00 00  78 F8 3A 00  18 4F 62 00  ..I.....x.:..Ob.
003AF860: B8 F7 49 08  20 30 3F 0A  F0 7D 13 08  00 00 00 00  ..I. 0?..}......
003AF870: 63 8C 47 00  A8 37 B3 02  AC F8 3A 00  A2 8C 47 00  c.G..7....:...G.
003AF880: C8 AD 49 08  C8 F9 3A 00  01 00 00 00  00 00 00 00  ..I...:.........
003AF890: AC F8 3A 00  11 2C 48 00  48 CC B3 02  00 00 00 00  ..:..,H.H.......
003AF8A0: D4 F8 3A 00  FE 39 48 00  00 00 00 00  D4 F8 3A 00  ..:..9H.......:.
003AF8B0: 42 3A 48 00  00 00 00 00  C8 F9 3A 00  00 C2 2B 08  B:H.......:...+.
003AF8C0: C8 F9 3A 00  D0 F8 3A 00  9E 82 47 00  F0 7D 13 08  ..:...:...G..}..
003AF8D0: C8 F3 46 08  A8 F9 3A 00  F8 6A 48 00  00 00 00 00  ..F...:..jH.....
003AF8E0: 00 00 00 00  88 7A 62 06  41 FE 77 3F  00 00 00 80  .....zb.A.w?....
003AF8F0: 00 00 00 00  00 00 00 80  00 00 00 80  AF FE 39 3F  ..............9?
003AF900: 00 00 00 80  00 00 00 00  00 00 00 00  00 00 00 80  ................
003AF910: 00 00 00 00  00 00 80 3F  00 00 00 80  00 00 00 00  .......?........
003AF920: 0D FD 0F C0  F2 02 10 40  3D 9F 49 AC  26 77 89 B7  .......@=.I.&w..
003AF930: 00 00 80 BF  00 00 00 00  00 00 80 3F  2E BD 3B B4  ...........?..;.
003AF940: 00 00 00 00  00 00 00 00  2E BD 3B 34  00 00 80 3F  ..........;4...?
003AF950: 26 77 89 B7  00 00 00 00  00 00 00 00  00 00 00 00  &w..............
003AF960: 00 00 00 00  00 00 80 3F  F6 21 84 3F  00 00 00 00  .......?.!.?....
003AF970: 00 00 00 00  00 00 00 00  00 00 00 00  49 2D B0 3F  ............I-.?
003AF980: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AF990: 3E 05 80 3F  00 00 80 3F  00 00 00 00  00 00 00 00  >..?...?........
003AF9A0: E2 92 E3 BE  00 00 00 00  78 FA 3A 00  75 6D 48 00  ........x.:.umH.
003AF9B0: 00 00 00 00  88 C1 8D 08  00 C2 2B 08  0F 00 00 00  ..........+.....
003AF9C0: 01 00 00 00  D4 B5 12 08  41 FE 77 3F  00 00 00 80  ........A.w?....
003AF9D0: 00 00 00 00  00 00 00 80  00 00 00 80  AF FE 39 3F  ..............9?
003AF9E0: 00 00 00 80  00 00 00 00  00 00 00 00  00 00 00 80  ................
003AF9F0: 00 00 00 00  00 00 80 3F  00 00 00 80  00 00 00 00  .......?........
003AFA00: 0D FD 0F C0  F2 02 10 40  88 7A 62 06  10 20 07 01  .......@.zb.. ..
003AFA10: 30 00 2B 0A  00 00 00 00  AC D0 8D 08  00 00 00 00  0.+.............
003AFA20: 00 00 00 00  FF FF FF FF  20 30 3F 0A  00 00 00 00  ........ 0?.....
003AFA30: F0 7D 13 08  00 00 00 00  FC 31 3F 0A  00 00 00 00  .}.......1?.....
003AFA40: 00 00 00 00  00 00 00 00  01 00 00 00  FF FF FF FF  ................
003AFA50: C8 CC 54 08  00 00 00 00  40 F1 46 08  00 00 00 00  ..T.....@.F.....
003AFA60: 80 AB 33 0A  00 00 00 00  38 CE E3 05  48 17 20 06  ..3.....8...H. .
003AFA70: 08 86 31 06  00 00 00 00  50 FB 3A 00  01 EC 7F 00  ..1.....P.:.....
003AFA80: 00 00 00 00  D4 B5 12 08  00 00 80 3F  00 00 00 00  ...........?....
003AFA90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 80 3F  ...............?
003AFAA0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AFAB0: 00 00 80 3F  00 00 00 00  CD CC CC BE  99 99 99 BE  ...?............
003AFAC0: 00 00 00 00  00 00 80 3F  00 00 20 40  00 00 00 00  .......?.. @....
003AFAD0: 00 00 00 00  00 00 00 00  00 00 00 00  56 55 55 40  ............VUU@
003AFAE0: 00 00 00 00  00 00 00 00  00 00 00 80  00 00 00 80  ................
003AFAF0: 6F 12 03 BB  00 00 00 00  00 00 00 80  00 00 00 80  o...............
003AFB00: 00 00 00 80  00 00 80 3F  CC 8D 24 C1  1D 7F 0F BD  .......?..$.....
003AFB10: 58 41 1C 40  01 00 00 00  00 00 00 00  C0 DF 31 41  XA.@..........1A
003AFB20: 1D 7F 0F BD  17 47 1C 40  00 00 00 00  00 00 00 00  .....G.@........
003AFB30: 00 00 80 3F  00 00 00 00  00 00 80 3F  00 00 80 3F  ...?.......?...?
003AFB40: 00 00 00 00  00 00 00 00  00 00 80 3F  00 00 80 3F  ...........?...?
003AFB50: 7C FB 3A 00  80 C1 7B 00  00 00 00 FF  03 00 00 00  |.:...{.........
003AFB60: 00 00 00 FF  14 55 62 06  E8 3A 58 06  00 00 00 00  .....Ub..:X.....
003AFB70: 14 00 00 00  00 00 00 00  33 33 A3 41  3C FC 3A 00  ........33.A<.:.
003AFB80: 6A 99 7F 00  00 00 00 FF  01 00 00 00  98 54 62 06  j............Tb.
003AFB90: 14 55 62 06  C0 8D 55 06  B0 FB 3A 00  E3 86 7F 00  .Ub...U...:.....
003AFBA0: 00 00 00 00  30 E8 62 06  1C B7 47 08  01 00 00 00  ....0.b...G.....
003AFBB0: C8 FB 3A 00  83 89 7F 00  30 E8 62 06  74 25 5D 06  ..:.....0.b.t%].
003AFBC0: 38 6D 10 08  1C B7 47 08  00 FC 3A 00  3F 8A 7F 00  8m....G...:.?...
003AFBD0: 18 2E 58 06  02 00 00 00  04 00 00 00  54 26 5D 06  ..X.........T&].
003AFBE0: B4 26 5D 06  00 00 00 00  00 00 00 00  06 00 00 00  .&].............
003AFBF0: C8 88 04 01  60 F6 B3 02  03 00 00 00  74 25 5D 06  ....`.......t%].
003AFC00: 0C FC 3A 00  B5 8A 7F 00  74 25 5D 06  24 FC 3A 00  ..:.....t%].$.:.
003AFC10: F6 6C 80 00  1C B7 47 08  A8 51 AC 01  84 52 AC 01  .l....G..Q...R..
003AFC20: 00 00 00 00  A8 51 AC 01  CC 9E 7F 00  84 52 AC 01  .....Q.......R..
003AFC30: 26 55 81 00  D0 D2 3C 06  06 00 00 00  58 FC 3A 00  &U....<.....X.:.


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x1
Number of Processors:   1
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        15
Processor Revision:     19458
Os Version:             5.1
Os Service Pack:        3.0

Percent memory used:    16
Total physical memory:  2374905856
Free Memory:            1993949184
Page file:              5681426432
Total virtual memory:   2147352575

soo how can i solve the problem and thanks for ur time and for ur help =)

---

