---
title: "Running Applications consistently fail"
date: 2010-11-23
forum: Wine
---

### Post by Kreen on 2010-11-23
So I'll go ahead and preface that I am completely new to Ubuntu, and so far I'm loving it for my laptop. However, I've got a trip coming up with a 7 hour drive, so a bit of gaming while I'm away from my main computer would be appreciated.

I've tried following all the guides I possibly can, but I'm just stumped on it. I'm spending most of my time trying to set up Morrowind (Tribunal + Bloodmoon). I've followed several guides to the tee with no luck, including [http://forums.fedoraforum.org/showthread.php?t=156033](http://forums.fedoraforum.org/showthread.php?t=156033) and [http://www.uesp.net/wiki/Morrowind:Linux](http://www.uesp.net/wiki/Morrowind:Linux) (while referencing the Oblivion version). I'm not sure what I'm doing all the time, so chances are I haven't tried something outside of those two guides. 

I've checked the sticky here and have tried/done all the things it recommends. Here is my system information:

Acer Aspire One 751h (GMA500 drivers enabled)
Ubuntu 10.10
Wine 1.3.7
For Morrowind: Win98, D:/ drive set up as CDROM (that worked, it no longer asks for the CD), ASLA audio Hardware emulation, emulate virtual desktop 1024x768, vertex shader support hardware; those are all the things I've kept the same. I've tried toggling between different OS versions, using different audio drivers, messing with the windows, and more.

Terminal output:
```
andrew@Aeris:~$ cd /home/andrew/.wine/drive_c/Program\ Files/Bethesda\ Softworks/Morrowind/
andrew@Aeris:~/.wine/drive_c/Program Files/Bethesda Softworks/Morrowind$ wine Morrowind.exe
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1083
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1083
wine: Unhandled page fault on read access to 0x00000000 at address 0x76ea2557 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x76ea2557).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:76ea2557 ESP:0032ee40 EBP:0032ee40 EFLAGS:00210202(  R- --  I   - - - )
 EAX:00000000 EBX:77112ff4 ECX:00000000 EDX:7d93de4c
 ESI:7d93e4a8 EDI:7d93e188
Stack dump:
0x0032ee40:  0032ee80 76ea1d70 00000000 00000000
0x0032ee50:  00000000 76ea8aad 00000de1 00000000
0x0032ee60:  00008057 7d93e188 00000010 00000001
0x0032ee70:  00000000 77112ff4 0000000b 7d97b008
0x0032ee80:  0032eea0 76f098da 7d97b008 7d93dbf8
0x0032ee90:  7d93de4c 7d93df80 7d97b008 7d93e188
Backtrace:
=>0 0x76ea2557 in psb_dri.so (+0x4a557) (0x0032ee40)
  1 0x76ea1d70 in psb_dri.so (+0x49d6f) (0x0032ee80)
  2 0x76f098da in psb_dri.so (+0xb18d9) (0x0032eea0)
  3 0x76f0f6f2 _mesa_TexImage2D+0x2b2() in psb_dri.so (0x0032ef10)
  4 0x688e20f6 in wined3d (+0xe20f5) (0x0032efe0)
  5 0x68865956 in wined3d (+0x65955) (0x0032f470)
  6 0x688665a6 in wined3d (+0x665a5) (0x0032f490)
  7 0x688eb0ca WineDirect3DCreate+0x59() in wined3d (0x0032f4d0)
  8 0x687dcd28 Direct3DCreate8+0x67() in d3d8 (0x0032f500)
  9 0x006b1014 in morrowind (+0x2b1013) (0x00180788)
  10 0x001ca738 (0x0074665c)
  11 0x004f52a0 in morrowind (+0xf529f) (0x004174a0)
0x76ea2557: cmpl	$0x8513,0x0(%ecx)
Modules:
Module	Address			Debug info	Name (82 modules)
PE	  400000-  7e4000	Export          morrowind
PE	30000000-3006e000	Deferred        binkw32
ELF	40133000-40186000	Deferred        libgl.so.1
ELF	45f1b000-45f1f000	Deferred        libxdamage.so.1
ELF	501d4000-501f0000	Deferred        libgcc_s.so.1
ELF	68000000-6801e000	Deferred        ld-linux.so.2
ELF	6801e000-6815e000	Deferred        libwine.so.1
ELF	6815e000-68178000	Deferred        libpthread.so.0
ELF	68178000-682d6000	Deferred        libc.so.6
ELF	682d6000-682da000	Deferred        libdl.so.2
ELF	682da000-68300000	Deferred        libm.so.6
ELF	68300000-68308000	Deferred        libnss_compat.so.2
ELF	68308000-6831f000	Deferred        libnsl.so.1
ELF	6831f000-6832a000	Deferred        libnss_nis.so.2
ELF	6832a000-68336000	Deferred        libnss_files.so.2
ELF	68336000-6846a000	Deferred        user32<elf>
  \-PE	68350000-6846a000	\               user32
ELF	6846a000-684f6000	Deferred        gdi32<elf>
  \-PE	68480000-684f6000	\               gdi32
ELF	684f6000-68551000	Deferred        advapi32<elf>
  \-PE	68500000-68551000	\               advapi32
ELF	68551000-6856a000	Deferred        version<elf>
  \-PE	68560000-6856a000	\               version
ELF	6856a000-6866c000	Deferred        ole32<elf>
  \-PE	68580000-6866c000	\               ole32
ELF	6866c000-686df000	Deferred        rpcrt4<elf>
  \-PE	68680000-686df000	\               rpcrt4
ELF	686df000-68774000	Deferred        winmm<elf>
  \-PE	686f0000-68774000	\               winmm
ELF	68774000-6878f000	Deferred        dinput8<elf>
  \-PE	68780000-6878f000	\               dinput8
ELF	6878f000-687c8000	Deferred        dinput<elf>
  \-PE	687a0000-687c8000	\               dinput
ELF	687c8000-687f6000	Export          d3d8<elf>
  \-PE	687d0000-687f6000	\               d3d8
ELF	687f6000-68926000	Export          wined3d<elf>
  \-PE	68800000-68926000	\               wined3d
ELF	68926000-689ae000	Deferred        msvcrt<elf>
  \-PE	68940000-689ae000	\               msvcrt
ELF	689ae000-68a9e000	Deferred        comctl32<elf>
  \-PE	689c0000-68a9e000	\               comctl32
ELF	68a9e000-68b3c000	Deferred        krnl386.exe16.so
PE	68ab0000-68b3c000	Deferred        krnl386.exe16
ELF	68b3c000-68b51000	Deferred        system.drv16.so
PE	68b40000-68b51000	Deferred        system.drv16
ELF	68b51000-68b65000	Deferred        comm.drv16.so
PE	68b60000-68b65000	Deferred        comm.drv16
ELF	68b65000-68bdc000	Deferred        libfreetype.so.6
ELF	68bdc000-68bf1000	Deferred        libz.so.1
ELF	68bf1000-68c21000	Deferred        libfontconfig.so.1
ELF	68c21000-68c48000	Deferred        libexpat.so.1
ELF	68c48000-68c51000	Deferred        libsm.so.6
ELF	68c51000-68c6a000	Deferred        libice.so.6
ELF	68c6a000-68c7a000	Deferred        libxext.so.6
ELF	68c7a000-68d97000	Deferred        libx11.so.6
ELF	68d97000-68d9c000	Deferred        libuuid.so.1
ELF	68d9c000-68da0000	Deferred        libxau.so.6
ELF	68da0000-68da6000	Deferred        libxdmcp.so.6
ELF	68da6000-68dc7000	Deferred        imm32<elf>
  \-PE	68db0000-68dc7000	\               imm32
ELF	68dc7000-68dcd000	Deferred        libxxf86vm.so.1
ELF	68dcd000-68dd7000	Deferred        libxrender.so.1
ELF	68dd7000-68ddf000	Deferred        libxrandr.so.2
ELF	68ddf000-68de3000	Deferred        libxcomposite.so.1
ELF	68de3000-68de9000	Deferred        libxfixes.so.3
ELF	68de9000-68df3000	Deferred        libxcursor.so.1
ELF	68df3000-68e27000	Deferred        uxtheme<elf>
  \-PE	68e00000-68e27000	\               uxtheme
ELF	6ca19000-6ca61000	Deferred        dsound<elf>
  \-PE	6ca20000-6ca61000	\               dsound
ELF	7114b000-71165000	Deferred        libxcb.so.1
ELF	72d69000-72d73000	Deferred        libdrm.so.2
ELF	76e58000-7712e000	Export          psb_dri.so
PE	780c0000-78121000	Deferred        msvcp60
ELF	7a3cd000-7a476000	Deferred        winex11<elf>
  \-PE	7a3e0000-7a476000	\               winex11
ELF	7adf7000-7adfb000	Deferred        libxinerama.so.1
ELF	7b800000-7b980000	Deferred        kernel32<elf>
  \-PE	7b810000-7b980000	\               kernel32
ELF	7bc00000-7bcbb000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcbb000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Bethesda Softworks\Morrowind\Morrowind.exe
	00000009    0 <==
0000000e services.exe
	00000018    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000017    0
	00000016    0
	00000013    0
	00000012    0
0000001b explorer.exe
	0000001c    0
Backtrace:
=>0 0x76ea2557 in psb_dri.so (+0x4a557) (0x0032ee40)
  1 0x76ea1d70 in psb_dri.so (+0x49d6f) (0x0032ee80)
  2 0x76f098da in psb_dri.so (+0xb18d9) (0x0032eea0)
  3 0x76f0f6f2 _mesa_TexImage2D+0x2b2() in psb_dri.so (0x0032ef10)
  4 0x688e20f6 in wined3d (+0xe20f5) (0x0032efe0)
  5 0x68865956 in wined3d (+0x65955) (0x0032f470)
  6 0x688665a6 in wined3d (+0x665a5) (0x0032f490)
  7 0x688eb0ca WineDirect3DCreate+0x59() in wined3d (0x0032f4d0)
  8 0x687dcd28 Direct3DCreate8+0x67() in d3d8 (0x0032f500)
  9 0x006b1014 in morrowind (+0x2b1013) (0x00180788)
  10 0x001ca738 (0x0074665c)
  11 0x004f52a0 in morrowind (+0xf529f) (0x004174a0)
andrew@Aeris:~/.wine/drive_c/Program Files/Bethesda Softworks/Morrowind$
```

As for what happens, I recently disabled pixel shader, and now I get the virtual desktop window and a window inside that that is about to start up morrowind before I get the "program has encountered a serious error" message. Before when I had that option checked, I'd just get the message and no window.

What frustrates me is that in the appdb this is supposed to work fairly well, and there's no indication or documentation as to what all the other people did to get it working.

In addition to Morrowind, I've tried installing Zeus: Master of Olympus (I thought an older 2D game might work better, especially on my Netbook). Everything is pretty much the same. I install it flawlessly, either set up a CDROM drive/crack the .exe (I own all the CDs to these games and made .iso's from them for setting up the drive), and then it just fails. It too, states that it should run without any modifications in the appdb.

