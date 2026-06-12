---
title: "Diablo 1?"
date: 2011-01-29
forum: Wine
---

### Post by cessusbangy on 2011-01-29
Pretty disappointed that I can't play Diablo 1 on Wine (latest version), with latest patch.
Come on... a game from 1995? How hard is that to run... like seriously?

Stack dump:
0x0033f2fc:  0033f3ac 01b40010 0000025d 00000000
0x0033f30c:  000065cf 00000000 01ce5d98 1502e148
0x0033f31c:  000000ee 00000008 0000025d 0033f354
0x0033f32c:  010000fa 00000000 00000000 0033f36c
0x0033f33c:  0033f350 ffffffff ffffffff 000000ee
0x0033f34c:  0033f408 00000000 00000000 00000000
Backtrace:
=>0 0x1502e284 in storm (+0x2e284) (0x01cf4000)
0x1502e284: movb    0x0(%ebp),%cl
Modules:
Module    Address            Debug info    Name (131 modules)
PE      400000-  6b2000    Deferred        diablo
PE     1520000- 153a000    Deferred        smackw32
PE    10000000-1004b000    Deferred        diabloui
PE    15000000-15045000    Export          storm
ELF    7b3a4000-7b3ba000    Deferred        midimap<elf>
  \-PE    7b3b0000-7b3ba000    \               midimap
ELF    7b3ba000-7b3e1000    Deferred        msacm32<elf>
  \-PE    7b3c0000-7b3e1000    \               msacm32
ELF    7b3e1000-7b559000    Deferred        libvorbisenc.so.2
ELF    7b559000-7b5a5000    Deferred        libflac.so.8
ELF    7b5a5000-7b60d000    Deferred        libsndfile.so.1
ELF    7b60d000-7b6d3000    Deferred        libasound.so.2
ELF    7b800000-7b97b000    Deferred        kernel32<elf>
  \-PE    7b810000-7b97b000    \               kernel32
ELF    7bc00000-7bcb7000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb7000    \               ntdll
ELF    7bcb8000-7bcd1000    Deferred        msacm32<elf>
  \-PE    7bcc0000-7bcd1000    \               msacm32
ELF    7bcd1000-7bcd8000    Deferred        libogg.so.0
ELF    7bcd8000-7bd00000    Deferred        libvorbis.so.0
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7bf06000-7bf0f000    Deferred        libwrap.so.0
ELF    7bf0f000-7bf1d000    Deferred        libxi.so.6
ELF    7bf1d000-7bf67000    Deferred        libpulsecommon-0.9.21.so
ELF    7bf67000-7bf6c000    Deferred        libxcb-atom.so.1
ELF    7bf6c000-7c000000    Deferred        winmm<elf>
  \-PE    7bf70000-7c000000    \               winmm
ELF    7c005000-7c047000    Deferred        libpulse.so.0
ELF    7c052000-7c058000    Deferred        libasound_module_pcm_pulse.so
ELF    7c058000-7c0a0000    Deferred        dsound<elf>
  \-PE    7c060000-7c0a0000    \               dsound
ELF    7c3c4000-7c3ca000    Deferred        libxtst.so.6
ELF    7c3ca000-7c3cd000    Deferred        libx11-xcb.so.1
ELF    7c3d0000-7c407000    Deferred        winealsa<elf>
  \-PE    7c3e0000-7c407000    \               winealsa
ELF    7c421000-7dabe000    Deferred        libnvidia-glcore.so.260.19.06
ELF    7dabe000-7dac0000    Deferred        libnvidia-tls.so.260.19.06
ELF    7dac0000-7db89000    Deferred        libgl.so.1
ELF    7db89000-7dcc1000    Deferred        wined3d<elf>
  \-PE    7db90000-7dcc1000    \               wined3d
ELF    7dcc1000-7dd19000    Deferred        ddraw<elf>
  \-PE    7dcd0000-7dd19000    \               ddraw
ELF    7dd19000-7dd34000    Deferred        spoolss<elf>
  \-PE    7dd20000-7dd34000    \               spoolss
ELF    7dd34000-7dd55000    Deferred        localspl<elf>
  \-PE    7dd40000-7dd55000    \               localspl
