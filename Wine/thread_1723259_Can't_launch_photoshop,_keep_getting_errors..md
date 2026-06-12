---
title: "Can't launch photoshop, keep getting errors."
date: 2011-04-06
forum: Wine
---

### Post by thecompgame on 2011-04-06
Iv tried the portable version of photoshop cs5 and i still get errors.
Please help!

neal@neal-AW012AAR-ABA-p6280t:~/Desktop$ wine Photoshop.exe
err:shell:HCR_GetFolderAttributes should be called for simple PIDL's only!
wine: Unhandled exception 0xc06d007e at address 0x7b8399d2 (thread 0035), starting debugger...
Unhandled exception: 0xc06d007e in 32-bit code (0x7b8399d2).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b8399d2 ESP:0032fd14 EBP:0032fd78 EFLAGS:00000283(   - --  I S - - -C)
 EAX:7b8258b5 EBX:7b889ff4 ECX:0032fd9c EDX:0032fd38
 ESI:c06d007e EDI:00000000
Stack dump:
0x0032fd14:  0032fdec 00000004 034c38f8 c06d007e
0x0032fd24:  00000000 00000000 7b8399d2 00000001
0x0032fd34:  0032fd9c 7ffd8c00 0218dd0c 00000000
0x0032fd44:  0032fd64 7b853285 7ffd8c00 00000000
0x0032fd54:  00000000 00000000 7b85324b 7b889ff4
0x0032fd64:  0032fd84 7b8532bf 7b83998a 00000000
Backtrace:
=>0 0x7b8399d2 in kernel32 (+0x299d2) (0x0032fd78)
  1 0x01c4dac2 in photoshop (+0x184dac1) (0x0032fde0)
  2 0x014248b7 in photoshop (+0x10248b6) (0x0032fe08)
  3 0x013127be in photoshop (+0xf127bd) (0x0032fe90)
  4 0x7b8588fc call_process_entry+0xb() in kernel32 (0x0032fea8)
  5 0x7b85959f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  6 0x7bc73238 call_thread_func+0xb() in ntdll (0x0032fef8)
  7 0x7bc75cf0 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  8 0x7bc4aa0a call_dll_entry_point+0x629() in ntdll (0x0032ffe8)
0x7b8399d2: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (112 modules)
PE      340000-  3b6000    Deferred        cggl
PE      3c0000-  3c9000    Deferred        adbeape
PE      400000- 2c2c000    Export          photoshop
PE     2c30000- 2d84000    Deferred        adobeowl
PE     2d90000- 2dd8000    Deferred        adobeowlcanvas
PE     2de0000- 2e1c000    Deferred        ahclient
PE     2e20000- 2ec6000    Deferred        axedomcore
PE     2ed0000- 3372000    Deferred        mps
PE     3380000- 3497000    Deferred        plugplug
PE    10000000-100fe000    Deferred        cg
PE    4ec50000-4edfb000    Deferred        gdiplus
PE    78480000-7850e000    Deferred        msvcp90
PE    78520000-785c3000    Deferred        msvcr90
ELF    79c9c000-7b800000    Deferred        fglrx_dri.so
ELF    7b800000-7b991000    Dwarf           kernel32<elf>
  \-PE    7b810000-7b991000    \               kernel32
ELF    7bc00000-7bcbc000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcbc000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d32a000-7d35e000    Deferred        uxtheme<elf>
  \-PE    7d330000-7d35e000    \               uxtheme
ELF    7d35e000-7d379000    Deferred        spoolss<elf>
  \-PE    7d360000-7d379000    \               spoolss
ELF    7d379000-7d3b5000    Deferred        libdbus-1.so.3
ELF    7d3b5000-7d3ba000    Deferred        libgpg-error.so.0
ELF    7d3ba000-7d3cb000    Deferred        libtasn1.so.3
ELF    7d3cb000-7d3df000    Deferred        libresolv.so.2
ELF    7d3df000-7d3e3000    Deferred        libkeyutils.so.1
ELF    7d3e3000-7d3eb000    Deferred        libkrb5support.so.0
ELF    7d3eb000-7d40f000    Deferred        libk5crypto.so.3
ELF    7d40f000-7d4be000    Deferred        libkrb5.so.3
ELF    7d4be000-7d4ce000    Deferred        libavahi-client.so.3
ELF    7d4ce000-7d542000    Deferred        libgcrypt.so.11
ELF    7d542000-7d5dd000    Deferred        libgnutls.so.26
ELF    7d5dd000-7d60c000    Deferred        libgssapi_krb5.so.2
ELF    7d60c000-7d656000    Deferred        libcups.so.2
ELF    7d713000-7d745000    Deferred        libatiadlxx.so
ELF    7d748000-7d769000    Deferred        localspl<elf>
  \-PE    7d750000-7d769000    \               localspl