I am new to Ubuntu and Linux in general, but I'm not computer-illiterate. I cannot for the life of me find any guides for interpreting the wine error messages (which would help a LOT) nor any guides for installing these programs that work. I'm literally at the end of my rope in terms of what more I can do/research, so I hope that someone here has had experience with this before who might be seeing something very simple and obvious that I'm missing!

Thanks in advance =)

---

### Post by bobwyajnr on 2010-11-24
> **Kreen said:**
> 
In addition to Morrowind, I've tried installing Zeus: Master of Olympus (I thought an older 2D game might work better, especially on my Netbook). 

I think that this game should definitely run on an Intel GMA - since it only requires DX7.0 support. Did you try setting Wine to Windows 95 mode for this one? It would actually be more instructive to see what the console output is from this game.

RE Morrowind III - I have a sneaky suspicion that games that require DX8.x support - which in return requires hardware pixel shader support.

Sorry I can't give a definite answer but I (personally) avoid Intel integrated graphics like the plague. Nvidia GPUs would generally be my GPU of choice (both on the desktop and notebooks). My current ASUS notebook has an AMD Radeon 4650M which has 'reasonable' 3D driver support!

Unfortunately the minimum system specification contents for Wine AppDB application reports was very poorly thought out - when it was originally conceived. The reports should also include the GPU model and driver version.
Most of the reports for DirectX 8.0+ games, which run out of the box without complications, will be for Nvidia GPUs (and AMD GPUs) with binary drivers.

