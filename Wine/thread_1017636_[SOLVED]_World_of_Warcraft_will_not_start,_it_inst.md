---
title: "[SOLVED] World of Warcraft will not start, it instead only has an error"
date: 2008-12-21
forum: Wine
---

### Post by Scytes on 2008-12-21
Yes I am on an Alienware M15x with a 8600m gt nvidia card, I am wondering if there is anyway to fix this. Because the driver in the system>Hardware Drivers does not solve it. IS there maybe a version close to it that will help solve this issue. The error comes up as...




World of WarCraft (build 9183)

Exe:      Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
Time:     Dec 21, 2008 10:12:26.572 AM
User:     james
Computer: james-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:005CEF48

The instruction at "0x005CEF48" referenced memory at "0xFFB69588".
The memory could not be "read".


WoWBuild: 9183
Settings: 
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "53"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET movie "0"
SET showToolsUI "0"
SET Sound_OutputDriverName "System Default"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET farclip "777.000000"
SET particleDensity "1.000000"
SET readTerminationWithoutNotice "-1"
SET gxWindow "1"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET gameTip "84"
SET uiScale "0.89999997615814"
SET CombatLogRangeParty "2000"
SET CombatLogRangePartyPet "2000"
SET CombatLogRangeFriendlyPlayers "2000"
SET CombatLogRangeFriendlyPlayersPets "2000"
SET CombatLogRangeHostilePlayers "2000"
SET CombatLogRangeHostilePlayersPets "2000"
SET CombatLogRangeCreature "2000"
SET DesktopGamma "1"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_MasterVolume "0.40000000596046"
SET Sound_SFXVolume "0.40000000596046"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "0"
SET OutboundChatVolume "2.5"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0"
SET EnableVoiceChat "1"
SET Sound_OutputQuality "2"
SET useUiScale "1"
SET Sound_EnableSoundWhenGameIsInBG "1"
SET PushToTalkButton "TAB"
SET Sound_EnableAmbience "0"
SET installType "Retail"
SET portal "us"
SET mouseSpeed "1"
SET Sound_EnableMusic "0"
SET weatherDensity "0"
SET ffxGlow "0"
SET realmilist "nemesiswow.hopto.org"
SET timingTestError "0"
SET ffxDeath "0"
SET realmName "Antonidas"
SET lastCharacterIndex "1"
SET gxFixLag "0"
SET specular "1"
SET groundEffectDensity "24"
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=011B0CC8  EBX=084173B0  ECX=3F857321  EDX=01A0A1C0  ESI=084173B0
EDI=0000000C  EBP=003AF8D0  ESP=003AF8C4  EIP=005CEF48  FLG=00210246
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 12/12 threads...

--- Thread ID: 39 ---
7BC68F2B 7BBFE988 0001:00057F2B C:\windows\system32\ntdll.dll
7BC69202 7BBFE9B8 0001:00058202 C:\windows\system32\ntdll.dll
7BC6925C 7BBFE9D8 0001:0005825C C:\windows\system32\ntdll.dll
7BC6DDB0 7BBFEA38 0001:0005CDB0 C:\windows\system32\ntdll.dll
7BC6AEAE 7BBFEA48 0001:00059EAE C:\windows\system32\ntdll.dll
7BC6B542 7BBFEAE8 0001:0005A542 C:\windows\system32\ntdll.dll
7BC6B772 7BBFF3D8 0001:0005A772 C:\windows\system32\ntdll.dll
B7E184FB 7BBFF4C8 0000:00000000 <unknown>

--- Thread ID: 32 ---
7BC68F2B 7BEFE988 0001:00057F2B C:\windows\system32\ntdll.dll
7BC69202 7BEFE9B8 0001:00058202 C:\windows\system32\ntdll.dll
7BC6925C 7BEFE9D8 0001:0005825C C:\windows\system32\ntdll.dll
7BC6DDB0 7BEFEA38 0001:0005CDB0 C:\windows\system32\ntdll.dll
7BC6AEAE 7BEFEA48 0001:00059EAE C:\windows\system32\ntdll.dll
7BC6B542 7BEFEAE8 0001:0005A542 C:\windows\system32\ntdll.dll
7BC6B772 7BEFF3D8 0001:0005A772 C:\windows\system32\ntdll.dll
B7E184FB 7BEFF4C8 0000:00000000 <unknown>