ELF    7de69000-7de72000    Deferred        librt.so.1
ELF    7de72000-7de7c000    Deferred        libxcursor.so.1
ELF    7de7c000-7de82000    Deferred        libxfixes.so.3
ELF    7de82000-7de86000    Deferred        libxcomposite.so.1
ELF    7de86000-7de8e000    Deferred        libxrandr.so.2
ELF    7de8e000-7de98000    Deferred        libxrender.so.1
ELF    7de98000-7de9e000    Deferred        libxxf86vm.so.1
ELF    7de9e000-7dea2000    Deferred        libxinerama.so.1
ELF    7dea3000-7dea7000    Deferred        libcom_err.so.2
ELF    7dea7000-7deb3000    Deferred        libavahi-common.so.3
ELF    7dec6000-7dee7000    Deferred        imm32<elf>
  \-PE    7ded0000-7dee7000    \               imm32
ELF    7dee7000-7df90000    Deferred        winex11<elf>
  \-PE    7def0000-7df90000    \               winex11
ELF    7dfef000-7e016000    Deferred        libexpat.so.1
ELF    7e016000-7e046000    Deferred        libfontconfig.so.1
ELF    7e046000-7e0bd000    Deferred        libfreetype.so.6
ELF    7e0bd000-7e0f6000    Deferred        libncurses.so.5
ELF    7e0f6000-7e1e3000    Deferred        oleaut32<elf>
  \-PE    7e110000-7e1e3000    \               oleaut32
ELF    7e1e3000-7e207000    Deferred        mpr<elf>
  \-PE    7e1f0000-7e207000    \               mpr
ELF    7e207000-7e21c000    Deferred        libz.so.1
ELF    7e21c000-7e284000    Deferred        wininet<elf>
  \-PE    7e230000-7e284000    \               wininet
ELF    7e284000-7e2b4000    Deferred        ws2_32<elf>
  \-PE    7e290000-7e2b4000    \               ws2_32
ELF    7e2b4000-7e3a8000    Deferred        comctl32<elf>
  \-PE    7e2c0000-7e3a8000    \               comctl32
ELF    7e3a8000-7e40c000    Deferred        shlwapi<elf>
  \-PE    7e3c0000-7e40c000    \               shlwapi
ELF    7e40c000-7e609000    Deferred        shell32<elf>
  \-PE    7e420000-7e609000    \               shell32
ELF    7e609000-7e641000    Deferred        winspool<elf>
  \-PE    7e610000-7e641000    \               winspool
ELF    7e641000-7e647000    Deferred        libxdmcp.so.6
ELF    7e647000-7e64b000    Deferred        libxau.so.6
ELF    7e64b000-7e667000    Deferred        libgcc_s.so.1
ELF    7e667000-7e66f000    Deferred        libatiuki.so.1
ELF    7e66f000-7e689000    Deferred        libxcb.so.1
ELF    7e689000-7e68e000    Deferred        libuuid.so.1
ELF    7e68e000-7e752000    Deferred        libgl.so.1
ELF    7e752000-7e86f000    Deferred        libx11.so.6
ELF    7e86f000-7e87f000    Deferred        libxext.so.6
ELF    7e87f000-7e898000    Deferred        libice.so.6
ELF    7e8bc000-7e96e000    Deferred        opengl32<elf>
  \-PE    7e8d0000-7e96e000    \               opengl32
ELF    7e96e000-7e9e2000    Deferred        rpcrt4<elf>
  \-PE    7e980000-7e9e2000    \               rpcrt4
ELF    7e9e2000-7eae6000    Deferred        ole32<elf>
  \-PE    7ea00000-7eae6000    \               ole32
ELF    7eae6000-7eb42000    Deferred        advapi32<elf>
  \-PE    7eaf0000-7eb42000    \               advapi32
ELF    7eb42000-7ebd0000    Deferred        gdi32<elf>
  \-PE    7eb50000-7ebd0000    \               gdi32
ELF    7ebd0000-7ed05000    Deferred        user32<elf>
  \-PE    7ebe0000-7ed05000    \               user32