Bob

---

### Post by Kreen on 2010-11-24
Here it is when trying to run Zeus:

```
andrew@Aeris:~/.wine/drive_c/Impressions Games/Zeus$ wine ZEUS.EXE 
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1083
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1083
wine: Unhandled page fault on read access to 0x00000000 at address 0x3ec61557 (thread 0027), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x3ec61557).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:3ec61557 ESP:0032f4d4 EBP:0032f4d4 EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000000 EBX:3eed1ff4 ECX:00000000 EDX:7c8bee04
 ESI:7c8bf3e0 EDI:7c8c15a0
Stack dump:
0x0032f4d4:  0032f514 3ec60d70 00000000 00000000
0x0032f4e4:  00000000 3ec67aad 00000de1 00000000
0x0032f4f4:  00008057 7c8c15a0 00000010 00000001
0x0032f504:  00000000 3eed1ff4 0000000b 7c59a108
0x0032f514:  0032f534 3ecc88da 7c59a108 7c8bebb0
0x0032f524:  7c8bee04 7c8bef38 7c59a108 7c8c15a0
Backtrace:
=>0 0x3ec61557 in psb_dri.so (+0x4a557) (0x0032f4d4)
  1 0x3ec60d70 in psb_dri.so (+0x49d6f) (0x0032f514)
  2 0x3ecc88da in psb_dri.so (+0xb18d9) (0x0032f534)
  3 0x3ecce6f2 _mesa_TexImage2D+0x2b2() in psb_dri.so (0x0032f5a4)
  4 0x62bba0f6 in wined3d (+0xda0f5) (0x0032f674)
  5 0x62b3d956 in wined3d (+0x5d955) (0x0032fb04)
  6 0x62b3e5a6 in wined3d (+0x5e5a5) (0x0032fb24)
  7 0x62bc30ca WineDirect3DCreate+0x59() in wined3d (0x0032fb64)
  8 0x6834d970 in ddraw (+0x1d96f) (0x0032fbb4)
  9 0x6835e0d5 in ddraw (+0x2e0d4) (0x0032fc14)
  10 0x6835e963 DirectDrawCreate+0x52() in ddraw (0x0032fc64)
  11 0x004f3b3a in zeus (+0xf3b39) (0x0032fe04)
  12 0x0058431e in zeus (+0x18431d) (0x0032fe90)
  13 0x7b8560ac call_process_entry+0xb() in kernel32 (0x0032fea8)
  14 0x7b856d4f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  15 0x7bc717f0 call_thread_func+0xb() in ntdll (0x0032fef8)
  16 0x7bc74390 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  17 0x7bc49cba call_dll_entry_point+0x659() in ntdll (0x0032ffe8)
0x3ec61557: cmpl	$0x8513,0x0(%ecx)
Modules:
Module	Address			Debug info	Name (81 modules)
PE	  400000- 1451000	Export          zeus
PE	10000000-10057000	Deferred        binkw32
PE	21100000-2115e000	Deferred        mss32
ELF	3cf93000-3cfaf000	Deferred        libgcc_s.so.1
ELF	3e383000-3e38d000	Deferred        libdrm.so.2
ELF	3ec17000-3eeed000	Export          psb_dri.so
ELF	3fc4a000-3fc4e000	Deferred        libxdamage.so.1
ELF	51aee000-51b41000	Deferred        libgl.so.1
PE	60000000-60025000	Deferred        ijl10
ELF	62ace000-62bfe000	Export          wined3d<elf>
  \-PE	62ae0000-62bfe000	\               wined3d
ELF	68000000-6801e000	Deferred        ld-linux.so.2
ELF	6801e000-6815e000	Export          libwine.so.1
ELF	6815e000-68178000	Deferred        libpthread.so.0
ELF	68178000-682d6000	Deferred        libc.so.6
ELF	682d6000-682da000	Deferred        libdl.so.2
ELF	682da000-68300000	Deferred        libm.so.6
ELF	68300000-68308000	Deferred        libnss_compat.so.2
ELF	68308000-6831f000	Deferred        libnsl.so.1
ELF	6831f000-6832b000	Deferred        libnss_files.so.2
ELF	6832b000-68388000	Export          ddraw<elf>
  \-PE	68330000-68388000	\               ddraw
ELF	68388000-6848a000	Deferred        ole32<elf>
  \-PE	683a0000-6848a000	\               ole32
ELF	6848a000-684e5000	Deferred        advapi32<elf>
  \-PE	684a0000-684e5000	\               advapi32
ELF	684e5000-68619000	Deferred        user32<elf>
  \-PE	68500000-68619000	\               user32
ELF	68619000-686a5000	Deferred        gdi32<elf>
  \-PE	68620000-686a5000	\               gdi32
ELF	686a5000-686be000	Deferred        version<elf>
  \-PE	686b0000-686be000	\               version
ELF	686be000-68731000	Deferred        rpcrt4<elf>
  \-PE	686d0000-68731000	\               rpcrt4
ELF	68731000-6891e000	Deferred        shell32<elf>
  \-PE	68740000-6891e000	\               shell32
ELF	6891e000-68981000	Deferred        shlwapi<elf>
  \-PE	68930000-68981000	\               shlwapi
ELF	68981000-68a71000	Deferred        comctl32<elf>
  \-PE	68990000-68a71000	\               comctl32
ELF	68a71000-68b06000	Deferred        winmm<elf>
  \-PE	68a80000-68b06000	\               winmm
ELF	68b06000-68ba4000	Deferred        krnl386.exe16.so
PE	68b10000-68ba4000	Deferred        krnl386.exe16
ELF	68ba4000-68bb9000	Deferred        system.drv16.so
PE	68bb0000-68bb9000	Deferred        system.drv16
ELF	68bb9000-68bcd000	Deferred        comm.drv16.so
PE	68bc0000-68bcd000	Deferred        comm.drv16
ELF	68bcd000-68c44000	Deferred        libfreetype.so.6
ELF	68c44000-68c59000	Deferred        libz.so.1
ELF	68c59000-68c89000	Deferred        libfontconfig.so.1
ELF	68c89000-68cb0000	Deferred        libexpat.so.1
ELF	68cb0000-68d59000	Deferred        winex11<elf>
  \-PE	68cc0000-68d59000	\               winex11
ELF	68d59000-68d62000	Deferred        libsm.so.6
ELF	68d62000-68d7b000	Deferred        libice.so.6
ELF	68d7b000-68d8b000	Deferred        libxext.so.6
ELF	68d8b000-68ea8000	Deferred        libx11.so.6
ELF	68ea8000-68ead000	Deferred        libuuid.so.1
ELF	68ead000-68ec7000	Deferred        libxcb.so.1
ELF	68ec7000-68ecb000	Deferred        libxau.so.6
ELF	68ecb000-68ed1000	Deferred        libxdmcp.so.6
ELF	68ed1000-68ef2000	Deferred        imm32<elf>
  \-PE	68ee0000-68ef2000	\               imm32
ELF	68ef2000-68ef6000	Deferred        libxinerama.so.1
ELF	68ef6000-68f00000	Deferred        libxrender.so.1
ELF	68f00000-68f08000	Deferred        libxrandr.so.2
ELF	68f08000-68f0c000	Deferred        libxcomposite.so.1
ELF	68f0c000-68f12000	Deferred        libxfixes.so.3
ELF	68f12000-68f1c000	Deferred        libxcursor.so.1
ELF	68f1c000-68f50000	Deferred        uxtheme<elf>
  \-PE	68f20000-68f50000	\               uxtheme
ELF	6d11e000-6d1a6000	Deferred        msvcrt<elf>
  \-PE	6d130000-6d1a6000	\               msvcrt
ELF	6ef5d000-6ef68000	Deferred        libnss_nis.so.2
ELF	70024000-7002a000	Deferred        libxxf86vm.so.1
ELF	7b800000-7b980000	Export          kernel32<elf>
  \-PE	7b810000-7b980000	\               kernel32
ELF	7bc00000-7bcbb000	Export          ntdll<elf>
  \-PE	7bc10000-7bcbb000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 winecfg.exe
	0000001b    0
	00000009    0
0000000e services.exe
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000018    0
	00000017    0
	00000013    0
	00000012    0
00000019 explorer.exe
	0000001a    0
00000026 (D) C:\Impressions Games\Zeus\ZEUS.EXE
	00000027    0 <==
00000028 explorer.exe
	00000029    0
Backtrace:
=>0 0x3ec61557 in psb_dri.so (+0x4a557) (0x0032f4d4)
  1 0x3ec60d70 in psb_dri.so (+0x49d6f) (0x0032f514)
  2 0x3ecc88da in psb_dri.so (+0xb18d9) (0x0032f534)
  3 0x3ecce6f2 _mesa_TexImage2D+0x2b2() in psb_dri.so (0x0032f5a4)
  4 0x62bba0f6 in wined3d (+0xda0f5) (0x0032f674)
  5 0x62b3d956 in wined3d (+0x5d955) (0x0032fb04)
  6 0x62b3e5a6 in wined3d (+0x5e5a5) (0x0032fb24)
  7 0x62bc30ca WineDirect3DCreate+0x59() in wined3d (0x0032fb64)
  8 0x6834d970 in ddraw (+0x1d96f) (0x0032fbb4)
  9 0x6835e0d5 in ddraw (+0x2e0d4) (0x0032fc14)
  10 0x6835e963 DirectDrawCreate+0x52() in ddraw (0x0032fc64)
  11 0x004f3b3a in zeus (+0xf3b39) (0x0032fe04)
  12 0x0058431e in zeus (+0x18431d) (0x0032fe90)
  13 0x7b8560ac call_process_entry+0xb() in kernel32 (0x0032fea8)
  14 0x7b856d4f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  15 0x7bc717f0 call_thread_func+0xb() in ntdll (0x0032fef8)
  16 0x7bc74390 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  17 0x7bc49cba call_dll_entry_point+0x659() in ntdll (0x0032ffe8)
```

