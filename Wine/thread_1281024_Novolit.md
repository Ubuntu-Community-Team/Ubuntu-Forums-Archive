---
title: "Novolit"
date: 2009-10-02
forum: Wine
---

### Post by basraks on 2009-10-02
I have installed application called Novolit on Ubuntu 9.0.4 in Wine 1.0.1. Installation went fine but when I run it I get some error and next code in terminal:

```

err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject no class object {00000514-0000-0010-8000-00aa006d2ea4} could be created for context 0x5
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b845450 (thread 0009), starting debugger...
First chance exception: 0xc0000025 in 32-bit code (0x7bc3ba9e).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc3ba9e ESP:0032f5e4 EBP:0032f648 EFLAGS:00200282(   - 00      - -IS1)
 EAX:0032f5f0 EBX:7bc8aff4 ECX:00110048 EDX:00000000
 ESI:0032f9cc EDI:0032f654
Stack dump:
0x0032f5e4:  0001003c 0032f628 041a46ea c0000025
0x0032f5f4:  00000001 0032f9cc 00000019 00000000
0x0032f604:  7bc8aff4 7bc8aff4 7b820000 0032f6e0
0x0032f614:  7bc46217 0032f638 00000000 00000000
0x0032f624:  00000402 0032faf8 0032f740 7bc46ea0
0x0032f634:  00000402 7bc8aff4 7b820000 7bc3ba50
Backtrace:
=>1 0x7bc3ba9e __regs_RtlRaiseException+0x4e() in ntdll (0x0032f648)
  2 0x7bc78a3f in ntdll (+0x68a3f) (0x0032f9ac)
  3 0x7bc3ad56 RtlRaiseException+0x6() in ntdll (0x0032fa24)
  4 0x00530d7b in novolit (+0x130d7b) (0x0032fa64)
  5 0x0053161f in novolit (+0x13161f) (0x0032fa9c)
  6 0x00428df8 in novolit (+0x28df8) (0x0032fac8)
  7 0x00429029 in novolit (+0x29029) (0x0032fb20)
  8 0x004292da in novolit (+0x292da) (0x0032fb4c)
  9 0x00429219 in novolit (+0x29219) (0x0032fb68)
  10 0x00430112 in novolit (+0x30112) (0x0032fbf0)
  11 0x004272bb in novolit (+0x272bb) (0x0032fc10)
  12 0x0042302c in novolit (+0x2302c) (0x0032fc34)
  13 0x004231b6 in novolit (+0x231b6) (0x0032fd54)
  14 0x00423247 in novolit (+0x23247) (0x0032fd84)
  15 0x00430dad in novolit (+0x30dad) (0x0032fecc)
  16 0x0048e5ec in novolit (+0x8e5ec) (0x0032fef0)
  17 0x00a78734 in novolit (+0x678734) (0x0032ff08)
  18 0x7b878828 in kernel32 (+0x58828) (0x0032ffe8)
  19 0xb7db6d37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc3ba9e __regs_RtlRaiseException+0x4e in ntdll: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (110 modules)
PE      400000-  dcd000    Export          novolit
PE    70bd0000-70c35000    Deferred        shlwapi
ELF    77fe7000-78000000    Deferred        msacm32<elf>
  \-PE    77ff0000-78000000    \               msacm32
PE    78000000-78044000    Deferred        msvcrt
ELF    7b800000-7b93d000    Export          kernel32<elf>
  \-PE    7b820000-7b93d000    \               kernel32
ELF    7bc00000-7bca7000    Export          ntdll<elf>
  \-PE    7bc10000-7bca7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7dd7d000-7dda0000    Deferred        hhctrl<elf>
  \-PE    7dd80000-7dda0000    \               hhctrl
ELF    7dda0000-7ddeb000    Deferred        riched20<elf>
  \-PE    7ddb0000-7ddeb000    \               riched20
ELF    7ddeb000-7de24000    Deferred        gdiplus<elf>
  \-PE    7de00000-7de24000    \               gdiplus
ELF    7de24000-7de39000    Deferred        dwmapi<elf>
  \-PE    7de30000-7de39000    \               dwmapi
ELF    7de39000-7de4e000    Deferred        midimap<elf>
  \-PE    7de40000-7de4e000    \               midimap
ELF    7de4e000-7de76000    Deferred        msacm32<elf>
  \-PE    7de50000-7de76000    \               msacm32
ELF    7de76000-7de7c000    Deferred        libattr.so.1
ELF    7de7c000-7dedb000    Deferred        libpulse.so.0
ELF    7deef000-7def8000    Deferred        librt.so.1
ELF    7def8000-7dfc0000    Deferred        libasound.so.2
ELF    7dfc0000-7dff7000    Deferred        winealsa<elf>
  \-PE    7dfd0000-7dff7000    \               winealsa
ELF    7dff7000-7dffb000    Deferred        libgpg-error.so.0
ELF    7dffb000-7e064000    Deferred        libgcrypt.so.11
ELF    7e064000-7e076000    Deferred        libtasn1.so.3
ELF    7e076000-7e07f000    Deferred        libkrb5support.so.0
ELF    7e07f000-7e0a3000    Deferred        libk5crypto.so.3
ELF    7e0a3000-7e135000    Deferred        libkrb5.so.3
ELF    7e135000-7e1d2000    Deferred        libgnutls.so.26
ELF    7e1d2000-7e1fd000    Deferred        libgssapi_krb5.so.2
ELF    7e1fd000-7e234000    Deferred        libcups.so.2
ELF    7e235000-7e23c000    Deferred        libgdbm.so.3
ELF    7e23c000-7e241000    Deferred        libcap.so.2
ELF    7e241000-7e248000    Deferred        libasound_module_pcm_pulse.so
ELF    7e2d1000-7e304000    Deferred        uxtheme<elf>
  \-PE    7e2e0000-7e304000    \               uxtheme
ELF    7e304000-7e30d000    Deferred        libxcursor.so.1
ELF    7e30d000-7e312000    Deferred        libxfixes.so.3
ELF    7e312000-7e316000    Deferred        libxcomposite.so.1
ELF    7e316000-7e31e000    Deferred        libxrandr.so.2
ELF    7e31e000-7e328000    Deferred        libxrender.so.1
ELF    7e328000-7e349000    Deferred        imm32<elf>
  \-PE    7e330000-7e349000    \               imm32
ELF    7e349000-7e34e000    Deferred        libxdmcp.so.6
ELF    7e34e000-7e368000    Deferred        libxcb.so.1
ELF    7e368000-7e36c000    Deferred        libxau.so.6
ELF    7e36c000-7e371000    Deferred        libuuid.so.1
ELF    7e371000-7e460000    Deferred        libx11.so.6
ELF    7e460000-7e470000    Deferred        libxext.so.6
ELF    7e470000-7e476000    Deferred        libxxf86vm.so.1
ELF    7e476000-7e48e000    Deferred        libice.so.6
ELF    7e48e000-7e497000    Deferred        libsm.so.6
ELF    7e498000-7e49c000    Deferred        libkeyutils.so.1
ELF    7e4a5000-7e4a9000    Deferred        libcom_err.so.2
ELF    7e4ab000-7e546000    Deferred        winex11<elf>
  \-PE    7e4c0000-7e546000    \               winex11
ELF    7e59e000-7e5c5000    Deferred        libexpat.so.1
ELF    7e5c5000-7e5f2000    Deferred        libfontconfig.so.1
ELF    7e5f2000-7e608000    Deferred        libz.so.1
ELF    7e608000-7e67f000    Deferred        libfreetype.so.6
ELF    7e693000-7e6ba000    Deferred        oledlg<elf>
  \-PE    7e6a0000-7e6ba000    \               oledlg
ELF    7e6ba000-7e74e000    Deferred        winmm<elf>
  \-PE    7e6d0000-7e74e000    \               winmm
ELF    7e74e000-7e7fc000    Deferred        comdlg32<elf>
  \-PE    7e760000-7e7fc000    \               comdlg32
ELF    7e7fc000-7e833000    Deferred        winspool<elf>
  \-PE    7e800000-7e833000    \               winspool
ELF    7e833000-7e947000    Deferred        shell32<elf>
  \-PE    7e840000-7e947000    \               shell32
ELF    7e947000-7ea0c000    Deferred        comctl32<elf>
  \-PE    7e950000-7ea0c000    \               comctl32
ELF    7ea0c000-7ea21000    Deferred        lz32<elf>
  \-PE    7ea10000-7ea21000    \               lz32
ELF    7ea21000-7ea3c000    Deferred        version<elf>
  \-PE    7ea30000-7ea3c000    \               version
ELF    7ea3c000-7ea52000    Deferred        libresolv.so.2
ELF    7ea52000-7ea66000    Deferred        msimg32<elf>
  \-PE    7ea60000-7ea66000    \               msimg32
ELF    7ea66000-7ea85000    Deferred        iphlpapi<elf>
  \-PE    7ea70000-7ea85000    \               iphlpapi
ELF    7ea85000-7eae8000    Deferred        rpcrt4<elf>
  \-PE    7ea90000-7eae8000    \               rpcrt4
ELF    7eae8000-7eb88000    Deferred        gdi32<elf>
  \-PE    7eb00000-7eb88000    \               gdi32
ELF    7eb88000-7ecd4000    Deferred        user32<elf>
  \-PE    7eba0000-7ecd4000    \               user32
ELF    7ecd4000-7ed27000    Deferred        advapi32<elf>
  \-PE    7ece0000-7ed27000    \               advapi32
ELF    7ed27000-7edcd000    Deferred        ole32<elf>
  \-PE    7ed40000-7edcd000    \               ole32
ELF    7edcd000-7ee73000    Deferred        oleaut32<elf>
  \-PE    7ede0000-7ee73000    \               oleaut32
ELF    7efa1000-7efad000    Deferred        libnss_files.so.2
ELF    7efad000-7efc6000    Deferred        libnsl.so.1
ELF    7efc6000-7efec000    Deferred        libm.so.6
ELF    7efec000-7efef000    Deferred        libxinerama.so.1
ELF    7eff5000-7f000000    Deferred        libnss_nis.so.2
ELF    b7c10000-b7c19000    Deferred        libnss_compat.so.2
ELF    b7c1a000-b7c1e000    Deferred        libdl.so.2
ELF    b7c1e000-b7d81000    Deferred        libc.so.6
ELF    b7d82000-b7d9b000    Deferred        libpthread.so.0
ELF    b7daf000-b7ee6000    Export          libwine.so.1
ELF    b7ee8000-b7f06000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Novolit\Novolit 2005\novolit.exe
    00000009    0 <==
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
Backtrace:
=>1 0x7bc3ba9e __regs_RtlRaiseException+0x4e() in ntdll (0x0032f648)
  2 0x7bc78a3f in ntdll (+0x68a3f) (0x0032f9ac)
  3 0x7bc3ad56 RtlRaiseException+0x6() in ntdll (0x0032fa24)
  4 0x00530d7b in novolit (+0x130d7b) (0x0032fa64)
  5 0x0053161f in novolit (+0x13161f) (0x0032fa9c)
  6 0x00428df8 in novolit (+0x28df8) (0x0032fac8)
  7 0x00429029 in novolit (+0x29029) (0x0032fb20)
  8 0x004292da in novolit (+0x292da) (0x0032fb4c)
  9 0x00429219 in novolit (+0x29219) (0x0032fb68)
  10 0x00430112 in novolit (+0x30112) (0x0032fbf0)
  11 0x004272bb in novolit (+0x272bb) (0x0032fc10)
  12 0x0042302c in novolit (+0x2302c) (0x0032fc34)
  13 0x004231b6 in novolit (+0x231b6) (0x0032fd54)
  14 0x00423247 in novolit (+0x23247) (0x0032fd84)
  15 0x00430dad in novolit (+0x30dad) (0x0032fecc)
  16 0x0048e5ec in novolit (+0x8e5ec) (0x0032fef0)
  17 0x00a78734 in novolit (+0x678734) (0x0032ff08)
  18 0x7b878828 in kernel32 (+0x58828) (0x0032ffe8)
  19 0xb7db6d37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```I also tried to install it in Crossover on OsX 10.5.8. with same results.

