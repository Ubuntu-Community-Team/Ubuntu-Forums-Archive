---
title: "Wow on Wine in Kubuntu help"
date: 2009-02-21
forum: Wine
---

### Post by HH60Gunner on 2009-02-21
I'm still a newbie to linux and wanted to transistion further away from windows and get the one program on linux that always draws me back to logging into windows, WOW.  I'm running on a gateway FX series laptop with, a dual core processor, 4 gigs of memory, and a Nvidia 9800 gts.  I've installed wine, and I've installed the Nvidia 177 proprietary drivers.  When I try to launch wow I get a scrambled mess that even shows parts of a website that I was recently at, even though I no longer even have a web browser open.  Any idea on what's going on?

---

### Post by HH60Gunner on 2009-02-21
This is what pops up on the wow-error screen....

==============================================================================
World of WarCraft (build 9551)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Feb 21, 2009  4:32:28.619 AM
User:     enderusaf
Computer: enderusaf-lapto
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #131 (0x85100083) File Corrupt
Program:	C:\Program Files\World of Warcraft\Wow.exe
File:	DBFilesClient\Achievement.dbc




WoWBuild: 9551
Settings: 
SET locale "enUS"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxWindow "1"
SET gxMaximize "1"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1440x900"
SET gxTripleBuffer "1"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "1"
SET textureFilteringMode "5"
SET movie "0"
SET mouseSpeed "1"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_EnableErrorSpeech "0"
SET Sound_EnableMusic "0"
SET Sound_MasterVolume "0.5"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "0"
SET shadowLevel "0"
SET farclip "1277"
SET specular "1"
SET particleDensity "1.000000"
SET groundEffectDensity "64"
SET groundEffectDist "140"
SET environmentDetail "1.5"
SET extShadowQuality "4"
SET weatherDensity "3"
SET realmName "Bloodscalp"
SET gameTip "50"
SET VoiceActivationSensitivity "0.39999997615814"
SET uiScale "0.63999998569489"
SET useUiScale "1"
SET gxRefresh "50"
SET checkAddonVersion "0"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET gxVSync "0"
SET Sound_SFXVolume "0.10000000149012"
SET lastCharacterIndex "3"
SET SoundOutputSystem "â&#8364;&#339;1â&#8364;³"
------------------------------------------------------------------------------

----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 5/5 threads...

--- Thread ID: 42 ---
7BC6AF03 7C5F7858 0001:00059F03 C:\windows\system32\ntdll.dll
7BC6B1F2 7C5F7888 0001:0005A1F2 C:\windows\system32\ntdll.dll
7B890752 7C5F79C8 0001:0006F752 C:\windows\system32\KERNEL32.dll
7B89094C 7C5F79E8 0001:0006F94C C:\windows\system32\KERNEL32.dll
006AB710 7C5F79F8 0001:002AA710 C:\Program Files\World of Warcraft\Wow.exe
00780C4D 7C5F7A0C 0001:0037FC4D C:\Program Files\World of Warcraft\Wow.exe
006A79A7 7C5F7A28 0001:002A69A7 C:\Program Files\World of Warcraft\Wow.exe
7BC6C91E 7C5F7A38 0001:0005B91E C:\windows\system32\ntdll.dll
7BC6DF42 7C5F7AD8 0001:0005CF42 C:\windows\system32\ntdll.dll
7BC6E13D 7C5F83C8 0001:0005D13D C:\windows\system32\ntdll.dll
B7E8450F 7C5F84C8 0000:00000000 <unknown>