It's the same error message I think, concerning the frambuffer. It says to check utils.c, but I don't think I can since I didn't compile wine? I'm also guessing that D3D could stand for Direct3D, but I'm not sure where to find those settings to tweak.

---

### Post by Penguin=) on 2010-11-24
> **Kreen said:**
> Here it is when trying to run Zeus:

```
andrew@Aeris:~/.wine/drive_c/Impressions Games/Zeus$ wine ZEUS.EXE 
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1083
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1083
wine: Unhandled page fault on read access to 0x00000000 at address 0x3ec61557 (thread 0027), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x3ec61557).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:3ec61557 ESP:0032f4d4 EBP:0032f4d4 EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000000 EBX:3eed1ff4 ECX:00000000 EDX:7c8bee04
 ESI:7c8bf3e0 EDI:7c8c15a0
Stack dump:
0x0032f4d4:  0032f514 3ec60d70 00000000 00000000
0x0032f4e4:  00000000 3ec67aad 00000de1 00000000
0x0032f4f4:  00008057 7c8c15a0 00000010 00000001
0x0032f504:  00000000 3eed1ff4 0000000b 7c59a108
0x0032f514:  0032f534 3ecc88da 7c59a108 7c8bebb0
0x0032f524:  7c8bee04 7c8bef38 7c59a108 7c8c15a0
Backtrace:
=>0 0x3ec61557 in psb_dri.so (+0x4a557) (0x0032f4d4)
  1 0x3ec60d70 in psb_dri.so (+0x49d6f) (0x0032f514)
  2 0x3ecc88da in psb_dri.so (+0xb18d9) (0x0032f534)
  3 0x3ecce6f2 _mesa_TexImage2D+0x2b2() in psb_dri.so (0x0032f5a4)
  4 0x62bba0f6 in wined3d (+0xda0f5) (0x0032f674)
  5 0x62b3d956 in wined3d (+0x5d955) (0x0032fb04)
  6 0x62b3e5a6 in wined3d (+0x5e5a5) (0x0032fb24)
  7 0x62bc30ca WineDirect3DCreate+0x59() in wined3d (0x0032fb64)
  8 0x6834d970 in ddraw (+0x1d96f) (0x0032fbb4)
  9 0x6835e0d5 in ddraw (+0x2e0d4) (0x0032fc14)
  10 0x6835e963 DirectDrawCreate+0x52() in ddraw (0x0032fc64)
  11 0x004f3b3a in zeus (+0xf3b39) (0x0032fe04)
  12 0x0058431e in zeus (+0x18431d) (0x0032fe90)
  13 0x7b8560ac call_process_entry+0xb() in kernel32 (0x0032fea8)
  14 0x7b856d4f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  15 0x7bc717f0 call_thread_func+0xb() in ntdll (0x0032fef8)
  16 0x7bc74390 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  17 0x7bc49cba call_dll_entry_point+0x659() in ntdll (0x0032ffe8)
0x3ec61557: cmpl    $0x8513,0x0(%ecx)
Modules:
Module    Address            Debug info    Name (81 modules)
PE      400000- 1451000    Export          zeus
PE    10000000-10057000    Deferred        binkw32
PE    21100000-2115e000    Deferred        mss32
ELF    3cf93000-3cfaf000    Deferred        libgcc_s.so.1
ELF    3e383000-3e38d000    Deferred        libdrm.so.2
ELF    3ec17000-3eeed000    Export          psb_dri.so
ELF    3fc4a000-3fc4e000    Deferred        libxdamage.so.1
ELF    51aee000-51b41000    Deferred        libgl.so.1
PE    60000000-60025000    Deferred        ijl10
ELF    62ace000-62bfe000    Export          wined3d<elf>
  \-PE    62ae0000-62bfe000    \               wined3d
ELF    68000000-6801e000    Deferred        ld-linux.so.2
ELF    6801e000-6815e000    Export          libwine.so.1
ELF    6815e000-68178000    Deferred        libpthread.so.0
ELF    68178000-682d6000    Deferred        libc.so.6
ELF    682d6000-682da000    Deferred        libdl.so.2
ELF    682da000-68300000    Deferred        libm.so.6
ELF    68300000-68308000    Deferred        libnss_compat.so.2
ELF    68308000-6831f000    Deferred        libnsl.so.1
ELF    6831f000-6832b000    Deferred        libnss_files.so.2
ELF    6832b000-68388000    Export          ddraw<elf>
  \-PE    68330000-68388000    \               ddraw
ELF    68388000-6848a000    Deferred        ole32<elf>
  \-PE    683a0000-6848a000    \               ole32
ELF    6848a000-684e5000    Deferred        advapi32<elf>
  \-PE    684a0000-684e5000    \               advapi32
ELF    684e5000-68619000    Deferred        user32<elf>
  \-PE    68500000-68619000    \               user32
ELF    68619000-686a5000    Deferred        gdi32<elf>
  \-PE    68620000-686a5000    \               gdi32
ELF    686a5000-686be000    Deferred        version<elf>
  \-PE    686b0000-686be000    \               version
ELF    686be000-68731000    Deferred        rpcrt4<elf>
  \-PE    686d0000-68731000    \               rpcrt4
ELF    68731000-6891e000    Deferred        shell32<elf>
  \-PE    68740000-6891e000    \               shell32
ELF    6891e000-68981000    Deferred        shlwapi<elf>
  \-PE    68930000-68981000    \               shlwapi
ELF    68981000-68a71000    Deferred        comctl32<elf>
  \-PE    68990000-68a71000    \               comctl32
ELF    68a71000-68b06000    Deferred        winmm<elf>
  \-PE    68a80000-68b06000    \               winmm
ELF    68b06000-68ba4000    Deferred        krnl386.exe16.so
PE    68b10000-68ba4000    Deferred        krnl386.exe16
ELF    68ba4000-68bb9000    Deferred        system.drv16.so
PE    68bb0000-68bb9000    Deferred        system.drv16
ELF    68bb9000-68bcd000    Deferred        comm.drv16.so
PE    68bc0000-68bcd000    Deferred        comm.drv16
ELF    68bcd000-68c44000    Deferred        libfreetype.so.6
ELF    68c44000-68c59000    Deferred        libz.so.1
ELF    68c59000-68c89000    Deferred        libfontconfig.so.1
ELF    68c89000-68cb0000    Deferred        libexpat.so.1
ELF    68cb0000-68d59000    Deferred        winex11<elf>
  \-PE    68cc0000-68d59000    \               winex11
ELF    68d59000-68d62000    Deferred        libsm.so.6
ELF    68d62000-68d7b000    Deferred        libice.so.6
ELF    68d7b000-68d8b000    Deferred        libxext.so.6
ELF    68d8b000-68ea8000    Deferred        libx11.so.6
ELF    68ea8000-68ead000    Deferred        libuuid.so.1
ELF    68ead000-68ec7000    Deferred        libxcb.so.1
ELF    68ec7000-68ecb000    Deferred        libxau.so.6
ELF    68ecb000-68ed1000    Deferred        libxdmcp.so.6
ELF    68ed1000-68ef2000    Deferred        imm32<elf>
  \-PE    68ee0000-68ef2000    \               imm32
ELF    68ef2000-68ef6000    Deferred        libxinerama.so.1
ELF    68ef6000-68f00000    Deferred        libxrender.so.1
ELF    68f00000-68f08000    Deferred        libxrandr.so.2
ELF    68f08000-68f0c000    Deferred        libxcomposite.so.1
ELF    68f0c000-68f12000    Deferred        libxfixes.so.3
ELF    68f12000-68f1c000    Deferred        libxcursor.so.1
ELF    68f1c000-68f50000    Deferred        uxtheme<elf>
  \-PE    68f20000-68f50000    \               uxtheme
ELF    6d11e000-6d1a6000    Deferred        msvcrt<elf>
  \-PE    6d130000-6d1a6000    \               msvcrt
ELF    6ef5d000-6ef68000    Deferred        libnss_nis.so.2
ELF    70024000-7002a000    Deferred        libxxf86vm.so.1
ELF    7b800000-7b980000    Export          kernel32<elf>
  \-PE    7b810000-7b980000    \               kernel32
ELF    7bc00000-7bcbb000    Export          ntdll<elf>
  \-PE    7bc10000-7bcbb000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 winecfg.exe
    0000001b    0
    00000009    0
0000000e services.exe
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000017    0
    00000013    0
    00000012    0
00000019 explorer.exe
    0000001a    0
00000026 (D) C:\Impressions Games\Zeus\ZEUS.EXE
    00000027    0 <==
00000028 explorer.exe
    00000029    0
Backtrace:
=>0 0x3ec61557 in psb_dri.so (+0x4a557) (0x0032f4d4)
  1 0x3ec60d70 in psb_dri.so (+0x49d6f) (0x0032f514)
  2 0x3ecc88da in psb_dri.so (+0xb18d9) (0x0032f534)
  3 0x3ecce6f2 _mesa_TexImage2D+0x2b2() in psb_dri.so (0x0032f5a4)
  4 0x62bba0f6 in wined3d (+0xda0f5) (0x0032f674)
  5 0x62b3d956 in wined3d (+0x5d955) (0x0032fb04)
  6 0x62b3e5a6 in wined3d (+0x5e5a5) (0x0032fb24)
  7 0x62bc30ca WineDirect3DCreate+0x59() in wined3d (0x0032fb64)
  8 0x6834d970 in ddraw (+0x1d96f) (0x0032fbb4)
  9 0x6835e0d5 in ddraw (+0x2e0d4) (0x0032fc14)
  10 0x6835e963 DirectDrawCreate+0x52() in ddraw (0x0032fc64)
  11 0x004f3b3a in zeus (+0xf3b39) (0x0032fe04)
  12 0x0058431e in zeus (+0x18431d) (0x0032fe90)
  13 0x7b8560ac call_process_entry+0xb() in kernel32 (0x0032fea8)
  14 0x7b856d4f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  15 0x7bc717f0 call_thread_func+0xb() in ntdll (0x0032fef8)
  16 0x7bc74390 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  17 0x7bc49cba call_dll_entry_point+0x659() in ntdll (0x0032ffe8)
```It's the same error message I think, concerning the frambuffer. It says to check utils.c, but I don't think I can since I didn't compile wine? I'm also guessing that D3D could stand for Direct3D, but I'm not sure where to find those settings to tweak.



