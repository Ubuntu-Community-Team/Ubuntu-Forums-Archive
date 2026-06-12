---
title: "WoW on Ubuntu Netbook Edition (10.04)"
date: 2010-07-04
forum: Wine
---

### Post by Felrohan on 2010-07-04
Hello everyone, i just installed Ubuntu Netbook Edition  (UNE) 10.04 on my Gateway LT2104u Netbook. I have Wine installed also. I  keep trying to run WoW through Wine, but I keep getting the bellow  error, i have tried numerous things to get it to run properly, but it  won't. Strange thing is though when i load the launcher, the  launcherpage shows up and even the sound works when you move past the  launcher page lol I can hear the opening music that you get when you  have to scroll down and press "Accept" these terms. 

Here is the error that shows up: 
```

=================================================================================== 
World of WarCraft (build 12340) 

Exe:      Z:\home\felrohan\Desktop\World of Warcraft\Wow.exe 
Time:     Jul  3, 2010  9:38:28.322 PM 
User:     felrohan 
Computer: felrohan-laptop 
------------------------------------------------------------------------------ 

This application has encountered a critical error: 

ERROR #132 (0x85100084) Fatal Exception 
Program:	Z:\home\felrohan\Desktop\World of Warcraft\Wow.exe 
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:3747714E 

The instruction at "0x3747714E" referenced memory at  "0x3747714E". 
The memory could not be "read". 


WoWBuild: 12340 
Settings:  
SET readTOS "1" 
SET readEULA "1" 
SET readScanning "-1" 
SET readContest "-1" 
SET readTerminationWithoutNotice "-1" 
SET installType "Retail" 
SET locale "enUS" 
SET movie "0" 
SET showToolsUI "1" 
SET portal "us" 
SET realmList "us.logon.worldofwarcraft.com" 
SET patchlist "us.version.worldofwarcraft.com" 
SET hwDetect "0" 
SET gxRefresh "60" 
SET gxMultisampleQuality "0.000000" 
SET gxFixLag "0" 
SET videoOptionsVersion "3" 
SET textureFilteringMode "0" 
SET mouseSpeed "1" 
SET Gamma "1.000000" 
SET lastCharacterIndex "9" 
SET accounttype "LK" 
SET VoiceActivationSensitivity "0.39999997615814" 
SET Sound_OutputDriverName "System Default" 
SET ChatMusicVolume "0.29999998211861" 
SET ChatSoundVolume "0.39999997615814" 
SET ChatAmbienceVolume "0.29999998211861" 
SET Sound_MusicVolume "0.40000000596046" 
SET Sound_AmbienceVolume "0.60000002384186" 
SET MaxLights "1" 
SET farclip "177" 
SET particleDensity "0.10000000149012" 
SET baseMip "1" 
SET environmentDetail "0.5" 
SET weatherDensity "0" 
SET realmName "The Venture Co" 
SET gameTip "6" 
SET gxResolution "1024x600" 
SET timingTestError "0" 
SET gxTripleBuffer "1" 
SET ffxGlow "0" 
SET ffxDeath "0" 
SET gxWindow "1" 
SET gxAPI "OpenGL" 

---------------------------------------- 
               GxInfo 
---------------------------------------- 
GxApi: OpenGL 
Vendor: Tungsten Graphics, Inc 
Renderer: Mesa DRI Intel(R) IGD GEM 20091221 2009Q4 x86/MMX/SSE2 
Version: 1.4 Mesa 7.7.1 

------------------------------------------------------------------------------ 

---------------------------------------- 
    x86 Registers 
---------------------------------------- 

EAX=00000001  EBX=067D5D9C  ECX=00000004  EDX=00000001  ESI=067D5D88 
EDI=01D41A20  EBP=0195F958  ESP=0195F940  EIP=3747714E  FLG=00210202 
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033       GS =003B 


---------------------------------------- 
    Stack Trace (Manual) 
---------------------------------------- 

Address  Frame    Logical addr  Module 

Showing 20/20 threads... 

--- Thread ID: 51 --- 
7BC76263 0A6EE5E8 0001:00065263 C:\windows\system32\ntdll.dll 
7BC76553 0A6EE628 0001:00065553 C:\windows\system32\ntdll.dll 
7B869E56 0A6EE778 0001:00058E56 C:\windows\system32\KERNEL32.dll 
68D0579C 0A6EE7B8 0001:0003479C C:\windows\system32\winex11.drv 
685B65F8 0A6EE7F8 0001:000955F8 C:\windows\system32\user32.dll 
6857CD9A 0A6EE9B8 0001:0005BD9A C:\windows\system32\user32.dll 
6857CDEF 0A6EE9E8 0001:0005BDEF C:\windows\system32\user32.dll 
0044CFA6 0A6EEA14 0001:0004BFA6 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0044DF1A 0A6EEA28 0001:0004CF1A Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0088C5DF 0A6EEA60 0001:0048B5DF Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0088C684 0A6EEA78 0001:0048B684 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F750 0A6EEB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 0A6EF398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 0A6EF498 0000:00000000 <unknown> 

--- Thread ID: 46 --- 
7BC76263 0A40E988 0001:00065263 C:\windows\system32\ntdll.dll 
7BC76553 0A40E9C8 0001:00065553 C:\windows\system32\ntdll.dll 
7BC765AC 0A40E9F8 0001:000655AC C:\windows\system32\ntdll.dll 
7BC7B67F 0A40EA68 0001:0006A67F C:\windows\system32\ntdll.dll 
7BC6F584 0A40EA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 0A40EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 0A40F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 0A40F498 0000:00000000 <unknown> 

--- Thread ID: 45 --- 
7BC76263 0A29E868 0001:00065263 C:\windows\system32\ntdll.dll 
7BC76553 0A29E8A8 0001:00065553 C:\windows\system32\ntdll.dll 
7B869E56 0A29E9F8 0001:00058E56 C:\windows\system32\KERNEL32.dll 
7B869F6C 0A29EA28 0001:00058F6C C:\windows\system32\KERNEL32.dll 
008E4FA5 0A29EA44 0001:004E3FA5 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
008D2029 0A29EA54 0001:004D1029 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
008E51D0 0A29EA68 0001:004E41D0 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F584 0A29EA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 0A29EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 0A29F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 0A29F498 0000:00000000 <unknown> 

--- Thread ID: 44 --- 
7BC76263 0A12E5E8 0001:00065263 C:\windows\system32\ntdll.dll 
7BC76553 0A12E628 0001:00065553 C:\windows\system32\ntdll.dll 
7B869E56 0A12E778 0001:00058E56 C:\windows\system32\KERNEL32.dll 
68D0579C 0A12E7B8 0001:0003479C C:\windows\system32\winex11.drv 
685B65F8 0A12E7F8 0001:000955F8 C:\windows\system32\user32.dll 
6857CD9A 0A12E9B8 0001:0005BD9A C:\windows\system32\user32.dll 
6857CDEF 0A12E9E8 0001:0005BDEF C:\windows\system32\user32.dll 
0044CFA6 0A12EA14 0001:0004BFA6 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0044DF1A 0A12EA28 0001:0004CF1A Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0088C5DF 0A12EA60 0001:0048B5DF Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0088C684 0A12EA78 0001:0048B684 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F750 0A12EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 0A12F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 0A12F498 0000:00000000 <unknown> 

--- Thread ID: 43 --- 
7BC76263 09FBE868 0001:00065263 C:\windows\system32\ntdll.dll 
7BC76553 09FBE8A8 0001:00065553 C:\windows\system32\ntdll.dll 
7B869E56 09FBE9F8 0001:00058E56 C:\windows\system32\KERNEL32.dll 
7B869F6C 09FBEA28 0001:00058F6C C:\windows\system32\KERNEL32.dll 
008E4FA5 09FBEA44 0001:004E3FA5 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
008D2029 09FBEA54 0001:004D1029 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
008E51D0 09FBEA68 0001:004E41D0 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F584 09FBEA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 09FBEB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 09FBF398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 09FBF498 0000:00000000 <unknown> 

--- Thread ID: 42 --- 
7BC76263 09E4E988 0001:00065263 C:\windows\system32\ntdll.dll 
7BC76553 09E4E9C8 0001:00065553 C:\windows\system32\ntdll.dll 
7BC765AC 09E4E9F8 0001:000655AC C:\windows\system32\ntdll.dll 
7BC7B67F 09E4EA68 0001:0006A67F C:\windows\system32\ntdll.dll 
7BC6F584 09E4EA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 09E4EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 09E4F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 09E4F498 0000:00000000 <unknown> 

--- Thread ID: 41 --- 
7BC76263 09CDE988 0001:00065263 C:\windows\system32\ntdll.dll 
7BC76553 09CDE9C8 0001:00065553 C:\windows\system32\ntdll.dll 
7BC765AC 09CDE9F8 0001:000655AC C:\windows\system32\ntdll.dll 
7BC7B67F 09CDEA68 0001:0006A67F C:\windows\system32\ntdll.dll 
7BC6F584 09CDEA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 09CDEB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 09CDF398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 09CDF498 0000:00000000 <unknown> 

--- Thread ID: 40 --- 
7BC76263 0989E5E8 0001:00065263 C:\windows\system32\ntdll.dll 
7BC76553 0989E628 0001:00065553 C:\windows\system32\ntdll.dll 
7B869E56 0989E778 0001:00058E56 C:\windows\system32\KERNEL32.dll 
68D0579C 0989E7B8 0001:0003479C C:\windows\system32\winex11.drv 
685B65F8 0989E7F8 0001:000955F8 C:\windows\system32\user32.dll 
6857CD9A 0989E9B8 0001:0005BD9A C:\windows\system32\user32.dll 
6857CDEF 0989E9E8 0001:0005BDEF C:\windows\system32\user32.dll 
0044CFA6 0989EA14 0001:0004BFA6 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0044DF1A 0989EA28 0001:0004CF1A Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0088C5DF 0989EA60 0001:0048B5DF Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0088C684 0989EA78 0001:0048B684 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F750 0989EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 0989F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 0989F498 0000:00000000 <unknown> 

--- Thread ID: 39 --- 
7BC76263 08E0E61C 0001:00065263 C:\windows\system32\ntdll.dll 
7BC76553 08E0E65C 0001:00065553 C:\windows\system32\ntdll.dll 
7B869E56 08E0E7AC 0001:00058E56 C:\windows\system32\KERNEL32.dll 
7B869ECA 08E0E7DC 0001:00058ECA C:\windows\system32\KERNEL32.dll 
004699CB 08E0EA34 0001:000689CB Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0046906E 08E0EA40 0001:0006806E Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0076FFCB 08E0EA68 0001:0036EFCB Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F584 08E0EA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 08E0EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 08E0F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 08E0F498 0000:00000000 <unknown> 

--- Thread ID: 38 --- 
7BC76263 08C9E84C 0001:00065263 C:\windows\system32\ntdll.dll 
7BC76553 08C9E88C 0001:00065553 C:\windows\system32\ntdll.dll 
7B869E56 08C9E9DC 0001:00058E56 C:\windows\system32\KERNEL32.dll 
7B869F6C 08C9EA0C 0001:00058F6C C:\windows\system32\KERNEL32.dll 
007746A0 08C9EA1C 0001:003736A0 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
004691A5 08C9EA34 0001:000681A5 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
00469311 08C9EA40 0001:00068311 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0076FFCB 08C9EA68 0001:0036EFCB Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F584 08C9EA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 08C9EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 08C9F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 08C9F498 0000:00000000 <unknown> 

--- Thread ID: 37 --- 
7BC76263 08B2E864 0001:00065263 C:\windows\system32\ntdll.dll 
7BC76553 08B2E8A4 0001:00065553 C:\windows\system32\ntdll.dll 
7B869E56 08B2E9F4 0001:00058E56 C:\windows\system32\KERNEL32.dll 
7B869F6C 08B2EA24 0001:00058F6C C:\windows\system32\KERNEL32.dll 
007746A0 08B2EA34 0001:003736A0 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
004F12CB 08B2EA68 0001:000F02CB Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F584 08B2EA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 08B2EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 08B2F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 08B2F498 0000:00000000 <unknown> 

--- Thread ID: 36 --- 
7B869FE1 0611EA28 0001:00058FE1 C:\windows\system32\KERNEL32.dll 
7B86A025 0611EA48 0001:00059025 C:\windows\system32\KERNEL32.dll 
008D1E8D 0611EA54 0001:004D0E8D Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
008E520C 0611EA68 0001:004E420C Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F584 0611EA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 0611EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 0611F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 0611F498 0000:00000000 <unknown> 

--- Thread ID: 35 --- 
7B869FE1 05FAEA28 0001:00058FE1 C:\windows\system32\KERNEL32.dll 
7B86A025 05FAEA48 0001:00059025 C:\windows\system32\KERNEL32.dll 
008D1E8D 05FAEA54 0001:004D0E8D Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
008E520C 05FAEA68 0001:004E420C Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F584 05FAEA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 05FAEB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 05FAF398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 05FAF498 0000:00000000 <unknown> 

--- Thread ID: 34 --- 
7B869FE1 05E3EA28 0001:00058FE1 C:\windows\system32\KERNEL32.dll 
7B86A025 05E3EA48 0001:00059025 C:\windows\system32\KERNEL32.dll 
008D1E8D 05E3EA54 0001:004D0E8D Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
008E520C 05E3EA68 0001:004E420C Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F584 05E3EA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 05E3EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 05E3F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 05E3F498 0000:00000000 <unknown> 

--- Thread ID: 33 --- 
7B869FE1 05CCEA28 0001:00058FE1 C:\windows\system32\KERNEL32.dll 
7B86A025 05CCEA48 0001:00059025 C:\windows\system32\KERNEL32.dll 
008D1E8D 05CCEA54 0001:004D0E8D Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
008E520C 05CCEA68 0001:004E420C Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F584 05CCEA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 05CCEB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 05CCF398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 05CCF498 0000:00000000 <unknown> 

--- Thread ID: 32 --- 
68BB0817 05B5EA68 0001:0001F817 C:\windows\system32\winmm.dll 
7BC6F584 05B5EA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 05B5EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 05B5F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 05B5F498 0000:00000000 <unknown> 

--- Thread ID: 31 --- 
7BC76263 0289E858 0001:00065263 C:\windows\system32\ntdll.dll 
7BC76553 0289E898 0001:00065553 C:\windows\system32\ntdll.dll 
7B869E56 0289E9E8 0001:00058E56 C:\windows\system32\KERNEL32.dll 
7B869F6C 0289EA18 0001:00058F6C C:\windows\system32\KERNEL32.dll 
007746A0 0289EA28 0001:003736A0 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0081C042 0289EA40 0001:0041B042 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0076FFCB 0289EA68 0001:0036EFCB Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F584 0289EA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 0289EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 0289F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 0289F498 0000:00000000 <unknown> 

--- Thread ID: 30 --- 
7B869FE1 0255E5F4 0001:00058FE1 C:\windows\system32\KERNEL32.dll 
7B86A025 0255E614 0001:00059025 C:\windows\system32\KERNEL32.dll 
0086B28D 0255E620 0001:0046A28D Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
004BA8BD 0255EA40 0001:000B98BD Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0076FFCB 0255EA68 0001:0036EFCB Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F584 0255EA78 0001:0005E584 C:\windows\system32\ntdll.dll 
7BC6F750 0255EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 0255F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 0255F498 0000:00000000 <unknown> 

--- Thread ID: 29 --- 
7B869FE1 01A5E9D4 0001:00058FE1 C:\windows\system32\KERNEL32.dll 
7B86A025 01A5E9F4 0001:00059025 C:\windows\system32\KERNEL32.dll 
00438935 01A5EA14 0001:00037935 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0044DF1A 01A5EA28 0001:0004CF1A Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0088C5DF 01A5EA60 0001:0048B5DF Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0088C684 01A5EA78 0001:0048B684 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7BC6F750 01A5EB48 0001:0005E750 C:\windows\system32\ntdll.dll 
7BC77F35 01A5F398 0001:00066F35 C:\windows\system32\ntdll.dll 
6ACC696E 01A5F498 0000:00000000 <unknown> 

--- Thread ID: 26 [Current Thread] --- 
3747714E 0195F958 0000:00000000 <unknown> 
0068B4F8 0195F978 0001:0028A4F8 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
00836144 0195F9AC 0001:00435144 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
00820583 0195F9CC 0001:0041F583 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
00823A88 0195FAA0 0001:00422A88 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
00823D24 0195FB7C 0001:00422D24 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0095FF4E 0195FC54 0001:0055EF4E Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
004E621B 0195FC78 0001:000E521B Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
00485128 0195FD38 0001:00084128 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
00494F67 0195FD54 0001:00093F67 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0049545B 0195FD70 0001:0009445B Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
004A8A42 0195FE3C 0001:000A7A42 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
00480B79 0195FE6C 0001:0007FB79 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0047DC89 0195FE94 0001:0007CC89 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0047F29A 0195FEE8 0001:0007E29A Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0047F2E1 0195FF00 0001:0007E2E1 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
0040B7D8 0195FF08 0001:0000A7D8 Z:\home\felrohan\Desktop\World  of Warcraft\Wow.exe 
7B837683 0195FFE8 0001:00026683 C:\windows\system32\KERNEL32.dll 

---------------------------------------- 
    Stack Trace (Using DBGHELP.DLL) 
---------------------------------------- 

Showing 20/20 threads... 

--- Thread ID: 51 --- 
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595  (0x00000003,0x00000004,0x00000000,0x00000000) 
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99  (0x00000003,0x00000000,0x00000000,0x00000000) 
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246  (0x00000003,0x00000000,0x00000000,0x00000000) 
68D0579C winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+268  (0x00000003,0xFFFFFFFF,0x00000000,0x00000000) 
685B65F8 user32.dll   <unknown symbol>+0 (0x00000003,0xFFFFFFFF,0x00000000,0x7BC99FF4) 
6857CD9A user32.dll   MsgWaitForMultipleObjectsEx+250  (0x00000002,0xFFFFFFFF,0x00000000,0x0044CD87) 
6857CDEF user32.dll   MsgWaitForMultipleObjects+63  (0x00000002,0x00000000,0x00000000,0x06ABE5F0) 
0044CFA6 Wow.exe      <unknown symbol>+0 (0x00B33A00,0x06ED32A0,0x0088C5DF,0x8475F3BB) 
0044DF1A Wow.exe      <unknown symbol>+0 (0x06ABE5F0,0x0088C605,0x7BC99FF4,0x0A6EEA34) 
0088C5DF Wow.exe      <unknown symbol>+0 (0x7FF88F10,0x06ED32A0,0x0A6EEB48,0x0088C605) 
0088C684 Wow.exe      <unknown symbol>+0 (0x0088C605,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x0088C605,0x00000000,0x00000000,0x7FF881BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FF88FB8,0x0A6EFB70,0x0A6EF454,0x00000000) 
6ACC696E              start_thread+190 (0x0A6EFB70,0x00000000,0x00000000,0x00000000)
```

