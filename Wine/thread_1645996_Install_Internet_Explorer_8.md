---
title: "Install Internet Explorer 8"
date: 2010-12-15
forum: Wine
---

### Post by kreoton on 2010-12-15
Hi, I'm trying to install IE8 on wine via tutorial ([http://wine-reviews.net/wine-reviews/applications/how-to-install-internet-explorer-8-ie-8-on-linux.html](http://wine-reviews.net/wine-reviews/applications/how-to-install-internet-explorer-8-ie-8-on-linux.html)) i found on web. I got error witch is registered as bug ([http://bugs.winehq.org/show_bug.cgi?id=18149](http://bugs.winehq.org/show_bug.cgi?id=18149)) and is fixed in 1.3.1 version, my wine version is 1.3.9. Before this version I tried using last stable version, same error.

Using Ubuntu 10.10

Sorry for my English :)

---

### Post by cbilljones on 2010-12-15
> **kreoton said:**
> Hi, I'm trying to install IE8 on wine via tutorial ([http://wine-reviews.net/wine-reviews/applications/how-to-install-internet-explorer-8-ie-8-on-linux.html](http://wine-reviews.net/wine-reviews/applications/how-to-install-internet-explorer-8-ie-8-on-linux.html)) i found on web. I got error witch is registered as bug ([http://bugs.winehq.org/show_bug.cgi?id=18149](http://bugs.winehq.org/show_bug.cgi?id=18149)) and is fixed in 1.3.1 version, my wine version is 1.3.9. Before this version I tried using last stable version, same error.

Using Ubuntu 10.10

Sorry for my English :)

can you pastebin the error your getting; and you did install all the dependencies with winetricks, right?

corefonts
gdiplus
msls31
msxml3
riched20
riched32
tahoma

---

### Post by kreoton on 2010-12-17
> **cbilljones said:**
> can you pastebin the error your getting; and you did install all the dependencies with winetricks, right?

corefonts
gdiplus
msls31
msxml3
riched20
riched32
tahoma

Yes. All steps was done before starting install. I use 64bit Ubuntu maybe here is problem?

