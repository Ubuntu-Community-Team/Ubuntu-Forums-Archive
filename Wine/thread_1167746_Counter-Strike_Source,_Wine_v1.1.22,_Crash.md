---
title: "Counter-Strike Source, Wine v1.1.22, Crash"
date: 2009-05-23
forum: Wine
---

### Post by 8Kuula on 2009-05-23
After upgrading wine to 1.1.22, CSS started to crash every time after spawning in game and round starts.
Did start from Counter-Strike Source dir to see what crash outputs, with command: wine hl2.exe -game cstrike

```

...
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:avifile:AVIFileExit (): stub!
wine: Unhandled page fault on read access to 0x00000024 at address 0xd49b423 (thread 0062), starting debugger...
Unhandled exception: page fault on read access to 0x00000024 in 32-bit code (0x0d49b423).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0d49b423 ESP:0032e5e8 EBP:00000002 EFLAGS:00010212(  R- --  I   -A- - )
 EAX:00000020 EBX:00000000 ECX:14a99380 EDX:07365900
 ESI:0d4aea18 EDI:00000090
Stack dump:
0x0032e5e8:  0d4aea18 00663654 0d49b452 14a90002
0x0032e5f8:  0d4aea18 00663654 0d4aea18 14a90006
0x0032e608:  0d49b7d5 14a90006 0d4aea18 14a90006
0x0032e618:  0d4aea3c 00000020 0d4aea18 0d4998da
0x0032e628:  14a90001 ffffffff 00000000 00000009
0x0032e638:  0032ff08 0032e67c 1000753b 00000003
Backtrace:
=>0 0x0d49b423 in datacache (+0xb423) (0x00000002)
  1 0x00000000 (0x00000000)
0x0d49b423: movl    0x24(%ebx),%eax
Modules:
Module    Address            Debug info    Name (201 modules)
PE      330000-  366000    Deferred        tier0
PE      370000-  38e000    Deferred        vstdlib
PE      390000-  3e4000    Deferred        filesystem_steam
PE      3f0000-  3ff000    Deferred        unicode
PE      400000-  41c000    Deferred        hl2
PE     d240000- d33e000    Deferred        datamodel
PE     d450000- d48d000    Deferred        dmserializers
PE     d490000- d4b5000    Export          datacache
PE     d4c0000- d4d4000    Deferred        inputsystem
PE     d5f0000- d6a5000    Deferred        materialsystem
PE     d6b0000- d6c6000    Deferred        valve_avi
PE     d6d0000- d7a0000    Deferred        vguimatsurface
PE     d7a0000- d815000    Deferred        vgui2
PE     d820000- d834000    Deferred        steam_api
PE     d950000- d979000    Deferred        stdshader_dbg
PE     d980000- d9b5000    Deferred        stdshader_dx6
PE     d9c0000- d9e8000    Deferred        stdshader_dx7
PE     d9f0000- da33000    Deferred        stdshader_dx8
PE     da40000- da91000    Deferred        stdshader_dx9
PE     daa0000- dad6000    Deferred        soundemittersystem
PE     dae0000- dafb000    Deferred        scenefilecache
PE     f0f0000- f2d3000    Deferred        gameui
PE     f700000- fa05000    Deferred        steamclient
PE     fa10000- fa7b000    Deferred        vstdlib_s
PE     fa80000- fb26000    Deferred        tier0_s
PE     fc40000- fd6d000    Deferred        p2pvoice
PE    10000000-10030000    Deferred        launcher
PE    116e0000-11707000    Deferred        vaudio_speex
PE    11810000-11818000    Deferred        xpcom
PE    11820000-1185b000    Deferred        nspr4
PE    11860000-1186a000    Deferred        plds4
PE    11870000-1193b000    Deferred        serverbrowser
PE    11af0000-11b00000    Deferred        vaudio_miles
PE    11b00000-11b64000    Deferred        mss32
PE    13c30000-13c45000    Deferred        nssutil3
PE    13c50000-13c5a000    Deferred        plc4
PE    15d00000-15d21000    Deferred        smime3
PE    16030000-16059000    Deferred        ssl3
PE    1f450000-1f513000    Deferred        js3250
PE    1f520000-1f5fe000    Deferred        nss3
PE    1f600000-1f679000    Deferred        sqlite3
PE    20000000-205ef000    Deferred        engine
PE    21100000-211ad000    Deferred        mss32_s
PE    22000000-22642000    Deferred        server
PE    22650000-2383b000    Deferred        xul
PE    24000000-24476000    Deferred        client
PE    26000000-26138000    Deferred        vphysics
PE    26400000-26439000    Deferred        mssvoice.asi
PE    26f00000-26f2e000    Deferred        mssmp3.asi
PE    2a000000-2a0a8000    Deferred        shaderapidx9
PE    2c000000-2c3e3000    Deferred        studiorender
PE    30000000-302c1000    Deferred        steam
PE    60000000-60021000    Deferred        cserhelper
PE    628c0000-628d9000    Deferred        parsifal
ELF    78b27000-78b36000    Deferred        libgcc_s.so.1
ELF    790d6000-79120000    Deferred        jscript<elf>
  \-PE    790e0000-79120000    \               jscript
ELF    79120000-79134000    Deferred        t2embed<elf>
  \-PE    79130000-79134000    \               t2embed
ELF    79234000-79238000    Deferred        libkeyutils.so.1
ELF    79238000-79241000    Deferred        libkrb5support.so.0
ELF    79241000-79265000    Deferred        libk5crypto.so.3
ELF    79265000-792f7000    Deferred        libkrb5.so.3
ELF    792f7000-79322000    Deferred        libgssapi_krb5.so.2
ELF    79322000-79359000    Deferred        libcups.so.2
ELF    79361000-79376000    Deferred        dwmapi<elf>
  \-PE    79370000-79376000    \               dwmapi
ELF    79376000-7938f000    Deferred        usp10<elf>
  \-PE    79380000-7938f000    \               usp10
ELF    7938f000-793a3000    Deferred        msimg32<elf>
  \-PE    79390000-793a3000    \               msimg32
ELF    793a3000-793d9000    Deferred        winspool<elf>
  \-PE    793b0000-793d9000    \               winspool
ELF    793d9000-7948b000    Deferred        comdlg32<elf>
  \-PE    793e0000-7948b000    \               comdlg32
ELF    7948b000-794f9000    Deferred        msvcrt<elf>
  \-PE    794a0000-794f9000    \               msvcrt
ELF    7b800000-7b948000    Deferred        kernel32<elf>
  \-PE    7b820000-7b948000    \               kernel32
ELF    7b948000-7b94c000    Deferred        libcom_err.so.2
ELF    7b94c000-7ba07000    Deferred        mshtml<elf>
  \-PE    7b960000-7ba07000    \               mshtml
ELF    7ba07000-7ba4a000    Deferred        urlmon<elf>
  \-PE    7ba10000-7ba4a000    \               urlmon
ELF    7bbc0000-7bc00000    Deferred        shdocvw<elf>
  \-PE    7bbd0000-7bc00000    \               shdocvw
ELF    7bc00000-7bcb1000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb1000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c4d1000-7c53a000    Deferred        libgcrypt.so.11
ELF    7c53a000-7c5d7000    Deferred        libgnutls.so.26
ELF    7c5d7000-7c5fe000    Deferred        netapi32<elf>
  \-PE    7c5e0000-7c5fe000    \               netapi32
ELF    7c5fe000-7c629000    Deferred        secur32<elf>
  \-PE    7c610000-7c629000    \               secur32
ELF    7cc78000-7ccfb000    Deferred        crypt32<elf>
  \-PE    7cc80000-7ccfb000    \               crypt32
ELF    7ccfb000-7cd47000    Deferred        dsound<elf>
  \-PE    7cd00000-7cd47000    \               dsound
ELF    7cd55000-7cd5c000    Deferred        libnss_dns.so.2
ELF    7cd5c000-7cd60000    Deferred        libgpg-error.so.0
ELF    7cd60000-7cd64000    Deferred        iso8859-15.so
ELF    7cdba000-7dcd2000    Deferred        libglcore.so.1
ELF    7dcd2000-7dd8c000    Deferred        libgl.so.1
ELF    7dd8c000-7dd8f000    Deferred        libnss_mdns4_minimal.so.2
ELF    7dd8f000-7dda1000    Deferred        libtasn1.so.3
ELF    7dda9000-7ddbf000    Deferred        winejoystick<elf>
  \-PE    7ddb0000-7ddbf000    \               winejoystick
ELF    7ddbf000-7ddd5000    Deferred        psapi<elf>
  \-PE    7ddc0000-7ddd5000    \               psapi
ELF    7ddd5000-7de24000    Deferred        dbghelp<elf>
  \-PE    7dde0000-7de24000    \               dbghelp
ELF    7de24000-7df4c000    Deferred        wined3d<elf>
  \-PE    7de40000-7df4c000    \               wined3d
ELF    7df4c000-7df7d000    Deferred        d3d9<elf>
  \-PE    7df50000-7df7d000    \               d3d9
ELF    7df7d000-7dfa0000    Deferred        mpr<elf>
  \-PE    7df80000-7dfa0000    \               mpr
ELF    7dfa0000-7dff2000    Deferred        wininet<elf>
  \-PE    7dfb0000-7dff2000    \               wininet
ELF    7dff2000-7e0d9000    Deferred        oleaut32<elf>
  \-PE    7e010000-7e0d9000    \               oleaut32
ELF    7e0d9000-7e0ff000    Deferred        msvfw32<elf>
  \-PE    7e0e0000-7e0ff000    \               msvfw32
ELF    7e0ff000-7e13b000    Deferred        avifil32<elf>
  \-PE    7e110000-7e13b000    \               avifil32
ELF    7e13b000-7e150000    Deferred        midimap<elf>
  \-PE    7e140000-7e150000    \               midimap
ELF    7e150000-7e176000    Deferred        msacm32<elf>
  \-PE    7e160000-7e176000    \               msacm32
ELF    7e176000-7e17f000    Deferred        librt.so.1
ELF    7e17f000-7e247000    Deferred        libasound.so.2
ELF    7e24c000-7e264000    Deferred        msacm32<elf>
  \-PE    7e250000-7e264000    \               msacm32
ELF    7e264000-7e29b000    Deferred        winealsa<elf>
  \-PE    7e270000-7e29b000    \               winealsa
ELF    7e29b000-7e332000    Deferred        winmm<elf>
  \-PE    7e2b0000-7e332000    \               winmm
ELF    7e3c8000-7e3fc000    Deferred        uxtheme<elf>
  \-PE    7e3d0000-7e3fc000    \               uxtheme
ELF    7e3fc000-7e410000    Deferred        lz32<elf>
  \-PE    7e400000-7e410000    \               lz32
ELF    7e410000-7e4d8000    Deferred        comctl32<elf>
  \-PE    7e420000-7e4d8000    \               comctl32
ELF    7e4d8000-7e536000    Deferred        shlwapi<elf>
  \-PE    7e4f0000-7e536000    \               shlwapi
ELF    7e536000-7e6c0000    Deferred        shell32<elf>
  \-PE    7e550000-7e6c0000    \               shell32
ELF    7e6c0000-7e72c000    Deferred        rpcrt4<elf>
  \-PE    7e6d0000-7e72c000    \               rpcrt4
ELF    7e72c000-7e827000    Deferred        ole32<elf>
  \-PE    7e740000-7e827000    \               ole32
ELF    7e827000-7e83d000    Deferred        libresolv.so.2
ELF    7e83d000-7e83f000    Deferred        libnvidia-tls.so.1
ELF    7e83f000-7e85a000    Deferred        version<elf>
  \-PE    7e840000-7e85a000    \               version
ELF    7e85a000-7e87a000    Deferred        iphlpapi<elf>
  \-PE    7e860000-7e87a000    \               iphlpapi
ELF    7e87a000-7e8a8000    Deferred        ws2_32<elf>
  \-PE    7e880000-7e8a8000    \               ws2_32
ELF    7e8a8000-7e8b1000    Deferred        libxcursor.so.1
ELF    7e8b1000-7e8b6000    Deferred        libxfixes.so.3
ELF    7e8b6000-7e8ba000    Deferred        libxcomposite.so.1
ELF    7e8ba000-7e8c2000    Deferred        libxrandr.so.2
ELF    7e8c2000-7e8cc000    Deferred        libxrender.so.1
ELF    7e8cc000-7e8d2000    Deferred        libxxf86vm.so.1
ELF    7e8d2000-7e8f3000    Deferred        imm32<elf>
  \-PE    7e8e0000-7e8f3000    \               imm32
ELF    7e8f3000-7e8f8000    Deferred        libxdmcp.so.6
ELF    7e8f8000-7e912000    Deferred        libxcb.so.1
ELF    7e912000-7e916000    Deferred        libxau.so.6
ELF    7e916000-7e91b000    Deferred        libuuid.so.1
ELF    7e91b000-7ea0a000    Deferred        libx11.so.6
ELF    7ea0a000-7ea1a000    Deferred        libxext.so.6
ELF    7ea1a000-7ea32000    Deferred        libice.so.6
ELF    7ea32000-7ea3b000    Deferred        libsm.so.6
ELF    7ea3b000-7ea56000    Deferred        wsock32<elf>
  \-PE    7ea40000-7ea56000    \               wsock32
ELF    7ea58000-7eaf4000    Deferred        winex11<elf>
  \-PE    7ea70000-7eaf4000    \               winex11
ELF    7eb48000-7eb6f000    Deferred        libexpat.so.1
ELF    7eb6f000-7eb9c000    Deferred        libfontconfig.so.1
ELF    7eb9c000-7ebb2000    Deferred        libz.so.1
ELF    7ebb2000-7ec29000    Deferred        libfreetype.so.6
ELF    7ec29000-7ec7f000    Deferred        advapi32<elf>
  \-PE    7ec40000-7ec7f000    \               advapi32
ELF    7ec7f000-7ed20000    Deferred        gdi32<elf>
  \-PE    7ec90000-7ed20000    \               gdi32
ELF    7ed20000-7ee6b000    Deferred        user32<elf>
  \-PE    7ed40000-7ee6b000    \               user32
ELF    7ef8d000-7ef99000    Deferred        libnss_files.so.2
ELF    7ef99000-7efa4000    Deferred        libnss_nis.so.2
ELF    7efa4000-7efbd000    Deferred        libnsl.so.1
ELF    7efbd000-7efe3000    Deferred        libm.so.6
ELF    7efe3000-7efe6000    Deferred        libxinerama.so.1
ELF    f7c40000-f7c49000    Deferred        libnss_compat.so.2
ELF    f7c4a000-f7c4e000    Deferred        libdl.so.2
ELF    f7c4e000-f7db1000    Deferred        libc.so.6
ELF    f7db2000-f7dcb000    Deferred        libpthread.so.0
ELF    f7de8000-f7f23000    Deferred        libwine.so.1
ELF    f7f25000-f7f46000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
    00000043    1
    00000065    1
    00000042    0
    00000041    1
    00000040    1
    0000003f    1
    0000003e    1
    0000003d    1
    0000003c    1
    0000003b    1
    0000003a    1
    00000035    0
    00000030    0
    0000002f    0
    0000002d    1
    0000002b    0
    00000029   15
    00000027    0
    00000026    0
    00000023    0
    00000020    0
    0000001f    1
    0000001e    0
    0000001d    0
    0000001c    0
    0000001b    0
    0000001a    0
    00000019    0
    00000018    0
    00000009    0
0000000c 
    00000024    0
    00000034    0
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
00000061 (D) D:\Games\Steam\steamapps\[SENSORED K18]\counter-strike source\hl2.exe
    0000002a    0
    0000002c    0
    00000025    0
    00000021    0
    0000002e    0
    00000033    0
    0000004d    0
    00000022    0
    0000004b   15
    00000048    2
    00000067    0
    00000066    0
    00000064    0
    00000063    2
    00000062    0 <==
Backtrace:
=>0 0x0d49b423 in datacache (+0xb423) (0x00000002)
  1 0x00000000 (0x00000000)
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```Ubuntu 9.04 (x64), Wine 1.1.22, nvidia 180.44, GeForce 8800 GT