ELF    7ed05000-7ed93000    Deferred        msvcrt<elf>
  \-PE    7ed20000-7ed93000    \               msvcrt
ELF    7ef93000-7ef9f000    Deferred        libnss_files.so.2
ELF    7ef9f000-7efb6000    Deferred        libnsl.so.1
ELF    7efb6000-7efdc000    Deferred        libm.so.6
ELF    7efde000-7efe7000    Deferred        libsm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f74a1000-f74ac000    Deferred        libnss_nis.so.2
ELF    f74ad000-f74b1000    Deferred        libdl.so.2
ELF    f74b1000-f760c000    Deferred        libc.so.6
ELF    f760d000-f7626000    Deferred        libpthread.so.0
ELF    f7642000-f764a000    Deferred        libnss_compat.so.2
ELF    f764a000-f778b000    Dwarf           libwine.so.1
ELF    f778d000-f77ab000    Deferred        ld-linux.so.2
ELF    f77ab000-f77ac000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001c    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000017    0
    00000013    0
    00000012    0
00000019 plugplay.exe
    0000001d    0
    0000001b    0
    0000001a    0
0000001e explorer.exe
    0000001f    0
00000020 PhotoshopCS5Portable.exe
    00000021    0
00000026 Photoshop.exe
    0000002d    0
    0000002c    0
    0000002b    0
    0000002a    0
    00000029    0
    00000028    0
00000034 (D) Z:\home\neal\Desktop\Photoshop.exe
    00000035    0 <==
Backtrace:
=>0 0x7b8399d2 in kernel32 (+0x299d2) (0x0032fd78)
  1 0x01c4dac2 in photoshop (+0x184dac1) (0x0032fde0)
  2 0x014248b7 in photoshop (+0x10248b6) (0x0032fe08)
  3 0x013127be in photoshop (+0xf127bd) (0x0032fe90)
  4 0x7b8588fc call_process_entry+0xb() in kernel32 (0x0032fea8)
  5 0x7b85959f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  6 0x7bc73238 call_thread_func+0xb() in ntdll (0x0032fef8)
  7 0x7bc75cf0 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  8 0x7bc4aa0a call_dll_entry_point+0x629() in ntdll (0x0032ffe8)
neal@neal-AW012AAR-ABA-p6280t:~/Desktop$ wine Photoshop.exe
err:process:create_process starting 64-bit process L"Z:\\home\\neal\\Desktop\\Photoshop.exe" not supported in 32-bit wineprefix
wine: Bad EXE format for Z:\home\neal\Desktop\Photoshop.exe
neal@neal-AW012AAR-ABA-p6280t:~/Desktop$ wine Photoshop.exe
err:shell:HCR_GetFolderAttributes should be called for simple PIDL's only!
wine: Unhandled exception 0xc06d007e at address 0x7b8399d2 (thread 003b), starting debugger...
Unhandled exception: 0xc06d007e in 32-bit code (0x7b8399d2).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b8399d2 ESP:0032fd14 EBP:0032fd78 EFLAGS:00000283(   - --  I S - - -C)
 EAX:7b8258b5 EBX:7b889ff4 ECX:0032fd9c EDX:0032fd38
 ESI:c06d007e EDI:00000000
Stack dump:
0x0032fd14:  0032fdec 00000004 034c38f8 c06d007e
0x0032fd24:  00000000 00000000 7b8399d2 00000001
0x0032fd34:  0032fd9c 7ffd8c00 0218dd0c 00000000
0x0032fd44:  0032fd64 7b853285 7ffd8c00 00000000
0x0032fd54:  00000000 00000000 7b85324b 7b889ff4
0x0032fd64:  0032fd84 7b8532bf 7b83998a 00000000
Backtrace:
=>0 0x7b8399d2 in kernel32 (+0x299d2) (0x0032fd78)
  1 0x01c4dac2 in photoshop (+0x184dac1) (0x0032fde0)
  2 0x014248b7 in photoshop (+0x10248b6) (0x0032fe08)
  3 0x013127be in photoshop (+0xf127bd) (0x0032fe90)
  4 0x7b8588fc call_process_entry+0xb() in kernel32 (0x0032fea8)
  5 0x7b85959f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  6 0x7bc73238 call_thread_func+0xb() in ntdll (0x0032fef8)
  7 0x7bc75cf0 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  8 0x7bc4aa0a call_dll_entry_point+0x629() in ntdll (0x0032ffe8)
