---
title: "WoW Error 132 memory could not be read"
date: 2009-07-03
forum: Wine
---

### Post by firewall_03 on 2009-07-03
I am using a Sony Vaio VGN-VR160E laptop, I know its probably not smart to run Wow but, it helps to pass the time while your in Afghanistan, and this is my video card Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) also my Config.wtf contains this [PHP]SET locale "enUS"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET doodadAnim "0"
SET SmallCull "0.080000"
SET DistCull "350.000000"
SET frillDensity "8"
SET farclip "177"
SET pixelShaders "0"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET showToolsUI "0"
SET coresDetected "2"
SET videoOptionsVersion "2"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET accounttype "LK"
SET realmName "Icecrown"
SET gameTip "7"
SET accountName "firewall03"
SET textureFilteringMode "0"
SET particleDensity "0.10000000149012"
SET baseMip "1"
SET environmentDetail "0.5"
SET weatherDensity "0"
SET ffxGlow "0"
SET ffxDeath "0"
SET mouseSpeed "1.2999999523163"
SET VoiceActivationSensitivity "0.39999997615814"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"[/PHP]

[PHP]==============================================================================

World of WarCraft (build 9947)



Exe:      C:\Program Files\World of Warcraft\Wow.exe

Time:     Jul  4, 2009 12:53:38.688 AM

User:     rob

Computer: rob-laptop

------------------------------------------------------------------------------



This application has encountered a critical error:



ERROR #132 (0x85100084) Fatal Exception

Program:	C:\Program Files\World of Warcraft\Wow.exe

Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7E8B61FB



The instruction at "0x7E8B61FB" referenced memory at "0x39604A08".

The memory could not be "read".





WoWBuild: 9947

Realm: Icecrown [206.17.111.52:3724]

Local Zone: Stormwind City

Local Player: Ghagme, 05800000053D137A, (-8825.91,830.697,98.9172)

Locked Target: Master Fire Eater, F130006577002587, (-8836.37,851.844,99.0481)

Total lua memory: 16891KB

Add Ons: QuestHelper 

Settings: 

SET locale "enUS"

SET hwDetect "0"

SET gxRefresh "60"

SET gxMultisampleQuality "0.000000"

SET gxFixLag "0"

SET doodadAnim "0"

SET SmallCull "0.080000"

SET DistCull "350.000000"

SET frillDensity "8"

SET farclip "177"

SET pixelShaders "0"

SET movie "0"

SET readTOS "1"

SET readEULA "1"

SET realmList "us.logon.worldofwarcraft.com"

SET patchlist "us.version.worldofwarcraft.com"

SET readScanning "-1"

SET readContest "-1"

SET readTerminationWithoutNotice "-1"

SET installType "Retail"

SET showToolsUI "0"

SET coresDetected "2"

SET videoOptionsVersion "2"

SET Gamma "1.000000"

SET Sound_OutputDriverName "System Default"

SET Sound_MusicVolume "0.40000000596046"

SET Sound_AmbienceVolume "0.60000002384186"

SET accounttype "LK"

SET realmName "Icecrown"

SET gameTip "7"

SET textureFilteringMode "0"

SET particleDensity "0.10000000149012"

SET baseMip "1"

SET environmentDetail "0.5"

SET weatherDensity "0"

SET ffxGlow "0"

SET ffxDeath "0"

SET mouseSpeed "1.2999999523163"

SET VoiceActivationSensitivity "0.39999997615814"

SET ChatMusicVolume "0.29999998211861"

SET ChatSoundVolume "0.39999997615814"

SET ChatAmbienceVolume "0.29999998211861"

------------------------------------------------------------------------------



----------------------------------------

    x86 Registers

----------------------------------------



EAX=15CC3670  EBX=7E8F7FF4  ECX=003AFC94  EDX=39604A04  ESI=00000001

EDI=15D81D28  EBP=003AFC64  ESP=003AFC3C  EIP=7E8B61FB  FLG=00210202

CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B





----------------------------------------

    Stack Trace (Manual)

----------------------------------------



Address  Frame    Logical addr  Module



Showing 21/21 threads...



--- Thread ID: 68 ---

7BC71D65 0D7AE6A4 0001:00060D65 C:\windows\system32\ntdll.dll

7BC72062 0D7AE6D4 0001:00061062 C:\windows\system32\ntdll.dll

7B88F972 0D7AE814 0001:0006E972 C:\windows\system32\KERNEL32.dll

7E0AC9BB 0D7AE844 0001:0002B9BB C:\windows\system32\winex11.drv

7ED13D05 0D7AE9F4 0001:00072D05 C:\windows\system32\user32.dll

