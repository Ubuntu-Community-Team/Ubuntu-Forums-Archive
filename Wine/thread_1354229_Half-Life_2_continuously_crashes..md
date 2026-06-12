---
title: "Half-Life 2 continuously crashes."
date: 2009-12-13
forum: Wine
---

### Post by nemodot on 2009-12-13
Hi,

I just installed it, but after a while of playing it crashes with an error message. This is what the console shows me:

```
esteban@esteban-desktop:~$ wine /media/GORDO/Half-Life\ 2/Half-Life\ 2/ahu-hl2/hl2.exe -steam -console
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 15/03/2009, dlt (d/m/y): 31/12/2009
fixme:win:EnumDisplayDevicesW ((null),0,0x32de5c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
Unable to remove z:\media\gordo\half-life 2\half-life 2\ahu-hl2\hl2\SAVE!
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x8619050,0x86197e8): stub
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:shdocvw:ViewObject_SetAdvise (0x892eef0)->(1 00000002 0xa878be8)
fixme:shdocvw:PersistStreamInit_InitNew (0x892eef0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x892eef0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x892eef0)->(ffffffff)
Unable to remove z:\media\gordo\half-life 2\half-life 2\ahu-hl2\hl2\SAVE!
Unable to remove z:\media\gordo\half-life 2\half-life 2\ahu-hl2\hl2\SAVE!
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8996730: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8996948: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8996b60: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8996d78: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8996f90: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89971a8: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89973c0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8997578: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8997730: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89978e8: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8997aa0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8997c58: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8997e10: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8997fb0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8998150: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89982f0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8998490: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8998630: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89987d0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8998970: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8998b10: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8998cb0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8998e50: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8998ff0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8999190: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8999330: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89994d0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8999670: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8999810: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89999b0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89414d0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89416e8: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8941900: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8941b18: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8941d30: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8941f48: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8942160: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8942318: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89424d0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8942688: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8942840: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89429f8: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8942bb0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8942d50: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8942ef0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8943090: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8943230: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89433d0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8943570: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8943710: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89438b0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8943a50: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8943bf0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8943d90: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8943f30: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89440d0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8944270: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8948ee8: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8949030: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89491a0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x1886c980: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x1886cd18: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x1886cf30: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x1886d100: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x1886d2a0: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x1886d440: Downloading rgb texture to reload it as srgb
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x892eef0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x892eef0)
fixme:shdocvw:OleObject_Close (0x892eef0)->(1)
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8949788: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x89499a0: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8949bb8: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8949dd0: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x8949fe8: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894a200: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894a418: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894a5d0: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894a788: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894a940: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894aaf8: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894acb0: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894ae68: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894b008: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894b1a8: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894b348: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894b4e8: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894b688: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894b828: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894b9c8: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894bb68: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894bd08: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894bea8: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894c048: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894c1e8: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894c388: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894c528: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894c6c8: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894c868: Downloading srgb texture to reload it as rgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x894ca08: Downloading srgb texture to reload it as rgb
wine: Unhandled page fault on read access to 0xee15271c at address 0x50710057 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0xee15271c in 32-bit code (0x50710057).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:50710057 ESP:0032ed70 EBP:00000000 EFLAGS:00210a87(  R- --O I S - -P-C)
 EAX:9d31a93c EBX:00000001 ECX:00020000 EDX:00000000
 ESI:00000008 EDI:00000040
Stack dump:
0x0032ed70:  00000000 00000000 00000000 00000000
0x0032ed80:  00000000 00000000 00000000 00000000
0x0032ed90:  00000000 00000000 00000000 00000001
0x0032eda0:  7e505008 00000000 00000000 00000000
0x0032edb0:  00000000 00000000 00000100 00000000
0x0032edc0:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x50710057 in libglcore.so.1 (+0x5f8057) (0x00000000)
0x50710057: movl	0x50e37de0(%eax),%ecx
Modules:
Module	Address			Debug info	Name (135 modules)
PE	  330000-  346000	Deferred        vstdlib
PE	  350000-  387000	Deferred        tier0
PE	  3b0000-  3c4000	Deferred        steam
PE	  3d0000-  3e3000	Deferred        steamy
PE	  3f0000-  3fe000	Deferred        unicode
PE	  400000-  416000	Deferred        hl2
PE	 18a0000- 18bf000	Deferred        stdshader_dbg
PE	 18c0000- 18ed000	Deferred        stdshader_dx6
PE	 18f0000- 1925000	Deferred        stdshader_dx7
PE	 1930000- 1992000	Deferred        stdshader_dx8
PE	 19a0000- 19cc000	Deferred        stdshader_dx9
PE	 7a30000- 7ca0000	Deferred        studiorender
PE	 7ca0000- 7e4c000	Deferred        gameui
PE	 89e0000- 89ed000	Deferred        vaudio_miles
PE	 b730000- b7cc000	Deferred        trackerui
PE	 b7d0000- b8f7000	Deferred        serverbrowser
PE	 b900000- b93d000	Deferred        trackernet
PE	10000000-10010000	Deferred        launcher
ELF	20000000-20014000	Deferred        libresolv.so.2
ELF	20014000-2002e000	Deferred        dinput8<elf>
  \-PE	20020000-2002e000	\               dinput8
ELF	2002e000-20065000	Deferred        winealsa<elf>
  \-PE	20040000-20065000	\               winealsa
ELF	20065000-200a5000	Deferred        libpulse.so.0
ELF	200a5000-200ab000	Deferred        libxtst.so.6
ELF	200ab000-200b2000	Deferred        libasound_module_pcm_pulse.so
ELF	200b2000-200d8000	Deferred        msacm32<elf>
  \-PE	200c0000-200d8000	\               msacm32
ELF	200d8000-20268000	Deferred        shell32<elf>
  \-PE	200f0000-20268000	\               shell32
ELF	20268000-2029b000	Deferred        uxtheme<elf>
  \-PE	20270000-2029b000	\               uxtheme
ELF	2029b000-202b4000	Deferred        mcicda<elf>
  \-PE	202a0000-202b4000	\               mcicda
ELF	202b4000-202d2000	Deferred        libgcc_s.so.1
PE	21100000-21164000	Deferred        mss32
PE	22000000-2262d000	Deferred        server
ELF	23dc1000-23dc8000	Deferred        libogg.so.0
PE	24000000-24388000	Deferred        client
PE	26000000-26109000	Deferred        vphysics
PE	26400000-26439000	Deferred        mssvoice.asi
PE	26f00000-26f2e000	Deferred        mssmp3.asi
PE	2a000000-2a07d000	Deferred        shaderapidx9
ELF	2a197000-2a21e000	Deferred        winmm<elf>
  \-PE	2a1a0000-2a21e000	\               winmm
ELF	2c556000-2c625000	Deferred        comctl32<elf>
  \-PE	2c560000-2c625000	\               comctl32
ELF	30f6e000-30f87000	Deferred        msacm32<elf>
  \-PE	30f70000-30f87000	\               msacm32
ELF	347ca000-3480b000	Deferred        shdocvw<elf>
  \-PE	347d0000-3480b000	\               shdocvw
ELF	3497d000-349c7000	Deferred        libpulsecommon-0.9.19.so
ELF	36e35000-36e85000	Deferred        libflac.so.8
ELF	373bc000-373e5000	Deferred        libvorbis.so.0
ELF	3a062000-3a15e000	Deferred        libvorbisenc.so.2
ELF	3c52d000-3c543000	Deferred        winejoystick<elf>
  \-PE	3c530000-3c543000	\               winejoystick
ELF	3e66e000-3e698000	Deferred        ws2_32<elf>
  \-PE	3e680000-3e698000	\               ws2_32
ELF	3f8b6000-3f8d6000	Deferred        iphlpapi<elf>
  \-PE	3f8c0000-3f8d6000	\               iphlpapi
ELF	4976b000-4984f000	Deferred        oleaut32<elf>
  \-PE	49780000-4984f000	\               oleaut32
ELF	4c5b9000-4c625000	Deferred        libsndfile.so.1
ELF	50118000-50e58000	Export          libglcore.so.1
ELF	52b30000-52b45000	Deferred        midimap<elf>
  \-PE	52b40000-52b45000	\               midimap
ELF	535a2000-535ab000	Deferred        librt.so.1
ELF	54cda000-54d38000	Deferred        shlwapi<elf>
  \-PE	54cf0000-54d38000	\               shlwapi
ELF	575d1000-5760a000	Deferred        libdbus-1.so.3
ELF	5add3000-5af04000	Deferred        wined3d<elf>
  \-PE	5ade0000-5af04000	\               wined3d
ELF	62d37000-62d70000	Deferred        dinput<elf>
  \-PE	62d40000-62d70000	\               dinput
ELF	63320000-6341d000	Deferred        ole32<elf>
  \-PE	63340000-6341d000	\               ole32
ELF	6369f000-636d3000	Deferred        d3d9<elf>
  \-PE	636b0000-636d3000	\               d3d9
ELF	68000000-6801d000	Deferred        ld-linux.so.2
ELF	6801d000-68159000	Deferred        libwine.so.1
ELF	68159000-68172000	Deferred        libpthread.so.0
ELF	68172000-682b6000	Deferred        libc.so.6
ELF	682b6000-682ba000	Deferred        libdl.so.2
ELF	682ba000-682e0000	Deferred        libm.so.6
ELF	682e0000-682e8000	Deferred        libnss_compat.so.2
ELF	682e8000-682ff000	Deferred        libnsl.so.1
ELF	682ff000-6830a000	Deferred        libnss_nis.so.2
ELF	6830a000-68316000	Deferred        libnss_files.so.2
ELF	68316000-683b6000	Deferred        gdi32<elf>
  \-PE	68330000-683b6000	\               gdi32
ELF	683b6000-6840e000	Deferred        advapi32<elf>
  \-PE	683c0000-6840e000	\               advapi32
ELF	6840e000-6847c000	Deferred        rpcrt4<elf>
  \-PE	68420000-6847c000	\               rpcrt4
ELF	6847c000-68491000	Deferred        system.drv16.so
PE	68480000-68491000	Deferred        system.drv16
ELF	68491000-68510000	Deferred        libfreetype.so.6
ELF	68510000-68526000	Deferred        libz.so.1
ELF	68526000-68553000	Deferred        libfontconfig.so.1
ELF	68553000-6857a000	Deferred        libexpat.so.1
ELF	6857a000-6861a000	Deferred        winex11<elf>
  \-PE	68590000-6861a000	\               winex11
ELF	6861a000-68623000	Deferred        libsm.so.6
ELF	68623000-6863e000	Deferred        libice.so.6
ELF	6863e000-6864e000	Deferred        libxext.so.6
ELF	6864e000-6877d000	Deferred        libx11.so.6
ELF	6877d000-68782000	Deferred        libuuid.so.1
ELF	68782000-68786000	Deferred        libxau.so.6
ELF	68786000-6878b000	Deferred        libxdmcp.so.6
ELF	6878b000-687ac000	Deferred        imm32<elf>
  \-PE	68790000-687ac000	\               imm32
ELF	687ac000-687af000	Deferred        libxinerama.so.1
ELF	687af000-687b5000	Deferred        libxxf86vm.so.1
ELF	687b5000-687bf000	Deferred        libxrender.so.1
ELF	687bf000-687c3000	Deferred        libxcomposite.so.1
ELF	687c3000-687c9000	Deferred        libxfixes.so.3
ELF	687c9000-687d4000	Deferred        libxcursor.so.1
ELF	6afe9000-6b007000	Deferred        libxcb.so.1
ELF	6d6d1000-6d798000	Deferred        libasound.so.2
ELF	6eff5000-6effe000	Deferred        libxrandr.so.2
ELF	70402000-70404000	Deferred        libnvidia-tls.so.1
ELF	72cdc000-72ce5000	Deferred        libwrap.so.0
ELF	72ff5000-7313f000	Deferred        user32<elf>
  \-PE	73010000-7313f000	\               user32
ELF	77036000-77081000	Deferred        dsound<elf>
  \-PE	77040000-77081000	\               dsound
ELF	78bfa000-78c9e000	Deferred        libgl.so.1
ELF	7b5c8000-7b5e3000	Deferred        wsock32<elf>
  \-PE	7b5d0000-7b5e3000	\               wsock32
ELF	7b800000-7b973000	Deferred        kernel32<elf>
  \-PE	7b820000-7b973000	\               kernel32
ELF	7bc00000-7bcb5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb5000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\media\GORDO\Half-Life 2\Half-Life 2\ahu-hl2\hl2.exe
	00000009    0 <==
0000000e 
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000018 
	00000019    0
Backtrace:
=>0 0x50710057 in libglcore.so.1 (+0x5f8057) (0x00000000)

```

