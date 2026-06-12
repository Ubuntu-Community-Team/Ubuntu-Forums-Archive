---
title: "World of Warcraft problem"
date: 2009-02-09
forum: Wine
---

### Post by Paliusz on 2009-02-09
Hello

I have got problem with World of Warcraft under wine.
In unknow moments in game WoW crash.
```
==============================================================================
World of WarCraft (build 8606)

Exe:      C:\World of Warcraft\Wow.exe
Time:     Feb  9, 2009  9:42:10.922 PM
User:     luki
Computer: luki-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00733085

The instruction at "0x00733085" referenced memory at "0xC9F23EAB".
The memory could not be "read".


WoWBuild: 8606
Realm: Avalon-ForumWoW [193.200.241.139:8085]
Local Zone: Stormwind City
Local Player: Paliusz, 0000000000003FC0, (-8740.21,496.648,96.5337)
Add Ons: Atlas Atlas_DungeonLocs Atlas_Entrances Atlas_FlightPaths Atlas_OutdoorRaids AtlasLoot Cartographer Cartographer_QuestInfo Cartographer_Battlegrounds Cartographer_Coordinates Cartographer_Foglight Cartographer_GroupColors Cartographer_GuildPositions Cartographer_InstanceLoot Cartographer_InstanceMaps Cartographer_InstanceNotes Cartographer_LookNFeel Cartographer_Notes Cartographer_POI Cartographer_Professions Cartographer_Waypoints Cartographer_ZoneInfo Cooldowns Cryolysis2 DamageMeters OmniCC Prat QuestHelper !Swatter TitanGuild TitanMail TitanAmmo TitanBag TitanClock TitanCoords TitanCritLine TitanGoldTracker TitanHonor TitanLootType TitanPerformance TitanRegen TitanRepair TitanRider TitanStanceSets TitanVolume TitanXP Titan WeaponQuickSwap XPerl XPerl_ArcaneBar XPerl_PartyPet XPerl_Party XPerl_PlayerBuffs XPerl_PlayerPet XPerl_Player XPerl_RaidAdmin XPerl_RaidHelper XPerl_RaidMonitor XPerl_RaidPets XPerl_RaidFrames XPerl_TargetTarget XPerl_Target XLoot majBar 
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=076F39C2  EBX=076F39C2  ECX=008D726D  EDX=0032F540  ESI=0032F540
EDI=008D7267  EBP=0032F428  ESP=0032F428  EIP=00733085  FLG=00010297
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 21/21 threads...

--- Thread ID: 49 ---
7B890932 7A8989EC 0001:0006F932 C:\windows\system32\KERNEL32.dll
7B890975 7A898A0C 0001:0006F975 C:\windows\system32\KERNEL32.dll
007FDB00 7A898A28 0001:003FCB00 C:\World of Warcraft\Wow.exe
7BC738DE 7A898A38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 7A898AD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7A8993C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7A8994C8 0000:00000000 <unknown>

--- Thread ID: 48 ---
7B890932 7A9A99EC 0001:0006F932 C:\windows\system32\KERNEL32.dll
7B890975 7A9A9A0C 0001:0006F975 C:\windows\system32\KERNEL32.dll
007FDB00 7A9A9A28 0001:003FCB00 C:\World of Warcraft\Wow.exe
7BC738DE 7A9A9A38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 7A9A9AD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7A9AA3C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7A9AA4C8 0000:00000000 <unknown>

--- Thread ID: 47 ---
7BC71EA5 78ADF85C 0001:00060EA5 C:\windows\system32\ntdll.dll
7BC721A2 78ADF88C 0001:000611A2 C:\windows\system32\ntdll.dll
7B890622 78ADF9CC 0001:0006F622 C:\windows\system32\KERNEL32.dll
7B89081C 78ADF9EC 0001:0006F81C C:\windows\system32\KERNEL32.dll
00649400 78ADF9FC 0001:00248400 C:\World of Warcraft\Wow.exe
00424E66 78ADFA0C 0001:00023E66 C:\World of Warcraft\Wow.exe
00645617 78ADFA28 0001:00244617 C:\World of Warcraft\Wow.exe
7BC738DE 78ADFA38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 78ADFAD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 78AE03C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 78AE04C8 0000:00000000 <unknown>

--- Thread ID: 46 ---
7BC71EA5 78BF063C 0001:00060EA5 C:\windows\system32\ntdll.dll
7BC721A2 78BF066C 0001:000611A2 C:\windows\system32\ntdll.dll
7B890622 78BF07AC 0001:0006F622 C:\windows\system32\KERNEL32.dll
7D25336B 78BF07DC 0001:0003236B C:\windows\system32\winex11.drv
7ED1C315 78BF098C 0001:0007B315 C:\windows\system32\user32.dll
7ED1C37F 78BF09AC 0001:0007B37F C:\windows\system32\user32.dll
006771C8 78BF0A20 0001:002761C8 C:\World of Warcraft\Wow.exe
0075FDD4 78BF0A38 0001:0035EDD4 C:\World of Warcraft\Wow.exe
7BC75032 78BF0AD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 78BF13C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 78BF14C8 0000:00000000 <unknown>

--- Thread ID: 45 ---
7BC71EA5 7A00163C 0001:00060EA5 C:\windows\system32\ntdll.dll
7BC721A2 7A00166C 0001:000611A2 C:\windows\system32\ntdll.dll
7B890622 7A0017AC 0001:0006F622 C:\windows\system32\KERNEL32.dll
7D25336B 7A0017DC 0001:0003236B C:\windows\system32\winex11.drv
7ED1C315 7A00198C 0001:0007B315 C:\windows\system32\user32.dll
7ED1C37F 7A0019AC 0001:0007B37F C:\windows\system32\user32.dll
006771C8 7A001A20 0001:002761C8 C:\World of Warcraft\Wow.exe
0075FDD4 7A001A38 0001:0035EDD4 C:\World of Warcraft\Wow.exe
7BC75032 7A001AD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7A0023C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7A0024C8 0000:00000000 <unknown>

--- Thread ID: 44 ---
7BC71EA5 7A6A8868 0001:00060EA5 C:\windows\system32\ntdll.dll
7BC721A2 7A6A8898 0001:000611A2 C:\windows\system32\ntdll.dll
7B890622 7A6A89D8 0001:0006F622 C:\windows\system32\KERNEL32.dll
7B89081C 7A6A89F8 0001:0006F81C C:\windows\system32\KERNEL32.dll
0083544E 7A6A8A28 0001:0043444E C:\World of Warcraft\Wow.exe
7BC738DE 7A6A8A38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 7A6A8AD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7A6A93C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7A6A94C8 0000:00000000 <unknown>

--- Thread ID: 43 ---
7BC71EA5 7ABBA63C 0001:00060EA5 C:\windows\system32\ntdll.dll
7BC721A2 7ABBA66C 0001:000611A2 C:\windows\system32\ntdll.dll
7B890622 7ABBA7AC 0001:0006F622 C:\windows\system32\KERNEL32.dll
7D25336B 7ABBA7DC 0001:0003236B C:\windows\system32\winex11.drv
7ED1C315 7ABBA98C 0001:0007B315 C:\windows\system32\user32.dll
7ED1C37F 7ABBA9AC 0001:0007B37F C:\windows\system32\user32.dll
006771C8 7ABBAA20 0001:002761C8 C:\World of Warcraft\Wow.exe
0075FDD4 7ABBAA38 0001:0035EDD4 C:\World of Warcraft\Wow.exe
7BC75032 7ABBAAD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7ABBB3C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7ABBB4C8 0000:00000000 <unknown>

--- Thread ID: 42 ---
7BC71EA5 7B4CB868 0001:00060EA5 C:\windows\system32\ntdll.dll
7BC721A2 7B4CB898 0001:000611A2 C:\windows\system32\ntdll.dll
7B890622 7B4CB9D8 0001:0006F622 C:\windows\system32\KERNEL32.dll
7B89081C 7B4CB9F8 0001:0006F81C C:\windows\system32\KERNEL32.dll
0083544E 7B4CBA28 0001:0043444E C:\World of Warcraft\Wow.exe
7BC738DE 7B4CBA38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 7B4CBAD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7B4CC3C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7B4CC4C8 0000:00000000 <unknown>

--- Thread ID: 36 ---
7BC71EA5 7B7FE63C 0001:00060EA5 C:\windows\system32\ntdll.dll
7BC721A2 7B7FE66C 0001:000611A2 C:\windows\system32\ntdll.dll
7B890622 7B7FE7AC 0001:0006F622 C:\windows\system32\KERNEL32.dll
7D25336B 7B7FE7DC 0001:0003236B C:\windows\system32\winex11.drv
7ED1C315 7B7FE98C 0001:0007B315 C:\windows\system32\user32.dll
7ED1C37F 7B7FE9AC 0001:0007B37F C:\windows\system32\user32.dll
006771C8 7B7FEA20 0001:002761C8 C:\World of Warcraft\Wow.exe
0075FDD4 7B7FEA38 0001:0035EDD4 C:\World of Warcraft\Wow.exe
7BC75032 7B7FEAD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7B7FF3C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7B7FF4C8 0000:00000000 <unknown>

--- Thread ID: 35 ---
7BC71EA5 7BAED614 0001:00060EA5 C:\windows\system32\ntdll.dll
7BC721A2 7BAED644 0001:000611A2 C:\windows\system32\ntdll.dll
7B890622 7BAED784 0001:0006F622 C:\windows\system32\KERNEL32.dll
7B89077A 7BAED7A4 0001:0006F77A C:\windows\system32\KERNEL32.dll
00425ACB 7BAED9FC 0001:00024ACB C:\World of Warcraft\Wow.exe
00425328 7BAEDA0C 0001:00024328 C:\World of Warcraft\Wow.exe
00645617 7BAEDA28 0001:00244617 C:\World of Warcraft\Wow.exe
7BC738DE 7BAEDA38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 7BAEDAD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7BAEE3C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7BAEE4C8 0000:00000000 <unknown>

--- Thread ID: 34 ---
7BC71EA5 7BBFE848 0001:00060EA5 C:\windows\system32\ntdll.dll
7BC721A2 7BBFE878 0001:000611A2 C:\windows\system32\ntdll.dll
7B890622 7BBFE9B8 0001:0006F622 C:\windows\system32\KERNEL32.dll
7B89081C 7BBFE9D8 0001:0006F81C C:\windows\system32\KERNEL32.dll
00649400 7BBFE9E8 0001:00248400 C:\World of Warcraft\Wow.exe
00425215 7BBFEA00 0001:00024215 C:\World of Warcraft\Wow.exe
00425351 7BBFEA0C 0001:00024351 C:\World of Warcraft\Wow.exe
00645617 7BBFEA28 0001:00244617 C:\World of Warcraft\Wow.exe
7BC738DE 7BBFEA38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 7BBFEAD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7BBFF3C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7BBFF4C8 0000:00000000 <unknown>

--- Thread ID: 33 ---
7B890932 7BDED9EC 0001:0006F932 C:\windows\system32\KERNEL32.dll
7B890975 7BDEDA0C 0001:0006F975 C:\windows\system32\KERNEL32.dll
007FDB00 7BDEDA28 0001:003FCB00 C:\World of Warcraft\Wow.exe
7BC738DE 7BDEDA38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 7BDEDAD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7BDEE3C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7BDEE4C8 0000:00000000 <unknown>

--- Thread ID: 32 ---
7B890932 7BEFE9EC 0001:0006F932 C:\windows\system32\KERNEL32.dll
7B890975 7BEFEA0C 0001:0006F975 C:\windows\system32\KERNEL32.dll
007FDB00 7BEFEA28 0001:003FCB00 C:\World of Warcraft\Wow.exe
7BC738DE 7BEFEA38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 7BEFEAD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7BEFF3C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7BEFF4C8 0000:00000000 <unknown>

--- Thread ID: 31 ---
7B890932 7C4D69EC 0001:0006F932 C:\windows\system32\KERNEL32.dll
7B890975 7C4D6A0C 0001:0006F975 C:\windows\system32\KERNEL32.dll
007FDB00 7C4D6A28 0001:003FCB00 C:\World of Warcraft\Wow.exe
7BC738DE 7C4D6A38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 7C4D6AD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7C4D73C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7C4D74C8 0000:00000000 <unknown>

--- Thread ID: 30 ---
7B890932 7C5E79EC 0001:0006F932 C:\windows\system32\KERNEL32.dll
7B890975 7C5E7A0C 0001:0006F975 C:\windows\system32\KERNEL32.dll
007FDB00 7C5E7A28 0001:003FCB00 C:\World of Warcraft\Wow.exe
7BC738DE 7C5E7A38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 7C5E7AD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7C5E83C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7C5E84C8 0000:00000000 <unknown>

--- Thread ID: 29 ---
7EE0E967 7C708A28 0001:0002D967 C:\windows\system32\winmm.dll
7BC738DE 7C708A38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 7C708AD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7C7093C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7C7094C8 0000:00000000 <unknown>

--- Thread ID: 28 ---
7BC71EA5 7C866854 0001:00060EA5 C:\windows\system32\ntdll.dll
7BC721A2 7C866884 0001:000611A2 C:\windows\system32\ntdll.dll
7B890622 7C8669C4 0001:0006F622 C:\windows\system32\KERNEL32.dll
7B89081C 7C8669E4 0001:0006F81C C:\windows\system32\KERNEL32.dll
00649400 7C8669F4 0001:00248400 C:\World of Warcraft\Wow.exe
00709102 7C866A0C 0001:00308102 C:\World of Warcraft\Wow.exe
00645617 7C866A28 0001:00244617 C:\World of Warcraft\Wow.exe
7BC738DE 7C866A38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 7C866AD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7C8673C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7C8674C8 0000:00000000 <unknown>

--- Thread ID: 27 ---
7B890932 7C9775C0 0001:0006F932 C:\windows\system32\KERNEL32.dll
7B890975 7C9775E0 0001:0006F975 C:\windows\system32\KERNEL32.dll
00749C3D 7C9775EC 0001:00348C3D C:\World of Warcraft\Wow.exe
004584BD 7C977A0C 0001:000574BD C:\World of Warcraft\Wow.exe
00645617 7C977A28 0001:00244617 C:\World of Warcraft\Wow.exe
7BC738DE 7C977A38 0001:000628DE C:\windows\system32\ntdll.dll
7BC75032 7C977AD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7C9783C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7C9784C8 0000:00000000 <unknown>

--- Thread ID: 26 ---
7BC71EA5 7CAC782C 0001:00060EA5 C:\windows\system32\ntdll.dll
7BC721A2 7CAC785C 0001:000611A2 C:\windows\system32\ntdll.dll
7B890622 7CAC799C 0001:0006F622 C:\windows\system32\KERNEL32.dll
7B89081C 7CAC79BC 0001:0006F81C C:\windows\system32\KERNEL32.dll

--- Thread ID: 25 ---
7B890932 7CBD89A4 0001:0006F932 C:\windows\system32\KERNEL32.dll
7B890975 7CBD89C4 0001:0006F975 C:\windows\system32\KERNEL32.dll
0065EF34 7CBD8A20 0001:0025DF34 C:\World of Warcraft\Wow.exe
0075FDD4 7CBD8A38 0001:0035EDD4 C:\World of Warcraft\Wow.exe
7BC75032 7CBD8AD8 0001:00064032 C:\windows\system32\ntdll.dll
7BC7522D 7CBD93C8 0001:0006422D C:\windows\system32\ntdll.dll
B7F0B50F 7CBD94C8 0000:00000000 <unknown>

--- Thread ID: 9 [Current Thread] ---
00733085 0032F428 0001:00332085 C:\World of Warcraft\Wow.exe
007332B3 0032F444 0001:003322B3 C:\World of Warcraft\Wow.exe
00733032 0032F45C 0001:00332032 C:\World of Warcraft\Wow.exe
007332C7 0032F474 0001:003322C7 C:\World of Warcraft\Wow.exe
00732F4E 0032F490 0001:00331F4E C:\World of Warcraft\Wow.exe
007332F5 0032F4B0 0001:003322F5 C:\World of Warcraft\Wow.exe
00732FF9 0032F4C8 0001:00331FF9 C:\World of Warcraft\Wow.exe
007332B3 0032F4E4 0001:003322B3 C:\World of Warcraft\Wow.exe
00732F4E 0032F500 0001:00331F4E C:\World of Warcraft\Wow.exe
007332F5 0032F520 0001:003322F5 C:\World of Warcraft\Wow.exe
00733F36 0032FA94 0001:00332F36 C:\World of Warcraft\Wow.exe
0073661D 0032FAB0 0001:0033561D C:\World of Warcraft\Wow.exe
00739BCF 0032FB18 0001:00338BCF C:\World of Warcraft\Wow.exe
007368C7 0032FB34 0001:003358C7 C:\World of Warcraft\Wow.exe
0072EB26 0032FB48 0001:0032DB26 C:\World of Warcraft\Wow.exe
00735C73 0032FBA4 0001:00334C73 C:\World of Warcraft\Wow.exe
00736A89 0032FBCC 0001:00335A89 C:\World of Warcraft\Wow.exe
0072EB7F 0032FBF8 0001:0032DB7F C:\World of Warcraft\Wow.exe
0070763B 0032FC68 0001:0030663B C:\World of Warcraft\Wow.exe
007077A0 0032FC84 0001:003067A0 C:\World of Warcraft\Wow.exe
00437859 0032FCA0 0001:00036859 C:\World of Warcraft\Wow.exe
0043C313 0032FCB0 0001:0003B313 C:\World of Warcraft\Wow.exe
0043CC92 0032FCD0 0001:0003BC92 C:\World of Warcraft\Wow.exe
0043D0F8 0032FCE0 0001:0003C0F8 C:\World of Warcraft\Wow.exe
00447870 0032FDAC 0001:00046870 C:\World of Warcraft\Wow.exe
0042B42B 0032FDDC 0001:0002A42B C:\World of Warcraft\Wow.exe
00428879 0032FE54 0001:00027879 C:\World of Warcraft\Wow.exe
00429D61 0032FE6C 0001:00028D61 C:\World of Warcraft\Wow.exe
00406898 0032FF08 0001:00005898 C:\World of Warcraft\Wow.exe
7B878C38 0032FFE8 0001:00057C38 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 21/21 threads...

--- Thread ID: 49 ---
7B890932 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x7A898A14,0x007F36E8)
7B890975 KERNEL32.dll Sleep+37 (0x0000000A,0x008020C5,0x0000000A,0x06087FA8)
007FDB00 Wow.exe      <unknown symbol>+0 (0x06087FA8,0x00802057,0x7A898AD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x00802057,0x06087FA8,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7A898B0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FF80FB8,0x7A899B90,0x7A899B90,0x7A899B90)
B7F0B50F              start_thread+191 (0x7A899B90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 48 ---
7B890932 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x00000000,0x00000002)
7B890975 KERNEL32.dll Sleep+37 (0x0000000A,0x008020C5,0x0000000A,0x05F1C288)
007FDB00 Wow.exe      <unknown symbol>+0 (0x05F1C288,0x00802057,0x7A9A9AD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x00802057,0x05F1C288,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7A9A9B0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FF84FB8,0x7A9AAB90,0x7A9AAB90,0x7A9AAB90)
B7F0B50F              start_thread+191 (0x7A9AAB90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 47 ---
7BC71EA5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x78ADF8B4,0x00000004,0x78ADF9B4)
7BC721A2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x78ADF8B4,0x00000000,0x00000000)
7B890622 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x78ADF9F4,0x00000000,0x00000064)
7B89081C KERNEL32.dll WaitForSingleObject+60 (0x00002258,0x00000064,0x78ADFA0C,0x00424E66)
00649400 Wow.exe      <unknown symbol>+0 (0x00000064,0x00424E50,0x78ADFA28,0x00645617)
00424E66 Wow.exe      <unknown symbol>+0 (0x07F80C50,0x006455E0,0x07F80128,0x7BC94FF4)
00645617 Wow.exe      <unknown symbol>+0 (0x0000225C,0x006455E0,0x78ADFAD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x006455E0,0x07F80128,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x78ADFB0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FF88FB8,0x78AE0B90,0x78AE0B90,0x78AE0B90)
B7F0B50F              start_thread+191 (0x78AE0B90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 46 ---
7BC71EA5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x78BF0694,0x00000004,0x00000000)
7BC721A2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x78BF0694,0x00000000,0x00000000)
7B890622 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x78BF080C,0x00000000,0xFFFFFFFF)
7D25336B winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x78BF080C,0xFFFFFFFF,0x00000000)
7ED1C315 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x78BF09D4,0xFFFFFFFF,0x00000000)
7ED1C37F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x78BF09D4,0x00000000,0xFFFFFFFF)
006771C8 Wow.exe      <unknown symbol>+0 (0x012FB068,0x7BC738DE,0x012FB068,0x0075FD55)
0075FDD4 Wow.exe      <unknown symbol>+0 (0x0075FD55,0x012FB068,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x78BF0B0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FF8CFB8,0x78BF1B90,0x78BF1B90,0x78BF1B90)
B7F0B50F              start_thread+191 (0x78BF1B90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 45 ---
7BC71EA5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x7A001694,0x00000004,0x00000000)
7BC721A2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x7A001694,0x00000000,0x00000000)
7B890622 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x7A00180C,0x00000000,0xFFFFFFFF)
7D25336B winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x7A00180C,0xFFFFFFFF,0x00000000)
7ED1C315 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x7A0019D4,0xFFFFFFFF,0x00000000)
7ED1C37F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x7A0019D4,0x00000000,0xFFFFFFFF)
006771C8 Wow.exe      <unknown symbol>+0 (0x012FABF0,0x7BC738DE,0x012FABF0,0x0075FD55)
0075FDD4 Wow.exe      <unknown symbol>+0 (0x0075FD55,0x012FABF0,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7A001B0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FF90FB8,0x7A002B90,0x7A002B90,0x7A002B90)
B7F0B50F              start_thread+191 (0x7A002B90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 44 ---
7BC71EA5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x7A6A88C0,0x00000004,0x00000000)
7BC721A2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7A6A88C0,0x00000000,0x00000000)
7B890622 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x7A6A8A00,0x00000000,0xFFFFFFFF)
7B89081C KERNEL32.dll WaitForSingleObject+60 (0x0000221C,0xFFFFFFFF,0x07DD7424,0x007FDC2B)
0083544E Wow.exe      <unknown symbol>+0 (0x07DD7424,0x00802057,0x7A6A8AD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x00802057,0x07DD7424,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7A6A8B0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FF94FB8,0x7A6A9B90,0x7A6A9B90,0x7A6A9B90)
B7F0B50F              start_thread+191 (0x7A6A9B90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 43 ---
7BC71EA5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x7ABBA694,0x00000004,0x00000000)
7BC721A2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x7ABBA694,0x00000000,0x00000000)
7B890622 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x7ABBA80C,0x00000000,0xFFFFFFFF)
7D25336B winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x7ABBA80C,0xFFFFFFFF,0x00000000)
7ED1C315 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x7ABBA9D4,0xFFFFFFFF,0x00000000)
7ED1C37F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x7ABBA9D4,0x00000000,0xFFFFFFFF)
006771C8 Wow.exe      <unknown symbol>+0 (0x012FA778,0x7BC738DE,0x012FA778,0x0075FD55)
0075FDD4 Wow.exe      <unknown symbol>+0 (0x0075FD55,0x012FA778,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7ABBAB0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FF98FB8,0x7ABBBB90,0x7ABBBB90,0x7ABBBB90)
B7F0B50F              start_thread+191 (0x7ABBBB90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 42 ---
7BC71EA5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x7B4CB8C0,0x00000004,0x00000000)
7BC721A2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7B4CB8C0,0x00000000,0x00000000)
7B890622 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x7B4CBA00,0x00000000,0xFFFFFFFF)
7B89081C KERNEL32.dll WaitForSingleObject+60 (0x000021F0,0xFFFFFFFF,0x05EFD824,0x007FDC2B)
0083544E Wow.exe      <unknown symbol>+0 (0x05EFD824,0x00802057,0x7B4CBAD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x00802057,0x05EFD824,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7B4CBB0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FF9CFB8,0x7B4CCB90,0x7B4CCB90,0x7B4CCB90)
B7F0B50F              start_thread+191 (0x7B4CCB90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 36 ---
7BC71EA5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x7B7FE694,0x00000004,0x00000000)
7BC721A2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x7B7FE694,0x00000000,0x00000000)
7B890622 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x7B7FE80C,0x00000000,0xFFFFFFFF)
7D25336B winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x7B7FE80C,0xFFFFFFFF,0x00000000)
7ED1C315 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x7B7FE9D4,0xFFFFFFFF,0x00000000)
7ED1C37F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x7B7FE9D4,0x00000000,0xFFFFFFFF)
006771C8 Wow.exe      <unknown symbol>+0 (0x012F9350,0x7BC738DE,0x012F9350,0x0075FD55)
0075FDD4 Wow.exe      <unknown symbol>+0 (0x0075FD55,0x012F9350,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7B7FEB0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x7B7FFB90,0x7B7FFB90,0x7B7FFB90)
B7F0B50F              start_thread+191 (0x7B7FFB90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 35 ---
7BC71EA5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000002,0x7BAED66C,0x00000004,0x7BAED76C)
7BC721A2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000002,0x7BAED66C,0x00000000,0x00000000)
7B890622 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000002,0x7BAED8C8,0x00000000,0x000001F4)
7B89077A KERNEL32.dll WaitForMultipleObjects+58 (0x00000002,0x7BAED8C8,0x00000000,0x000001F4)
00425ACB Wow.exe      <unknown symbol>+0 (0x00425360,0x0042536B,0x7BAEDA28,0x00645617)
00425328 Wow.exe      <unknown symbol>+0 (0x05710008,0x006455E0,0x056BF2C8,0x7BC94FF4)
00645617 Wow.exe      <unknown symbol>+0 (0x000021AC,0x006455E0,0x7BAEDAD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x006455E0,0x056BF2C8,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7BAEDB0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x7BAEEB90,0x7BAEEB90,0x7BAEEB90)
B7F0B50F              start_thread+191 (0x7BAEEB90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 34 ---
7BC71EA5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x7BBFE8A0,0x00000004,0x7BBFE9A0)
7BC721A2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7BBFE8A0,0x00000000,0x00000000)
7B890622 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x7BBFE9E0,0x00000000,0x000003E8)
7B89081C KERNEL32.dll WaitForSingleObject+60 (0x0000211C,0x000003E8,0x7BBFEA00,0x00425215)
00649400 Wow.exe      <unknown symbol>+0 (0x000003E8,0x05710018,0x00425340,0x00000022)
00425215 Wow.exe      <unknown symbol>+0 (0x00000000,0x7BBFEA28,0x00645617,0x05710018)
00425351 Wow.exe      <unknown symbol>+0 (0x05710018,0x006455E0,0x056BF2A8,0x7BC94FF4)
00645617 Wow.exe      <unknown symbol>+0 (0x000021A8,0x006455E0,0x7BBFEAD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x006455E0,0x056BF2A8,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7BBFEB0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x7BBFFB90,0x7BBFFB90,0x7BBFFB90)
B7F0B50F              start_thread+191 (0x7BBFFB90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 33 ---
7B890932 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x7BDEDA14,0x007F36E8)
7B890975 KERNEL32.dll Sleep+37 (0x0000000A,0x008020C5,0x0000000A,0x04F77FA8)
007FDB00 Wow.exe      <unknown symbol>+0 (0x04F77FA8,0x00802057,0x7BDEDAD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x00802057,0x04F77FA8,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7BDEDB0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x7BDEEB90,0x7BDEEB90,0x7BDEEB90)
B7F0B50F              start_thread+191 (0x7BDEEB90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 32 ---
7B890932 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x00000000,0x00000002)
7B890975 KERNEL32.dll Sleep+37 (0x0000000A,0x008020C5,0x0000000A,0x04FC6288)
007FDB00 Wow.exe      <unknown symbol>+0 (0x04FC6288,0x00802057,0x7BEFEAD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x00802057,0x04FC6288,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7BEFEB0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x7BEFFB90,0x7BEFFB90,0x7BEFFB90)
B7F0B50F              start_thread+191 (0x7BEFFB90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 31 ---
7B890932 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x7C4D6A14,0x007F36E8)
7B890975 KERNEL32.dll Sleep+37 (0x0000000A,0x008020C5,0x0000000A,0x04F87FA8)
007FDB00 Wow.exe      <unknown symbol>+0 (0x04F87FA8,0x00802057,0x7C4D6AD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x00802057,0x04F87FA8,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7C4D6B0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x7C4D7B90,0x7C4D7B90,0x7C4D7B90)
B7F0B50F              start_thread+191 (0x7C4D7B90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 30 ---
7B890932 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x00000000,0x00000002)
7B890975 KERNEL32.dll Sleep+37 (0x0000000A,0x008020C5,0x0000000A,0x04F67288)
007FDB00 Wow.exe      <unknown symbol>+0 (0x04F67288,0x00802057,0x7C5E7AD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x00802057,0x04F67288,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7C5E7B0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FFC0FB8,0x7C5E8B90,0x7C5E8B90,0x7C5E8B90)
B7F0B50F              start_thread+191 (0x7C5E8B90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 29 ---
7EE0E967 winmm.dll    <unknown symbol>+0 (0x00000000,0x7EE0E730,0x7C708AD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x7EE0E730,0x00000000,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7C708B0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FFC4FB8,0x7C709B90,0x7C709B90,0x7C709B90)
B7F0B50F              start_thread+191 (0x7C709B90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 28 ---
7BC71EA5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x7C8668AC,0x00000004,0x00000000)
7BC721A2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7C8668AC,0x00000000,0x00000000)
7B890622 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x7C8669EC,0x00000000,0xFFFFFFFF)
7B89081C KERNEL32.dll WaitForSingleObject+60 (0x00002090,0xFFFFFFFF,0x7C866A0C,0x00709102)
00649400 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x0000001C,0x00E1E060,0x007090A0)
00709102 Wow.exe      <unknown symbol>+0 (0x00E1E060,0x006455E0,0x025F3EC8,0x7BC94FF4)
00645617 Wow.exe      <unknown symbol>+0 (0x000020E4,0x006455E0,0x7C866AD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x006455E0,0x025F3EC8,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7C866B0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x7C867B90,0x7C867B90,0x7C867B90)
B7F0B50F              start_thread+191 (0x7C867B90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 27 ---
7B890932 KERNEL32.dll SleepEx+50 (0x00000001,0x00000000,0x00000000,0x00000000)
7B890975 KERNEL32.dll Sleep+37 (0x00000001,0x7C977A0C,0x004584BD,0x00000001)
00749C3D Wow.exe      <unknown symbol>+0 (0x00000001,0x00000000,0x004582E0,0x0000001B)
004584BD Wow.exe      <unknown symbol>+0 (0x00000000,0x006455E0,0x025F2968,0x7BC94FF4)
00645617 Wow.exe      <unknown symbol>+0 (0x000020E0,0x006455E0,0x7C977AD8,0x7BC75032)
7BC738DE ntdll.dll    call_thread_entry_point+14 (0x006455E0,0x025F2968,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7C977B0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x7C978B90,0x7C978B90,0x7C978B90)
B7F0B50F              start_thread+191 (0x7C978B90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 26 ---
7BC71EA5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x7CAC7884,0x00000004,0x00000000)
7BC721A2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7CAC7884,0x00000000,0x00000000)
7B890622 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x7CAC79C4,0x00000000,0xFFFFFFFF)
7B89081C KERNEL32.dll WaitForSingleObject+60 (0x000020C8,0xFFFFFFFF,0x7BC94FF4,0x0075FD55)
0065D313 Wow.exe      <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 25 ---
7B890932 KERNEL32.dll SleepEx+50 (0x00000064,0x00000000,0x7CBD89C4,0x7B855CE7)
7B890975 KERNEL32.dll Sleep+37 (0x00000064,0x0075FD55,0x7BC94FF4,0x012013F0)
0065EF34 Wow.exe      <unknown symbol>+0 (0x012035D8,0x7BC738DE,0x012035D8,0x012035D8)
0075FDD4 Wow.exe      <unknown symbol>+0 (0x0075FD55,0x012035D8,0x7BCB0900,0xB7F100C1)
7BC75032 ntdll.dll    <unknown symbol>+0 (0x7CBD8B0C,0x00000000,0x00000000,0x00000000)
7BC7522D ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x7CBD9B90,0x7CBD9B90,0x7CBD9B90)
B7F0B50F              start_thread+191 (0x7CBD9B90,0x00000000,0x00000000,0x00000000)
B7E877EE              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 9 [Current Thread] ---
00733085 Wow.exe      <unknown symbol>+0 (0x008D7269,0xFFFFFFFF,0x00000000,0x0032F540)
007332B3 Wow.exe      <unknown symbol>+0 (0x0032F540,0x076F39C2,0x008D7265,0x008D7264)
00733032 Wow.exe      <unknown symbol>+0 (0x008D7265,0x008D7264,0x00000001,0x0032F540)
007332C7 Wow.exe      <unknown symbol>+0 (0x0032F540,0x076F39C2,0x008D7264,0x008D7263)
00732F4E Wow.exe      <unknown symbol>+0 (0x076F39C1,0x008D7261,0x008D7263,0x00000001)
007332F5 Wow.exe      <unknown symbol>+0 (0x0032F540,0x076F39C1,0x008D7261,0x008D7260)
00732FF9 Wow.exe      <unknown symbol>+0 (0x008D7261,0xFFFFFFFF,0x008D7260,0x00000001)
007332B3 Wow.exe      <unknown symbol>+0 (0x0032F540,0x076F39C1,0x008D7260,0x008D725F)
00732F4E Wow.exe      <unknown symbol>+0 (0x076F39C0,0x008D7258,0x008D725F,0x076F39C0)
007332F5 Wow.exe      <unknown symbol>+0 (0x0032F540,0x076F39C0,0x008D7258,0x00733DE0)
00733F36 Wow.exe      <unknown symbol>+0 (0x03D0CC08,0x00733DE0,0x00000000,0x1C53C168)
0073661D Wow.exe      <unknown symbol>+0 (0x00000160,0x1C53C168,0xFFFFFFFF,0x00000000)
00739BCF Wow.exe      <unknown symbol>+0 (0x03D0CC08,0x00000005,0x03D0CC08,0x007368C7)
007368C7 Wow.exe      <unknown symbol>+0 (0x03D0CC08,0x1C53C058,0x00000000,0x0032FBA4)
0072EB26 Wow.exe      <unknown symbol>+0 (0x03D0CC08,0x0032FBF0,0x03D0CC08,0x00000000)
00735C73 Wow.exe      <unknown symbol>+0 (0x03D0CC08,0x0072EB10,0x0032FBF0,0x00000000)
00736A89 Wow.exe      <unknown symbol>+0 (0x01D0CC08,0x0072EB10,0x0032FBF0,0x00000050)
0072EB7F Wow.exe      <unknown symbol>+0 (0x03D0CC08,0x00000002,0x00000000,0xFFFFFFFC)
0070763B Wow.exe      <unknown symbol>+0 (0x00008EFD,0x0D5A3808,0x00000001,0x00000000)
007077A0 Wow.exe      <unknown symbol>+0 (0x0D5A3938,0x00000001,0x00000000,0x08ED6C08)
00437859 Wow.exe      <unknown symbol>+0 (0x3CBC6A80,0x07DD4AA8,0x0032FCD0,0x0043CC92)
0043C313 Wow.exe      <unknown symbol>+0 (0x3CBC6A80,0x025DFD08,0x05F12008,0x07DD3888)
0043CC92 Wow.exe      <unknown symbol>+0 (0x3CBC6A80,0x07DD38A0,0x0032FDAC,0x00447870)
0043D0F8 Wow.exe      <unknown symbol>+0 (0x00000000,0x07DD3890,0x07DD38A0,0x3CBC6A80)
00447870 Wow.exe      <unknown symbol>+0 (0x00000000,0x00000000,0x01467408,0x00000000)
0042B42B Wow.exe      <unknown symbol>+0 (0x01467408,0x00000011,0x00000000,0x00429C7D)
00428879 Wow.exe      <unknown symbol>+0 (0x00000001,0x00406858,0x00000001,0x00000001)
00429D61 Wow.exe      <unknown symbol>+0 (0x0040A4E9,0x00400000,0x00000000,0x001148EF)
00406898 Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B878C38 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7F44D37              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00EC8000  C:\World of Warcraft\Wow.exe
0x10000000 - 0x10069000  C:\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B940000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCB1000  C:\windows\system32\ntdll.dll
0x7BFC0000 - 0x7C000000  C:\windows\system32\dbghelp.dll
0x7C710000 - 0x7C757000  C:\windows\system32\dsound.dll
0x7CFA0000 - 0x7CFAD000  C:\windows\system32\psapi.dll
0x7CFE0000 - 0x7D011000  C:\windows\system32\uxtheme.dll
0x7D0B0000 - 0x7D0BF000  C:\windows\system32\midimap.dll
0x7D1A0000 - 0x7D1C8000  C:\windows\system32\winealsa.drv
0x7D200000 - 0x7D213000  C:\windows\system32\msacm32.drv
0x7D220000 - 0x7D2AF000  C:\windows\system32\winex11.drv
0x7D420000 - 0x7D470000  C:\windows\system32\rpcrt4.dll
0x7D490000 - 0x7D582000  C:\windows\system32\ole32.dll
0x7D590000 - 0x7D5AB000  C:\windows\system32\msacm32.dll
0x7D5B0000 - 0x7D5D8000  C:\windows\system32\ws2_32.dll
0x7D5E0000 - 0x7D69F000  C:\windows\system32\comctl32.dll
0x7D6B0000 - 0x7D829000  C:\windows\system32\shell32.dll
0x7D840000 - 0x7D887000  C:\windows\system32\shlwapi.dll
0x7D890000 - 0x7D8AA000  C:\windows\system32\mpr.dll
0x7D8B0000 - 0x7D8FB000  C:\windows\system32\wininet.dll
0x7D900000 - 0x7D91C000  C:\windows\system32\imm32.dll
0x7D920000 - 0x7D931000  C:\windows\system32\lz32.dll
0x7D940000 - 0x7DA54000  C:\windows\system32\wined3d.dll
0x7DA60000 - 0x7DA85000  C:\windows\system32\d3d9.dll
0x7EAF0000 - 0x7EAFB000  C:\windows\system32\version.dll
0x7EB10000 - 0x7EB92000  C:\windows\system32\opengl32.dll
0x7EBA0000 - 0x7EBE7000  C:\windows\system32\advapi32.dll
0x7EC00000 - 0x7EC88000  C:\windows\system32\gdi32.dll
0x7ECA0000 - 0x7EDD7000  C:\windows\system32\user32.dll
0x7EDE0000 - 0x7EE6B000  C:\windows\system32\winmm.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 00733085)

00733085: 12 83 E9 04  83 C2 04 83  C0 04 83 F9  04 73 EC 85  .............s..


Stack: 1024 bytes starting at (ESP = 0032F428)

* = addr                            **                                *       
0032F420: 69 72 8D 00  67 72 8D 00  44 F4 32 00  B3 32 73 00  ir..gr..D.2..2s.
0032F430: 69 72 8D 00  FF FF FF FF  00 00 00 00  40 F5 32 00  ir..........@.2.
0032F440: C2 39 6F 07  5C F4 32 00  32 30 73 00  40 F5 32 00  .9o.\.2.20s.@.2.
0032F450: C2 39 6F 07  65 72 8D 00  64 72 8D 00  74 F4 32 00  .9o.er..dr..t.2.
0032F460: C7 32 73 00  65 72 8D 00  64 72 8D 00  01 00 00 00  .2s.er..dr......
0032F470: 40 F5 32 00  90 F4 32 00  4E 2F 73 00  40 F5 32 00  @.2...2.N/s.@.2.
0032F480: C2 39 6F 07  64 72 8D 00  63 72 8D 00  61 72 8D 00  .9o.dr..cr..ar..
0032F490: B0 F4 32 00  F5 32 73 00  C1 39 6F 07  61 72 8D 00  ..2..2s..9o.ar..
0032F4A0: 63 72 8D 00  01 00 00 00  40 F5 32 00  C1 39 6F 07  cr......@.2..9o.
0032F4B0: C8 F4 32 00  F9 2F 73 00  40 F5 32 00  C1 39 6F 07  ..2../s.@.2..9o.
0032F4C0: 61 72 8D 00  60 72 8D 00  E4 F4 32 00  B3 32 73 00  ar..`r....2..2s.
0032F4D0: 61 72 8D 00  FF FF FF FF  60 72 8D 00  01 00 00 00  ar......`r......
0032F4E0: 40 F5 32 00  00 F5 32 00  4E 2F 73 00  40 F5 32 00  @.2...2.N/s.@.2.
0032F4F0: C1 39 6F 07  60 72 8D 00  5F 72 8D 00  58 72 8D 00  .9o.`r.._r..Xr..
0032F500: 20 F5 32 00  F5 32 73 00  C0 39 6F 07  58 72 8D 00   .2..2s..9o.Xr..
0032F510: 5F 72 8D 00  C0 39 6F 07  08 CC D0 03  C0 39 6F 07  _r...9o......9o.
0032F520: 94 FA 32 00  36 3F 73 00  40 F5 32 00  C0 39 6F 07  ..2.6?s.@.2..9o.
0032F530: 58 72 8D 00  E0 3D 73 00  08 CC D0 03  08 CC D0 03  Xr...=s.........
0032F540: C0 39 6F 07  C4 39 6F 07  08 CC D0 03  02 00 00 00  .9o..9o.........
0032F550: C1 39 6F 07  01 00 00 00  C2 39 6F 07  00 00 00 00  .9o......9o.....
0032F560: 00 00 1A 43  0C BF 80 C1  00 00 16 C3  A1 49 32 43  ...C.........I2C
0032F570: 00 00 A0 C0  00 00 23 C3  00 00 1A 43  0C BF 80 C1  ......#....C....
0032F580: 00 00 18 C3  A1 49 32 43  00 00 A0 C0  28 1E 8C C0  .....I2C....(...
0032F590: 00 00 50 C1  00 54 36 3E  0C F6 32 00  24 31 6C 00  ..P..T6>..2.$1l.
0032F5A0: 00 26 0F C1  00 00 30 C1  D0 F5 32 00  A0 F6 32 00  .&....0...2...2.
0032F5B0: 6C E4 3C 11  4C F9 32 00  60 F2 20 C3  00 00 1A 43  l.<.L.2.`. ....C
0032F5C0: D6 0A 9F C1  00 00 23 C3  33 07 1A 43  D2 9C A5 C1  ......#.3..C....
0032F5D0: 00 00 23 C3  00 00 1A 43  0C BF 80 C1  00 00 16 C3  ..#....C........
0032F5E0: A1 49 32 43  00 00 A0 C0  00 00 23 C3  00 00 13 43  .I2C......#....C
0032F5F0: 0C BF 80 C1  00 00 16 C3  00 00 1A 43  00 00 A0 C0  ...........C....
0032F600: 60 F2 20 C3  00 00 1A 43  D6 0A 9F C1  80 F6 32 00  `. ....C......2.
0032F610: FA 2F 6C 00  00 88 19 BE  A0 51 49 00  66 F6 32 00  ./l......QI.f.2.
0032F620: 16 00 00 00  0A 00 00 00  54 FA 32 00  81 48 64 00  ........T.2..Hd.
0032F630: 50 F6 32 00  16 00 00 00  00 00 00 00  40 35 D7 00  P.2.........@5..
0032F640: 90 48 64 00  65 00 00 00  00 00 00 00  32 B3 BF 07  .Hd.e.......2...
0032F650: 07 00 00 00  C3 39 6F 07  53 45 4D 49  4C 49 54 41  .....9o.SEMILITA
0032F660: 52 59 54 49  4D 45 00 49  08 CC D0 03  03 00 00 00  RYTIME.I........
0032F670: 7E F6 32 00  00 00 00 00  08 CC D0 03  39 3A 8C 3E  ~.2.........9:.>
0032F680: F4 F6 32 00  C6 30 6C 00  C0 33 DB 40  60 E6 E0 40  ..2..0l..3.@`..@
0032F690: D0 F6 32 00  08 F8 32 00  91 15 DD B7  4C F9 32 00  ..2...2.....L.2.
0032F6A0: 00 00 16 C3  9E D9 19 43  F4 7F 8B 7B  40 74 15 06  .......C...{@t..
0032F6B0: 90 F7 32 00  4F F8 89 7B  E0 F6 32 00  00 00 00 00  ..2.O..{..2.....
0032F6C0: 0C BF 80 C1  00 00 0F C3  A1 49 32 43  00 00 A0 C0  .........I2C....
0032F6D0: 00 00 23 C3  F8 FE 32 00  E0 F5 89 7B  00 00 16 C3  ..#...2....{....
0032F6E0: F4 7F 8B 7B  40 74 15 06  00 37 D7 00  90 F7 32 00  ...{@t...7....2.
0032F6F0: DB 71 4D E9  2C 9F 50 9F  00 00 00 00  00 00 E0 40  .qM.,.P........@
0032F700: 33 33 B3 3E  44 F7 32 00  FC F7 32 00  2C DE 3C 11  33.>D.2...2.,.<.
0032F710: 4C F9 32 00  00 00 0F C3  13 C1 19 43  E1 39 4B C1  L.2........C.9K.
0032F720: 00 00 23 C3  33 07 1A 43  D2 9C A5 C1  00 00 0F C3  ..#.3..C........
0032F730: 07 00 00 00  5C 37 D7 00  80 48 99 1D  58 F7 32 00  ....\7...H..X.2.
0032F740: 84 39 64 00  00 37 D7 00  40 74 15 06  05 00 00 00  .9d..7..@t......
0032F750: 78 F7 32 00  D1 3B 64 00  40 74 15 06  05 00 00 00  x.2..;d.@t......
0032F760: 10 00 00 00  00 37 D7 00  10 00 00 00  2C 3B D7 00  .....7......,;..
0032F770: 5C 37 D7 00  0F 42 C3 7B  98 F7 32 00  2C 3B D7 00  \7...B.{..2.,;..
0032F780: 98 F7 32 00  DF 40 64 00  2C 3B D7 00  10 00 00 00  ..2..@d.,;......
0032F790: 1C F0 12 06  1C 28 C3 08  10 00 00 00  1C 42 64 00  .....(.......Bd.
0032F7A0: 48 74 15 06  00 00 00 00  10 00 00 00  C4 F7 32 00  Ht............2.
0032F7B0: 1E BA 73 00  D0 06 A0 0C  91 15 DD B7  08 CC D0 03  ..s.............
0032F7C0: 43 B9 87 DB  62 45 F9 BF  F4 7F 8B 7B  E0 CD 28 06  C...bE.....{..(.
0032F7D0: B0 F8 32 00  4F F8 89 7B  00 F8 32 00  00 00 00 00  ..2.O..{..2.....
0032F7E0: F8 F7 32 00  30 4A 43 00  04 F8 32 00  55 C0 73 00  ..2.0JC...2.U.s.
0032F7F0: 00 00 00 00  F8 FE 32 00  E0 F5 89 7B  18 F8 32 00  ......2....{..2.
0032F800: F4 7F 8B 7B  E0 CD 28 06  00 37 D7 00  B0 F8 32 00  ...{..(..7....2.
0032F810: DB B1 4F E9  2C 9F 50 9F  00 00 00 00  38 F8 32 00  ..O.,.P.....8.2.
0032F820: FC C0 73 00  20 38 14 0B  A0 17 14 0B  D8 C0 53 1C  ..s. 8........S.


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
Processor Level:        15
Processor Revision:     27394

Percent memory used:    48
Total physical memory:  2122350592
Free Memory:            1092763648
Page file:              3150467072
Total virtual memory:   2147352575

```

And console output

```
luki@luki-desktop:~/Pulpit$ ./World\ of\ Warcraft.sh 
fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
fixme:powrprof:DllMain (0x7cfa0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cfa0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x32eda4,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32ebc8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f144,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x145790,0x145690): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x374028c4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x20028, 0x13ff30): stub
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x32d194,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d200,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32eff0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f444,0x00000000), stub!
luki@luki-desktop:~/Pulpit$ 


```

I can only run WoW with OpenGL.
Any suggestions? :)

---

### Post by Eviljim on 2009-02-09
Error #132 is a very generic one, with no actual reference to the offending bit of hardware/software.

It is usually corrected by re-installing WoW, however this does not always work.

You have'nt told us your PC spec, but if you have an ATi card, then OpenGL is the only way you will be able to play WoW.

---