--- Thread ID: 41 ---
7B890A62 7C7685C0 0001:0006FA62 C:\windows\system32\KERNEL32.dll
7B890AA5 7C7685E0 0001:0006FAA5 C:\windows\system32\KERNEL32.dll
007CB33D 7C7685EC 0001:003CA33D C:\Program Files\World of Warcraft\Wow.exe
004555FE 7C768A0C 0001:000545FE C:\Program Files\World of Warcraft\Wow.exe
006A79A7 7C768A28 0001:002A69A7 C:\Program Files\World of Warcraft\Wow.exe
7BC6C91E 7C768A38 0001:0005B91E C:\windows\system32\ntdll.dll
7BC6DF42 7C768AD8 0001:0005CF42 C:\windows\system32\ntdll.dll
7BC6E13D 7C7693C8 0001:0005D13D C:\windows\system32\ntdll.dll
B7E8450F 7C7694C8 0000:00000000 <unknown>

--- Thread ID: 40 ---
7B890A62 7C8D99A0 0001:0006FA62 C:\windows\system32\KERNEL32.dll
7B890AA5 7C8D99C0 0001:0006FAA5 C:\windows\system32\KERNEL32.dll
006BD254 7C8D99E8 0001:002BC254 C:\Program Files\World of Warcraft\Wow.exe
007EDBCF 7C8D9A20 0001:003ECBCF C:\Program Files\World of Warcraft\Wow.exe
007EDC74 7C8D9A38 0001:003ECC74 C:\Program Files\World of Warcraft\Wow.exe
7BC6DF42 7C8D9AD8 0001:0005CF42 C:\windows\system32\ntdll.dll
7BC6E13D 7C8DA3C8 0001:0005D13D C:\windows\system32\ntdll.dll
B7E8450F 7C8DA4C8 0000:00000000 <unknown>

--- Thread ID: 39 ---
7BC6AF03 7CB4A828 0001:00059F03 C:\windows\system32\ntdll.dll
7BC6B1F2 7CB4A858 0001:0005A1F2 C:\windows\system32\ntdll.dll
7B890752 7CB4A998 0001:0006F752 C:\windows\system32\KERNEL32.dll
7B89094C 7CB4A9B8 0001:0006F94C C:\windows\system32\KERNEL32.dll
006BB325 7CB4A9D4 0001:002BA325 C:\Program Files\World of Warcraft\Wow.exe
006D56D5 7CB4A9E8 0001:002D46D5 C:\Program Files\World of Warcraft\Wow.exe
007EDBCF 7CB4AA20 0001:003ECBCF C:\Program Files\World of Warcraft\Wow.exe
007EDC74 7CB4AA38 0001:003ECC74 C:\Program Files\World of Warcraft\Wow.exe
7BC6DF42 7CB4AAD8 0001:0005CF42 C:\windows\system32\ntdll.dll
7BC6E13D 7CB4B3C8 0001:0005D13D C:\windows\system32\ntdll.dll
B7E8450F 7CB4B4C8 0000:00000000 <unknown>

--- Thread ID: 37 [Current Thread] ---
006BFC92 003AF544 0001:002BEC92 C:\Program Files\World of Warcraft\Wow.exe
006B7223 003AF550 0001:002B6223 C:\Program Files\World of Warcraft\Wow.exe
006DD654 003AF574 0001:002DC654 C:\Program Files\World of Warcraft\Wow.exe
006BB020 003AF5AC 0001:002BA020 C:\Program Files\World of Warcraft\Wow.exe
006B6F81 003AF5C8 0001:002B5F81 C:\Program Files\World of Warcraft\Wow.exe
006E0711 003AFAF8 0001:002DF711 C:\Program Files\World of Warcraft\Wow.exe
006E747C 003AFC24 0001:002E647C C:\Program Files\World of Warcraft\Wow.exe
006E9ACE 003AFD68 0001:002E8ACE C:\Program Files\World of Warcraft\Wow.exe
00588AFF 003AFD98 0001:00187AFF C:\Program Files\World of Warcraft\Wow.exe
005A8504 003AFDE8 0001:001A7504 C:\Program Files\World of Warcraft\Wow.exe
004262E0 003AFE54 0001:000252E0 C:\Program Files\World of Warcraft\Wow.exe
00426481 003AFE6C 0001:00025481 C:\Program Files\World of Warcraft\Wow.exe
00406958 003AFF08 0001:00005958 C:\Program Files\World of Warcraft\Wow.exe
7B878828 003AFFE8 0001:00057828 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 5/5 threads...