7ED13D6F 0D7AEA14 0001:00072D6F C:\windows\system32\user32.dll

004415D9 0D7AEA44 0001:000405D9 C:\Program Files\World of Warcraft\Wow.exe

004425DA 0D7AEA58 0001:000415DA C:\Program Files\World of Warcraft\Wow.exe

008D967F 0D7AEA90 0001:004D867F C:\Program Files\World of Warcraft\Wow.exe

008D9724 0D7AEAA8 0001:004D8724 C:\Program Files\World of Warcraft\Wow.exe

7BC6B770 0D7AEB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 0D7AF3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 0D7AF4B8 0000:00000000 <unknown>



--- Thread ID: 67 ---

7BC71D65 0D63E6A4 0001:00060D65 C:\windows\system32\ntdll.dll

7BC72062 0D63E6D4 0001:00061062 C:\windows\system32\ntdll.dll

7B88F972 0D63E814 0001:0006E972 C:\windows\system32\KERNEL32.dll

7E0AC9BB 0D63E844 0001:0002B9BB C:\windows\system32\winex11.drv

7ED13D05 0D63E9F4 0001:00072D05 C:\windows\system32\user32.dll

7ED13D6F 0D63EA14 0001:00072D6F C:\windows\system32\user32.dll

004415D9 0D63EA44 0001:000405D9 C:\Program Files\World of Warcraft\Wow.exe

004425DA 0D63EA58 0001:000415DA C:\Program Files\World of Warcraft\Wow.exe

008D967F 0D63EA90 0001:004D867F C:\Program Files\World of Warcraft\Wow.exe

008D9724 0D63EAA8 0001:004D8724 C:\Program Files\World of Warcraft\Wow.exe

7BC6B770 0D63EB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 0D63F3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 0D63F4B8 0000:00000000 <unknown>



--- Thread ID: 66 ---

7BC71D65 0D4CE8CC 0001:00060D65 C:\windows\system32\ntdll.dll

7BC72062 0D4CE8FC 0001:00061062 C:\windows\system32\ntdll.dll

7B88F972 0D4CEA3C 0001:0006E972 C:\windows\system32\KERNEL32.dll

7B88FB6C 0D4CEA5C 0001:0006EB6C C:\windows\system32\KERNEL32.dll

00540210 0D4CEA6C 0001:0013F210 C:\Program Files\World of Warcraft\Wow.exe

008F15C6 0D4CEA7C 0001:004F05C6 C:\Program Files\World of Warcraft\Wow.exe

0053BBE7 0D4CEA98 0001:0013ABE7 C:\Program Files\World of Warcraft\Wow.exe

7BC6B568 0D4CEAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 0D4CEB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 0D4CF3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 0D4CF4B8 0000:00000000 <unknown>



--- Thread ID: 65 ---

7BC71D65 0657E6A4 0001:00060D65 C:\windows\system32\ntdll.dll

7BC72062 0657E6D4 0001:00061062 C:\windows\system32\ntdll.dll

7B88F972 0657E814 0001:0006E972 C:\windows\system32\KERNEL32.dll

7E0AC9BB 0657E844 0001:0002B9BB C:\windows\system32\winex11.drv

7ED13D05 0657E9F4 0001:00072D05 C:\windows\system32\user32.dll

7ED13D6F 0657EA14 0001:00072D6F C:\windows\system32\user32.dll

004415D9 0657EA44 0001:000405D9 C:\Program Files\World of Warcraft\Wow.exe

004425DA 0657EA58 0001:000415DA C:\Program Files\World of Warcraft\Wow.exe

008D967F 0657EA90 0001:004D867F C:\Program Files\World of Warcraft\Wow.exe

008D9724 0657EAA8 0001:004D8724 C:\Program Files\World of Warcraft\Wow.exe

7BC6B770 0657EB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 0657F3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 0657F4B8 0000:00000000 <unknown>



--- Thread ID: 62 ---

7BC71D65 0C3CE8C8 0001:00060D65 C:\windows\system32\ntdll.dll

7BC72062 0C3CE8F8 0001:00061062 C:\windows\system32\ntdll.dll

7B88F972 0C3CEA38 0001:0006E972 C:\windows\system32\KERNEL32.dll

7B88FB6C 0C3CEA58 0001:0006EB6C C:\windows\system32\KERNEL32.dll

00895FF5 0C3CEA74 0001:00494FF5 C:\Program Files\World of Warcraft\Wow.exe

0085547A 0C3CEA84 0001:0045447A C:\Program Files\World of Warcraft\Wow.exe

00855AD0 0C3CEA98 0001:00454AD0 C:\Program Files\World of Warcraft\Wow.exe

