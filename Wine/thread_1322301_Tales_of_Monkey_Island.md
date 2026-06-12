---
title: "Tales of Monkey Island"
date: 2009-11-10
forum: Wine
---

### Post by xenogia on 2009-11-10
I installed Tales of Monkey Island episode 1 (w/ crack) in Karmic using Wine 1.1.32. Just to note I also have the 190.42 nvidia drivers installed and using x64 version.  

Anyway the game comes up and crashes on boot up.  Below is the terminal output when I try to load it.  Any help would be great guys.

```

fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x1eac570
err:module:DelayLoadFailureHook failed to delay load rpcrt4.dll.I_RpcExceptionFilter
wine: Call from 0x7b843ca2 to unimplemented function rpcrt4.dll.I_RpcExceptionFilter, aborting
fixme:iphlpapi:NotifyAddrChange (Handle 0x794e8a4, overlapped 0x794e8ac): stub
wine: Unimplemented function rpcrt4.dll.I_RpcExceptionFilter called at address 0x7b843ca2 (thread 0009), starting debugger...
Unhandled exception: unimplemented function rpcrt4.dll.I_RpcExceptionFilter called in 32-bit code (0x7b843ca2).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b843ca2 ESP:01eaba64 EBP:01eabac8 EFLAGS:00000246(   - --  I  Z- -P- )
 EAX:7b82e84d EBX:7b8b3ff4 ECX:00000000 EDX:80000100
 ESI:80000100 EDI:7ec7187c
Stack dump:
0x01eaba64:  01eabaf8 00000008 0000003c 80000100
0x01eaba74:  00000001 00000000 7b843ca2 00000002
0x01eaba84:  7ec7187c 7ec71887 f76193f7 00000001
0x01eaba94:  7b96e6b0 7b8ace5f 7b8acdd9 01eabae0
0x01eabaa4:  7bc95ff4 01eabae8 7bc4d425 7bc9e764
0x01eabab4:  7ec71887 ffffffff 7b843c5a 7b8b3ff4
Backtrace:
=>0 0x7b843ca2 in kernel32 (+0x23ca2) (0x01eabac8)
  1 0x7b86632b DelayLoadFailureHook+0x5b() in kernel32 (0x01eabb18)
  2 0x7ec636ca in advapi32 (+0x336ca) (0x01eabb58)
  3 0x7ec36fe8 in advapi32 (+0x6fe8) (0x01eabb88)
  4 0x7ec5c5ad in advapi32 (+0x2c5ad) (0x01eabbd8)
  5 0x7bc6cbf9 call_exception_handler+0x29() in ntdll (0x01eabc08)
  6 0x7bc6cbcb EXC_CallHandler+0x1b() in ntdll (0x01eabc28)
  7 0x7bc6d156 in ntdll (+0x5d156) (0x01eabcb8)
  8 0x7bc6d594 __regs_RtlRaiseException+0x34() in ntdll (0x01eabcd8)
  9 0x7bc83565 in ntdll (+0x73565) (0x01eac038)
  10 0x7bc6cb84 RtlRaiseException+0xc() in ntdll (0x01eac0b4)
err:dbghelp:pe_load_dbg_file Couldn't find .DBG file "rpcrt4.dbg" ("")
  11 0x7010a6d7 in rpcrt4 (+0xa6d7) (0x01eac2e4)
  12 0x7ec5bc1e OpenSCManagerW+0x8e() in advapi32 (0x01eac3d4)
  13 0x7ec5cd7d OpenSCManagerA+0x15d() in advapi32 (0x01eac424)
  14 0x0559269d in xul (+0xe269d) (0x01eac484)
  15 0x05591fc6 in xul (+0xe1fc6) (0x01eac4c4)
  16 0x05591ef8 in xul (+0xe1ef8) (0x01eac4f4)
  17 0x05591e47 in xul (+0xe1e47) (0x01eac514)
  18 0x05591d2e in xul (+0xe1d2e) (0x01eac7f4)
  19 0x05572c51 in xul (+0xc2c51) (0x01eac814)
  20 0x05570a55 in xul (+0xc0a55) (0x01eac8b4)
  21 0x05570d06 in xul (+0xc0d06) (0x01eac8e4)
  22 0x05561619 in xul (+0xb1619) (0x01eac904)
  23 0x060946d3 in xul (+0xbe46d3) (0x01eac924)
  24 0x7d88fb3c init_nsio+0x7c() in mshtml (0x01eac984)
  25 0x7d88e24f load_gecko+0x20f() in mshtml (0x01eacc74)
  26 0x7d88e785 NSContainer_Create+0x25() in mshtml (0x01eaccd4)
  27 0x7d84a8c5 HTMLDocument_Create+0xf5() in mshtml (0x01eacd44)
  28 0x7d8847d0 in mshtml (+0x547d0) (0x01eacd64)
err:dbghelp:pe_load_dbg_file Couldn't find .DBG file "ole32.dbg" ("")
  29 0x65f14078 in ole32 (+0x14078) (0x01eacff4)
  30 0x65f143c4 in ole32 (+0x143c4) (0x01ead020)
  31 0x65f14397 in ole32 (+0x14397) (0x01ead048)
  32 0x7d8fb5c1 in urlmon (+0xb5c1) (0x01ead0e8)
  33 0x7d8fbc18 in urlmon (+0xbc18) (0x01ead138)
  34 0x7d8ff38a in urlmon (+0xf38a) (0x01ead9a8)
  35 0x7d8ff56c in urlmon (+0xf56c) (0x01ead9e8)
  36 0x7d901cf0 in urlmon (+0x11cf0) (0x01eadac8)
  37 0x7d8feb40 in urlmon (+0xeb40) (0x01eadb78)
  38 0x7d8fe6f5 in urlmon (+0xe6f5) (0x01eadbd8)
  39 0x7d8fc761 in urlmon (+0xc761) (0x01eadcd8)
  40 0x7d8fc97e bind_to_object+0x3e() in urlmon (0x01eadd18)
  41 0x7d912235 in urlmon (+0x22235) (0x01eadd78)
  42 0x7d9471ed in shdocvw (+0x171ed) (0x01eadee8)
  43 0x7d94767e in shdocvw (+0x1767e) (0x01eae028)
  44 0x7d947da3 in shdocvw (+0x17da3) (0x01eae058)
  45 0x7d93ed96 process_dochost_task+0x16() in shdocvw (0x01eae078)
  46 0x7d949ee1 in shdocvw (+0x19ee1) (0x01eae0c8)
  47 0x7eddf7aa WINPROC_wrapper+0x1a() in user32 (0x01eae0f8)
  48 0x7ede0d8d in user32 (+0xb0d8d) (0x01eae148)
  49 0x7ede4b5b in user32 (+0xb4b5b) (0x01eae198)
  50 0x7eda3501 in user32 (+0x73501) (0x01eae1f8)
  51 0x7eda81e6 in user32 (+0x781e6) (0x01eae278)
  52 0x7eda868c SendMessageW+0x4c() in user32 (0x01eae2c8)
  53 0x7d93ee1f push_dochost_task+0x5f() in shdocvw (0x01eae2e8)
  54 0x7d946a94 navigate_url+0x164() in shdocvw (0x01eae348)
  55 0x7d9515b3 in shdocvw (+0x215b3) (0x01eae3b8)
  56 0x007c7d76 in monkeyisland101 (+0x3c7d76) (0x7edc2b30)
  57 0x458b68ec (0x83e58955)
  58 0x00000000 (0x00000000)
0x7b843ca2: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (150 modules)
PE      3a0000-  3a8000    Deferred        xpcom
PE      3b0000-  3eb000    Deferred        nspr4
PE      3f0000-  3fa000    Deferred        plds4
PE      400000- 19aa000    Export          monkeyisland101
PE     3fa0000- 40bb000    Deferred        js3250
PE     40c0000- 40d5000    Deferred        nssutil3
PE     40e0000- 40ea000    Deferred        plc4
PE     40f0000- 40f7000    Deferred        rpcltc1
PE     54b0000- 6788000    Export          xul
PE     6790000- 685b000    Deferred        nss3
PE     6860000- 6881000    Deferred        smime3
PE     6890000- 690d000    Deferred        sqlite3
PE     6910000- 693a000    Deferred        ssl3
PE    10000000-101a6000    Deferred        fmodex
PE    65340000-653d2000    Deferred        oleaut32
PE    65f00000-65fc2000    Export          ole32
PE    70100000-70153000    Export          rpcrt4
PE    78000000-78044000    Deferred        msvcrt
ELF    7b800000-7b971000    Export          kernel32<elf>
  \-PE    7b820000-7b971000    \               kernel32
ELF    7bc00000-7bcb2000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb2000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d7c0000-7d7d5000    Deferred        dwmapi<elf>
  \-PE    7d7d0000-7d7d5000    \               dwmapi
ELF    7d7d5000-7d7e9000    Deferred        lz32<elf>
  \-PE    7d7e0000-7d7e9000    \               lz32
ELF    7d7e9000-7d803000    Deferred        version<elf>
  \-PE    7d7f0000-7d803000    \               version
ELF    7d803000-7d81c000    Deferred        usp10<elf>
  \-PE    7d810000-7d81c000    \               usp10
ELF    7d81c000-7d8e2000    Export          mshtml<elf>
  \-PE    7d830000-7d8e2000    \               mshtml
ELF    7d8e2000-7d927000    Export          urlmon<elf>
  \-PE    7d8f0000-7d927000    \               urlmon
ELF    7d927000-7d968000    Export          shdocvw<elf>
  \-PE    7d930000-7d968000    \               shdocvw
ELF    7d968000-7d96d000    Deferred        libgpg-error.so.0
ELF    7d96d000-7d9e9000    Deferred        libgcrypt.so.11
ELF    7d9e9000-7d9fb000    Deferred        libtasn1.so.3
ELF    7d9fb000-7d9ff000    Deferred        libkeyutils.so.1
ELF    7d9ff000-7da08000    Deferred        libkrb5support.so.0
ELF    7da08000-7da0c000    Deferred        libcom_err.so.2
ELF    7da0c000-7da37000    Deferred        libk5crypto.so.3
ELF    7da37000-7dae9000    Deferred        libkrb5.so.3
ELF    7dae9000-7dafa000    Deferred        libavahi-client.so.3
ELF    7dafa000-7db06000    Deferred        libavahi-common.so.3
ELF    7db06000-7dbae000    Deferred        libgnutls.so.26
ELF    7dbae000-7dbdb000    Deferred        libgssapi_krb5.so.2
ELF    7dbdb000-7dc20000    Deferred        libcups.so.2
ELF    7dc27000-7dc3b000    Deferred        msimg32<elf>
  \-PE    7dc30000-7dc3b000    \               msimg32
ELF    7dc3b000-7dc51000    Deferred        midimap<elf>
  \-PE    7dc40000-7dc51000    \               midimap
ELF    7dc51000-7dc58000    Deferred        libogg.so.0
ELF    7dc58000-7dc83000    Deferred        libvorbis.so.0
ELF    7dc83000-7dd7d000    Deferred        libvorbisenc.so.2
ELF    7dd7d000-7ddcd000    Deferred        libflac.so.8
ELF    7ddcd000-7de06000    Deferred        libdbus-1.so.3
ELF    7de06000-7de72000    Deferred        libsndfile.so.1
ELF    7de72000-7de7b000    Deferred        libwrap.so.0
ELF    7de7b000-7de81000    Deferred        libxtst.so.6
ELF    7de81000-7decb000    Deferred        libpulsecommon-0.9.19.so
ELF    7decb000-7df0b000    Deferred        libpulse.so.0
ELF    7df0b000-7df14000    Deferred        librt.so.1
ELF    7df14000-7dfdc000    Deferred        libasound.so.2
ELF    7dfdf000-7dff7000    Deferred        msacm32<elf>
  \-PE    7dfe0000-7dff7000    \               msacm32
ELF    7dff7000-7e02e000    Deferred        winealsa<elf>
  \-PE    7e000000-7e02e000    \               winealsa
ELF    7e042000-7e075000    Deferred        uxtheme<elf>
  \-PE    7e050000-7e075000    \               uxtheme
ELF    7e075000-7e0a9000    Deferred        winspool<elf>
  \-PE    7e080000-7e0a9000    \               winspool
ELF    7e0a9000-7e15b000    Deferred        comdlg32<elf>
  \-PE    7e0b0000-7e15b000    \               comdlg32
ELF    7e15b000-7e194000    Deferred        dinput<elf>
  \-PE    7e160000-7e194000    \               dinput
ELF    7e194000-7e1a8000    Deferred        libresolv.so.2
ELF    7e1a9000-7e1c3000    Deferred        dinput8<elf>
  \-PE    7e1b0000-7e1c3000    \               dinput8
ELF    7e1c3000-7e1e3000    Deferred        iphlpapi<elf>
  \-PE    7e1d0000-7e1e3000    \               iphlpapi
ELF    7e1e3000-7e20d000    Deferred        ws2_32<elf>
  \-PE    7e1f0000-7e20d000    \               ws2_32
ELF    7e20d000-7e228000    Deferred        wsock32<elf>
  \-PE    7e210000-7e228000    \               wsock32
ELF    7e228000-7e2af000    Deferred        winmm<elf>
  \-PE    7e230000-7e2af000    \               winmm
ELF    7e2af000-7e2d5000    Deferred        msacm32<elf>
  \-PE    7e2c0000-7e2d5000    \               msacm32
ELF    7e2d5000-7e465000    Deferred        shell32<elf>
  \-PE    7e2f0000-7e465000    \               shell32
ELF    7e465000-7e488000    Deferred        mpr<elf>
  \-PE    7e470000-7e488000    \               mpr
ELF    7e488000-7e4df000    Deferred        wininet<elf>
  \-PE    7e490000-7e4df000    \               wininet
ELF    7e4df000-7e4ea000    Deferred        libxcursor.so.1
ELF    7e4ea000-7e4f0000    Deferred        libxfixes.so.3
ELF    7e4f0000-7e4f4000    Deferred        libxcomposite.so.1
ELF    7e4f4000-7e4fd000    Deferred        libxrandr.so.2
ELF    7e4fd000-7e507000    Deferred        libxrender.so.1
ELF    7e507000-7e50d000    Deferred        libxxf86vm.so.1
ELF    7e50d000-7e510000    Deferred        libxinerama.so.1
ELF    7e510000-7e531000    Deferred        imm32<elf>
  \-PE    7e520000-7e531000    \               imm32
ELF    7e531000-7e536000    Deferred        libxdmcp.so.6
ELF    7e536000-7e554000    Deferred        libxcb.so.1
ELF    7e554000-7e558000    Deferred        libxau.so.6
ELF    7e558000-7e55d000    Deferred        libuuid.so.1
ELF    7e55d000-7e68c000    Deferred        libx11.so.6
ELF    7e68c000-7e69c000    Deferred        libxext.so.6
ELF    7e69c000-7e6b7000    Deferred        libice.so.6
ELF    7e6b7000-7e6c0000    Deferred        libsm.so.6
ELF    7e6db000-7e779000    Deferred        winex11<elf>
  \-PE    7e6f0000-7e779000    \               winex11
ELF    7e852000-7e879000    Deferred        libexpat.so.1
ELF    7e879000-7e8a6000    Deferred        libfontconfig.so.1
ELF    7e8a6000-7e8bc000    Deferred        libz.so.1
ELF    7e8bc000-7e93b000    Deferred        libfreetype.so.6
ELF    7e956000-7e96b000    Deferred        system.drv16.so
PE    7e960000-7e96b000    Deferred        system.drv16
ELF    7e96b000-7e996000    Deferred        d3dx9_36<elf>
  \-PE    7e970000-7e996000    \               d3dx9_36
ELF    7e996000-7eac3000    Deferred        wined3d<elf>
  \-PE    7e9a0000-7eac3000    \               wined3d
ELF    7eac3000-7eaf6000    Deferred        d3d9<elf>
  \-PE    7ead0000-7eaf6000    \               d3d9
ELF    7eaf6000-7ebbe000    Deferred        comctl32<elf>
  \-PE    7eb00000-7ebbe000    \               comctl32
ELF    7ebbe000-7ec1b000    Deferred        shlwapi<elf>
  \-PE    7ebd0000-7ec1b000    \               shlwapi
ELF    7ec1b000-7ec72000    Export          advapi32<elf>
  \-PE    7ec30000-7ec72000    \               advapi32
ELF    7ec72000-7ed12000    Deferred        gdi32<elf>
  \-PE    7ec80000-7ed12000    \               gdi32
ELF    7ed12000-7ee5d000    Export          user32<elf>
  \-PE    7ed30000-7ee5d000    \               user32
ELF    7ef89000-7ef95000    Deferred        libnss_files.so.2
ELF    7ef95000-7efa0000    Deferred        libnss_nis.so.2
ELF    7efa0000-7efb7000    Deferred        libnsl.so.1
ELF    7efb7000-7efbf000    Deferred        libnss_compat.so.2
ELF    7efbf000-7efe5000    Deferred        libm.so.6
ELF    7efe6000-7f000000    Deferred        d3dx9_41<elf>
  \-PE    7eff0000-7f000000    \               d3dx9_41
ELF    f7497000-f749b000    Deferred        libdl.so.2
ELF    f749b000-f75df000    Deferred        libc.so.6
ELF    f75e0000-f75f9000    Deferred        libpthread.so.0
ELF    f7614000-f774f000    Deferred        libwine.so.1
ELF    f7751000-f776f000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\media\isos\GAMES\tomi1\Launch of the Screaming Narwhal\MonkeyIsland101.exe
    0000001e    0
    0000001d    0
    0000001c    0
    0000001b    0
    00000009    0 <==
0000000e 
    00000017    0
    00000015    0
    00000014    0
    00000010    0
    0000000f    0
00000011 
    00000018    0
    00000016    0
    00000013    0
    00000012    0
00000019 
    0000001a    0
Backtrace:
=>0 0x7b843ca2 in kernel32 (+0x23ca2) (0x01eabac8)
  1 0x7b86632b DelayLoadFailureHook+0x5b() in kernel32 (0x01eabb18)
  2 0x7ec636ca in advapi32 (+0x336ca) (0x01eabb58)
  3 0x7ec36fe8 in advapi32 (+0x6fe8) (0x01eabb88)
  4 0x7ec5c5ad in advapi32 (+0x2c5ad) (0x01eabbd8)
  5 0x7bc6cbf9 call_exception_handler+0x29() in ntdll (0x01eabc08)
  6 0x7bc6cbcb EXC_CallHandler+0x1b() in ntdll (0x01eabc28)
  7 0x7bc6d156 in ntdll (+0x5d156) (0x01eabcb8)
  8 0x7bc6d594 __regs_RtlRaiseException+0x34() in ntdll (0x01eabcd8)
  9 0x7bc83565 in ntdll (+0x73565) (0x01eac038)
  10 0x7bc6cb84 RtlRaiseException+0xc() in ntdll (0x01eac0b4)
  11 0x7010a6d7 in rpcrt4 (+0xa6d7) (0x01eac2e4)
  12 0x7ec5bc1e OpenSCManagerW+0x8e() in advapi32 (0x01eac3d4)
  13 0x7ec5cd7d OpenSCManagerA+0x15d() in advapi32 (0x01eac424)
  14 0x0559269d in xul (+0xe269d) (0x01eac484)
  15 0x05591fc6 in xul (+0xe1fc6) (0x01eac4c4)
  16 0x05591ef8 in xul (+0xe1ef8) (0x01eac4f4)
  17 0x05591e47 in xul (+0xe1e47) (0x01eac514)
  18 0x05591d2e in xul (+0xe1d2e) (0x01eac7f4)
  19 0x05572c51 in xul (+0xc2c51) (0x01eac814)
  20 0x05570a55 in xul (+0xc0a55) (0x01eac8b4)
  21 0x05570d06 in xul (+0xc0d06) (0x01eac8e4)
  22 0x05561619 in xul (+0xb1619) (0x01eac904)
  23 0x060946d3 in xul (+0xbe46d3) (0x01eac924)
  24 0x7d88fb3c init_nsio+0x7c() in mshtml (0x01eac984)
  25 0x7d88e24f load_gecko+0x20f() in mshtml (0x01eacc74)
  26 0x7d88e785 NSContainer_Create+0x25() in mshtml (0x01eaccd4)
  27 0x7d84a8c5 HTMLDocument_Create+0xf5() in mshtml (0x01eacd44)
  28 0x7d8847d0 in mshtml (+0x547d0) (0x01eacd64)
  29 0x65f14078 in ole32 (+0x14078) (0x01eacff4)
  30 0x65f143c4 in ole32 (+0x143c4) (0x01ead020)
  31 0x65f14397 in ole32 (+0x14397) (0x01ead048)
  32 0x7d8fb5c1 in urlmon (+0xb5c1) (0x01ead0e8)
  33 0x7d8fbc18 in urlmon (+0xbc18) (0x01ead138)
  34 0x7d8ff38a in urlmon (+0xf38a) (0x01ead9a8)
  35 0x7d8ff56c in urlmon (+0xf56c) (0x01ead9e8)
  36 0x7d901cf0 in urlmon (+0x11cf0) (0x01eadac8)
  37 0x7d8feb40 in urlmon (+0xeb40) (0x01eadb78)
  38 0x7d8fe6f5 in urlmon (+0xe6f5) (0x01eadbd8)
  39 0x7d8fc761 in urlmon (+0xc761) (0x01eadcd8)
  40 0x7d8fc97e bind_to_object+0x3e() in urlmon (0x01eadd18)
  41 0x7d912235 in urlmon (+0x22235) (0x01eadd78)
  42 0x7d9471ed in shdocvw (+0x171ed) (0x01eadee8)
  43 0x7d94767e in shdocvw (+0x1767e) (0x01eae028)
  44 0x7d947da3 in shdocvw (+0x17da3) (0x01eae058)
  45 0x7d93ed96 process_dochost_task+0x16() in shdocvw (0x01eae078)
  46 0x7d949ee1 in shdocvw (+0x19ee1) (0x01eae0c8)
  47 0x7eddf7aa WINPROC_wrapper+0x1a() in user32 (0x01eae0f8)
  48 0x7ede0d8d in user32 (+0xb0d8d) (0x01eae148)
  49 0x7ede4b5b in user32 (+0xb4b5b) (0x01eae198)
  50 0x7eda3501 in user32 (+0x73501) (0x01eae1f8)
  51 0x7eda81e6 in user32 (+0x781e6) (0x01eae278)
  52 0x7eda868c SendMessageW+0x4c() in user32 (0x01eae2c8)
  53 0x7d93ee1f push_dochost_task+0x5f() in shdocvw (0x01eae2e8)
  54 0x7d946a94 navigate_url+0x164() in shdocvw (0x01eae348)
  55 0x7d9515b3 in shdocvw (+0x215b3) (0x01eae3b8)
  56 0x007c7d76 in monkeyisland101 (+0x3c7d76) (0x7edc2b30)
  57 0x458b68ec (0x83e58955)
  58 0x00000000 (0x00000000)
err:seh:raise_exception Unhandled exception code 80000100 flags 1 addr 0x7b843ca2

```

---

### Post by joeelmex on 2009-11-10
Did you make the changes that the guide recommended?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17135](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17135)

---

### Post by beastrace91 on 2009-11-10
> **xenogia said:**
> (w/ crack)

What do you mean by crack? As a heads up it is against forum rules to post about pirated software. Also remember that if this is the case it can cause random issues in an application by using 3rd party cracks - so don't expect much help getting them working.

~Jeff

---

### Post by xenogia on 2009-11-10
My apologies I own the game but I thought I needed a NoCD patch.  Anyway I reinstalled the game with no NoCD patch and it still crashes on startup.

---