ELF    7dd55000-7dd5e000    Deferred        librt.so.1
ELF    7dd5e000-7dd9a000    Deferred        libdbus-1.so.3
ELF    7dd9a000-7dd9f000    Deferred        libgpg-error.so.0
ELF    7dd9f000-7ddb0000    Deferred        libtasn1.so.3
ELF    7ddb0000-7ddc4000    Deferred        libresolv.so.2
ELF    7ddc4000-7ddc8000    Deferred        libkeyutils.so.1
ELF    7ddc8000-7ddd0000    Deferred        libkrb5support.so.0
ELF    7ddd0000-7ddf4000    Deferred        libk5crypto.so.3
ELF    7ddf4000-7dea3000    Deferred        libkrb5.so.3
ELF    7dea3000-7deb3000    Deferred        libavahi-client.so.3
ELF    7deb3000-7debf000    Deferred        libavahi-common.so.3
ELF    7debf000-7df33000    Deferred        libgcrypt.so.11
ELF    7df33000-7dfce000    Deferred        libgnutls.so.26
ELF    7dfce000-7dffd000    Deferred        libgssapi_krb5.so.2
ELF    7dffd000-7e047000    Deferred        libcups.so.2
ELF    7e07c000-7e0ef000    Deferred        rpcrt4<elf>
  \-PE    7e090000-7e0ef000    \               rpcrt4
ELF    7e0ef000-7e1ed000    Deferred        ole32<elf>
  \-PE    7e110000-7e1ed000    \               ole32
ELF    7e21b000-7e24f000    Deferred        uxtheme<elf>
  \-PE    7e220000-7e24f000    \               uxtheme
ELF    7e24f000-7e259000    Deferred        libxcursor.so.1
ELF    7e259000-7e25f000    Deferred        libxfixes.so.3
ELF    7e25f000-7e263000    Deferred        libxcomposite.so.1
ELF    7e263000-7e26b000    Deferred        libxrandr.so.2
ELF    7e26b000-7e275000    Deferred        libxrender.so.1
ELF    7e275000-7e27b000    Deferred        libxxf86vm.so.1
ELF    7e27b000-7e27f000    Deferred        libxinerama.so.1
ELF    7e27f000-7e2a0000    Deferred        imm32<elf>
  \-PE    7e290000-7e2a0000    \               imm32
ELF    7e2a0000-7e2a6000    Deferred        libxdmcp.so.6
ELF    7e2a6000-7e2aa000    Deferred        libxau.so.6
ELF    7e2aa000-7e2c4000    Deferred        libxcb.so.1
ELF    7e2c4000-7e2c9000    Deferred        libuuid.so.1
ELF    7e2c9000-7e3e6000    Deferred        libx11.so.6
ELF    7e3e6000-7e3f6000    Deferred        libxext.so.6
ELF    7e3f6000-7e40f000    Deferred        libice.so.6
ELF    7e40f000-7e418000    Deferred        libsm.so.6
ELF    7e425000-7e429000    Deferred        libcom_err.so.2
ELF    7e429000-7e4cb000    Deferred        winex11<elf>
  \-PE    7e440000-7e4cb000    \               winex11
ELF    7e4e8000-7e50f000    Deferred        libexpat.so.1
ELF    7e50f000-7e53f000    Deferred        libfontconfig.so.1
ELF    7e550000-7e565000    Deferred        libz.so.1
ELF    7e565000-7e5dc000    Deferred        libfreetype.so.6
ELF    7e5dc000-7e5f0000    Deferred        comm.drv16.so
PE    7e5e0000-7e5f0000    Deferred        comm.drv16
ELF    7e5f0000-7e605000    Deferred        system.drv16.so
PE    7e600000-7e605000    Deferred        system.drv16
ELF    7e605000-7e6a4000    Deferred        krnl386.exe16.so
PE    7e610000-7e6a4000    Deferred        krnl386.exe16
ELF    7e6a4000-7e6b8000    Deferred        lz32<elf>
  \-PE    7e6b0000-7e6b8000    \               lz32