--- Thread ID: 40 ---
7BC68F2B 7C46E634 0001:00057F2B C:\windows\system32\ntdll.dll
7BC69202 7C46E664 0001:00058202 C:\windows\system32\ntdll.dll
7B88BAB2 7C46E7B4 0001:0006AAB2 C:\windows\system32\KERNEL32.dll
7D6E11CE 7C46E7E4 0001:000301CE C:\windows\system32\winex11.drv
7ED2EBDE 7C46E994 0001:0006DBDE C:\windows\system32\user32.dll
7ED2EC3F 7C46E9B4 0001:0006DC3F C:\windows\system32\user32.dll
006DA017 7C46E9E4 0001:002D9017 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
006D83E5 7C46E9F8 0001:002D73E5 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
007E9CDF 7C46EA30 0001:003E8CDF Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
007E9D84 7C46EA48 0001:003E8D84 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
7BC6B542 7C46EAE8 0001:0005A542 C:\windows\system32\ntdll.dll
7BC6B772 7C46F3D8 0001:0005A772 C:\windows\system32\ntdll.dll
B7E184FB 7C46F4C8 0000:00000000 <unknown>

--- Thread ID: 37 ---
7BC68F2B 7C5DF618 0001:00057F2B C:\windows\system32\ntdll.dll
7BC69202 7C5DF648 0001:00058202 C:\windows\system32\ntdll.dll
7B88BAB2 7C5DF798 0001:0006AAB2 C:\windows\system32\KERNEL32.dll
7B88BC0A 7C5DF7B8 0001:0006AC0A C:\windows\system32\KERNEL32.dll
004224DB 7C5DFA10 0001:000214DB Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
00421DEE 7C5DFA1C 0001:00020DEE Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
006A1F57 7C5DFA38 0001:002A0F57 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
7BC6AEAE 7C5DFA48 0001:00059EAE C:\windows\system32\ntdll.dll
7BC6B542 7C5DFAE8 0001:0005A542 C:\windows\system32\ntdll.dll
7BC6B772 7C5E03D8 0001:0005A772 C:\windows\system32\ntdll.dll
B7E184FB 7C5E04C8 0000:00000000 <unknown>

--- Thread ID: 31 ---
7BC68F2B 7C750848 0001:00057F2B C:\windows\system32\ntdll.dll
7BC69202 7C750878 0001:00058202 C:\windows\system32\ntdll.dll
7B88BAB2 7C7509C8 0001:0006AAB2 C:\windows\system32\KERNEL32.dll
7B88BCAC 7C7509E8 0001:0006ACAC C:\windows\system32\KERNEL32.dll
006A5C40 7C7509F8 0001:002A4C40 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
00421CB5 7C750A10 0001:00020CB5 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
00421DD1 7C750A1C 0001:00020DD1 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
006A1F57 7C750A38 0001:002A0F57 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
7BC6AEAE 7C750A48 0001:00059EAE C:\windows\system32\ntdll.dll
7BC6B542 7C750AE8 0001:0005A542 C:\windows\system32\ntdll.dll
7BC6B772 7C7513D8 0001:0005A772 C:\windows\system32\ntdll.dll
B7E184FB 7C7514C8 0000:00000000 <unknown>

--- Thread ID: 36 ---
7B88DCF4 7C8C19F8 0001:0006CCF4 C:\windows\system32\KERNEL32.dll
7B88DD45 7C8C1A18 0001:0006CD45 C:\windows\system32\KERNEL32.dll
008369BA 7C8C1A24 0001:004359BA Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
0083AAE9 7C8C1A38 0001:00439AE9 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
7BC6AEAE 7C8C1A48 0001:00059EAE C:\windows\system32\ntdll.dll
7BC6B542 7C8C1AE8 0001:0005A542 C:\windows\system32\ntdll.dll
7BC6B772 7C8C23D8 0001:0005A772 C:\windows\system32\ntdll.dll
B7E184FB 7C8C24C8 0000:00000000 <unknown>