You could try and do this: Go to your desktop--->right click--->effects--->then put it to Extra

hope this helps get back to me

---

### Post by Kreen on 2010-11-24
I don't have that option when I right-click, so I went to System>Preferences>Appearance and the Visual Effects tab and checked "Extra", then close (if that's what you were talking about). Still the same error messages though.

I'm running Compiz though, if that helps

---

### Post by bobwyajnr on 2010-11-24
> **Kreen said:**
> 
I'm running Compiz though, if that helps

Uhhhmmmm (**<coughs>** very loudly in frustration)... Compiz will crash or (at the very least) c**p up most OpenGL/DirectX games run via Wine. You need to have your Window manager set to Metacity for a Gnome Desktop (or KVM with effects+compositing off for a KDE desktop).

Bob

---

### Post by Kreen on 2010-11-24
Thanks for the advice. I uninstalled Compiz and set my manager back to Metacity, but I'm still getting the same error messages. Also, in my appearances window, all the choices are grayed out now and it's set to "none". I'm not sure if that is normal or not.

With Compiz removed, I'm going to try all the various settings/possibilities I can again, but I'm not having any luck so far. Any other ideas?

---

### Post by bobwyajnr on 2010-11-25
> **Kreen said:**
> Also, in my appearances window, all the choices are grayed out now and it's set to "none". I'm not sure if that is normal or not.