---

### Post by Felrohan on 2010-07-04
```
--- Thread ID: 46 --- 
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595  (0x00000001,0x00000004,0x00000000,0x0A40E9C8) 
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99  (0x00000001,0x00000000,0x0A40EA48,0x00000000) 
7BC765AC ntdll.dll    NtWaitForSingleObject+60  (0x000021D0,0x0A40EA48,0x00111748,0x0A40EB08) 
7BC7B67F ntdll.dll    <unknown symbol>+0 (0x00000000,0x0A40EB48,0x7BC7B540,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x7BC7B540,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x7BC7B540,0x00000000,0x00000000,0x7FF901BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FF90FB8,0x0A40FB70,0x0A40F454,0x00000000) 
6ACC696E              start_thread+190 (0x0A40FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 45 --- 
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595  (0x00000001,0x00000004,0x00000000,0x7BC354D1) 
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99  (0x00000001,0x00000000,0x00000000,0x06BE5768) 
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246  (0x00000001,0x00000000,0x00000000,0x00000000) 
7B869F6C KERNEL32.dll WaitForSingleObject+60  (0x00002214,0x008E5190,0x7BC99FF4,0x008D2029) 
008E4FA5 Wow.exe      <unknown symbol>+0 (0x06BD2550,0x0A29EA68,0x06BD2550,0x0000002D) 
008D2029 Wow.exe      <unknown symbol>+0 (0x06BD2550,0x0000002D,0x7BC6F584,0x7FF94F10) 
008E51D0 Wow.exe      <unknown symbol>+0 (0x06BE741C,0x0A29EB48,0x008E5190,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x008E5190,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x008E5190,0x00000000,0x00000000,0x7FF941BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FF94FB8,0x0A29FB70,0x0A29F454,0x00000000) 
6ACC696E              start_thread+190 (0x0A29FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 44 --- 
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595  (0x00000003,0x00000004,0x00000000,0x00000000) 
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99  (0x00000003,0x00000000,0x00000000,0x00000000) 
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246  (0x00000003,0x00000000,0x00000000,0x00000000) 
68D0579C winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+268  (0x00000003,0xFFFFFFFF,0x00000000,0x00000000) 
685B65F8 user32.dll   <unknown symbol>+0 (0x00000003,0xFFFFFFFF,0x00000000,0x7BC99FF4) 
6857CD9A user32.dll   MsgWaitForMultipleObjectsEx+250  (0x00000002,0xFFFFFFFF,0x00000000,0x0044CD87) 
6857CDEF user32.dll   MsgWaitForMultipleObjects+63  (0x00000002,0x00000000,0x00000000,0x06BE7D28) 
0044CFA6 Wow.exe      <unknown symbol>+0 (0x00B339A0,0x06BE7D80,0x0088C5DF,0x8409F3BB) 
0044DF1A Wow.exe      <unknown symbol>+0 (0x06BE7D28,0x0088C605,0x7BC99FF4,0x0A12EA34) 
0088C5DF Wow.exe      <unknown symbol>+0 (0x7FF98F10,0x06BE7D80,0x0A12EB48,0x0088C605) 
0088C684 Wow.exe      <unknown symbol>+0 (0x0088C605,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x0088C605,0x00000000,0x00000000,0x7FF981BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FF98FB8,0x0A12FB70,0x0A12F454,0x00000000) 
6ACC696E              start_thread+190 (0x0A12FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 43 --- 
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595  (0x00000001,0x00000004,0x00000000,0x00000000) 
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99  (0x00000001,0x00000000,0x00000000,0x00000000) 
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246  (0x00000001,0x00000000,0x00000000,0x00000000) 
7B869F6C KERNEL32.dll WaitForSingleObject+60  (0x000021E4,0x008E5190,0x7BC99FF4,0x008D2029) 
008E4FA5 Wow.exe      <unknown symbol>+0 (0x06BE55C0,0x09FBEA68,0x06BE55C0,0x0000002B) 
008D2029 Wow.exe      <unknown symbol>+0 (0x06BE55C0,0x0000002B,0x7BC6F584,0x7FF9CF10) 
008E51D0 Wow.exe      <unknown symbol>+0 (0x06BE542C,0x09FBEB48,0x008E5190,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x008E5190,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x008E5190,0x00000000,0x00000000,0x7FF9C1BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FF9CFB8,0x09FBFB70,0x09FBF454,0x00000000) 
6ACC696E              start_thread+190 (0x09FBFB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 42 --- 
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595  (0x00000001,0x00000004,0x00000000,0x09E4E9C8) 
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99  (0x00000001,0x00000000,0x09E4EA48,0x00000000) 
7BC765AC ntdll.dll    NtWaitForSingleObject+60  (0x000021D0,0x09E4EA48,0x00111748,0x09E4EB08) 
7BC7B67F ntdll.dll    <unknown symbol>+0 (0x00000000,0x09E4EB48,0x7BC7B540,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x7BC7B540,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x7BC7B540,0x00000000,0x00000000,0x7FFA01BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFA0FB8,0x09E4FB70,0x09E4F454,0x00000000) 
6ACC696E              start_thread+190 (0x09E4FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 41 --- 
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595  (0x00000001,0x00000004,0x00000000,0x09CDE9C8) 
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99  (0x00000001,0x00000000,0x09CDEA48,0x00000000) 
7BC765AC ntdll.dll    NtWaitForSingleObject+60  (0x000021D0,0x09CDEA48,0x687EC150,0x09CDEB08) 
7BC7B67F ntdll.dll    <unknown symbol>+0 (0x00000000,0x09CDEB48,0x7BC7B540,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x7BC7B540,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x7BC7B540,0x00000000,0x00000000,0x7FFA41BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFA4FB8,0x09CDFB70,0x09CDF454,0x00000000) 
6ACC696E              start_thread+190 (0x09CDFB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 40 --- 
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595  (0x00000003,0x00000004,0x00000000,0x00000000) 
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99  (0x00000003,0x00000000,0x00000000,0x00000000) 
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246  (0x00000003,0x00000000,0x00000000,0x00000000) 
68D0579C winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+268  (0x00000003,0xFFFFFFFF,0x00000000,0x00000000) 
685B65F8 user32.dll   <unknown symbol>+0 (0x00000003,0xFFFFFFFF,0x00000000,0x7BC99FF4) 
6857CD9A user32.dll   MsgWaitForMultipleObjectsEx+250  (0x00000002,0xFFFFFFFF,0x00000000,0x0044CD87) 
6857CDEF user32.dll   MsgWaitForMultipleObjects+63  (0x00000002,0x00000000,0x00000000,0x067DFEA8) 
0044CFA6 Wow.exe      <unknown symbol>+0 (0x00B33958,0x067DFF20,0x0088C5DF,0x8792F3BB) 
0044DF1A Wow.exe      <unknown symbol>+0 (0x067DFEA8,0x0088C605,0x7BC99FF4,0x0989EA34) 
0088C5DF Wow.exe      <unknown symbol>+0 (0x7FFA8F10,0x067DFF20,0x0989EB48,0x0088C605) 
0088C684 Wow.exe      <unknown symbol>+0 (0x0088C605,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x0088C605,0x00000000,0x00000000,0x7FFA81BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x0989FB70,0x0989F454,0x00000000) 
6ACC696E              start_thread+190 (0x0989FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 39 --- 
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595  (0x00000001,0x00000004,0x00000000,0x7FFAC000) 
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99  (0x00000001,0x00000000,0x08E0E78C,0x00000000) 
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246  (0x00000001,0x00000000,0x00000000,0x7B8696FA) 
7B869ECA KERNEL32.dll WaitForMultipleObjects+58  (0x00000001,0x00000000,0x00000027,0x06418748) 
004699CB Wow.exe      <unknown symbol>+0 (0x0629BBE0,0x0076FFCB,0x0076FF30,0x7BC99FF4) 
0046906E Wow.exe      <unknown symbol>+0 (0x06418748,0x7FFACF10,0x000021AC,0x06418748) 
0076FFCB Wow.exe      <unknown symbol>+0 (0x00CAC860,0x08E0EB48,0x0076FF30,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x0076FF30,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x0076FF30,0x00000000,0x00000000,0x7FFAC1BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x08E0FB70,0x08E0F454,0x00000000) 
6ACC696E              start_thread+190 (0x08E0FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 38 --- 
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595  (0x00000001,0x00000004,0x00000000,0x7BC6EBBE) 
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99  (0x00000001,0x00000000,0x08C9E9BC,0x7BC99FF4) 
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246  (0x00000001,0x00000000,0x00000000,0x0086D6F1) 
7B869F6C KERNEL32.dll WaitForSingleObject+60  (0x0000211C,0x08C9EA34,0x000003E8,0x0629BBC8) 
007746A0 Wow.exe      <unknown symbol>+0 (0x000003E8,0x0629BBC8,0x08C9EA40,0x00000000) 
004691A5 Wow.exe      <unknown symbol>+0 (0x00000000,0x0076FFCB,0x0076FF30,0x7BC99FF4) 
00469311 Wow.exe      <unknown symbol>+0 (0x06418758,0x7FFB0F10,0x000021A8,0x06418758) 
0076FFCB Wow.exe      <unknown symbol>+0 (0x00CAC840,0x08C9EB48,0x0076FF30,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x0076FF30,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x0076FF30,0x00000000,0x00000000,0x7FFB01BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x08C9FB70,0x08C9F454,0x00000000) 
6ACC696E              start_thread+190 (0x08C9FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 37 --- 
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595  (0x00000001,0x00000004,0x00000000,0x00000000) 
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99  (0x00000001,0x00000000,0x00000000,0x00000001) 
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246  (0x00000001,0x00000000,0x00000000,0x08B2EA24) 
7B869F6C KERNEL32.dll WaitForSingleObject+60  (0x00002070,0x08B2EA68,0xFFFFFFFF,0x0076FFCB) 
007746A0 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x0076FFCB,0x0076FF30,0x7BC99FF4) 
004F12CB Wow.exe      <unknown symbol>+0 (0x00CAC820,0x08B2EB48,0x0076FF30,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x0076FF30,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x0076FF30,0x00000000,0x00000000,0x7FFB41BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x08B2FB70,0x08B2F454,0x00000000) 
6ACC696E              start_thread+190 (0x08B2FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 36 --- 
7B869FE1 KERNEL32.dll SleepEx+65 (0x0000000A,0x0611EA54,0x7B86A009,0x0611EA54) 
7B86A025 KERNEL32.dll Sleep+37 (0x0000000A,0x008E520C,0x7FFB8F10,0x0611EA78) 
008D1E8D Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000024,0x7BC6F584,0x7FFB8F10) 
008E520C Wow.exe      <unknown symbol>+0 (0x04613A50,0x0611EB48,0x008E5190,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x008E5190,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x008E5190,0x00000000,0x00000000,0x7FFB81BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x0611FB70,0x0611F454,0x00000000) 
6ACC696E              start_thread+190 (0x0611FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 35 --- 
7B869FE1 KERNEL32.dll SleepEx+65 (0x0000000A,0x00000000,0x7B86A009,0x05FAEA54) 
7B86A025 KERNEL32.dll Sleep+37 (0x0000000A,0x008E520C,0x7FFBCF10,0x05FAEA78) 
008D1E8D Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000023,0x7BC6F584,0x7FFBCF10) 
008E520C Wow.exe      <unknown symbol>+0 (0x047CE008,0x05FAEB48,0x008E5190,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x008E5190,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x008E5190,0x00000000,0x00000000,0x7FFBC1BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x05FAFB70,0x05FAF454,0x00000000) 
6ACC696E              start_thread+190 (0x05FAFB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 34 --- 
7B869FE1 KERNEL32.dll SleepEx+65 (0x0000000A,0x05E3EA54,0x7B86A009,0x05E3EA54) 
7B86A025 KERNEL32.dll Sleep+37 (0x0000000A,0x008E520C,0x7FFC0F10,0x05E3EA78) 
008D1E8D Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000022,0x7BC6F584,0x7FFC0F10) 
008E520C Wow.exe      <unknown symbol>+0 (0x0498DD00,0x05E3EB48,0x008E5190,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x008E5190,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x008E5190,0x00000000,0x00000000,0x7FFC01BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFC0FB8,0x05E3FB70,0x05E3F454,0x00000000) 
6ACC696E              start_thread+190 (0x05E3FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 33 --- 
7B869FE1 KERNEL32.dll SleepEx+65 (0x0000000A,0x00000000,0x7B86A009,0x05CCEA54) 
7B86A025 KERNEL32.dll Sleep+37 (0x0000000A,0x008E520C,0x7FFC4F10,0x05CCEA78) 
008D1E8D Wow.exe      <unknown symbol>+0 (0x0000000A,0x00000021,0x7BC6F584,0x7FFC4F10) 
008E520C Wow.exe      <unknown symbol>+0 (0x04614F50,0x05CCEB48,0x008E5190,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x008E5190,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x008E5190,0x00000000,0x00000000,0x7FFC41BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFC4FB8,0x05CCFB70,0x05CCF454,0x00000000) 
6ACC696E              start_thread+190 (0x05CCFB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 32 --- 
68BB0817 winmm.dll    <unknown symbol>+0 (0x00000000,0x05B5EB48,0x68BB0640,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x68BB0640,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x68BB0640,0x00000000,0x00000000,0x7FFC81BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x05B5FB70,0x05B5F454,0x00000000) 
6ACC696E              start_thread+190 (0x05B5FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 31 --- 
7BC76263 ntdll.dll    NTDLL_wait_for_multiple_objects+595  (0x00000001,0x00000004,0x00000000,0x7FFCC000) 
7BC76553 ntdll.dll    NtWaitForMultipleObjects+99  (0x00000001,0x00000000,0x00000000,0x0289E9C8) 
7B869E56 KERNEL32.dll WaitForMultipleObjectsEx+246  (0x00000001,0x00000000,0x00000000,0x7B86974A) 
7B869F6C KERNEL32.dll WaitForSingleObject+60  (0x0000207C,0x0289EA40,0xFFFFFFFF,0x0000001F) 
007746A0 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x0000001F,0x0289EA68,0x00D3FCF0) 
0081C042 Wow.exe      <unknown symbol>+0 (0x00D3FCF0,0x7FFCCF10,0x000020DC,0x00D3FCF0) 
0076FFCB Wow.exe      <unknown symbol>+0 (0x00CAC800,0x0289EB48,0x0076FF30,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x0076FF30,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x0076FF30,0x00000000,0x00000000,0x7FFCC1BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x0289FB70,0x0289F454,0x00000000) 
6ACC696E              start_thread+190 (0x0289FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 30 --- 
7B869FE1 KERNEL32.dll SleepEx+65 (0x00000001,0x0255E614,0x7B86A009,0x0255E620) 
7B86A025 KERNEL32.dll Sleep+37 (0x00000001,0x004BA8BD,0x01D47BD0,0x000020D8) 
0086B28D Wow.exe      <unknown symbol>+0 (0x00000001,0x0000001E,0x00000000,0x00000000) 
004BA8CB Wow.exe      <unknown symbol>+0 (0x01D47BB0,0x7FFD0F10,0x000020D8,0x01D47BB0) 
0076FFCB Wow.exe      <unknown symbol>+0 (0x00CAC7E0,0x0255EB48,0x0076FF30,0x7BC99FF4) 
7BC6F584 ntdll.dll    call_thread_func+12 (0x0076FF30,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x0076FF30,0x00000000,0x00000000,0x7FFD01BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFD0FB8,0x0255FB70,0x0255F454,0x00000000) 
6ACC696E              start_thread+190 (0x0255FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 29 --- 
7B869FE1 KERNEL32.dll SleepEx+65 (0x00000064,0x00000000,0x7B86A009,0x01A5EA14) 
7B86A025 KERNEL32.dll Sleep+37 (0x00000064,0x7BC99FF4,0x01879075,0x01A5EA28) 
00438935 Wow.exe      <unknown symbol>+0 (0x00000000,0x01098318,0x0088C5DF,0x8FBEF3BB) 
0044DF1A Wow.exe      <unknown symbol>+0 (0x0106AD30,0x0088C605,0x7BC99FF4,0x01A5EA34) 
0088C5DF Wow.exe      <unknown symbol>+0 (0x7FFD4F10,0x01098318,0x01A5EB48,0x0088C605) 
0088C684 Wow.exe      <unknown symbol>+0 (0x0088C605,0x7BC99FF4,0xFFFFFFFF,0x7B836E60) 
7BC6F750 ntdll.dll    call_thread_entry_point+112  (0x0088C605,0x00000000,0x00000000,0x7FFD41BC) 
7BC77F35 ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x01A5FB70,0x01A5F454,0x00000000) 
6ACC696E              start_thread+190 (0x01A5FB70,0x00000000,0x00000000,0x00000000) 

--- Thread ID: 26 [Current Thread] --- 
3747714E <unknown module> <unknown symbol>+0  (0x067D5D88,0x06CCC070,0x00836105,0x0195F9AC) 
0068B4F8 Wow.exe      <unknown symbol>+0 (0x067D5DC8,0x06AAC800,0x00000000,0x06AAC800) 
00836144 Wow.exe      <unknown symbol>+0 (0x00000000,0x0195F9C8,0x06CCC070,0x0195FAA0) 
00820583 Wow.exe      <unknown symbol>+0 (0x00000000,0x06CCB708,0x80000000,0x80000000) 
00823A88 Wow.exe      <unknown symbol>+0 (0x00000000,0x06AAC800,0x00000001,0x3F7FA4A8) 
00823D24 Wow.exe      <unknown symbol>+0 (0x00000000,0x3F800000,0x00000000,0x00000000) 
0095FF4E Wow.exe      <unknown symbol>+0 (0xFF000000,0x06CD5D50,0x00000014,0x41A33333) 
004E621B Wow.exe      <unknown symbol>+0 (0xFF000000,0x06A80920,0x00484A9C,0x00000002) 
00485128 Wow.exe      <unknown symbol>+0 (0x06A8099C,0x00000006,0x06943050,0x0049545B) 
00494F67 Wow.exe      <unknown symbol>+0 (0x01DF8ED0,0x06942E28,0x00000000,0x004A8A42) 
0049545B Wow.exe      <unknown symbol>+0 (0x00000000,0x06942E40,0x01D0A8E0,0x01D45EB8) 
004A8A42 Wow.exe      <unknown symbol>+0 (0x00000000,0x00001582,0x01D0A8E0,0x00001582) 
00480B79 Wow.exe      <unknown symbol>+0 (0x01D45D38,0x00000000,0x00000A28,0x7B881FF4) 
0047DC89 Wow.exe      <unknown symbol>+0 (0x00000000,0x003AFDB8,0x3120656E,0x7B869930) 
0047F29A Wow.exe      <unknown symbol>+0 (0x00000000,0x00000001,0x0195FF08,0x0195FFE8) 
0047F2E1 Wow.exe      <unknown symbol>+0 (0x0195FFE8,0x003AFE0C,0x00000000,0x00000000) 
0040B7D8 Wow.exe      <unknown symbol>+0 (0x003AFE0C,0x00000000,0x00000000,0x00000000) 
7B837683 KERNEL32.dll <unknown symbol>+0 (0x0012EAA8,0x00000000,0x00000000,0x00000000) 



---------------------------------------- 
    Loaded Modules 
---------------------------------------- 

DBG-MODULE<00400000 009FD000 "Wow.exe" "Wow.pdb" 0  {8805d059-f6a3-4565-a646aa69736d4efe} 1 1277448958> 
DBG-MODULE<10000000 00069000 "DivxDecoder.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 1076466304> 
DBG-MODULE<200D0000 00062000 "msvcrt.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<317B0000 00008000 "msacm32.drv" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<35A30000 00009000 "midimap.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<364E0000 0000C000 "psapi.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<42210000 00048000 "dbghelp.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<42470000 00039000 "dsound.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68520000 000F7000 "user32.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68620000 00081000 "gdi32.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<686B0000 0004A000 "advapi32.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68710000 0005B000 "rpcrt4.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68770000 00014000 "version.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68790000 00008000 "lz32.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<687A0000 00019000 "imm32.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<687C0000 00052000 "wininet.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68830000 0001A000 "mpr.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68860000 00049000 "shlwapi.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<688C0000 0017D000 "shell32.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68A50000 000BB000 "comctl32.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68B10000 00027000 "ws2_32.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68B40000 00012000 "dinput8.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68B60000 0002B000 "dinput.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68B90000 00082000 "winmm.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68C20000 00018000 "msacm32.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68C40000 0002E000 "winspool.drv" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<68CD0000 00094000 "winex11.drv" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<69030000 00028000 "uxtheme.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<6AF80000 00007000 "hid.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<74330000 00090000 "opengl32.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<751D0000 000D9000 "ole32.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<79280000 00032000 "winealsa.drv" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<7A040000 00045000 "setupapi.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<7B810000 0012A000 "KERNEL32.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 
DBG-MODULE<7BC10000 000A6000 "ntdll.dll" "" 0  {00000000-0000-0000-0000000000000000} 0 0> 

---------------------------------------- 
    Memory Dump 
---------------------------------------- 

Code: 16 bytes starting at (EIP = 3747714E) 

3747714E: <can't read from this address> 


Stack: 1024 bytes starting at (ESP = 0195F940) 

* = addr  **                                                  *                 
0195F940: A5 B3 68 00  01 00 00 00  9C 5D 7D 06  C8 5D 7D 06   ..h......]}..]}. 
0195F950: 88 5D 7D 06  00 00 00 00  78 F9 95 01  F8 B4 68 00   .]}.....x.....h. 
0195F960: 88 5D 7D 06  20 C0 9E 09  70 C0 CC 06  00 00 00 00  .]}.  ...p....... 
0195F970: 05 61 83 00  20 1A D4 01  AC F9 95 01  44 61 83 00  .a..  .......Da.. 
0195F980: C8 5D 7D 06  C0 FA 95 01  00 C8 AA 06  00 00 00 00   .]}............. 
0195F990: 00 00 00 00  C0 FA 95 01  00 C8 AA 06  01 00 00 00   ................ 
0195F9A0: CC F9 95 01  3F 05 82 00  00 00 00 00  CC F9 95 01   ....?........... 
0195F9B0: 83 05 82 00  00 00 00 00  C0 FA 95 01  C8 F9 95 01   ................ 
0195F9C0: 5E C8 81 00  70 C0 CC 06  A0 FA 95 01  A0 FA 95 01   ^...p........... 
0195F9D0: 88 3A 82 00  00 00 00 00  00 00 00 00  08 B7 CC 06   .:.............. 
0195F9E0: A8 A4 7F 3F  00 00 00 80  00 00 00 00  00 00 00 80   ...?............ 
0195F9F0: 00 00 00 80  7B CA 15 3F  00 00 00 80  00 00 00 00   ....{..?........ 
0195FA00: 00 00 00 00  00 00 00 80  00 00 00 00  00 00 80 3F   ...............? 
0195FA10: 00 00 00 80  00 00 00 00  0D FD 0F C0  F3 02 10 40   ...............@ 
0195FA20: 3D 9F 49 AC  26 77 89 B7  00 00 80 BF  00 00 00 00   =.I.&w.......... 
0195FA30: 00 00 80 3F  2E BD 3B B4  00 00 00 00  00 00 00 00   ...?..;......... 
0195FA40: 2E BD 3B 34  00 00 80 3F  26 77 89 B7  00 00 00 00   ..;4...?&w...... 
0195FA50: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 80 3F   ...............? 
0195FA60: BD 2D 80 3F  00 00 00 00  00 00 00 00  00 00 00 00   .-.?............ 
0195FA70: 00 00 00 00  1C C2 DA 3F  00 00 00 00  00 00 00 00   .......?........ 
0195FA80: 00 00 00 00  00 00 00 00  3E 05 80 3F  00 00 80 3F   ........>..?...? 
0195FA90: 00 00 00 00  00 00 00 00  E2 92 E3 BE  00 00 00 00   ................ 
0195FAA0: 7C FB 95 01  24 3D 82 00  00 00 00 00  80 4B D7 06   |...$=.......K.. 
0195FAB0: 00 C8 AA 06  0C 00 00 00  01 00 00 00  4C 99 BB 06   ............L... 
0195FAC0: A8 A4 7F 3F  00 00 00 80  00 00 00 00  00 00 00 80   ...?............ 
0195FAD0: 00 00 00 80  7B CA 15 3F  00 00 00 80  00 00 00 00   ....{..?........ 
0195FAE0: 00 00 00 00  00 00 00 80  00 00 00 00  00 00 80 3F   ...............? 
0195FAF0: 00 00 00 80  00 00 00 00  0D FD 0F C0  F3 02 10 40   ...............@ 
0195FB00: 08 B7 CC 06  F0 FC D3 00  30 00 8A 09  00 00 00 00   ........0....... 
0195FB10: 84 58 D7 06  00 00 00 00  00 00 00 00  FF FF FF FF   .X.............. 
0195FB20: 20 C0 9E 09  00 00 00 00  70 C0 CC 06  00 00 00 00    .......p....... 
0195FB30: F4 C1 9E 09  00 00 00 00  00 00 00 00  00 00 00 00   ................ 
0195FB40: 01 00 00 00  FF FF FF FF  88 D5 C2 06  00 00 00 00   ................ 
0195FB50: E8 40 F7 06  00 00 00 00  B8 36 93 09  00 00 00 00   .@.......6...... 
0195FB60: 58 D8 64 06  90 44 76 06  90 DC 64 06  60 8A 72 06   X.d..Dv...d.`.r. 
0195FB70: 58 D2 6F 06  60 06 74 06  00 00 00 00  54 FC 95 01   X.o.`.t.....T... 
0195FB80: 4E FF 95 00  00 00 00 00  4C 99 BB 06  00 00 80 3F   N.......L......? 
0195FB90: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00   ................ 
0195FBA0: 00 00 80 3F  00 00 00 00  00 00 00 00  00 00 00 00   ...?............ 
0195FBB0: 00 00 00 00  00 00 80 3F  00 00 00 00  6B E0 DC BE   .......?....k... 
0195FBC0: 7F 6B 81 BE  00 00 00 00  00 00 80 3F  B4 5A 14 40   .k.........?.Z.@ 
0195FBD0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00   ................ 
0195FBE0: FC 30 7D 40  00 00 00 00  00 00 00 00  00 00 00 80   .0}@............ 
0195FBF0: 00 00 00 80  6F 12 03 BB  00 00 00 00  00 00 00 80   ....o........... 
0195FC00: 00 00 00 80  00 00 00 80  00 00 80 3F  CC 8D 24 C1   ...........?..$. 
0195FC10: 1D 7F 0F BD  58 41 1C 40  00 00 00 00  20 1A D4 01   ....XA.@.... ... 
0195FC20: C0 DF 31 41  1D 7F 0F BD  17 47 1C 40  00 00 00 00   ..1A.....G.@.... 
0195FC30: 00 00 00 00  00 00 80 3F  00 00 00 00  00 00 80 3F   .......?.......? 
0195FC40: 00 00 80 3F  00 00 00 00  00 00 00 00  00 00 80 3F   ...?...........? 
0195FC50: 00 00 80 3F  78 FC 95 01  1B 62 4E 00  00 00 00 FF   ...?x....bN..... 
0195FC60: 9C 09 A8 06  50 5D CD 06  00 00 00 00  14 00 00 00   ....P].......... 
0195FC70: 00 00 00 00  33 33 A3 41  38 FD 95 01  28 51 48 00   ....33.A8...(QH. 
0195FC80: 00 00 00 FF  01 00 00 00  20 09 A8 06  9C 09 A8 06   ........ ....... 
0195FC90: 9C 4A 48 00  48 C1 B3 06  02 00 00 00  04 00 00 00   .JH.H........... 
0195FCA0: B0 72 A1 06  10 73 A1 06  00 00 00 00  7C 72 A1 06   .r...s......|r.. 
0195FCB0: 06 00 00 00  04 0F AC 00  F0 49 D9 01  D4 E1 B7 06   .........I...... 
0195FCC0: 03 00 00 00  80 E2 98 06  F0 FC 95 01  31 44 48 00   ............1DH. 
0195FCD0: E8 0B B4 06  58 1E BE 06  4C 58 BD 06  C4 47 A3 06   ....X...LX...G.. 
0195FCE0: D0 49 99 3D  4C 58 BD 06  C4 47 A3 06  C4 47 A3 06   .I.=LX...G...G.. 
0195FCF0: 04 FD 95 01  7C 58 BD 06  04 FD 95 01  55 51 48 00   ....|X......UQH. 
0195FD00: D0 71 A1 06  1C FD 95 01  86 08 49 00  7C 58 BD 06   .q........I.|X.. 
0195FD10: F4 A8 BD 06  F4 A8 BD 06  78 59 48 00  00 00 00 00   ........xYH..... 
0195FD20: 2C 5F 48 00  18 A8 BD 06  E7 4B 49 00  04 00 00 00   ,_H......KI..... 
0195FD30: 06 00 00 00  50 30 94 06  54 FD 95 01  67 4F 49 00   ....P0..T...gOI. 


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
Processor Revision:     7178 
Os Version:             5.1 
Os Service Pack:        3.0 

Percent memory used:    42 
Total physical memory:  1040105472 
Free Memory:            597016576 
Page file:              4084113408 
Total virtual memory:   2147352575 

```
BTW: WoW was running fine on this netbook when Windows 7 Starter was  originally installed. Any help is greatly appreciated!!!!!