--- Thread ID: 35 ---
7B88DCF4 7CA329F8 0001:0006CCF4 C:\windows\system32\KERNEL32.dll
7B88DD45 7CA32A18 0001:0006CD45 C:\windows\system32\KERNEL32.dll
008369BA 7CA32A24 0001:004359BA Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
0083AAE9 7CA32A38 0001:00439AE9 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
7BC6AEAE 7CA32A48 0001:00059EAE C:\windows\system32\ntdll.dll
7BC6B542 7CA32AE8 0001:0005A542 C:\windows\system32\ntdll.dll
7BC6B772 7CA333D8 0001:0005A772 C:\windows\system32\ntdll.dll
B7E184FB 7CA334C8 0000:00000000 <unknown>

--- Thread ID: 34 ---
7BC68F2B 7CBA3854 0001:00057F2B C:\windows\system32\ntdll.dll
7BC69202 7CBA3884 0001:00058202 C:\windows\system32\ntdll.dll
7B88BAB2 7CBA39D4 0001:0006AAB2 C:\windows\system32\KERNEL32.dll
7B88BCAC 7CBA39F4 0001:0006ACAC C:\windows\system32\KERNEL32.dll
006A5C40 7CBA3A04 0001:002A4C40 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
007805B2 7CBA3A1C 0001:0037F5B2 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
006A1F57 7CBA3A38 0001:002A0F57 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
7BC6AEAE 7CBA3A48 0001:00059EAE C:\windows\system32\ntdll.dll
7BC6B542 7CBA3AE8 0001:0005A542 C:\windows\system32\ntdll.dll
7BC6B772 7CBA43D8 0001:0005A772 C:\windows\system32\ntdll.dll
B7E184FB 7CBA44C8 0000:00000000 <unknown>

--- Thread ID: 33 ---
7B88DCF4 7CD145D0 0001:0006CCF4 C:\windows\system32\KERNEL32.dll
7B88DD45 7CD145F0 0001:0006CD45 C:\windows\system32\KERNEL32.dll
007CAA8D 7CD145FC 0001:003C9A8D Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
00455159 7CD14A1C 0001:00054159 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
006A1F57 7CD14A38 0001:002A0F57 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
7BC6AEAE 7CD14A48 0001:00059EAE C:\windows\system32\ntdll.dll
7BC6B542 7CD14AE8 0001:0005A542 C:\windows\system32\ntdll.dll
7BC6B772 7CD153D8 0001:0005A772 C:\windows\system32\ntdll.dll
B7E184FB 7CD154C8 0000:00000000 <unknown>

--- Thread ID: 43 ---
7B88DCF4 7CE859B0 0001:0006CCF4 C:\windows\system32\KERNEL32.dll
7B88DD45 7CE859D0 0001:0006CD45 C:\windows\system32\KERNEL32.dll
006BDA34 7CE859F8 0001:002BCA34 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
007E9CDF 7CE85A30 0001:003E8CDF Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
007E9D84 7CE85A48 0001:003E8D84 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
7BC6B542 7CE85AE8 0001:0005A542 C:\windows\system32\ntdll.dll
7BC6B772 7CE863D8 0001:0005A772 C:\windows\system32\ntdll.dll
B7E184FB 7CE864C8 0000:00000000 <unknown>

--- Thread ID: 59 ---
7BC68F2B 7D0DA828 0001:00057F2B C:\windows\system32\ntdll.dll
7BC69202 7D0DA858 0001:00058202 C:\windows\system32\ntdll.dll
7B88BAB2 7D0DA9A8 0001:0006AAB2 C:\windows\system32\KERNEL32.dll
7B88BCAC 7D0DA9C8 0001:0006ACAC C:\windows\system32\KERNEL32.dll
006BBB05 7D0DA9E4 0001:002BAB05 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
006D83E5 7D0DA9F8 0001:002D73E5 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
007E9CDF 7D0DAA30 0001:003E8CDF Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
007E9D84 7D0DAA48 0001:003E8D84 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
7BC6B542 7D0DAAE8 0001:0005A542 C:\windows\system32\ntdll.dll
7BC6B772 7D0DB3D8 0001:0005A772 C:\windows\system32\ntdll.dll
B7E184FB 7D0DB4C8 0000:00000000 <unknown>

