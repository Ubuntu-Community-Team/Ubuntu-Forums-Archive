---
title: "Morrowind + Hardy 64-bit + Wine = Nothing?"
date: 2009-01-02
forum: Wine
---

### Post by alphaakenny1 on 2009-01-02
I just installed Morrowind through wine on a 64 bit Hardy Heron install, then when I run the program I get the following:

> 
fixme:win:EnumDisplayDevicesW ((null),0,0x32f118,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
@ directx.c / 3554
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x19f9b0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x19f9b0) : stub
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(1024,76
wine: Unhandled page fault on execute access to 0x7c0d1d98 at address 0x7c0d1d98 (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x7c0d1d98 in 32-bit code (0x7c0d1d9.
Register dump:
CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
EIP:7c0d1d98 ESP:0032f624 EBP:0032f670 EFLAGS:00010206( - 00 - RIP1)
EAX:0032f654 EBX:7e999c84 ECX:0019f9b0 EDX:7e99a920
ESI:00000000 EDI:7e987487
Stack dump:
0x0032f624: 7e929449 00008775 0032f654 00000000
0x0032f634: 00000002 00000002 00000000 00000001
0x0032f644: 7e9298c1 7e987487 3f800000 7e987487
0x0032f654: 3f000000 00000000 00000000 3f000000
0x0032f664: 7e999c84 00000006 00000043 0032f6f0
0x0032f674: 7e8cd8dc 000000d8 0019ff30 001ae678
Backtrace:
=>1 0x7c0d1d98 (0x0032f670)
2 0x7e8cd8dc ActivateContext+0x4fc() in wined3d (0x0032f6f0)
3 0x7e90269b drawPrimitive+0x17b() in wined3d (0x0032fa00)
4 0x7e8d9fac in wined3d (+0x29fac) (0x0032fa40)
5 0x7e9b38cf in d3d8 (+0x138cf) (0x0032fa70)
6 0x0063d167 in morrowind (+0x23d167) (0x0016226
7 0x00199ef0 (0x00738634)
8 0x004ed940 in morrowind (+0xed940) (0x004171c0)
9 0x00000018 (0xe8f18b56)
0x7c0d1d98: movl 0x7e2b9960,%eax
Modules:
Module Address Debug info Name (87 modules)
PE 400000- 7d4000 Export morrowind
PE 30000000-3006e000 Deferred binkw32
PE 780c0000-78121000 Deferred msvcp60
ELF 7b800000-7b92d000 Deferred kernel32<elf>
\-PE 7b820000-7b92d000 \ kernel32
ELF 7bc00000-7bca4000 Deferred ntdll<elf>
\-PE 7bc10000-7bca4000 \ ntdll
ELF 7bf00000-7bf03000 Deferred <wine-loader>
ELF 7d226000-7d22f000 Deferred librt.so.1
ELF 7d22f000-7e23a000 Deferred fglrx_dri.so
ELF 7e23a000-7e245000 Deferred libgcc_s.so.1
ELF 7e245000-7e2bf000 Export libgl.so.1
ELF 7e2d7000-7e30a000 Deferred uxtheme<elf>
\-PE 7e2e0000-7e30a000 \ uxtheme
ELF 7e31d000-7e343000 Deferred msacm32<elf>
\-PE 7e320000-7e343000 \ msacm32
ELF 7e343000-7e35a000 Deferred msacm32<elf>
\-PE 7e350000-7e35a000 \ msacm32
ELF 7e35a000-7e41d000 Deferred libasound.so.2
ELF 7e433000-7e469000 Deferred winealsa<elf>
\-PE 7e440000-7e469000 \ winealsa
ELF 7e469000-7e472000 Deferred libxcursor.so.1
ELF 7e472000-7e477000 Deferred libxfixes.so.3
ELF 7e477000-7e47a000 Deferred libxcomposite.so.1
ELF 7e47a000-7e480000 Deferred libxrandr.so.2
ELF 7e480000-7e488000 Deferred libxrender.so.1
ELF 7e488000-7e4a8000 Deferred imm32<elf>
\-PE 7e490000-7e4a8000 \ imm32
ELF 7e4a8000-7e4ad000 Deferred libxdmcp.so.6
ELF 7e4ad000-7e4c5000 Deferred libxcb.so.1
ELF 7e4c5000-7e5ac000 Deferred libx11.so.6
ELF 7e5ac000-7e5ba000 Deferred libxext.so.6
ELF 7e5ba000-7e5bf000 Deferred libxxf86vm.so.1
ELF 7e5bf000-7e5d3000 Deferred midimap<elf>
\-PE 7e5c0000-7e5d3000 \ midimap
ELF 7e5d5000-7e66c000 Deferred winex11<elf>
\-PE 7e5e0000-7e66c000 \ winex11
ELF 7e68c000-7e6ad000 Deferred libexpat.so.1
ELF 7e6ad000-7e6d7000 Deferred libfontconfig.so.1
ELF 7e6d7000-7e6ec000 Deferred libz.so.1
ELF 7e6ec000-7e75c000 Deferred libfreetype.so.6
ELF 7e75c000-7e75f000 Deferred libxinerama.so.1
ELF 7e772000-7e831000 Deferred comctl32<elf>
\-PE 7e780000-7e831000 \ comctl32
ELF 7e831000-7e89b000 Deferred msvcrt<elf>
\-PE 7e840000-7e89b000 \ msvcrt
ELF 7e89b000-7e99e000 Export wined3d<elf>
\-PE 7e8b0000-7e99e000 \ wined3d
ELF 7e99e000-7e9c9000 Export d3d8<elf>
\-PE 7e9a0000-7e9c9000 \ d3d8
ELF 7e9c9000-7ea13000 Deferred dsound<elf>
\-PE 7e9d0000-7ea13000 \ dsound
ELF 7ea13000-7ea4a000 Deferred dinput<elf>
\-PE 7ea20000-7ea4a000 \ dinput
ELF 7ea4a000-7ea62000 Deferred dinput8<elf>
\-PE 7ea50000-7ea62000 \ dinput8
ELF 7ea62000-7ea7b000 Deferred version<elf>
\-PE 7ea70000-7ea7b000 \ version
ELF 7ea7b000-7eb0d000 Deferred winmm<elf>
\-PE 7ea90000-7eb0d000 \ winmm
ELF 7eb0d000-7eb20000 Deferred libresolv.so.2
ELF 7eb20000-7eb22000 Deferred libxcb-xlib.so.0
ELF 7eb22000-7eb36000 Deferred lz32<elf>
\-PE 7eb30000-7eb36000 \ lz32
ELF 7eb36000-7eb54000 Deferred iphlpapi<elf>
\-PE 7eb40000-7eb54000 \ iphlpapi
ELF 7eb54000-7ebb5000 Deferred rpcrt4<elf>
\-PE 7eb60000-7ebb5000 \ rpcrt4
ELF 7ebb5000-7ec59000 Deferred ole32<elf>
\-PE 7ebc0000-7ec59000 \ ole32
ELF 7ec59000-7ecab000 Deferred advapi32<elf>
\-PE 7ec70000-7ecab000 \ advapi32
ELF 7ecab000-7ed46000 Deferred gdi32<elf>
\-PE 7ecc0000-7ed46000 \ gdi32
ELF 7ed46000-7ee8d000 Deferred user32<elf>
\-PE 7ed60000-7ee8d000 \ user32
ELF 7efad000-7efc5000 Deferred libnsl.so.1
ELF 7efc5000-7efea000 Deferred libm.so.6
ELF 7efeb000-7eff6000 Deferred libnss_files.so.2
ELF 7eff6000-7f000000 Deferred libnss_nis.so.2
ELF f7c51000-f7c5a000 Deferred libnss_compat.so.2
ELF f7c5b000-f7c5f000 Deferred libdl.so.2
ELF f7c5f000-f7dae000 Deferred libc.so.6
ELF f7daf000-f7dc7000 Deferred libpthread.so.0
ELF f7dc8000-f7dcb000 Deferred libxau.so.6
ELF f7ddd000-f7f13000 Deferred libwine.so.1
ELF f7f15000-f7f34000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
00000008 (D) C:\Program Files\Bethesda Softworks\Morrowind\Morrowind.exe
0000001b 0
0000001a 0
00000019 15
00000018 0
00000009 0 <==
0000000c
00000013 0
00000012 0
0000000e 0
0000000d 0
0000000f
00000015 0
00000014 0
00000011 0
00000010 0
00000016
00000017 0
Backtrace:
=>1 0x7c0d1d98 (0x0032f670)
2 0x7e8cd8dc ActivateContext+0x4fc() in wined3d (0x0032f6f0)
3 0x7e90269b drawPrimitive+0x17b() in wined3d (0x0032fa00)
4 0x7e8d9fac in wined3d (+0x29fac) (0x0032fa40)
5 0x7e9b38cf in d3d8 (+0x138cf) (0x0032fa70)
6 0x0063d167 in morrowind (+0x23d167) (0x0016226
7 0x00199ef0 (0x00738634)
8 0x004ed940 in morrowind (+0xed940) (0x004171c0)
9 0x00000018 (0xe8f18b56)


When wine starts the program it shows nothing, it plays a sound for a second, then once again...nothing. I've looked at winehq the problems they have are different. Any help would be appreciated.

---

### Post by itix on 2009-01-03
I thought I actually might be of help here since I've actually run Morrowind on 64-bit wine in Hardy, but apparantly not so.

Have you tried emulating it as a desktop??

BTW; If you are able to get it working and need to remap the keys, don't hesitate to contact me. I know a super haxx way to remap the keys ;)

---

### Post by JEV2 on 2009-01-04
not sure if same, but, on the graphics option on wine, turn off pixel shader.

click on auto detect drives(drive options), select all boxes on sound options.

and that's all i can think of,lol.

---

### Post by alphaakenny1 on 2009-01-04
Thanks guys but still no lucky, I've tried everything from the ubuntu forums, fedora forums, and linux forums with no luck.  If any body has any kind of idea please help me.

---

### Post by JEV2 on 2009-01-04
well, you probably know, how it was designed for 32-bit...(it didn't work on my 24-bit computer,lol).but works on this laptop.

have you gotten the drivers needed.
serious sam would lag completely on a quad core, after i installed the video drive it worked flawlessly.

my brothers was a nvidia gforce ???, but using the drive 1.77(wait or was it 177,lol), the 178 is out on windows not sure if on linux.

if there's a notification on the top right, when highlighted(mouse arrow put over it) that mentions drivers then that may be what is wrong.

try to switch the platform, like xp to nt or 98,etc.,lol.

edit:you may also want to switch versions.(you know upgrade wine version or downgrade).

---

### Post by JEV2 on 2009-01-04
[http://prdownloads.sourceforge.net/wine/wine-1.1.12.tar.bz2](http://prdownloads.sourceforge.net/wine/wine-1.1.12.tar.bz2)

guess what i found,lol.new wine update something 64-bit updates as well.

here the link for info,released 2days ago, not sure if this is what your using though.
[http://www.linuxgames.com/archives/11319](http://www.linuxgames.com/archives/11319)

edit:sorry for not making it a link, for some reason i can't...probably that one restart to complete update thing,lol.

---