7BC6B568 0C3CEAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 0C3CEB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 0C3CF3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 0C3CF4B8 0000:00000000 <unknown>



--- Thread ID: 59 ---

7BC71D65 0BC4E6A4 0001:00060D65 C:\windows\system32\ntdll.dll

7BC72062 0BC4E6D4 0001:00061062 C:\windows\system32\ntdll.dll

7B88F972 0BC4E814 0001:0006E972 C:\windows\system32\KERNEL32.dll

7E0AC9BB 0BC4E844 0001:0002B9BB C:\windows\system32\winex11.drv

7ED13D05 0BC4E9F4 0001:00072D05 C:\windows\system32\user32.dll

7ED13D6F 0BC4EA14 0001:00072D6F C:\windows\system32\user32.dll

004415D9 0BC4EA44 0001:000405D9 C:\Program Files\World of Warcraft\Wow.exe

004425DA 0BC4EA58 0001:000415DA C:\Program Files\World of Warcraft\Wow.exe

008D967F 0BC4EA90 0001:004D867F C:\Program Files\World of Warcraft\Wow.exe

008D9724 0BC4EAA8 0001:004D8724 C:\Program Files\World of Warcraft\Wow.exe

7BC6B770 0BC4EB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 0BC4F3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 0BC4F4B8 0000:00000000 <unknown>



--- Thread ID: 58 ---

7BC71D65 0BADE8C8 0001:00060D65 C:\windows\system32\ntdll.dll

7BC72062 0BADE8F8 0001:00061062 C:\windows\system32\ntdll.dll

7B88F972 0BADEA38 0001:0006E972 C:\windows\system32\KERNEL32.dll

7B88FB6C 0BADEA58 0001:0006EB6C C:\windows\system32\KERNEL32.dll

00895FF5 0BADEA74 0001:00494FF5 C:\Program Files\World of Warcraft\Wow.exe

0085547A 0BADEA84 0001:0045447A C:\Program Files\World of Warcraft\Wow.exe

00855AD0 0BADEA98 0001:00454AD0 C:\Program Files\World of Warcraft\Wow.exe

7BC6B568 0BADEAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 0BADEB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 0BADF3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 0BADF4B8 0000:00000000 <unknown>



--- Thread ID: 56 ---

7BC71D65 0830E6A4 0001:00060D65 C:\windows\system32\ntdll.dll

7BC72062 0830E6D4 0001:00061062 C:\windows\system32\ntdll.dll

7B88F972 0830E814 0001:0006E972 C:\windows\system32\KERNEL32.dll

7E0AC9BB 0830E844 0001:0002B9BB C:\windows\system32\winex11.drv

7ED13D05 0830E9F4 0001:00072D05 C:\windows\system32\user32.dll

7ED13D6F 0830EA14 0001:00072D6F C:\windows\system32\user32.dll

004415D9 0830EA44 0001:000405D9 C:\Program Files\World of Warcraft\Wow.exe

004425DA 0830EA58 0001:000415DA C:\Program Files\World of Warcraft\Wow.exe

008D967F 0830EA90 0001:004D867F C:\Program Files\World of Warcraft\Wow.exe

008D9724 0830EAA8 0001:004D8724 C:\Program Files\World of Warcraft\Wow.exe

7BC6B770 0830EB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 0830F3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 0830F4B8 0000:00000000 <unknown>



--- Thread ID: 55 ---

7BC71D65 0819E688 0001:00060D65 C:\windows\system32\ntdll.dll

7BC72062 0819E6B8 0001:00061062 C:\windows\system32\ntdll.dll

7B88F972 0819E7F8 0001:0006E972 C:\windows\system32\KERNEL32.dll

7B88FACA 0819E818 0001:0006EACA C:\windows\system32\KERNEL32.dll

0046293B 0819EA70 0001:0006193B C:\Program Files\World of Warcraft\Wow.exe

004620CE 0819EA7C 0001:000610CE C:\Program Files\World of Warcraft\Wow.exe

0053BBE7 0819EA98 0001:0013ABE7 C:\Program Files\World of Warcraft\Wow.exe

7BC6B568 0819EAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 0819EB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 0819F3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 0819F4B8 0000:00000000 <unknown>



--- Thread ID: 54 ---

7BC71D65 0802E8B8 0001:00060D65 C:\windows\system32\ntdll.dll

7BC72062 0802E8E8 0001:00061062 C:\windows\system32\ntdll.dll

7B88F972 0802EA28 0001:0006E972 C:\windows\system32\KERNEL32.dll

7B88FB6C 0802EA48 0001:0006EB6C C:\windows\system32\KERNEL32.dll

00540210 0802EA58 0001:0013F210 C:\Program Files\World of Warcraft\Wow.exe