---

### Post by Felrohan on 2010-07-04
oh, i literally just added another Gig to this netbook, so i have 2GB of RAM in it now.

---

### Post by hikaricore on 2010-07-04
Yea... none of that garbage you posted is helpful.
The likely cause of your issue is your video hardware/drivers or lack thereof.  The fact that wow runs on windows means nothing.
You'll need to tell us more about your system hardware because chances are it's some integrated intel chipset that has terrible opengl support.
Try running the game from a terminal and see what kinda output you get there, this output might actually serve a purpose unlike the blizzlog you posted.

Also in the future post wine related issues in the wine forum.
This thread will be moved shortly.

---

### Post by Felrohan on 2010-07-04
Ok... geez. you are so helpful. I was just posting what i thought may help, excuse me for being a little new to Linux. You don't have to be a jerk. Anyway, what would you like me to post? And where would you like me to post it?

---

### Post by Felrohan on 2010-07-04
ok i hope this is more helpful, i got this in terminal:

felrohan@felrohan-laptop:~$ wine "Z:\\home\\felrohan\\Desktop\\World of Warcraft\\WoW.exe"
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\enUS\patch-enUS-3.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\patch-3.MPQ opened
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
fixme:win:EnumDisplayDevicesW ((null),0,0x192ee20,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x192eb0c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f464,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f5fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f5f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f1b4,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13ea90,0x13e990): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x192f89c): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x192f89c): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x192df60,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192df88,0x00000000), stub!
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37404684) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:reg:GetNativeSystemInfo (0x33fd9c) using GetSystemInfo()

