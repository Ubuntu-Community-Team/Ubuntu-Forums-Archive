---
title: "WoW Error plz help"
date: 2009-04-27
forum: Wine
---

### Post by JohanA on 2009-04-27
Hi, I am new to Ubuntu so dont know that much about it yet but have installed  WoW  and all WoW expansions and downloaded all paches but when I am trying to start it with wine this happend.

If anyone know how I can fix it it whould be great thanks.



==============================================================================
World of WarCraft (build 9806)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Apr 26, 2009  7:40:30.500 PM
User:     johan
Computer: johan
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:    C:\Program Files\World of Warcraft\Wow.exe
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0073:7D8F08C5

The instruction at "0x7D8F08C5" referenced memory at "0x00000024".
The memory could not be "read".


WoWBuild: 9806
Settings: 
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enGB"
SET movie "0"
SET showToolsUI "1"
SET portal "eu"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxRefresh "66"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "450.000000"
SET specular "1"
SET groundEffectDensity "24"
SET projectedTextures "1"
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=0013B5B4  EBX=7D991FF4  ECX=00145EA0  EDX=00145EA0  ESI=00000000
EDI=00000000  EBP=003AD5D0  ESP=003AD5A8  EIP=7D8F08C5  FLG=00010212
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 15/15 threads...

--- Thread ID: 4670 ---
7BC71945 0B94E968 0001:00060945 C:\windows\system32\ntdll.dll
7BC71C42 0B94E998 0001:00060C42 C:\windows\system32\ntdll.dll
7BC71C9C 0B94E9B8 0001:00060C9C C:\windows\system32\ntdll.dll
7BC773D5 0B94EA18 0001:000663D5 C:\windows\system32\ntdll.dll
7BC7337E 0B94EA28 0001:0006237E C:\windows\system32\ntdll.dll
7BC751B2 0B94EAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 0B94F3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 0B94F4B8 0000:00000000 <unknown>

--- Thread ID: 4669 ---
7BC71945 0830E624 0001:00060945 C:\windows\system32\ntdll.dll
7BC71C42 0830E654 0001:00060C42 C:\windows\system32\ntdll.dll
7B88F522 0830E794 0001:0006E522 C:\windows\system32\KERNEL32.dll
7D17937B 0830E7C4 0001:0002837B C:\windows\system32\winex11.drv
7ECFAE85 0830E974 0001:00079E85 C:\windows\system32\user32.dll
7ECFAEEF 0830E994 0001:00079EEF C:\windows\system32\user32.dll
004417F9 0830E9C4 0001:000407F9 C:\Program Files\World of Warcraft\Wow.exe
004427FA 0830E9D8 0001:000417FA C:\Program Files\World of Warcraft\Wow.exe
008D4D1F 0830EA10 0001:004D3D1F C:\Program Files\World of Warcraft\Wow.exe
008D4DC4 0830EA28 0001:004D3DC4 C:\Program Files\World of Warcraft\Wow.exe
7BC751B2 0830EAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 0830F3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 0830F4B8 0000:00000000 <unknown>

--- Thread ID: 4668 ---
7BC71945 0819E608 0001:00060945 C:\windows\system32\ntdll.dll
7BC71C42 0819E638 0001:00060C42 C:\windows\system32\ntdll.dll
7B88F522 0819E778 0001:0006E522 C:\windows\system32\KERNEL32.dll
7B88F67A 0819E798 0001:0006E67A C:\windows\system32\KERNEL32.dll
00462CFB 0819E9F0 0001:00061CFB C:\Program Files\World of Warcraft\Wow.exe
0046243E 0819E9FC 0001:0006143E C:\Program Files\World of Warcraft\Wow.exe
0053AF87 0819EA18 0001:00139F87 C:\Program Files\World of Warcraft\Wow.exe
7BC7337E 0819EA28 0001:0006237E C:\windows\system32\ntdll.dll
7BC751B2 0819EAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 0819F3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 0819F4B8 0000:00000000 <unknown>