00462125 0802EA70 0001:00061125 C:\Program Files\World of Warcraft\Wow.exe

00462291 0802EA7C 0001:00061291 C:\Program Files\World of Warcraft\Wow.exe

0053BBE7 0802EA98 0001:0013ABE7 C:\Program Files\World of Warcraft\Wow.exe

7BC6B568 0802EAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 0802EB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 0802F3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 0802F4B8 0000:00000000 <unknown>



--- Thread ID: 53 ---

7BC71D65 07EBE8C8 0001:00060D65 C:\windows\system32\ntdll.dll

7BC72062 07EBE8F8 0001:00061062 C:\windows\system32\ntdll.dll

7B88F972 07EBEA38 0001:0006E972 C:\windows\system32\KERNEL32.dll

7B88FB6C 07EBEA58 0001:0006EB6C C:\windows\system32\KERNEL32.dll

00540210 07EBEA68 0001:0013F210 C:\Program Files\World of Warcraft\Wow.exe

007ADA89 07EBEA98 0001:003ACA89 C:\Program Files\World of Warcraft\Wow.exe

7BC6B568 07EBEAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 07EBEB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 07EBF3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 07EBF4B8 0000:00000000 <unknown>



--- Thread ID: 52 ---

7B88FC82 07D4EA58 0001:0006EC82 C:\windows\system32\KERNEL32.dll

7B88FCC5 07D4EA78 0001:0006ECC5 C:\windows\system32\KERNEL32.dll

008552DD 07D4EA84 0001:004542DD C:\Program Files\World of Warcraft\Wow.exe

00855B0C 07D4EA98 0001:00454B0C C:\Program Files\World of Warcraft\Wow.exe

7BC6B568 07D4EAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 07D4EB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 07D4F3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 07D4F4B8 0000:00000000 <unknown>



--- Thread ID: 51 ---

7B88FC82 07ACEA58 0001:0006EC82 C:\windows\system32\KERNEL32.dll

7B88FCC5 07ACEA78 0001:0006ECC5 C:\windows\system32\KERNEL32.dll

008552DD 07ACEA84 0001:004542DD C:\Program Files\World of Warcraft\Wow.exe

00855B0C 07ACEA98 0001:00454B0C C:\Program Files\World of Warcraft\Wow.exe

7BC6B568 07ACEAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 07ACEB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 07ACF3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 07ACF4B8 0000:00000000 <unknown>



--- Thread ID: 50 ---

7E01F2CB 0609EA48 0001:0000E2CB C:\windows\system32\winealsa.drv

7E031BFC 0609EA98 0001:00020BFC C:\windows\system32\winealsa.drv

7BC6B568 0609EAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 0609EB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 0609F3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 0609F4B8 0000:00000000 <unknown>



--- Thread ID: 49 ---

7B88FC82 0685EA58 0001:0006EC82 C:\windows\system32\KERNEL32.dll

7B88FCC5 0685EA78 0001:0006ECC5 C:\windows\system32\KERNEL32.dll

008552DD 0685EA84 0001:004542DD C:\Program Files\World of Warcraft\Wow.exe

00855B0C 0685EA98 0001:00454B0C C:\Program Files\World of Warcraft\Wow.exe

7BC6B568 0685EAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 0685EB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 0685F3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 0685F4B8 0000:00000000 <unknown>



--- Thread ID: 48 ---

7B88FC82 066EEA58 0001:0006EC82 C:\windows\system32\KERNEL32.dll

7B88FCC5 066EEA78 0001:0006ECC5 C:\windows\system32\KERNEL32.dll

008552DD 066EEA84 0001:004542DD C:\Program Files\World of Warcraft\Wow.exe

00855B0C 066EEA98 0001:00454B0C C:\Program Files\World of Warcraft\Wow.exe

7BC6B568 066EEAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 066EEB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 066EF3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 066EF4B8 0000:00000000 <unknown>



--- Thread ID: 46 ---

7EE03E47 0640EA98 0001:00022E47 C:\windows\system32\winmm.dll

7BC6B568 0640EAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 0640EB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 0640F3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 0640F4B8 0000:00000000 <unknown>



--- Thread ID: 44 ---

7BC71D65 040DE8C4 0001:00060D65 C:\windows\system32\ntdll.dll

7BC72062 040DE8F4 0001:00061062 C:\windows\system32\ntdll.dll

7B88F972 040DEA34 0001:0006E972 C:\windows\system32\KERNEL32.dll

7B88FB6C 040DEA54 0001:0006EB6C C:\windows\system32\KERNEL32.dll

00540210 040DEA64 0001:0013F210 C:\Program Files\World of Warcraft\Wow.exe