Kubuntu / KDE (which uses the KVM Window manager) has 'built-in' effects. Ubuntu just uses Compiz to provide visual effects in Gnome. So obviously uninstalling Compiz will disable the option to turn on the effects. To be honest you could just install something like the CompizConfigIcon and manually switch between Metacity and Compiz as you require.

> **Kreen said:**
> 
With Compiz removed, I'm going to try all the various settings/possibilities I can again, but I'm not having any luck so far. Any other ideas?
```
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1083
```

DirectX calls are crashing Wine (**d3d**=Direct3D, **fbo**=frame buffer object, **compat**=comptability?). This would suggest that the Intel GMA kernel driver is at fault (simply deduced by the fact that other folks can get these games to work).

Just in case no one replies here (Ubuntu forums) I would suggest filing your problems as bugs on AppDB. There is a flood of bugs updates filed everyday (I subscribe to that email list). File a bug report with your console output and your hardware specs (+Intel MESA driver version - I suspect) - for each of the games you tried. There is a good chance you will get some feedback from the developer community (even if it just tells you that the Intel MESA driver is rubbish :p ).

From reading the KVM developer logs the Intel MESA driver advertises hardware capabilities that it doesn't actually possess!! (KVM, the KDE window manager, natively does desktop effects like Compiz.)

Bob

---