---

### Post by gvoima on 2010-07-04
I got that error (#132) A LOT, when I some time ago, had faulty memory. WoW is so memory intensive and sensitive about it, that I highly recommend you running the memtest included on ubuntus live cds.

That's an overall error that relates to some degree of faulty hardware (or events mimicking it), may not be the memory, but you will sleep better knowing, that you atleast checked it :)

---

### Post by pedro_orange on 2010-07-04
I doubt you will be able to run the game on your hardware with Linux. I think it's mainly down to the fact you're running an integrated Intel video card.

Also, please consult the Ubuntu wiki on all things WoW/Ubuntu - [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Felrohan on 2010-07-04
> **gvoima said:**
> I got that error (#132) A LOT, when I some time ago, had faulty memory. WoW is so memory intensive and sensitive about it, that I highly recommend you running the memtest included on ubuntus live cds.

That's an overall error that relates to some degree of faulty hardware (or events mimicking it), may not be the memory, but you will sleep better knowing, that you atleast checked it :)

Hey Gvoima, could you please give me the command to run the memtest, i can't find the application and i have tried different variations of commands in terminal, but nothing has worked so far. Thank you for the help.

Oh and i updated Xorg and it seems all my drivers are up-to-date.

---

### Post by hikaricore on 2010-07-04
WoW throws error 132 all the time for a number of reasons, and even though it is sometimes attributed to memory this usually isn't the case.
This error is especially prevalent when running Wow through wine.

---

### Post by Felrohan on 2010-07-04
well i finally got into winecfg and added both WoW.exe and Launcher.exe into the application section, now i get no reaction from WoW.exe... no errors, reactions, nothing.

---

### Post by hikaricore on 2010-07-04
Why are you adding them to winecfg?..  They don't need to be an I've not seen a single person suggest that.
In addition you never told us about your hardware so we're still assuming it's intel integrated and that's the problem.

---

### Post by gvoima on 2010-07-04
> **hikaricore said:**
> WoW throws error 132 all the time for a number of reasons, and even though it is sometimes attributed to memory this usually isn't the case.
This error is especially prevalent when running Wow through wine.

Yes I know, therefore I stated that
*"That's an overall error that relates to some degree of faulty hardware OR events mimicking it"*
As I got this error, I was using windows. So wine cannot directly be blamed. As a matter of fact I've never got any errors while playing with wine (and sadly I've been playing for the whole 5 years :()

---

### Post by Woojoo//.deb on 2010-07-04
Felrohan what kind of grafics card are you using? did you install drivers for your card? 

```
fixme:win:EnumDisplayDevicesW ((null),0,0x192ee20,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x192eb0c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f464,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f5fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f5f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192f1b4,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13ea90,0x13e990): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x192f89c): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x192f89c): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x192df60,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x192df88,0x00000000), stub!
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37404684) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:reg:GetNativeSystemInfo (0x33fd9c) using GetSystemInfo() 
```

you all should note that "fixme" points out whats not going right there + it all starts with the display device

---

### Post by hikaricore on 2010-07-04
The OP already stated he updated X and his drivers but has yet to tell us the type of hardware.
As far as the fixme messages those not errors and are generally misleading so I wouldn't claim that they tell the exact issue.

---

### Post by Felrohan on 2010-07-04
It's a Gateway LT2104u Netbook,

**New Intel®  Atom™ N450**
Designed for new-generation mobile devices  and delivering new performance while saving energy for longer battery  life, the [Intel® Atom™ Processor N450]("http://syndication.intel.com/DistributeModule.aspx?id=3843")[1]("http://www.gateway.com/systems/product/529668485.php#disclaimer1")  is a revolution in chip architecture. Finally, the power you've always  wished a netbook could deliver is in your hands.
[Learn  More]("javascript:win=window.open('http://syndication.intel.com/DistributeModule.aspx?id=3843',%20's3843',%20'resizable=1,scrollbars=0,width=360,height=220');win.focus();")
 
 [B]

Intel®  Graphics Media
Accelerator 3100 Series[/B]
This system is equipped with the Intel® Graphics Media Accelerator 3100 series, which adds  response-boosting dynamic video memory. Hardware based, it improves  graphics performance while saving power.  		 			 
 
 [B]

Mobile Intel®  NM10 Express Chipset[/B]
This system has the Mobile Intel® NM10 Express chipset that provides sharper images  and higher performance on your netbook applications.
 


Thats what it says on the Gateway website.

---

### Post by Woojoo//.deb on 2010-07-04
```

GxApi: OpenGL 
Vendor: Tungsten Graphics, Inc 
Renderer: Mesa DRI Intel(R) IGD GEM 20091221 2009Q4 x86/MMX/SSE2 
Version: 1.4 Mesa 7.7.1 

```

well i didnt read the first post good enough it seems

he statet with the report that he uses the above mentiont config and card

normaly i think he just would need a driver for this card with 
3d acceleration support but since intel got not many drivers on linux this could be a hard to find


how did you install wow? did you use the winehq tutorial???

---

### Post by Felrohan on 2010-07-06
actually, i just copied it over from my external HD, i have done it before on windows, should i try reinstalling VIA Wine?

---

### Post by hikaricore on 2010-07-06
Installation method doesn't really matter as long as you make a few minor changes such as the opengl mode and such.
I think you're still going to be severely limited by that hardware and there's no other way to put it.
There might be a few workarounds for intel hardware on the various guides and threads around here, but your chances are excessively slim of success.

---

### Post by Felrohan on 2010-07-06
ever the optimistic lol like i said i had it running fine before on win 7 stater, granted i was getting about 9-16 fps with about 100-200ms latency. But i know it is possible. and i have run the opengl command, it should be present in my first post with all the "garbage" I just can't really come up with anything else. I've played with the winecfg, put in suggested commands into the WTF (config) file (which it is aptly named). And it seems like i'm not the only person with this problem, i have started to find other people who updated Ubuntu and then WoW stopped working. So i dont know if it is something in the new patch (3.3.5) or if it is Ubuntu. I can try re-installing WoW and starting over, maybe all my tinkering has done more hurting than helping.

---

### Post by Felrohan on 2010-07-06
Example of my people who continue to suffer (being sarcastic of coarse):

[http://bugs.winehq.org/show_bug.cgi?id=23323](http://bugs.winehq.org/show_bug.cgi?id=23323)

---

### Post by hikaricore on 2010-07-06
> **Felrohan said:**
> ever the optimistic lol like i said i had it running fine before on win 7 stater, granted i was getting about 9-16 fps with about 100-200ms latency. But i know it is possible

You still don't understand..

Just because it runs on windows does not mean that it's possible to run on Linux.
Your hardware and the available drivers for it are pretty much a guarantee that WoW will not run on Linux.
You might think I'm just being a bastard at this point but I'm really just trying to help limit your suffering.

---

### Post by Felrohan on 2010-07-07
No, it's ok, i understand. I know that there is a very good chance that the drivers and such aren't out yet for my little comp. But soon, hopefully, there will be. Thank you guys for your help, and as i said - hopefully this gets resolved soon : / Everyone's input is very much appreciated, even Hikaricore's. ^.^

---

