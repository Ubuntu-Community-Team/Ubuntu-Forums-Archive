---
title: "Wine locking my files?"
date: 2009-11-10
forum: Wine
---

### Post by Dreygz on 2009-11-10
So on Nov. 9th 2009 Blizzard released a very small patch for WoW... ever since that patch i have been unable to play, i tried running the program in sudo and tht didn't work so i went to the actual wine folder to see what was going on and in the program files the WoW file had a lock and an x on the file and it told me that these files do not belong to me... anyone had this issue or possibly have any hints as to how i could fix this?

---

### Post by Drezliok on 2009-11-10
same.

Goto the folder and change it's permissions. I was able to right click it normal user mode and do it.

Then if you want to play into the game folder and right click WoW.exe and tell it to run in wine.

The launcher and desktop link will force it to lock again.

---

### Post by Dreygz on 2009-11-10
I was able to change permission but now when i try to start it i get this
```
==============================================================================

World of WarCraft (build 8874)



Exe:      C:\Program Files\World of Warcraft\Wow.exe

Time:     Sep 23, 2009  5:06:31.885 PM

User:     taylor

Computer: taylor-desktop

------------------------------------------------------------------------------



This application has encountered a critical error:



ERROR #132 (0x85100084) Fatal Exception

Program:	C:\Program Files\World of Warcraft\Wow.exe

Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7D959C69



The instruction at "0x7D959C69" referenced memory at "0x00000000".

The memory could not be "read".





WoWBuild: 8874

Settings: 

SET readTOS "-1"

SET readEULA "-1"

SET readTerminationWithoutNotice "-1"

SET readScanning "-1"

SET readContest "-1"

SET locale "enUS"

SET movie "0"

SET showToolsUI "1"

SET portal "us"

SET realmList "us.logon.worldofwarcraft.com"

SET coresDetected "2"

SET hwDetect "0"

SET gxColorBits "24"

SET gxDepthBits "24"

SET gxResolution "1024x768"

SET gxRefresh "57"

SET gxMultisampleQuality "0.000000"

SET gxFixLag "0"

SET videoOptionsVersion "1"

SET Sound_OutputDriverName "System Default"

SET farclip "777.000000"

SET specular "1"

SET particleDensity "1.000000"

SET groundEffectDensity "24"

------------------------------------------------------------------------------



----------------------------------------

    x86 Registers

----------------------------------------



EAX=00000000  EBX=7D99FFF4  ECX=00000003  EDX=FFFFFFFF  ESI=001474F8

EDI=0015DFB8  EBP=003AD2A8  ESP=003AD280  EIP=7D959C69  FLG=00010246

CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B





----------------------------------------

    Stack Trace (Manual)

----------------------------------------



Address  Frame    Logical addr  Module



Showing 13/13 threads...



--- Thread ID: 39 ---

7BC722D5 0B2AE9E8 0001:000612D5 C:\windows\system32\ntdll.dll

7BC725D2 0B2AEA18 0001:000615D2 C:\windows\system32\ntdll.dll

7BC7262C 0B2AEA38 0001:0006162C C:\windows\system32\ntdll.dll

7BC77A75 0B2AEA98 0001:00066A75 C:\windows\system32\ntdll.dll

7BC6BA74 0B2AEAA8 0001:0005AA74 C:\windows\system32\ntdll.dll

7BC6BC90 0B2AEB78 0001:0005AC90 C:\windows\system32\ntdll.dll

7BC73EDB 0B2AF3B8 0001:00062EDB C:\windows\system32\ntdll.dll

B7EB34FF 0B2AF4B8 0000:00000000 <unknown>



--- Thread ID: 38 ---

7BC722D5 0B02E6A4 0001:000612D5 C:\windows\system32\ntdll.dll

7BC725D2 0B02E6D4 0001:000615D2 C:\windows\system32\ntdll.dll

7B8900B2 0B02E814 0001:0006F0B2 C:\windows\system32\KERNEL32.dll

7D18639B 0B02E844 0001:0003539B C:\windows\system32\winex11.drv

7ED0E095 0B02E9F4 0001:0006D095 C:\windows\system32\user32.dll

7ED0E0FF 0B02EA14 0001:0006D0FF C:\windows\system32\user32.dll

006DB5F7 0B02EA44 0001:002DA5F7 C:\Program Files\World of Warcraft\Wow.exe

006D99C5 0B02EA58 0001:002D89C5 C:\Program Files\World of Warcraft\Wow.exe

007E734F 0B02EA90 0001:003E634F C:\Program Files\World of Warcraft\Wow.exe

007E73F4 0B02EAA8 0001:003E63F4 C:\Program Files\World of Warcraft\Wow.exe

7BC6BC90 0B02EB78 0001:0005AC90 C:\windows\system32\ntdll.dll

7BC73EDB 0B02F3B8 0001:00062EDB C:\windows\system32\ntdll.dll

B7EB34FF 0B02F4B8 0000:00000000 <unknown>



--- Thread ID: 37 ---

7BC722D5 08EBE688 0001:000612D5 C:\windows\system32\ntdll.dll

7BC725D2 08EBE6B8 0001:000615D2 C:\windows\system32\ntdll.dll

7B8900B2 08EBE7F8 0001:0006F0B2 C:\windows\system32\KERNEL32.dll

7B89020A 08EBE818 0001:0006F20A C:\windows\system32\KERNEL32.dll

0042236B 08EBEA70 0001:0002136B C:\Program Files\World of Warcraft\Wow.exe

00421C7E 08EBEA7C 0001:00020C7E C:\Program Files\World of Warcraft\Wow.exe

006A25F7 08EBEA98 0001:002A15F7 C:\Program Files\World of Warcraft\Wow.exe

7BC6BA74 08EBEAA8 0001:0005AA74 C:\windows\system32\ntdll.dll

7BC6BC90 08EBEB78 0001:0005AC90 C:\windows\system32\ntdll.dll

7BC73EDB 08EBF3B8 0001:00062EDB C:\windows\system32\ntdll.dll

B7EB34FF 08EBF4B8 0000:00000000 <unknown>



--- Thread ID: 36 ---

7BC722D5 08D4E8B8 0001:000612D5 C:\windows\system32\ntdll.dll

7BC725D2 08D4E8E8 0001:000615D2 C:\windows\system32\ntdll.dll

7B8900B2 08D4EA28 0001:0006F0B2 C:\windows\system32\KERNEL32.dll

7B8902AC 08D4EA48 0001:0006F2AC C:\windows\system32\KERNEL32.dll

006A62D0 08D4EA58 0001:002A52D0 C:\Program Files\World of Warcraft\Wow.exe

00421B45 08D4EA70 0001:00020B45 C:\Program Files\World of Warcraft\Wow.exe

00421C61 08D4EA7C 0001:00020C61 C:\Program Files\World of Warcraft\Wow.exe

006A25F7 08D4EA98 0001:002A15F7 C:\Program Files\World of Warcraft\Wow.exe

7BC6BA74 08D4EAA8 0001:0005AA74 C:\windows\system32\ntdll.dll

7BC6BC90 08D4EB78 0001:0005AC90 C:\windows\system32\ntdll.dll

7BC73EDB 08D4F3B8 0001:00062EDB C:\windows\system32\ntdll.dll

B7EB34FF 08D4F4B8 0000:00000000 <unknown>



--- Thread ID: 35 ---

7B8903C2 08ACEA58 0001:0006F3C2 C:\windows\system32\KERNEL32.dll

7B890405 08ACEA78 0001:0006F405 C:\windows\system32\KERNEL32.dll

00834994 08ACEA84 0001:00433994 C:\Program Files\World of Warcraft\Wow.exe

00838AB9 08ACEA98 0001:00437AB9 C:\Program Files\World of Warcraft\Wow.exe

7BC6BA74 08ACEAA8 0001:0005AA74 C:\windows\system32\ntdll.dll

7BC6BC90 08ACEB78 0001:0005AC90 C:\windows\system32\ntdll.dll

7BC73EDB 08ACF3B8 0001:00062EDB C:\windows\system32\ntdll.dll

B7EB34FF 08ACF4B8 0000:00000000 <unknown>



--- Thread ID: 34 ---

7B8903C2 0895EA58 0001:0006F3C2 C:\windows\system32\KERNEL32.dll

7B890405 0895EA78 0001:0006F405 C:\windows\system32\KERNEL32.dll

00834994 0895EA84 0001:00433994 C:\Program Files\World of Warcraft\Wow.exe

00838AB9 0895EA98 0001:00437AB9 C:\Program Files\World of Warcraft\Wow.exe

7BC6BA74 0895EAA8 0001:0005AA74 C:\windows\system32\ntdll.dll

7BC6BC90 0895EB78 0001:0005AC90 C:\windows\system32\ntdll.dll

7BC73EDB 0895F3B8 0001:00062EDB C:\windows\system32\ntdll.dll

B7EB34FF 0895F4B8 0000:00000000 <unknown>



--- Thread ID: 33 ---

7B8903C2 087EEA58 0001:0006F3C2 C:\windows\system32\KERNEL32.dll

7B890405 087EEA78 0001:0006F405 C:\windows\system32\KERNEL32.dll

00834994 087EEA84 0001:00433994 C:\Program Files\World of Warcraft\Wow.exe

00838AB9 087EEA98 0001:00437AB9 C:\Program Files\World of Warcraft\Wow.exe

7BC6BA74 087EEAA8 0001:0005AA74 C:\windows\system32\ntdll.dll

7BC6BC90 087EEB78 0001:0005AC90 C:\windows\system32\ntdll.dll

7BC73EDB 087EF3B8 0001:00062EDB C:\windows\system32\ntdll.dll

B7EB34FF 087EF4B8 0000:00000000 <unknown>



--- Thread ID: 32 ---

7B8903C2 0867EA58 0001:0006F3C2 C:\windows\system32\KERNEL32.dll

7B890405 0867EA78 0001:0006F405 C:\windows\system32\KERNEL32.dll

00834994 0867EA84 0001:00433994 C:\Program Files\World of Warcraft\Wow.exe

00838AB9 0867EA98 0001:00437AB9 C:\Program Files\World of Warcraft\Wow.exe

7BC6BA74 0867EAA8 0001:0005AA74 C:\windows\system32\ntdll.dll

7BC6BC90 0867EB78 0001:0005AC90 C:\windows\system32\ntdll.dll

7BC73EDB 0867F3B8 0001:00062EDB C:\windows\system32\ntdll.dll

B7EB34FF 0867F4B8 0000:00000000 <unknown>



--- Thread ID: 31 ---

7EDFEE57 0850EA98 0001:0002DE57 C:\windows\system32\winmm.dll

7BC6BA74 0850EAA8 0001:0005AA74 C:\windows\system32\ntdll.dll

7BC6BC90 0850EB78 0001:0005AC90 C:\windows\system32\ntdll.dll

7BC73EDB 0850F3B8 0001:00062EDB C:\windows\system32\ntdll.dll

B7EB34FF 0850F4B8 0000:00000000 <unknown>



--- Thread ID: 30 ---

7BC722D5 0437E8C4 0001:000612D5 C:\windows\system32\ntdll.dll

7BC725D2 0437E8F4 0001:000615D2 C:\windows\system32\ntdll.dll

7B8900B2 0437EA34 0001:0006F0B2 C:\windows\system32\KERNEL32.dll

7B8902AC 0437EA54 0001:0006F2AC C:\windows\system32\KERNEL32.dll

006A62D0 0437EA64 0001:002A52D0 C:\Program Files\World of Warcraft\Wow.exe

0077E422 0437EA7C 0001:0037D422 C:\Program Files\World of Warcraft\Wow.exe

006A25F7 0437EA98 0001:002A15F7 C:\Program Files\World of Warcraft\Wow.exe

7BC6BA74 0437EAA8 0001:0005AA74 C:\windows\system32\ntdll.dll

7BC6BC90 0437EB78 0001:0005AC90 C:\windows\system32\ntdll.dll

7BC73EDB 0437F3B8 0001:00062EDB C:\windows\system32\ntdll.dll

B7EB34FF 0437F4B8 0000:00000000 <unknown>



--- Thread ID: 29 ---

7B8903C2 0420E630 0001:0006F3C2 C:\windows\system32\KERNEL32.dll

7B890405 0420E650 0001:0006F405 C:\windows\system32\KERNEL32.dll

007C8E8D 0420E65C 0001:003C7E8D C:\Program Files\World of Warcraft\Wow.exe

00454D79 0420EA7C 0001:00053D79 C:\Program Files\World of Warcraft\Wow.exe

006A25F7 0420EA98 0001:002A15F7 C:\Program Files\World of Warcraft\Wow.exe

7BC6BA74 0420EAA8 0001:0005AA74 C:\windows\system32\ntdll.dll

7BC6BC90 0420EB78 0001:0005AC90 C:\windows\system32\ntdll.dll

7BC73EDB 0420F3B8 0001:00062EDB C:\windows\system32\ntdll.dll

B7EB34FF 0420F4B8 0000:00000000 <unknown>



--- Thread ID: 28 ---

7B8903C2 0409EA10 0001:0006F3C2 C:\windows\system32\KERNEL32.dll

7B890405 0409EA30 0001:0006F405 C:\windows\system32\KERNEL32.dll

006BF014 0409EA58 0001:002BE014 C:\Program Files\World of Warcraft\Wow.exe

007E734F 0409EA90 0001:003E634F C:\Program Files\World of Warcraft\Wow.exe

007E73F4 0409EAA8 0001:003E63F4 C:\Program Files\World of Warcraft\Wow.exe

7BC6BC90 0409EB78 0001:0005AC90 C:\windows\system32\ntdll.dll

7BC73EDB 0409F3B8 0001:00062EDB C:\windows\system32\ntdll.dll

B7EB34FF 0409F4B8 0000:00000000 <unknown>



--- Thread ID: 25 [Current Thread] ---

7D959C69 003AD2A8 0001:000D8C69 C:\windows\system32\wined3d.dll

7D8AA3BC 003AD588 0001:000293BC C:\windows\system32\wined3d.dll

7D8BE31F 003AD5E8 0001:0003D31F C:\windows\system32\wined3d.dll

7D8C7D4D 003AD668 0001:00046D4D C:\windows\system32\wined3d.dll

7D9BC9BA 003AD6D8 0001:0000B9BA C:\windows\system32\d3d9.dll

005DA88C 003AD734 0001:001D988C C:\Program Files\World of Warcraft\Wow.exe

005D8E4F 003AD7A4 0001:001D7E4F C:\Program Files\World of Warcraft\Wow.exe

7ED4866A 003AD7D4 0001:000A766A C:\windows\system32\user32.dll

7ED48ABA 003AD814 0001:000A7ABA C:\windows\system32\user32.dll

7ED4B8E5 003ADCE4 0001:000AA8E5 C:\windows\system32\user32.dll

7ED4DE7E 003ADD24 0001:000ACE7E C:\windows\system32\user32.dll

7ED0CC41 003ADD84 0001:0006BC41 C:\windows\system32\user32.dll

7ED11F45 003ADDE4 0001:00070F45 C:\windows\system32\user32.dll

7ED1245C 003ADE24 0001:0007145C C:\windows\system32\user32.dll

7ECD3574 003ADEF4 0001:00032574 C:\windows\system32\user32.dll

7ECD4361 003ADF44 0001:00033361 C:\windows\system32\user32.dll

007C856A 003ADF78 0001:003C756A C:\Program Files\World of Warcraft\Wow.exe

005D8F60 003ADFEC 0001:001D7F60 C:\Program Files\World of Warcraft\Wow.exe

7ED4866A 003AE01C 0001:000A766A C:\windows\system32\user32.dll

7ED48ABA 003AE05C 0001:000A7ABA C:\windows\system32\user32.dll

7ED4B8E5 003AE52C 0001:000AA8E5 C:\windows\system32\user32.dll

7ED4DE7E 003AE56C 0001:000ACE7E C:\windows\system32\user32.dll

7ED0CC41 003AE5CC 0001:0006BC41 C:\windows\system32\user32.dll

7ED11F45 003AE62C 0001:00070F45 C:\windows\system32\user32.dll

7ED1245C 003AE66C 0001:0007145C C:\windows\system32\user32.dll

7ED4335B 003AE7BC 0001:000A235B C:\windows\system32\user32.dll

7ED441B8 003AE82C 0001:000A31B8 C:\windows\system32\user32.dll

7D8BDA39 003AE86C 0001:0003CA39 C:\windows\system32\wined3d.dll

7D8C85F4 003AE8EC 0001:000475F4 C:\windows\system32\wined3d.dll

7D9BC9BA 003AE95C 0001:0000B9BA C:\windows\system32\d3d9.dll

005DA88C 003AE9B8 0001:001D988C C:\Program Files\World of Warcraft\Wow.exe

005D8E4F 003AEA28 0001:001D7E4F C:\Program Files\World of Warcraft\Wow.exe

7ED4866A 003AEA58 0001:000A766A C:\windows\system32\user32.dll

7ED48ABA 003AEA98 0001:000A7ABA C:\windows\system32\user32.dll

7ED4B8E5 003AEF68 0001:000AA8E5 C:\windows\system32\user32.dll

7ED4DE7E 003AEFA8 0001:000ACE7E C:\windows\system32\user32.dll

7ED0CC41 003AF008 0001:0006BC41 C:\windows\system32\user32.dll

7ED11F45 003AF068 0001:00070F45 C:\windows\system32\user32.dll

7ED1245C 003AF0A8 0001:0007145C C:\windows\system32\user32.dll

7ECD3574 003AF178 0001:00032574 C:\windows\system32\user32.dll

7ECD4361 003AF1C8 0001:00033361 C:\windows\system32\user32.dll

007C856A 003AF1FC 0001:003C756A C:\Program Files\World of Warcraft\Wow.exe

005D8F60 003AF270 0001:001D7F60 C:\Program Files\World of Warcraft\Wow.exe

7ED4866A 003AF2A0 0001:000A766A C:\windows\system32\user32.dll

7ED48ABA 003AF2E0 0001:000A7ABA C:\windows\system32\user32.dll

7ED4B8E5 003AF7B0 0001:000AA8E5 C:\windows\system32\user32.dll

7ED4DE7E 003AF7F0 0001:000ACE7E C:\windows\system32\user32.dll

7ED0CC41 003AF850 0001:0006BC41 C:\windows\system32\user32.dll

7ED11F45 003AF8B0 0001:00070F45 C:\windows\system32\user32.dll

7ED1245C 003AF8F0 0001:0007145C C:\windows\system32\user32.dll

7ED4335B 003AFA40 0001:000A235B C:\windows\system32\user32.dll

7ED441B8 003AFAB0 0001:000A31B8 C:\windows\system32\user32.dll

7D1846D4 003AFB30 0001:000336D4 C:\windows\system32\winex11.drv

7D185E8B 003AFC60 0001:00034E8B C:\windows\system32\winex11.drv

7D186335 003AFC90 0001:00035335 C:\windows\system32\winex11.drv

7ED11238 003AFCE0 0001:00070238 C:\windows\system32\user32.dll

7ED1135B 003AFD10 0001:0007035B C:\windows\system32\user32.dll

007C7C20 003AFD64 0001:003C6C20 C:\Program Files\World of Warcraft\Wow.exe

00427526 003AFD9C 0001:00026526 C:\Program Files\World of Warcraft\Wow.exe

00426387 003AFE04 0001:00025387 C:\Program Files\World of Warcraft\Wow.exe

004264F1 003AFE1C 0001:000254F1 C:\Program Files\World of Warcraft\Wow.exe

00406B28 003AFEB8 0001:00005B28 C:\Program Files\World of Warcraft\Wow.exe

7B8785A5 003AFEE8 0001:000575A5 C:\windows\system32\KERNEL32.dll

7BC6BA74 003AFEF8 0001:0005AA74 C:\windows\system32\ntdll.dll

7BC6BC90 003AFFC8 0001:0005AC90 C:\windows\system32\ntdll.dll

7BC497CA 003AFFE8 0001:000387CA C:\windows\system32\ntdll.dll



----------------------------------------

    Stack Trace (Using DBGHELP.DLL)

----------------------------------------



Showing 13/13 threads...



--- Thread ID: 39 ---

7BC722D5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0B2AEA40,0x00000004,0x0B2AEA80)

7BC725D2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0B2AEA40,0x00000000,0x00000000)

7BC7262C ntdll.dll    NtWaitForSingleObject+60 (0x000021AC,0x00000000,0x0B2AEA80,0x7BC91223)

7BC77A75 ntdll.dll    <unknown symbol>+0 (0x00000000,0x7FFA8F10,0x0B2AEB78,0x7BC6BC90)

7BC6BA74 ntdll.dll    call_thread_func+12 (0x7BC77930,0x00000000,0x00000000,0x00000000)

7BC6BC90 ntdll.dll    call_thread_entry_point+112 (0x7BC77930,0x00000000,0x00000000,0x00000000)

7BC73EDB ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x0B2AFB90,0x0B2AFB90,0x0B2AFB90)

B7EB34FF              start_thread+191 (0x0B2AFB90,0x00000000,0x00000000,0x00000000)

B7E2D49E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 38 ---

7BC722D5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x0B02E6FC,0x00000004,0x00000000)

7BC725D2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x0B02E6FC,0x00000000,0x00000000)

7B8900B2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x0B02E874,0x00000000,0xFFFFFFFF)

7D18639B winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x0B02E874,0xFFFFFFFF,0x00000000)

7ED0E095 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x0B02EA3C,0xFFFFFFFF,0x00000000)

7ED0E0FF user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x0B02EA3C,0x00000000,0xFFFFFFFF)

006DB5F7 Wow.exe      <unknown symbol>+0 (0x00F0BA00,0x7FFAC1D4,0x08B0BC68,0x0B02EA90)

006D99C5 Wow.exe      <unknown symbol>+0 (0x08B0BC28,0xD3ED7393,0x7FFAC1D4,0x08B0BC68)

007E734F Wow.exe      <unknown symbol>+0 (0x7FFACF10,0x7BC6BA74,0x08B0BC68,0x7FFACF10)

007E73F4 Wow.exe      <unknown symbol>+0 (0x007E7375,0x08B0BC68,0x00000000,0x00000000)

7BC6BC90 ntdll.dll    call_thread_entry_point+112 (0x007E7375,0x08B0BC68,0x00000000,0x00000000)

7BC73EDB ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x0B02FB90,0x0B02FB90,0x0B02FB90)

B7EB34FF              start_thread+191 (0x0B02FB90,0x00000000,0x00000000,0x00000000)

B7E2D49E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 37 ---

7BC722D5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x08EBE6E0,0x00000004,0x08EBE7E0)

7BC725D2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x08EBE6E0,0x00000000,0x00000000)

7B8900B2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x08EBE93C,0x00000000,0x000001F4)

7B89020A KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x08EBE93C,0x00000000,0x000001F4)

0042236B Wow.exe      <unknown symbol>+0 (0x00421C70,0x08EBEA98,0x006A25F7,0x07E3E808)

00421C7E Wow.exe      <unknown symbol>+0 (0x07E3E808,0x7FFB01D4,0x7FFB0F10,0x7BC94FF4)

006A25F7 Wow.exe      <unknown symbol>+0 (0x00002188,0x7FFB0F10,0x08EBEB78,0x7BC6BC90)

7BC6BA74 ntdll.dll    call_thread_func+12 (0x006A25A0,0x07E3DFE8,0x00000000,0x00000000)

7BC6BC90 ntdll.dll    call_thread_entry_point+112 (0x006A25A0,0x07E3DFE8,0x00000000,0x00000000)

7BC73EDB ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x08EBFB90,0x08EBFB90,0x08EBFB90)

B7EB34FF              start_thread+191 (0x08EBFB90,0x00000000,0x00000000,0x00000000)

B7E2D49E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 36 ---

7BC722D5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x08D4E910,0x00000004,0x08D4EA10)

7BC725D2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x08D4E910,0x00000000,0x00000000)

7B8900B2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x08D4EA50,0x00000000,0x000003E8)

7B8902AC KERNEL32.dll WaitForSingleObject+60 (0x000020F8,0x000003E8,0x08D4EA70,0x00421B45)

006A62D0 Wow.exe      <unknown symbol>+0 (0x000003E8,0x00000024,0x00421C50,0x07E3E818)

00421B45 Wow.exe      <unknown symbol>+0 (0x00000000,0x08D4EA98,0x006A25F7,0x07E3E818)

00421C61 Wow.exe      <unknown symbol>+0 (0x07E3E818,0x7FFB41D4,0x7FFB4F10,0x7BC94FF4)

006A25F7 Wow.exe      <unknown symbol>+0 (0x00002184,0x7FFB4F10,0x08D4EB78,0x7BC6BC90)

7BC6BA74 ntdll.dll    call_thread_func+12 (0x006A25A0,0x07E3DFC8,0x00000000,0x00000000)

7BC6BC90 ntdll.dll    call_thread_entry_point+112 (0x006A25A0,0x07E3DFC8,0x00000000,0x00000000)

7BC73EDB ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x08D4FB90,0x08D4FB90,0x08D4FB90)

B7EB34FF              start_thread+191 (0x08D4FB90,0x00000000,0x00000000,0x00000000)

B7E2D49E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 35 ---

7B8903C2 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x3F733333,0x08ACEA84)

7B890405 KERNEL32.dll Sleep+37 (0x0000000A,0x08ACEA98,0x00838AB9,0x0000000A)

00834994 Wow.exe      <unknown symbol>+0 (0x0000000A,0x7FFB8F10,0x00000023,0x08ACEAA8)

00838AB9 Wow.exe      <unknown symbol>+0 (0x07547FA8,0x7FFB8F10,0x08ACEB78,0x7BC6BC90)

7BC6BA74 ntdll.dll    call_thread_func+12 (0x00838A4B,0x07547FA8,0x00000000,0x00000000)

7BC6BC90 ntdll.dll    call_thread_entry_point+112 (0x00838A4B,0x07547FA8,0x00000000,0x00000000)

7BC73EDB ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x08ACFB90,0x08ACFB90,0x08ACFB90)

B7EB34FF              start_thread+191 (0x08ACFB90,0x00000000,0x00000000,0x00000000)

B7E2D49E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 34 ---

7B8903C2 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x00000000,0x00000000)

7B890405 KERNEL32.dll Sleep+37 (0x0000000A,0x0895EA98,0x00838AB9,0x0000000A)

00834994 Wow.exe      <unknown symbol>+0 (0x0000000A,0x7FFBCF10,0x00000022,0x0895EAA8)

00838AB9 Wow.exe      <unknown symbol>+0 (0x07597288,0x7FFBCF10,0x0895EB78,0x7BC6BC90)

7BC6BA74 ntdll.dll    call_thread_func+12 (0x00838A4B,0x07597288,0x00000000,0x00000000)

7BC6BC90 ntdll.dll    call_thread_entry_point+112 (0x00838A4B,0x07597288,0x00000000,0x00000000)

7BC73EDB ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x0895FB90,0x0895FB90,0x0895FB90)

B7EB34FF              start_thread+191 (0x0895FB90,0x00000000,0x00000000,0x00000000)

B7E2D49E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 33 ---

7B8903C2 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x3F733333,0x087EEA84)

7B890405 KERNEL32.dll Sleep+37 (0x0000000A,0x087EEA98,0x00838AB9,0x0000000A)

00834994 Wow.exe      <unknown symbol>+0 (0x0000000A,0x7FFC0F10,0x00000021,0x087EEAA8)

00838AB9 Wow.exe      <unknown symbol>+0 (0x07557FA8,0x7FFC0F10,0x087EEB78,0x7BC6BC90)

7BC6BA74 ntdll.dll    call_thread_func+12 (0x00838A4B,0x07557FA8,0x00000000,0x00000000)

7BC6BC90 ntdll.dll    call_thread_entry_point+112 (0x00838A4B,0x07557FA8,0x00000000,0x00000000)

7BC73EDB ntdll.dll    <unknown symbol>+0 (0x7FFC0FB8,0x087EFB90,0x087EFB90,0x087EFB90)

B7EB34FF              start_thread+191 (0x087EFB90,0x00000000,0x00000000,0x00000000)

B7E2D49E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 32 ---

7B8903C2 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x00000000,0x00000000)

7B890405 KERNEL32.dll Sleep+37 (0x0000000A,0x0867EA98,0x00838AB9,0x0000000A)

00834994 Wow.exe      <unknown symbol>+0 (0x0000000A,0x7FFC4F10,0x00000020,0x0867EAA8)

00838AB9 Wow.exe      <unknown symbol>+0 (0x074D8288,0x7FFC4F10,0x0867EB78,0x7BC6BC90)

7BC6BA74 ntdll.dll    call_thread_func+12 (0x00838A4B,0x074D8288,0x00000000,0x00000000)

7BC6BC90 ntdll.dll    call_thread_entry_point+112 (0x00838A4B,0x074D8288,0x00000000,0x00000000)

7BC73EDB ntdll.dll    <unknown symbol>+0 (0x7FFC4FB8,0x0867FB90,0x0867FB90,0x0867FB90)

B7EB34FF              start_thread+191 (0x0867FB90,0x00000000,0x00000000,0x00000000)

B7E2D49E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 31 ---

7EDFEE57 winmm.dll    <unknown symbol>+0 (0x00000000,0x7FFC8F10,0x0850EB78,0x7BC6BC90)

7BC6BA74 ntdll.dll    call_thread_func+12 (0x7EDFEC20,0x00000000,0x00000000,0x00000000)

7BC6BC90 ntdll.dll    call_thread_entry_point+112 (0x7EDFEC20,0x00000000,0x00000000,0x00000000)

7BC73EDB ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x0850FB90,0x0850FB90,0x0850FB90)

B7EB34FF              start_thread+191 (0x0850FB90,0x00000000,0x00000000,0x00000000)

B7E2D49E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 30 ---

7BC722D5 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0437E91C,0x00000004,0x00000000)

7BC725D2 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0437E91C,0x00000000,0x00000000)

7B8900B2 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x0437EA5C,0x00000000,0xFFFFFFFF)

7B8902AC KERNEL32.dll WaitForSingleObject+60 (0x00002078,0xFFFFFFFF,0x0437EA7C,0x0077E422)

006A62D0 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x00FEC198,0x0000001E,0x0077E3C0)

0077E422 Wow.exe      <unknown symbol>+0 (0x00FEC198,0x7FFCC1D4,0x7FFCCF10,0x7BC94FF4)

006A25F7 Wow.exe      <unknown symbol>+0 (0x000020C0,0x7FFCCF10,0x0437EB78,0x7BC6BC90)

7BC6BA74 ntdll.dll    call_thread_func+12 (0x006A25A0,0x02B59928,0x00000000,0x00000000)

7BC6BC90 ntdll.dll    call_thread_entry_point+112 (0x006A25A0,0x02B59928,0x00000000,0x00000000)

7BC73EDB ntdll.dll    <unknown symbol>+0 (0x7FFCCFB8,0x0437FB90,0x0437FB90,0x0437FB90)

B7EB34FF              start_thread+191 (0x0437FB90,0x00000000,0x00000000,0x00000000)

B7E2D49E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 29 ---

7B8903C2 KERNEL32.dll SleepEx+50 (0x00000001,0x00000000,0x00000000,0x00000000)

7B890405 KERNEL32.dll Sleep+37 (0x00000001,0x0420EA7C,0x00454D79,0x00000001)

007C8E8D Wow.exe      <unknown symbol>+0 (0x00000001,0x00454BA0,0x02B58A28,0x0000001D)

00454D79 Wow.exe      <unknown symbol>+0 (0x02B58A28,0x7FFD01D4,0x7FFD0F10,0x7BC94FF4)

006A25F7 Wow.exe      <unknown symbol>+0 (0x000020BC,0x7FFD0F10,0x0420EB78,0x7BC6BC90)

7BC6BA74 ntdll.dll    call_thread_func+12 (0x006A25A0,0x02B58A48,0x00000000,0x00000000)

7BC6BC90 ntdll.dll    call_thread_entry_point+112 (0x006A25A0,0x02B58A48,0x00000000,0x00000000)

7BC73EDB ntdll.dll    <unknown symbol>+0 (0x7FFD0FB8,0x0420FB90,0x0420FB90,0x0420FB90)

B7EB34FF              start_thread+191 (0x0420FB90,0x00000000,0x00000000,0x00000000)

B7E2D49E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 28 ---

7B8903C2 KERNEL32.dll SleepEx+50 (0x00000064,0x00000000,0x0409EA30,0x7B854D17)

7B890405 KERNEL32.dll Sleep+37 (0x00000064,0x7B8903E0,0x7BC94FF4,0x01400BF8)

006BF014 Wow.exe      <unknown symbol>+0 (0x01400BF8,0xDCE67393,0x7FFD41D4,0x01400C38)

007E734F Wow.exe      <unknown symbol>+0 (0x7FFD4F10,0x7BC6BA74,0x01400C38,0x7FFD4F10)

007E73F4 Wow.exe      <unknown symbol>+0 (0x007E7375,0x01400C38,0x00000000,0x00000000)

7BC6BC90 ntdll.dll    call_thread_entry_point+112 (0x007E7375,0x01400C38,0x00000000,0x00000000)

7BC73EDB ntdll.dll    <unknown symbol>+0 (0x7FFD4FB8,0x0409FB90,0x0409FB90,0x0409FB90)

B7EB34FF              start_thread+191 (0x0409FB90,0x00000000,0x00000000,0x00000000)

B7E2D49E              clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)



--- Thread ID: 25 [Current Thread] ---

7D959C69 wined3d.dll  IWineD3DSwapChainImpl_CreateContextForThread+57 (0x0015DFB8,0x7D998530,0x003AD578,0x00000000)

7D8AA3BC wined3d.dll  ActivateContext+284 (0x001474F8,0x00000000,0x00000001,0x00000000)

7D8BE31F wined3d.dll  delete_opengl_contexts+47 (0x001474F8,0x0015DFB8,0x00000000,0x00000007)

7D8C7D4D wined3d.dll  <unknown symbol>+0 (0x001474F8,0x003AD68C,0x003AD6C8,0x00000000)

7D9BC9BA d3d9.dll     <unknown symbol>+0 (0x0013FAE0,0x003AD6EC,0x0152C008,0x00000400)

005DA88C Wow.exe      <unknown symbol>+0 (0x00000000,0x003AD794,0x00000000,0x00040030)

005D8E4F Wow.exe      <unknown symbol>+0 (0x00040030,0x00000005,0x00000000,0x00000400)

7ED4866A user32.dll   WINPROC_wrapper+26 (0x005D8CE0,0x00040030,0x00000005,0x00000000)

7ED48ABA user32.dll   WINPROC_wrapper+1130 (0x00040030,0x00000005,0x00000000,0x03000400)

7ED4B8E5 user32.dll   <unknown symbol>+0 (0x00000005,0x00000000,0x03000400,0x003ADD78)

7ED4DE7E user32.dll   <unknown symbol>+0 (0x00040030,0x00000005,0x00000000,0x03000400)

7ED0CC41 user32.dll   <unknown symbol>+0 (0x00000000,0x03000400,0x00000001,0x00000001)

7ED11F45 user32.dll   <unknown symbol>+0 (0x00000001,0x00040030,0x00000001,0x00000019)

7ED1245C user32.dll   SendMessageW+76 (0x00040030,0x00000005,0x00000000,0x03000400)

7ECD3574 user32.dll   <unknown symbol>+0 (0x00000000,0x003AE804,0x00000047,0x00000000)

7ECD4361 user32.dll   DefWindowProcA+161 (0x00040030,0x00000047,0x00000000,0x003AE804)

007C856A Wow.exe      <unknown symbol>+0 (0x00040030,0x00000047,0x00000000,0x003AE804)

005D8F60 Wow.exe      <unknown symbol>+0 (0x00040030,0x00000047,0x00000000,0x003AE804)

7ED4866A user32.dll   WINPROC_wrapper+26 (0x005D8CE0,0x00040030,0x00000047,0x00000000)

7ED48ABA user32.dll   WINPROC_wrapper+1130 (0x00040030,0x00000047,0x00000000,0x003AE804)

7ED4B8E5 user32.dll   <unknown symbol>+0 (0x00000047,0x00000000,0x003AE804,0x003AE5C0)

7ED4DE7E user32.dll   <unknown symbol>+0 (0x00040030,0x00000047,0x00000000,0x003AE804)

7ED0CC41 user32.dll   <unknown symbol>+0 (0x00000000,0x003AE804,0x00000001,0x00000001)

7ED11F45 user32.dll   <unknown symbol>+0 (0x00000001,0x003AE804,0x00000001,0x00000019)

7ED1245C user32.dll   SendMessageW+76 (0x00040030,0x00000047,0x00000000,0x003AE804)

7ED4335B user32.dll   <unknown symbol>+0 (0x003AE804,0x00000000,0x0013BFAC,0x7D99FFF4)

7ED441B8 user32.dll   SetWindowPos+168 (0x00040030,0x00000000,0x00000000,0x00000000)

7D8BDA39 wined3d.dll  <unknown symbol>+0 (0x00000400,0x00000300,0x00000000,0x00000007)

7D8C85F4 wined3d.dll  <unknown symbol>+0 (0x001474F8,0x003AE910,0x003AE94C,0x00000000)

7D9BC9BA d3d9.dll     <unknown symbol>+0 (0x0013FAE0,0x003AE970,0x0152C008,0x00000400)

005DA88C Wow.exe      <unknown symbol>+0 (0x00000000,0x003AEA18,0x00000000,0x00040030)

005D8E4F Wow.exe      <unknown symbol>+0 (0x00040030,0x00000005,0x00000000,0x00000400)

7ED4866A user32.dll   WINPROC_wrapper+26 (0x005D8CE0,0x00040030,0x00000005,0x00000000)

7ED48ABA user32.dll   WINPROC_wrapper+1130 (0x00040030,0x00000005,0x00000000,0x02D00400)

7ED4B8E5 user32.dll   <unknown symbol>+0 (0x00000005,0x00000000,0x02D00400,0x003AEFFC)

7ED4DE7E user32.dll   <unknown symbol>+0 (0x00040030,0x00000005,0x00000000,0x02D00400)

7ED0CC41 user32.dll   <unknown symbol>+0 (0x00000000,0x02D00400,0x00000001,0x00000001)

7ED11F45 user32.dll   <unknown symbol>+0 (0x00000001,0x00040030,0x00000001,0x00000019)

7ED1245C user32.dll   SendMessageW+76 (0x00040030,0x00000005,0x00000000,0x02D00400)

7ECD3574 user32.dll   <unknown symbol>+0 (0x00000000,0x003AFA88,0x00000047,0x00000000)

7ECD4361 user32.dll   DefWindowProcA+161 (0x00040030,0x00000047,0x00000000,0x003AFA88)

007C856A Wow.exe      <unknown symbol>+0 (0x00040030,0x00000047,0x00000000,0x003AFA88)

005D8F60 Wow.exe      <unknown symbol>+0 (0x00040030,0x00000047,0x00000000,0x003AFA88)

7ED4866A user32.dll   WINPROC_wrapper+26 (0x005D8CE0,0x00040030,0x00000047,0x00000000)

7ED48ABA user32.dll   WINPROC_wrapper+1130 (0x00040030,0x00000047,0x00000000,0x003AFA88)

7ED4B8E5 user32.dll   <unknown symbol>+0 (0x00000047,0x00000000,0x003AFA88,0x003AF844)

7ED4DE7E user32.dll   <unknown symbol>+0 (0x00040030,0x00000047,0x00000000,0x003AFA88)

7ED0CC41 user32.dll   <unknown symbol>+0 (0x00000000,0x003AFA88,0x00000001,0x00000001)

7ED11F45 user32.dll   <unknown symbol>+0 (0x00000001,0x00000000,0x00000001,0x00000019)

7ED1245C user32.dll   SendMessageW+76 (0x00040030,0x00000047,0x00000000,0x003AFA88)

7ED4335B user32.dll   <unknown symbol>+0 (0x003AFA88,0x03A0000B,0x00000101,0x00000000)

7ED441B8 user32.dll   SetWindowPos+168 (0x00040030,0x00000000,0x00000000,0x00000018)

7D1846D4 winex11.drv  <unknown symbol>+0 (0x00040030,0x003AFB90,0xFFFFFFFD,0x003AFB8C)

7D185E8B winex11.drv  <unknown symbol>+0 (0x000004FF,0x00000000,0x00000000,0x00000000)

7D186335 winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+85 (0x00000000,0x00000000,0x00000000,0x000004FF)

7ED11238 user32.dll   PeekMessageW+88 (0x003AFD38,0x00000000,0x00000000,0x00000000)

7ED1135B user32.dll   PeekMessageA+91 (0x003AFD38,0x00000000,0x00000000,0x00000000)

007C7C20 Wow.exe      <unknown symbol>+0 (0x003AFDA4,0x003AFD88,0x003AFD8C,0x003AFD90)

00427526 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x003AFDFC,0x00000A28,0x00000002)

00426387 Wow.exe      <unknown symbol>+0 (0x00000000,0x00406AC0,0x00000001,0x00000001)

004264F1 Wow.exe      <unknown symbol>+0 (0x0040ADD9,0x00400000,0x00000000,0x00111A9C)

00406B28 Wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)

7B8785A5 KERNEL32.dll <unknown symbol>+0 (0x7FFDF000,0xBFC2DE54,0x003AFFC8,0x7BC6BC90)

7BC6BA74 ntdll.dll    call_thread_func+12 (0x7B878550,0x7FFDF000,0x00000000,0x00000000)

7BC6BC90 ntdll.dll    call_thread_entry_point+112 (0x7B878550,0x7FFDF000,0x00000000,0x00000000)

7BC497CA ntdll.dll    <unknown symbol>+0 (0x7B878550,0x00000000,0x00000000,0x00000000)

B7EDD01D              wine_call_on_stack+29 (0x00000000,0x00000000,0x00000000,0x00000000)





----------------------------------------

    Loaded Modules

----------------------------------------



0x00400000 - 0x01093000  C:\Program Files\World of Warcraft\Wow.exe

0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll

0x7B820000 - 0x7B96E000  C:\windows\system32\KERNEL32.dll

0x7BC10000 - 0x7BCB1000  C:\windows\system32\ntdll.dll

0x7BCC0000 - 0x7BD00000  C:\windows\system32\dbghelp.dll

0x7BF40000 - 0x7BF80000  C:\windows\system32\dsound.dll

0x7C670000 - 0x7C67F000  C:\windows\system32\psapi.dll

0x7C6B0000 - 0x7C6DF000  C:\windows\system32\uxtheme.dll

0x7C760000 - 0x7C773000  C:\windows\system32\midimap.dll

0x7C780000 - 0x7C78B000  C:\windows\system32\msacm32.drv

0x7D0F0000 - 0x7D115000  C:\windows\system32\winealsa.drv

0x7D150000 - 0x7D1E4000  C:\windows\system32\winex11.drv

0x7D310000 - 0x7D370000  C:\windows\system32\rpcrt4.dll

0x7D390000 - 0x7D46C000  C:\windows\system32\ole32.dll

0x7D470000 - 0x7D492000  C:\windows\system32\msacm32.dll

0x7D4A0000 - 0x7D4C0000  C:\windows\system32\ws2_32.dll

0x7D4D0000 - 0x7D589000  C:\windows\system32\comctl32.dll

0x7D5A0000 - 0x7D719000  C:\windows\system32\shell32.dll

0x7D730000 - 0x7D775000  C:\windows\system32\shlwapi.dll

0x7D780000 - 0x7D798000  C:\windows\system32\mpr.dll

0x7D7D0000 - 0x7D813000  C:\windows\system32\wininet.dll

0x7D820000 - 0x7D834000  C:\windows\system32\imm32.dll

0x7D840000 - 0x7D848000  C:\windows\system32\lz32.dll

0x7D850000 - 0x7D863000  C:\windows\system32\version.dll

0x7D880000 - 0x7D9A2000  C:\windows\system32\wined3d.dll

0x7D9B0000 - 0x7D9D2000  C:\windows\system32\d3d9.dll

0x7EB00000 - 0x7EB83000  C:\windows\system32\opengl32.dll

0x7EB90000 - 0x7EBDA000  C:\windows\system32\advapi32.dll

0x7EBF0000 - 0x7EC7C000  C:\windows\system32\gdi32.dll

0x7ECA0000 - 0x7EDC8000  C:\windows\system32\user32.dll

0x7EDD0000 - 0x7EE64000  C:\windows\system32\winmm.dll





----------------------------------------

    Memory Dump

----------------------------------------



Code: 16 bytes starting at (EIP = 7D959C69)



7D959C69: 8B 00 8B 80  58 0F 00 00  89 44 24 08  8B 47 14 89  ....X....D$..G..





Stack: 1024 bytes starting at (ESP = 003AD280)



* = addr  **                                                  *               

003AD280: 03 00 00 00  78 0D 9A 7D  40 02 99 7D  00 00 00 00  ....x..}@..}....

003AD290: D0 DF 15 00  19 00 00 00  3B 9C 95 7D  F4 FF 99 7D  ........;..}...}

003AD2A0: F8 74 14 00  38 FC 15 00  88 D5 3A 00  BC A3 8A 7D  .t..8.....:....}

003AD2B0: B8 DF 15 00  30 85 99 7D  78 D5 3A 00  00 00 00 00  ....0..}x.:.....

003AD2C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD2D0: 10 00 00 00  F0 00 00 00  40 01 00 00  00 00 00 00  ........@.......

003AD2E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD2F0: B8 DF 15 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD300: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD310: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD320: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD330: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD340: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD350: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD360: 00 00 00 00  00 00 00 00  00 60 A6 95  F4 EF D6 7E  .........`.....~