--- Thread ID: 50 [Current Thread] ---
005CEF48 003AF8D0 0001:001CDF48 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
005CC53A 003AF8F0 0001:001CB53A Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
0079A067 003AF920 0001:00399067 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
00786E18 003AF94C 0001:00385E18 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
007880F7 003AFA20 0001:003870F7 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
00788375 003AFAF8 0001:00387375 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
008AFBCB 003AFBD0 0001:004AEBCB Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
0047BD11 003AFBF8 0001:0007AD11 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
0042C162 003AFCB4 0001:0002B162 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
004393C7 003AFCD0 0001:000383C7 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
004398B9 003AFCEC 0001:000388B9 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
00443F6C 003AFDB8 0001:00042F6C Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
00427AE9 003AFDE8 0001:00026AE9 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
00426429 003AFE54 0001:00025429 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
00426501 003AFE6C 0001:00025501 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
00406AE8 003AFF08 0001:00005AE8 Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
7B8773A7 003AFFE8 0001:000563A7 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 12/12 threads...

--- Thread ID: 39 ---
7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7BBFE9E0,0x00000004,0x7BBFEA20)
7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7BBFE9E0,0x00000000,0x00000000)
7BC6925C ntdll.dll    NtWaitForSingleObject+60 (0x000021B0,0x00000000,0x7BBFEA20,0x7BC728BF)
7BC6DDB0 ntdll.dll    <unknown symbol>+0 (0x00000000,0x7BC6DC80,0x7BBFEAE8,0x7BC6B542)
7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x7BC6DC80,0x00000000,0x10012A03,0x00000000)
7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7BBFEB1C,0x00000000,0x00000000,0x00000000)
7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x7BBFF490,0x7BBFF490,0x7BBFF490)
B7E184FB              start_thread+203 (0x7BBFFB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 32 ---
7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7BEFE9E0,0x00000004,0x7BEFEA20)
7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7BEFE9E0,0x00000000,0x00000000)
7BC6925C ntdll.dll    NtWaitForSingleObject+60 (0x000021B0,0x00000000,0x7BEFEA20,0x7BC859F6)
7BC6DDB0 ntdll.dll    <unknown symbol>+0 (0x00000000,0x7BC6DC80,0x7BEFEAE8,0x7BC6B542)
7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x7BC6DC80,0x00000000,0x10012A03,0x00000000)
7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7BEFEB1C,0x00000000,0x00000000,0x00000000)
7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x7BEFF490,0x7BEFF490,0x7BEFF490)
B7E184FB              start_thread+203 (0x7BEFFB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 40 ---
7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000003,0x7C46E69C,0x00000004,0x00000000)
7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x7C46E69C,0x00000000,0x00000000)
7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000003,0x7C46E818,0x00000000,0xFFFFFFFF)
7D6E11CE winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+126 (0x00000003,0x7C46E818,0xFFFFFFFF,0x00000000)
7ED2EBDE user32.dll   MsgWaitForMultipleObjectsEx+238 (0x00000002,0x7C46E9DC,0xFFFFFFFF,0x00000000)
7ED2EC3F user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x7C46E9DC,0x00000000,0xFFFFFFFF)
006DA017 Wow.exe      <unknown symbol>+0 (0x01207D20,0x007E9D05,0x07799BF0,0x7C46EA30)
006D83E5 Wow.exe      <unknown symbol>+0 (0x07799B90,0xA891D70A,0x007E9D05,0x07799BF0)
007E9CDF Wow.exe      <unknown symbol>+0 (0x07799BF0,0x7BC6AEAE,0x07799BF0,0x007E9D05)
007E9D84 Wow.exe      <unknown symbol>+0 (0x007E9D05,0x07799BF0,0x10012A03,0x00000000)
7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7C46EB1C,0x00000000,0x00000000,0x00000000)
7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x7C46F490,0x7C46F490,0x7C46F490)
B7E184FB              start_thread+203 (0x7C46FB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 37 ---
7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7C5DF680,0x00000004,0x7C5DF780)
7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7C5DF680,0x00000000,0x00000000)
7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7C5DF8DC,0x00000000,0x000001F4)
7B88BC0A KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x7C5DF8DC,0x00000000,0x000001F4)
004224DB Wow.exe      <unknown symbol>+0 (0x00421DE0,0x7C5DFA38,0x006A1F57,0x067D6588)
00421DEE Wow.exe      <unknown symbol>+0 (0x067D6588,0x006A1F00,0x063BE108,0x7BC88444)
006A1F57 Wow.exe      <unknown symbol>+0 (0x0000218C,0x006A1F00,0x7C5DFAE8,0x7BC6B542)
7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x006A1F00,0x063BE108,0x10012A03,0x00000000)
7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7C5DFB1C,0x00000000,0x00000000,0x00000000)
7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x7C5E0490,0x7C5E0490,0x7C5E0490)
B7E184FB              start_thread+203 (0x7C5E0B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 31 ---
7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7C7508B0,0x00000004,0x7C7509B0)
7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7C7508B0,0x00000000,0x00000000)
7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7C7509F0,0x00000000,0x000003E8)
7B88BCAC KERNEL32.dll WaitForSingleObject+60 (0x000020FC,0x000003E8,0x7C750A10,0x00421CB5)
006A5C40 Wow.exe      <unknown symbol>+0 (0x000003E8,0x0000001F,0x00421DC0,0x067D6598)
00421CB5 Wow.exe      <unknown symbol>+0 (0x00000000,0x7C750A38,0x006A1F57,0x067D6598)
00421DD1 Wow.exe      <unknown symbol>+0 (0x067D6598,0x006A1F00,0x063BE0F0,0x7BC88444)
006A1F57 Wow.exe      <unknown symbol>+0 (0x00002188,0x006A1F00,0x7C750AE8,0x7BC6B542)
7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x006A1F00,0x063BE0F0,0x10012A03,0x00000000)
7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7C750B1C,0x00000000,0x00000000,0x00000000)
7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x7C751490,0x7C751490,0x7C751490)
B7E184FB              start_thread+203 (0x7C751B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 36 ---
7B88DCF4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x3F733333,0x7C8C1A24)
7B88DD45 KERNEL32.dll Sleep+37 (0x0000000A,0x7C8C1A38,0x0083AAE9,0x0000000A)
008369BA Wow.exe      <unknown symbol>+0 (0x0000000A,0x057CAED0,0x00000024,0x7C8C1A48)
0083AAE9 Wow.exe      <unknown symbol>+0 (0x057CAED0,0x0083AA7B,0x7C8C1AE8,0x7BC6B542)
7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x0083AA7B,0x057CAED0,0x10012A03,0x00000000)
7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7C8C1B1C,0x00000000,0x00000000,0x00000000)
7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFC0FB8,0x7C8C2490,0x7C8C2490,0x7C8C2490)
B7E184FB              start_thread+203 (0x7C8C2B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 35 ---
7B88DCF4 KERNEL32.dll SleepEx+68 (0x0000000A,0x00000000,0x00000000,0x00000000)
7B88DD45 KERNEL32.dll Sleep+37 (0x0000000A,0x7CA32A38,0x0083AAE9,0x0000000A)
008369BA Wow.exe      <unknown symbol>+0 (0x0000000A,0x082BE748,0x00000023,0x7CA32A48)
0083AAE9 Wow.exe      <unknown symbol>+0 (0x082BE748,0x0083AA7B,0x7CA32AE8,0x7BC6B542)
7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x0083AA7B,0x082BE748,0x10012A03,0x00000000)
7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7CA32B1C,0x00000000,0x00000000,0x00000000)
7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFC4FB8,0x7CA33490,0x7CA33490,0x7CA33490)
B7E184FB              start_thread+203 (0x7CA33B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 34 ---
7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7CBA38BC,0x00000004,0x00000000)
7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7CBA38BC,0x00000000,0x00000000)
7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7CBA39FC,0x00000000,0xFFFFFFFF)
7B88BCAC KERNEL32.dll WaitForSingleObject+60 (0x00002084,0xFFFFFFFF,0x7CBA3A1C,0x007805B2)
006A5C40 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x012E8CC8,0x00000022,0x00780550)
007805B2 Wow.exe      <unknown symbol>+0 (0x012E8CC8,0x006A1F00,0x0305F150,0x7BC88444)
006A1F57 Wow.exe      <unknown symbol>+0 (0x000020E4,0x006A1F00,0x7CBA3AE8,0x7BC6B542)
7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x006A1F00,0x0305F150,0x10012A03,0x00000000)
7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7CBA3B1C,0x00000000,0x00000000,0x00000000)
7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x7CBA4490,0x7CBA4490,0x7CBA4490)
B7E184FB              start_thread+203 (0x7CBA4B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 33 ---
7B88DCF4 KERNEL32.dll SleepEx+68 (0x00000001,0x00000000,0x00000000,0x00000000)
7B88DD45 KERNEL32.dll Sleep+37 (0x00000001,0x7CD14A1C,0x00455159,0x00000001)
007CAA8D Wow.exe      <unknown symbol>+0 (0x00000001,0x00454F80,0x0308C518,0x00000021)
00455159 Wow.exe      <unknown symbol>+0 (0x0308C518,0x006A1F00,0x03087198,0x7BC88444)
006A1F57 Wow.exe      <unknown symbol>+0 (0x000020E0,0x006A1F00,0x7CD14AE8,0x7BC6B542)
7BC6AEAE ntdll.dll    call_thread_entry_point+14 (0x006A1F00,0x03087198,0x10012A03,0x00000000)
7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7CD14B1C,0x00000000,0x00000000,0x00000000)
7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x7CD15490,0x7CD15490,0x7CD15490)
B7E184FB              start_thread+203 (0x7CD15B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 43 ---
7B88DCF4 KERNEL32.dll SleepEx+68 (0x00000064,0x00000000,0x7CE859D0,0x7B854DC7)
7B88DD45 KERNEL32.dll Sleep+37 (0x00000064,0x007E9D05,0x7BC88444,0x030E1BD8)
006BDA34 Wow.exe      <unknown symbol>+0 (0x030E1BD8,0xA83F670A,0x007E9D05,0x030E84A8)
007E9CDF Wow.exe      <unknown symbol>+0 (0x030E84A8,0x7BC6AEAE,0x030E84A8,0x007E9D05)
007E9D84 Wow.exe      <unknown symbol>+0 (0x007E9D05,0x030E84A8,0x10012A03,0x00000000)
7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7CE85B1C,0x00000000,0x00000000,0x00000000)
7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFD0FB8,0x7CE86490,0x7CE86490,0x7CE86490)
B7E184FB              start_thread+203 (0x7CE86B90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 59 ---
7BC68F2B ntdll.dll    NTDLL_wait_for_multiple_objects+523 (0x00000001,0x7D0DA890,0x00000004,0x00000000)
7BC69202 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x7D0DA890,0x00000000,0x00000000)
7B88BAB2 KERNEL32.dll WaitForMultipleObjectsEx+322 (0x00000001,0x7D0DA9D0,0x00000000,0xFFFFFFFF)
7B88BCAC KERNEL32.dll WaitForSingleObject+60 (0x000020C0,0xFFFFFFFF,0x7BC88444,0x007E9D05)
006BBB05 Wow.exe      <unknown symbol>+0 (0x017E44E0,0x007E9D05,0x0189A880,0x7D0DAA30)
006D83E5 Wow.exe      <unknown symbol>+0 (0x0189A840,0xA9DA970A,0x007E9D05,0x0189A880)
007E9CDF Wow.exe      <unknown symbol>+0 (0x0189A880,0x7BC6AEAE,0x0189A880,0x0189A880)
007E9D84 Wow.exe      <unknown symbol>+0 (0x007E9D05,0x0189A880,0x10012A03,0x00000000)
7BC6B542 ntdll.dll    <unknown symbol>+0 (0x7D0DAB1C,0x00000000,0x00000000,0x00000000)
7BC6B772 ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x7D0DB490,0x7D0DB490,0x7D0DB490)
B7E184FB              start_thread+203 (0x7D0DBB90,0x00000000,0x00000000,0x00000000)

