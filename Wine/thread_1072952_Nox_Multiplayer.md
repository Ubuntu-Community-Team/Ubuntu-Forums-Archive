---
title: "Nox Multiplayer"
date: 2009-02-17
forum: Wine
---

### Post by Noxxan on 2009-02-17
I'm trying to get nox working online. The game runs fine in singelplayer and on LAN games but when i'm trying to go online it crashes and i have no idea why.

Wine version: wine-1.1.14

```
wine explorer /desktop=1040x768 "C:\Westwood\Nox\Nox.EXE"
fixme:win:EnumDisplayDevicesW ((null),0,0x33f104,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(640,480)
fixme:imm:ImmReleaseContext (0x10028, 0x124c50): stub
fixme:winsock:WSACancelAsyncRequest (0xdeae),stub
wine: Unhandled page fault on write access to 0x00000080 at address 0x7ede8e72 (thread 0019), starting debugger...
Unhandled exception: page fault on write access to 0x00000080 in 32-bit code (0x7ede8e72).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ede8e72 ESP:0033f6a4 EBP:0033f71c EFLAGS:00010216(   - 00      -RIAP1)
 EAX:00000043 EBX:7ee06ff4 ECX:00002500 EDX:003c5054
 ESI:01165c60 EDI:00000080
Stack dump:
0x0033f6a4:  7bc94ff4 000000e8 0033f704 0033f740
0x0033f6b4:  7bc51822 0033f6c4 00000000 ffffffff
0x0033f6c4:  0033f6e4 00000000 0033f73c 003c5054
0x0033f6d4:  00000400 00000080 00000000 00000000
0x0033f6e4:  00000000 00000000 00000000 00000000
0x0033f6f4:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x7ede8e72 in user32 (+0xb8e72) (0x0033f71c)
  1 0x7ede9170 wsprintfA+0x20() in user32 (0x0033f72c)
  2 0x003a8d86 in wolapi (+0x8d86) (0x0033f904)
  3 0x003a31f3 in wolapi (+0x31f3) (0x7b872eb0)
  4 0xfb4c0ee8 (0x53e58955)
  5 0x00000000 (0x00000000)
0x7ede8e72: movb	%al,0x0(%edi)
Modules:
Module	Address			Debug info	Name (101 modules)
PE	  3a0000-  3d7000	Export          wolapi
PE	  400000-  980000	Deferred        game
PE	21000000-21056000	Deferred        mss32
ELF	7b47d000-7b569000	Deferred        oleaut32<elf>
  \-PE	7b490000-7b569000	\               oleaut32
ELF	7b800000-7b940000	Deferred        kernel32<elf>
  \-PE	7b820000-7b940000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c146000-7cebd000	Deferred        libglcore.so.1
ELF	7d8f8000-7d907000	Deferred        libgcc_s.so.1
ELF	7d917000-7d92e000	Deferred        snmpapi<elf>
  \-PE	7d920000-7d92e000	\               snmpapi
ELF	7d92e000-7d944000	Deferred        winejoystick<elf>
  \-PE	7d930000-7d944000	\               winejoystick
ELF	7de7c000-7df1f000	Deferred        libgl.so.1
ELF	7df1f000-7e042000	Deferred        wined3d<elf>
  \-PE	7df30000-7e042000	\               wined3d
ELF	7e042000-7e057000	Deferred        midimap<elf>
  \-PE	7e050000-7e057000	\               midimap
ELF	7e057000-7e080000	Deferred        msacm32<elf>
  \-PE	7e060000-7e080000	\               msacm32
ELF	7e080000-7e099000	Deferred        msacm32<elf>
  \-PE	7e090000-7e099000	\               msacm32
ELF	7e099000-7e0e9000	Deferred        libpulse.so.0
ELF	7e0eb000-7e0f1000	Deferred        libnss_dns.so.2
ELF	7e0f1000-7e0f4000	Deferred        libnss_mdns4_minimal.so.2
ELF	7e0f9000-7e102000	Deferred        librt.so.1
ELF	7e102000-7e1ca000	Deferred        libasound.so.2
ELF	7e1d3000-7e1da000	Deferred        libasound_module_pcm_pulse.so
ELF	7e1da000-7e211000	Deferred        winealsa<elf>
  \-PE	7e1e0000-7e211000	\               winealsa
ELF	7e25d000-7e290000	Deferred        uxtheme<elf>
  \-PE	7e260000-7e290000	\               uxtheme
ELF	7e290000-7e299000	Deferred        libxcursor.so.1
ELF	7e299000-7e29e000	Deferred        libxfixes.so.3
ELF	7e29e000-7e2a2000	Deferred        libxcomposite.so.1
ELF	7e2a2000-7e2a9000	Deferred        libxrandr.so.2
ELF	7e2a9000-7e2b3000	Deferred        libxrender.so.1
ELF	7e2b3000-7e2b9000	Deferred        libxxf86vm.so.1
ELF	7e2b9000-7e2be000	Deferred        libxdmcp.so.6
ELF	7e2be000-7e2d7000	Deferred        libxcb.so.1
ELF	7e2d7000-7e3c6000	Deferred        libx11.so.6
ELF	7e3c6000-7e3d5000	Deferred        libxext.so.6
ELF	7e3d5000-7e3ed000	Deferred        libice.so.6
ELF	7e3ed000-7e3f6000	Deferred        libsm.so.6
ELF	7e3f6000-7e3f8000	Deferred        libnvidia-tls.so.1
ELF	7e402000-7e406000	Deferred        libcap.so.1
ELF	7e406000-7e4a2000	Deferred        winex11<elf>
  \-PE	7e410000-7e4a2000	\               winex11
ELF	7e4f5000-7e51c000	Deferred        libexpat.so.1
ELF	7e51c000-7e549000	Deferred        libfontconfig.so.1
ELF	7e549000-7e54c000	Deferred        libxinerama.so.1
ELF	7e559000-7e56f000	Deferred        libz.so.1
ELF	7e56f000-7e5e5000	Deferred        libfreetype.so.6
ELF	7e5e5000-7e606000	Deferred        imm32<elf>
  \-PE	7e5f0000-7e606000	\               imm32
ELF	7e606000-7e61a000	Deferred        libresolv.so.2
ELF	7e61a000-7e63a000	Deferred        iphlpapi<elf>
  \-PE	7e620000-7e63a000	\               iphlpapi
ELF	7e63a000-7e667000	Deferred        ws2_32<elf>
  \-PE	7e640000-7e667000	\               ws2_32
ELF	7e667000-7e682000	Deferred        wsock32<elf>
  \-PE	7e670000-7e682000	\               wsock32
ELF	7e682000-7e6bb000	Deferred        dinput<elf>
  \-PE	7e690000-7e6bb000	\               dinput
ELF	7e6bb000-7e708000	Deferred        dsound<elf>
  \-PE	7e6c0000-7e708000	\               dsound
ELF	7e708000-7e760000	Deferred        ddraw<elf>
  \-PE	7e710000-7e760000	\               ddraw
ELF	7e760000-7e7f4000	Deferred        winmm<elf>
  \-PE	7e770000-7e7f4000	\               winmm
ELF	7e7f4000-7e85b000	Deferred        rpcrt4<elf>
  \-PE	7e800000-7e85b000	\               rpcrt4
ELF	7e85b000-7e96d000	Deferred        ole32<elf>
  \-PE	7e880000-7e96d000	\               ole32
ELF	7e96d000-7ea34000	Deferred        comctl32<elf>
  \-PE	7e980000-7ea34000	\               comctl32
ELF	7ea34000-7ea92000	Deferred        shlwapi<elf>
  \-PE	7ea40000-7ea92000	\               shlwapi
ELF	7ea92000-7ec1c000	Deferred        shell32<elf>
  \-PE	7eaa0000-7ec1c000	\               shell32
ELF	7ec1c000-7ec71000	Deferred        advapi32<elf>
  \-PE	7ec30000-7ec71000	\               advapi32
ELF	7ec71000-7ed12000	Deferred        gdi32<elf>
  \-PE	7ec80000-7ed12000	\               gdi32
ELF	7ed12000-7ee61000	Export          user32<elf>
  \-PE	7ed30000-7ee61000	\               user32
ELF	7ee61000-7ee6d000	Deferred        libnss_files.so.2
ELF	7ee6d000-7ee78000	Deferred        libnss_nis.so.2
ELF	7ee78000-7ee91000	Deferred        libnsl.so.1
ELF	7ee91000-7ee9a000	Deferred        libnss_compat.so.2
ELF	7ee9a000-7ee9d000	Deferred        libxcb-xlib.so.0
ELF	7ee9d000-7eea0000	Deferred        libxau.so.6
ELF	7efca000-7eff0000	Deferred        libm.so.6
ELF	b7d34000-b7d38000	Deferred        libdl.so.2
ELF	b7d38000-b7e96000	Deferred        libc.so.6
ELF	b7e97000-b7eb0000	Deferred        libpthread.so.0
ELF	b7ec0000-b7ffb000	Deferred        libwine.so.1
ELF	b7ffd000-b801a000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
00000018 (D) C:\Westwood\Nox\GAME.EXE
	00000024    0
	00000023    0
	00000022    0
	00000021    0
	00000020    0
	0000001f    0
	0000001e    0
	0000001d    0
	0000001c    0
	0000001b    0
	0000001a    0
	00000019    0 <==
Backtrace:
=>0 0x7ede8e72 in user32 (+0xb8e72) (0x0033f71c)
  1 0x7ede9170 wsprintfA+0x20() in user32 (0x0033f72c)
  2 0x003a8d86 in wolapi (+0x8d86) (0x0033f904)
  3 0x003a31f3 in wolapi (+0x31f3) (0x7b872eb0)
  4 0xfb4c0ee8 (0x53e58955)
  5 0x00000000 (0x00000000)
```

---

### Post by Tak11 on 2009-08-01
do you have westwood online installed?

---

### Post by Atagad on 2010-07-25
i dunno about the multiplayer, but i have a problem running nox beyond 30 seconds...

the opening movie and the music play, but its a little bit delayed;
does anyone know what the wine settings are for nox?

right now i have it emulating a virtual desk top and using the OSS drivers for the audio.

---

### Post by Tak11 on 2010-07-25
> **Atagad said:**
> i dunno about the multiplayer, but i have a problem running nox beyond 30 seconds...

the opening movie and the music play, but its a little bit delayed;
does anyone know what the wine settings are for nox?

right now i have it emulating a virtual desk top and using the OSS drivers for the audio.

you can run it perfectly in wine, you just need all of the files, which you have to go searching to find them.

---