003AD370: 60 00 00 00  40 00 00 00  98 D3 3A 00  4B A0 D2 7E  `...@.....:.K..~

003AD380: 00 00 00 00  60 00 00 00  D0 D3 3A 00  00 00 00 00  ....`.....:.....

003AD390: 19 A0 D2 7E  F4 FF 99 7D  B8 D4 3A 00  0D D1 8C 7D  ...~...}..:....}

003AD3A0: 00 00 00 00  60 00 00 00  D0 D3 3A 00  00 00 00 00  ....`.....:.....

003AD3B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD3C0: 00 00 00 00  00 00 00 00  D0 D3 3A 00  00 00 00 00  ..........:.....

003AD3D0: 57 00 69 00  6E 00 65 00  20 00 58 00  31 00 31 00  W.i.n.e. .X.1.1.

003AD3E0: 20 00 64 00  72 00 69 00  76 00 65 00  72 00 00 00   .d.r.i.v.e.r...

003AD3F0: 20 00 00 00  00 03 00 00  00 04 00 00  00 00 00 00   ...............

003AD400: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD410: 01 04 01 04  BC 00 00 00  00 00 7C 00  00 00 00 00  ..........|.....

003AD420: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD430: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD440: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD450: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD460: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD470: 00 00 00 00  00 00 00 00  10 00 00 00  40 01 00 00  ............@...

003AD480: F0 00 00 00  00 00 00 00  00 60 A6 95  F4 EF D6 7E  .........`.....~

