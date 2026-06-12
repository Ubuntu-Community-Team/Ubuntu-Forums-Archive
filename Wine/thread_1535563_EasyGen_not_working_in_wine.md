---
title: "EasyGen not working in wine"
date: 2010-07-21
forum: Wine
---

### Post by darkcodemonkey on 2010-07-21
Easygen is a map maker for the quake 3 engine. After reading that others could load it in wine, then after trying it, the program failed. So, I loaded it in the terminal and got this:
```

ethan@ethan-desktop:~$ cd '/home/ethan/Desktop/untitled folder' 
ethan@ethan-desktop:~/Desktop/untitled folder$ wine EasyGen.exe
wine: Call from 0x7bc486c0 to unimplemented function MFC42.DLL.6880, aborting
wine: Unimplemented function MFC42.DLL.6880 called at address 0x7bc486c0 (thread 0009), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6880 called in 32-bit code (0x7bc486c0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc486c0 ESP:0032f318 EBP:0032f37c EFLAGS:00200202(   - --  I   - - - )
 EAX:00001ae0 EBX:7bc93ff4 ECX:0032fce0 EDX:0032f3b4
 ESI:0032f324 EDI:7eb4b440
Stack dump:
0x0032f318:  7eb74ff4 0032f3b4 00000002 80000100
0x0032f328:  00000001 00000000 7bc486c0 00000002
0x0032f338:  0043ad3a 00001ae0 0000000a 000001b7
0x0032f348:  00000166 0032f3b4 00000001 0032f384
0x0032f358:  7eb4b4c2 0002004a 00000000 0032f3b4
0x0032f368:  00000002 5f40bf49 000001dc 00420ca0
Backtrace:
=>0 0x7bc486c0 in ntdll (+0x386c0) (0x0032f37c)
  1 0x0033000f (0x0032f498)
err:dbghelp:pe_load_dbg_file Couldn't find .DBG file "MFC42.dbg" ("P")
  2 0x5f40230b in mfc42 (+0x230b) (0x0032f4b8)
  3 0x5f402294 in mfc42 (+0x2294) (0x0032f518)
  4 0x5f40221f in mfc42 (+0x221f) (0x0032f534)
  5 0x5f4021d6 in mfc42 (+0x21d6) (0x0032f560)
  6 0x7eb4ef1a WINPROC_wrapper+0x1a() in user32 (0x0032f590)
  7 0x7eb4f36a WINPROC_wrapper+0x46a() in user32 (0x0032f5d0)
  8 0x7eb52195 in user32 (+0xb2195) (0x0032faa0)
  9 0x7eb5472e in user32 (+0xb472e) (0x0032fae0)
  10 0x7eb13771 in user32 (+0x73771) (0x0032fb40)
  11 0x7eb18a15 in user32 (+0x78a15) (0x0032fba0)
  12 0x7eb18f2c SendMessageW+0x4c() in user32 (0x0032fbe0)
  13 0x7eb2538e RedrawWindow+0x20e() in user32 (0x0032fc40)
  14 0x7eb268f5 UpdateWindow+0x35() in user32 (0x0032fc60)
  15 0x5f41a72b in mfc42 (+0x1a72b) (0x0043e344)
  16 0x00000000 (0x00000000)
0x7bc486c0: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (89 modules)
PE	  400000-  51a000	Deferred        easygen
PE	10000000-100f8000	Deferred        btnexgenipl32
PE	5f400000-5f4ed000	Export          mfc42
ELF	7b800000-7b948000	Deferred        kernel32<elf>
  \-PE	7b820000-7b948000	\               kernel32
ELF	7bc00000-7bcb0000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb0000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c5e2000-7c5f7000	Deferred        midimap<elf>
  \-PE	7c5f0000-7c5f7000	\               midimap
ELF	7c5f7000-7c61d000	Deferred        msacm32<elf>
  \-PE	7c600000-7c61d000	\               msacm32
ELF	7c61d000-7c635000	Deferred        msacm32<elf>
  \-PE	7c620000-7c635000	\               msacm32
ELF	7c635000-7c694000	Deferred        libpulse.so.0
ELF	7c694000-7c75c000	Deferred        libasound.so.2
ELF	7c75c000-7c7c8000	Deferred        rpcrt4<elf>
  \-PE	7c770000-7c7c8000	\               rpcrt4
ELF	7c7c8000-7c8c3000	Deferred        ole32<elf>
  \-PE	7c7e0000-7c8c3000	\               ole32
ELF	7cfc3000-7dedb000	Deferred        libglcore.so.1
ELF	7e017000-7e01d000	Deferred        libattr.so.1
ELF	7e01d000-7e024000	Deferred        libgdbm.so.3
ELF	7e024000-7e029000	Deferred        libcap.so.2
ELF	7e03d000-7e044000	Deferred        libasound_module_pcm_pulse.so
ELF	7e044000-7e07b000	Deferred        winealsa<elf>
  \-PE	7e050000-7e07b000	\               winealsa
ELF	7e118000-7e14b000	Deferred        uxtheme<elf>
  \-PE	7e120000-7e14b000	\               uxtheme
ELF	7e1ca000-7e1d3000	Deferred        libxcursor.so.1
ELF	7e1d3000-7e1d8000	Deferred        libxfixes.so.3
ELF	7e1d8000-7e1dc000	Deferred        libxcomposite.so.1
ELF	7e1dc000-7e1e4000	Deferred        libxrandr.so.2
ELF	7e1e4000-7e1ee000	Deferred        libxrender.so.1
ELF	7e1ee000-7e1f4000	Deferred        libxxf86vm.so.1
ELF	7e1f4000-7e1f7000	Deferred        libxinerama.so.1
ELF	7e1fa000-7e203000	Deferred        librt.so.1
ELF	7e20b000-7e22c000	Deferred        imm32<elf>
  \-PE	7e210000-7e22c000	\               imm32
ELF	7e22c000-7e2c8000	Deferred        winex11<elf>
  \-PE	7e240000-7e2c8000	\               winex11
ELF	7e337000-7e35e000	Deferred        libexpat.so.1
ELF	7e35e000-7e38b000	Deferred        libfontconfig.so.1
ELF	7e39f000-7e3b5000	Deferred        libz.so.1
ELF	7e3b5000-7e42c000	Deferred        libfreetype.so.6
ELF	7e42c000-7e4c3000	Deferred        winmm<elf>
  \-PE	7e440000-7e4c3000	\               winmm
ELF	7e4c3000-7e4e2000	Deferred        msvcirt<elf>
  \-PE	7e4d0000-7e4e2000	\               msvcirt
ELF	7e4e2000-7e5aa000	Deferred        comctl32<elf>
  \-PE	7e4f0000-7e5aa000	\               comctl32
ELF	7e5aa000-7e608000	Deferred        shlwapi<elf>
  \-PE	7e5c0000-7e608000	\               shlwapi
ELF	7e608000-7e792000	Deferred        shell32<elf>
  \-PE	7e620000-7e792000	\               shell32
ELF	7e792000-7e800000	Deferred        msvcrt<elf>
  \-PE	7e7a0000-7e800000	\               msvcrt
ELF	7e8ef000-7e961000	Deferred        libglu.so.1
ELF	7e975000-7e98c000	Deferred        glu32<elf>
  \-PE	7e980000-7e98c000	\               glu32
ELF	7e98c000-7e9e2000	Deferred        advapi32<elf>
  \-PE	7e9a0000-7e9e2000	\               advapi32
ELF	7e9e2000-7ea83000	Deferred        gdi32<elf>
  \-PE	7e9f0000-7ea83000	\               gdi32
ELF	7ea83000-7ebce000	Export          user32<elf>
  \-PE	7eaa0000-7ebce000	\               user32
ELF	7ebce000-7ebd3000	Deferred        libxdmcp.so.6
ELF	7ebd3000-7ebed000	Deferred        libxcb.so.1
ELF	7ebed000-7ebf1000	Deferred        libxau.so.6
ELF	7ebf1000-7ecab000	Deferred        libgl.so.1
ELF	7ecab000-7ed9a000	Deferred        libx11.so.6
ELF	7ed9a000-7edaa000	Deferred        libxext.so.6
ELF	7edaa000-7edc2000	Deferred        libice.so.6
ELF	7edc2000-7edcb000	Deferred        libsm.so.6
ELF	7edce000-7eddd000	Deferred        libgcc_s.so.1
ELF	7eddf000-7ee77000	Deferred        opengl32<elf>
  \-PE	7ee00000-7ee77000	\               opengl32
ELF	7efa1000-7efad000	Deferred        libnss_files.so.2
ELF	7efad000-7efc6000	Deferred        libnsl.so.1
ELF	7efc6000-7efec000	Deferred        libm.so.6
ELF	7efec000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7ce1000-b7ce6000	Deferred        libuuid.so.1
ELF	b7ce7000-b7ceb000	Deferred        libdl.so.2
ELF	b7ceb000-b7e4e000	Deferred        libc.so.6
ELF	b7e4f000-b7e68000	Deferred        libpthread.so.0
ELF	b7e69000-b7e6b000	Deferred        libnvidia-tls.so.1
ELF	b7e7c000-b7fb7000	Deferred        libwine.so.1
ELF	b7fb9000-b7fd7000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) H:\Desktop\untitled folder\EasyGen.exe
	00000009    0 <==
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000017 
	00000018    0
Backtrace:
=>0 0x7bc486c0 in ntdll (+0x386c0) (0x0032f37c)
  1 0x0033000f (0x0032f498)
  2 0x5f40230b in mfc42 (+0x230b) (0x0032f4b8)
  3 0x5f402294 in mfc42 (+0x2294) (0x0032f518)
  4 0x5f40221f in mfc42 (+0x221f) (0x0032f534)
  5 0x5f4021d6 in mfc42 (+0x21d6) (0x0032f560)
  6 0x7eb4ef1a WINPROC_wrapper+0x1a() in user32 (0x0032f590)
  7 0x7eb4f36a WINPROC_wrapper+0x46a() in user32 (0x0032f5d0)
  8 0x7eb52195 in user32 (+0xb2195) (0x0032faa0)
  9 0x7eb5472e in user32 (+0xb472e) (0x0032fae0)
  10 0x7eb13771 in user32 (+0x73771) (0x0032fb40)
  11 0x7eb18a15 in user32 (+0x78a15) (0x0032fba0)
  12 0x7eb18f2c SendMessageW+0x4c() in user32 (0x0032fbe0)
  13 0x7eb2538e RedrawWindow+0x20e() in user32 (0x0032fc40)
  14 0x7eb268f5 UpdateWindow+0x35() in user32 (0x0032fc60)
  15 0x5f41a72b in mfc42 (+0x1a72b) (0x0043e344)
  16 0x00000000 (0x00000000)
wine: Call from 0x7bc486c0 to unimplemented function MFC42.DLL.6880, aborting
wine: Call from 0x7bc486c0 to unimplemented function MFC42.DLL.6880, aborting
ethan@ethan-desktop:~/Desktop/untitled folder$ 

```

