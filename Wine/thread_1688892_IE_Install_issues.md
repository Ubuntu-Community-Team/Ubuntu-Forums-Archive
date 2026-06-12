---
title: "IE Install issues"
date: 2011-02-15
forum: Wine
---

### Post by jchase45 on 2011-02-15
I'm trying to install IE with wine . But everytime I try with wine or even winetricks it gives me this error 


[PHP]

jared@jared-EP45-DS3L:~$ winetricks
Executing /usr/bin/cabextract -q --directory=/home/jared/.wine/dosdevices/c:/winetrickstmp /home/jared/.cache/winetricks/msls31/InstMsiA.exe
Executing cp -f /home/jared/.wine/dosdevices/c:/winetrickstmp/msls31.dll /home/jared/.wine/dosdevices/c:/windows/system32
Using native,builtin override for following DLLs: iexplore.exe itircl itss jscript msctf mshtml shdoclc shdocvw shlwapi urlmon xmllite
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Using builtin override for following DLLs: updspapi
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Executing cp -f /home/jared/.cache/winetricks/ie8/winetest.cat /home/jared/.wine/dosdevices/c:/windows/system32/catroot/{f750e6c3-38ee-11d1-85e5-00c04fc295ee}/oem0.cat
mv: cannot stat `/home/jared/.wine/dosdevices/z:': No such file or directory
fixme:clusapi:GetNodeClusterState ((null),0x32eba4) stub!
fixme:advapi:DecryptFileA "s:\\cb9ccc6cf278f4552bb9453f\\" 00000000
fixme:advapi:RegisterTraceGuidsW (0x6cd15f38, 0x6cd20180, {e2821408-c59d-418f-ad3f-aa4e792aeb79}, 1, 0x33f870, (null), (null), 0x6cd20188,)
fixme:ole:NdrCorrelationInitialize (0x33f484, 0x33f084, 1024, 0x0): stub
fixme:ole:NdrCorrelationInitialize (0x33f4c4, 0x33f0c4, 1024, 0x0): stub
fixme:ole:NdrCorrelationInitialize (0x33f48c, 0x33f08c, 1024, 0x0): stub
fixme:ole:NdrCorrelationInitialize (0x33f498, 0x33f098, 1024, 0x0): stub
fixme:ole:NdrCorrelationInitialize (0x33f460, 0x33f060, 1024, 0x0): stub
fixme:ole:NdrCorrelationInitialize (0x33f498, 0x33f098, 1024, 0x0): stub
fixme:ole:NdrCorrelationInitialize (0x33f460, 0x33f060, 1024, 0x0): stub
wine: Unhandled page fault on write access to 0x00000024 at address 0x7b869e51 (thread 0065), starting debugger...
Unhandled exception: page fault on write access to 0x00000024 in 32-bit code (0x7b869e51).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b869e51 ESP:0033fb64 EBP:0033fbac EFLAGS:00010206(  R- --  I   - -P- )
 EAX:ffffffff EBX:7dd38ff4 ECX:00000000 EDX:00000024
 ESI:00000000 EDI:0000003c
Stack dump:
0x0033fb64:  76323dea 00000024 00000001 7dd2fdbe
0x0033fb74:  00000000 ffffffff 0033fc0c 7dd316a0
0x0033fb84:  00136c50 0013b1d0 00000000 00000000
0x0033fb94:  00000000 00000000 7b888ff4 7dd38ff4
0x0033fba4:  00000000 00136c50 0033fc0c 7dd305a0
0x0033fbb4:  00136c50 001334f8 7dd30b80 0033fd3c
Backtrace:
=>0 0x7b869e51 InterlockedDecrement+0x9() in kernel32 (0x0033fbac)
  1 0x7dd305a0 in wintrust (+0x2059f) (0x0033fc0c)
  2 0x7dd32a31 WinVerifyTrust+0x1080() in wintrust (0x0033fcac)
  3 0x01013954 in iesetup (+0x13953) (0x0033fd50)
  4 0x0101732a in iesetup (+0x17329) (0x0033fde8)
  5 0x01011163 in iesetup (+0x11162) (0x0033fe00)
  6 0x01028a8c in iesetup (+0x28a8b) (0x0033fe90)
  7 0x7b8583cc call_process_entry+0xb() in kernel32 (0x0033fea8)
  8 0x7b85906f ExitProcess+0xc9e() in kernel32 (0x0033fee8)
  9 0x7bc71b28 call_thread_func+0xb() in ntdll (0x0033fef8)
  10 0x7bc74610 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  11 0x7bc49e4a call_dll_entry_point+0x629() in ntdll (0x0033ffe8)
0x7b869e51 InterlockedDecrement+0x9 in kernel32: lock xaddl	%eax,0x0(%edx)
Modules:
Module	Address			Debug info	Name (95 modules)
PE	 1000000- 1118000	Export          iesetup
PE	6cd00000-6cd24000	Deferred        sqmapi
PE	762c0000-76348000	Deferred        crypt32
PE	77430000-77440000	Deferred        msasn1
ELF	7b800000-7b98f000	Dwarf           kernel32<elf>
  \-PE	7b810000-7b98f000	\               kernel32
ELF	7bc00000-7bcbb000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcbb000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7dcb3000-7dcf1000	Deferred        rsaenh<elf>
  \-PE	7dcc0000-7dcf1000	\               rsaenh
ELF	7dcf1000-7dd0a000	Deferred        imagehlp<elf>
  \-PE	7dd00000-7dd0a000	\               imagehlp
ELF	7dd0a000-7dd3c000	Dwarf           wintrust<elf>
  \-PE	7dd10000-7dd3c000	\               wintrust
ELF	7dd8e000-7dd97000	Deferred        librt.so.1
ELF	7dd97000-7ddd3000	Deferred        libdbus-1.so.3
ELF	7ddd3000-7ddd8000	Deferred        libgpg-error.so.0
ELF	7ddd8000-7dde9000	Deferred        libtasn1.so.3
ELF	7dde9000-7ddfd000	Deferred        libresolv.so.2
ELF	7ddfd000-7de01000	Deferred        libkeyutils.so.1
ELF	7de01000-7de09000	Deferred        libkrb5support.so.0
ELF	7de09000-7de0d000	Deferred        libcom_err.so.2
ELF	7de0d000-7de31000	Deferred        libk5crypto.so.3
ELF	7de31000-7dee0000	Deferred        libkrb5.so.3
ELF	7dee0000-7def0000	Deferred        libavahi-client.so.3
ELF	7def0000-7defc000	Deferred        libavahi-common.so.3
ELF	7defc000-7df70000	Deferred        libgcrypt.so.11
ELF	7df70000-7e00b000	Deferred        libgnutls.so.26
ELF	7e00b000-7e03a000	Deferred        libgssapi_krb5.so.2
ELF	7e03a000-7e084000	Deferred        libcups.so.2
ELF	7e084000-7e0b8000	Deferred        uxtheme<elf>
  \-PE	7e090000-7e0b8000	\               uxtheme
ELF	7e0b8000-7e0c2000	Deferred        libxcursor.so.1
ELF	7e0c2000-7e0c8000	Deferred        libxfixes.so.3
ELF	7e0c8000-7e0cc000	Deferred        libxcomposite.so.1
ELF	7e0cc000-7e0d4000	Deferred        libxrandr.so.2
ELF	7e0d4000-7e0de000	Deferred        libxrender.so.1
ELF	7e0de000-7e0e4000	Deferred        libxxf86vm.so.1
ELF	7e0e4000-7e0e8000	Deferred        libxinerama.so.1
ELF	7e0e8000-7e109000	Deferred        imm32<elf>
  \-PE	7e0f0000-7e109000	\               imm32
ELF	7e109000-7e10f000	Deferred        libxdmcp.so.6
ELF	7e10f000-7e113000	Deferred        libxau.so.6
ELF	7e113000-7e12d000	Deferred        libxcb.so.1
ELF	7e12d000-7e24a000	Deferred        libx11.so.6
ELF	7e24a000-7e25a000	Deferred        libxext.so.6
ELF	7e25a000-7e273000	Deferred        libice.so.6
ELF	7e273000-7e27c000	Deferred        libsm.so.6
ELF	7e28c000-7e336000	Deferred        winex11<elf>
  \-PE	7e2a0000-7e336000	\               winex11
ELF	7e383000-7e3aa000	Deferred        libexpat.so.1
ELF	7e3aa000-7e3da000	Deferred        libfontconfig.so.1
ELF	7e3ea000-7e3ff000	Deferred        libz.so.1
ELF	7e3ff000-7e476000	Deferred        libfreetype.so.6
ELF	7e476000-7e4da000	Deferred        shlwapi<elf>
  \-PE	7e480000-7e4da000	\               shlwapi
ELF	7e4da000-7e6d6000	Deferred        shell32<elf>
  \-PE	7e4f0000-7e6d6000	\               shell32
ELF	7e6d6000-7e70e000	Deferred        winspool<elf>
  \-PE	7e6e0000-7e70e000	\               winspool
ELF	7e70e000-7e76d000	Deferred        setupapi<elf>
  \-PE	7e720000-7e76d000	\               setupapi
ELF	7e76d000-7e783000	Deferred        psapi<elf>
  \-PE	7e770000-7e783000	\               psapi
ELF	7e783000-7e86f000	Deferred        oleaut32<elf>
  \-PE	7e7a0000-7e86f000	\               oleaut32
ELF	7e86f000-7e8e2000	Deferred        rpcrt4<elf>
  \-PE	7e880000-7e8e2000	\               rpcrt4
ELF	7e8e2000-7e9e6000	Deferred        ole32<elf>
  \-PE	7e900000-7e9e6000	\               ole32
ELF	7e9e6000-7eada000	Deferred        comctl32<elf>
  \-PE	7e9f0000-7eada000	\               comctl32
ELF	7eada000-7eb67000	Deferred        msvcrt<elf>
  \-PE	7eaf0000-7eb67000	\               msvcrt
ELF	7eb67000-7eb80000	Deferred        version<elf>
  \-PE	7eb70000-7eb80000	\               version
ELF	7eb80000-7ecb4000	Deferred        user32<elf>
  \-PE	7eb90000-7ecb4000	\               user32
ELF	7ecb4000-7ed40000	Deferred        gdi32<elf>
  \-PE	7ecc0000-7ed40000	\               gdi32
ELF	7ed40000-7ed9c000	Deferred        advapi32<elf>
  \-PE	7ed50000-7ed9c000	\               advapi32
ELF	7ed9c000-7eda8000	Deferred        libnss_files.so.2
ELF	7eda8000-7edb3000	Deferred        libnss_nis.so.2
ELF	7edb3000-7edca000	Deferred        libnsl.so.1
ELF	7efca000-7eff0000	Deferred        libm.so.6
ELF	7eff0000-7eff5000	Deferred        libuuid.so.1
ELF	b7425000-b7429000	Deferred        libdl.so.2
ELF	b7429000-b7586000	Deferred        libc.so.6
ELF	b7587000-b75a1000	Deferred        libpthread.so.0
ELF	b75a8000-b75b0000	Deferred        libnss_compat.so.2
ELF	b75b1000-b76f2000	Dwarf           libwine.so.1
ELF	b76f4000-b7712000	Deferred        ld-linux.so.2
ELF	b7712000-b7713000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000051    0
	00000053    0
	0000001b    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000016    0
	00000013    0
	00000012    0
00000018 plugplay.exe
	0000001c    0
	0000001a    0
	00000019    0
0000001d explorer.exe
	0000001e    0
00000021 Steam.exe
	00000041    0
	00000040    0
	0000003f    0
	0000003b    0
	0000003a    1
	00000038    1
	00000037    0
	00000036    0
	00000035    0
	00000033    0
	00000031   15
	0000002f    0
	0000002e    0
	0000002c    0
	00000029    0
	00000028    0
	00000027    0
	00000026    0
	00000025    0
	00000024    0
	00000023    0
	00000022    0
0000000d Unity.exe
	00000043    0
	00000046    0
	0000003d    0
	0000003e    0
	00000032    0
00000049 IE8-WindowsXP-x86-enu.exe
	00000063    0
	00000047    0
00000015 (D) S:\cb9ccc6cf278f4552bb9453f\update\iesetup.exe
	0000004d    0
	0000004c    0
	00000065    0 <==
Backtrace:
=>0 0x7b869e51 InterlockedDecrement+0x9() in kernel32 (0x0033fbac)
  1 0x7dd305a0 in wintrust (+0x2059f) (0x0033fc0c)
  2 0x7dd32a31 WinVerifyTrust+0x1080() in wintrust (0x0033fcac)
  3 0x01013954 in iesetup (+0x13953) (0x0033fd50)
  4 0x0101732a in iesetup (+0x17329) (0x0033fde8)
  5 0x01011163 in iesetup (+0x11162) (0x0033fe00)
  6 0x01028a8c in iesetup (+0x28a8b) (0x0033fe90)
  7 0x7b8583cc call_process_entry+0xb() in kernel32 (0x0033fea8)
  8 0x7b85906f ExitProcess+0xc9e() in kernel32 (0x0033fee8)
  9 0x7bc71b28 call_thread_func+0xb() in ntdll (0x0033fef8)
  10 0x7bc74610 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  11 0x7bc49e4a call_dll_entry_point+0x629() in ntdll (0x0033ffe8)
  

[/PHP]

---

