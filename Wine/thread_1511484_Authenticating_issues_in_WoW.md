---
title: "Authenticating issues in WoW"
date: 2010-06-16
forum: Wine
---

### Post by allegedlyyours on 2010-06-16
I am trying to run WoW through Wine, but I seem to be running into some issues. I've followed the tutorial at
 
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

...up until the "configuration" section. First issue is here: the config.wtf file isn't saved, so I can open it to edit it but when I hit "save" I get an error saying the file could not be located. 

Second issue I believe is the reason for the first: When I open the game, type in my username and password, I get stuck at the "authenticating" screen. 

I've searched around the forums and not found a whole lot...but I'm really really new at this whole Linux thing (literally, I'm on my 4th day or so, lol) so maybe I'm missing something. I know someone's going to probably ask for some of my system specs, but I really have no idea how to find any information in Ubuntu so if someone could kinda hold my hand through this, I'd really appreciate it.

---

### Post by Sammi on 2010-06-19
WoW should create a config.wtf file when you launch it the first time.

But please elaborate on exactly what your authentication issue is. What happens?

---

### Post by allegedlyyours on 2010-06-19
Hey Sammi, thanks for your reply. I think it's not making the config file because I've never successfully logged in. When I try, I just end up at "authenticating" for around 15 minutes, then it gives me an "log in unsuccessful" message. 

I found the issue: when you log into WoW now, it requires a battle.net account. The version of the game I have is almost 4 years old, so the login screen wasn't allowing for the "@" symbol in my battle.net account name. Since I couldn't log in, the patches couldn't download to update the login screen, and it ended up being a vicious circle. lol.

I think I found a work-around though...I downloaded the entire game to my win machine and transferred it over. It seems to have installed ok, I'm just patching now. Hopefully this works. 

Thanks!

---

### Post by allegedlyyours on 2010-06-20
Well, apparently that didn't work. Here's what I've got going on now:

I installed the game from the Blizzard website and patched it, so it should be up to date. When I click the desktop icon, it starts up, runs through the cinematics and then as soon as it finishes, I get a white screen and two new windows with these errors:

"This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program: C:\Program Files\World of Warcraft\WoW.exe
Exception: 0xC0000005 (ACCESS_VIOLATION) at 0073:68FAD370

The instruction at "0x68FAD370" referenced memory at "0x0000000".

Press OK to terminate the application."


and the other is a long string:
```

==============================================================================
World of WarCraft (build 11723)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Jun 20, 2010  7:22:11.432 PM
User:     emily
Computer: Desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:    C:\Program Files\World of Warcraft\Wow.exe
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0073:68F6D370

The instruction at "0x68F6D370" referenced memory at "0x00000000".
The memory could not be "read".


WoWBuild: 11723
Settings: 
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET expansionMovie "0"
SET movie "0"
SET showToolsUI "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "3"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "550.000000"
SET specular "1"
SET particleDensity "0.7"
SET groundEffectDensity "24"
SET projectedTextures "1"

----------------------------------------
               GxInfo
----------------------------------------
GxApi: D3D9
Adapter Count: 1

Adapter 0 (primary):
  Driver: ati2dvag.dll
  Version: 6.15.0008.0006
  Description: Direct3D HAL
  DeviceName: \\.\DISPLAY1

------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000000  EBX=69190FF4  ECX=00000001  EDX=7BF18020  ESI=00000000
EDI=7BF18020  EBP=003AF4C0  ESP=003AF478  EIP=68F6D370  FLG=00010202
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 17/17 threads...

--- Thread ID: 28 ---
7BC76753 0799E5E8 0001:00065753 C:\windows\system32\ntdll.dll
7BC76A43 0799E628 0001:00065A43 C:\windows\system32\ntdll.dll
7B8694D6 0799E778 0001:000584D6 C:\windows\system32\KERNEL32.dll
72226C8C 0799E7B8 0001:00035C8C C:\windows\system32\winex11.drv
68443E48 0799E7F8 0001:00092E48 C:\windows\system32\user32.dll
6840A5CA 0799E9B8 0001:000595CA C:\windows\system32\user32.dll
6840A61F 0799E9E8 0001:0005961F C:\windows\system32\user32.dll
0044C3E6 0799EA14 0001:0004B3E6 C:\Program Files\World of Warcraft\Wow.exe
0044D35A 0799EA28 0001:0004C35A C:\Program Files\World of Warcraft\Wow.exe
0093236F 0799EA60 0001:0053136F C:\Program Files\World of Warcraft\Wow.exe
00932414 0799EA78 0001:00531414 C:\Program Files\World of Warcraft\Wow.exe
7BC6FE40 0799EB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 0799F398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 0799F498 0000:00000000 <unknown>

--- Thread ID: 33 ---
7BC76753 0782E868 0001:00065753 C:\windows\system32\ntdll.dll
7BC76A43 0782E8A8 0001:00065A43 C:\windows\system32\ntdll.dll
7B8694D6 0782E9F8 0001:000584D6 C:\windows\system32\KERNEL32.dll
7B8695EC 0782EA28 0001:000585EC C:\windows\system32\KERNEL32.dll
008EE4B5 0782EA44 0001:004ED4B5 C:\Program Files\World of Warcraft\Wow.exe
008AD949 0782EA54 0001:004AC949 C:\Program Files\World of Warcraft\Wow.exe
008ADF90 0782EA68 0001:004ACF90 C:\Program Files\World of Warcraft\Wow.exe
7BC6FC70 0782EA78 0001:0005EC70 C:\windows\system32\ntdll.dll
7BC6FE40 0782EB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 0782F398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 0782F498 0000:00000000 <unknown>

--- Thread ID: 31 ---
7BC76753 076BE5E8 0001:00065753 C:\windows\system32\ntdll.dll
7BC76A43 076BE628 0001:00065A43 C:\windows\system32\ntdll.dll
7B8694D6 076BE778 0001:000584D6 C:\windows\system32\KERNEL32.dll
72226C8C 076BE7B8 0001:00035C8C C:\windows\system32\winex11.drv
68443E48 076BE7F8 0001:00092E48 C:\windows\system32\user32.dll
6840A5CA 076BE9B8 0001:000595CA C:\windows\system32\user32.dll
6840A61F 076BE9E8 0001:0005961F C:\windows\system32\user32.dll
0044C3E6 076BEA14 0001:0004B3E6 C:\Program Files\World of Warcraft\Wow.exe
0044D35A 076BEA28 0001:0004C35A C:\Program Files\World of Warcraft\Wow.exe
0093236F 076BEA60 0001:0053136F C:\Program Files\World of Warcraft\Wow.exe
00932414 076BEA78 0001:00531414 C:\Program Files\World of Warcraft\Wow.exe
7BC6FE40 076BEB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 076BF398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 076BF498 0000:00000000 <unknown>

--- Thread ID: 32 ---
7BC76753 0754E868 0001:00065753 C:\windows\system32\ntdll.dll
7BC76A43 0754E8A8 0001:00065A43 C:\windows\system32\ntdll.dll
7B8694D6 0754E9F8 0001:000584D6 C:\windows\system32\KERNEL32.dll
7B8695EC 0754EA28 0001:000585EC C:\windows\system32\KERNEL32.dll
008EE4B5 0754EA44 0001:004ED4B5 C:\Program Files\World of Warcraft\Wow.exe
008AD949 0754EA54 0001:004AC949 C:\Program Files\World of Warcraft\Wow.exe
008ADF90 0754EA68 0001:004ACF90 C:\Program Files\World of Warcraft\Wow.exe
7BC6FC70 0754EA78 0001:0005EC70 C:\windows\system32\ntdll.dll
7BC6FE40 0754EB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 0754F398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 0754F498 0000:00000000 <unknown>

--- Thread ID: 12 ---
7BC76753 073DE988 0001:00065753 C:\windows\system32\ntdll.dll
7BC76A43 073DE9C8 0001:00065A43 C:\windows\system32\ntdll.dll
7BC76A9C 073DE9F8 0001:00065A9C C:\windows\system32\ntdll.dll
7BC7BB6F 073DEA68 0001:0006AB6F C:\windows\system32\ntdll.dll
7BC6FC70 073DEA78 0001:0005EC70 C:\windows\system32\ntdll.dll
7BC6FE40 073DEB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 073DF398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 073DF498 0000:00000000 <unknown>

--- Thread ID: 13 ---
7BC76753 0726E988 0001:00065753 C:\windows\system32\ntdll.dll
7BC76A43 0726E9C8 0001:00065A43 C:\windows\system32\ntdll.dll
7BC76A9C 0726E9F8 0001:00065A9C C:\windows\system32\ntdll.dll
7BC7BB6F 0726EA68 0001:0006AB6F C:\windows\system32\ntdll.dll
7BC6FC70 0726EA78 0001:0005EC70 C:\windows\system32\ntdll.dll
7BC6FE40 0726EB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 0726F398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 0726F498 0000:00000000 <unknown>

--- Thread ID: 11 ---
7BC76753 06E2E5E8 0001:00065753 C:\windows\system32\ntdll.dll
7BC76A43 06E2E628 0001:00065A43 C:\windows\system32\ntdll.dll
7B8694D6 06E2E778 0001:000584D6 C:\windows\system32\KERNEL32.dll
72226C8C 06E2E7B8 0001:00035C8C C:\windows\system32\winex11.drv
68443E48 06E2E7F8 0001:00092E48 C:\windows\system32\user32.dll
6840A5CA 06E2E9B8 0001:000595CA C:\windows\system32\user32.dll
6840A61F 06E2E9E8 0001:0005961F C:\windows\system32\user32.dll
0044C3E6 06E2EA14 0001:0004B3E6 C:\Program Files\World of Warcraft\Wow.exe
0044D35A 06E2EA28 0001:0004C35A C:\Program Files\World of Warcraft\Wow.exe
0093236F 06E2EA60 0001:0053136F C:\Program Files\World of Warcraft\Wow.exe
00932414 06E2EA78 0001:00531414 C:\Program Files\World of Warcraft\Wow.exe
7BC6FE40 06E2EB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 06E2F398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 06E2F498 0000:00000000 <unknown>

--- Thread ID: 71 ---
7BC76753 0639E61C 0001:00065753 C:\windows\system32\ntdll.dll
7BC76A43 0639E65C 0001:00065A43 C:\windows\system32\ntdll.dll
7B8694D6 0639E7AC 0001:000584D6 C:\windows\system32\KERNEL32.dll
7B86954A 0639E7DC 0001:0005854A C:\windows\system32\KERNEL32.dll
00468D1B 0639EA34 0001:00067D1B C:\Program Files\World of Warcraft\Wow.exe
004683CE 0639EA40 0001:000673CE C:\Program Files\World of Warcraft\Wow.exe
0055AD7B 0639EA68 0001:00159D7B C:\Program Files\World of Warcraft\Wow.exe
7BC6FC70 0639EA78 0001:0005EC70 C:\windows\system32\ntdll.dll
7BC6FE40 0639EB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 0639F398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 0639F498 0000:00000000 <unknown>

--- Thread ID: 70 ---
7BC76753 0622E84C 0001:00065753 C:\windows\system32\ntdll.dll
7BC76A43 0622E88C 0001:00065A43 C:\windows\system32\ntdll.dll
7B8694D6 0622E9DC 0001:000584D6 C:\windows\system32\KERNEL32.dll
7B8695EC 0622EA0C 0001:000585EC C:\windows\system32\KERNEL32.dll
0055F4D0 0622EA1C 0001:0015E4D0 C:\Program Files\World of Warcraft\Wow.exe
00468505 0622EA34 0001:00067505 C:\Program Files\World of Warcraft\Wow.exe
00468671 0622EA40 0001:00067671 C:\Program Files\World of Warcraft\Wow.exe
0055AD7B 0622EA68 0001:00159D7B C:\Program Files\World of Warcraft\Wow.exe
7BC6FC70 0622EA78 0001:0005EC70 C:\windows\system32\ntdll.dll
7BC6FE40 0622EB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 0622F398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 0622F498 0000:00000000 <unknown>

--- Thread ID: 69 ---
7B869661 060BEA28 0001:00058661 C:\windows\system32\KERNEL32.dll
7B8696A5 060BEA48 0001:000586A5 C:\windows\system32\KERNEL32.dll
008AD7AD 060BEA54 0001:004AC7AD C:\Program Files\World of Warcraft\Wow.exe
008ADFCC 060BEA68 0001:004ACFCC C:\Program Files\World of Warcraft\Wow.exe
7BC6FC70 060BEA78 0001:0005EC70 C:\windows\system32\ntdll.dll
7BC6FE40 060BEB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 060BF398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 060BF498 0000:00000000 <unknown>

--- Thread ID: 68 ---
7B869661 05F4EA28 0001:00058661 C:\windows\system32\KERNEL32.dll
7B8696A5 05F4EA48 0001:000586A5 C:\windows\system32\KERNEL32.dll
008AD7AD 05F4EA54 0001:004AC7AD C:\Program Files\World of Warcraft\Wow.exe
008ADFCC 05F4EA68 0001:004ACFCC C:\Program Files\World of Warcraft\Wow.exe
7BC6FC70 05F4EA78 0001:0005EC70 C:\windows\system32\ntdll.dll
7BC6FE40 05F4EB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 05F4F398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 05F4F498 0000:00000000 <unknown>

--- Thread ID: 67 ---
7B869661 05DDEA28 0001:00058661 C:\windows\system32\KERNEL32.dll
7B8696A5 05DDEA48 0001:000586A5 C:\windows\system32\KERNEL32.dll
008AD7AD 05DDEA54 0001:004AC7AD C:\Program Files\World of Warcraft\Wow.exe
008ADFCC 05DDEA68 0001:004ACFCC C:\Program Files\World of Warcraft\Wow.exe
7BC6FC70 05DDEA78 0001:0005EC70 C:\windows\system32\ntdll.dll
7BC6FE40 05DDEB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 05DDF398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 05DDF498 0000:00000000 <unknown>

--- Thread ID: 66 ---
7B869661 05C6EA28 0001:00058661 C:\windows\system32\KERNEL32.dll
7B8696A5 05C6EA48 0001:000586A5 C:\windows\system32\KERNEL32.dll
008AD7AD 05C6EA54 0001:004AC7AD C:\Program Files\World of Warcraft\Wow.exe
008ADFCC 05C6EA68 0001:004ACFCC C:\Program Files\World of Warcraft\Wow.exe
7BC6FC70 05C6EA78 0001:0005EC70 C:\windows\system32\ntdll.dll
7BC6FE40 05C6EB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 05C6F398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 05C6F498 0000:00000000 <unknown>

--- Thread ID: 65 ---
68333A3A 05AFEA68 0001:00012A3A C:\windows\system32\winmm.dll
7BC6FC70 05AFEA78 0001:0005EC70 C:\windows\system32\ntdll.dll
7BC6FE40 05AFEB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 05AFF398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 05AFF498 0000:00000000 <unknown>

--- Thread ID: 64 ---
7B869661 01EEE5F4 0001:00058661 C:\windows\system32\KERNEL32.dll
7B8696A5 01EEE614 0001:000586A5 C:\windows\system32\KERNEL32.dll
00473A7D 01EEE620 0001:00072A7D C:\Program Files\World of Warcraft\Wow.exe
0082C3ED 01EEEA40 0001:0042B3ED C:\Program Files\World of Warcraft\Wow.exe
0055AD7B 01EEEA68 0001:00159D7B C:\Program Files\World of Warcraft\Wow.exe
7BC6FC70 01EEEA78 0001:0005EC70 C:\windows\system32\ntdll.dll
7BC6FE40 01EEEB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 01EEF398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 01EEF498 0000:00000000 <unknown>

--- Thread ID: 63 ---
7B869661 0120E9D4 0001:00058661 C:\windows\system32\KERNEL32.dll
7B8696A5 0120E9F4 0001:000586A5 C:\windows\system32\KERNEL32.dll
00437635 0120EA14 0001:00036635 C:\Program Files\World of Warcraft\Wow.exe
0044D35A 0120EA28 0001:0004C35A C:\Program Files\World of Warcraft\Wow.exe
0093236F 0120EA60 0001:0053136F C:\Program Files\World of Warcraft\Wow.exe
00932414 0120EA78 0001:00531414 C:\Program Files\World of Warcraft\Wow.exe
7BC6FE40 0120EB48 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC78425 0120F398 0001:00067425 C:\windows\system32\ntdll.dll
6DD0F96E 0120F498 0000:00000000 <unknown>

--- Thread ID: 62 [Current Thread] ---
68F6D370 003AF4C0 0000:00000000 <unknown>
68F50F0E 003AF570 0000:00000000 <unknown>
6900024B 003AF5E0 0000:00000000 <unknown>
690003BE 003AF620 0000:00000000 <unknown>
68FF74EE 003AF640 0000:00000000 <unknown>
2007AB21 003AF9F0 0001:00069B21 C:\windows\system32\wined3d.dll
2004CB31 003AFA40 0001:0003BB31 C:\windows\system32\wined3d.dll
3C8E5556 003AFAA0 0001:00004556 C:\windows\system32\d3d9.dll
00663E11 003AFAD0 0001:00262E11 C:\Program Files\World of Warcraft\Wow.exe
0092FF7D 003AFB24 0001:0052EF7D C:\Program Files\World of Warcraft\Wow.exe
0092F35D 003AFB4C 0001:0052E35D C:\Program Files\World of Warcraft\Wow.exe
0080C2B3 003AFB6C 0001:0040B2B3 C:\Program Files\World of Warcraft\Wow.exe
0084C7F8 003AFC2C 0001:0044B7F8 C:\Program Files\World of Warcraft\Wow.exe
0086A9F7 003AFC48 0001:004699F7 C:\Program Files\World of Warcraft\Wow.exe
0086AEEB 003AFC64 0001:00469EEB C:\Program Files\World of Warcraft\Wow.exe
0083CB72 003AFD30 0001:0043BB72 C:\Program Files\World of Warcraft\Wow.exe
0088DA29 003AFD60 0001:0048CA29 C:\Program Files\World of Warcraft\Wow.exe
0088AB09 003AFD88 0001:00489B09 C:\Program Files\World of Warcraft\Wow.exe
0088C11A 003AFDDC 0001:0048B11A C:\Program Files\World of Warcraft\Wow.exe
0088C161 003AFDF4 0001:0048B161 C:\Program Files\World of Warcraft\Wow.exe
00406D7D 003AFE90 0001:00005D7D C:\Program Files\World of Warcraft\Wow.exe
7B85545C 003AFEA8 0001:0004445C C:\windows\system32\KERNEL32.dll
7B8576CB 003AFEE8 0001:000466CB C:\windows\system32\KERNEL32.dll
7BC6FC70 003AFEF8 0001:0005EC70 C:\windows\system32\ntdll.dll
7BC6FE40 003AFFC8 0001:0005EE40 C:\windows\system32\ntdll.dll
7BC4B6AA 003AFFE8 0001:0003A6AA C:\windows\system32\ntdll.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 17/17 threads...

--- Thread ID: 28 ---
7BC76753 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000003,0x00000004,0x00000000,0x00000000)
7BC76A43 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000003,0x00000000,0x00000000,0x00000000)
7B8694D6 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000003,0x00000000,0x00000000,0x00000000)
72226C8C winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+268 (0x00000003,0xFFFFFFFF,0x00000000,0x00000000)
68443E48 user32.dll   <unknown symbol>+0 (0x00000003,0xFFFFFFFF,0x00000000,0x7BC9BFF4)
6840A5CA user32.dll   MsgWaitForMultipleObjectsEx+250 (0x00000002,0xFFFFFFFF,0x00000000,0x0044C1C7)
6840A61F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x00000000,0x00000000,0x093C4B68)
0044C3E6 Wow.exe      <unknown symbol>+0 (0x00AE79F8,0x093C4BE0,0x0093236F,0x59DE4A5F)
0044D35A Wow.exe      <unknown symbol>+0 (0x093C4B68,0x00932395,0x7BC9BFF4,0x0799EA34)
0093236F Wow.exe      <unknown symbol>+0 (0x7FF94F10,0x093C4BE0,0x0799EB48,0x00932395)
00932414 Wow.exe      <unknown symbol>+0 (0x00932395,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x00932395,0x00000000,0x00000000,0x7FF941BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FF94FB8,0x0799FB70,0x0799F454,0x00000000)
6DD0F96E              start_thread+190 (0x0799FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 33 ---
7BC76753 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x7BC35B91)
7BC76A43 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x00000000,0x08B5BAB0)
7B8694D6 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x00000000)
7B8695EC KERNEL32.dll WaitForSingleObject+60 (0x00002210,0x008ADF50,0x7BC9BFF4,0x008AD949)
008EE4B5 Wow.exe      <unknown symbol>+0 (0x09213530,0x0782EA68,0x09213530,0x00000021)
008AD949 Wow.exe      <unknown symbol>+0 (0x09213530,0x00000021,0x7BC6FC70,0x7FF98F10)
008ADF90 Wow.exe      <unknown symbol>+0 (0x0921339C,0x0782EB48,0x008ADF50,0x7BC9BFF4)
7BC6FC70 ntdll.dll    call_thread_func+12 (0x008ADF50,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x008ADF50,0x00000000,0x00000000,0x7FF981BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FF98FB8,0x0782FB70,0x0782F454,0x00000000)
6DD0F96E              start_thread+190 (0x0782FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 31 ---
7BC76753 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000003,0x00000004,0x00000000,0x00000000)
7BC76A43 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000003,0x00000000,0x00000000,0x00000000)
7B8694D6 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000003,0x00000000,0x00000000,0x00000000)
72226C8C winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+268 (0x00000003,0xFFFFFFFF,0x00000000,0x00000000)
68443E48 user32.dll   <unknown symbol>+0 (0x00000003,0xFFFFFFFF,0x00000000,0x7BC9BFF4)
6840A5CA user32.dll   MsgWaitForMultipleObjectsEx+250 (0x00000002,0xFFFFFFFF,0x00000000,0x0044C1C7)
6840A61F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x00000000,0x00000000,0x09213CA8)
0044C3E6 Wow.exe      <unknown symbol>+0 (0x00AE7998,0x09213D20,0x0093236F,0x592C4A5F)
0044D35A Wow.exe      <unknown symbol>+0 (0x09213CA8,0x00932395,0x7BC9BFF4,0x076BEA34)
0093236F Wow.exe      <unknown symbol>+0 (0x7FF9CF10,0x09213D20,0x076BEB48,0x00932395)
00932414 Wow.exe      <unknown symbol>+0 (0x00932395,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x00932395,0x00000000,0x00000000,0x7FF9C1BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FF9CFB8,0x076BFB70,0x076BF454,0x00000000)
6DD0F96E              start_thread+190 (0x076BFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 32 ---
7BC76753 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x00000001)
7BC76A43 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x00000000,0x00000000)
7B8694D6 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x00000000)
7B8695EC KERNEL32.dll WaitForSingleObject+60 (0x000021D8,0x008ADF50,0x7BC9BFF4,0x008AD949)
008EE4B5 Wow.exe      <unknown symbol>+0 (0x08B5CDA8,0x0754EA68,0x08B5CDA8,0x00000020)
008AD949 Wow.exe      <unknown symbol>+0 (0x08B5CDA8,0x00000020,0x7BC6FC70,0x7FFA4F10)
008ADF90 Wow.exe      <unknown symbol>+0 (0x08B5CC44,0x0754EB48,0x008ADF50,0x7BC9BFF4)
7BC6FC70 ntdll.dll    call_thread_func+12 (0x008ADF50,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x008ADF50,0x00000000,0x00000000,0x7FFA41BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FFA4FB8,0x0754FB70,0x0754F454,0x00000000)
6DD0F96E              start_thread+190 (0x0754FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 12 ---
7BC76753 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x073DE9C8)
7BC76A43 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x073DEA48,0x00000000)
7BC76A9C ntdll.dll    NtWaitForSingleObject+60 (0x000021C0,0x073DEA48,0x00111600,0x073DEB08)
7BC7BB6F ntdll.dll    <unknown symbol>+0 (0x00000000,0x073DEB48,0x7BC7BA30,0x7BC9BFF4)
7BC6FC70 ntdll.dll    call_thread_func+12 (0x7BC7BA30,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x7BC7BA30,0x00000000,0x00000000,0x7FFA81BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x073DFB70,0x073DF454,0x00000000)
6DD0F96E              start_thread+190 (0x073DFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 13 ---
7BC76753 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x0726E9C8)
7BC76A43 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x0726EA48,0x00000000)
7BC76A9C ntdll.dll    NtWaitForSingleObject+60 (0x000021C0,0x0726EA48,0x688F8280,0x0726EB08)
7BC7BB6F ntdll.dll    <unknown symbol>+0 (0x00000000,0x0726EB48,0x7BC7BA30,0x7BC9BFF4)
7BC6FC70 ntdll.dll    call_thread_func+12 (0x7BC7BA30,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x7BC7BA30,0x00000000,0x00000000,0x7FFAC1BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x0726FB70,0x0726F454,0x00000000)
6DD0F96E              start_thread+190 (0x0726FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 11 ---
7BC76753 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000003,0x00000004,0x00000000,0x00000000)
7BC76A43 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000003,0x00000000,0x00000000,0x00000000)
7B8694D6 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000003,0x00000000,0x00000000,0x00000000)
72226C8C winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+268 (0x00000003,0xFFFFFFFF,0x00000000,0x00000000)
68443E48 user32.dll   <unknown symbol>+0 (0x00000003,0xFFFFFFFF,0x00000000,0x7BC9BFF4)
6840A5CA user32.dll   MsgWaitForMultipleObjectsEx+250 (0x00000002,0xFFFFFFFF,0x00000000,0x0044C1C7)
6840A61F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x00000000,0x00000000,0x053A91B8)
0044C3E6 Wow.exe      <unknown symbol>+0 (0x00AE7950,0x053A9210,0x0093236F,0x58A54A5F)
0044D35A Wow.exe      <unknown symbol>+0 (0x053A91B8,0x00932395,0x7BC9BFF4,0x06E2EA34)
0093236F Wow.exe      <unknown symbol>+0 (0x7FFB0F10,0x053A9210,0x06E2EB48,0x00932395)
00932414 Wow.exe      <unknown symbol>+0 (0x00932395,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x00932395,0x00000000,0x00000000,0x7FFB01BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x06E2FB70,0x06E2F454,0x00000000)
6DD0F96E              start_thread+190 (0x06E2FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 71 ---
7BC76753 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x7FFB4000)
7BC76A43 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x0639E78C,0x00000000)
7B8694D6 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x7B868D7A)
7B86954A KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x00000000,0x00000047,0x05261570)
00468D1B Wow.exe      <unknown symbol>+0 (0x051FA420,0x0055AD7B,0x0055ACE0,0x7BC9BFF4)
004683CE Wow.exe      <unknown symbol>+0 (0x05261570,0x7FFB4F10,0x0000219C,0x05261570)
0055AD7B Wow.exe      <unknown symbol>+0 (0x00B78EB0,0x0639EB48,0x0055ACE0,0x7BC9BFF4)
7BC6FC70 ntdll.dll    call_thread_func+12 (0x0055ACE0,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x0055ACE0,0x00000000,0x00000000,0x7FFB41BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x0639FB70,0x0639F454,0x00000000)
6DD0F96E              start_thread+190 (0x0639FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 70 ---
7BC76753 ntdll.dll    NTDLL_wait_for_multiple_objects+595 (0x00000001,0x00000004,0x00000000,0x7BC6F28E)
7BC76A43 ntdll.dll    NtWaitForMultipleObjects+99 (0x00000001,0x00000000,0x0622E9BC,0x7BC9BFF4)
7B8694D6 KERNEL32.dll WaitForMultipleObjectsEx+246 (0x00000001,0x00000000,0x00000000,0x009747F1)
7B8695EC KERNEL32.dll WaitForSingleObject+60 (0x0000210C,0x0622EA34,0x000003E8,0x051FA408)
0055F4D0 Wow.exe      <unknown symbol>+0 (0x000003E8,0x051FA408,0x0622EA40,0x00000000)
00468505 Wow.exe      <unknown symbol>+0 (0x00000000,0x0055AD7B,0x0055ACE0,0x7BC9BFF4)
00468671 Wow.exe      <unknown symbol>+0 (0x05261580,0x7FFB8F10,0x00002198,0x05261580)
0055AD7B Wow.exe      <unknown symbol>+0 (0x00B78E90,0x0622EB48,0x0055ACE0,0x7BC9BFF4)
7BC6FC70 ntdll.dll    call_thread_func+12 (0x0055ACE0,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x0055ACE0,0x00000000,0x00000000,0x7FFB81BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x0622FB70,0x0622F454,0x00000000)
6DD0F96E              start_thread+190 (0x0622FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 69 ---
7B869661 KERNEL32.dll SleepEx+65 (0x0000000A,0x060BEA54,0x7B869689,0x060BEA54)
7B8696A5 KERNEL32.dll Sleep+37 (0x0000000A,0x008ADFCC,0x7FFBCF10,0x060BEA78)
008AD7AD Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000045,0x7BC6FC70,0x7FFBCF10)
008ADFCC Wow.exe      <unknown symbol>+0 (0x048DC068,0x060BEB48,0x008ADF50,0x7BC9BFF4)
7BC6FC70 ntdll.dll    call_thread_func+12 (0x008ADF50,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x008ADF50,0x00000000,0x00000000,0x7FFBC1BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x060BFB70,0x060BF454,0x00000000)
6DD0F96E              start_thread+190 (0x060BFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 68 ---
7B869661 KERNEL32.dll SleepEx+65 (0x0000000A,0x00000000,0x7B869689,0x05F4EA54)
7B8696A5 KERNEL32.dll Sleep+37 (0x0000000A,0x008ADFCC,0x7FFC0F10,0x05F4EA78)
008AD7AD Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000044,0x7BC6FC70,0x7FFC0F10)
008ADFCC Wow.exe      <unknown symbol>+0 (0x045CF618,0x05F4EB48,0x008ADF50,0x7BC9BFF4)
7BC6FC70 ntdll.dll    call_thread_func+12 (0x008ADF50,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x008ADF50,0x00000000,0x00000000,0x7FFC01BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FFC0FB8,0x05F4FB70,0x05F4F454,0x00000000)
6DD0F96E              start_thread+190 (0x05F4FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 67 ---
7B869661 KERNEL32.dll SleepEx+65 (0x0000000A,0x05DDEA54,0x7B869689,0x05DDEA54)
7B8696A5 KERNEL32.dll Sleep+37 (0x0000000A,0x008ADFCC,0x7FFC4F10,0x05DDEA78)
008AD7AD Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000043,0x7BC6FC70,0x7FFC4F10)
008ADFCC Wow.exe      <unknown symbol>+0 (0x048E46E8,0x05DDEB48,0x008ADF50,0x7BC9BFF4)
7BC6FC70 ntdll.dll    call_thread_func+12 (0x008ADF50,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x008ADF50,0x00000000,0x00000000,0x7FFC41BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FFC4FB8,0x05DDFB70,0x05DDF454,0x00000000)
6DD0F96E              start_thread+190 (0x05DDFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 66 ---
7B869661 KERNEL32.dll SleepEx+65 (0x0000000A,0x00000000,0x7B869689,0x05C6EA54)
7B8696A5 KERNEL32.dll Sleep+37 (0x0000000A,0x008ADFCC,0x7FFC8F10,0x05C6EA78)
008AD7AD Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000042,0x7BC6FC70,0x7FFC8F10)
008ADFCC Wow.exe      <unknown symbol>+0 (0x0478D488,0x05C6EB48,0x008ADF50,0x7BC9BFF4)
7BC6FC70 ntdll.dll    call_thread_func+12 (0x008ADF50,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x008ADF50,0x00000000,0x00000000,0x7FFC81BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x05C6FB70,0x05C6F454,0x00000000)
6DD0F96E              start_thread+190 (0x05C6FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 65 ---
68333A3A winmm.dll    <unknown symbol>+0 (0x68320000,0x05AFEB48,0x68333710,0x7BC9BFF4)
7BC6FC70 ntdll.dll    call_thread_func+12 (0x68333710,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x68333710,0x00000000,0x00000000,0x7FFCC1BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x05AFFB70,0x05AFF454,0x00000000)
6DD0F96E              start_thread+190 (0x05AFFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 64 ---
7B869661 KERNEL32.dll SleepEx+65 (0x00000001,0x01EEE614,0x7B869689,0x01EEE620)
7B8696A5 KERNEL32.dll Sleep+37 (0x00000001,0x0082C3ED,0x020535E8,0x000020D4)
00473A7D Wow.exe      <unknown symbol>+0 (0x00000001,0x00000040,0x00000000,0x00000000)
0082C3ED Wow.exe      <unknown symbol>+0 (0x020535C8,0x7FFD0F10,0x000020D4,0x020535C8)
0055AD7B Wow.exe      <unknown symbol>+0 (0x00B78E70,0x01EEEB48,0x0055ACE0,0x7BC9BFF4)
7BC6FC70 ntdll.dll    call_thread_func+12 (0x0055ACE0,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x0055ACE0,0x00000000,0x00000000,0x7FFD01BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FFD0FB8,0x01EEFB70,0x01EEF454,0x00000000)
6DD0F96E              start_thread+190 (0x01EEFB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 63 ---
7B869661 KERNEL32.dll SleepEx+65 (0x00000064,0x00000000,0x7B869689,0x0120EA14)
7B8696A5 KERNEL32.dll Sleep+37 (0x00000064,0x7BC9BFF4,0x018F709D,0x0120EA28)
00437635 Wow.exe      <unknown symbol>+0 (0x00000000,0x01043FA0,0x0093236F,0x5F674A5F)
0044D35A Wow.exe      <unknown symbol>+0 (0x0101A6B8,0x00932395,0x7BC9BFF4,0x0120EA34)
0093236F Wow.exe      <unknown symbol>+0 (0x7FFD4F10,0x01043FA0,0x0120EB48,0x00932395)
00932414 Wow.exe      <unknown symbol>+0 (0x00932395,0x7BC9BFF4,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x00932395,0x00000000,0x00000000,0x7FFD41BC)
7BC78425 ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x0120FB70,0x0120F454,0x00000000)
6DD0F96E              start_thread+190 (0x0120FB70,0x00000000,0x00000000,0x00000000)

--- Thread ID: 62 [Current Thread] ---
68F6D370              radeonEmitVec16+64 (0x7BF18020,0x00000000,0x00000020,0x00000001)
68F50F0E              <unknown symbol>+0 (0x7D61B748,0x003AF5A8,0x003AF5B8,0x00000000)
6900024B              <unknown symbol>+0 (0x00000000,0xFFFFFFFF,0x00001403,0x00000000)
690003BE              <unknown symbol>+0 (0x00000005,0x00001403,0x20135FF4,0x003AF9F0)
68FF74EE              <unknown symbol>+0 (0x00000005,0x00001403,0x00000300,0x0000002E)
2007AB21 wined3d.dll  <unknown symbol>+0 (0x00134CE8,0x00000098,0x100B41E0,0x00000000)
2004CB31 wined3d.dll  <unknown symbol>+0 (0x00134CE8,0x00000004,0x003AFAA0,0x00134CE8)
3C8E5556 d3d9.dll     <unknown symbol>+0 (0x0012DF10,0x000000C3,0x00000004,0x00000002)
00663E11 Wow.exe      <unknown symbol>+0 (0x3C902CE0,0x090F35E8,0x3F402000,0x3A000000)
0092FF7D Wow.exe      <unknown symbol>+0 (0x00000001,0x0092E72E,0x00000000,0x00000000)
0092F35D Wow.exe      <unknown symbol>+0 (0x048D2BFC,0x00000000,0x00000000,0x003AFC2C)
0080C2B3 Wow.exe      <unknown symbol>+0 (0xFF000000,0x048D2B80,0x0084C16C,0x00000002)
0084C7F8 Wow.exe      <unknown symbol>+0 (0x048D2BFC,0x00000006,0x05483570,0x0086AEEB)
0086A9F7 Wow.exe      <unknown symbol>+0 (0x0211E548,0x05483348,0x00000000,0x0083CB72)
0086AEEB Wow.exe      <unknown symbol>+0 (0x00000000,0x05483360,0x0207C150,0x020618F8)
0083CB72 Wow.exe      <unknown symbol>+0 (0x00000000,0x00004EF7,0x0207C150,0x00004EF7)
0088DA29 Wow.exe      <unknown symbol>+0 (0x02061778,0x00000000,0x00000A28,0x00000001)
0088AB09 Wow.exe      <unknown symbol>+0 (0x00000000,0x00000002,0x3320656E,0x7B868FB0)
0088C11A Wow.exe      <unknown symbol>+0 (0x00000000,0x00000001,0x003AFE90,0x0040B979)
0088C161 Wow.exe      <unknown symbol>+0 (0x0040B979,0x00000000,0x0000000A,0x00401000)
00406D7D Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x7B883FF4,0x003AFEE8,0x7FFDF000)
7B85545C KERNEL32.dll call_process_entry+12 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B8576CB KERNEL32.dll <unknown symbol>+0 (0x7FFDF000,0x003AFFC8,0x7B857670,0x00000000)
7BC6FC70 ntdll.dll    call_thread_func+12 (0x7B857670,0x00000000,0xFFFFFFFF,0x7B837100)
7BC6FE40 ntdll.dll    call_thread_entry_point+112 (0x7B857670,0x00000000,0x00000000,0x00000000)
7BC4B6AA ntdll.dll    <unknown symbol>+0 (0x7B857670,0x00000000,0x00000001,0x73676F4C)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00D9C000  C:\Program Files\World of Warcraft\Wow.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x20010000 - 0x20138000  C:\windows\system32\wined3d.dll
0x20140000 - 0x20180000  C:\windows\system32\dsound.dll
0x201C0000 - 0x201CF000  C:\windows\system32\msacm32.drv
0x201D0000 - 0x201E5000  C:\windows\system32\psapi.dll
0x3C8E0000 - 0x3C904000  C:\windows\system32\d3d9.dll
0x51E00000 - 0x51E47000  C:\windows\system32\dbghelp.dll
0x5B0B0000 - 0x5B0C4000  C:\windows\system32\midimap.dll
0x68320000 - 0x68396000  C:\windows\system32\winmm.dll
0x683B0000 - 0x684C6000  C:\windows\system32\user32.dll
0x684D0000 - 0x68551000  C:\windows\system32\gdi32.dll
0x68560000 - 0x685AB000  C:\windows\system32\advapi32.dll
0x685C0000 - 0x68620000  C:\windows\system32\rpcrt4.dll
0x68640000 - 0x686C5000  C:\windows\system32\opengl32.dll
0x688D0000 - 0x68921000  C:\windows\system32\wininet.dll
0x68940000 - 0x68998000  C:\windows\system32\shlwapi.dll
0x689B0000 - 0x68B6A000  C:\windows\system32\shell32.dll
0x68B70000 - 0x68C55000  C:\windows\system32\comctl32.dll
0x68C60000 - 0x68C7B000  C:\windows\system32\msacm32.dll
0x68C80000 - 0x68CA8000  C:\windows\system32\ws2_32.dll
0x68CB0000 - 0x68CC3000  C:\windows\system32\dinput8.dll
0x68CD0000 - 0x68CFC000  C:\windows\system32\dinput.dll
0x68D20000 - 0x68DFC000  C:\windows\system32\ole32.dll
0x68E10000 - 0x68E59000  C:\windows\system32\setupapi.dll
0x68E60000 - 0x68E90000  C:\windows\system32\winspool.drv
0x68EA0000 - 0x68EA9000  C:\windows\system32\version.dll
0x691B0000 - 0x691D6000  C:\windows\system32\uxtheme.dll
0x691E0000 - 0x691F7000  C:\windows\system32\localspl.dll
0x69200000 - 0x69212000  C:\windows\system32\spoolss.dll
0x6F660000 - 0x6F67C000  C:\windows\system32\mpr.dll
0x71D90000 - 0x71DA3000  C:\windows\system32\hid.dll
0x721F0000 - 0x72288000  C:\windows\system32\winex11.drv
0x76AF0000 - 0x76B09000  C:\windows\system32\imm32.dll
0x798C0000 - 0x798EA000  C:\windows\system32\winealsa.drv
0x7B810000 - 0x7B946000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCB8000  C:\windows\system32\ntdll.dll
0x7C620000 - 0x7C625000  C:\windows\system32\lz32.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 68F6D370)

68F6D370: 8B 16 83 C0  01 89 17 8B  56 04 89 57  04 8B 56 08  ........V..W..V.


Stack: 1024 bytes starting at (ESP = 003AF478)

* = addr                            **                                *       
003AF470: C0 F4 3A 00  F4 0F 19 69  B0 4D C0 7D  08 00 00 00  ..:....i.M.}....
003AF480: C0 F4 3A 00  61 E0 F6 68  E0 C7 03 7E  08 00 00 00  ..:.a..h...~....
003AF490: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
003AF4A0: 08 00 00 00  E1 FC F4 68  00 80 F1 7B  10 43 0B 10  .......h...{.C..
003AF4B0: 3B D3 F6 68  F4 0F 19 69  A0 13 C9 7D  01 00 00 00  ;..h...i...}....
003AF4C0: 70 F5 3A 00  0E 0F F5 68  20 80 F1 7B  00 00 00 00  p.:....h ..{....
003AF4D0: 00 00 00 00  01 00 00 00  20 00 00 00  01 00 00 00  ........ .......
003AF4E0: 01 00 00 00  F4 0F 19 69  48 B7 61 7D  80 48 CA 7C  .......iH.a}.H.|
003AF4F0: 50 F5 3A 00  19 84 FD 68  48 B7 61 7D  00 00 40 08  P.:....hH.a}..@.
003AF500: 00 00 00 00  5C B1 E6 7D  00 00 00 00  BB 01 00 00  ....\..}........
003AF510: 03 00 00 00  B0 4D C0 7D  B0 4D C0 7D  01 00 00 03  .....M.}.M.}....
003AF520: B0 4D C0 7D  04 00 00 00  00 B7 61 7D  01 00 00 00  .M.}......a}....
003AF530: C4 4D C0 7D  00 73 FE 68  00 00 00 00  CC 4D C0 7D  .M.}.s.h.....M.}
003AF540: 04 00 00 00  6C B0 E6 7D  48 B7 61 7D  F4 0F 19 69  ....l..}H.a}...i
003AF550: 70 F5 3A 00  42 8D FD 68  48 B7 61 7D  F4 5F 13 20  p.:.B..hH.a}._. 
003AF560: E0 F5 3A 00  F4 0F 19 69  48 B7 61 7D  88 F1 C8 7D  ..:....iH.a}...}
003AF570: E0 F5 3A 00  4B 02 00 69  48 B7 61 7D  94 13 C9 7D  ..:.K..iH.a}...}
003AF580: A8 F5 3A 00  01 00 00 00  B8 F5 3A 00  00 00 00 00  ..:.......:.....
003AF590: 00 00 00 00  03 00 00 00  F4 0F 19 69  48 B7 61 7D  ...........iH.a}
003AF5A0: E0 F5 3A 00  05 00 00 00  05 07 00 00  00 00 00 00  ..:.............
003AF5B0: 04 00 00 00  00 00 00 00  04 00 00 00  03 14 00 00  ................
003AF5C0: A0 06 C0 7D  10 43 0B 10  40 2A 28 72  A8 FA 0A 10  ...}.C..@*(r....
003AF5D0: D8 0A 00 00  F4 0F 19 69  48 B7 61 7D  03 14 00 00  .......iH.a}....
003AF5E0: 20 F6 3A 00  BE 03 00 69  00 00 00 00  FF FF FF FF   .:....i........
003AF5F0: FF FF FF FF  04 00 00 00  03 14 00 00  10 43 0B 10  .............C..
003AF600: 00 00 00 00  AE CF FF 68  28 FA C8 7D  6C 0C 10 20  .......h(..}l.. 
003AF610: 40 F6 3A 00  F4 0F 19 69  48 B7 61 7D  00 00 00 00  @.:....iH.a}....
003AF620: 40 F6 3A 00  EE 74 FF 68  05 00 00 00  04 00 00 00  @.:..t.h........
003AF630: 03 14 00 00  10 43 0B 10  F4 5F 13 20  05 00 00 00  .....C..._. ....
003AF640: F0 F9 3A 00  21 AB 07 20  05 00 00 00  04 00 00 00  ..:.!.. ........
003AF650: 03 14 00 00  10 43 0B 10  00 03 00 00  4E 56 11 20  .....C......NV. 
003AF660: 2E 00 00 00  38 1B 09 10  00 00 00 00  CC F6 3A 00  ....8.........:.
003AF670: 9F B9 0D 20  38 1B 09 10  00 00 00 00  E8 4C 13 00  ... 8........L..
003AF680: 00 00 04 00  C0 F9 3A 00  20 26 13 00  C8 F9 3A 00  ......:. &....:.
003AF690: 10 1B 09 10  04 2B 90 3C  00 00 00 00  00 00 00 00  .....+.<........
003AF6A0: 00 00 11 00  AD 10 11 20  4E 56 11 20  20 26 13 00  ....... NV.  &..
003AF6B0: B0 B3 0D 20  4F 52 C3 7B  F4 BF C9 7B  8B 88 C4 7B  ... OR.{...{...{
003AF6C0: F4 5F 13 20  38 1B 09 10  E8 4C 13 00  05 00 00 00  ._. 8....L......
003AF6D0: 98 51 14 00  05 00 00 00  98 51 14 00  6C 0C 10 20  .Q.......Q..l.. 
003AF6E0: AD 10 11 20  4E 56 11 20  00 00 00 00  94 7A 13 00  ... NV. .....z..
003AF6F0: 00 00 00 00  00 00 00 00  00 00 00 00  E8 4C 13 00  .............L..
003AF700: 4F 52 C3 7B  72 00 00 00  00 00 00 00  10 1B 09 10  OR.{r...........
003AF710: 79 4A 8E 3C  10 1B 09 10  F4 5F 13 20  3C F7 3A 00  yJ.<....._. <.:.
003AF720: 20 C8 0F 20  60 72 13 20  6C 0C 10 20  DB 1E 05 20   .. `r. l.. ... 
003AF730: F4 2F 90 3C  F4 2F 90 3C  10 1B 09 10  5E 68 C4 7B  ./.<./.<....^h.{
003AF740: 67 07 8F 3C  91 75 C4 7B  68 67 09 10  02 00 00 00  g..<.u.{hg......
003AF750: 68 67 09 10  00 00 00 00  F4 BF C9 7B  4F 52 C3 7B  hg.........{OR.{
003AF760: 50 00 00 00  78 F7 3A 00  96 77 C4 7B  E0 47 00 00  P...x.:..w.{.G..
003AF770: 30 1F 09 10  F4 BF C9 7B  D8 F7 3A 00  1E 8B C4 7B  0......{..:....{
003AF780: 60 00 11 00  02 00 00 00  68 67 09 10  00 00 00 00  `.......hg......
003AF790: 4F 52 C3 7B  4F 52 C3 7B  78 00 00 00  7B 06 8F 3C  OR.{OR.{x...{..<
003AF7A0: 50 00 00 00  00 00 00 00  00 00 00 00  D0 6B 0F 20  P............k. 
003AF7B0: 20 C8 0F 20  60 72 13 20  10 DF 12 00  00 90 06 10   .. `r. ........
003AF7C0: F4 2F 90 3C  91 75 C4 7B  8B 88 C4 7B  F4 5F 13 20  ./.<.u.{...{._. 
003AF7D0: F4 5F 13 20  80 1E 09 10  91 75 C4 7B  90 1E 09 10  ._. .....u.{....
003AF7E0: 02 00 00 00  90 1E 09 10  50 00 00 00  F4 BF C9 7B  ........P......{
003AF7F0: 00 90 06 10  48 1E 09 10  48 F8 3A 00  78 78 C4 7B  ....H...H.:.xx.{
003AF800: 48 00 00 00  00 00 00 00  68 00 00 00  5E 68 C4 7B  H.......h...^h.{
003AF810: 1E 57 0E 20  91 75 C4 7B  74 1F 09 10  40 00 00 00  .W. .u.{t...@...
003AF820: 00 C1 12 20  60 C2 12 20  8C F8 3A 00  4F 52 C3 7B  ... `.. ..:.OR.{
003AF830: 0C 11 13 00  48 F8 01 00  04 00 00 00  F4 BF C9 7B  ....H..........{
003AF840: 00 00 00 00  00 00 00 00  00 04 00 00  00 03 00 00  ................
003AF850: 60 00 11 00  04 00 00 00  6C 2F 03 20  CA 0F 05 20  `.......l/. ... 
003AF860: C8 1E 09 10  E8 4C 13 00  59 18 03 20  4F 52 C3 7B  .....L..Y.. OR.{
003AF870: 28 1E 09 10  10 2C 90 3C  48 1E 09 10  C3 03 00 00  (....,.<H.......


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
Processor Revision:     1027
Os Version:             5.1
Os Service Pack:        3.0

Percent memory used:    31
Total physical memory:  1049497600
Free Memory:            723488768
Page file:              4120768512
Total virtual memory:   2147352575

```....And it all just looks like a hot mess to me. Does anyone have any suggestions?

---

### Post by hikaricore on 2010-06-20
Error 132 is a pretty generic error that can be caused by a wide range of problems.
Right off the bat I'd be willing to be it's video hardware/driver related.

---