I don't think I'm missing any files. If anyone could help me, it would be most appreciated. Thanks in advanced.

I'm using wine 1.1.22 and Ubuntu Jaunty 9.04

---

### Post by asdfoo on 2010-07-22
> **darkcodemonkey said:**
> Easygen is a map maker for the quake 3 engine. After reading that others could load it in wine, then after trying it, the program failed. So, I loaded it in the terminal and got this:
```

ethan@ethan-desktop:~$ cd '/home/ethan/Desktop/untitled folder' 
ethan@ethan-desktop:~/Desktop/untitled folder$ wine EasyGen.exe
wine: Call from 0x7bc486c0 to unimplemented function MFC42.DLL.6880, aborting
wine: Unimplemented function MFC42.DLL.6880 called at address 0x7bc486c0 (thread 0009), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6880 called in 32-bit code (0x7bc486c0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc486c0 ESP:0032f318 EBP:0032f37c EFLAGS:00200202(   - --  I   - - - )
 EAX:00001ae0 EBX:7bc93ff4 ECX:0032fce0 EDX:0032f3b4
 ESI:0032f324 EDI:7eb4b440
Stack dump:
0x0032f318:  7eb74ff4 0032f3b4 00000002 80000100
0x0032f328:  00000001 00000000 7bc486c0 00000002
0x0032f338:  0043ad3a 00001ae0 0000000a 000001b7
0x0032f348:  00000166 0032f3b4 00000001 0032f384
0x0032f358:  7eb4b4c2 0002004a 00000000 0032f3b4
0x0032f368:  00000002 5f40bf49 000001dc 00420ca0
Backtrace:
=>0 0x7bc486c0 in ntdll (+0x386c0) (0x0032f37c)
  1 0x0033000f (0x0032f498)
err:dbghelp:pe_load_dbg_file Couldn't find .DBG file "MFC42.dbg" ("P")
  2 0x5f40230b in mfc42 (+0x230b) (0x0032f4b8)
  3 0x5f402294 in mfc42 (+0x2294) (0x0032f518)
  4 0x5f40221f in mfc42 (+0x221f) (0x0032f534)
  5 0x5f4021d6 in mfc42 (+0x21d6) (0x0032f560)
  6 0x7eb4ef1a WINPROC_wrapper+0x1a() in user32 (0x0032f590)
  7 0x7eb4f36a WINPROC_wrapper+0x46a() in user32 (0x0032f5d0)
  8 0x7eb52195 in user32 (+0xb2195) (0x0032faa0)
  9 0x7eb5472e in user32 (+0xb472e) (0x0032fae0)
  10 0x7eb13771 in user32 (+0x73771) (0x0032fb40)
  11 0x7eb18a15 in user32 (+0x78a15) (0x0032fba0)
  12 0x7eb18f2c SendMessageW+0x4c() in user32 (0x0032fbe0)
  13 0x7eb2538e RedrawWindow+0x20e() in user32 (0x0032fc40)
  14 0x7eb268f5 UpdateWindow+0x35() in user32 (0x0032fc60)
  15 0x5f41a72b in mfc42 (+0x1a72b) (0x0043e344)
  16 0x00000000 (0x00000000)
0x7bc486c0: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (89 modules)
PE	  400000-  51a000	Deferred        easygen
PE	10000000-100f8000	Deferred        btnexgenipl32
PE	5f400000-5f4ed000	Export          mfc42
ELF	7b800000-7b948000	Deferred        kernel32<elf>
  \-PE	7b820000-7b948000	\               kernel32
ELF	7bc00000-7bcb0000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb0000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c5e2000-7c5f7000	Deferred        midimap<elf>
  \-PE	7c5f0000-7c5f7000	\               midimap
ELF	7c5f7000-7c61d000	Deferred        msacm32<elf>
  \-PE	7c600000-7c61d000	\               msacm32
ELF	7c61d000-7c635000	Deferred        msacm32<elf>
  \-PE	7c620000-7c635000	\               msacm32
ELF	7c635000-7c694000	Deferred        libpulse.so.0
ELF	7c694000-7c75c000	Deferred        libasound.so.2
ELF	7c75c000-7c7c8000	Deferred        rpcrt4<elf>
  \-PE	7c770000-7c7c8000	\               rpcrt4
ELF	7c7c8000-7c8c3000	Deferred        ole32<elf>
  \-PE	7c7e0000-7c8c3000	\               ole32
ELF	7cfc3000-7dedb000	Deferred        libglcore.so.1
ELF	7e017000-7e01d000	Deferred        libattr.so.1
ELF	7e01d000-7e024000	Deferred        libgdbm.so.3
ELF	7e024000-7e029000	Deferred        libcap.so.2
ELF	7e03d000-7e044000	Deferred        libasound_module_pcm_pulse.so
ELF	7e044000-7e07b000	Deferred        winealsa<elf>
  \-PE	7e050000-7e07b000	\               winealsa
ELF	7e118000-7e14b000	Deferred        uxtheme<elf>
  \-PE	7e120000-7e14b000	\               uxtheme
ELF	7e1ca000-7e1d3000	Deferred        libxcursor.so.1
ELF	7e1d3000-7e1d8000	Deferred        libxfixes.so.3
ELF	7e1d8000-7e1dc000	Deferred        libxcomposite.so.1
ELF	7e1dc000-7e1e4000	Deferred        libxrandr.so.2
ELF	7e1e4000-7e1ee000	Deferred        libxrender.so.1
ELF	7e1ee000-7e1f4000	Deferred        libxxf86vm.so.1
ELF	7e1f4000-7e1f7000	Deferred        libxinerama.so.1
ELF	7e1fa000-7e203000	Deferred        librt.so.1
ELF	7e20b000-7e22c000	Deferred        imm32<elf>
  \-PE	7e210000-7e22c000	\               imm32
ELF	7e22c000-7e2c8000	Deferred        winex11<elf>
  \-PE	7e240000-7e2c8000	\               winex11
ELF	7e337000-7e35e000	Deferred        libexpat.so.1
ELF	7e35e000-7e38b000	Deferred        libfontconfig.so.1
ELF	7e39f000-7e3b5000	Deferred        libz.so.1
ELF	7e3b5000-7e42c000	Deferred        libfreetype.so.6
ELF	7e42c000-7e4c3000	Deferred        winmm<elf>
  \-PE	7e440000-7e4c3000	\               winmm
ELF	7e4c3000-7e4e2000	Deferred        msvcirt<elf>
  \-PE	7e4d0000-7e4e2000	\               msvcirt
ELF	7e4e2000-7e5aa000	Deferred        comctl32<elf>
  \-PE	7e4f0000-7e5aa000	\               comctl32
ELF	7e5aa000-7e608000	Deferred        shlwapi<elf>
  \-PE	7e5c0000-7e608000	\               shlwapi
ELF	7e608000-7e792000	Deferred        shell32<elf>
  \-PE	7e620000-7e792000	\               shell32
ELF	7e792000-7e800000	Deferred        msvcrt<elf>
  \-PE	7e7a0000-7e800000	\               msvcrt
ELF	7e8ef000-7e961000	Deferred        libglu.so.1
ELF	7e975000-7e98c000	Deferred        glu32<elf>
  \-PE	7e980000-7e98c000	\               glu32
ELF	7e98c000-7e9e2000	Deferred        advapi32<elf>
  \-PE	7e9a0000-7e9e2000	\               advapi32
ELF	7e9e2000-7ea83000	Deferred        gdi32<elf>
  \-PE	7e9f0000-7ea83000	\               gdi32
ELF	7ea83000-7ebce000	Export          user32<elf>
  \-PE	7eaa0000-7ebce000	\               user32
ELF	7ebce000-7ebd3000	Deferred        libxdmcp.so.6
ELF	7ebd3000-7ebed000	Deferred        libxcb.so.1
ELF	7ebed000-7ebf1000	Deferred        libxau.so.6
ELF	7ebf1000-7ecab000	Deferred        libgl.so.1
ELF	7ecab000-7ed9a000	Deferred        libx11.so.6
ELF	7ed9a000-7edaa000	Deferred        libxext.so.6
ELF	7edaa000-7edc2000	Deferred        libice.so.6
ELF	7edc2000-7edcb000	Deferred        libsm.so.6
ELF	7edce000-7eddd000	Deferred        libgcc_s.so.1
ELF	7eddf000-7ee77000	Deferred        opengl32<elf>
  \-PE	7ee00000-7ee77000	\               opengl32
ELF	7efa1000-7efad000	Deferred        libnss_files.so.2
ELF	7efad000-7efc6000	Deferred        libnsl.so.1
ELF	7efc6000-7efec000	Deferred        libm.so.6
ELF	7efec000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7ce1000-b7ce6000	Deferred        libuuid.so.1
ELF	b7ce7000-b7ceb000	Deferred        libdl.so.2
ELF	b7ceb000-b7e4e000	Deferred        libc.so.6
ELF	b7e4f000-b7e68000	Deferred        libpthread.so.0
ELF	b7e69000-b7e6b000	Deferred        libnvidia-tls.so.1
ELF	b7e7c000-b7fb7000	Deferred        libwine.so.1
ELF	b7fb9000-b7fd7000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) H:\Desktop\untitled folder\EasyGen.exe
	00000009    0 <==
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000017 
	00000018    0
Backtrace:
=>0 0x7bc486c0 in ntdll (+0x386c0) (0x0032f37c)
  1 0x0033000f (0x0032f498)
  2 0x5f40230b in mfc42 (+0x230b) (0x0032f4b8)
  3 0x5f402294 in mfc42 (+0x2294) (0x0032f518)
  4 0x5f40221f in mfc42 (+0x221f) (0x0032f534)
  5 0x5f4021d6 in mfc42 (+0x21d6) (0x0032f560)
  6 0x7eb4ef1a WINPROC_wrapper+0x1a() in user32 (0x0032f590)
  7 0x7eb4f36a WINPROC_wrapper+0x46a() in user32 (0x0032f5d0)
  8 0x7eb52195 in user32 (+0xb2195) (0x0032faa0)
  9 0x7eb5472e in user32 (+0xb472e) (0x0032fae0)
  10 0x7eb13771 in user32 (+0x73771) (0x0032fb40)
  11 0x7eb18a15 in user32 (+0x78a15) (0x0032fba0)
  12 0x7eb18f2c SendMessageW+0x4c() in user32 (0x0032fbe0)
  13 0x7eb2538e RedrawWindow+0x20e() in user32 (0x0032fc40)
  14 0x7eb268f5 UpdateWindow+0x35() in user32 (0x0032fc60)
  15 0x5f41a72b in mfc42 (+0x1a72b) (0x0043e344)
  16 0x00000000 (0x00000000)
wine: Call from 0x7bc486c0 to unimplemented function MFC42.DLL.6880, aborting
wine: Call from 0x7bc486c0 to unimplemented function MFC42.DLL.6880, aborting
ethan@ethan-desktop:~/Desktop/untitled folder$ 

```

I don't think I'm missing any files. If anyone could help me, it would be most appreciated. Thanks in advanced.

I'm using wine 1.1.22 and Ubuntu Jaunty 9.04

looks like you've got a strange version of mfc42.dll, I suggest you delete it and use winetricks to install a valid copy using the following two commands:

wget kegel.com/wine/winetricks
sh winetricks mfc42

---

### Post by darkcodemonkey on 2010-07-23
It work now!

Thank you very much.:D

---

