---
title: "Algodoo"
date: 2010-04-25
forum: Wine
---

### Post by Affrikka on 2010-04-25
Hey everyone,

I installed Algodoo, and when I try to run it I get this output in the terminal:

```
mathieu@prometheus:~/.wine/dosdevices/c:/Program Files/Algodoo$ wine Algodoo.exefixme:win:EnumDisplayDevicesW ((null),0,0x32f32c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f394,0x00000000), stub!
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
wine: Call from 0x7bc4b9b0 to unimplemented function SDL.dll.SDL_RWFromConstMem, aborting
wine: Unimplemented function SDL.dll.SDL_RWFromConstMem called at address 0x7bc4b9b0 (thread 002e), starting debugger...
Unhandled exception: unimplemented function SDL.dll.SDL_RWFromConstMem called in 32-bit code (0x7bc4b9b0).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc4b9b0 ESP:0032eab4 EBP:0032eb18 EFLAGS:00000202(   - --  I   - - - )
 EAX:0098cf58 EBX:7bc9aff4 ECX:0032eb4c EDX:00000000
 ESI:0032eac0 EDI:0000018e
Stack dump:
0x0032eab4:  00000000 00e3c6d8 7bc3520f 80000100
0x0032eac4:  00000001 00000000 7bc4b9b0 00000002
0x0032ead4:  0098d214 0098cf58 784b88f4 785061f0
0x0032eae4:  0032eb00 784b4ffe 785061f0 78484f8d
0x0032eaf4:  0000018e 0032efb8 00000000 00e3c6d8
0x0032eb04:  7848501d 005fe669 00000000 00000000
Backtrace:
=>0 0x7bc4b9b0 in ntdll (+0x3b9b0) (0x0032eb18)
  1 0x0037000f (0x00e3c6d8)
0x7bc4b9b0: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (109 modules)
PE	  330000-  36c000	Deferred        sdl
PE	  380000-  39f000	Deferred        libpng12
PE	  3a0000-  3b2000	Deferred        zlib1
PE	  3c0000-  3eb000	Deferred        curllib
PE	  400000-  a60000	Deferred        algodoo
PE	  a60000-  af6000	Deferred        highgui100
PE	  b00000-  be2000	Deferred        cxcore100
PE	  bf0000-  cf7000	Deferred        libeay32
PE	  d00000-  d31000	Deferred        ssleay32
PE	 12c0000- 1363000	Deferred        libzip
PE	 1370000- 1384000	Deferred        mgwz
PE	10000000-10036000	Deferred        glew32
PE	62e40000-62e60000	Deferred        sdl_image
PE	72880000-7288e000	Deferred        vcomp90
PE	78480000-7850d000	Deferred        msvcp90
PE	78520000-785c3000	Deferred        msvcr90
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b810000-7b93d000	\               kernel32
ELF	7bc00000-7bcb7000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb7000	\               ntdll
ELF	7bdc9000-7bf00000	Deferred        wined3d<elf>
  \-PE	7bdd0000-7bf00000	\               wined3d
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c02a000-7c082000	Deferred        ddraw<elf>
  \-PE	7c030000-7c082000	\               ddraw
ELF	7c384000-7dba3000	Deferred        fglrx_dri.so
ELF	7dcfd000-7dd36000	Deferred        dinput<elf>
  \-PE	7dd10000-7dd36000	\               dinput
ELF	7de32000-7de5e000	Deferred        libatiadlxx.so
ELF	7de6b000-7de81000	Deferred        winejoystick<elf>
  \-PE	7de70000-7de81000	\               winejoystick
ELF	7deda000-7df0e000	Deferred        uxtheme<elf>
  \-PE	7dee0000-7df0e000	\               uxtheme
ELF	7df0e000-7df19000	Deferred        libxcursor.so.1
ELF	7df19000-7df1f000	Deferred        libxfixes.so.3
ELF	7df1f000-7df23000	Deferred        libxcomposite.so.1
ELF	7df23000-7df2c000	Deferred        libxrandr.so.2
ELF	7df2c000-7df36000	Deferred        libxrender.so.1
ELF	7df36000-7df3c000	Deferred        libxxf86vm.so.1
ELF	7df3c000-7df3f000	Deferred        libxinerama.so.1
ELF	7df41000-7df4a000	Deferred        librt.so.1
ELF	7df62000-7df84000	Deferred        imm32<elf>
  \-PE	7df70000-7df84000	\               imm32
ELF	7df84000-7e025000	Deferred        winex11<elf>
  \-PE	7df90000-7e025000	\               winex11
ELF	7e064000-7e08b000	Deferred        libexpat.so.1
ELF	7e08b000-7e0b8000	Deferred        libfontconfig.so.1
ELF	7e0b8000-7e0ce000	Deferred        libz.so.1
ELF	7e0ce000-7e14d000	Deferred        libfreetype.so.6
ELF	7e14d000-7e161000	Deferred        libresolv.so.2
ELF	7e184000-7e1a5000	Deferred        iphlpapi<elf>
  \-PE	7e190000-7e1a5000	\               iphlpapi
ELF	7e1a5000-7e1d1000	Deferred        ws2_32<elf>
  \-PE	7e1b0000-7e1d1000	\               ws2_32
ELF	7e1d1000-7e1ec000	Deferred        wsock32<elf>
  \-PE	7e1e0000-7e1ec000	\               wsock32
ELF	7e1ec000-7e2ea000	Deferred        ole32<elf>
  \-PE	7e210000-7e2ea000	\               ole32
ELF	7e2ea000-7e310000	Deferred        msvfw32<elf>
  \-PE	7e2f0000-7e310000	\               msvfw32
ELF	7e310000-7e336000	Deferred        msacm32<elf>
  \-PE	7e320000-7e336000	\               msacm32
ELF	7e336000-7e374000	Deferred        avifil32<elf>
  \-PE	7e340000-7e374000	\               avifil32
ELF	7e374000-7e3e8000	Deferred        msvcrt<elf>
  \-PE	7e390000-7e3e8000	\               msvcrt
ELF	7e3e8000-7e470000	Deferred        winmm<elf>
  \-PE	7e3f0000-7e470000	\               winmm
ELF	7e562000-7e5d2000	Deferred        libglu.so.1
ELF	7e5e0000-7e5f5000	Deferred        avicap32<elf>
  \-PE	7e5f0000-7e5f5000	\               avicap32
ELF	7e5f5000-7e5fa000	Deferred        libxdmcp.so.6
ELF	7e5fa000-7e618000	Deferred        libgcc_s.so.1
ELF	7e618000-7e636000	Deferred        libxcb.so.1
ELF	7e636000-7e63a000	Deferred        libxau.so.6
ELF	7e63a000-7e63f000	Deferred        libuuid.so.1
ELF	7e63f000-7e6d0000	Deferred        libgl.so.1
ELF	7e6d0000-7e7ff000	Deferred        libx11.so.6
ELF	7e7ff000-7e81a000	Deferred        libice.so.6
ELF	7e826000-7e83d000	Deferred        glu32<elf>
  \-PE	7e830000-7e83d000	\               glu32
ELF	7e83d000-7e8e2000	Deferred        opengl32<elf>
  \-PE	7e850000-7e8e2000	\               opengl32
ELF	7e8e2000-7e9b2000	Deferred        comctl32<elf>
  \-PE	7e8f0000-7e9b2000	\               comctl32
ELF	7e9b2000-7ea14000	Deferred        shlwapi<elf>
  \-PE	7e9c0000-7ea14000	\               shlwapi
ELF	7ea14000-7ebde000	Deferred        shell32<elf>
  \-PE	7ea20000-7ebde000	\               shell32
ELF	7ebde000-7ec52000	Deferred        rpcrt4<elf>
  \-PE	7ebf0000-7ec52000	\               rpcrt4
ELF	7ec52000-7ecac000	Deferred        advapi32<elf>
  \-PE	7ec60000-7ecac000	\               advapi32
ELF	7ecac000-7ed37000	Deferred        gdi32<elf>
  \-PE	7ecc0000-7ed37000	\               gdi32
ELF	7ed37000-7ee68000	Deferred        user32<elf>
  \-PE	7ed50000-7ee68000	\               user32
ELF	7ef94000-7efa0000	Deferred        libnss_files.so.2
ELF	7efa0000-7efb7000	Deferred        libnsl.so.1
ELF	7efb7000-7efdd000	Deferred        libm.so.6
ELF	7efde000-7efee000	Deferred        libxext.so.6
ELF	7efee000-7eff7000	Deferred        libsm.so.6
ELF	f74e2000-f74e6000	Deferred        libdl.so.2
ELF	f74e6000-f762b000	Deferred        libc.so.6
ELF	f762c000-f7645000	Deferred        libpthread.so.0
ELF	f7645000-f7650000	Deferred        libnss_nis.so.2
ELF	f7660000-f7668000	Deferred        libnss_compat.so.2
ELF	f7668000-f77a3000	Deferred        libwine.so.1
ELF	f77a5000-f77c3000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 Algodoo.exe
	0000001c   15
	0000001b    0
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
00000025 Algodoo.exe
	00000028   15
	00000027    0
0000002d (D) C:\Program Files\Algodoo\Algodoo.exe
	00000030   15
	0000002f    0
	0000002e    0 <==
Backtrace:
=>0 0x7bc4b9b0 in ntdll (+0x3b9b0) (0x0032eb18)
  1 0x0037000f (0x00e3c6d8)
wine: Call from 0x7bc4b9b0 to unimplemented function SDL.dll.SDL_RWFromConstMem, aborting

```

The popup message just says that a serious error and they're sorry for the inconvenience.

Any ideas?

thanks!!


Mathieu

---

### Post by cogadh on 2010-04-25
```
wine: Call from 0x7bc4b9b0 to unimplemented function SDL.dll.SDL_RWFromConstMemwine: Call from 0x7bc4b9b0 to unimplemented function SDL.dll.SDL_RWFromConstMem
```
That would seem to explain the problem. It looks like the app is trying to do something Wine can't do yet. Are you using the latest version of Wine? If not, you might try that out to see if that function has actually been implemented.
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