0x7b8399d2: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (112 modules)
PE      340000-  3b6000    Deferred        cggl
PE      3c0000-  3c9000    Deferred        adbeape
PE      400000- 2c2c000    Export          photoshop
PE     2c30000- 2d84000    Deferred        adobeowl
PE     2d90000- 2dd8000    Deferred        adobeowlcanvas
PE     2de0000- 2e1c000    Deferred        ahclient
PE     2e20000- 2ec6000    Deferred        axedomcore
PE     2ed0000- 3372000    Deferred        mps
PE     3380000- 3497000    Deferred        plugplug
PE    10000000-100fe000    Deferred        cg
PE    4ec50000-4edfb000    Deferred        gdiplus
PE    78480000-7850e000    Deferred        msvcp90
PE    78520000-785c3000    Deferred        msvcr90
ELF    79c9c000-7b800000    Deferred        fglrx_dri.so
ELF    7b800000-7b991000    Dwarf           kernel32<elf>
  \-PE    7b810000-7b991000    \               kernel32
ELF    7bc00000-7bcbc000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcbc000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d311000-7d345000    Deferred        uxtheme<elf>
  \-PE    7d320000-7d345000    \               uxtheme
ELF    7d345000-7d360000    Deferred        spoolss<elf>
  \-PE    7d350000-7d360000    \               spoolss
ELF    7d360000-7d39c000    Deferred        libdbus-1.so.3
ELF    7d39c000-7d3a1000    Deferred        libgpg-error.so.0
ELF    7d3a1000-7d3b2000    Deferred        libtasn1.so.3
ELF    7d3b2000-7d3c6000    Deferred        libresolv.so.2
ELF    7d3c6000-7d3ca000    Deferred        libkeyutils.so.1
ELF    7d3ca000-7d3ee000    Deferred        libk5crypto.so.3
ELF    7d3ee000-7d49d000    Deferred        libkrb5.so.3
ELF    7d49d000-7d511000    Deferred        libgcrypt.so.11
ELF    7d511000-7d5ac000    Deferred        libgnutls.so.26
ELF    7d5ac000-7d5db000    Deferred        libgssapi_krb5.so.2
ELF    7d5db000-7d625000    Deferred        libcups.so.2
ELF    7d628000-7d649000    Deferred        localspl<elf>
  \-PE    7d630000-7d649000    \               localspl
ELF    7d706000-7d738000    Deferred        libatiadlxx.so
ELF    7d738000-7d740000    Deferred        libkrb5support.so.0
ELF    7d740000-7d750000    Deferred        libavahi-client.so.3
ELF    7d750000-7d75c000    Deferred        libavahi-common.so.3
ELF    7de5c000-7de66000    Deferred        libxcursor.so.1
ELF    7de66000-7de6c000    Deferred        libxfixes.so.3
ELF    7de6c000-7de70000    Deferred        libxcomposite.so.1
ELF    7de70000-7de78000    Deferred        libxrandr.so.2
ELF    7de78000-7de82000    Deferred        libxrender.so.1
ELF    7de82000-7de88000    Deferred        libxxf86vm.so.1
ELF    7de88000-7de8c000    Deferred        libxinerama.so.1
ELF    7de8e000-7de92000    Deferred        libcom_err.so.2
ELF    7dea5000-7deae000    Deferred        librt.so.1
ELF    7deb0000-7ded1000    Deferred        imm32<elf>
  \-PE    7dec0000-7ded1000    \               imm32
ELF    7ded1000-7df7a000    Deferred        winex11<elf>
  \-PE    7dee0000-7df7a000    \               winex11
ELF    7dfd7000-7dffe000    Deferred        libexpat.so.1
ELF    7dffe000-7e02e000    Deferred        libfontconfig.so.1
ELF    7e02e000-7e0a5000    Deferred        libfreetype.so.6
ELF    7e0a5000-7e0de000    Deferred        libncurses.so.5
ELF    7e0de000-7e1cb000    Deferred        oleaut32<elf>
  \-PE    7e0f0000-7e1cb000    \               oleaut32
ELF    7e1cb000-7e1ef000    Deferred        mpr<elf>
  \-PE    7e1d0000-7e1ef000    \               mpr
ELF    7e1ef000-7e204000    Deferred        libz.so.1
ELF    7e204000-7e26c000    Deferred        wininet<elf>
  \-PE    7e210000-7e26c000    \               wininet
ELF    7e26c000-7e29c000    Deferred        ws2_32<elf>
  \-PE    7e270000-7e29c000    \               ws2_32