--- Thread ID: 4667 ---
7BC71945 0802E838 0001:00060945 C:\windows\system32\ntdll.dll
7BC71C42 0802E868 0001:00060C42 C:\windows\system32\ntdll.dll
7B88F522 0802E9A8 0001:0006E522 C:\windows\system32\KERNEL32.dll
7B88F71C 0802E9C8 0001:0006E71C C:\windows\system32\KERNEL32.dll
0053F4F0 0802E9D8 0001:0013E4F0 C:\Program Files\World of Warcraft\Wow.exe
00462495 0802E9F0 0001:00061495 C:\Program Files\World of Warcraft\Wow.exe
00462601 0802E9FC 0001:00061601 C:\Program Files\World of Warcraft\Wow.exe
0053AF87 0802EA18 0001:00139F87 C:\Program Files\World of Warcraft\Wow.exe
7BC7337E 0802EA28 0001:0006237E C:\windows\system32\ntdll.dll
7BC751B2 0802EAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 0802F3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 0802F4B8 0000:00000000 <unknown>

--- Thread ID: 4666 ---
7BC71945 07EBE850 0001:00060945 C:\windows\system32\ntdll.dll
7BC71C42 07EBE880 0001:00060C42 C:\windows\system32\ntdll.dll
7B88F522 07EBE9C0 0001:0006E522 C:\windows\system32\KERNEL32.dll
7B88F71C 07EBE9E0 0001:0006E71C C:\windows\system32\KERNEL32.dll
0053F4F0 07EBE9F0 0001:0013E4F0 C:\Program Files\World of Warcraft\Wow.exe
007A8D0B 07EBEA18 0001:003A7D0B C:\Program Files\World of Warcraft\Wow.exe
7BC7337E 07EBEA28 0001:0006237E C:\windows\system32\ntdll.dll
7BC751B2 07EBEAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 07EBF3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 07EBF4B8 0000:00000000 <unknown>

--- Thread ID: 4665 ---
7B88F832 07D4E9D8 0001:0006E832 C:\windows\system32\KERNEL32.dll
7B88F875 07D4E9F8 0001:0006E875 C:\windows\system32\KERNEL32.dll
0085093D 07D4EA04 0001:0044F93D C:\Program Files\World of Warcraft\Wow.exe
0085116C 07D4EA18 0001:0045016C C:\Program Files\World of Warcraft\Wow.exe
7BC7337E 07D4EA28 0001:0006237E C:\windows\system32\ntdll.dll
7BC751B2 07D4EAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 07D4F3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 07D4F4B8 0000:00000000 <unknown>

--- Thread ID: 4664 ---
7B88F832 069CE9D8 0001:0006E832 C:\windows\system32\KERNEL32.dll
7B88F875 069CE9F8 0001:0006E875 C:\windows\system32\KERNEL32.dll
0085093D 069CEA04 0001:0044F93D C:\Program Files\World of Warcraft\Wow.exe
0085116C 069CEA18 0001:0045016C C:\Program Files\World of Warcraft\Wow.exe
7BC7337E 069CEA28 0001:0006237E C:\windows\system32\ntdll.dll
7BC751B2 069CEAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 069CF3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 069CF4B8 0000:00000000 <unknown>

--- Thread ID: 4663 ---
7D0DF2CB 0609E9C8 0001:0000E2CB C:\windows\system32\winealsa.drv
7D0F1BFC 0609EA18 0001:00020BFC C:\windows\system32\winealsa.drv
7BC7337E 0609EA28 0001:0006237E C:\windows\system32\ntdll.dll
7BC751B2 0609EAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 0609F3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 0609F4B8 0000:00000000 <unknown>

--- Thread ID: 4662 ---
7B88F832 0685E9D8 0001:0006E832 C:\windows\system32\KERNEL32.dll
7B88F875 0685E9F8 0001:0006E875 C:\windows\system32\KERNEL32.dll
0085093D 0685EA04 0001:0044F93D C:\Program Files\World of Warcraft\Wow.exe
0085116C 0685EA18 0001:0045016C C:\Program Files\World of Warcraft\Wow.exe
7BC7337E 0685EA28 0001:0006237E C:\windows\system32\ntdll.dll
7BC751B2 0685EAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 0685F3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 0685F4B8 0000:00000000 <unknown>

