---
title: "Stronghold Crusader"
date: 2010-04-05
forum: Wine
---

### Post by deightm on 2010-04-05
I have netbook with UNR 9.10 on it. I have installed wine 1.1.41 (latest one). Installation of Stronghold Crusader went perfect. Stronghold crusader version is 1.1. But I am unable to run it. It just shows black rect and then quits. Here's the terminal output:
> deightm@deightm-netbook:~$ wine "C:/Games/Strategy/Crusader/Stronghold Crusader.exe"
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f68c,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f4ac,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f4b0,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x155af0,0x155a78): stub
wine: Unhandled page fault on read access to 0x066e5001 at address 0x4545ae (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x066e5001 in 32-bit code (0x004545ae).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:004545ae ESP:0032fd98 EBP:0032fdb4 EFLAGS:00010206(  R- --  I   - -P- )
 EAX:00000000 EBX:0015a183 ECX:00000000 EDX:00000000
 ESI:066e5001 EDI:06be9606
Stack dump:
0x0032fd98:  00000000 062d7020 00000000 00000000
0x0032fda8:  00000320 00000000 00000640 00000001
0x0032fdb8:  00454438 00000190 0000012c 00000640
0x0032fdc8:  00000000 062d7028 00000000 0057a856
0x0032fdd8:  00000000 00000190 0000012c 0057dfdd
0x0032fde8:  00000000 0032fea8 7b881ff4 00000001
Backtrace:
=>0 0x004545ae in stronghold crusader (+0x545ae) (0x0032fdb4)
  1 0x00454438 in stronghold crusader (+0x54438) (0x00000001)
  2 0x00000000 (0x00000000)
0x004545ae: movb    0x0(%esi),%al
Modules:
Module    Address            Debug info    Name (123 modules)
PE      400000- 1da5000    Export          stronghold crusader
ELF    20000000-20135000    Deferred        wined3d<elf>
  \-PE    20010000-20135000    \               wined3d
ELF    20135000-2013f000    Deferred        libdrm_intel.so.1
ELF    2013f000-20186000    Deferred        dsound<elf>
  \-PE    20150000-20186000    \               dsound
PE    21100000-2115e000    Deferred        mss32
ELF    24b54000-24bb8000    Deferred        libgl.so.1
PE    30000000-3006d000    Deferred        binkw32
ELF    5a9a2000-5a9ac000    Deferred        libdrm.so.2
ELF    5e8e0000-5eb70000    Deferred        i915_dri.so
ELF    68000000-6801d000    Deferred        ld-linux.so.2
ELF    6801d000-68158000    Deferred        libwine.so.1
ELF    68158000-68171000    Deferred        libpthread.so.0
ELF    68171000-68175000    Deferred        libdl.so.2
ELF    68175000-6817d000    Deferred        libnss_compat.so.2
ELF    6817d000-68194000    Deferred        libnsl.so.1
ELF    68194000-6819f000    Deferred        libnss_nis.so.2
ELF    6819f000-682ad000    Deferred        user32<elf>
  \-PE    681b0000-682ad000    \               user32
ELF    682ad000-68337000    Deferred        gdi32<elf>
  \-PE    682c0000-68337000    \               gdi32
ELF    68337000-68390000    Deferred        advapi32<elf>
  \-PE    68340000-68390000    \               advapi32
ELF    68390000-6843b000    Deferred        comdlg32<elf>
  \-PE    683a0000-6843b000    \               comdlg32
ELF    6843b000-68509000    Deferred        comctl32<elf>
  \-PE    68440000-68509000    \               comctl32
ELF    68509000-68606000    Deferred        ole32<elf>
  \-PE    68520000-68606000    \               ole32
ELF    68606000-68621000    Deferred        wsock32<elf>
  \-PE    68610000-68621000    \               wsock32
ELF    68621000-6864c000    Deferred        ws2_32<elf>
  \-PE    68630000-6864c000    \               ws2_32
ELF    6864c000-6866c000    Deferred        iphlpapi<elf>
  \-PE    68650000-6866c000    \               iphlpapi
ELF    6866c000-686f3000    Deferred        winmm<elf>
  \-PE    68670000-686f3000    \               winmm
ELF    686f3000-6874a000    Deferred        ddraw<elf>
  \-PE    68700000-6874a000    \               ddraw
ELF    6874a000-6877f000    Deferred        dplayx<elf>
  \-PE    68750000-6877f000    \               dplayx
ELF    6877f000-68795000    Deferred        libz.so.1
ELF    68795000-687bc000    Deferred        libexpat.so.1
ELF    687bc000-6885b000    Deferred        winex11<elf>
  \-PE    687d0000-6885b000    \               winex11
ELF    6885b000-68864000    Deferred        libsm.so.6
ELF    68864000-68874000    Deferred        libxext.so.6
ELF    68874000-689a3000    Deferred        libx11.so.6
ELF    689a3000-689a8000    Deferred        libuuid.so.1
ELF    689a8000-689ac000    Deferred        libxau.so.6
ELF    689ac000-689ca000    Deferred        libxcb.so.1
ELF    689ca000-689cf000    Deferred        libxdmcp.so.6
ELF    689cf000-689f0000    Deferred        imm32<elf>
  \-PE    689e0000-689f0000    \               imm32
ELF    689f0000-689f3000    Deferred        libxinerama.so.1
ELF    689f6000-68a1c000    Deferred        libm.so.6
ELF    68a1c000-68a22000    Deferred        libxxf86vm.so.1
ELF    68a22000-68a2c000    Deferred        libxrender.so.1
ELF    68a2c000-68a30000    Deferred        libxcomposite.so.1
ELF    68a30000-68a36000    Deferred        libxfixes.so.3
ELF    68a36000-68a41000    Deferred        libxcursor.so.1
ELF    68a41000-68a74000    Deferred        uxtheme<elf>
  \-PE    68a50000-68a74000    \               uxtheme
ELF    68a74000-68a94000    Deferred        localspl<elf>
  \-PE    68a80000-68a94000    \               localspl
ELF    68a94000-68aad000    Deferred        spoolss<elf>
  \-PE    68aa0000-68aad000    \               spoolss
ELF    68aad000-68af3000    Deferred        libcups.so.2
ELF    68af3000-68b1d000    Deferred        libgssapi_krb5.so.2
ELF    68b1d000-68bc5000    Deferred        libgnutls.so.26
ELF    68bc5000-68bd1000    Deferred        libavahi-common.so.3
ELF    68bd1000-68be2000    Deferred        libavahi-client.so.3
ELF    68be2000-68c88000    Deferred        libkrb5.so.3
ELF    68c88000-68cb1000    Deferred        libk5crypto.so.3
ELF    68cb1000-68cb5000    Deferred        libcom_err.so.2
ELF    68cb5000-68cbd000    Deferred        libkrb5support.so.0
ELF    68cbd000-68cc1000    Deferred        libkeyutils.so.1
ELF    68cc1000-68cd3000    Deferred        libtasn1.so.3
ELF    68cd3000-68d4f000    Deferred        libgcrypt.so.11
ELF    68d4f000-68d88000    Deferred        libdbus-1.so.3
ELF    68d88000-68d8d000    Deferred        libgpg-error.so.0
ELF    68d8d000-68dc4000    Deferred        winealsa<elf>
  \-PE    68da0000-68dc4000    \               winealsa
ELF    68dc4000-68e8b000    Deferred        libasound.so.2
ELF    68e8b000-68ecb000    Deferred        libpulse.so.0
ELF    68ecb000-68f15000    Deferred        libpulsecommon-0.9.19.so
ELF    68f15000-68f1b000    Deferred        libxtst.so.6
ELF    68f1b000-68f24000    Deferred        libwrap.so.0
ELF    68f24000-68f90000    Deferred        libsndfile.so.1
ELF    68f90000-68fe0000    Deferred        libflac.so.8
ELF    68fe0000-690dc000    Deferred        libvorbisenc.so.2
ELF    690dc000-69105000    Deferred        libvorbis.so.0
ELF    69105000-6910c000    Deferred        libogg.so.0
ELF    6910c000-69113000    Deferred        libasound_module_pcm_pulse.so
ELF    69113000-6912b000    Deferred        msacm32<elf>
  \-PE    69120000-6912b000    \               msacm32
ELF    6912b000-69151000    Deferred        msacm32<elf>
  \-PE    69130000-69151000    \               msacm32
ELF    69f98000-6a017000    Deferred        libfreetype.so.6
ELF    6b372000-6b39f000    Deferred        libfontconfig.so.1
ELF    6c8e6000-6c8ef000    Deferred        librt.so.1
ELF    6e799000-6e7ad000    Deferred        libresolv.so.2
ELF    72b10000-72b6e000    Deferred        shlwapi<elf>
  \-PE    72b20000-72b6e000    \               shlwapi
ELF    74a97000-74b07000    Deferred        rpcrt4<elf>
  \-PE    74aa0000-74b07000    \               rpcrt4
ELF    75851000-7585d000    Deferred        libnss_files.so.2
ELF    765a8000-766ed000    Deferred        libc.so.6
ELF    76909000-76924000    Deferred        libice.so.6
ELF    77f5a000-77f5d000    Deferred        libxdamage.so.1
ELF    78093000-780c9000    Deferred        winspool<elf>
  \-PE    780a0000-780c9000    \               winspool
ELF    799ff000-79b91000    Deferred        shell32<elf>
  \-PE    79a10000-79b91000    \               shell32
ELF    7b800000-7b93a000    Deferred        kernel32<elf>
  \-PE    7b810000-7b93a000    \               kernel32
ELF    7b9f7000-7ba0d000    Deferred        midimap<elf>
  \-PE    7ba00000-7ba0d000    \               midimap
ELF    7bc00000-7bcb5000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb5000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c332000-7c33b000    Deferred        libxrandr.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Games\Strategy\Crusader\Stronghold Crusader.exe
    0000001b   15
    0000001a   15
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
00000018 explorer.exe
    00000019    0
Backtrace:
=>0 0x004545ae in stronghold crusader (+0x545ae) (0x0032fdb4)
  1 0x00454438 in stronghold crusader (+0x54438) (0x00000001)
  2 0x00000000 (0x00000000)
deightm@deightm-netbook:~$ 

DirectDrawRenderer is set to gdi. How to fix this?
P.s. using ubuntu for almost 1 day now. So I am not familiar with ways stuff work.

---

### Post by deightm on 2010-04-05
Well I managed to run it in windowed mode by turning on "virtual desktop" option. But I need full screen because 800x600 + titlebar window doesnt fit vertically on my 10'' netbook screen. But there is no "800x600" resolution in display settings. Manual creation of xorg.conf resulted in rebooting in recovery mode and deleting it.
 So the new question is how do I add "800x600" resolution to my ubuntu 9.10 if its non native for monitor.

p.s sorry for bad english

---

### Post by deightm on 2010-04-05
Already fixed using xrandr. Sorry for asking noob questions. Newer used linux before.

---