In game settings have not touched, did work ok with wine 1.1.21. Only updated wine today morning :)

Tried:
 - -dxlevel 90, 81, 70 -> crash.
 - Windows 98 mode -> crash.
 - nvidia 180.51 -> crash.
 - downgrading wine to 1.1.21 -> WORKS! ;)

Only me with this?

---

### Post by sickwookie on 2009-05-23
I am not sure if it is related, but I am crashing in TF2 after the update this morning to 1.1.22. It happens after launching TF2 and just before the main menu is displayed.

err:d3d_surface:IWineD3DSurfaceImpl_ModifyLocation 0x189ed0: Surface does not have any up to date location

---

### Post by diagram30 on 2009-05-24
Are you running hl2.exe in the win98 mode?

---

### Post by asdfoo on 2009-05-24
both tf2 and cs:s work ok here with 1.1.22.  nv gf8800 gts. 180.51

---

### Post by 8Kuula on 2009-05-24
> **diagram30 said:**
> Are you running hl2.exe in the win98 mode?

Tried -> crash.

---

### Post by 8Kuula on 2009-05-24
Tried with nvidia 180.51 drivers. Crashes still :(

---

### Post by cactuar32 on 2009-05-25
I've also suffered from TF2 crashing since updating to wine 1.1.22. - 9.04, nv 8400MGS with 180.44 drivers.

---

### Post by Duskao on 2009-05-25
Then use 1.1.21 and submit a bug for 1.1.22 in bugzilla at winehq.

---

### Post by u235sentinel on 2009-05-25
Perhaps try something like this for your command line

WINEDEBUG=-all env WINEPREFIX="/home/xxx/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 240 -high -noforcemaccel -noforcemparams -noipx -nojoy -dxlevel 81 -heapsize 256000 -novid -width 1024 -height 768

This is how I start my games like css.  Give it a try and see if it helps.

I haven't tried 1.1.22 yet but perhaps in a day or two when I have some free time I will.

---

### Post by 8Kuula on 2009-05-26
> **u235sentinel said:**
> Perhaps try something like this for your command line

WINEDEBUG=-all env WINEPREFIX="/home/xxx/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 240 -high -noforcemaccel -noforcemparams -noipx -nojoy -dxlevel 81 -heapsize 256000 -novid -width 1024 -height 768

This is how I start my games like css.  Give it a try and see if it helps.

I haven't tried 1.1.22 yet but perhaps in a day or two when I have some free time I will.

Crash :(
Same place than before, spawning in game -> round start -> all freeze, wine crash message pops up -> I click ok -> back on desktop.

```

bunbun@triton:~/OS/Windows/Games/Steam# WINEDEBUG=-all env WINEPREFIX="/home/bunbun/.wine" wine steam.exe -applaunch 240 -high -noforcemaccel -noforcemparams -noipx -nojoy -dxlevel 81 -heapsize 256000 -novid -width 1024 -height 768
wine: configuration in '/home/bunbun/.wine' has been updated.
CellID: Fetching server list from CSDS. . .
CellID: CSDS returned 168 servers.
CellID: Connecting to 203.77.185.5:27031. . .
CellID: Connect to 203.77.185.5:27031 took 389 MS
CellID: Nothing beat our old best time of 49 MS
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
wine: Unhandled page fault on read access to 0x00000024 at address 0xd4ab423 (thread 001b), starting debugger...
Unhandled exception: page fault on read access to 0x00000024 in 32-bit code (0x0d4ab423).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0d4ab423 ESP:0033e5e8 EBP:00000002 EFLAGS:00010216(  R- --  I   -A-P- )
 EAX:00000250 EBX:00000000 ECX:0cb81800 EDX:07365840
 ESI:0d4bea18 EDI:00000090
Stack dump:
0x0033e5e8:  0d4bea18 00664334 0d4ab452 0cb80025
0x0033e5f8:  0d4bea18 00664334 0d4bea18 0cb80029
0x0033e608:  0d4ab7d5 0cb80029 0d4bea18 0cb80029
0x0033e618:  0d4bea3c 00000250 0d4bea18 0d4a98da
0x0033e628:  0cb80001 ffffffff 00000000 00000009
0x0033e638:  0033ff08 0033e67c 1000753b 00000003
Backtrace:
=>0 0x0d4ab423 in datacache (+0xb423) (0x00000002)
  1 0x00000000 (0x00000000)
0x0d4ab423: movl    0x24(%ebx),%eax
Modules:
Module    Address            Debug info    Name (201 modules)
PE      340000-  376000    Deferred        tier0
PE      380000-  39e000    Deferred        vstdlib
PE      3a0000-  3f4000    Deferred        filesystem_steam
PE      400000-  41c000    Deferred        hl2
PE     cf50000- cf64000    Deferred        inputsystem
PE     d250000- d34e000    Deferred        datamodel
PE     d460000- d49d000    Deferred        dmserializers
PE     d4a0000- d4c5000    Export          datacache
PE     d5e0000- d695000    Deferred        materialsystem
PE     d6a0000- d6b6000    Deferred        valve_avi
PE     d6c0000- d790000    Deferred        vguimatsurface
PE     d790000- d805000    Deferred        vgui2
PE     d810000- d824000    Deferred        steam_api
PE     da50000- da79000    Deferred        stdshader_dbg
PE     da80000- dab5000    Deferred        stdshader_dx6
PE     dac0000- dae8000    Deferred        stdshader_dx7
PE     daf0000- db33000    Deferred        stdshader_dx8
PE     db40000- db91000    Deferred        stdshader_dx9
PE     dba0000- dbaf000    Deferred        unicode
PE     dbb0000- dbe6000    Deferred        soundemittersystem
PE     dbf0000- dc0b000    Deferred        scenefilecache
PE     eae0000- ecc3000    Deferred        gameui
PE     eef0000- f1f5000    Deferred        steamclient
PE     f200000- f26b000    Deferred        vstdlib_s
PE     f270000- f316000    Deferred        tier0_s
PE     f430000- f55d000    Deferred        p2pvoice
PE    10000000-10030000    Deferred        launcher
PE    20000000-205ef000    Deferred        engine
PE    209c0000-209e7000    Deferred        vaudio_speex
PE    20af0000-20af8000    Deferred        xpcom
PE    20b00000-20b3b000    Deferred        nspr4
PE    20b40000-20b4a000    Deferred        plds4
PE    20b50000-20c1b000    Deferred        serverbrowser
PE    20dd0000-20de0000    Deferred        vaudio_miles
PE    20de0000-20e44000    Deferred        mss32
PE    210c0000-210d5000    Deferred        nssutil3
PE    210e0000-210ea000    Deferred        plc4
PE    21100000-211ad000    Deferred        mss32_s
PE    21e60000-21e81000    Deferred        smime3
PE    21fc0000-21fe9000    Deferred        ssl3
PE    22000000-22642000    Deferred        server
PE    24000000-24476000    Deferred        client
PE    26000000-26138000    Deferred        vphysics
PE    26380000-263f9000    Deferred        sqlite3
PE    26400000-26439000    Deferred        mssvoice.asi
PE    26f00000-26f2e000    Deferred        mssmp3.asi
PE    28c00000-29deb000    Deferred        xul
PE    29df0000-29eb3000    Deferred        js3250
PE    29ec0000-29f9e000    Deferred        nss3
PE    2a000000-2a0a8000    Deferred        shaderapidx9
PE    2c000000-2c3e3000    Deferred        studiorender
PE    30000000-302c1000    Deferred        steam
PE    60000000-60021000    Deferred        cserhelper
PE    628c0000-628d9000    Deferred        parsifal
ELF    7985c000-7986b000    Deferred        libgcc_s.so.1
ELF    79d8a000-79dd4000    Deferred        jscript<elf>
  \-PE    79d90000-79dd4000    \               jscript
ELF    79dd4000-79de8000    Deferred        t2embed<elf>
  \-PE    79de0000-79de8000    \               t2embed
ELF    79ee8000-79eec000    Deferred        libkeyutils.so.1
ELF    79eec000-79ef5000    Deferred        libkrb5support.so.0
ELF    79ef5000-79ef9000    Deferred        libcom_err.so.2
ELF    79ef9000-79f1d000    Deferred        libk5crypto.so.3
ELF    79f1d000-79faf000    Deferred        libkrb5.so.3
ELF    79faf000-79fda000    Deferred        libgssapi_krb5.so.2
ELF    79fda000-7a011000    Deferred        libcups.so.2
ELF    7a019000-7a02e000    Deferred        dwmapi<elf>
  \-PE    7a020000-7a02e000    \               dwmapi
ELF    7a02e000-7a047000    Deferred        usp10<elf>
  \-PE    7a030000-7a047000    \               usp10
ELF    7a047000-7a05b000    Deferred        msimg32<elf>
  \-PE    7a050000-7a05b000    \               msimg32
ELF    7a05b000-7a091000    Deferred        winspool<elf>
  \-PE    7a060000-7a091000    \               winspool
ELF    7a091000-7a143000    Deferred        comdlg32<elf>
  \-PE    7a0a0000-7a143000    \               comdlg32
ELF    7a143000-7a1b1000    Deferred        msvcrt<elf>
  \-PE    7a150000-7a1b1000    \               msvcrt
ELF    7a1b1000-7a26c000    Deferred        mshtml<elf>
  \-PE    7a1c0000-7a26c000    \               mshtml
ELF    7a26c000-7a2af000    Deferred        urlmon<elf>
  \-PE    7a270000-7a2af000    \               urlmon
ELF    7aace000-7ab0e000    Deferred        shdocvw<elf>
  \-PE    7aae0000-7ab0e000    \               shdocvw
ELF    7b800000-7b948000    Deferred        kernel32<elf>
  \-PE    7b820000-7b948000    \               kernel32
ELF    7bc00000-7bcb1000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb1000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c41d000-7c486000    Deferred        libgcrypt.so.11
ELF    7c486000-7c523000    Deferred        libgnutls.so.26
ELF    7c540000-7c567000    Deferred        netapi32<elf>
  \-PE    7c550000-7c567000    \               netapi32
ELF    7c567000-7c5ea000    Deferred        crypt32<elf>
  \-PE    7c570000-7c5ea000    \               crypt32
ELF    7cb6d000-7cb98000    Deferred        secur32<elf>
  \-PE    7cb70000-7cb98000    \               secur32
ELF    7cbe2000-7cc2e000    Deferred        dsound<elf>
  \-PE    7cbf0000-7cc2e000    \               dsound
ELF    7cd2a000-7cd3c000    Deferred        libtasn1.so.3
ELF    7cdb1000-7dcc9000    Deferred        libglcore.so.1
ELF    7dcc9000-7dd83000    Deferred        libgl.so.1
ELF    7dd86000-7dd8d000    Deferred        libnss_dns.so.2
ELF    7dd8d000-7dd90000    Deferred        libnss_mdns4_minimal.so.2
ELF    7dd90000-7dd94000    Deferred        libgpg-error.so.0
ELF    7dd94000-7dd98000    Deferred        iso8859-15.so
ELF    7dda0000-7ddb6000    Deferred        winejoystick<elf>
  \-PE    7ddb0000-7ddb6000    \               winejoystick
ELF    7ddb6000-7ddcc000    Deferred        psapi<elf>
  \-PE    7ddc0000-7ddcc000    \               psapi
ELF    7ddcc000-7de1b000    Deferred        dbghelp<elf>
  \-PE    7ddd0000-7de1b000    \               dbghelp
ELF    7de1b000-7df43000    Deferred        wined3d<elf>
  \-PE    7de30000-7df43000    \               wined3d
ELF    7df43000-7df74000    Deferred        d3d9<elf>
  \-PE    7df50000-7df74000    \               d3d9
ELF    7df74000-7df97000    Deferred        mpr<elf>
  \-PE    7df80000-7df97000    \               mpr
ELF    7df97000-7dfe9000    Deferred        wininet<elf>
  \-PE    7dfa0000-7dfe9000    \               wininet
ELF    7dfe9000-7e0d0000    Deferred        oleaut32<elf>
  \-PE    7e000000-7e0d0000    \               oleaut32
ELF    7e0d0000-7e0f6000    Deferred        msvfw32<elf>
  \-PE    7e0e0000-7e0f6000    \               msvfw32
ELF    7e0f6000-7e132000    Deferred        avifil32<elf>
  \-PE    7e100000-7e132000    \               avifil32
ELF    7e132000-7e147000    Deferred        midimap<elf>
  \-PE    7e140000-7e147000    \               midimap
ELF    7e147000-7e16d000    Deferred        msacm32<elf>
  \-PE    7e150000-7e16d000    \               msacm32
ELF    7e16d000-7e176000    Deferred        librt.so.1
ELF    7e176000-7e23e000    Deferred        libasound.so.2
ELF    7e243000-7e25b000    Deferred        msacm32<elf>
  \-PE    7e250000-7e25b000    \               msacm32
ELF    7e25b000-7e292000    Deferred        winealsa<elf>
  \-PE    7e260000-7e292000    \               winealsa
ELF    7e292000-7e329000    Deferred        winmm<elf>
  \-PE    7e2a0000-7e329000    \               winmm
ELF    7e3bf000-7e3f3000    Deferred        uxtheme<elf>
  \-PE    7e3d0000-7e3f3000    \               uxtheme
ELF    7e3f3000-7e407000    Deferred        lz32<elf>
  \-PE    7e400000-7e407000    \               lz32
ELF    7e407000-7e4cf000    Deferred        comctl32<elf>
  \-PE    7e410000-7e4cf000    \               comctl32
ELF    7e4cf000-7e52d000    Deferred        shlwapi<elf>
  \-PE    7e4e0000-7e52d000    \               shlwapi
ELF    7e52d000-7e6b7000    Deferred        shell32<elf>
  \-PE    7e540000-7e6b7000    \               shell32
ELF    7e6b7000-7e723000    Deferred        rpcrt4<elf>
  \-PE    7e6c0000-7e723000    \               rpcrt4
ELF    7e723000-7e81e000    Deferred        ole32<elf>
  \-PE    7e740000-7e81e000    \               ole32
ELF    7e81e000-7e834000    Deferred        libresolv.so.2
ELF    7e834000-7e836000    Deferred        libnvidia-tls.so.1
ELF    7e836000-7e851000    Deferred        version<elf>
  \-PE    7e840000-7e851000    \               version
ELF    7e851000-7e871000    Deferred        iphlpapi<elf>
  \-PE    7e860000-7e871000    \               iphlpapi
ELF    7e871000-7e89f000    Deferred        ws2_32<elf>
  \-PE    7e880000-7e89f000    \               ws2_32
ELF    7e89f000-7e8a8000    Deferred        libxcursor.so.1
ELF    7e8a8000-7e8ad000    Deferred        libxfixes.so.3
ELF    7e8ad000-7e8b1000    Deferred        libxcomposite.so.1
ELF    7e8b1000-7e8b9000    Deferred        libxrandr.so.2
ELF    7e8b9000-7e8c3000    Deferred        libxrender.so.1
ELF    7e8c3000-7e8c9000    Deferred        libxxf86vm.so.1
ELF    7e8c9000-7e8cc000    Deferred        libxinerama.so.1
ELF    7e8cc000-7e8ed000    Deferred        imm32<elf>
  \-PE    7e8d0000-7e8ed000    \               imm32
ELF    7e8ed000-7e8f2000    Deferred        libxdmcp.so.6
ELF    7e8f2000-7e90c000    Deferred        libxcb.so.1
ELF    7e90c000-7e910000    Deferred        libxau.so.6
ELF    7e910000-7e915000    Deferred        libuuid.so.1
ELF    7e915000-7ea04000    Deferred        libx11.so.6
ELF    7ea04000-7ea14000    Deferred        libxext.so.6
ELF    7ea14000-7ea2c000    Deferred        libice.so.6
ELF    7ea2c000-7ea35000    Deferred        libsm.so.6
ELF    7ea35000-7ea50000    Deferred        wsock32<elf>
  \-PE    7ea40000-7ea50000    \               wsock32
ELF    7ea52000-7eaee000    Deferred        winex11<elf>
  \-PE    7ea60000-7eaee000    \               winex11
ELF    7eb3b000-7eb62000    Deferred        libexpat.so.1
ELF    7eb62000-7eb8f000    Deferred        libfontconfig.so.1
ELF    7eb8f000-7eba5000    Deferred        libz.so.1
ELF    7eba5000-7ec1c000    Deferred        libfreetype.so.6
ELF    7ec1c000-7ec72000    Deferred        advapi32<elf>
  \-PE    7ec30000-7ec72000    \               advapi32
ELF    7ec72000-7ed13000    Deferred        gdi32<elf>
  \-PE    7ec80000-7ed13000    \               gdi32
ELF    7ed13000-7ee5e000    Deferred        user32<elf>
  \-PE    7ed30000-7ee5e000    \               user32
ELF    7ee5e000-7ee6a000    Deferred        libnss_files.so.2
ELF    7ee6a000-7ee75000    Deferred        libnss_nis.so.2
ELF    7ee75000-7ee7e000    Deferred        libnss_compat.so.2
ELF    7efbd000-7efe3000    Deferred        libm.so.6
ELF    7efe7000-7f000000    Deferred        libnsl.so.1
ELF    f7c12000-f7c16000    Deferred        libdl.so.2
ELF    f7c16000-f7d79000    Deferred        libc.so.6
ELF    f7d7a000-f7d93000    Deferred        libpthread.so.0
ELF    f7db0000-f7eeb000    Deferred        libwine.so.1
ELF    f7eed000-f7f0e000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
    00000037    1
    0000000b    1
    0000001f    0
    00000020    0
    0000001a    0
    00000047    1
    00000046    1
    00000045    1
    00000044    1
    00000043    1
    00000042    1
    00000041    1
    00000040    1
    0000003e    0
    0000003b    0
    0000003a    1
    00000039    0
    00000038    0
    00000036    1
    00000034    0
    00000032   15
    00000030    0
    0000002f    0
    0000002c    0
    0000002a    0
    00000029    1
    00000028    0
    00000027    0
    00000026    0
    00000025    0
    00000024    0
    00000023    0
    00000022    0
    00000009    0
0000000c 
    00000014    0
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
00000021 (D) D:\Games\Steam\steamapps\[sensored-k18]\counter-strike source\hl2.exe
    0000004b    0
    00000049    0
    00000013    0
    00000019    0
    0000003f    0
    0000003d    0
    00000035    0
    00000033    0
    0000002e   15
    0000002d    2
    0000002b    0
    0000001e    0
    0000001d    0
    0000001c    2
    0000001b    0 <==
Backtrace:
=>0 0x0d4ab423 in datacache (+0xb423) (0x00000002)
  1 0x00000000 (0x00000000)

```This is now with nvidia 180.51, did not downgrade that after that test.
So 9.04 (x64), wine 1.1.22, nvidia 180.51, GeForce 8800 GT

---

### Post by mynameisfiber on 2009-06-04
I am having the same problem.  My hardware is:

*i7 920
*nvidia 9600GT
*Asus p6t v2 deluxe

Also, I'm running the nvidia drivers (v180) at 1920x1080 and wine v1.1.22.

---

### Post by ross232 on 2009-06-04
I also have this problem. I have tried disabling Pulse Audio (even completely removing it from my system). I have hl2.exe set to run in win98 mode as well. Crashes for me result in a hard lockup of the system. I am unable to even access another terminal with ALT + F2 and have to reset my machine.

Annoyingly, the game plays really well otherwise- 80+fps in DirectX9 mode. I have spent many hours on this issue but can't resolve it.

Hardware:

Dell Studio 1555 Laptop
Core 2 Duo 2.4ghz P8600 CPU
512mb ATi 4570HD Graphics

Wine 1.0.1 and 1.1.xx up until 1.1.22.

---

### Post by wootah on 2009-06-06
I have the same issue with 1.1.22. I am running 9.04 with an ATI Mobile HD 3400 on my laptop.

Proprietary drivers (fglrx) with most current driver version.

Downgrade to version 1.1.20 works... but I have a crash after 5 minutes of game play. Does anyone know what causes this or the above problem?

What's the best version to use?

---

### Post by NightMKoder on 2009-06-07
There is a good chance [http://source.winehq.org/git/wine.git/?a=commitdiff;h=13a33b73c349530b17347d3ec6a1f5bb268cc917](http://source.winehq.org/git/wine.git/?a=commitdiff;h=13a33b73c349530b17347d3ec6a1f5bb268cc917) broke it, but there is no fix. That commit has been known to break a couple of games.

---

### Post by 8Kuula on 2009-06-07
Upgrade to wine 1.1.23, seems to work. Atleast no more crashing on spawn.

---

### Post by Technophobia on 2009-06-11
I'm still crashing all over the place with 1.1.23.

I launch Steam with:

env WINEPREFIX="/home/mark/.wine" wine "C:\Program Files\Steam\Steam.exe"

and CS:S with:

-dxlevel 80

---

### Post by NightMKoder on 2009-06-11
> **Technophobia said:**
> I'm still crashing all over the place with 1.1.23.

I launch Steam with:

env WINEPREFIX="/home/mark/.wine" wine "C:\Program Files\Steam\Steam.exe"

and CS:S with:

-dxlevel 80

If you're on ati set offscreenrenderingmode to backbuffer (look it up).

---

### Post by MysteriousKnight on 2009-06-14
Crashing should stop when you do this:

**Game crashes after a few minutes. **You can fix this by putting [this file]("http://bugs.winehq.org/attachment.cgi?id=18679") into your "~/.wine/drive_c/Program Files/Steam/steamapps/YOURUSERNAME/counter-strike source/cstrike/resource" folder, or by applying [this patch]("http://bugs.winehq.org/attachment.cgi?id=6853"). See [bug #7698]("http://bugs.winehq.org/show_bug.cgi?id=7698") for more information. 

ThAnx to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)

---

### Post by DenBona on 2009-07-29
> **MysteriousKnight said:**
> Crashing should stop when you do this:

**Game crashes after a few minutes. **You can fix this by putting [this file]("http://bugs.winehq.org/attachment.cgi?id=18679") into your "~/.wine/drive_c/Program Files/Steam/steamapps/YOURUSERNAME/counter-strike source/cstrike/resource" folder, or by applying [this patch]("http://bugs.winehq.org/attachment.cgi?id=6853"). See [bug #7698]("http://bugs.winehq.org/show_bug.cgi?id=7698") for more information. 

ThAnx to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)

THX alot, i've been looking for days for this solution, i just added the firs file and everything fell into place

  you saved my evening !

---