00477D72 040DEA7C 0001:00076D72 C:\Program Files\World of Warcraft\Wow.exe

0053BBE7 040DEA98 0001:0013ABE7 C:\Program Files\World of Warcraft\Wow.exe

7BC6B568 040DEAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 040DEB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 040DF3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 040DF4B8 0000:00000000 <unknown>



--- Thread ID: 43 ---

7B88FC82 03A0E630 0001:0006EC82 C:\windows\system32\KERNEL32.dll

7B88FCC5 03A0E650 0001:0006ECC5 C:\windows\system32\KERNEL32.dll

0046E92D 03A0E65C 0001:0006D92D C:\Program Files\World of Warcraft\Wow.exe

007DAAD5 03A0EA7C 0001:003D9AD5 C:\Program Files\World of Warcraft\Wow.exe

0053BBE7 03A0EA98 0001:0013ABE7 C:\Program Files\World of Warcraft\Wow.exe

7BC6B568 03A0EAA8 0001:0005A568 C:\windows\system32\ntdll.dll

7BC6B770 03A0EB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 03A0F3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 03A0F4B8 0000:00000000 <unknown>



--- Thread ID: 42 ---

7B88FC82 01CCEA10 0001:0006EC82 C:\windows\system32\KERNEL32.dll

7B88FCC5 01CCEA30 0001:0006ECC5 C:\windows\system32\KERNEL32.dll

004245E4 01CCEA58 0001:000235E4 C:\Program Files\World of Warcraft\Wow.exe

008D967F 01CCEA90 0001:004D867F C:\Program Files\World of Warcraft\Wow.exe

008D9724 01CCEAA8 0001:004D8724 C:\Program Files\World of Warcraft\Wow.exe

7BC6B770 01CCEB78 0001:0005A770 C:\windows\system32\ntdll.dll

7BC738EB 01CCF3B8 0001:000628EB C:\windows\system32\ntdll.dll

B7E434FF 01CCF4B8 0000:00000000 <unknown>



--- Thread ID: 38 [Current Thread] ---

7E8B61FB 003AFC64 0001:000D51FB C:\windows\system32\wined3d.dll

7E91BF47 003AFCA4 0001:0001AF47 C:\windows\system32\d3d9.dll

0063A2DD 003AFD18 0001:002392DD C:\Program Files\World of Warcraft\Wow.exe

0063A505 003AFD2C 0001:00239505 C:\Program Files\World of Warcraft\Wow.exe

0061E1EC 003AFD38 0001:0021D1EC C:\Program Files\World of Warcraft\Wow.exe

0061B954 003AFD5C 0001:0021A954 C:\Program Files\World of Warcraft\Wow.exe

007A5FFC 003AFDA0 0001:003A4FFC C:\Program Files\World of Warcraft\Wow.exe

008356B9 003AFDD0 0001:004346B9 C:\Program Files\World of Warcraft\Wow.exe

00833DAF 003AFE54 0001:00432DAF C:\Program Files\World of Warcraft\Wow.exe

00833F11 003AFE6C 0001:00432F11 C:\Program Files\World of Warcraft\Wow.exe

00406C7D 003AFF08 0001:00005C7D C:\Program Files\World of Warcraft\Wow.exe

7B878140 003AFFE8 0001:00057140 C:\windows\system32\KERNEL32.dll



----------------------------------------

    Stack Trace (Using DBGHELP.DLL)

----------------------------------------



Showing 21/21 threads...



--- Thread ID: 68 ---

7BC71D65 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x0D7AE6FC,0x00000004,0x00000000)

7BC72062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x0D7AE6FC,0x00000000,0x00000000)

7B88F972 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x0D7AE874,0x00000000,0xFFFFFFFF)

7E0AC9BB winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x0D7AE874,0xFFFFFFFF,0x00000000)

7ED13D05 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x0D7AEA3C,0xFFFFFFFF,0x00000000)

7ED13D6F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x0D7AEA3C,0x00000000,0xFFFFFFFF)

004415D9 Wow.exe      <unknown symbol>+0 (0x0106A320,0x7FF7C1D4,0x09F021C0,0x0D7AEA90)

004425DA Wow.exe      <unknown symbol>+0 (0x09F01BB0,0x4138B021,0x7FF7C1D4,0x09F021C0)

008D967F Wow.exe      <unknown symbol>+0 (0x7FF7CF10,0x7BC6B568,0x09F021C0,0x7FF7CF10)

008D9724 Wow.exe      <unknown symbol>+0 (0x008D96A5,0x09F021C0,0x00000000,0x00000000)

7BC6B770 ntdll.dll    call_thread_entry_point+112 (0x008D96A5,0x09F021C0,0x00000000,0x00000000)

