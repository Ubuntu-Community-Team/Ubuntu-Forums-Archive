---
title: "cant install Eve Online :("
date: 2020-06-26
forum: Ubuntu/Debian BASED
---

### Post by corporal-canada on 2020-06-26
hi, im using Linux Mint with wine 1.6...... and im a total noob but in the past ive never had trouble installing eve online... but now the installer wont even start.... 

the following is the error msg i get

```
---------------------------------------------
Unhandled exception: unimplemented function bcrypt.dll.BCryptGenRandom called in 32-bit code (0x7b83aace).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b83aace ESP:0033f9b4 EBP:0033fa28 EFLAGS:00000283(   - --  I S - - -C)
 EAX:7b82695d EBX:7b8b5000 ECX:00000008 EDX:0033f9d4
 ESI:80000100 EDI:0016ceb0
Stack dump:
0x0033f9b4:  0033fa54 00000008 0016cea8 80000100
0x0033f9c4:  00000001 00000000 7b83aace 00000002
0x0033f9d4:  7dd0c4c4 7dd0c6ea 00000000 00000000
0x0033f9e4:  00000000 4d430000 0016cf10 00000000
0x0033f9f4:  00000000 00000000 00000000 00000000
0x0033fa04:  00000000 0033fa30 7bcbf000 0016ce68
Backtrace:
=>0 0x7b83aace in kernel32 (+0x2aace) (0x0033fa28)
  1 0x7dd0c4a8 in bcrypt (+0xc4a7) (0x0033fa64)
  2 0x7dd0bc45 in bcrypt (+0xbc44) (0x00000020)
0x7b83aace: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (91 modules)
PE      400000- 18f5000    Export          evelauncher-1747682
ELF    7b800000-7ba5b000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba5b000    \               kernel32
ELF    7bc00000-7bcdb000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcdb000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d883000-7d8a2000    Deferred        wintab32<elf>
  \-PE    7d890000-7d8a2000    \               wintab32
ELF    7d8e8000-7d8ee000    Deferred        libxfixes.so.3
ELF    7d8ee000-7d8f9000    Deferred        libxcursor.so.1
ELF    7d8f9000-7d909000    Deferred        libxi.so.6
ELF    7d909000-7d90d000    Deferred        libxcomposite.so.1
ELF    7d90d000-7d918000    Deferred        libxrandr.so.2
ELF    7d918000-7d923000    Deferred        libxrender.so.1
ELF    7d923000-7d929000    Deferred        libxxf86vm.so.1
ELF    7d929000-7d92d000    Deferred        libxinerama.so.1
ELF    7d92d000-7d934000    Deferred        libxdmcp.so.6
ELF    7d934000-7d938000    Deferred        libxau.so.6
ELF    7d938000-7d95a000    Deferred        libxcb.so.1
ELF    7d95a000-7da8e000    Deferred        libx11.so.6
ELF    7da8e000-7daa1000    Deferred        libxext.so.6
ELF    7dab9000-7db4b000    Deferred        winex11<elf>
  \-PE    7dac0000-7db4b000    \               winex11
ELF    7db9c000-7dbc5000    Deferred        libexpat.so.1
ELF    7dbc5000-7dc00000    Deferred        libfontconfig.so.1
ELF    7dc00000-7dc28000    Deferred        libpng12.so.0
ELF    7dc28000-7dc42000    Deferred        libz.so.1
ELF    7dc42000-7dce2000    Deferred        libfreetype.so.6
ELF    7dcfa000-7dd10000    Dwarf           bcrypt<elf>
  \-PE    7dd00000-7dd10000    \               bcrypt
ELF    7dd10000-7de1f000    Deferred        opengl32<elf>
  \-PE    7dd30000-7de1f000    \               opengl32
ELF    7de1f000-7df5f000    Deferred        wined3d<elf>
  \-PE    7de30000-7df5f000    \               wined3d
ELF    7df5f000-7df9c000    Deferred        d3d9<elf>
  \-PE    7df70000-7df9c000    \               d3d9
ELF    7df9c000-7dfc7000    Deferred        msacm32<elf>
  \-PE    7dfa0000-7dfc7000    \               msacm32
ELF    7dfc7000-7e081000    Deferred        winmm<elf>
  \-PE    7dfd0000-7e081000    \               winmm
ELF    7e081000-7e188000    Deferred        comctl32<elf>
  \-PE    7e090000-7e188000    \               comctl32
ELF    7e188000-7e202000    Deferred        shlwapi<elf>
  \-PE    7e1a0000-7e202000    \               shlwapi
ELF    7e202000-7e435000    Deferred        shell32<elf>
  \-PE    7e210000-7e435000    \               shell32
ELF    7e435000-7e44d000    Deferred        userenv<elf>
  \-PE    7e440000-7e44d000    \               userenv
ELF    7e44d000-7e47a000    Deferred        netapi32<elf>
  \-PE    7e450000-7e47a000    \               netapi32
ELF    7e47a000-7e4a2000    Deferred        mpr<elf>
  \-PE    7e480000-7e4a2000    \               mpr
ELF    7e4a2000-7e4d8000    Deferred        ws2_32<elf>
  \-PE    7e4b0000-7e4d8000    \               ws2_32
ELF    7e4d8000-7e5a7000    Deferred        crypt32<elf>
  \-PE    7e4e0000-7e5a7000    \               crypt32
ELF    7e5a7000-7e5cd000    Deferred        iphlpapi<elf>
  \-PE    7e5b0000-7e5cd000    \               iphlpapi
ELF    7e5cd000-7e5e3000    Deferred        dwmapi<elf>
  \-PE    7e5d0000-7e5e3000    \               dwmapi
ELF    7e5e3000-7e61a000    Deferred        uxtheme<elf>
  \-PE    7e5f0000-7e61a000    \               uxtheme
ELF    7e61a000-7e69b000    Deferred        rpcrt4<elf>
  \-PE    7e630000-7e69b000    \               rpcrt4
ELF    7e69b000-7e7d7000    Deferred        ole32<elf>
  \-PE    7e6b0000-7e7d7000    \               ole32
ELF    7e7d7000-7e90d000    Deferred        oleaut32<elf>
  \-PE    7e7f0000-7e90d000    \               oleaut32
ELF    7e90d000-7e927000    Deferred        version<elf>
  \-PE    7e910000-7e927000    \               version
ELF    7e927000-7e999000    Deferred        advapi32<elf>
  \-PE    7e930000-7e999000    \               advapi32
ELF    7e999000-7eab6000    Deferred        gdi32<elf>
  \-PE    7e9b0000-7eab6000    \               gdi32
ELF    7eab6000-7ec10000    Deferred        user32<elf>
  \-PE    7ead0000-7ec10000    \               user32
ELF    7ec10000-7ec35000    Deferred        imm32<elf>
  \-PE    7ec20000-7ec35000    \               imm32
ELF    7ec35000-7ec42000    Deferred        libnss_files.so.2
ELF    7ec42000-7ec4e000    Deferred        libnss_nis.so.2
ELF    7ec4e000-7ec67000    Deferred        libnsl.so.1
ELF    7ec67000-7ec70000    Deferred        libnss_compat.so.2
ELF    7efa2000-7efe8000    Deferred        libm.so.6
ELF    7efe8000-7f000000    Deferred        wtsapi32<elf>
  \-PE    7eff0000-7f000000    \               wtsapi32
ELF    b7408000-b75b6000    Deferred        libc.so.6
ELF    b75b6000-b75bb000    Deferred        libdl.so.2
ELF    b75bc000-b75d8000    Deferred        libpthread.so.0
ELF    b75f0000-b77a5000    Dwarf           libwine.so.1
ELF    b77a7000-b77c9000    Deferred        ld-linux.so.2
ELF    b77c9000-b77ca000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001e    0
    0000001d    0
    00000018    0
    00000016    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000017    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001f    0
    0000001b    0
00000021 explorer.exe
    00000023    0
    00000022    0
00000024 (D) Z:\home\chris\Downloads\EveLauncher-1747682.exe
    00000025    0 <==
System information:
    Wine build: wine-1.6.2
    Platform: i386
    Host system: Linux
    Host version: 3.16.0-38-generic

------------------------------------
```