003AD490: 08 00 00 00  00 00 00 00  B8 D4 3A 00  4B A0 D2 7E  ..........:.K..~

003AD4A0: 00 00 00 00  07 00 00 00  00 D5 3A 00  00 00 00 00  ..........:.....

003AD4B0: 19 A0 D2 7E  5B D7 95 7D  E8 D5 3A 00  81 E0 8C 7D  ...~[..}..:....}

003AD4C0: 20 00 00 00  07 00 00 00  00 D5 3A 00  00 00 00 00   .........:.....

003AD4D0: 00 00 00 00  60 00 00 00  00 D5 3A 00  00 00 00 00  ....`.....:.....

003AD4E0: 00 00 00 00  00 00 00 00  00 00 00 00  6E CC 8F 7D  ............n..}

003AD4F0: 00 D5 3A 00  07 00 00 00  08 00 00 00  00 00 00 00  ..:.............

003AD500: 57 00 69 00  6E 00 65 00  20 00 58 00  31 00 31 00  W.i.n.e. .X.1.1.

003AD510: 20 00 64 00  72 00 69 00  76 00 65 00  72 00 00 00   .d.r.i.v.e.r...

003AD520: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD530: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD540: 01 04 01 04  BC 00 00 00  00 00 7C 00  00 00 00 00  ..........|.....

003AD550: 00 00 00 00  19 00 00 00  38 75 14 00  00 00 00 00  ........8u......

003AD560: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD570: 00 00 00 00  00 00 00 00  B8 DF 15 00  F4 FF 99 7D  ...............}

003AD580: F8 74 14 00  F8 74 14 00  E8 D5 3A 00  1F E3 8B 7D  .t...t....:....}

003AD590: F8 74 14 00  00 00 00 00  01 00 00 00  00 00 00 00  .t..............

003AD5A0: 00 00 00 00  00 00 00 00  20 00 00 00  00 04 00 00  ........ .......

003AD5B0: 00 03 00 00  00 00 00 00  39 00 00 00  00 00 00 00  ........9.......

003AD5C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

003AD5D0: 00 00 00 00  00 00 00 00  FB E2 8B 7D  F4 FF 99 7D  ...........}...}

003AD5E0: F8 74 14 00  38 D6 3A 00  68 D6 3A 00  4D 7D 8C 7D  .t..8.:.h.:.M}.}

003AD5F0: F8 74 14 00  B8 DF 15 00  00 00 00 00  07 00 00 00  .t..............

003AD600: 38 D6 3A 00  CC 80 FD 7F  48 D6 3A 00  7B 1C 89 7B  8.:.....H.:.{..{

003AD610: A0 D3 D8 7E  00 00 00 00  00 EA 15 00  7C 0B 9A 7D  ...~........|..}

003AD620: 1D A1 97 7D  18 51 97 7D  40 00 00 00  80 07 8B 7D  ...}.Q.}@......}

003AD630: 28 EA 15 00  C8 D6 3A 00  00 04 00 00  00 03 00 00  (.....:.........

003AD640: 39 00 00 00  03 00 00 00  68 D6 3A 00  07 B5 9B 7D  9.......h.:....}

003AD650: E0 8C 97 7D  51 45 97 7D  B8 DF 15 00  F4 0F 9D 7D  ...}QE.}.......}

003AD660: 10 00 00 00  E0 FA 13 00  D8 D6 3A 00  BA C9 9B 7D  ..........:....}

003AD670: F8 74 14 00  8C D6 3A 00  C8 D6 3A 00  00 00 00 00  .t....:...:.....





------------------------------------------------------------------------------
```

