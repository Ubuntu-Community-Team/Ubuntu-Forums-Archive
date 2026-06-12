---
title: "Attempting to run Prelude to Darkness in Wine"
date: 2009-08-27
forum: Wine
---

### Post by aniruddha on 2009-08-27
Hello all. I have recently been trying to run a rather old-ish indie rpg called Prelude to Darkness in Wine. The installer runs uptil 100% and then I get the following error message in the terminal:

fixme:shell:IPersistFile_fnGetCurFile (0x147e08)
wine: Unhandled page fault on read access to 0x0000000a at address 0x7b860fd0 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x0000000a in 32-bit code (0x7b860fd0).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b860fd0 ESP:0032f318 EBP:0032f360 EFLAGS:00010286(  R- --  I S - -P- )
 EAX:0000000a EBX:7b8b7ff4 ECX:0032f4b4 EDX:00000031
 ESI:00000001 EDI:0032f4b4
Stack dump:
0x0032f318:  00000000 f7f38ff4 7ec1c200 0032f851
0x0032f328:  0032f358 f7e162b9 00000000 7ec1c200
0x0032f338:  7eb13ec1 7eb0f21d 0032f370 00000000
0x0032f348:  00000000 00000000 7eb27ff4 0032f7f4
0x0032f358:  00651df0 0032f851 00000000 004053a3
0x0032f368:  00000000 00000000 0000000a ffffffff
Backtrace:
=>0 0x7b860fd0 WideCharToMultiByte+0x1f0(page=0, flags=0, src=0xa, srclen=1, dst="\", dstlen=260, defchar=0x0, used=(nil)) [/home/aniruddha/downloads/wine-1.1.26/dlls/kernel32/../../include/wine/unicode.h:216] in kernel32 (0x0032f360)
  1 0x004053a3 in pyrrhic_tales_prelude_to_darknesZ:\home\aniruddha\games\Ptd\Pyrrhic_Tales_Prelude_to_Darkness_v1.8_[final].exe (+0x53a3) (0x00000000)
0x7b860fd0 WideCharToMultiByte+0x1f0 [/home/aniruddha/downloads/wine-1.1.26/dlls/kernel32/../../include/wine/unicode.h:216] in kernel32: cmpw	$0,0x0(%eax)
Unable to open file ''
Modules:
Module	Address			Debug info	Name (67 modules)
PE	  400000-  422000	Export          pyrrhic_tales_prelude_to_darknesZ:\home\aniruddha\games\Ptd\Pyrrhic_Tales_Prelude_to_Darkness_v1.8_[final].exe
ELF	7b800000-7b962000	Dwarf           kernel32<elf>
  \-PE	7b820000-7b962000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e26b000-7e353000	Deferred        oleaut32<elf>
  \-PE	7e280000-7e353000	\               oleaut32
ELF	7e353000-7e3ac000	Deferred        riched20<elf>
  \-PE	7e360000-7e3ac000	\               riched20
ELF	7e3ed000-7e421000	Deferred        uxtheme<elf>
  \-PE	7e3f0000-7e421000	\               uxtheme
ELF	7e421000-7e42a000	Deferred        libxcursor.so.1
ELF	7e42a000-7e42f000	Deferred        libxfixes.so.3
ELF	7e42f000-7e433000	Deferred        libxcomposite.so.1
ELF	7e433000-7e43b000	Deferred        libxrandr.so.2
ELF	7e43b000-7e445000	Deferred        libxrender.so.1
ELF	7e445000-7e44b000	Deferred        libxxf86vm.so.1
ELF	7e44b000-7e44e000	Deferred        libxinerama.so.1
ELF	7e44e000-7e46f000	Deferred        imm32<elf>
  \-PE	7e450000-7e46f000	\               imm32
ELF	7e46f000-7e474000	Deferred        libxdmcp.so.6
ELF	7e474000-7e48e000	Deferred        libxcb.so.1
ELF	7e48e000-7e492000	Deferred        libxau.so.6
ELF	7e492000-7e497000	Deferred        libuuid.so.1
ELF	7e497000-7e586000	Deferred        libx11.so.6
ELF	7e586000-7e596000	Deferred        libxext.so.6
ELF	7e596000-7e5ae000	Deferred        libice.so.6
ELF	7e5ae000-7e5b7000	Deferred        libsm.so.6
ELF	7e5d6000-7e673000	Deferred        winex11<elf>
  \-PE	7e5e0000-7e673000	\               winex11
ELF	7e673000-7e688000	Deferred        keyboard.drv16.so
PE	7e680000-7e688000	Deferred        keyboard.drv16
ELF	7e6ec000-7e713000	Deferred        libexpat.so.1
ELF	7e713000-7e740000	Deferred        libfontconfig.so.1
ELF	7e740000-7e756000	Deferred        libz.so.1
ELF	7e756000-7e7cd000	Deferred        libfreetype.so.6
ELF	7e7ec000-7e800000	Deferred        lz32<elf>
  \-PE	7e7f0000-7e800000	\               lz32
ELF	7e800000-7e86d000	Deferred        rpcrt4<elf>
  \-PE	7e810000-7e86d000	\               rpcrt4
ELF	7e86d000-7e969000	Deferred        ole32<elf>
  \-PE	7e890000-7e969000	\               ole32
ELF	7e969000-7ea31000	Deferred        comctl32<elf>
  \-PE	7e970000-7ea31000	\               comctl32
ELF	7ea31000-7ea8f000	Deferred        shlwapi<elf>
  \-PE	7ea40000-7ea8f000	\               shlwapi
ELF	7ea8f000-7ec1d000	Deferred        shell32<elf>
  \-PE	7eaa0000-7ec1d000	\               shell32
ELF	7ec1d000-7ec73000	Deferred        advapi32<elf>
  \-PE	7ec30000-7ec73000	\               advapi32
ELF	7ec73000-7ed15000	Deferred        gdi32<elf>
  \-PE	7ec80000-7ed15000	\               gdi32
ELF	7ed15000-7ee61000	Deferred        user32<elf>
  \-PE	7ed30000-7ee61000	\               user32
ELF	7ef8b000-7ef97000	Deferred        libnss_files.so.2
ELF	7ef97000-7efa2000	Deferred        libnss_nis.so.2
ELF	7efa2000-7efbb000	Deferred        libnsl.so.1
ELF	7efbb000-7efe1000	Deferred        libm.so.6
ELF	7efe1000-7effc000	Deferred        version<elf>
  \-PE	7eff0000-7effc000	\               version
ELF	f7c71000-f7c75000	Deferred        libdl.so.2
ELF	f7c75000-f7dd8000	Deferred        libc.so.6
ELF	f7dd9000-f7df2000	Deferred        libpthread.so.0
ELF	f7df7000-f7e00000	Deferred        libnss_compat.so.2
ELF	f7e11000-f7f4d000	Deferred        libwine.so.1
ELF	f7f4f000-f7f70000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\aniruddha\games\Ptd\Pyrrhic_Tales_Prelude_to_Darkness_v1.8_[final].exe
	00000009    0 <==
0000000e 
	0000001c    0
	00000018    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000019 
	0000001e    0
	0000001d    0
	0000001b    0
	0000001a    0
0000001f 
	00000020    0
00000021 
	00000022    0
Backtrace:
=>0 0x7b860fd0 WideCharToMultiByte+0x1f0(page=0, flags=0, src=0xa, srclen=1, dst="\", dstlen=260, defchar=0x0, used=(nil)) [/home/aniruddha/downloads/wine-1.1.26/dlls/kernel32/../../include/wine/unicode.h:216] in kernel32 (0x0032f360)

The game itself starts up, but then immediately hangs up on the main menu screen. I am currently using Wine 1.1.26 on Ubuntu Jaunty 64bit with the 185.18.31 NVIDIA drivers. All settings in Wine are defaults (set to WinXP, with ALSA drivers, with D3D support and no custom libraries). Any help would be appreciated.,,

---

### Post by aniruddha on 2009-09-01
bump?

---