keep your instructions simple as heck please....

---

### Post by howefield on 2020-06-26
Thread moved to the "Ubuntu/Debian BASED" forum.

Please enclose your error output n code tags.

---

### Post by corporal-canada on 2020-06-26
Please enclose your error output n code tag

what ?

---

### Post by CelticWarrior on 2020-06-26
It means please click the Go Advanced button below to open additional formatting options. Then click "#" and paste inside.

---

### Post by corporal-canada on 2020-06-26
i have no advanced button all i got is "show details" and "close"
and in show details i pasted the whole page

---

### Post by CelticWarrior on 2020-06-26
In the Quick Reply field **in this page** you have 3 buttons: "Post Quick Replay", "**Go Advanced**" and "Cancel".

---

### Post by QIII on 2020-06-26
I added code tags for you.  Please follow the instructions above in the future.

Thanks.

---

### Post by corporal-canada on 2020-06-26
```
Unhandled exception: unimplemented function bcrypt.dll.BCryptGenRandom called in 32-bit code (0x7b83aace).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b83aace ESP:0033f9b4 EBP:0033fa28 EFLAGS:00000283(   - --  I S - - -C)
 EAX:7b82695d EBX:7b8b5000 ECX:00000008 EDX:0033f9d4
 ESI:80000100 EDI:0016ceb0
Stack dump:
0x0033f9b4:  0033fa54 00000008 0016cea8 80000100
0x0033f9c4:  00000001 00000000 7b83aace 00000002
0x0033f9d4:  7dd0c4c4 7dd0c6ea 00000000 00000000
0x0033f9e4:  00000000 4d430000 0016cf10 00000000
0x0033f9f4:  00000000 00000000 00000000 00000000
0x0033fa04:  00000000 0033fa30 7bcbf000 0016ce68
Backtrace:
=>0 0x7b83aace in kernel32 (+0x2aace) (0x0033fa28)
  1 0x7dd0c4a8 in bcrypt (+0xc4a7) (0x0033fa64)
  2 0x7dd0bc45 in bcrypt (+0xbc44) (0x00000020)
0x7b83aace: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (91 modules)
PE      400000- 18f5000    Export          evelauncher-1747682
ELF    7b800000-7ba5b000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba5b000    \               kernel32
ELF    7bc00000-7bcdb000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcdb000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d883000-7d8a2000    Deferred        wintab32<elf>
  \-PE    7d890000-7d8a2000    \               wintab32
ELF    7d8e8000-7d8ee000    Deferred        libxfixes.so.3
ELF    7d8ee000-7d8f9000    Deferred        libxcursor.so.1
ELF    7d8f9000-7d909000    Deferred        libxi.so.6
ELF    7d909000-7d90d000    Deferred        libxcomposite.so.1
ELF    7d90d000-7d918000    Deferred        libxrandr.so.2
ELF    7d918000-7d923000    Deferred        libxrender.so.1
ELF    7d923000-7d929000    Deferred        libxxf86vm.so.1
ELF    7d929000-7d92d000    Deferred        libxinerama.so.1
ELF    7d92d000-7d934000    Deferred        libxdmcp.so.6
ELF    7d934000-7d938000    Deferred        libxau.so.6
ELF    7d938000-7d95a000    Deferred        libxcb.so.1
ELF    7d95a000-7da8e000    Deferred        libx11.so.6
ELF    7da8e000-7daa1000    Deferred        libxext.so.6
ELF    7dab9000-7db4b000    Deferred        winex11<elf>
  \-PE    7dac0000-7db4b000    \               winex11
ELF    7db9c000-7dbc5000    Deferred        libexpat.so.1
ELF    7dbc5000-7dc00000    Deferred        libfontconfig.so.1
ELF    7dc00000-7dc28000    Deferred        libpng12.so.0
ELF    7dc28000-7dc42000    Deferred        libz.so.1
ELF    7dc42000-7dce2000    Deferred        libfreetype.so.6
ELF    7dcfa000-7dd10000    Dwarf           bcrypt<elf>
  \-PE    7dd00000-7dd10000    \               bcrypt
ELF    7dd10000-7de1f000    Deferred        opengl32<elf>
  \-PE    7dd30000-7de1f000    \               opengl32
ELF    7de1f000-7df5f000    Deferred        wined3d<elf>
  \-PE    7de30000-7df5f000    \               wined3d
ELF    7df5f000-7df9c000    Deferred        d3d9<elf>
  \-PE    7df70000-7df9c000    \               d3d9
ELF    7df9c000-7dfc7000    Deferred        msacm32<elf>
  \-PE    7dfa0000-7dfc7000    \               msacm32
ELF    7dfc7000-7e081000    Deferred        winmm<elf>
  \-PE    7dfd0000-7e081000    \               winmm
ELF    7e081000-7e188000    Deferred        comctl32<elf>
  \-PE    7e090000-7e188000    \               comctl32
ELF    7e188000-7e202000    Deferred        shlwapi<elf>
  \-PE    7e1a0000-7e202000    \               shlwapi
ELF    7e202000-7e435000    Deferred        shell32<elf>
  \-PE    7e210000-7e435000    \               shell32
ELF    7e435000-7e44d000    Deferred        userenv<elf>
  \-PE    7e440000-7e44d000    \               userenv
ELF    7e44d000-7e47a000    Deferred        netapi32<elf>
  \-PE    7e450000-7e47a000    \               netapi32
ELF    7e47a000-7e4a2000    Deferred        mpr<elf>
  \-PE    7e480000-7e4a2000    \               mpr
ELF    7e4a2000-7e4d8000    Deferred        ws2_32<elf>
  \-PE    7e4b0000-7e4d8000    \               ws2_32
ELF    7e4d8000-7e5a7000    Deferred        crypt32<elf>
  \-PE    7e4e0000-7e5a7000    \               crypt32
ELF    7e5a7000-7e5cd000    Deferred        iphlpapi<elf>
  \-PE    7e5b0000-7e5cd000    \               iphlpapi
ELF    7e5cd000-7e5e3000    Deferred        dwmapi<elf>
  \-PE    7e5d0000-7e5e3000    \               dwmapi
ELF    7e5e3000-7e61a000    Deferred        uxtheme<elf>
  \-PE    7e5f0000-7e61a000    \               uxtheme
ELF    7e61a000-7e69b000    Deferred        rpcrt4<elf>
  \-PE    7e630000-7e69b000    \               rpcrt4
ELF    7e69b000-7e7d7000    Deferred        ole32<elf>
  \-PE    7e6b0000-7e7d7000    \               ole32
ELF    7e7d7000-7e90d000    Deferred        oleaut32<elf>
  \-PE    7e7f0000-7e90d000    \               oleaut32
ELF    7e90d000-7e927000    Deferred        version<elf>
  \-PE    7e910000-7e927000    \               version
ELF    7e927000-7e999000    Deferred        advapi32<elf>
  \-PE    7e930000-7e999000    \               advapi32
ELF    7e999000-7eab6000    Deferred        gdi32<elf>
  \-PE    7e9b0000-7eab6000    \               gdi32
ELF    7eab6000-7ec10000    Deferred        user32<elf>
  \-PE    7ead0000-7ec10000    \               user32
ELF    7ec10000-7ec35000    Deferred        imm32<elf>
  \-PE    7ec20000-7ec35000    \               imm32
ELF    7ec35000-7ec42000    Deferred        libnss_files.so.2
ELF    7ec42000-7ec4e000    Deferred        libnss_nis.so.2
ELF    7ec4e000-7ec67000    Deferred        libnsl.so.1
ELF    7ec67000-7ec70000    Deferred        libnss_compat.so.2
ELF    7efa2000-7efe8000    Deferred        libm.so.6
ELF    7efe8000-7f000000    Deferred        wtsapi32<elf>
  \-PE    7eff0000-7f000000    \               wtsapi32
ELF    b7408000-b75b6000    Deferred        libc.so.6
ELF    b75b6000-b75bb000    Deferred        libdl.so.2
ELF    b75bc000-b75d8000    Deferred        libpthread.so.0
ELF    b75f0000-b77a5000    Dwarf           libwine.so.1
ELF    b77a7000-b77c9000    Deferred        ld-linux.so.2
ELF    b77c9000-b77ca000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001e    0
    0000001d    0
    00000018    0
    00000016    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000017    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001f    0
    0000001b    0
00000021 explorer.exe
    00000023    0
    00000022    0
00000024 (D) Z:\home\chris\Downloads\EveLauncher-1747682.exe
    00000025    0 <==
System information:
    Wine build: wine-1.6.2
    Platform: i386
    Host system: Linux
    Host version: 3.16.0-38-generic
```

like this ? hope i got it right

---

### Post by haytham-med on 2020-06-29
Man , update wine, latest's 5.0.1

---

