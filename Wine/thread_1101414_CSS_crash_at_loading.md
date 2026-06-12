---
title: "CSS crash at loading"
date: 2009-03-20
forum: Wine
---

### Post by Hate on 2009-03-20
I've already use the search to find the answer but I didn't find nothing...

as the title says at soon as I launch CSS at loading screen it crashes... this is the output I hope it helps...

```

wine: Unhandled page fault on read access to 0x00000000 at address 0x2c01fb2f (thread 0040), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x2c01fb2f).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:2c01fb2f ESP:0033e634 EBP:0033ff08 EFLAGS:00210257(   - 00     RIZAP1C)
 EAX:2c054d00 EBX:00000000 ECX:00000000 EDX:0d65cd08
 ESI:2c05d790 EDI:0033e67c
Stack dump:
0x0033e634:  2c05d790 2c001918 00000006 1000753b
0x0033e644:  00000003 0033e67c 100083ea 00000001
0x0033e654:  0033e6d4 100083e1 0036b090 00341960
0x0033e664:  10005cf2 00400000 0053227d 7b8b6ff4
0x0033e674:  00000000 00000000 10023c8c 06750cf0
0x0033e684:  0000000c 00000000 0000000b 06750cf0
Backtrace:
=>0 0x2c01fb2f in studiorender (+0x1fb2f) (0x0033ff08)
  1 0x7b877a30 in kernel32 (+0x57a30) (0x0033ffe8)
  2 0xb7f9ad97 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x2c01fb2f: movl	0x0(%ecx),%eax
Modules:
Module	Address			Debug info	Name (134 modules)
PE	  340000-  376000	Deferred        tier0
PE	  380000-  39e000	Deferred        vstdlib
PE	  3a0000-  3f4000	Deferred        filesystem_steam
PE	  400000-  41c000	Deferred        hl2
PE	 cf50000- cf64000	Deferred        inputsystem
PE	 d250000- d34e000	Deferred        datamodel
PE	 d460000- d49d000	Deferred        dmserializers
PE	 d4a0000- d4c5000	Deferred        datacache
PE	 d5e0000- d695000	Deferred        materialsystem
PE	 d6a0000- d6b6000	Deferred        valve_avi
PE	 d6c0000- d790000	Deferred        vguimatsurface
PE	 d790000- d805000	Deferred        vgui2
PE	 d810000- d824000	Deferred        steam_api
PE	 da50000- da79000	Deferred        stdshader_dbg
PE	 da80000- dab5000	Deferred        stdshader_dx6
PE	 dbc0000- dbcf000	Deferred        unicode
PE	10000000-10030000	Deferred        launcher
PE	20000000-205ef000	Deferred        engine
PE	26000000-26138000	Deferred        vphysics
PE	2a000000-2a0a8000	Deferred        shaderapidx9
PE	2c000000-2c3e3000	Export          studiorender
PE	30000000-302c0000	Deferred        steam
PE	60000000-60021000	Deferred        cserhelper
PE	628c0000-628d9000	Deferred        parsifal
ELF	7b800000-7b93e000	Export          kernel32<elf>
  \-PE	7b820000-7b93e000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c033000-7c080000	Deferred        dsound<elf>
  \-PE	7c040000-7c080000	\               dsound
ELF	7c080000-7c099000	Deferred        mcicda<elf>
  \-PE	7c090000-7c099000	\               mcicda
ELF	7c099000-7d540000	Deferred        fglrx_dri.so
ELF	7d630000-7d652000	Deferred        libatiadlxx.so
ELF	7dd62000-7dd71000	Deferred        libgcc_s.so.1
ELF	7dd71000-7ddfe000	Deferred        libgl.so.1
ELF	7ddfe000-7de14000	Deferred        winejoystick<elf>
  \-PE	7de00000-7de14000	\               winejoystick
ELF	7de14000-7de2a000	Deferred        psapi<elf>
  \-PE	7de20000-7de2a000	\               psapi
ELF	7de2a000-7de78000	Deferred        dbghelp<elf>
  \-PE	7de30000-7de78000	\               dbghelp
ELF	7de78000-7df9d000	Deferred        wined3d<elf>
  \-PE	7de90000-7df9d000	\               wined3d
ELF	7df9d000-7dfa0000	Deferred        libnss_mdns4.so.2
ELF	7dfa0000-7dfa6000	Deferred        libnss_dns.so.2
ELF	7dfb1000-7dfe3000	Deferred        d3d9<elf>
  \-PE	7dfc0000-7dfe3000	\               d3d9
ELF	7dfe3000-7e006000	Deferred        mpr<elf>
  \-PE	7dff0000-7e006000	\               mpr
ELF	7e006000-7e058000	Deferred        wininet<elf>
  \-PE	7e010000-7e058000	\               wininet
ELF	7e058000-7e13f000	Deferred        oleaut32<elf>
  \-PE	7e070000-7e13f000	\               oleaut32
ELF	7e13f000-7e169000	Deferred        msvfw32<elf>
  \-PE	7e150000-7e169000	\               msvfw32
ELF	7e169000-7e1a7000	Deferred        avifil32<elf>
  \-PE	7e170000-7e1a7000	\               avifil32
ELF	7e1a7000-7e1bc000	Deferred        midimap<elf>
  \-PE	7e1b0000-7e1bc000	\               midimap
ELF	7e1bc000-7e1e2000	Deferred        msacm32<elf>
  \-PE	7e1c0000-7e1e2000	\               msacm32
ELF	7e1e2000-7e1fb000	Deferred        msacm32<elf>
  \-PE	7e1f0000-7e1fb000	\               msacm32
ELF	7e1fb000-7e204000	Deferred        librt.so.1
ELF	7e204000-7e2cc000	Deferred        libasound.so.2
ELF	7e2dc000-7e313000	Deferred        winealsa<elf>
  \-PE	7e2f0000-7e313000	\               winealsa
ELF	7e313000-7e3a7000	Deferred        winmm<elf>
  \-PE	7e320000-7e3a7000	\               winmm
ELF	7e3f3000-7e426000	Deferred        uxtheme<elf>
  \-PE	7e400000-7e426000	\               uxtheme
ELF	7e426000-7e43a000	Deferred        lz32<elf>
  \-PE	7e430000-7e43a000	\               lz32
ELF	7e43a000-7e455000	Deferred        version<elf>
  \-PE	7e440000-7e455000	\               version
ELF	7e455000-7e51d000	Deferred        comctl32<elf>
  \-PE	7e460000-7e51d000	\               comctl32
ELF	7e51d000-7e57b000	Deferred        shlwapi<elf>
  \-PE	7e530000-7e57b000	\               shlwapi
ELF	7e57b000-7e708000	Deferred        shell32<elf>
  \-PE	7e590000-7e708000	\               shell32
ELF	7e708000-7e76f000	Deferred        rpcrt4<elf>
  \-PE	7e710000-7e76f000	\               rpcrt4
ELF	7e76f000-7e867000	Deferred        ole32<elf>
  \-PE	7e790000-7e867000	\               ole32
ELF	7e867000-7e87b000	Deferred        libresolv.so.2
ELF	7e87b000-7e89a000	Deferred        iphlpapi<elf>
  \-PE	7e880000-7e89a000	\               iphlpapi
ELF	7e89a000-7e8c7000	Deferred        ws2_32<elf>
  \-PE	7e8a0000-7e8c7000	\               ws2_32
ELF	7e8c7000-7e8e2000	Deferred        wsock32<elf>
  \-PE	7e8d0000-7e8e2000	\               wsock32
ELF	7e8e2000-7e8eb000	Deferred        libxcursor.so.1
ELF	7e8eb000-7e8f0000	Deferred        libxfixes.so.3
ELF	7e8f0000-7e8f4000	Deferred        libxcomposite.so.1
ELF	7e8f4000-7e8fb000	Deferred        libxrandr.so.2
ELF	7e8fb000-7e905000	Deferred        libxrender.so.1
ELF	7e905000-7e90b000	Deferred        libxxf86vm.so.1
ELF	7e90b000-7e90e000	Deferred        libxinerama.so.1
ELF	7e90e000-7e92f000	Deferred        imm32<elf>
  \-PE	7e910000-7e92f000	\               imm32
ELF	7e92f000-7e934000	Deferred        libxdmcp.so.6
ELF	7e934000-7e94d000	Deferred        libxcb.so.1
ELF	7e94d000-7e950000	Deferred        libxcb-xlib.so.0
ELF	7e950000-7e953000	Deferred        libxau.so.6
ELF	7e953000-7ea42000	Deferred        libx11.so.6
ELF	7ea42000-7ea51000	Deferred        libxext.so.6
ELF	7ea51000-7ea69000	Deferred        libice.so.6
ELF	7ea69000-7ea72000	Deferred        libsm.so.6
ELF	7ea72000-7ea75000	Deferred        libnss_mdns4_minimal.so.2
ELF	7ea82000-7eb1e000	Deferred        winex11<elf>
  \-PE	7ea90000-7eb1e000	\               winex11
ELF	7eb3a000-7eb61000	Deferred        libexpat.so.1
ELF	7eb61000-7eb8e000	Deferred        libfontconfig.so.1
ELF	7eb9e000-7ebb4000	Deferred        libz.so.1
ELF	7ebb4000-7ec2a000	Deferred        libfreetype.so.6
ELF	7ec2a000-7ec7f000	Deferred        advapi32<elf>
  \-PE	7ec40000-7ec7f000	\               advapi32
ELF	7ec7f000-7ed20000	Deferred        gdi32<elf>
  \-PE	7ec90000-7ed20000	\               gdi32
ELF	7ed20000-7ee6c000	Deferred        user32<elf>
  \-PE	7ed40000-7ee6c000	\               user32
ELF	7ee6c000-7ee78000	Deferred        libnss_files.so.2
ELF	7ee78000-7ee91000	Deferred        libnsl.so.1
ELF	7ee91000-7ee9a000	Deferred        libnss_compat.so.2
ELF	7efca000-7eff0000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7e07000-b7e0b000	Deferred        libdl.so.2
ELF	b7e0b000-b7f69000	Deferred        libc.so.6
ELF	b7f6a000-b7f83000	Deferred        libpthread.so.0
ELF	b7f93000-b80ce000	Export          libwine.so.1
ELF	b80d0000-b80ed000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000043    1
	0000003e    0
	0000003d    0
	0000003b    0
	0000003a    1
	00000039    1
	00000038    1
	00000037    1
	00000036    1
	00000035    1
	00000034    1
	00000033    1
	0000002f    0
	0000002e    0
	0000002c    1
	0000002a    0
	00000028    0
	00000027    0
	00000024    0
	00000022    0
	00000021    1
	00000020    0
	0000001f    0
	0000001e    0
	0000001d    0
	0000001c    0
	0000001b    0
	0000001a    0
	00000019    0
	00000009    0
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
0000003f (D) C:\Program Files\Steam\steamapps\darkheian\counter-strike source\hl2.exe
	00000045    0
	00000044    0
	00000042    0
	00000041    2
	00000040    0 <==
Backtrace:
=>0 0x2c01fb2f in studiorender (+0x1fb2f) (0x0033ff08)
  1 0x7b877a30 in kernel32 (+0x57a30) (0x0033ffe8)
  2 0xb7f9ad97 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
Shutting down. . .

```

:(

---

### Post by u235sentinel on 2009-03-20
Not sure if I can help but maybe with a few questions we may resolve this.

What version of Ubuntu are you running?

What version of WINE?

Are you running gnome / KDE / another desktop?

3D desktop enabled?


I'm running Ubuntu 8.04 with pretty much all the standard packages that come with it.  I've tried really hard to follow the stable lines for everything I have installed.  Which means I'm also running WINE 1.0.1.  I've turned off Compiz as it was breaking my gaming (frequently!).  I've since switched to KDE under Ubuntu (not Kubuntu btw).  It seems to be more stable for gaming for some reason (thought this could be just my experience).

Installing and playing Source games under Ubuntu has worked out well for me.  The ONLY bugging me right now is in game chat is broken.  I'd love to see that fixed someday.  

Hope this helps at least get you started...

---

### Post by Hate on 2009-03-21
sorry for not specifying those details before...

```
Running version: Ubuntu 8.10 intrepid Ibex (Gnome)   
      WIne version: 1.1.17
      Effects disabled

```

I don't know if it helps, but I'm using and ATI 9600 SE and CS 1.6 works without any problem

---

### Post by Hate on 2009-03-22
up :(

---