--- Thread ID: 50 [Current Thread] ---
005CEF48 Wow.exe      <unknown symbol>+0 (0x00000006,0x011B0CC8,0x00000006,0x0000008F)
005CC53A Wow.exe      <unknown symbol>+0 (0x084173B0,0x0000000C,0x0000008F,0x07A55240)
0079A067 Wow.exe      <unknown symbol>+0 (0x00000000,0x003AFA40,0x07A3D0F8,0x00000000)
00786E18 Wow.exe      <unknown symbol>+0 (0x00000001,0x00000000,0x079F58A0,0x3F77FE41)
007880F7 Wow.exe      <unknown symbol>+0 (0x00000001,0x087407A8,0x07A3D0F8,0x00000042)
00788375 Wow.exe      <unknown symbol>+0 (0x00000001,0x00000000,0x07A41C64,0x3F800000)
008AFBCB Wow.exe      <unknown symbol>+0 (0x3F800000,0x00000003,0xFF000000,0x078C109C)
0047BD11 Wow.exe      <unknown symbol>+0 (0x4405199A,0x00000001,0x078C1020,0x078C109C)
0042C162 Wow.exe      <unknown symbol>+0 (0x078C109C,0x0788C5B0,0x00000006,0x0788B8C0)
004393C7 Wow.exe      <unknown symbol>+0 (0x03124108,0x0788B5D8,0x0788B5C0,0x00000000)
004398B9 Wow.exe      <unknown symbol>+0 (0x00000000,0x0788B5C8,0x0788B5D8,0x3EEB020D)
00443F6C Wow.exe      <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x017E2590)
00427AE9 Wow.exe      <unknown symbol>+0 (0x017E2590,0x00000011,0x00000000,0x00001770)
00426429 Wow.exe      <unknown symbol>+0 (0x00000000,0x00406A80,0x00000001,0x00000001)
00426501 Wow.exe      <unknown symbol>+0 (0x0040AD49,0x00400000,0x00000000,0x00111E9D)
00406AE8 Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B8773A7 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x01390000  Z:\mnt\windows\Users\Public\Games\World of Warcraft\Wow.exe
0x10000000 - 0x10069000  Z:\mnt\windows\Users\Public\Games\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B92D000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCA4000  C:\windows\system32\ntdll.dll
0x7BFC0000 - 0x7C000000  C:\windows\system32\dbghelp.dll
0x7D430000 - 0x7D442000  C:\windows\system32\psapi.dll
0x7D4C0000 - 0x7D4E6000  C:\windows\system32\uxtheme.dll
0x7D560000 - 0x7D567000  C:\windows\system32\midimap.dll
0x7D570000 - 0x7D57E000  C:\windows\system32\msacm32.drv
0x7D650000 - 0x7D677000  C:\windows\system32\winealsa.drv
0x7D6B0000 - 0x7D739000  C:\windows\system32\winex11.drv
0x7D840000 - 0x7D892000  C:\windows\system32\rpcrt4.dll
0x7D8A0000 - 0x7D936000  C:\windows\system32\ole32.dll
0x7D940000 - 0x7D95C000  C:\windows\system32\msacm32.dll
0x7D980000 - 0x7D999000  C:\windows\system32\iphlpapi.dll
0x7D9A0000 - 0x7D9C5000  C:\windows\system32\ws2_32.dll
0x7D9D0000 - 0x7DA84000  C:\windows\system32\comctl32.dll
0x7DA90000 - 0x7DB97000  C:\windows\system32\shell32.dll
0x7DBA0000 - 0x7DBF0000  C:\windows\system32\shlwapi.dll
0x7DC00000 - 0x7DC11000  C:\windows\system32\mpr.dll
0x7DC20000 - 0x7DC5F000  C:\windows\system32\wininet.dll
0x7DC70000 - 0x7DC7F000  C:\windows\system32\imm32.dll
0x7DC80000 - 0x7DC93000  C:\windows\system32\lz32.dll
0x7DCA0000 - 0x7DCAC000  C:\windows\system32\version.dll
0x7DCC0000 - 0x7DDAF000  C:\windows\system32\wined3d.dll
0x7DDC0000 - 0x7DDDF000  C:\windows\system32\d3d9.dll
0x7EB40000 - 0x7EBB1000  C:\windows\system32\opengl32.dll
0x7EBC0000 - 0x7EC03000  C:\windows\system32\advapi32.dll
0x7EC10000 - 0x7EC9E000  C:\windows\system32\gdi32.dll
0x7ECC0000 - 0x7EDE5000  C:\windows\system32\user32.dll
0x7EDF0000 - 0x7EE77000  C:\windows\system32\winmm.dll

---