--- Thread ID: 4661 ---
7B88F832 066EE9D8 0001:0006E832 C:\windows\system32\KERNEL32.dll
7B88F875 066EE9F8 0001:0006E875 C:\windows\system32\KERNEL32.dll
0085093D 066EEA04 0001:0044F93D C:\Program Files\World of Warcraft\Wow.exe
0085116C 066EEA18 0001:0045016C C:\Program Files\World of Warcraft\Wow.exe
7BC7337E 066EEA28 0001:0006237E C:\windows\system32\ntdll.dll
7BC751B2 066EEAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 066EF3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 066EF4B8 0000:00000000 <unknown>

--- Thread ID: 4659 ---
7EDEAE07 0640EA18 0001:00029E07 C:\windows\system32\winmm.dll
7BC7337E 0640EA28 0001:0006237E C:\windows\system32\ntdll.dll
7BC751B2 0640EAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 0640F3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 0640F4B8 0000:00000000 <unknown>

--- Thread ID: 4657 ---
7BC71945 040DE844 0001:00060945 C:\windows\system32\ntdll.dll
7BC71C42 040DE874 0001:00060C42 C:\windows\system32\ntdll.dll
7B88F522 040DE9B4 0001:0006E522 C:\windows\system32\KERNEL32.dll
7B88F71C 040DE9D4 0001:0006E71C C:\windows\system32\KERNEL32.dll
0053F4F0 040DE9E4 0001:0013E4F0 C:\Program Files\World of Warcraft\Wow.exe
00478102 040DE9FC 0001:00077102 C:\Program Files\World of Warcraft\Wow.exe
0053AF87 040DEA18 0001:00139F87 C:\Program Files\World of Warcraft\Wow.exe
7BC7337E 040DEA28 0001:0006237E C:\windows\system32\ntdll.dll
7BC751B2 040DEAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 040DF3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 040DF4B8 0000:00000000 <unknown>

--- Thread ID: 4656 ---
7B88F832 03A0E5B0 0001:0006E832 C:\windows\system32\KERNEL32.dll
7B88F875 03A0E5D0 0001:0006E875 C:\windows\system32\KERNEL32.dll
0046EC9D 03A0E5DC 0001:0006DC9D C:\Program Files\World of Warcraft\Wow.exe
007D5E45 03A0E9FC 0001:003D4E45 C:\Program Files\World of Warcraft\Wow.exe
0053AF87 03A0EA18 0001:00139F87 C:\Program Files\World of Warcraft\Wow.exe
7BC7337E 03A0EA28 0001:0006237E C:\windows\system32\ntdll.dll
7BC751B2 03A0EAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 03A0F3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 03A0F4B8 0000:00000000 <unknown>

--- Thread ID: 4655 ---
7B88F832 01CCE990 0001:0006E832 C:\windows\system32\KERNEL32.dll
7B88F875 01CCE9B0 0001:0006E875 C:\windows\system32\KERNEL32.dll
00424754 01CCE9D8 0001:00023754 C:\Program Files\World of Warcraft\Wow.exe
008D4D1F 01CCEA10 0001:004D3D1F C:\Program Files\World of Warcraft\Wow.exe
008D4DC4 01CCEA28 0001:004D3DC4 C:\Program Files\World of Warcraft\Wow.exe
7BC751B2 01CCEAC8 0001:000641B2 C:\windows\system32\ntdll.dll
7BC75380 01CCF3B8 0001:00064380 C:\windows\system32\ntdll.dll
B7F394FF 01CCF4B8 0000:00000000 <unknown>

