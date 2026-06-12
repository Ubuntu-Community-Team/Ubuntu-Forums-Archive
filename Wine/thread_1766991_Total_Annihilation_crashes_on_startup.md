---
title: "Total Annihilation crashes on startup"
date: 2011-05-25
forum: Wine
---

### Post by ELD on 2011-05-25
Have no idea what any of this means:

> 
liam@liam-desktop:~$ wine '/home/liam/.wine/drive_c/Program Files/GOG.com/Total Annihilation/TotalA.exe' 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 93 (SPI_SETMOUSETRAILS)
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:win:EnumDisplayDevicesW ((null),0,0x32f270,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:mixer:ALSA_MixerInit No master control found on HD-Audio Generic, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8da, disabling mixer
err:alsa:ALSA_CheckSetVolume Could not find '{PCM,Line} Playback Volume' element
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x180e30,0x180788): stub
wine: Call from 0x7b839b12 to unimplemented function msvcp90.dll.?find@?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QBEIABV12@I@Z, aborting
fixme:dbghelp_msc:pe_load_debug_directory This guy has FPO information
wine: Unimplemented function msvcp90.dll.?find@?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QBEIABV12@I@Z called at address 0x7b839b12 (thread 0009), starting debugger...
Unhandled exception: unimplemented function msvcp90.dll.?find@?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@s called in 32-bit code (0x7b839b12).
fixme:dbghelp_msc:pe_load_debug_directory This guy has FPO information
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b839b12 ESP:0032f904 EBP:0032f968 EFLAGS:00000283(   - --  I S - - -C)
 EAX:7b8259f5 EBX:7b88aff4 ECX:7e7685c2 EDX:0032f92c
 ESI:80000100 EDI:10002140
Stack dump:
0x0032f904:  0032f988 00000008 7e7471eb 80000100
0x0032f914:  00000001 00000000 7b839b12 00000002
0x0032f924:  7e74b1c0 7e7685c2 7e746f13 00180812
0x0032f934:  7e780407 f75eeff4 7e792ff4 7e792ff4
0x0032f944:  7e792ff4 0032f988 7e74826d 00180800
0x0032f954:  0000001f 10004420 7b839aca 00000001
Backtrace:
=>0 0x7b839b12 in kernel32 (+0x29b12) (0x0032f968)
  1 0x7e74b128 in msvcp90 (+0x2b127) (0x0032f998)
  2 0x7e738f79 in msvcp90 (+0x18f78) (0x0032fcb8)
  3 0x1000219f in win32 (+0x219e) (0x0032fcb8)
0x7b839b12: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (112 modules)
PE      330000-  3ba000    Deferred        audiere
PE      3c0000-  3d8000    Deferred        smackw32
PE      400000-  52e000    Export          totala
PE    10000000-1000c000    Export          win32
ELF    7b800000-7b99e000    Dwarf           kernel32<elf>
  \-PE    7b810000-7b99e000    \               kernel32
ELF    7bc00000-7bcba000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcba000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7cb68000-7cb7d000    Deferred        psapi<elf>
  \-PE    7cb70000-7cb7d000    \               psapi
ELF    7cb7d000-7cbd8000    Deferred        dbghelp<elf>
  \-PE    7cb80000-7cbd8000    \               dbghelp
ELF    7cbf1000-7cc1a000    Deferred        msacm32<elf>
  \-PE    7cc00000-7cc1a000    \               msacm32
ELF    7cc1a000-7cc33000    Deferred        msacm32<elf>
  \-PE    7cc20000-7cc33000    \               msacm32
ELF    7d434000-7d43b000    Deferred        libogg.so.0
ELF    7d43b000-7d462000    Deferred        libvorbis.so.0
ELF    7d462000-7d5da000    Deferred        libvorbisenc.so.2
ELF    7d5da000-7d626000    Deferred        libflac.so.8
ELF    7d626000-7d68c000    Deferred        libsndfile.so.1
ELF    7d68c000-7d695000    Deferred        libwrap.so.0
ELF    7d695000-7d6d2000    Deferred        libdbus-1.so.3
ELF    7d6d2000-7d71b000    Deferred        libpulsecommon-0.9.22.so
ELF    7d71b000-7d720000    Deferred        libxcb-atom.so.1
ELF    7d720000-7d726000    Deferred        libxtst.so.6
ELF    7d726000-7d729000    Deferred        libx11-xcb.so.1
ELF    7d729000-7d76a000    Deferred        libpulse.so.0
ELF    7d76d000-7d839000    Deferred        libasound.so.2
ELF    7d839000-7d87c000    Deferred        winealsa<elf>
  \-PE    7d840000-7d87c000    \               winealsa