### Post by Kreen on 2010-11-25
Bit of an update. You were right in suspecting that the drivers were the issue I believe. I removed the poulsbolo drivers and installed the alternate emgd drivers v1.5 (from lucazade's post [http://ubuntuforums.org/showthread.php?t=1229345&page=243](http://ubuntuforums.org/showthread.php?t=1229345&page=243)).

This is the new terminal output for running Zeus.

```
andrew@Aeris:~$ cd .wine/drive_c/Impressions\ Games/Zeus/
andrew@Aeris:~/.wine/drive_c/Impressions Games/Zeus$ wine ZEUS.EXE 
fixme:d3d_caps:wined3d_guess_gl_vendor Received unrecognized GL_VENDOR "Imagination Technologies". Returning GL_VENDOR_UNKNOWN.
fixme:d3d_caps:wined3d_guess_card_vendor Received unrecognized GL_VENDOR "Imagination Technologies". Returning HW_VENDOR_NVIDIA.
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 0 and card vendor 10de.
Mesa warning: User called no-op dispatch function (an unsupported extension function?)
Mesa warning: User called no-op dispatch function (an unsupported extension function?)
err:d3d:match_fbo_tex_update >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glFramebufferTexture2D @ directx.c / 707
err:d3d:match_fbo_tex_update FBO status 0
Mesa warning: User called no-op dispatch function (an unsupported extension function?)
err:d3d:match_fbo_tex_update >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glBindTexture @ directx.c / 727
lib/drivers/powervr/bufobj.c:118: BufObjIndexFromTarget: Assertion `0' failed.
wine: Assertion failed at address 0x6c817832 (thread 0009), starting debugger...
Unhandled exception: assertion failed in 32-bit code (0x6c817832).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6c817832 ESP:0032f1f8 EBP:0032f204 EFLAGS:00200206(   - --  I   - -P- )
 EAX:00000000 EBX:00000699 ECX:00000699 EDX:00000006
 ESI:6814fb7f EDI:68173ff4
Stack dump:
0x0032f1f8:  68044941 68173ff4 0032f324 0032f32c
0x0032f208:  68047e42 00000006 0032f2a4 00000000
0x0032f218:  0032f24c 6808bf53 00000068 00000058
0x0032f228:  68085b62 0032f33c 00000068 00000058
0x0032f238:  00000050 7dadfd88 68173ff4 00000050
0x0032f248:  0000004f 0032f314 6807af72 7dadfd90
Backtrace:
=>0 0x6c817832 GLIBC_2+0x832() in ld-linux.so.2 (0x0032f204)
  1 0x68047e42 abort+0x181() in libc.so.6 (0x0032f32c)
  2 0x6803d8e8 __assert_fail+0xf7() in libc.so.6 (0x0032f374)
  3 0x66171a99 in libpvrogl.so (+0x23a98) (0x0032f394)
  4 0x66171af5 in libpvrogl.so (+0x23af4) (0x0032f3d4)
  5 0x66223eb5 pvroglGetBufferPointervARB+0x24() in libpvrogl.so (0x0032f3f4)
  6 0x513c8c28 in wined3d (+0x48c27) (0x0032f4b4)
  7 0x513d7c0d in wined3d (+0x57c0c) (0x0032f674)
  8 0x513dc91e in wined3d (+0x5c91d) (0x0032fb04)
  9 0x513dd5a6 in wined3d (+0x5d5a5) (0x0032fb24)
  10 0x514620ca WineDirect3DCreate+0x59() in wined3d (0x0032fb64)
  11 0x681e3970 in ddraw (+0x1396f) (0x0032fbb4)
  12 0x681f40d5 in ddraw (+0x240d4) (0x0032fc14)
  13 0x681f4963 DirectDrawCreate+0x52() in ddraw (0x0032fc64)
  14 0x004f3b3a in zeus (+0xf3b39) (0x0032fe04)
  15 0x0058431e in zeus (+0x18431d) (0x0032fe90)
  16 0x7b8560ac call_process_entry+0xb() in kernel32 (0x0032fea8)
  17 0x7b856d4f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  18 0x7bc717f0 call_thread_func+0xb() in ntdll (0x0032fef8)
  19 0x7bc74390 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  20 0x7bc49cba call_dll_entry_point+0x659() in ntdll (0x0032ffe8)
0x6c817832 GLIBC_2+0x832 in ld-linux.so.2: ret	
Modules:
Module	Address			Debug info	Name (85 modules)
PE	  400000- 1451000	Export          zeus
PE	10000000-10057000	Deferred        binkw32
ELF	20000000-20008000	Deferred        libpvr2d.so
PE	21100000-2115e000	Deferred        mss32
ELF	2e3d1000-2e424000	Deferred        libgl.so.1
ELF	2fd56000-2ff75000	Deferred        emgd_dri.so
ELF	35661000-35684000	Deferred        libsrv_um.so
ELF	37549000-37553000	Deferred        libdrm.so.2
ELF	5136d000-5149d000	Export          wined3d<elf>
  \-PE	51380000-5149d000	\               wined3d
PE	60000000-60025000	Deferred        ijl10
ELF	6614e000-6643e000	Export          libpvrogl.so
ELF	68000000-6801a000	Deferred        libpthread.so.0
ELF	6801a000-68178000	Export          libc.so.6
ELF	68178000-6817c000	Deferred        libdl.so.2
ELF	6817c000-681a2000	Deferred        libm.so.6
ELF	681a2000-681aa000	Deferred        libnss_compat.so.2
ELF	681aa000-681b5000	Deferred        libnss_nis.so.2
ELF	681b5000-681c1000	Deferred        libnss_files.so.2
ELF	681c1000-6821e000	Export          ddraw<elf>
  \-PE	681d0000-6821e000	\               ddraw
ELF	6821e000-68320000	Deferred        ole32<elf>
  \-PE	68240000-68320000	\               ole32
ELF	68320000-68454000	Deferred        user32<elf>
  \-PE	68330000-68454000	\               user32
ELF	68454000-6846d000	Deferred        version<elf>
  \-PE	68460000-6846d000	\               version
ELF	6846d000-6865a000	Deferred        shell32<elf>
  \-PE	68480000-6865a000	\               shell32
ELF	6865a000-6874a000	Deferred        comctl32<elf>
  \-PE	68660000-6874a000	\               comctl32
ELF	6874a000-687df000	Deferred        winmm<elf>
  \-PE	68750000-687df000	\               winmm
ELF	687df000-68867000	Deferred        msvcrt<elf>
  \-PE	687f0000-68867000	\               msvcrt
ELF	68867000-68905000	Deferred        krnl386.exe16.so
PE	68880000-68905000	Deferred        krnl386.exe16
ELF	68905000-6891a000	Deferred        system.drv16.so
PE	68910000-6891a000	Deferred        system.drv16
ELF	6891a000-68991000	Deferred        libfreetype.so.6
ELF	68991000-689a6000	Deferred        libz.so.1
ELF	689a6000-689d6000	Deferred        libfontconfig.so.1
ELF	689d6000-689fd000	Deferred        libexpat.so.1
ELF	689fd000-68aa6000	Deferred        winex11<elf>
  \-PE	68a10000-68aa6000	\               winex11
ELF	68aa6000-68aaf000	Deferred        libsm.so.6
ELF	68aaf000-68abf000	Deferred        libxext.so.6
ELF	68abf000-68bdc000	Deferred        libx11.so.6
ELF	68bdc000-68be1000	Deferred        libuuid.so.1
ELF	68be1000-68bfb000	Deferred        libxcb.so.1
ELF	68bfb000-68c01000	Deferred        libxdmcp.so.6
ELF	68c01000-68c22000	Deferred        imm32<elf>
  \-PE	68c10000-68c22000	\               imm32
ELF	68c22000-68c28000	Deferred        libxxf86vm.so.1
ELF	68c28000-68c30000	Deferred        libxrandr.so.2
ELF	68c30000-68c34000	Deferred        libxcomposite.so.1
ELF	68c34000-68c3e000	Deferred        libxcursor.so.1
ELF	68c3e000-68c72000	Deferred        uxtheme<elf>
  \-PE	68c40000-68c72000	\               uxtheme
ELF	696c5000-69738000	Deferred        rpcrt4<elf>
  \-PE	696d0000-69738000	\               rpcrt4
ELF	6a03b000-6a03f000	Deferred        libxdamage.so.1
ELF	6bfd8000-6bfdc000	Deferred        libxinerama.so.1
ELF	6c817000-6c835000	Export          ld-linux.so.2
ELF	6cb74000-6cb8b000	Deferred        libnsl.so.1
ELF	6ce36000-6ce3c000	Deferred        libxfixes.so.3
ELF	6d39e000-6d3ba000	Deferred        libgcc_s.so.1
ELF	6e67c000-6e7bc000	Export          libwine.so.1
ELF	6f0bb000-6f147000	Deferred        gdi32<elf>
  \-PE	6f0d0000-6f147000	\               gdi32
ELF	6fc64000-6fc68000	Deferred        libxau.so.6
ELF	7068f000-706ea000	Deferred        advapi32<elf>
  \-PE	706a0000-706ea000	\               advapi32
ELF	70ce0000-70cf9000	Deferred        libice.so.6
ELF	724a9000-7250c000	Deferred        shlwapi<elf>
  \-PE	724c0000-7250c000	\               shlwapi
ELF	7268c000-72696000	Deferred        libxrender.so.1
ELF	72bcb000-72bdf000	Deferred        comm.drv16.so
PE	72bd0000-72bdf000	Deferred        comm.drv16
ELF	7a5c0000-7a5c9000	Deferred        librt.so.1
ELF	7b800000-7b980000	Export          kernel32<elf>
  \-PE	7b810000-7b980000	\               kernel32
ELF	7bc00000-7bcbb000	Export          ntdll<elf>
  \-PE	7bc10000-7bcbb000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Impressions Games\Zeus\ZEUS.EXE
	00000009    0 <==
0000000e services.exe
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000017    0
	00000016    0
	00000013    0
	00000012    0
0000001a explorer.exe
	0000001b    0
Backtrace:
=>0 0x6c817832 GLIBC_2+0x832() in ld-linux.so.2 (0x0032f204)
  1 0x68047e42 abort+0x181() in libc.so.6 (0x0032f32c)
  2 0x6803d8e8 __assert_fail+0xf7() in libc.so.6 (0x0032f374)
  3 0x66171a99 in libpvrogl.so (+0x23a98) (0x0032f394)
  4 0x66171af5 in libpvrogl.so (+0x23af4) (0x0032f3d4)
  5 0x66223eb5 pvroglGetBufferPointervARB+0x24() in libpvrogl.so (0x0032f3f4)
  6 0x513c8c28 in wined3d (+0x48c27) (0x0032f4b4)
  7 0x513d7c0d in wined3d (+0x57c0c) (0x0032f674)
  8 0x513dc91e in wined3d (+0x5c91d) (0x0032fb04)
  9 0x513dd5a6 in wined3d (+0x5d5a5) (0x0032fb24)
  10 0x514620ca WineDirect3DCreate+0x59() in wined3d (0x0032fb64)
  11 0x681e3970 in ddraw (+0x1396f) (0x0032fbb4)
  12 0x681f40d5 in ddraw (+0x240d4) (0x0032fc14)
  13 0x681f4963 DirectDrawCreate+0x52() in ddraw (0x0032fc64)
  14 0x004f3b3a in zeus (+0xf3b39) (0x0032fe04)
  15 0x0058431e in zeus (+0x18431d) (0x0032fe90)
  16 0x7b8560ac call_process_entry+0xb() in kernel32 (0x0032fea8)
  17 0x7b856d4f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  18 0x7bc717f0 call_thread_func+0xb() in ntdll (0x0032fef8)
  19 0x7bc74390 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  20 0x7bc49cba call_dll_entry_point+0x659() in ntdll (0x0032ffe8)
Aborted
```

---

### Post by bobwyajnr on 2010-11-28
> **Kreen said:**
> Bit of an update. You were right in suspecting that the drivers were the issue I believe. I removed the poulsbolo drivers and installed the alternate emgd drivers v1.5 (from lucazade's post [http://ubuntuforums.org/showthread.php?t=1229345&page=243](http://ubuntuforums.org/showthread.php?t=1229345&page=243)).


Hi

Sorry I haven't replied but I don't have a netbook or motherboard with an Intel GMA GPU to test against.

But like I said previously you best bet is to submit a bug against Wine.

Do ensure one of those two driver hacks actually works! I notice you haven't mentioned whether you have actually been able to run any native Linux OpenGL 3D games at all. The Wine developers tend to get a bit upset when people submit bugs from broken systems!! (Hmmm I wonder why... :popcorn:)

Bob

PS If you ever should be buying another netbook - it's probably best to get one with an [Nvidia ION2 GPU/chipset]("http://www.nvidia.com/object/IO_73301.html")!!

---