--- Thread ID: 8217 [Current Thread] ---
7D8F08C5 003AD5D0 0001:0006F8C5 C:\windows\system32\wined3d.dll
7D8BE3D0 003AD620 0001:0003D3D0 C:\windows\system32\wined3d.dll
7D8C9CAD 003AD6A0 0001:00048CAD C:\windows\system32\wined3d.dll
7D9AF3E2 003AD710 0001:0000E3E2 C:\windows\system32\d3d9.dll
0062903C 003AD76C 0001:0022803C C:\Program Files\World of Warcraft\Wow.exe
006273CF 003AD7DC 0001:002263CF C:\Program Files\World of Warcraft\Wow.exe
7ED3514A 003AD80C 0001:000B414A C:\windows\system32\user32.dll
7ED3559A 003AD84C 0001:000B459A C:\windows\system32\user32.dll
7ED383C5 003ADD1C 0001:000B73C5 C:\windows\system32\user32.dll
7ED3A95E 003ADD5C 0001:000B995E C:\windows\system32\user32.dll
7ECF9A31 003ADDBC 0001:00078A31 C:\windows\system32\user32.dll
7ECFECD5 003ADE1C 0001:0007DCD5 C:\windows\system32\user32.dll
7ECFF1EC 003ADE5C 0001:0007E1EC C:\windows\system32\user32.dll
7ECC023A 003ADF2C 0001:0003F23A C:\windows\system32\user32.dll
7ECC1011 003ADF7C 0001:00040011 C:\windows\system32\user32.dll
0046E377 003ADFB0 0001:0006D377 C:\Program Files\World of Warcraft\Wow.exe
006274E0 003AE024 0001:002264E0 C:\Program Files\World of Warcraft\Wow.exe
7ED3514A 003AE054 0001:000B414A C:\windows\system32\user32.dll
7ED3559A 003AE094 0001:000B459A C:\windows\system32\user32.dll
7ED383C5 003AE564 0001:000B73C5 C:\windows\system32\user32.dll
7ED3A95E 003AE5A4 0001:000B995E C:\windows\system32\user32.dll
7ECF9A31 003AE604 0001:00078A31 C:\windows\system32\user32.dll
7ECFECD5 003AE664 0001:0007DCD5 C:\windows\system32\user32.dll
7ECFF1EC 003AE6A4 0001:0007E1EC C:\windows\system32\user32.dll
7ED2FE6B 003AE7F4 0001:000AEE6B C:\windows\system32\user32.dll
7ED30CC8 003AE864 0001:000AFCC8 C:\windows\system32\user32.dll
7D8BDA69 003AE8A4 0001:0003CA69 C:\windows\system32\wined3d.dll
7D8CA554 003AE924 0001:00049554 C:\windows\system32\wined3d.dll
7D9AF3E2 003AE994 0001:0000E3E2 C:\windows\system32\d3d9.dll
0062903C 003AE9F0 0001:0022803C C:\Program Files\World of Warcraft\Wow.exe
006273CF 003AEA60 0001:002263CF C:\Program Files\World of Warcraft\Wow.exe
7ED3514A 003AEA90 0001:000B414A C:\windows\system32\user32.dll
7ED3559A 003AEAD0 0001:000B459A C:\windows\system32\user32.dll
7ED383C5 003AEFA0 0001:000B73C5 C:\windows\system32\user32.dll
7ED3A95E 003AEFE0 0001:000B995E C:\windows\system32\user32.dll
7ECF9A31 003AF040 0001:00078A31 C:\windows\system32\user32.dll
7ECFECD5 003AF0A0 0001:0007DCD5 C:\windows\system32\user32.dll
7ECFF1EC 003AF0E0 0001:0007E1EC C:\windows\system32\user32.dll
7ECC023A 003AF1B0 0001:0003F23A C:\windows\system32\user32.dll
7ECC1011 003AF200 0001:00040011 C:\windows\system32\user32.dll
0046E377 003AF234 0001:0006D377 C:\Program Files\World of Warcraft\Wow.exe
006274E0 003AF2A8 0001:002264E0 C:\Program Files\World of Warcraft\Wow.exe
7ED3514A 003AF2D8 0001:000B414A C:\windows\system32\user32.dll
7ED3559A 003AF318 0001:000B459A C:\windows\system32\user32.dll
7ED383C5 003AF7E8 0001:000B73C5 C:\windows\system32\user32.dll
7ED3A95E 003AF828 0001:000B995E C:\windows\system32\user32.dll
7ECF9A31 003AF888 0001:00078A31 C:\windows\system32\user32.dll
7ECFECD5 003AF8E8 0001:0007DCD5 C:\windows\system32\user32.dll
7ECFF1EC 003AF928 0001:0007E1EC C:\windows\system32\user32.dll
7ED2FE6B 003AFA78 0001:000AEE6B C:\windows\system32\user32.dll
7ED30CC8 003AFAE8 0001:000AFCC8 C:\windows\system32\user32.dll
7D177724 003AFB68 0001:00026724 C:\windows\system32\winex11.drv
7D178E6B 003AFC98 0001:00027E6B C:\windows\system32\winex11.drv
7D179315 003AFCC8 0001:00028315 C:\windows\system32\winex11.drv
7ECFDFC8 003AFD18 0001:0007CFC8 C:\windows\system32\user32.dll
7ECFE0EB 003AFD48 0001:0007D0EB C:\windows\system32\user32.dll
0046D9FF 003AFD9C 0001:0006C9FF C:\Program Files\World of Warcraft\Wow.exe
00830646 003AFDD4 0001:0042F646 C:\Program Files\World of Warcraft\Wow.exe
0082F2E2 003AFE54 0001:0042E2E2 C:\Program Files\World of Warcraft\Wow.exe
0082F491 003AFE6C 0001:0042E491 C:\Program Files\World of Warcraft\Wow.exe
00406C4D 003AFF08 0001:00005C4D C:\Program Files\World of Warcraft\Wow.exe
7B877D80 003AFFE8 0001:00056D80 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 15/15 threads...

