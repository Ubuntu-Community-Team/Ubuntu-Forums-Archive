---
title: "Homeworld2 in Wine 1.1.22"
date: 2009-06-14
forum: Wine
---

### Post by MechWarrior001 on 2009-06-14
Terminal gives me this when I try to run HW2:
```
fixme:win:EnumDisplayDevicesW ((null),0,0x33f150,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eb50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ebe0,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEn  umerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEn  umerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x163c08,0x164150): stub
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
err:wgl:X11DRV_wglShareLists Could not share display lists, context already created !
```

Here is debug:

```
Homeworld2.exe caused a Breakpoint in module Debug.dll at 0073:003f19b6.
Error occurred at 6/13/2009 21:44:04.
Homeworld2.exe, run by philip.
Microsoft Windows XP?.
1 processor(s), type 586.
376 MBytes physical memory.

MiniDump saved to file 'C:\Program Files\Sierra\Homeworld2\Bin\Release\6-13-2009_21_44_04_MiniDump.dmp'

Registers:
EAX=00000000 CS=0073 EIP=003f19b6 EFLGS=00200202
EBX=00000000 SS=007b ESP=0033f274 EBP=0033fd2c
ECX=00384444 DS=007b ESI=00000007 FS=0033
EDX=01036254 ES=007b EDI=000003ee GS=003b
Bytes at CS:EIP:
cc 83 4d fc ff 8d 8d 5c fe ff ff e8 9b fc ff ff 

Call Stack:





Stack dump:
0033f274: 007619a0 02fa1a88 0033fd78 62616e75 7420656c 7263206f 65746165 75627020
0033f294: 72656666 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0033f2b4: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0033f2d4: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0033f2f4: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0033f314: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0033f334: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0033f354: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0033f374: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0033f394: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0033f3b4: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0033f3d4: 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0033f3f4: 00000000 00000000

Module list: names, addresses, sizes, time stamps and file times:
C:\Program Files\Sierra\Homeworld2\Bin\Release\Platform.dll, loaded at 0x00340000 - 98304 bytes - 3f3c346d - file date is 8/14/2003 18:16:30
C:\Program Files\Sierra\Homeworld2\Bin\Release\Memory.dll, loaded at 0x00360000 - 33280 bytes - 3f3c341b - file date is 8/14/2003 18:15:08
C:\Program Files\Sierra\Homeworld2\Bin\Release\MSVCR70.dll, loaded at 0x00370000 - 344064 bytes - 3c36e574 - file date is 8/14/2003 18:08:58
C:\Program Files\Sierra\Homeworld2\Bin\Release\Localizer.dll, loaded at 0x003d0000 - 94208 bytes - 3f3c3468 - file date is 8/14/2003 18:16:26
C:\Program Files\Sierra\Homeworld2\Bin\Release\Debug.dll, loaded at 0x003f0000 - 10752 bytes - 3f3c3417 - file date is 8/14/2003 18:15:04
C:\Program Files\Sierra\Homeworld2\Bin\Release\Homeworld2.exe, loaded at 0x00400000 - 5333031 bytes - 37373778 - file date is 6/4/2007 22:04:08
C:\Program Files\Sierra\Homeworld2\Bin\Release\FileIO.dll, loaded at 0x00940000 - 155648 bytes - 3f3c3461 - file date is 8/14/2003 18:16:18
C:\Program Files\Sierra\Homeworld2\Bin\Release\ZLib.dll, loaded at 0x00970000 - 49152 bytes - 3f3c344d - file date is 8/14/2003 18:16:00
C:\Program Files\Sierra\Homeworld2\Bin\Release\objects.dll, loaded at 0x00980000 - 1093632 bytes - 3f3c358d - file date is 8/14/2003 18:21:20
C:\Program Files\Sierra\Homeworld2\Bin\Release\lua.dll, loaded at 0x00b30000 - 73728 bytes - 3f3c3472 - file date is 8/14/2003 18:16:36
C:\Program Files\Sierra\Homeworld2\Bin\Release\LuaConfig.dll, loaded at 0x00b50000 - 53248 bytes - 3f3c3476 - file date is 8/14/2003 18:16:40
C:\Program Files\Sierra\Homeworld2\Bin\Release\Util.dll, loaded at 0x00b60000 - 36864 bytes - 3f3c3489 - file date is 8/14/2003 18:16:58
C:\Program Files\Sierra\Homeworld2\Bin\Release\hw2box.dll, loaded at 0x00b70000 -  9728 bytes - 3f3c3486 - file date is 8/14/2003 18:16:56
C:\Program Files\Sierra\Homeworld2\Bin\Release\divxmedialib.dll, loaded at 0x00b80000 - 86016 bytes - 3f3bc007 - file date is 8/14/2003 18:08:56
C:\Program Files\Sierra\Homeworld2\Bin\Release\DivxDecoder.dll, loaded at 0x00ba0000 - 397312 bytes - 3f3bc002 - file date is 8/14/2003 18:08:56
C:\Program Files\Sierra\Homeworld2\Bin\Release\FileParser.dll, loaded at 0x00c10000 - 86016 bytes - 3f3bc005 - file date is 8/14/2003 18:08:56
C:\Program Files\Sierra\Homeworld2\Bin\Release\gslobby.dll, loaded at 0x00c30000 - 135168 bytes - 3f3c3510 - file date is 8/14/2003 18:19:14
C:\Program Files\Sierra\Homeworld2\Bin\Release\seFDAudio.dll, loaded at 0x00fd0000 - 40960 bytes - 3f3c34d7 - file date is 8/14/2003 18:18:16
C:\Program Files\Sierra\Homeworld2\Bin\Release\GL.dll, loaded at 0x028a0000 - 294912 bytes - 3f3c35a0 - file date is 8/14/2003 18:21:38
C:\Program Files\Sierra\Homeworld2\Bin\Release\console.dll, loaded at 0x10000000 -  5632 bytes - 3f3c3514 - file date is 8/14/2003 18:19:18
C:\windows\system32\KERNEL32.dll   , loaded at 0x7b820000 - 525172 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\ntdll.dll      , loaded at 0x7bc10000 -  2468 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\winedos.dll    , loaded at 0x7bfa0000 -     0 bytes - 00000000
C:\windows\system32\dbghelp.dll    , loaded at 0x7c010000 -  1032 bytes - 00000000 - file date is 6/5/2009 16:04:38
C:\windows\system32\opengl32.dll   , loaded at 0x7cb50000 -  2472 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\quartz.dll     , loaded at 0x7cbd0000 -  2496 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\psapi.dll      , loaded at 0x7cc70000 -  1032 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\msvfw32.dll    , loaded at 0x7ced0000 -     0 bytes - 00000000
C:\windows\system32\avicap32.dll   , loaded at 0x7cf00000 -     0 bytes - 00000000
C:\windows\system32\devenum.dll    , loaded at 0x7cf10000 -     0 bytes - 00000000
C:\windows\system32\wined3d.dll    , loaded at 0x7dd70000 -     0 bytes - 00000000
C:\windows\system32\dsound.dll     , loaded at 0x7df10000 -  2512 bytes - 00000000 - file date is 6/5/2009 16:04:38
C:\windows\system32\ddraw.dll      , loaded at 0x7dfa0000 -  2504 bytes - 00000000 - file date is 6/5/2009 16:04:38
C:\windows\system32\dxdiagn.dll    , loaded at 0x7dff0000 -  2460 bytes - 00000000 - file date is 6/5/2009 16:04:38
C:\windows\system32\uxtheme.dll    , loaded at 0x7e070000 -     0 bytes - 00000000
C:\windows\system32\midimap.dll    , loaded at 0x7e0a0000 -     0 bytes - 00000000
C:\windows\system32\msacm32.dll    , loaded at 0x7e0b0000 -     0 bytes - 00000000
C:\windows\system32\msacm32.drv    , loaded at 0x7e0d0000 -     0 bytes - 00000000
C:\windows\system32\winealsa.drv   , loaded at 0x7e1c0000 -     0 bytes - 00000000
C:\windows\system32\imm32.dll      , loaded at 0x7e220000 -     0 bytes - 00000000
C:\windows\system32\winex11.drv    , loaded at 0x7e3a0000 -     0 bytes - 00000000
C:\windows\system32\lz32.dll       , loaded at 0x7e570000 -     0 bytes - 00000000
C:\windows\system32\version.dll    , loaded at 0x7e580000 -  2484 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\imagehlp.dll   , loaded at 0x7e5a0000 -  1032 bytes - 00000000 - file date is 6/5/2009 16:04:38
C:\windows\system32\iphlpapi.dll   , loaded at 0x7e5e0000 -     0 bytes - 00000000
C:\windows\system32\ws2_32.dll     , loaded at 0x7e600000 -  2444 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\wsock32.dll    , loaded at 0x7e620000 -  2444 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\comctl32.dll   , loaded at 0x7e640000 - 64912 bytes - 00000000 - file date is 6/5/2009 16:04:38
C:\windows\system32\shell32.dll    , loaded at 0x7e710000 - 971284 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\shlwapi.dll    , loaded at 0x7e8a0000 - 14500 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\mpr.dll        , loaded at 0x7e8f0000 -     0 bytes - 00000000
C:\windows\system32\wininet.dll    , loaded at 0x7e920000 - 21684 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\oleaut32.dll   , loaded at 0x7e980000 -  5100 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\rpcrt4.dll     , loaded at 0x7ea50000 -  2472 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\ole32.dll      , loaded at 0x7ead0000 -  4232 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\advapi32.dll   , loaded at 0x7ebc0000 -  2488 bytes - 00000000 - file date is 6/5/2009 16:04:38
C:\windows\system32\gdi32.dll      , loaded at 0x7ec10000 -  2432 bytes - 00000000 - file date is 6/5/2009 16:04:38
C:\windows\system32\user32.dll     , loaded at 0x7ecc0000 - 74132 bytes - 00000000 - file date is 6/5/2009 16:04:40
C:\windows\system32\winmm.dll      , loaded at 0x7ee00000 - 318484 bytes - 00000000 - file date is 6/5/2009 16:04:40
```

Btw, what do I do with mini-dump files? (.dmp) Do I open them in some other sort of program?

---