--- Thread ID: 42 ---
7BC6AF03 ntdll.dll    NTDLL_wait_for_multiple_objects+547 (0x00000001,0x7C5F78B0,0x00000004,0x00000000)
7BC6B1F2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7C5F78B0,0x00000000,0x00000000)
7B890752 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x7C5F79F0,0x00000000,0xFFFFFFFF)
7B89094C KERNEL32.dll WaitForSingleObject+60 (0x00002080,0xFFFFFFFF,0x7C5F7A0C,0x00780C4D)
006AB710 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x0000002A,0x00780C20,0x7C5F7A28)
00780C4D Wow.exe      <unknown symbol>+0 (0x012E9DD8,0x006A7950,0x05F45818,0x7BC8AFF4)
006A79A7 Wow.exe      <unknown symbol>+0 (0x000020E0,0x006A7950,0x7C5F7AD8,0x7BC6DF42)
7BC6C91E ntdll.dll    call_thread_entry_point+14 (0x006A7950,0x05F45818,0x7BCA6360,0xB7E890C1)
7BC6DF42 ntdll.dll    <unknown symbol>+0 (0x7C5F7B0C,0x00000000,0x00000000,0x00000000)
7BC6E13D ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x7C5F8B90,0x7C5F8B90,0x7C5F8B90)
B7E8450F              start_thread+191 (0x7C5F8B90,0x00000000,0x00000000,0x00000000)
B7E00A0E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 41 ---
7B890A62 KERNEL32.dll SleepEx+50 (0x00000001,0x00000000,0x00000000,0x00000000)
7B890AA5 KERNEL32.dll Sleep+37 (0x00000001,0x7C768A0C,0x004555FE,0x00000001)
007CB33D Wow.exe      <unknown symbol>+0 (0x00000000,0x00455440,0x0235FD78,0x00000029)
004555FE Wow.exe      <unknown symbol>+0 (0x0235FD78,0x006A7950,0x0235F9A0,0x7BC8AFF4)
006A79A7 Wow.exe      <unknown symbol>+0 (0x000020DC,0x006A7950,0x7C768AD8,0x7BC6DF42)
7BC6C91E ntdll.dll    call_thread_entry_point+14 (0x006A7950,0x0235F9A0,0x7BCA6360,0xB7E890C1)
7BC6DF42 ntdll.dll    <unknown symbol>+0 (0x7C768B0C,0x00000000,0x00000000,0x00000000)
7BC6E13D ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x7C769B90,0x7C769B90,0x7C769B90)
B7E8450F              start_thread+191 (0x7C769B90,0x00000000,0x00000000,0x00000000)
B7E00A0E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 40 ---
7B890A62 KERNEL32.dll SleepEx+50 (0x00000064,0x00000000,0x7C8D99C0,0x7B855B07)
7B890AA5 KERNEL32.dll Sleep+37 (0x00000064,0x007EDBF5,0x7BC8AFF4,0x01906328)
006BD254 Wow.exe      <unknown symbol>+0 (0x01906328,0x6DBA9F04,0x007EDBF5,0x01907C68)
007EDBCF Wow.exe      <unknown symbol>+0 (0x01907C68,0x7BC6C91E,0x01907C68,0x007EDBF5)
007EDC74 Wow.exe      <unknown symbol>+0 (0x007EDBF5,0x01907C68,0x7BCA6360,0xB7E890C1)
7BC6DF42 ntdll.dll    <unknown symbol>+0 (0x7C8D9B0C,0x00000000,0x00000000,0x00000000)
7BC6E13D ntdll.dll    <unknown symbol>+0 (0x7FFD0FB8,0x7C8DAB90,0x7C8DAB90,0x7C8DAB90)
B7E8450F              start_thread+191 (0x7C8DAB90,0x00000000,0x00000000,0x00000000)
B7E00A0E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 39 ---
7BC6AF03 ntdll.dll    NTDLL_wait_for_multiple_objects+547 (0x00000001,0x7CB4A880,0x00000004,0x00000000)
7BC6B1F2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7CB4A880,0x00000000,0x00000000)
7B890752 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x7CB4A9C0,0x00000000,0xFFFFFFFF)
7B89094C KERNEL32.dll WaitForSingleObject+60 (0x000020C0,0xFFFFFFFF,0x7BC8AFF4,0x007EDBF5)
006BB325 Wow.exe      <unknown symbol>+0 (0x0171EAE0,0x007EDBF5,0x0171EB60,0x7CB4AA20)
006D56D5 Wow.exe      <unknown symbol>+0 (0x0171EB00,0x6D83AF04,0x007EDBF5,0x0171EB60)
007EDBCF Wow.exe      <unknown symbol>+0 (0x0171EB60,0x7BC6C91E,0x0171EB60,0x0171EB60)
007EDC74 Wow.exe      <unknown symbol>+0 (0x007EDBF5,0x0171EB60,0x7BCA6360,0xB7E890C1)
7BC6DF42 ntdll.dll    <unknown symbol>+0 (0x7CB4AB0C,0x00000000,0x00000000,0x00000000)
7BC6E13D ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x7CB4BB90,0x7CB4BB90,0x7CB4BB90)
B7E8450F              start_thread+191 (0x7CB4BB90,0x00000000,0x00000000,0x00000000)
B7E00A0E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 37 [Current Thread] ---
006BFC92 Wow.exe      <unknown symbol>+0 (0x05905DB0,0x003AF574,0x006DD654,0x05905E40)
006B7223 Wow.exe      <unknown symbol>+0 (0x05905E40,0x00000000,0x00000000,0x00061594)
006DD654 Wow.exe      <unknown symbol>+0 (0x05905E40,0x00000000,0x00000000,0x00061594)
006BB020 Wow.exe      <unknown symbol>+0 (0x05905E40,0x00000000,0x00000000,0x00061594)
006B6F81 Wow.exe      <unknown symbol>+0 (0x05905E40,0x00000000,0x00000000,0x00061594)
006E0711 Wow.exe      <unknown symbol>+0 (0x0191FDF8,0x05905E40,0x00061594,0x003AFC34)
006E747C Wow.exe      <unknown symbol>+0 (0x0191FC68,0x05905E40,0x00000000,0x00000000)
006E9ACE Wow.exe      <unknown symbol>+0 (0x0191FC68,0x0191FD74,0x05905E40,0x00000001)
00588AFF Wow.exe      <unknown symbol>+0 (0x00964CEC,0x000000E7,0x005A999E,0x004038D4)
005A8504 Wow.exe      <unknown symbol>+0 (0x018CB138,0x00000007,0x00000000,0x00000A28)
004262E0 Wow.exe      <unknown symbol>+0 (0x00000000,0x004068E0,0x00000001,0x00000001)
00426481 Wow.exe      <unknown symbol>+0 (0x0040ABB9,0x00400000,0x00000000,0x00111DF4)
00406958 Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B878828 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7EAED37              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x01391000  C:\Program Files\World of Warcraft\Wow.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B93D000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCA7000  C:\windows\system32\ntdll.dll
0x7CD10000 - 0x7CD20000  C:\windows\system32\psapi.dll
0x7CD30000 - 0x7CD6C000  C:\windows\system32\dbghelp.dll
0x7CDD0000 - 0x7CDFC000  C:\windows\system32\uxtheme.dll
0x7D1B0000 - 0x7D1C4000  C:\windows\system32\midimap.dll
0x7D1D0000 - 0x7D1DD000  C:\windows\system32\msacm32.drv
0x7D2C0000 - 0x7D2EC000  C:\windows\system32\winealsa.drv
0x7D330000 - 0x7D3B6000  C:\windows\system32\winex11.drv
0x7D5C0000 - 0x7D617000  C:\windows\system32\rpcrt4.dll
0x7D630000 - 0x7D6BD000  C:\windows\system32\ole32.dll
0x7D6C0000 - 0x7D6E5000  C:\windows\system32\msacm32.dll
0x7D700000 - 0x7D718000  C:\windows\system32\iphlpapi.dll
0x7D720000 - 0x7D745000  C:\windows\system32\ws2_32.dll
0x7D750000 - 0x7D80A000  C:\windows\system32\comctl32.dll
0x7D820000 - 0x7D91E000  C:\windows\system32\shell32.dll
0x7D930000 - 0x7D979000  C:\windows\system32\shlwapi.dll
0x7D980000 - 0x7D99C000  C:\windows\system32\mpr.dll
0x7D9B0000 - 0x7DAB1000  C:\windows\system32\wined3d.dll
0x7DB00000 - 0x7DB3F000  C:\windows\system32\wininet.dll
0x7DB50000 - 0x7DB60000  C:\windows\system32\imm32.dll
0x7DB70000 - 0x7DB75000  C:\windows\system32\lz32.dll
0x7DB80000 - 0x7DB90000  C:\windows\system32\version.dll
0x7DBA0000 - 0x7DBC1000  C:\windows\system32\d3d9.dll
0x7EB30000 - 0x7EB9A000  C:\windows\system32\opengl32.dll
0x7EBB0000 - 0x7EBED000  C:\windows\system32\advapi32.dll
0x7EC00000 - 0x7EC8C000  C:\windows\system32\gdi32.dll
0x7ECB0000 - 0x7EDD8000  C:\windows\system32\user32.dll
0x7EDE0000 - 0x7EE6C000  C:\windows\system32\winmm.dll


