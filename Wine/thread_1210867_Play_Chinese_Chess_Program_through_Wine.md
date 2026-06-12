---
title: "Play Chinese Chess Program through Wine"
date: 2009-07-12
forum: Wine
---

### Post by hosammy on 2009-07-12
I am using Ubuntu 9.04 & wine 1.1.25
I try to install the ECMS.exe, which is a Windows program that allows the players to play Chinese Chess (Xiang Qi) online. [http://www.chesssky.net/cdenglu.htm](http://www.chesssky.net/cdenglu.htm)

During the installation, Problem appears...
After unzip the zip file to a ../movesky/ folder, then I type:
[HTML]> [COLOR="Blue"]
sammy@sammy-desktop:~/Tmp/Movesky$ wine ECMS.exe
fixme:shdocvw:PersistStreamInit_InitNew (0x195420)
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32f9f4:3; TargetFrameName 0x32f9e4:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32e754
fixme:iphlpapi:NotifyAddrChange (Handle 0x29be8d4, overlapped 0x29be8dc): stub
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1954c0)->((null) 1 0x32ecec (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1954c0)->((null) 25 2 0x32ed00 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1954c0)->((null) 26 2 0x32ed00 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1954c0)->(0x32ed3c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1954c0)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32ee10 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1954c0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32eea0)
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32ea0c:3; TargetFrameName 0x32e9fc:8)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32f494:3; TargetFrameName 0x32f484:8)
fixme:shdocvw:PersistStreamInit_InitNew (0x1b9190)
fixme:shdocvw:PersistStreamInit_InitNew (0x1b95a8)
fixme:shdocvw:PersistStreamInit_InitNew (0x1b99c0)
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32f430:3; TargetFrameName 0x32f420:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1b9230)->((null) 1 0x32e728 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9230)->((null) 25 2 0x32e73c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9230)->((null) 26 2 0x32e73c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1b9230)->(0x32e778)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9230)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32e84c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9230)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e8dc)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32f42c:3; TargetFrameName 0x32f41c:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1b9648)->((null) 1 0x32e72c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9648)->((null) 25 2 0x32e740 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9648)->((null) 26 2 0x32e740 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1b9648)->(0x32e77c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9648)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32e850 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9648)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e8e0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32f42c:3; TargetFrameName 0x32f41c:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1b9a60)->((null) 1 0x32e72c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9a60)->((null) 25 2 0x32e740 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9a60)->((null) 26 2 0x32e740 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1b9a60)->(0x32e77c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9a60)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32e850 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9a60)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e8e0)
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32eeec:3; TargetFrameName 0x32eedc:8)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32eeec:3; TargetFrameName 0x32eedc:8)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32eeec:3; TargetFrameName 0x32eedc:8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1954c0)->((null) 29 2 0x32e468 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1954c0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1954c0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e378)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9230)->((null) 29 2 0x32e468 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1b9230)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9230)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e378)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9648)->((null) 29 2 0x32e468 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1b9648)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9648)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e378)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b9a60)->((null) 29 2 0x32e468 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1b9a60)
wine: Unhandled page fault on read access to 0x00000016 at address 0x19b883e (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000016 in 32-bit code (0x019b883e).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:019b883e ESP:0032de14 EBP:0032de6c EFLAGS:00010206(  R- --  I   - -P- )
 EAX:00000000 EBX:0032df24 ECX:02505ca8 EDX:0032de44
 ESI:0000c05c EDI:0001008c
Stack dump:
0x0032de14:  00000028 00000008 0032de3c 01c16a91
0x0032de24:  0250625c 00000008 0032de4c 01e07393
0x0032de34:  02505cb0 00000005 0032de5c 01c16be4
0x0032de44:  01906200 00000000 00000000 40400000
0x0032de54:  02505cb0 00000005 00000005 00000000
0x0032de64:  0250625c 0032df24 0032deac 019b8eeb
Backtrace:
=>0 0x019b883e in xul (+0xbc883e) (0x0032de6c)
  1 0x019b8eeb in xul (+0xbc8eeb) (0x0032deac)
  2 0x01887330 in xul (+0xa97330) (0x0032dedc)
  3 0x018877ad in xul (+0xa977ad) (0x0032defc)
  4 0x01089098 in xul (+0x299098) (0x0032df2c)
  5 0x01089217 in xul (+0x299217) (0x0032df7c)
  6 0x01089247 in xul (+0x299247) (0x0032df9c)
  7 0x01b4ca7a in xul (+0xd5ca7a) (0x0032dfbc)
  8 0x0105c7cd in xul (+0x26c7cd) (0x0032e00c)
  9 0x0104f984 in xul (+0x25f984) (0x0032e2cc)
  10 0x01063f2e in xul (+0x273f2e) (0x0032e33c)
  11 0x010853c0 in xul (+0x2953c0) (0x0032e4fc)
  12 0x01063f2e in xul (+0x273f2e) (0x0032e56c)
  13 0x0107ce00 in xul (+0x28ce00) (0x0032e6bc)
  14 0x0107d00c in xul (+0x28d00c) (0x0032e78c)
  15 0x0107d7f2 in xul (+0x28d7f2) (0x0032e89c)
  16 0x01063f2e in xul (+0x273f2e) (0x0032e90c)
  17 0x010cb37e in xul (+0x2db37e) (0x0032ea6c)
  18 0x01045614 in xul (+0x255614) (0x0032ec0c)
  19 0x010457d6 in xul (+0x2557d6) (0x0032ec5c)
  20 0x01040f1a in xul (+0x250f1a) (0x0032eccc)
  21 0x01045159 in xul (+0x255159) (0x0032ed0c)
  22 0x0196559f in xul (+0xb7559f) (0x0032ed8c)
  23 0x019200d7 in xul (+0xb300d7) (0x0032edbc)
  24 0x01965349 in xul (+0xb75349) (0x0032edfc)
  25 0x01972e9f in xul (+0xb82e9f) (0x0032ee1c)
  26 0x01972e6b in xul (+0xb82e6b) (0x0032ee3c)
  27 0x01969d64 in xul (+0xb79d64) (0x0032ee5c)
  28 0x0196559f in xul (+0xb7559f) (0x0032eedc)
  29 0x019200d7 in xul (+0xb300d7) (0x0032ef0c)
  30 0x01965349 in xul (+0xb75349) (0x0032ef4c)
  31 0x01972e9f in xul (+0xb82e9f) (0x0032ef6c)
  32 0x01972e6b in xul (+0xb82e6b) (0x0032ef8c)
  33 0x01969d64 in xul (+0xb79d64) (0x0032efac)
  34 0x0196559f in xul (+0xb7559f) (0x0032f02c)
  35 0x019200d7 in xul (+0xb300d7) (0x0032f05c)
  36 0x01965349 in xul (+0xb75349) (0x0032f09c)
  37 0x01972e9f in xul (+0xb82e9f) (0x0032f0b4)
  38 0x01972e6b in xul (+0xb82e6b) (0x0032f0d4)
  39 0x01969d64 in xul (+0xb79d64) (0x0032f0f4)
  40 0x0196559f in xul (+0xb7559f) (0x0032f174)
  41 0x01920004 in xul (+0xb30004) (0x0032f1a4)
  42 0x018c0e16 in xul (+0xad0e16) (0x0032f1d4)
  43 0x0189b53e in xul (+0xaab53e) (0x0032f1f4)
  44 0x7ecc778a WINPROC_wrapper+0x1a() in user32 (0x0032f224)
  45 0x7ecc7bda WINPROC_wrapper+0x46a() in user32 (0x0032f264)
  46 0x7eccbc99 in user32 (+0xbbc99) (0x0032f734)
  47 0x7ecccd64 CallWindowProcA+0xc4() in user32 (0x0032f774)
  48 0x5f406aae in mfc42 (+0x6aae) (0x0032f7e8)
  49 0x7ecc778a WINPROC_wrapper+0x1a() in user32 (0x0032f818)
  50 0x7ecc7bda WINPROC_wrapper+0x46a() in user32 (0x0032f858)
  51 0x7ecccf07 in user32 (+0xbcf07) (0x0032f898)
  52 0x7ec8c0b6 DispatchMessageA+0x96() in user32 (0x0032f8d8)
  53 0x5f4011ce in mfc42 (+0x11ce) (0x00542f2c)
  54 0x0000c05c (0x0001008c)
  55 0x00000000 (0x00000000)
0x019b883e: movw	0x16(%eax),%ax
Modules:
Module	Address			Debug info	Name (139 modules)
PE	  340000-  34a000	Deferred        plds4
PE	  390000-  3cb000	Deferred        nspr4
PE	  3d0000-  3e5000	Deferred        nssutil3
PE	  3f0000-  3fa000	Deferred        plc4
PE	  400000-  5c9000	Deferred        ecms
PE	  df0000- 1fdb000	Export          xul
PE	 1fe0000- 20a3000	Deferred        js3250
PE	 20b0000- 218e000	Deferred        nss3
PE	 2190000- 21b1000	Deferred        smime3
PE	 21c0000- 2239000	Deferred        sqlite3
PE	 2240000- 2269000	Deferred        ssl3
PE	10000000-10008000	Deferred        xpcom
PE	5f400000-5f4f2000	Export          mfc42
ELF	77fe8000-78000000	Deferred        msacm32<elf>
  \-PE	77ff0000-78000000	\               msacm32
PE	78000000-78044000	Deferred        msvcrt
ELF	7b7ec000-7b800000	Deferred        t2embed<elf>
  \-PE	7b7f0000-7b800000	\               t2embed
ELF	7b800000-7b954000	Deferred        kernel32<elf>
  \-PE	7b820000-7b954000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c026000-7c07f000	Deferred        jscript<elf>
  \-PE	7c030000-7c07f000	\               jscript
ELF	7c17f000-7c1e8000	Deferred        libgcrypt.so.11
ELF	7c1e8000-7c27a000	Deferred        libkrb5.so.3
ELF	7db20000-7db35000	Deferred        dwmapi<elf>
  \-PE	7db30000-7db35000	\               dwmapi
ELF	7db35000-7db39000	Deferred        libgpg-error.so.0
ELF	7db39000-7db4b000	Deferred        libtasn1.so.3
ELF	7db4b000-7db4f000	Deferred        libkeyutils.so.1
ELF	7db4f000-7db58000	Deferred        libkrb5support.so.0
ELF	7db58000-7db7c000	Deferred        libk5crypto.so.3
ELF	7db7c000-7dc19000	Deferred        libgnutls.so.26
ELF	7dc19000-7dc44000	Deferred        libgssapi_krb5.so.2
ELF	7dc44000-7dc7b000	Deferred        libcups.so.2
ELF	7dc7b000-7dc94000	Deferred        spoolss<elf>
  \-PE	7dc80000-7dc94000	\               spoolss
ELF	7dc94000-7dcb2000	Deferred        localspl<elf>
  \-PE	7dca0000-7dcb2000	\               localspl
ELF	7dcb2000-7dcc6000	Deferred        lz32<elf>
  \-PE	7dcc0000-7dcc6000	\               lz32
ELF	7dcc6000-7dce1000	Deferred        version<elf>
  \-PE	7dcd0000-7dce1000	\               version
ELF	7dce1000-7dcfa000	Deferred        usp10<elf>
  \-PE	7dcf0000-7dcfa000	\               usp10
ELF	7dcfa000-7dd0e000	Deferred        msimg32<elf>
  \-PE	7dd00000-7dd0e000	\               msimg32
ELF	7dd0e000-7dd44000	Deferred        winspool<elf>
  \-PE	7dd20000-7dd44000	\               winspool
ELF	7dd44000-7ddf6000	Deferred        comdlg32<elf>
  \-PE	7dd50000-7ddf6000	\               comdlg32
ELF	7ddf6000-7deb1000	Deferred        mshtml<elf>
  \-PE	7de00000-7deb1000	\               mshtml
ELF	7deb1000-7ded4000	Deferred        mpr<elf>
  \-PE	7dec0000-7ded4000	\               mpr
ELF	7ded4000-7df27000	Deferred        wininet<elf>
  \-PE	7dee0000-7df27000	\               wininet
ELF	7df27000-7df6b000	Deferred        urlmon<elf>
  \-PE	7df30000-7df6b000	\               urlmon
ELF	7dfdf000-7e01f000	Deferred        shdocvw<elf>
  \-PE	7dff0000-7e01f000	\               shdocvw
ELF	7e01f000-7e035000	Deferred        libresolv.so.2
ELF	7e035000-7e055000	Deferred        iphlpapi<elf>
  \-PE	7e040000-7e055000	\               iphlpapi
ELF	7e055000-7e083000	Deferred        ws2_32<elf>
  \-PE	7e060000-7e083000	\               ws2_32
ELF	7e083000-7e09e000	Deferred        wsock32<elf>
  \-PE	7e090000-7e09e000	\               wsock32
ELF	7e09e000-7e0b3000	Deferred        midimap<elf>
  \-PE	7e0a0000-7e0b3000	\               midimap
ELF	7e0b3000-7e0d9000	Deferred        msacm32<elf>
  \-PE	7e0c0000-7e0d9000	\               msacm32
ELF	7e0d9000-7e0df000	Deferred        libattr.so.1
ELF	7e0df000-7e0e6000	Deferred        libgdbm.so.3
ELF	7e0e6000-7e145000	Deferred        libpulse.so.0
ELF	7e155000-7e21d000	Deferred        libasound.so.2
ELF	7e21d000-7e221000	Deferred        libcom_err.so.2
ELF	7e221000-7e226000	Deferred        libcap.so.2
ELF	7e226000-7e22d000	Deferred        libasound_module_pcm_pulse.so
ELF	7e22d000-7e264000	Deferred        winealsa<elf>
  \-PE	7e240000-7e264000	\               winealsa
ELF	7e291000-7e2c4000	Deferred        uxtheme<elf>
  \-PE	7e2a0000-7e2c4000	\               uxtheme
ELF	7e2c4000-7e2cd000	Deferred        libxcursor.so.1
ELF	7e2cd000-7e2d2000	Deferred        libxfixes.so.3
ELF	7e2d2000-7e2d6000	Deferred        libxcomposite.so.1
ELF	7e2d6000-7e2de000	Deferred        libxrandr.so.2
ELF	7e2de000-7e2e8000	Deferred        libxrender.so.1
ELF	7e2e8000-7e2ee000	Deferred        libxxf86vm.so.1
ELF	7e2ee000-7e2f1000	Deferred        libxinerama.so.1
ELF	7e2f1000-7e312000	Deferred        imm32<elf>
  \-PE	7e300000-7e312000	\               imm32
ELF	7e312000-7e317000	Deferred        libxdmcp.so.6
ELF	7e317000-7e331000	Deferred        libxcb.so.1
ELF	7e331000-7e420000	Deferred        libx11.so.6
ELF	7e420000-7e430000	Deferred        libxext.so.6
ELF	7e430000-7e448000	Deferred        libice.so.6
ELF	7e448000-7e451000	Deferred        libsm.so.6
ELF	7e454000-7e45d000	Deferred        librt.so.1
ELF	7e461000-7e4fd000	Deferred        winex11<elf>
  \-PE	7e470000-7e4fd000	\               winex11
ELF	7e55b000-7e582000	Deferred        libexpat.so.1
ELF	7e582000-7e5af000	Deferred        libfontconfig.so.1
ELF	7e5af000-7e5b3000	Deferred        libxau.so.6
ELF	7e5bf000-7e5d5000	Deferred        libz.so.1
ELF	7e5d5000-7e64c000	Deferred        libfreetype.so.6
ELF	7e64c000-7e651000	Deferred        libuuid.so.1
ELF	7e65c000-7e6f8000	Deferred        winmm<elf>
  \-PE	7e670000-7e6f8000	\               winmm
ELF	7e6f8000-7e7df000	Deferred        oleaut32<elf>
  \-PE	7e710000-7e7df000	\               oleaut32
ELF	7e7df000-7e84c000	Deferred        rpcrt4<elf>
  \-PE	7e7f0000-7e84c000	\               rpcrt4
ELF	7e84c000-7e947000	Deferred        ole32<elf>
  \-PE	7e860000-7e947000	\               ole32
ELF	7e947000-7ea10000	Deferred        comctl32<elf>
  \-PE	7e950000-7ea10000	\               comctl32
ELF	7ea10000-7ea6e000	Deferred        shlwapi<elf>
  \-PE	7ea20000-7ea6e000	\               shlwapi
ELF	7ea6e000-7ebfb000	Deferred        shell32<elf>
  \-PE	7ea80000-7ebfb000	\               shell32
ELF	7ebfb000-7ed47000	Export          user32<elf>
  \-PE	7ec10000-7ed47000	\               user32
ELF	7ed47000-7ed9d000	Deferred        advapi32<elf>
  \-PE	7ed50000-7ed9d000	\               advapi32
ELF	7ed9d000-7ee3f000	Deferred        gdi32<elf>
  \-PE	7edb0000-7ee3f000	\               gdi32
ELF	7efa5000-7efb1000	Deferred        libnss_files.so.2
ELF	7efb1000-7efca000	Deferred        libnsl.so.1
ELF	7efca000-7eff0000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c91000-b7c9a000	Deferred        libnss_compat.so.2
ELF	b7c9b000-b7c9f000	Deferred        libdl.so.2
ELF	b7c9f000-b7e02000	Deferred        libc.so.6
ELF	b7e03000-b7e1c000	Deferred        libpthread.so.0
ELF	b7e2c000-b7f68000	Deferred        libwine.so.1
ELF	b7f6a000-b7f88000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\sammy\Tmp\Movesky\ECMS.exe
	00000022    0
	00000021    0
	00000020    0
	0000001f    0
	0000001e    0
	0000001c    0
	0000001b    0
	0000001a    0
	00000009    0 <==
0000000e 
	0000001d    0
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
=>0 0x019b883e in xul (+0xbc883e) (0x0032de6c)
  1 0x019b8eeb in xul (+0xbc8eeb) (0x0032deac)
  2 0x01887330 in xul (+0xa97330) (0x0032dedc)
  3 0x018877ad in xul (+0xa977ad) (0x0032defc)
  4 0x01089098 in xul (+0x299098) (0x0032df2c)
  5 0x01089217 in xul (+0x299217) (0x0032df7c)
  6 0x01089247 in xul (+0x299247) (0x0032df9c)
  7 0x01b4ca7a in xul (+0xd5ca7a) (0x0032dfbc)
  8 0x0105c7cd in xul (+0x26c7cd) (0x0032e00c)
  9 0x0104f984 in xul (+0x25f984) (0x0032e2cc)
  10 0x01063f2e in xul (+0x273f2e) (0x0032e33c)
  11 0x010853c0 in xul (+0x2953c0) (0x0032e4fc)
  12 0x01063f2e in xul (+0x273f2e) (0x0032e56c)
  13 0x0107ce00 in xul (+0x28ce00) (0x0032e6bc)
  14 0x0107d00c in xul (+0x28d00c) (0x0032e78c)
  15 0x0107d7f2 in xul (+0x28d7f2) (0x0032e89c)
  16 0x01063f2e in xul (+0x273f2e) (0x0032e90c)
  17 0x010cb37e in xul (+0x2db37e) (0x0032ea6c)
  18 0x01045614 in xul (+0x255614) (0x0032ec0c)
  19 0x010457d6 in xul (+0x2557d6) (0x0032ec5c)
  20 0x01040f1a in xul (+0x250f1a) (0x0032eccc)
  21 0x01045159 in xul (+0x255159) (0x0032ed0c)
  22 0x0196559f in xul (+0xb7559f) (0x0032ed8c)
  23 0x019200d7 in xul (+0xb300d7) (0x0032edbc)
  24 0x01965349 in xul (+0xb75349) (0x0032edfc)
  25 0x01972e9f in xul (+0xb82e9f) (0x0032ee1c)
  26 0x01972e6b in xul (+0xb82e6b) (0x0032ee3c)
  27 0x01969d64 in xul (+0xb79d64) (0x0032ee5c)
  28 0x0196559f in xul (+0xb7559f) (0x0032eedc)
  29 0x019200d7 in xul (+0xb300d7) (0x0032ef0c)
  30 0x01965349 in xul (+0xb75349) (0x0032ef4c)
  31 0x01972e9f in xul (+0xb82e9f) (0x0032ef6c)
  32 0x01972e6b in xul (+0xb82e6b) (0x0032ef8c)
  33 0x01969d64 in xul (+0xb79d64) (0x0032efac)
  34 0x0196559f in xul (+0xb7559f) (0x0032f02c)
  35 0x019200d7 in xul (+0xb300d7) (0x0032f05c)
  36 0x01965349 in xul (+0xb75349) (0x0032f09c)
  37 0x01972e9f in xul (+0xb82e9f) (0x0032f0b4)
  38 0x01972e6b in xul (+0xb82e6b) (0x0032f0d4)
  39 0x01969d64 in xul (+0xb79d64) (0x0032f0f4)
  40 0x0196559f in xul (+0xb7559f) (0x0032f174)
  41 0x01920004 in xul (+0xb30004) (0x0032f1a4)
  42 0x018c0e16 in xul (+0xad0e16) (0x0032f1d4)
  43 0x0189b53e in xul (+0xaab53e) (0x0032f1f4)
  44 0x7ecc778a WINPROC_wrapper+0x1a() in user32 (0x0032f224)
  45 0x7ecc7bda WINPROC_wrapper+0x46a() in user32 (0x0032f264)
  46 0x7eccbc99 in user32 (+0xbbc99) (0x0032f734)
  47 0x7ecccd64 CallWindowProcA+0xc4() in user32 (0x0032f774)
  48 0x5f406aae in mfc42 (+0x6aae) (0x0032f7e8)
  49 0x7ecc778a WINPROC_wrapper+0x1a() in user32 (0x0032f818)
  50 0x7ecc7bda WINPROC_wrapper+0x46a() in user32 (0x0032f858)
  51 0x7ecccf07 in user32 (+0xbcf07) (0x0032f898)
  52 0x7ec8c0b6 DispatchMessageA+0x96() in user32 (0x0032f8d8)
  53 0x5f4011ce in mfc42 (+0x11ce) (0x00542f2c)
  54 0x0000c05c (0x0001008c)
  55 0x00000000 (0x00000000)
sammy@sammy-desktop:~/Tmp/Movesky$ [/COLOR]
[/HTML]
Please advise ...

---