ELF    7dad6000-7dadf000    Deferred        librt.so.1
ELF    7dadf000-7dafb000    Deferred        libgcc_s.so.1
ELF    7dbe6000-7dbf0000    Deferred        libdrm.so.2
ELF    7dbf0000-7dc46000    Deferred        libgl.so.1
ELF    7dc47000-7dc5d000    Deferred        midimap<elf>
  \-PE    7dc50000-7dc5d000    \               midimap
ELF    7dc5d000-7dc63000    Deferred        libasound_module_pcm_pulse.so
ELF    7dcd0000-7dd04000    Deferred        uxtheme<elf>
  \-PE    7dce0000-7dd04000    \               uxtheme
ELF    7dd1a000-7dd20000    Deferred        libxfixes.so.3
ELF    7dd20000-7dd2a000    Deferred        libxcursor.so.1
ELF    7dd2a000-7dd39000    Deferred        libxi.so.6
ELF    7dd39000-7dd3d000    Deferred        libxcomposite.so.1
ELF    7dd3d000-7dd45000    Deferred        libxrandr.so.2
ELF    7dd45000-7dd4f000    Deferred        libxrender.so.1
ELF    7dd4f000-7dd55000    Deferred        libxxf86vm.so.1
ELF    7dd55000-7dd59000    Deferred        libxinerama.so.1
ELF    7dd59000-7dd7a000    Deferred        imm32<elf>
  \-PE    7dd60000-7dd7a000    \               imm32
ELF    7dd7a000-7dd80000    Deferred        libxdmcp.so.6
ELF    7dd80000-7dd84000    Deferred        libxau.so.6
ELF    7dd84000-7dd9d000    Deferred        libxcb.so.1
ELF    7dd9d000-7dda2000    Deferred        libuuid.so.1
ELF    7dda2000-7debd000    Deferred        libx11.so.6
ELF    7debd000-7decc000    Deferred        libxext.so.6
ELF    7decc000-7dee4000    Deferred        libice.so.6
ELF    7dee4000-7deec000    Deferred        libsm.so.6
ELF    7deec000-7def0000    Deferred        libxdamage.so.1
ELF    7df0c000-7dfb7000    Deferred        winex11<elf>
  \-PE    7df20000-7dfb7000    \               winex11
ELF    7e0df000-7e109000    Deferred        libexpat.so.1
ELF    7e153000-7e182000    Deferred        libfontconfig.so.1
ELF    7e182000-7e197000    Deferred        libz.so.1
ELF    7e197000-7e21d000    Deferred        libfreetype.so.6
ELF    7e21d000-7e254000    Deferred        libncurses.so.5
ELF    7e274000-7e368000    Deferred        comctl32<elf>
  \-PE    7e280000-7e368000    \               comctl32
ELF    7e368000-7e3cc000    Deferred        shlwapi<elf>
  \-PE    7e380000-7e3cc000    \               shlwapi
ELF    7e3cc000-7e5c7000    Deferred        shell32<elf>
  \-PE    7e3e0000-7e5c7000    \               shell32
ELF    7e5c7000-7e60f000    Deferred        dsound<elf>
  \-PE    7e5d0000-7e60f000    \               dsound
ELF    7e60f000-7e644000    Deferred        dplayx<elf>
  \-PE    7e620000-7e644000    \               dplayx
ELF    7e644000-7e673000    Deferred        msvcr90<elf>
  \-PE    7e650000-7e673000    \               msvcr90
ELF    7e673000-7e708000    Deferred        msvcrt<elf>
  \-PE    7e690000-7e708000    \               msvcrt
ELF    7e708000-7e7cf000    Dwarf           msvcp90<elf>
  \-PE    7e720000-7e7cf000    \               msvcp90