--- Thread ID: 4670 ---
7BC71945 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0B94E9C0,0x00000004,0x0B94EA00)
7BC71C42 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0B94E9C0,0x00000000,0x00000000)
7BC71C9C ntdll.dll    NtWaitForSingleObject+60 (0x000021D4,0x00000000,0x0B94EA00,0x7BC90AD7)
7BC773D5 ntdll.dll    <unknown symbol>+0 (0x00000000,0x7BC77290,0x0B94EAC8,0x7BC751B2)
7BC7337E ntdll.dll    call_thread_entry_point+14 (0x7BC77290,0x00000000,0x7BCB0880,0xB7F3E131)
7BC751B2 ntdll.dll    <unknown symbol>+0 (0x0B94EAFC,0x00000000,0x00000000,0x00000000)
7BC75380 ntdll.dll    <unknown symbol>+0 (0x7FF9CFB8,0x0B94FB90,0x0B94FB90,0x0B94FB90)
B7F394FF              start_thread+191 (0x0B94FB90,0x00000000,0x00000000,0x00000000)
B7EB349E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 4669 ---
7BC71945 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000003,0x0830E67C,0x00000004,0x00000000)
7BC71C42 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000003,0x0830E67C,0x00000000,0x00000000)
7B88F522 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000003,0x0830E7F4,0x00000000,0xFFFFFFFF)
7D17937B winex11.drv  X11DRV_MsgWaitForMultipleObjectsEx+187 (0x00000003,0x0830E7F4,0xFFFFFFFF,0x00000000)
7ECFAE85 user32.dll   MsgWaitForMultipleObjectsEx+229 (0x00000002,0x0830E9BC,0xFFFFFFFF,0x00000000)
7ECFAEEF user32.dll   MsgWaitForMultipleObjects+63 (0x00000002,0x0830E9BC,0x00000000,0xFFFFFFFF)
004417F9 Wow.exe      <unknown symbol>+0 (0x010631D0,0x008D4D45,0x07BAF430,0x0830EA10)
004427FA Wow.exe      <unknown symbol>+0 (0x07BAF3D0,0x82A753BA,0x008D4D45,0x07BAF430)
008D4D1F Wow.exe      <unknown symbol>+0 (0x07BAF430,0x7BC7337E,0x07BAF430,0x008D4D45)
008D4DC4 Wow.exe      <unknown symbol>+0 (0x008D4D45,0x07BAF430,0x7BCB0880,0xB7F3E131)
7BC751B2 ntdll.dll    <unknown symbol>+0 (0x0830EAFC,0x00000000,0x00000000,0x00000000)
7BC75380 ntdll.dll    <unknown symbol>+0 (0x7FFA0FB8,0x0830FB90,0x0830FB90,0x0830FB90)
B7F394FF              start_thread+191 (0x0830FB90,0x00000000,0x00000000,0x00000000)
B7EB349E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 4668 ---
7BC71945 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0819E660,0x00000004,0x0819E760)
7BC71C42 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0819E660,0x00000000,0x00000000)
7B88F522 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x0819E8BC,0x00000000,0x000001F4)
7B88F67A KERNEL32.dll WaitForMultipleObjects+58 (0x00000001,0x0819E8BC,0x00000000,0x000001F4)
00462CFB Wow.exe      <unknown symbol>+0 (0x00462430,0x0819EA18,0x0053AF87,0x0780EBC8)
0046243E Wow.exe      <unknown symbol>+0 (0x0780EBC8,0x0053AF30,0x07692370,0x7BC94FF4)
0053AF87 Wow.exe      <unknown symbol>+0 (0x000021B0,0x0053AF30,0x0819EAC8,0x7BC751B2)
7BC7337E ntdll.dll    call_thread_entry_point+14 (0x0053AF30,0x07692370,0x7BCB0880,0xB7F3E131)
7BC751B2 ntdll.dll    <unknown symbol>+0 (0x0819EAFC,0x00000000,0x00000000,0x00000000)
7BC75380 ntdll.dll    <unknown symbol>+0 (0x7FFA4FB8,0x0819FB90,0x0819FB90,0x0819FB90)
B7F394FF              start_thread+191 (0x0819FB90,0x00000000,0x00000000,0x00000000)
B7EB349E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 4667 ---
7BC71945 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x0802E890,0x00000004,0x0802E990)
7BC71C42 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x0802E890,0x00000000,0x00000000)
7B88F522 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x0802E9D0,0x00000000,0x000003E8)
7B88F71C KERNEL32.dll WaitForSingleObject+60 (0x00002120,0x000003E8,0x0802E9F0,0x00462495)
0053F4F0 Wow.exe      <unknown symbol>+0 (0x000003E8,0x0000123B,0x004625F0,0x0780EBD8)
00462495 Wow.exe      <unknown symbol>+0 (0x00000000,0x0802EA18,0x0053AF87,0x0780EBD8)
00462601 Wow.exe      <unknown symbol>+0 (0x0780EBD8,0x0053AF30,0x07756220,0x7BC94FF4)
0053AF87 Wow.exe      <unknown symbol>+0 (0x000021AC,0x0053AF30,0x0802EAC8,0x7BC751B2)
7BC7337E ntdll.dll    call_thread_entry_point+14 (0x0053AF30,0x07756220,0x7BCB0880,0xB7F3E131)
7BC751B2 ntdll.dll    <unknown symbol>+0 (0x0802EAFC,0x00000000,0x00000000,0x00000000)
7BC75380 ntdll.dll    <unknown symbol>+0 (0x7FFA8FB8,0x0802FB90,0x0802FB90,0x0802FB90)
B7F394FF              start_thread+191 (0x0802FB90,0x00000000,0x00000000,0x00000000)
B7EB349E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 4666 ---
7BC71945 ntdll.dll    NTDLL_wait_for_multiple_objects+629 (0x00000001,0x07EBE8A8,0x00000004,0x00000000)
7BC71C42 ntdll.dll    NtWaitForMultipleObjects+98 (0x00000001,0x07EBE8A8,0x00000000,0x00000000)
7B88F522 KERNEL32.dll WaitForMultipleObjectsEx+258 (0x00000001,0x07EBE9E8,0x00000000,0xFFFFFFFF)
7B88F71C KERNEL32.dll WaitForSingleObject+60 (0x00002078,0xFFFFFFFF,0x07EBEA18,0x007A8D0B)
0053F4F0 Wow.exe      <unknown symbol>+0 (0xFFFFFFFF,0x00000000,0x0053AF87,0x00000000)
007A8D0B Wow.exe      <unknown symbol>+0 (0x00002118,0x0053AF30,0x07EBEAC8,0x7BC751B2)
7BC7337E ntdll.dll    call_thread_entry_point+14 (0x0053AF30,0x07756220,0x7BCB0880,0xB7F3E131)
7BC751B2 ntdll.dll    <unknown symbol>+0 (0x07EBEAFC,0x00000000,0x00000000,0x00000000)
7BC75380 ntdll.dll    <unknown symbol>+0 (0x7FFACFB8,0x07EBFB90,0x07EBFB90,0x07EBFB90)
B7F394FF              start_thread+191 (0x07EBFB90,0x00000000,0x00000000,0x00000000)
B7EB349E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 4665 ---
7B88F832 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x07D4EA04,0x0083E3CA)
7B88F875 KERNEL32.dll Sleep+37 (0x0000000A,0x07D4EA18,0x0085116C,0x0000000A)
0085093D Wow.exe      <unknown symbol>+0 (0x0000000A,0x04DA6EC8,0x00001239,0x07D4EA28)
0085116C Wow.exe      <unknown symbol>+0 (0x04DA6EC8,0x008510F0,0x07D4EAC8,0x7BC751B2)
7BC7337E ntdll.dll    call_thread_entry_point+14 (0x008510F0,0x04DA6EC8,0x7BCB0880,0xB7F3E131)
7BC751B2 ntdll.dll    <unknown symbol>+0 (0x07D4EAFC,0x00000000,0x00000000,0x00000000)
7BC75380 ntdll.dll    <unknown symbol>+0 (0x7FFB0FB8,0x07D4FB90,0x07D4FB90,0x07D4FB90)
B7F394FF              start_thread+191 (0x07D4FB90,0x00000000,0x00000000,0x00000000)
B7EB349E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 4664 ---
7B88F832 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x00000000,0x00000012)
7B88F875 KERNEL32.dll Sleep+37 (0x0000000A,0x069CEA18,0x0085116C,0x0000000A)
0085093D Wow.exe      <unknown symbol>+0 (0x0000000A,0x04B8E8C8,0x00001238,0x069CEA28)
0085116C Wow.exe      <unknown symbol>+0 (0x04B8E8C8,0x008510F0,0x069CEAC8,0x7BC751B2)
7BC7337E ntdll.dll    call_thread_entry_point+14 (0x008510F0,0x04B8E8C8,0x7BCB0880,0xB7F3E131)
7BC751B2 ntdll.dll    <unknown symbol>+0 (0x069CEAFC,0x00000000,0x00000000,0x00000000)
7BC75380 ntdll.dll    <unknown symbol>+0 (0x7FFB4FB8,0x069CFB90,0x069CFB90,0x069CFB90)
B7F394FF              start_thread+191 (0x069CFB90,0x00000000,0x00000000,0x00000000)
B7EB349E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 4663 ---
7D0DF2CB winealsa.drv ALSA_WaitRingMessage+59 (0x00128548,0x00000009,0x00000000,0x00000000)
7D0F1BFC winealsa.drv <unknown symbol>+0 (0x00000000,0x7D0F1B60,0x0609EAC8,0x7BC751B2)
7BC7337E ntdll.dll    call_thread_entry_point+14 (0x7D0F1B60,0x00000000,0x7BCB0880,0xB7F3E131)
7BC751B2 ntdll.dll    <unknown symbol>+0 (0x0609EAFC,0x00000000,0x00000000,0x00000000)
7BC75380 ntdll.dll    <unknown symbol>+0 (0x7FFC8FB8,0x0609FB90,0x0609FB90,0x0609FB90)
B7F394FF              start_thread+191 (0x0609FB90,0x00000000,0x00000000,0x00000000)
B7EB349E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 4662 ---
7B88F832 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x0685EA04,0x0083E3CA)
7B88F875 KERNEL32.dll Sleep+37 (0x0000000A,0x0685EA18,0x0085116C,0x0000000A)
0085093D Wow.exe      <unknown symbol>+0 (0x0000000A,0x04DAF548,0x00001236,0x0685EA28)
0085116C Wow.exe      <unknown symbol>+0 (0x04DAF548,0x008510F0,0x0685EAC8,0x7BC751B2)
7BC7337E ntdll.dll    call_thread_entry_point+14 (0x008510F0,0x04DAF548,0x7BCB0880,0xB7F3E131)
7BC751B2 ntdll.dll    <unknown symbol>+0 (0x0685EAFC,0x00000000,0x00000000,0x00000000)
7BC75380 ntdll.dll    <unknown symbol>+0 (0x7FFB8FB8,0x0685FB90,0x0685FB90,0x0685FB90)
B7F394FF              start_thread+191 (0x0685FB90,0x00000000,0x00000000,0x00000000)
B7EB349E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 4661 ---
7B88F832 KERNEL32.dll SleepEx+50 (0x0000000A,0x00000000,0x00000000,0x00000005)
7B88F875 KERNEL32.dll Sleep+37 (0x0000000A,0x066EEA18,0x0085116C,0x0000000A)
0085093D Wow.exe      <unknown symbol>+0 (0x0000000A,0x04B07D70,0x00001235,0x066EEA28)
0085116C Wow.exe      <unknown symbol>+0 (0x04B07D70,0x008510F0,0x066EEAC8,0x7BC751B2)
7BC7337E ntdll.dll    call_thread_entry_point+14 (0x008510F0,0x04B07D70,0x7BCB0880,0xB7F3E131)
7BC751B2 ntdll.dll    <unknown symbol>+0 (0x066EEAFC,0x00000000,0x00000000,0x00000000)
7BC75380 ntdll.dll    <unknown symbol>+0 (0x7FFBCFB8,0x066EFB90,0x066EFB90,0x066EFB90)
B7F394FF              start_thread+191 (0x066EFB90,0x00000000,0x00000000,0x00000000)
B7EB349E              __clone+94 (0x00000000,0x00000000,0x00000000,0x00000000)