7BC738EB ntdll.dll    <unknown symbol>+0 (0x7FF7CFB8,0x0D7AFB90,0x0D7AFB90,0x0D7AFB90)

B7E434FF              start_thread+191 (0x0D7AFB90,0x00000000,0x00000000,0x00000000)

B7DBD49E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 67 ---

7BC71D65 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x0D63E6FC,0x00000004,0x00000000)

7BC72062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x0D63E6FC,0x00000000,0x00000000)

7B88F972 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x0D63E874,0x00000000,0xFFFFFFFF)

7E0AC9BB winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x0D63E874,0xFFFFFFFF,0x00000000)

7ED13D05 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x0D63EA3C,0xFFFFFFFF,0x00000000)

7ED13D6F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x0D63EA3C,0x00000000,0xFFFFFFFF)

004415D9 Wow.exe      <unknown symbol>+0 (0x0106A2D8,0x7FF801D4,0x09AA87D0,0x0D63EA90)

004425DA Wow.exe      <unknown symbol>+0 (0x097D03B8,0x4121B021,0x7FF801D4,0x09AA87D0)

008D967F Wow.exe      <unknown symbol>+0 (0x7FF80F10,0x7BC6B568,0x09AA87D0,0x7FF80F10)

008D9724 Wow.exe      <unknown symbol>+0 (0x008D96A5,0x09AA87D0,0x00000000,0x00000000)

7BC6B770 ntdll.dll    call_thread_entry_point+112 (0x008D96A5,0x09AA87D0,0x00000000,0x00000000)

7BC738EB ntdll.dll    <unknown symbol>+0 (0x7FF80FB8,0x0D63FB90,0x0D63FB90,0x0D63FB90)

B7E434FF              start_thread+191 (0x0D63FB90,0x00000000,0x00000000,0x00000000)

B7DBD49E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 66 ---

7BC71D65 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0D4CE924,0x00000004,0x0D4CEA24)

7BC72062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0D4CE924,0x00000000,0x00000000)

7B88F972 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x0D4CEA64,0x00000000,0x00000064)

7B88FB6C KERNEL32.dll WaitForSingleObject+60 (0x00002254,0x00000064,0x0D4CEA7C,0x008F15C6)

00540210 Wow.exe      <unknown symbol>+0 (0x00000064,0x008F15B0,0x0D4CEA98,0x0053BBE7)

008F15C6 Wow.exe      <unknown symbol>+0 (0x09B7E328,0x7FF841D4,0x7FF84F10,0x7BC94FF4)

0053BBE7 Wow.exe      <unknown symbol>+0 (0x00002258,0x7FF84F10,0x0D4CEB78,0x7BC6B770)

7BC6B568 ntdll.dll    call_thread_func+12 (0x0053BB90,0x09798E60,0x00000000,0x00000000)

7BC6B770 ntdll.dll    call_thread_entry_point+112 (0x0053BB90,0x09798E60,0x00000000,0x00000000)

7BC738EB ntdll.dll    <unknown symbol>+0 (0x7FF84FB8,0x0D4CFB90,0x0D4CFB90,0x0D4CFB90)

B7E434FF              start_thread+191 (0x0D4CFB90,0x00000000,0x00000000,0x00000000)

B7DBD49E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 65 ---

7BC71D65 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x0657E6FC,0x00000004,0x00000000)

7BC72062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x0657E6FC,0x00000000,0x00000000)

7B88F972 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x0657E874,0x00000000,0xFFFFFFFF)

7E0AC9BB winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x0657E874,0xFFFFFFFF,0x00000000)

7ED13D05 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x0657EA3C,0xFFFFFFFF,0x00000000)

7ED13D6F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x0657EA3C,0x00000000,0xFFFFFFFF)

004415D9 Wow.exe      <unknown symbol>+0 (0x0106A278,0x7FFC01D4,0x04DAFBA0,0x0657EA90)

004425DA Wow.exe      <unknown symbol>+0 (0x078032E8,0x4A15B021,0x7FFC01D4,0x04DAFBA0)

008D967F Wow.exe      <unknown symbol>+0 (0x7FFC0F10,0x7BC6B568,0x04DAFBA0,0x7FFC0F10)

008D9724 Wow.exe      <unknown symbol>+0 (0x008D96A5,0x04DAFBA0,0x00000000,0x00000000)

7BC6B770 ntdll.dll    call_thread_entry_point+112 (0x008D96A5,0x04DAFBA0,0x00000000,0x00000000)

7BC738EB ntdll.dll    <unknown symbol>+0 (0x7FFC0FB8,0x0657FB90,0x0657FB90,0x0657FB90)