ELF    7e6b8000-7e6d1000    Deferred        version<elf>
  \-PE    7e6c0000-7e6d1000    \               version
ELF    7e6d1000-7e708000    Deferred        winspool<elf>
  \-PE    7e6e0000-7e708000    \               winspool
ELF    7e708000-7e7c6000    Deferred        comdlg32<elf>
  \-PE    7e710000-7e7c6000    \               comdlg32
ELF    7e7c6000-7e846000    Deferred        msvcrt<elf>
  \-PE    7e7e0000-7e846000    \               msvcrt
ELF    7e846000-7e861000    Deferred        crtdll<elf>
  \-PE    7e850000-7e861000    \               crtdll
ELF    7e861000-7e94c000    Deferred        comctl32<elf>
  \-PE    7e870000-7e94c000    \               comctl32
ELF    7e94c000-7e9ad000    Deferred        shlwapi<elf>
  \-PE    7e960000-7e9ad000    \               shlwapi
ELF    7e9ad000-7eb86000    Deferred        shell32<elf>
  \-PE    7e9c0000-7eb86000    \               shell32
ELF    7eb86000-7ebe0000    Deferred        advapi32<elf>
  \-PE    7eb90000-7ebe0000    \               advapi32
ELF    7ebe0000-7ec6b000    Deferred        gdi32<elf>
  \-PE    7ebf0000-7ec6b000    \               gdi32
ELF    7ec6b000-7ed9b000    Deferred        user32<elf>
  \-PE    7ec80000-7ed9b000    \               user32
ELF    7ed9b000-7eda7000    Deferred        libnss_files.so.2
ELF    7eda7000-7edb2000    Deferred        libnss_nis.so.2
ELF    7edb2000-7edc9000    Deferred        libnsl.so.1
ELF    7efc9000-7efef000    Deferred        libm.so.6
ELF    b746a000-b746e000    Deferred        libdl.so.2
ELF    b746e000-b75cb000    Deferred        libc.so.6
ELF    b75cc000-b75e6000    Deferred        libpthread.so.0
ELF    b75ee000-b75f6000    Deferred        libnss_compat.so.2
ELF    b75f7000-b7737000    Deferred        libwine.so.1
ELF    b7739000-b7757000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
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
0000001b explorer.exe
    0000001c    0
0000001e Diablo.exe
    0000001f    0
00000020 (D) C:\Diablo\Diablo.exe
    00000023    1
    00000022   15
    00000021    0 <==
Backtrace:
=>0 0x1502e284 in storm (+0x2e284) (0x01cf4000)
err:mmtime:TIME_MMTimeStop Timer still active?!
err:d3d:wined3d_unregister_window Window 0x1007a is not registered with wined3d.
err:ddraw:IDirectDrawSurfaceImpl_IsLost  (0x142d28) Implementation was changed from 2 to 0


That stupid MMTime Error... :/

---

### Post by cessusbangy on 2011-01-29
63 views.... 0 answers.
What the f@ck.

---

### Post by DoktorSeven on 2011-01-29
Did you check WineHQ?  There are several fixes and hacks you can use to make Diablo 1 run. 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498)

---

### Post by slixz85 on 2011-01-29
i would imagine it would work too by now wtf lol. if u get it working let us know cuz that was a cool game. might have to install myself

---

### Post by DoktorSeven on 2011-01-29
Diablo has always been difficult to get working under Wine for one reason or the other.  Yeah, it's odd that such an old game is hard to get working, but Wine isn't perfect and you will find the occasional old program that is still difficult or impossible to work in Wine.

I usually find myself just playing old games like that under a virtual machine.  Old games run fine that way.

---

### Post by supergirlkara on 2011-04-05
Which virtual machine software do you use to play Diablo 1? I have found that it doesn't work very well in VirtualBox....Also what version of Windows are you running in said virtual machine? Just was curious, I also love Diablo, and getting it to run in the newest version of Wine is a major headache with no results.

---

### Post by twipley on 2011-08-17
It works alright under VirtualBox:

[http://diablo.incgamers.com/forums/showthread.php?t=805105](http://diablo.incgamers.com/forums/showthread.php?t=805105)

---

