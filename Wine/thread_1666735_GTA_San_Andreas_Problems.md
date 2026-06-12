---
title: "GTA San Andreas Problems"
date: 2011-01-14
forum: Wine
---

### Post by iFuzo on 2011-01-14
Ok so I am trying to run the game but it never opens the graphical part. It enlarges my monitor size from 1440/900 to 800/600 aswell. If I press arrow key up and down I can hear sound of gta just its not showing like the menu or anything. Below I posted my wine log when running.

```
liam@l00nix:~/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas$ wine gta_sa.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x177f494,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x177f484,0x00000000), stub!
fixme:mixer:ALSA_MixerInit No master control found on HD-Audio Generic, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x12af48,0x1364c8): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x177f10c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x177f5a4,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
wine: Unhandled page fault on read access to 0x00000000 at address 0x7480db (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x007480db).
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 088d8601 in module L"gta_sa"
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:007480db ESP:0177efe4 EBP:00000000 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:00000001 ECX:00747eb0 EDX:0000001c
 ESI:00000000 EDI:00000002
Stack dump:
0x0177efe4:  0003004a 0177f5b0 0177f05c 7ec9cff4
0x0177eff4:  00000000 00000000 00000000 00000000
0x0177f004:  00000000 00000000 00000000 00000000
0x0177f014:  00000000 00000000 00000000 00000000
0x0177f024:  00000000 00000000 00000000 7ec7dc8a
0x0177f034:  0003004a 0000001c 00000000 00000000
Backtrace:
0x007480db: movl	0x0(%eax),%ecx
Modules:
Module	Address			Debug info	Name (114 modules)
PE	  230000-  239000	Deferred        ogg
PE	  240000-  348000	Deferred        vorbis
PE	  350000-  380000	Deferred        eax
PE	  400000- 1577000	Export          gta_sa
PE	10000000-10011000	Deferred        vorbisfile
ELF	79c9c000-7b800000	Deferred        fglrx_dri.so
ELF	7b800000-7b971000	Deferred        kernel32<elf>
  \-PE	7b810000-7b971000	\               kernel32
ELF	7bc00000-7bcb7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7bf9f000-7c000000	Deferred        shlwapi<elf>
  \-PE	7bfb0000-7c000000	\               shlwapi
ELF	7c009000-7c02b000	Deferred        devenum<elf>
  \-PE	7c010000-7c02b000	\               devenum
ELF	7c02b000-7c05f000	Deferred        uxtheme<elf>
  \-PE	7c030000-7c05f000	\               uxtheme
ELF	7c05f000-7c146000	Deferred        oleaut32<elf>
  \-PE	7c070000-7c146000	\               oleaut32
ELF	7c146000-7c230000	Deferred        comctl32<elf>
  \-PE	7c150000-7c230000	\               comctl32
ELF	7c230000-7c2e3000	Deferred        quartz<elf>
  \-PE	7c240000-7c2e3000	\               quartz
ELF	7cc41000-7cc56000	Deferred        avicap32<elf>
  \-PE	7cc50000-7cc56000	\               avicap32
ELF	7cc56000-7cc7d000	Deferred        msvfw32<elf>
  \-PE	7cc60000-7cc7d000	\               msvfw32
ELF	7cd7d000-7cdb1000	Deferred        d3d9<elf>
  \-PE	7cd80000-7cdb1000	\               d3d9
ELF	7cdb1000-7cdea000	Deferred        dinput<elf>
  \-PE	7cdc0000-7cdea000	\               dinput
ELF	7cdea000-7ce05000	Deferred        dinput8<elf>
  \-PE	7cdf0000-7ce05000	\               dinput8
ELF	7ce05000-7ce1b000	Deferred        midimap<elf>
  \-PE	7ce10000-7ce1b000	\               midimap
ELF	7ce1b000-7ce41000	Deferred        msacm32<elf>
  \-PE	7ce20000-7ce41000	\               msacm32
ELF	7d642000-7d649000	Deferred        libogg.so.0
ELF	7d649000-7d671000	Deferred        libvorbis.so.0
ELF	7d671000-7d7e9000	Deferred        libvorbisenc.so.2
ELF	7d7e9000-7d835000	Deferred        libflac.so.8
ELF	7d835000-7d871000	Deferred        libdbus-1.so.3
ELF	7d871000-7d8d9000	Deferred        libsndfile.so.1
ELF	7d8d9000-7d8e2000	Deferred        libwrap.so.0
ELF	7d8e2000-7d8f0000	Deferred        libxi.so.6
ELF	7d8f0000-7d93a000	Deferred        libpulsecommon-0.9.21.so
ELF	7d93a000-7d97c000	Deferred        libpulse.so.0
ELF	7d97c000-7da42000	Deferred        libasound.so.2
ELF	7da42000-7da79000	Deferred        winealsa<elf>
  \-PE	7da50000-7da79000	\               winealsa
ELF	7da79000-7dac1000	Deferred        dsound<elf>
  \-PE	7da80000-7dac1000	\               dsound
ELF	7db81000-7dbb3000	Deferred        libatiadlxx.so
ELF	7dbb5000-7dbce000	Deferred        msacm32<elf>
  \-PE	7dbc0000-7dbce000	\               msacm32
ELF	7e2ee000-7e2f7000	Deferred        librt.so.1
ELF	7e2f7000-7e313000	Deferred        libgcc_s.so.1
ELF	7e313000-7e31b000	Deferred        libatiuki.so.1
ELF	7e31b000-7e3df000	Deferred        libgl.so.1
ELF	7e3df000-7e3e5000	Deferred        libasound_module_pcm_pulse.so
ELF	7e3e5000-7e3ea000	Deferred        libxcb-atom.so.1
ELF	7e3ea000-7e3f0000	Deferred        libxtst.so.6
ELF	7e3f0000-7e3f3000	Deferred        libx11-xcb.so.1
ELF	7e410000-7e548000	Deferred        wined3d<elf>
  \-PE	7e420000-7e548000	\               wined3d
ELF	7e548000-7e5a0000	Deferred        ddraw<elf>
  \-PE	7e550000-7e5a0000	\               ddraw
ELF	7e5a0000-7e5aa000	Deferred        libxcursor.so.1
ELF	7e5aa000-7e5b0000	Deferred        libxfixes.so.3
ELF	7e5b0000-7e5b4000	Deferred        libxcomposite.so.1
ELF	7e5b4000-7e5bc000	Deferred        libxrandr.so.2
ELF	7e5bc000-7e5c6000	Deferred        libxrender.so.1
ELF	7e5c6000-7e5cc000	Deferred        libxxf86vm.so.1
ELF	7e5cc000-7e5d0000	Deferred        libxinerama.so.1
ELF	7e5d0000-7e5f1000	Deferred        imm32<elf>
  \-PE	7e5e0000-7e5f1000	\               imm32
ELF	7e5f1000-7e5f7000	Deferred        libxdmcp.so.6
ELF	7e5f7000-7e5fb000	Deferred        libxau.so.6
ELF	7e5fb000-7e615000	Deferred        libxcb.so.1
ELF	7e615000-7e61a000	Deferred        libuuid.so.1
ELF	7e61a000-7e737000	Deferred        libx11.so.6
ELF	7e737000-7e747000	Deferred        libxext.so.6
ELF	7e747000-7e760000	Deferred        libice.so.6
ELF	7e760000-7e769000	Deferred        libsm.so.6
ELF	7e784000-7e825000	Deferred        winex11<elf>
  \-PE	7e790000-7e825000	\               winex11
ELF	7e84f000-7e876000	Deferred        libexpat.so.1
ELF	7e876000-7e8a6000	Deferred        libfontconfig.so.1
ELF	7e8a6000-7e8bb000	Deferred        libz.so.1
ELF	7e8bb000-7e932000	Deferred        libfreetype.so.6
ELF	7e94d000-7e9c0000	Deferred        rpcrt4<elf>
  \-PE	7e960000-7e9c0000	\               rpcrt4
ELF	7e9c0000-7eabe000	Deferred        ole32<elf>
  \-PE	7e9e0000-7eabe000	\               ole32
ELF	7eabe000-7eaeb000	Deferred        ws2_32<elf>
  \-PE	7ead0000-7eaeb000	\               ws2_32
ELF	7eaeb000-7eb45000	Deferred        advapi32<elf>
  \-PE	7eb00000-7eb45000	\               advapi32
ELF	7eb45000-7ebd0000	Deferred        gdi32<elf>
  \-PE	7eb50000-7ebd0000	\               gdi32
ELF	7ebd0000-7ed00000	Deferred        user32<elf>
  \-PE	7ebe0000-7ed00000	\               user32
ELF	7ed00000-7ed91000	Deferred        winmm<elf>
  \-PE	7ed10000-7ed91000	\               winmm
ELF	7ef91000-7ef9d000	Deferred        libnss_files.so.2
ELF	7ef9d000-7efa8000	Deferred        libnss_nis.so.2
ELF	7efa8000-7efbf000	Deferred        libnsl.so.1
ELF	7efbf000-7efe5000	Deferred        libm.so.6
ELF	f74f5000-f74f9000	Deferred        libdl.so.2
ELF	f74f9000-f7654000	Deferred        libc.so.6
ELF	f7655000-f766e000	Deferred        libpthread.so.0
ELF	f7681000-f7689000	Deferred        libnss_compat.so.2
ELF	f7689000-f77c9000	Deferred        libwine.so.1
ELF	f77cb000-f77e9000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Rockstar Games\GTA San Andreas\gta_sa.exe
	0000001d    0
	00000019    0
	00000009    0 <==
0000000e services.exe
	00000016    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000018    0
	00000017    0
	00000013    0
	00000012    0
0000001a explorer.exe
	0000001b    0
Backtrace:
liam@l00nix:~/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas$ 
```

---

### Post by ronnielsen1 on 2011-01-14
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2599](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2599)

It always helps to post the version number

---

### Post by cogadh on 2011-01-14
You probably just need to install a native quartz.dll and devenum.dll, both are required to get the game running at all. You can use [winetricks]("http://wiki.winehq.org/winetricks") to do that.

---