B7E434FF              start_thread+191 (0x0657FB90,0x00000000,0x00000000,0x00000000)

B7DBD49E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 62 ---

7BC71D65 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0C3CE920,0x00000004,0x00000000)

7BC72062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0C3CE920,0x00000000,0x00000000)

7B88F972 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x0C3CEA60,0x00000000,0xFFFFFFFF)

7B88FB6C KERNEL32.dll WaitForSingleObject+60 (0x00002228,0xFFFFFFFF,0x7FF881D4,0x077FA684)

00895FF5 Wow.exe      <unknown symbol>+0 (0x0983C2F8,0xFFFFFFFF,0x0C3CEA98,0x00855AD0)

0085547A Wow.exe      <unknown symbol>+0 (0x0983C2F8,0x7FF88F10,0x0000003E,0x0C3CEAA8)

00855AD0 Wow.exe      <unknown symbol>+0 (0x077FA684,0x7FF88F10,0x0C3CEB78,0x7BC6B770)

7BC6B568 ntdll.dll    call_thread_func+12 (0x00855A90,0x077FA684,0x00000000,0x00000000)

7BC6B770 ntdll.dll    call_thread_entry_point+112 (0x00855A90,0x077FA684,0x00000000,0x00000000)

7BC738EB ntdll.dll    <unknown symbol>+0 (0x7FF88FB8,0x0C3CFB90,0x0C3CFB90,0x0C3CFB90)

B7E434FF              start_thread+191 (0x0C3CFB90,0x00000000,0x00000000,0x00000000)

B7DBD49E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 59 ---

7BC71D65 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x0BC4E6FC,0x00000004,0x00000000)

7BC72062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x0BC4E6FC,0x00000000,0x00000000)

7B88F972 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x0BC4E874,0x00000000,0xFFFFFFFF)

7E0AC9BB winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x0BC4E874,0xFFFFFFFF,0x00000000)

7ED13D05 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x0BC4EA3C,0xFFFFFFFF,0x00000000)

7ED13D6F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x0BC4EA3C,0x00000000,0xFFFFFFFF)

004415D9 Wow.exe      <unknown symbol>+0 (0x0106A218,0x7FF941D4,0x0985CDB8,0x0BC4EA90)

004425DA Wow.exe      <unknown symbol>+0 (0x0985BC10,0x4786B021,0x7FF941D4,0x0985CDB8)

008D967F Wow.exe      <unknown symbol>+0 (0x7FF94F10,0x7BC6B568,0x0985CDB8,0x7FF94F10)

008D9724 Wow.exe      <unknown symbol>+0 (0x008D96A5,0x0985CDB8,0x00000000,0x00000000)

7BC6B770 ntdll.dll    call_thread_entry_point+112 (0x008D96A5,0x0985CDB8,0x00000000,0x00000000)

7BC738EB ntdll.dll    <unknown symbol>+0 (0x7FF94FB8,0x0BC4FB90,0x0BC4FB90,0x0BC4FB90)

B7E434FF              start_thread+191 (0x0BC4FB90,0x00000000,0x00000000,0x00000000)

B7DBD49E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 58 ---

7BC71D65 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0BADE920,0x00000004,0x00000000)

7BC72062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0BADE920,0x00000000,0x00000000)

7B88F972 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x0BADEA60,0x00000000,0xFFFFFFFF)

7B88FB6C KERNEL32.dll WaitForSingleObject+60 (0x000021DC,0xFFFFFFFF,0x7FF981D4,0x0985A80C)

00895FF5 Wow.exe      <unknown symbol>+0 (0x0985A9A0,0xFFFFFFFF,0x0BADEA98,0x00855AD0)

0085547A Wow.exe      <unknown symbol>+0 (0x0985A9A0,0x7FF98F10,0x0000003A,0x0BADEAA8)

00855AD0 Wow.exe      <unknown symbol>+0 (0x0985A80C,0x7FF98F10,0x0BADEB78,0x7BC6B770)

7BC6B568 ntdll.dll    call_thread_func+12 (0x00855A90,0x0985A80C,0x00000000,0x00000000)

7BC6B770 ntdll.dll    call_thread_entry_point+112 (0x00855A90,0x0985A80C,0x00000000,0x00000000)

7BC738EB ntdll.dll    <unknown symbol>+0 (0x7FF98FB8,0x0BADFB90,0x0BADFB90,0x0BADFB90)

B7E434FF              start_thread+191 (0x0BADFB90,0x00000000,0x00000000,0x00000000)

B7DBD49E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 56 ---

7BC71D65 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x0830E6FC,0x00000004,0x00000000)

7BC72062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x0830E6FC,0x00000000,0x00000000)