--- Thread ID: 4659 ---
7EDEAE07 winmm.dll    <unknown symbol>+0 (0x00000000,0x7EDEABD0,0x0640EAC8,0x7BC751B2)
7BC7337E ntdll.dll    call_thread_entry_point+14 (0x7EDEABD0,0x00000000,0x7BCB0880,0xB7F3E131)
7BC751B2 ntdll.dll    <unknown symbol>+0 (0x0640EAFC,0x00000000,0x00000000,0x00000000)
7BC75380 ntdll.dll    <unknown symbol>+0

---

### Post by Clopin on 2009-04-27
I've never had these kinds of errors for a long time, they usually disappeared after a reboot, so I'm no expert at this.

Therefore the only suggestion I can give you, is to run the Blizzard Repair tool, and let it reset & check all your files.

On the other hand, before doing so, you could try to add:
SET gxApi "OpenGL"
in your config.wtf, which is inside our WTF folder.

---

### Post by skkeeper on 2009-04-27
World of Warcraft only runs on OpenGL on Linux as far as i know, another trick to run it on this mode is to do in the terminal 
wine wow.exe -opengl
Off course you need to be in the wow main directory.

---

### Post by freyder on 2009-04-27
I use:

padsp wine WoW.exe -opengl

---

### Post by JohanA on 2009-04-27
[skkeeper]("http://ubuntuforums.org/member.php?u=374589")
                               
                                               **Re: WoW Error plz help**             
                                                                World of Warcraft only runs on OpenGL on Linux as far as i know, another trick to run it on this mode is to do in the terminal 
wine wow.exe -opengl
Off course you need to be in the wow main director



Thanks man you and [Clopin]("http://ubuntuforums.org/member.php?u=763414") helped allot, wow runs perfect now :P  Have a nice day and again thanks, keep up the good work \\:D/

---

### Post by Guestttt on 2009-04-29
I have this problem when trying to download a patch it says my computer seems to be behind a firewall but my firewall is turned off if you have any suggestions please let me know.

---