There's something I can do to fix this?

---

### Post by beastrace91 on 2009-12-13
Wine version, Graphics card, and driver version please?

Regards,
~Jeff

---

### Post by nemodot on 2009-12-13
Wine 1.1.34
Graphic card: GeForce 6600gt driver version 173 (the newer 185 gives me problems).

---

### Post by beastrace91 on 2009-12-13
Try reverting your Wine version to 1.1.32 or 1.1.28 and see if that resolves the crashing issue, sometimes certain Wine version don't play nicely with some applications for some people.

Also have you installed any Wine tricks in your current Wine prefix?

Regards,
~Jeff

---

### Post by nemodot on 2009-12-13
I had installed wine tricks. 

How can I downgrade to that version of wine?

---

### Post by beastrace91 on 2009-12-13
Run the following in terminal:

```
sudo apt-get remove wine
```

Then go to [here](http://wine.budgetdedicated.com/archive/index.html) and download the .deb file for the Wine version you want and install it. Also what did you install via Wine tricks? Some times packages from it can cause issues at times.

Regards,
~Jeff

---

### Post by nemodot on 2009-12-13
I used winetricks to install MS fonts and DirectX 9.

Ok, i downgraded to 1.1.28 but still crashes in the same place as before.

---

### Post by beastrace91 on 2009-12-13
> **nemodot said:**
> I used winetricks to install MS DirectX 9.

I'd bet that may be the culprit - I know there is a warning in Winetricks against installing DX9 directly from M$ because it causes issues.

Either delete your ~/.wine directory and try running the game with out it or try launching Steam through a clean wineprefix and see if that helps at all.

Also you could try adding **-dxlevel 81** to your HL2 launch options to see if that resolves the issue.

Regards,
~Jeff

---

### Post by commodore256 on 2009-12-14
> **beastrace91 said:**
> Also you could try adding **-dxlevel 81** to your HL2 launch options to see if that resolves the issue.

Regards,
~Jeff

I heard there was an opengl cli option.

---