7B88F972 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x0830E874,0x00000000,0xFFFFFFFF)

7E0AC9BB winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x0830E874,0xFFFFFFFF,0x00000000)

7ED13D05 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x0830EA3C,0xFFFFFFFF,0x00000000)

7ED13D6F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x0830EA3C,0x00000000,0xFFFFFFFF)

004415D9 Wow.exe      <unknown symbol>+0 (0x0106A1D0,0x7FFA01D4,0x0762E700,0x0830EA90)

004425DA Wow.exe      <unknown symbol>+0 (0x0762E6A0,0x4472B021,0x7FFA01D4,0x0762E700)

008D967F Wow.exe      <unknown symbol>+0 (0x7FFA0F10,0x7BC6B568,0x0762E700,0x7FFA0F10)

008D9724 Wow.exe      <unknown symbol>+0 (0x008D96A5,0x0762E700,0x00000000,0x00000000)

7BC6B770 ntdll.dll    call_thread_entry_point+112 (0x008D96A5,0x0762E700,0x00000000,0x00000000)

7BC738EB ntdll.dll    <unknown symbol>+0 (0x7FFA0FB8,0x0830FB90,0x0830FB90,0x0830FB90)

B7E434FF              start_thread+191 (0x0830FB90,0x00000000,0x00000000,0x00000000)

B7DBD49E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 55 ---

7BC71D65 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000002,0x0819E6E0,0x00000004,0x0819E7E0)

7BC72062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000002,0x0819E6E0,0x00000000,0x00000000)

7B88F972 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000002,0x0819E93C,0x00000000,0x000001F4)

7B88FACA KERNEL32.dll WaitForMultipleObjects+58 (0x00000002,0x0819E93C,0x00000000,0x000001F4)

0046293B Wow.exe      <unknown symbol>+0 (0x004620C0,0x0819EA98,0x0053BBE7,0x0759FBC8)

004620CE Wow.exe      <unknown symbol>+0 (0x0759FBC8,0x7FFA41D4,0x7FFA4F10,0x7BC94FF4)

0053BBE7 Wow.exe      <unknown symbol>+0 (0x000021B4,0x7FFA4F10,0x0819EB78,0x7BC6B770)

7BC6B568 ntdll.dll    call_thread_func+12 (0x0053BB90,0x07423378,0x00000000,0x00000000)

7BC6B770 ntdll.dll    call_thread_entry_point+112 (0x0053BB90,0x07423378,0x00000000,0x00000000)

7BC738EB ntdll.dll    <unknown symbol>+0 (0x7FFA4FB8,0x0819FB90,0x0819FB90,0x0819FB90)

B7E434FF              start_thread+191 (0x0819FB90,0x00000000,0x00000000,0x00000000)

B7DBD49E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 54 ---

7BC71D65 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0802E910,0x00000004,0x0802EA10)

7BC72062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0802E910,0x00000000,0x00000000)

7B88F972 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x0802EA50,0x00000000,0x000003E8)

7B88FB6C KERNEL32.dll WaitForSingleObject+60 (0x00002124,0x000003E8,0x0802EA70,0x00462125)

00540210 Wow.exe      <unknown symbol>+0 (0x000003E8,0x00000036,0x00462280,0x0759FBD8)

00462125 Wow.exe      <unknown symbol>+0 (0x00000000,0x0802EA98,0x0053BBE7,0x0759FBD8)

00462291 Wow.exe      <unknown symbol>+0 (0x0759FBD8,0x7FFA81D4,0x7FFA8F10,0x7BC94FF4)

0053BBE7 Wow.exe      <unknown symbol>+0 (0x000021B0,0x7FFA8F10,0x0802EB78,0x7BC6B770)

7BC6B568 ntdll.dll    call_thread_func+12 (0x0053BB90,0x07423378,0x00000000,0x00000000)

7BC6B770 ntdll.dll    call_thread_entry_point+112 (0x0053BB90,0x07423378,0x00000000,0x00000000)

7BC738EB ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x0802FB90,0x0802FB90,0x0802FB90)

B7E434FF              start_thread+191 (0x0802FB90,0x00000000,0x00000000,0x00000000)

B7DBD49E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 53 ---

7BC71D65 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x07EBE920,0x00000004,0x00000000)

7BC72062 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x07EB[/PHP]

---

### Post by firewall_03 on 2009-07-04
any ideas?

---

### Post by Dimarchi on 2009-07-06
The best advice I can offer is to run Repair.exe, which should be in the same folder with the rest of WoW stuff. The program checks for errors and tries to repair them if possible. It will give you the possibility of resetting some stuff, such as cache and addons (in other words, clean slate).

---