----------------------------------------
    Memory Dump
----------------------------------------

Stack: 1024 bytes starting at (ESP = 003AE758)

* = addr                            **                                *       
003AE750: 4C 57 6B 00  58 E7 3A 00  E4 20 00 00  02 00 00 00  LWk.X.:.. ......
003AE760: 4C 57 6B 00  58 E7 3A 00  6C E7 3A 00  F8 F4 3A 00  LWk.X.:.l.:...:.
003AE770: B3 9C 6A 00  01 00 6E 00  A0 8A 6A 00  E4 20 00 00  ..j...n...j.. ..
003AE780: 03 00 00 00  00 00 00 00  01 00 00 00  F8 FD 91 01  ................
003AE790: 94 15 06 00  00 63 90 01  88 0E 15 00  CE C4 8A 7B  .....c.........{
003AE7A0: 70 F9 3A 00  C0 6E 84 7B  0F 00 00 00  F4 7F 8B 7B  p.:..n.{.......{
003AE7B0: 50 6F 84 7B  F0 8E 6E 00  58 E8 3A 00  07 00 EF 41  Po.{..n.X.:....A
003AE7C0: F0 AE FA 3C  00 00 00 00  00 00 00 00  00 00 00 00  ...<............
003AE7D0: 00 00 00 00  00 00 00 00  0F 00 00 00  00 00 00 00  ................
003AE7E0: 00 E8 3A 00  00 C1 C4 01  00 00 00 00  00 00 00 00  ..:.............
003AE7F0: 00 00 00 00  00 00 00 00  0F 00 00 00  00 00 00 00  ................
003AE800: 00 D6 20 01  40 7B 90 01  01 0A 70 01  00 00 00 00  .. .@{....p.....
003AE810: 00 E2 C4 01  43 72 65 64  69 74 73 5F  42 43 2E 68  ....Credits_BC.h
003AE820: 74 6D 6C 00  0F 00 00 00  0F 00 00 00  00 D6 20 01  tml........... .
003AE830: E8 E4 3A 00  70 F9 3A 00  CC 7D 91 00  FF FF FF FF  ..:.p.:..}......
003AE840: 06 00 00 80  00 00 00 00  00 00 00 00  50 6F 84 7B  ............Po.{
003AE850: 00 00 00 00  50 6F 84 7B  34 F3 3A 00  F4 AA 6D 00  ....Po.{4.:...m.
003AE860: 88 0E 15 00  A4 FC 3A 00  D4 FA 3A 00  A4 FC 3A 00  ......:...:...:.
003AE870: 43 72 65 64  69 74 73 5F  42 43 2E 68  74 6D 6C 00  Credits_BC.html.
003AE880: 2D 65 6E 55  53 2E 4D 50  51 00 D8 B7  00 00 00 00  -enUS.MPQ.......
003AE890: 00 00 00 00  54 68 69 73  20 61 70 70  6C 69 63 61  ....This applica
003AE8A0: 74 69 6F 6E  20 68 61 73  20 65 6E 63  6F 75 6E 74  tion has encount
003AE8B0: 65 72 65 64  20 61 20 63  72 69 74 69  63 61 6C 20  ered a critical 
003AE8C0: 65 72 72 6F  72 3A 0A 0A  45 52 52 4F  52 20 23 31  error:..ERROR #1
003AE8D0: 33 31 20 28  30 78 38 35  31 30 30 30  38 33 29 20  31 (0x85100083) 
003AE8E0: 46 69 6C 65  20 43 6F 72  72 75 70 74  0A 50 72 6F  File Corrupt.Pro
003AE8F0: 67 72 61 6D  3A 09 43 3A  5C 50 72 6F  67 72 61 6D  gram:.C:\Program
003AE900: 20 46 69 6C  65 73 5C 57  6F 72 6C 64  20 6F 66 20   Files\World of 
003AE910: 57 61 72 63  72 61 66 74  5C 57 6F 77  2E 65 78 65  Warcraft\Wow.exe
003AE920: 0A 46 69 6C  65 3A 09 44  42 46 69 6C  65 73 43 6C  .File:.DBFilesCl
003AE930: 69 65 6E 74  5C 41 63 68  69 65 76 65  6D 65 6E 74  ient\Achievement
003AE940: 2E 64 62 63  0A 0A 0A 0A  00 00 00 00  00 00 00 00  .dbc............
003AE950: A4 EE 3A 00  00 00 00 00  00 00 00 00  E4 EF 3A 00  ..:...........:.
003AE960: FF FF FF FF  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AE970: FA FF FF FF  00 00 00 00  00 00 00 00  FF FF FF FF  ................
003AE980: EA E8 C7 7B  E3 E8 C7 7B  00 00 00 00  84 EE 63 00  ...{...{......c.
003AE990: 3A 00 00 00  0B 00 00 00  00 00 63 00  3A 00 63 00  :.........c.:.c.
003AE9A0: 3A 00 D6 7E  4A DD 63 00  3A 00 00 00  A4 EE 3A 00  :..~J.c.:.....:.
003AE9B0: 03 00 00 00  0B 00 00 00  00 00 00 00  00 00 00 00  ................
003AE9C0: 00 00 00 00  10 00 00 00  A3 EE 3A 00  00 00 00 00  ..........:.....
003AE9D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AE9E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AE9F0: 00 00 00 00  00 00 00 00  30 F0 3A 00  AF 77 D6 7E  ........0.:..w.~
003AEA00: 00 00 00 00  00 00 00 00  00 00 00 78  00 00 00 00  ...........x....
003AEA10: 00 00 00 00  D4 FF FF FF  35 03 00 00  00 00 00 00  ........5.......
003AEA20: 00 00 00 00  E4 09 D6 B7  00 00 00 00  00 00 00 00  ................
003AEA30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AEA40: 94 EF 3A 00  00 00 00 00  00 00 00 00  CC F0 3A 00  ..:...........:.
003AEA50: FD FF FF FF  EC E8 C7 7B  00 00 00 00  00 00 00 00  .......{........
003AEA60: 00 00 00 00  4A E0 D6 7E  00 00 00 00  00 00 00 00  ....J..~........
003AEA70: 00 00 00 00  62 DD D6 7E  00 00 00 00  00 00 00 00  ....b..~........
003AEA80: 1E 00 00 00  31 8D EC B7  00 00 00 00  EC E8 C7 7B  ....1..........{
003AEA90: 90 F0 3A 00  AD 77 D6 7E  88 F0 3A 00  94 EF 3A 00  ..:..w.~..:...:.
003AEAA0: 26 00 00 00  01 00 00 00  08 00 00 00  62 DD D6 7E  &...........b..~
003AEAB0: 00 F1 3A 00  A3 EE 3A 00  F4 F0 3A 00  00 00 00 00  ..:...:...:.....
003AEAC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AEAD0: 00 00 00 00  58 9D 71 01  B4 F0 3A 00  58 9D 71 01  ....X.q...:.X.q.
003AEAE0: 00 00 00 00  00 00 00 00  20 00 00 00  00 00 00 00  ........ .......
003AEAF0: 00 00 00 00  00 00 00 00  00 00 00 75  00 00 00 00  ...........u....
003AEB00: 00 00 00 00  00 00 00 00  61 3F C3 7B  00 00 00 00  ........a?.{....
003AEB10: 00 00 00 00  61 3F C3 7B  61 3F C3 7B  08 02 00 00  ....a?.{a?.{....
003AEB20: F4 AF C8 7B  34 EB 3A 00  8F 36 C3 7B  08 02 00 00  ...{4.:..6.{....
003AEB30: F4 AF C8 7B  44 EB 3A 00  A0 9B C5 7B  C0 35 C9 7B  ...{D.:....{.5.{
003AEB40: F4 AF C8 7B  C4 EB 3A 00  85 0B C5 7B  40 EC 3A 00  ...{..:....{@.:.
003AEB50: 90 02 22 00  46 00 00 00  B8 1C 57 03  00 00 08 03  ..".F.....W.....


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
Processor Revision:     5894
Os Version:             5.1
Os Service Pack:        4.0

Percent memory used:    15
Total physical memory:  3181928448
Free Memory:            2680180736
Page file:              6890115072
Total virtual memory:   2147352575

---

### Post by alexandari on 2009-02-21
Is your WOW installed on your Windows partition? And which version of Wine are you using? If it is,it may sound strange but,try installing it on your ubuntu. I dont mean copy and paste the whole folder,I mean install it. I`ve also had such problems with my WoW but that was maybe a year or two ago...I was still using cedega back then.

---

### Post by HH60Gunner on 2009-02-21
I copied and pasted it into kubuntu.  Honestly I'm not even sure exactly how to install it in kubuntu.  If I insert the wow disks, no there's no .exe that I can open with wine.

---

### Post by alexandari on 2009-02-21
type  ```
sudo mount -o remount,unhide /dev/cdrom

```

in the terminal and check the disk again :)

---

### Post by Mmmbopdowedop on 2009-02-21
Have you tried running it in OpenGL?

Add the line:
> 
SET gxApi "opengl"
to your config.wtf file

I had this problem when trying to start it in D3D, the screen would go black and throw an error #132 at me on my nVidia 8500 GT. 
Works great in OpenGL for me.

---

### Post by panaut0lordv on 2009-02-21
Run Repair.exe from your WoW folder or reinstall game.

---

### Post by boglio on 2009-02-21
Add to your config.wtf file:
```
SET gxApi "opengl"
```

---