My log:
```
fixme:ntdll:NtConnectPort (0x5b2a1170,L"\\ThemeApiPort",0x33f42c,(nil),(nil),(nil),0x33f43c,0x33f438),stub!
fixme:ntdll:NtConnectPort (0x5b2a1170,L"\\ThemeApiPort",0x33eff4,(nil),(nil),(nil),0x33f004,0x33f000),stub!
fixme:ntdll:NtConnectPort (0x5b2a1170,L"\\ThemeApiPort",0x33fb5c,(nil),(nil),(nil),0x33fb6c,0x33fb68),stub!
fixme:ntdll:NtConnectPort (0x5b2a1170,L"\\ThemeApiPort",0x32fbbc,(nil),(nil),(nil),0x32fbcc,0x32fbc8),stub!
fixme:clusapi:GetNodeClusterState ((null),0x32eba4) stub!
fixme:advapi:DecryptFileA "y:\\b0d3cf268fde7ef50e\\" 00000000
fixme:ntdll:NtConnectPort (0x5b2a1170,L"\\ThemeApiPort",0x33fbbc,(nil),(nil),(nil),0x33fbcc,0x33fbc8),stub!
fixme:advapi:RegisterTraceGuidsW (0x6cd15f38, 0x6cd20180, {e2821408-c59d-418f-ad3f-aa4e792aeb79}, 1, 0x33f870, (null), (null), 0x6cd20188,)
wine: Call from 0x7bc4a930 to unimplemented function msvcrt.dll.??_U@YAPAXI@Z, aborting
wine: Unimplemented function msvcrt.dll.??_U@YAPAXI@Z called at address 0x7bc4a930 (thread 001d), starting debugger...
Unhandled exception: unimplemented function msvcrt.dll.??_U@YAPAXI@Z called in 32-bit code (0x7bc4a930).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc4a930 ESP:0033fcc0 EBP:0033fd24 EFLAGS:00000202(   - --  I   - - - )
 EAX:0102d45e EBX:7bc9eff4 ECX:0033f9f4 EDX:00000000
 ESI:0033fccc EDI:00000000
Stack dump:
0x0033fcc0:  00000000 0012e084 00000001 80000100
0x0033fcd0:  00000001 00000000 7bc4a930 00000002
0x0033fce0:  0102d5d0 0102d45e 01016ab3 0012e080
0x0033fcf0:  003526a8 00000000 00000000 00000001
0x0033fd00:  00000001 00000000 00000000 01003af8
0x0033fd10:  d55ed500 00000000 003536b4 01001958
Backtrace:
=>0 0x7bc4a930 call_dll_entry_point+0x620() in ntdll (0x0033fd24)
  1 0x0034001e (0x0033fd58)
  2 0x01017506 in iesetup (+0x17505) (0x0033fde8)
  3 0x01011163 in iesetup (+0x11162) (0x0033fe00)
  4 0x01028a8c in iesetup (+0x28a8b) (0x0033fe90)
  5 0x7b8565ac call_process_entry+0xb() in kernel32 (0x0033fea8)
  6 0x7b85724f ExitProcess+0xc9e() in kernel32 (0x0033fee8)
  7 0x7bc72ce0 call_thread_func+0xb() in ntdll (0x0033fef8)
  8 0x7bc75850 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  9 0x7bc4a96a call_dll_entry_point+0x659() in ntdll (0x0033ffe8)
0x7bc4a930 call_dll_entry_point+0x620 in ntdll: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (84 modules)
PE	 1000000- 1118000	Export          iesetup
PE	5b270000-5b2a8000	Deferred        uxtheme
PE	6cd00000-6cd24000	Deferred        sqmapi
PE	78000000-78044000	Deferred        msvcrt
ELF	7b800000-7b980000	Export          kernel32<elf>
  \-PE	7b810000-7b980000	\               kernel32
ELF	7bc00000-7bcbb000	Export          ntdll<elf>
  \-PE	7bc10000-7bcbb000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7de5d000-7de66000	Deferred        librt.so.1
ELF	7de66000-7dea2000	Deferred        libdbus-1.so.3
ELF	7dea2000-7dea7000	Deferred        libgpg-error.so.0
ELF	7dea7000-7deb8000	Deferred        libtasn1.so.3
ELF	7deb8000-7decc000	Deferred        libresolv.so.2
ELF	7decc000-7ded0000	Deferred        libkeyutils.so.1
ELF	7ded0000-7ded8000	Deferred        libkrb5support.so.0
ELF	7ded8000-7dedc000	Deferred        libcom_err.so.2
ELF	7dedc000-7df00000	Deferred        libk5crypto.so.3
ELF	7df00000-7dfae000	Deferred        libkrb5.so.3
ELF	7dfae000-7dfbe000	Deferred        libavahi-client.so.3
ELF	7dfbe000-7dfca000	Deferred        libavahi-common.so.3
ELF	7dfca000-7e03e000	Deferred        libgcrypt.so.11
ELF	7e03e000-7e0d9000	Deferred        libgnutls.so.26
ELF	7e0d9000-7e108000	Deferred        libgssapi_krb5.so.2
ELF	7e108000-7e152000	Deferred        libcups.so.2
ELF	7e152000-7e15c000	Deferred        libxcursor.so.1
ELF	7e15c000-7e162000	Deferred        libxfixes.so.3
ELF	7e162000-7e166000	Deferred        libxcomposite.so.1
ELF	7e166000-7e16e000	Deferred        libxrandr.so.2
ELF	7e16e000-7e178000	Deferred        libxrender.so.1
ELF	7e178000-7e17e000	Deferred        libxxf86vm.so.1
ELF	7e17e000-7e182000	Deferred        libxinerama.so.1
ELF	7e182000-7e1a3000	Deferred        imm32<elf>
  \-PE	7e190000-7e1a3000	\               imm32
ELF	7e1a3000-7e1a9000	Deferred        libxdmcp.so.6
ELF	7e1a9000-7e1ad000	Deferred        libxau.so.6
ELF	7e1ad000-7e1c7000	Deferred        libxcb.so.1
ELF	7e1c7000-7e2e5000	Deferred        libx11.so.6
ELF	7e2e5000-7e2f5000	Deferred        libxext.so.6
ELF	7e2f5000-7e30e000	Deferred        libice.so.6
ELF	7e30e000-7e317000	Deferred        libsm.so.6
ELF	7e336000-7e3df000	Deferred        winex11<elf>
  \-PE	7e340000-7e3df000	\               winex11
ELF	7e401000-7e428000	Deferred        libexpat.so.1
ELF	7e428000-7e458000	Deferred        libfontconfig.so.1
ELF	7e458000-7e45d000	Deferred        libuuid.so.1
ELF	7e477000-7e48c000	Deferred        libz.so.1
ELF	7e48c000-7e503000	Deferred        libfreetype.so.6
ELF	7e522000-7e584000	Deferred        shlwapi<elf>
  \-PE	7e530000-7e584000	\               shlwapi
ELF	7e584000-7e771000	Deferred        shell32<elf>
  \-PE	7e590000-7e771000	\               shell32
ELF	7e771000-7e7a9000	Deferred        winspool<elf>
  \-PE	7e780000-7e7a9000	\               winspool
ELF	7e7a9000-7e808000	Deferred        setupapi<elf>
  \-PE	7e7b0000-7e808000	\               setupapi
ELF	7e808000-7e81e000	Deferred        psapi<elf>
  \-PE	7e810000-7e81e000	\               psapi
ELF	7e81e000-7e90a000	Deferred        oleaut32<elf>
  \-PE	7e830000-7e90a000	\               oleaut32
ELF	7e90a000-7e97d000	Deferred        rpcrt4<elf>
  \-PE	7e920000-7e97d000	\               rpcrt4
ELF	7e97d000-7ea81000	Deferred        ole32<elf>
  \-PE	7e990000-7ea81000	\               ole32
ELF	7ea81000-7eb72000	Deferred        comctl32<elf>
  \-PE	7ea90000-7eb72000	\               comctl32
ELF	7eb72000-7eca6000	Deferred        user32<elf>
  \-PE	7eb80000-7eca6000	\               user32
ELF	7eca6000-7ed32000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed32000	\               gdi32
ELF	7ed32000-7ed8d000	Deferred        advapi32<elf>
  \-PE	7ed40000-7ed8d000	\               advapi32
ELF	7ed8d000-7ed99000	Deferred        libnss_files.so.2
ELF	7ed99000-7eda4000	Deferred        libnss_nis.so.2
ELF	7eda4000-7edbb000	Deferred        libnsl.so.1
ELF	7efbb000-7efe1000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f7457000-f745b000	Deferred        libdl.so.2
ELF	f745b000-f75b6000	Deferred        libc.so.6
ELF	f75b7000-f75d0000	Deferred        libpthread.so.0
ELF	f75e6000-f75ee000	Deferred        libnss_compat.so.2
ELF	f75ef000-f772f000	Export          libwine.so.1
ELF	f7731000-f774f000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 IE8-WindowsXP-x86-ENU.exe
	0000001b    0
	00000009    0
0000000e services.exe
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000018    0
	00000017    0
	00000013    0
	00000012    0
00000019 explorer.exe
	0000001a    0
0000001c (D) Y:\b0d3cf268fde7ef50e\update\iesetup.exe
	0000001d    0 <==
Backtrace:
=>0 0x7bc4a930 call_dll_entry_point+0x620() in ntdll (0x0033fd24)
  1 0x0034001e (0x0033fd58)
  2 0x01017506 in iesetup (+0x17505) (0x0033fde8)
  3 0x01011163 in iesetup (+0x11162) (0x0033fe00)
  4 0x01028a8c in iesetup (+0x28a8b) (0x0033fe90)
  5 0x7b8565ac call_process_entry+0xb() in kernel32 (0x0033fea8)
  6 0x7b85724f ExitProcess+0xc9e() in kernel32 (0x0033fee8)
  7 0x7bc72ce0 call_thread_func+0xb() in ntdll (0x0033fef8)
  8 0x7bc75850 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  9 0x7bc4a96a call_dll_entry_point+0x659() in ntdll (0x0033ffe8)
wine: Call from 0x7bc4a930 to unimplemented function msvcrt.dll.??_U@YAPAXI@Z, aborting

```

---

