---
title: "Problem starting games in Wine"
date: 2011-05-06
forum: Wine
---

### Post by randwyck on 2011-05-06
I tried to use Wine for the first time and had no luck with.
The game install just fine, but after I try to start them I get an error. It seems to me that the problem is not with the game (I tried different ones), but with graphics configuration. 
I 'm on freshly installed Natty with nVidia 9800. 
How do I fix it?
Here's what I get if I try to start Hearts of Iron 3.

```
~/.wine-hoi3/drive_c/Program Files/Paradox Interactive/Hearts of Iron III$ env WINEPREFIX=$HOME/.wine-hoi3 wine hoi3game.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32e2d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e3c4,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"quartz.dll"
err:ole:CoGetClassObject no class object {e436ebb3-524f-11ce-9f53-0020af0ba770} could be created for context 0x3
wine: Unhandled page fault on read access to 0x00000000 at address 0xd8904d (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00d8904d).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00d8904d ESP:0032f4d8 EBP:0112dfa4 EFLAGS:00010287(  R- --  I S - -P-C)
 EAX:00000000 EBX:00000000 ECX:018d8a58 EDX:00000000
 ESI:0032f508 EDI:00000010
Stack dump:
0x0032f4d8:  0198a6c8 0032f8b0 0032f9b8 00000010
0x0032f4e8:  00000020 78645c2e 6973756d 70632e63
0x0032f4f8:  7bc30070 0000000d 0000000f 018f5c98
0x0032f508:  01196000 01131f48 01904058 00000000
0x0032f518:  00000000 0032f514 0032f518 00000000
0x0032f528:  00000000 0032f524 0032f528 00000000
Backtrace:
=>0 0x00d8904d in hoi3game (+0x98904d) (0x0112dfa4)
  1 0x00000000 (0x0041b17b)
  2 0x040be900 (0x0429f0e9)
0x00d8904d: movl	0x0(%eax),%edx
Modules:
Module	Address			Debug info	Name (83 modules)
PE	  330000-  336000	Deferred        lua51
PE	  340000-  369000	Deferred        lua5.1
PE	  370000-  383000	Deferred        zlib1
PE	  400000- 17a4000	Export          hoi3game
PE	10000000-1041a000	Deferred        d3dx9_41
PE	72880000-72890000	Deferred        vcomp
PE	78130000-781cb000	Deferred        msvcr80
ELF	7a0de000-7b800000	Deferred        libnvidia-glcore.so.270.41.06
ELF	7b800000-7b991000	Deferred        kernel32<elf>
  \-PE	7b810000-7b991000	\               kernel32
ELF	7bc00000-7bcba000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcba000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e0f3000-7e1c1000	Deferred        libgl.so.1
ELF	7e1f8000-7e1fe000	Deferred        libxfixes.so.3
ELF	7e1fe000-7e208000	Deferred        libxcursor.so.1
ELF	7e208000-7e217000	Deferred        libxi.so.6
ELF	7e217000-7e21b000	Deferred        libxcomposite.so.1
ELF	7e21b000-7e223000	Deferred        libxrandr.so.2
ELF	7e223000-7e22d000	Deferred        libxrender.so.1
ELF	7e22d000-7e233000	Deferred        libxxf86vm.so.1
ELF	7e233000-7e237000	Deferred        libxinerama.so.1
ELF	7e237000-7e258000	Deferred        imm32<elf>
  \-PE	7e240000-7e258000	\               imm32
ELF	7e258000-7e25e000	Deferred        libxdmcp.so.6
ELF	7e25e000-7e262000	Deferred        libxau.so.6
ELF	7e262000-7e27b000	Deferred        libxcb.so.1
ELF	7e27b000-7e280000	Deferred        libuuid.so.1
ELF	7e280000-7e39b000	Deferred        libx11.so.6
ELF	7e39b000-7e3aa000	Deferred        libxext.so.6
ELF	7e3aa000-7e3c2000	Deferred        libice.so.6
ELF	7e3c2000-7e3ca000	Deferred        libsm.so.6
ELF	7e3ce000-7e3d0000	Deferred        libnvidia-tls.so.270.41.06
ELF	7e3eb000-7e496000	Deferred        winex11<elf>
  \-PE	7e400000-7e496000	\               winex11
ELF	7e4d3000-7e4fd000	Deferred        libexpat.so.1
ELF	7e4fd000-7e52c000	Deferred        libfontconfig.so.1
ELF	7e52c000-7e541000	Deferred        libz.so.1
ELF	7e541000-7e5c7000	Deferred        libfreetype.so.6
ELF	7e5c7000-7e5fe000	Deferred        libncurses.so.5
ELF	7e61f000-7e691000	Deferred        rpcrt4<elf>
  \-PE	7e630000-7e691000	\               rpcrt4
ELF	7e691000-7e793000	Deferred        ole32<elf>
  \-PE	7e6b0000-7e793000	\               ole32
ELF	7e793000-7e7cc000	Deferred        dinput<elf>
  \-PE	7e7a0000-7e7cc000	\               dinput
ELF	7e7cc000-7e7e7000	Deferred        dinput8<elf>
  \-PE	7e7d0000-7e7e7000	\               dinput8
ELF	7e7e7000-7e844000	Deferred        ddraw<elf>
  \-PE	7e7f0000-7e844000	\               ddraw
ELF	7e844000-7e874000	Deferred        ws2_32<elf>
  \-PE	7e850000-7e874000	\               ws2_32
ELF	7e874000-7e90c000	Deferred        winmm<elf>
  \-PE	7e880000-7e90c000	\               winmm
ELF	7e90c000-7e954000	Deferred        dsound<elf>
  \-PE	7e910000-7e954000	\               dsound
ELF	7e954000-7ea82000	Deferred        wined3d<elf>
  \-PE	7e960000-7ea82000	\               wined3d
ELF	7ea82000-7eab8000	Deferred        d3d9<elf>
  \-PE	7ea90000-7eab8000	\               d3d9
ELF	7eab8000-7eace000	Deferred        psapi<elf>
  \-PE	7eac0000-7eace000	\               psapi
ELF	7eace000-7ec03000	Deferred        user32<elf>
  \-PE	7eae0000-7ec03000	\               user32
ELF	7ec03000-7ec5f000	Deferred        advapi32<elf>
  \-PE	7ec10000-7ec5f000	\               advapi32
ELF	7ec5f000-7ecf0000	Deferred        gdi32<elf>
  \-PE	7ec70000-7ecf0000	\               gdi32
ELF	7ecf0000-7ed83000	Deferred        msvcrt<elf>
  \-PE	7ed00000-7ed83000	\               msvcrt
ELF	7ef83000-7ef8f000	Deferred        libnss_files.so.2
ELF	7ef8f000-7ef9a000	Deferred        libnss_nis.so.2
ELF	7ef9a000-7efb1000	Deferred        libnsl.so.1
ELF	7efb1000-7efb9000	Deferred        libnss_compat.so.2
ELF	7efb9000-7efdf000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f7475000-f7479000	Deferred        libdl.so.2
ELF	f7479000-f75d6000	Deferred        libc.so.6
ELF	f75d6000-f75ef000	Deferred        libpthread.so.0
ELF	f7610000-f7751000	Dwarf           libwine.so.1
ELF	f7753000-f7771000	Deferred        ld-linux.so.2
ELF	f7771000-f7772000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Paradox Interactive\Hearts of Iron III\hoi3game.exe
	00000009    0 <==
0000000e services.exe
	00000024    0
	00000020    0
	0000001d    0
	00000017    0
	00000016    0
	00000010    0
	0000000f    0
00000011 mscorsvw.exe
	00000019    0
	00000018    0
	00000015    0
	00000012    0
00000013 explorer.exe
	00000014    0
0000001a winedevice.exe
	0000001f    0
	0000001e    0
	0000001c    0
	0000001b    0
00000021 plugplay.exe
	00000025    0
	00000023    0
	00000022    0
Backtrace:
=>0 0x00d8904d in hoi3game (+0x98904d) (0x0112dfa4)
  1 0x00000000 (0x0041b17b)
  2 0x040be900 (0x0429f0e9)

```

---

### Post by ajgreeny on 2011-05-06
How are you trying to start the game, using a terminal or a shortcut in the menu?

---

### Post by randwyck on 2011-05-06
> **ajgreeny said:**
> How are you trying to start the game, using a terminal or a shortcut in the menu?I tried both ways, the result is the same, except when starting from terminal I get this list of errors.

---