---

### Post by Drezliok on 2009-11-10
What version of WINE are you using?

I am using the developmental version for now.

---

### Post by Dreygz on 2009-11-10
says version 1.0.1 -0ubuntu8 (wine) but at this point i just don't understand what's going on really... i changed the permissions it goes to the launcher but after that the critical error hits...

---

### Post by beastrace91 on 2009-11-10
Ahh that is the older "stable" Wine version. Upgrade to the latest 1.1.32 using the instructions detailed [here](http://www.winehq.org/download/deb). Then give it a go.

Regards,
~Jeff

---

### Post by Dreygz on 2009-11-10
thanks that did it for me...

---

### Post by rob2nd9th on 2009-11-10
Same as 1st post.

Im running 9.10 and wine 1.1.32

"Goto the folder and change it's permissions"

What folder? and what permissions, thanks

---

### Post by beastrace91 on 2009-11-10
I am pretty sure he is referring to your WoW folder located in **~/.wine/drive_c/Program\ Files** but I do not own WoW to confirm this - I know alot of people where saying their WoW directory had it's permissions changed somehow so no one could write to it. Rather odd issue but at least it is an easy fix.

~Jeff

---

### Post by mvandemar on 2009-11-10
> **beastrace91 said:**
> I am pretty sure he is referring to your WoW folder located in **~/.wine/drive_c/Program\ Files** but I do not own WoW to confirm this - I know alot of people where saying their WoW directory had it's permissions changed somehow so no one could write to it. Rather odd issue but at least it is an easy fix.

~Jeff

Well, it would be an easy fix, if indeed it was a fix. The issue is that now the WoW *launcher* is what is causing the issue. If you bypass the launcher (Launcher.exe) and run the game directly (WoW.exe) then yes, the game will play. However, the whole "check for updates" process is completely skipped at that point. 

It's a temporary workaround, not technically a fix. I just don't know if it's an issue on Blizzard's or Wine's end.

-Michael

---

### Post by rob2nd9th on 2009-11-11
I'm still getting this


[IMG]http://i138.photobucket.com/albums/q244/rob2nd9th/Screenshot-2.jpg[/IMG] 


tried the permisions on the main folder, No matter how I launch the game still get it downloading the patch ??

Im shore if it works for some one i must be missing something, I normally do......

---

### Post by Drezliok on 2009-11-11
If you can get the game to open you can turn the "show launcher" off and that stops the issue for now.

---

### Post by m0rbidpercepti0ns on 2009-11-11
Well...actually going into your Wine program folders to World of Warcraft and changing permissions,THEN clicking Change permissions for contained files,does fix the problem,then you navigate into WoWs folder,right click EITHER Launcher.exe,or Wow.Exe,and run in wine,both should work. So long as you do it this way. However..this problem doesnt make much sense,and this is only a work around. And the minor of problems with WoW on Linux.

---

### Post by Pikestaff on 2009-11-12
> **mvandemar said:**
> Well, it would be an easy fix, if indeed it was a fix. The issue is that now the WoW *launcher* is what is causing the issue. If you bypass the launcher (Launcher.exe) and run the game directly (WoW.exe) then yes, the game will play. However, the whole "check for updates" process is completely skipped at that point. 

It's a temporary workaround, not technically a fix. I just don't know if it's an issue on Blizzard's or Wine's end.

-Michael

It's on Blizzard's end, I know a lot of people on Windows who can now only run the launcher in Administrative mode :P

Best we can do is wait for a patch to fix it, I'd imagine, and keep doing the workaround in the meantime.  (Now I just have to get out of the habit of clicking on the launcher...)

---