Does anyone know where could be a problem?

---

### Post by basraks on 2009-10-02
After Wine upgrade on version 1.1.30 I get next code output in terminal:

```

err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject no class object {00000514-0000-0010-8000-00aa006d2ea4} could be created for context 0x5
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b8434b3 (thread 0009), starting debugger...
First chance exception: 0xc0000025 in 32-bit code (0x7bc3c4d8).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc3c4d8 ESP:0032f574 EBP:0032f5d8 EFLAGS:00200202(   - --  I   - - - )
 EAX:0032f97c EBX:7bc95ff4 ECX:00110058 EDX:00000000
 ESI:0032f580 EDI:0032f604
Stack dump:
0x0032f574:  00000001 7b8c29b8 b7e57ff4 c0000025
0x0032f584:  00000001 0032f97c 7bc3c4d8 00000000
0x0032f594:  7bc89cf0 7bc9eb20 7bc90ec8 7bc89d0c
0x0032f5a4:  0032f5c8 7bc6c200 b7df4654 0032f60c
0x0032f5b4:  00000000 00000000 0032f6ec 00000000
0x0032f5c4:  fbad8001 0032f6ec 7bc95ff4 7bc95ff4
Backtrace:
=>0 0x7bc3c4d8 raise_status+0x38() in ntdll (0x0032f5d8)
  1 0x7bc6cba0 in ntdll (+0x5cba0) (0x0032f5f8)
  2 0x7bc827c5 in ntdll (+0x727c5) (0x0032f958)
  3 0x7bc6c174 RtlRaiseException+0xc() in ntdll (0x0032f9d4)
  4 0x00530d7b in novolit (+0x130d7b) (0x0032fa14)
  5 0x0053161f in novolit (+0x13161f) (0x0032fa4c)
  6 0x00428df8 in novolit (+0x28df8) (0x0032fa78)
  7 0x00429029 in novolit (+0x29029) (0x0032fad0)
  8 0x004292da in novolit (+0x292da) (0x0032fafc)
  9 0x00429219 in novolit (+0x29219) (0x0032fb18)
  10 0x00430112 in novolit (+0x30112) (0x0032fba0)
  11 0x004272bb in novolit (+0x272bb) (0x0032fbc0)
  12 0x0042302c in novolit (+0x2302c) (0x0032fbe4)
  13 0x004231b6 in novolit (+0x231b6) (0x0032fd04)
  14 0x00423247 in novolit (+0x23247) (0x0032fd34)
  15 0x00430dad in novolit (+0x30dad) (0x0032fe7c)
  16 0x0048e5ec in novolit (+0x8e5ec) (0x0032fea0)
  17 0x00a78734 in novolit (+0x678734) (0x0032feb8)
  18 0x7b8773a5 in kernel32 (+0x573a5) (0x0032fee8)
  19 0x7bc6c184 call_thread_func+0xc() in ntdll (0x0032fef8)
  20 0x7bc6c3a0 call_thread_entry_point+0x70() in ntdll (0x0032ffc8)
  21 0x7bc4985a in ntdll (+0x3985a) (0x0032ffe8)
  22 0xb7e9201d wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)
0x7bc3c4d8 raise_status+0x38 in ntdll: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (110 modules)
PE      400000-  dcd000    Export          novolit
PE    70bd0000-70c35000    Deferred        shlwapi
ELF    77fe8000-78000000    Deferred        msacm32<elf>
  \-PE    77ff0000-78000000    \               msacm32
PE    78000000-78044000    Deferred        msvcrt
ELF    7b800000-7b974000    Export          kernel32<elf>
  \-PE    7b820000-7b974000    \               kernel32
ELF    7bc00000-7bcb2000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb2000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7dab3000-7dad8000    Deferred        hhctrl<elf>
  \-PE    7dac0000-7dad8000    \               hhctrl
ELF    7dad8000-7db31000    Deferred        riched20<elf>
  \-PE    7dae0000-7db31000    \               riched20
ELF    7db31000-7db8a000    Deferred        gdiplus<elf>
  \-PE    7db40000-7db8a000    \               gdiplus
ELF    7db8a000-7db9f000    Deferred        midimap<elf>
  \-PE    7db90000-7db9f000    \               midimap
ELF    7db9f000-7dbc5000    Deferred        msacm32<elf>
  \-PE    7dbb0000-7dbc5000    \               msacm32
ELF    7dbc5000-7dc24000    Deferred        libpulse.so.0
ELF    7dc38000-7dc41000    Deferred        librt.so.1
ELF    7dc41000-7dd09000    Deferred        libasound.so.2
ELF    7dd09000-7dd40000    Deferred        winealsa<elf>
  \-PE    7dd10000-7dd40000    \               winealsa
ELF    7de40000-7dea9000    Deferred        libgcrypt.so.11
ELF    7dea9000-7debb000    Deferred        libtasn1.so.3
ELF    7debb000-7df4d000    Deferred        libkrb5.so.3
ELF    7df4d000-7dfea000    Deferred        libgnutls.so.26
ELF    7e047000-7e04d000    Deferred        libattr.so.1
ELF    7e04d000-7e051000    Deferred        libgpg-error.so.0
ELF    7e051000-7e067000    Deferred        libresolv.so.2
ELF    7e067000-7e070000    Deferred        libkrb5support.so.0
ELF    7e070000-7e094000    Deferred        libk5crypto.so.3
ELF    7e094000-7e0bf000    Deferred        libgssapi_krb5.so.2
ELF    7e0bf000-7e0f6000    Deferred        libcups.so.2
ELF    7e0f7000-7e0fe000    Deferred        libgdbm.so.3
ELF    7e0fe000-7e103000    Deferred        libcap.so.2
ELF    7e103000-7e10a000    Deferred        libasound_module_pcm_pulse.so
ELF    7e10a000-7e123000    Deferred        spoolss<elf>
  \-PE    7e110000-7e123000    \               spoolss
ELF    7e123000-7e141000    Deferred        localspl<elf>
  \-PE    7e130000-7e141000    \               localspl
ELF    7e1ca000-7e1fd000    Deferred        uxtheme<elf>
  \-PE    7e1d0000-7e1fd000    \               uxtheme
ELF    7e1fd000-7e206000    Deferred        libxcursor.so.1
ELF    7e206000-7e20b000    Deferred        libxfixes.so.3
ELF    7e20b000-7e20f000    Deferred        libxcomposite.so.1
ELF    7e20f000-7e217000    Deferred        libxrandr.so.2
ELF    7e217000-7e221000    Deferred        libxrender.so.1
ELF    7e221000-7e227000    Deferred        libxxf86vm.so.1
ELF    7e227000-7e248000    Deferred        imm32<elf>
  \-PE    7e230000-7e248000    \               imm32
ELF    7e248000-7e24d000    Deferred        libxdmcp.so.6
ELF    7e24d000-7e267000    Deferred        libxcb.so.1
ELF    7e267000-7e356000    Deferred        libx11.so.6
ELF    7e356000-7e366000    Deferred        libxext.so.6
ELF    7e366000-7e37e000    Deferred        libice.so.6
ELF    7e37e000-7e387000    Deferred        libsm.so.6
ELF    7e388000-7e38c000    Deferred        libkeyutils.so.1
ELF    7e395000-7e399000    Deferred        libcom_err.so.2
ELF    7e39b000-7e43a000    Deferred        winex11<elf>
  \-PE    7e3b0000-7e43a000    \               winex11
ELF    7e48b000-7e4b2000    Deferred        libexpat.so.1
ELF    7e4b2000-7e4df000    Deferred        libfontconfig.so.1
ELF    7e4f3000-7e509000    Deferred        libz.so.1
ELF    7e509000-7e580000    Deferred        libfreetype.so.6
ELF    7e580000-7e583000    Deferred        libxinerama.so.1
ELF    7e583000-7e588000    Deferred        libuuid.so.1
ELF    7e594000-7e5bd000    Deferred        oledlg<elf>
  \-PE    7e5a0000-7e5bd000    \               oledlg
ELF    7e5bd000-7e659000    Deferred        winmm<elf>
  \-PE    7e5d0000-7e659000    \               winmm
ELF    7e659000-7e70b000    Deferred        comdlg32<elf>
  \-PE    7e660000-7e70b000    \               comdlg32
ELF    7e70b000-7e741000    Deferred        winspool<elf>
  \-PE    7e710000-7e741000    \               winspool
ELF    7e741000-7e8d1000    Deferred        shell32<elf>
  \-PE    7e750000-7e8d1000    \               shell32
ELF    7e8d1000-7e99a000    Deferred        comctl32<elf>
  \-PE    7e8e0000-7e99a000    \               comctl32
ELF    7e99a000-7e9ae000    Deferred        lz32<elf>
  \-PE    7e9a0000-7e9ae000    \               lz32
ELF    7e9ae000-7e9c9000    Deferred        version<elf>
  \-PE    7e9b0000-7e9c9000    \               version
ELF    7e9c9000-7e9dd000    Deferred        msimg32<elf>
  \-PE    7e9d0000-7e9dd000    \               msimg32
ELF    7e9dd000-7ea4b000    Deferred        rpcrt4<elf>
  \-PE    7e9f0000-7ea4b000    \               rpcrt4
ELF    7ea4b000-7eaed000    Deferred        gdi32<elf>
  \-PE    7ea60000-7eaed000    \               gdi32
ELF    7eaed000-7ec39000    Deferred        user32<elf>
  \-PE    7eb10000-7ec39000    \               user32
ELF    7ec39000-7ec90000    Deferred        advapi32<elf>
  \-PE    7ec50000-7ec90000    \               advapi32
ELF    7ec90000-7ed8d000    Deferred        ole32<elf>
  \-PE    7ecb0000-7ed8d000    \               ole32
ELF    7ed8d000-7ee73000    Deferred        oleaut32<elf>
  \-PE    7eda0000-7ee73000    \               oleaut32
ELF    7efa1000-7efad000    Deferred        libnss_files.so.2
ELF    7efad000-7efc6000    Deferred        libnsl.so.1
ELF    7efc6000-7efec000    Deferred        libm.so.6
ELF    7efec000-7eff7000    Deferred        libnss_nis.so.2
ELF    7eff7000-7f000000    Deferred        libnss_compat.so.2
ELF    b7cf0000-b7cf4000    Deferred        libxau.so.6
ELF    b7cf5000-b7cf9000    Deferred        libdl.so.2
ELF    b7cf9000-b7e5c000    Deferred        libc.so.6
ELF    b7e5d000-b7e76000    Deferred        libpthread.so.0
ELF    b7e8a000-b7fc6000    Export          libwine.so.1
ELF    b7fc8000-b7fe6000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Novolit\Novolit 2005\novolit.exe
    00000009    0 <==
0000000e 
    00000015    0
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
=>0 0x7bc3c4d8 raise_status+0x38() in ntdll (0x0032f5d8)
  1 0x7bc6cba0 in ntdll (+0x5cba0) (0x0032f5f8)
  2 0x7bc827c5 in ntdll (+0x727c5) (0x0032f958)
  3 0x7bc6c174 RtlRaiseException+0xc() in ntdll (0x0032f9d4)
  4 0x00530d7b in novolit (+0x130d7b) (0x0032fa14)
  5 0x0053161f in novolit (+0x13161f) (0x0032fa4c)
  6 0x00428df8 in novolit (+0x28df8) (0x0032fa78)
  7 0x00429029 in novolit (+0x29029) (0x0032fad0)
  8 0x004292da in novolit (+0x292da) (0x0032fafc)
  9 0x00429219 in novolit (+0x29219) (0x0032fb18)
  10 0x00430112 in novolit (+0x30112) (0x0032fba0)
  11 0x004272bb in novolit (+0x272bb) (0x0032fbc0)
  12 0x0042302c in novolit (+0x2302c) (0x0032fbe4)
  13 0x004231b6 in novolit (+0x231b6) (0x0032fd04)
  14 0x00423247 in novolit (+0x23247) (0x0032fd34)
  15 0x00430dad in novolit (+0x30dad) (0x0032fe7c)
  16 0x0048e5ec in novolit (+0x8e5ec) (0x0032fea0)
  17 0x00a78734 in novolit (+0x678734) (0x0032feb8)
  18 0x7b8773a5 in kernel32 (+0x573a5) (0x0032fee8)
  19 0x7bc6c184 call_thread_func+0xc() in ntdll (0x0032fef8)
  20 0x7bc6c3a0 call_thread_entry_point+0x70() in ntdll (0x0032ffc8)
  21 0x7bc4985a in ntdll (+0x3985a) (0x0032ffe8)
  22 0xb7e9201d wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)

```