ELF    7e7cf000-7e8d1000    Deferred        ole32<elf>
  \-PE    7e7f0000-7e8d1000    \               ole32
ELF    7e8d1000-7e969000    Deferred        winmm<elf>
  \-PE    7e8e0000-7e969000    \               winmm
ELF    7e969000-7e9db000    Deferred        rpcrt4<elf>
  \-PE    7e970000-7e9db000    \               rpcrt4
ELF    7e9db000-7ea37000    Deferred        advapi32<elf>
  \-PE    7e9f0000-7ea37000    \               advapi32
ELF    7ea37000-7eaca000    Deferred        gdi32<elf>
  \-PE    7ea40000-7eaca000    \               gdi32
ELF    7eaca000-7ebff000    Deferred        user32<elf>
  \-PE    7eae0000-7ebff000    \               user32
ELF    7ebff000-7ed2e000    Deferred        wined3d<elf>
  \-PE    7ec10000-7ed2e000    \               wined3d
ELF    7ed2e000-7ed8c000    Deferred        ddraw<elf>
  \-PE    7ed40000-7ed8c000    \               ddraw
ELF    7ef8c000-7ef98000    Deferred        libnss_files.so.2
ELF    7ef98000-7efa3000    Deferred        libnss_nis.so.2
ELF    7efa3000-7efba000    Deferred        libnsl.so.1
ELF    7efba000-7efe0000    Deferred        libm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f7478000-f747c000    Deferred        libdl.so.2
ELF    f747c000-f75d9000    Deferred        libc.so.6
ELF    f75d9000-f75f2000    Deferred        libpthread.so.0
ELF    f75f8000-f7600000    Deferred        libnss_compat.so.2
ELF    f7612000-f7753000    Dwarf           libwine.so.1
ELF    f7755000-f7773000    Deferred        ld-linux.so.2
ELF    f7773000-f7774000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\GOG.com\Total Annihilation\TotalA.exe
    00000022   15
    00000021    0
    00000020    2
    00000009    0 <==
0000000e services.exe
    0000001c    0
    0000001b    0
    00000015    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000017    0
    00000016    0
    00000013    0
    00000012    0
00000018 plugplay.exe
    0000001d    0
    0000001a    0
    00000019    0
0000001e explorer.exe
    0000001f    0
Backtrace:
=>0 0x7b839b12 in kernel32 (+0x29b12) (0x0032f968)
  1 0x7e74b128 in msvcp90 (+0x2b127) (0x0032f998)
  2 0x7e738f79 in msvcp90 (+0x18f78) (0x0032fcb8)
  3 0x1000219f in win32 (+0x219e) (0x0032fcb8)
wine: Call from 0x7b839b12 to unimplemented function msvcp90.dll.?find@?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QBEIABV12@I@Z, aborting
wine: Call from 0x7b839b12 to unimplemented function msvcp90.dll.?find@?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QBEIABV12@I@Z, aborting
fixme:msvcr90:__clean_type_info_names_internal (0x10009384) stub
err:mmtime:TIME_MMTimeStop Timer still active?!



---

### Post by Everybody Loves Hypnotoad on 2011-10-21
Someone's been asking this very question in a lot of different forums. The key is on the second line - you need to install "Microsoft.VC90" and tell wine where to find it.

Install winetricks, run it, from gnome-terminal or whatever, 
select "Select the default wineprefix", 
select "Install a Windows DLL or component", 
select vcrun2008 (because this is the visual c++ version 9 file you need),
hit ok and it should download the magic stuff and install it into wine as well as configure wine to use it as an override inside winecfg (so you don't have to do it).

Close winetricks and play the GOG-version of TotalA!

---

### Post by ELD on 2011-10-22
Thanks might give it a go later on, would be useful if wine itself picked that up and just outright told you what to install - would sure make things more user friendly.

---

### Post by Everybody Loves Hypnotoad on 2011-10-22
I just noticed this thread was not exactly created yesterday :)

The reason why you need the vc9 stuff is GOG added something to totala.exe to make it play music from mp3s inside the music folder instead of the cd audio the original version uses, and also some kind of nocd. Convenient for those who use windows but not so much for us rebels. Don't forget to download the totala.ini file that can be found online that sets the maximum number of units to 500 instead of the default 250 ^^

---