ELF    7e29c000-7e390000    Deferred        comctl32<elf>
  \-PE    7e2a0000-7e390000    \               comctl32
ELF    7e390000-7e3f4000    Deferred        shlwapi<elf>
  \-PE    7e3a0000-7e3f4000    \               shlwapi
ELF    7e3f4000-7e5f1000    Deferred        shell32<elf>
  \-PE    7e400000-7e5f1000    \               shell32
ELF    7e5f1000-7e629000    Deferred        winspool<elf>
  \-PE    7e600000-7e629000    \               winspool
ELF    7e629000-7e62f000    Deferred        libxdmcp.so.6
ELF    7e62f000-7e64b000    Deferred        libgcc_s.so.1
ELF    7e64b000-7e653000    Deferred        libatiuki.so.1
ELF    7e653000-7e66d000    Deferred        libxcb.so.1
ELF    7e66d000-7e672000    Deferred        libuuid.so.1
ELF    7e672000-7e736000    Deferred        libgl.so.1
ELF    7e736000-7e853000    Deferred        libx11.so.6
ELF    7e853000-7e863000    Deferred        libxext.so.6
ELF    7e863000-7e87c000    Deferred        libice.so.6
ELF    7e87c000-7e885000    Deferred        libsm.so.6
ELF    7e8a9000-7e95b000    Deferred        opengl32<elf>
  \-PE    7e8c0000-7e95b000    \               opengl32
ELF    7e95b000-7e9cf000    Deferred        rpcrt4<elf>
  \-PE    7e970000-7e9cf000    \               rpcrt4
ELF    7e9cf000-7ead3000    Deferred        ole32<elf>
  \-PE    7e9f0000-7ead3000    \               ole32
ELF    7ead3000-7eb2f000    Deferred        advapi32<elf>
  \-PE    7eae0000-7eb2f000    \               advapi32
ELF    7eb2f000-7ebbd000    Deferred        gdi32<elf>
  \-PE    7eb40000-7ebbd000    \               gdi32
ELF    7ebbd000-7ecf2000    Deferred        user32<elf>
  \-PE    7ebd0000-7ecf2000    \               user32
ELF    7ecf2000-7ed80000    Deferred        msvcrt<elf>
  \-PE    7ed00000-7ed80000    \               msvcrt
ELF    7ef80000-7ef8c000    Deferred        libnss_files.so.2
ELF    7ef8c000-7ef97000    Deferred        libnss_nis.so.2
ELF    7ef97000-7efae000    Deferred        libnsl.so.1
ELF    7efae000-7efb6000    Deferred        libnss_compat.so.2
ELF    7efb6000-7efdc000    Deferred        libm.so.6
ELF    7efdc000-7efe0000    Deferred        libxau.so.6
ELF    7efe0000-7eff9000    Deferred        version<elf>
  \-PE    7eff0000-7eff9000    \               version
ELF    f74c4000-f74c8000    Deferred        libdl.so.2
ELF    f74c8000-f7623000    Deferred        libc.so.6
ELF    f7624000-f763d000    Deferred        libpthread.so.0
ELF    f7661000-f77a2000    Dwarf           libwine.so.1
ELF    f77a4000-f77c2000    Deferred        ld-linux.so.2
ELF    f77c2000-f77c3000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001c    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000017    0
    00000013    0
    00000012    0
00000019 plugplay.exe
    0000001d    0
    0000001b    0
    0000001a    0
0000001e explorer.exe
    0000001f    0
00000020 PhotoshopCS5Portable.exe
    00000021    0
00000026 Photoshop.exe
    0000002d    0
    0000002c    0
    0000002b    0
    0000002a    0
    00000029    0
    00000028    0
0000003a (D) Z:\home\neal\Desktop\Photoshop.exe
    0000003b    0 <==
Backtrace:
=>0 0x7b8399d2 in kernel32 (+0x299d2) (0x0032fd78)
  1 0x01c4dac2 in photoshop (+0x184dac1) (0x0032fde0)
  2 0x014248b7 in photoshop (+0x10248b6) (0x0032fe08)
  3 0x013127be in photoshop (+0xf127bd) (0x0032fe90)
  4 0x7b8588fc call_process_entry+0xb() in kernel32 (0x0032fea8)
  5 0x7b85959f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  6 0x7bc73238 call_thread_func+0xb() in ntdll (0x0032fef8)
  7 0x7bc75cf0 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  8 0x7bc4aa0a call_dll_entry_point+0x629() in ntdll (0x0032ffe8)

---