btw This application is free and could be found here [http://www.novolit.si/cgi-bin/downloadhr.cgi](http://www.novolit.si/cgi-bin/downloadhr.cgi) (just enter any name and e-mail, it doesn't have to be true)

---

### Post by qwertymn on 2009-10-03
>err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not >registered


Try 'winetricks mdac28'

---

### Post by qwertymn on 2009-10-03
hmm, just downloaded an ran the app, looks like it needs some more tricks.
Try this (if you use wine-0.9.30):

'winetricks mdac28 jet40'
'WINEDLLOVERRIDES="oledb32=n" regsvr32 ~/.wine/drive_c/Program\ Files/Common\ Files/System/OLE\ DB/oledb32.dll'
'WINEDLLOVERRIDES="oledb32=n" wine novolit.exe'

---

### Post by basraks on 2009-10-03
Tnx on suggestions. Thats step forward but I still have problems with this application. After winetricks mdac28 and jet40 I can start an application but I can't work in it. Program can't read from its database and I only get next error massage: 

dtProjekti: Cannot preform this operation on a closed dataset.

I also can't create new or import any finished project. :confused:

EDIT: With WINEDLLOVERRIDES application starts normally and I can actually work in it but its very unstable and it crashed with next error in terminal: fixme:richedit:ME_HandleMessage EM_FORMATRANGE: stub

Tnx once more! You helped me a lot and now I hope that I somehow will manage to solve this problem and actually work in it without Windows. That would be great solution for me because this is the last application that I really need for my work without any alternative software on linux or osx (well there are some other programs but not good as this one and also only for Windows). If this could work I'll leave Windows behind me for all times!

---

### Post by qwertymn on 2009-10-04
> EDIT: With WINEDLLOVERRIDES application starts normally and I can actually work in it but its very unstable and it crashed with next error in terminal: fixme:richedit:ME_HandleMessage EM_FORMATRANGE: stub

Two suggestions: try upgrade to wine-1.1.30 as i saw you used wine-1.0.1,right?

Or if you stick to wine-1.0.1 maybe try 'winetricks riched20 riched30'
The specific crash I didn't see in wine-1.1.30, but i saw another problem in comctl32, but it didn't seem fatal

---

### Post by basraks on 2009-10-05
I already have upgraded Wine on version 1.1.30 with no success but after winetricks riched20, riched30 and comctl32, and with winedlloverrides it seems its working fine. It is finally stable and usable so I can give it a try. Thanks a lot!

---

### Post by basraks on 2009-10-06
Sorry if I bother you with stupid questions but now I have problem on OsX. I have installed Wine 1.1.29.2 and all mentioned winetricks with one error on finishing mdac28 installation. And now I don't know how to add WINEDLLOVERRIDES. On Ubuntu I set this override with

'WINEDLLOVERRIDES="oledb32=n" regsvr32 ~/.wine/drive_c/Program\ Files/Common\ Files/System/OLE\ DB/oledb32.dll'

and after that I add oledb32 override in Wine configuration dialog in Libraries tab and now I can normally start application through main menu. 
But when I enter above mentioned command in OsX terminal I only get error 'regsvr32: command not found'. I have added oledb32 override in Wine configuration dialog but when I start application I get same old error message with something about database.
So my question is is it possible to add winedlloverrides through Wine configuration or do you maybe know what I should enter in OsX terminal to setup this oledb32 override?

---

### Post by qwertymn on 2009-10-06
> But when I enter above mentioned command in OsX terminal I only get error 'regsvr32: command not found'

Maybe a problem with the quotes, the outside quotes should be left out, sorry, so:

WINEDLLOVERRIDES="oledb32=n" regsvr32 ~/.wine/drive_c/Program\ Files/Common\ Files/System/OLE\ DB/oledb32.dll

> So my question is is it possible to add winedlloverrides through Wine configuration

running WINEDLLOVERRIDES="oledb32=n" is the same as setting oledb32 to native via winecfg. So if you already set oledb32 to native in winecfg you can leave the WINEDLLOVERRIDES out of the command. cheers

---

