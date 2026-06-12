---
title: "Source games don't run"
date: 2011-01-18
forum: Wine
---

### Post by PhosPhoton on 2011-01-18
I successfully installed and ran Steam, but whenever I try run a Source game in Steam, the "Preparing" window opens for a short while, then another window pops up saying the hl2.exe has encountered a problem and needs to close. Then the game does not run. This happens with Half-Life 2, Portal, Counter-Strike and Alien Swarm.

I am running Ubuntu Maverick Meercat 64-bit
Wine version 1.2.2

My computer specs:
Core 2 Duo E7200 @ 2.9GHz
4GB RAM
ATi Radeon HD4870, using proprietary drivers

I just installed wine and then Steam, nothing else is installed or changed

The output is as follows:
```
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer 0x4c01068, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x435beb8)
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:win:EnumDisplayDevicesW ((null),0,0x32ce24,0x00000000), stub!
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:advapi:RegisterTraceGuidsW (0x3924f30, 0x3f7b720, {3dada31d-19ef-4dc1-b345-037927193422}, 1, 0x3f53b24, (null), (null), 0x3f7b738,)
err:virtual:map_image failed to set 60000020 protection on section .text, noexec filesystem?
wine: Unhandled page fault on read access to 0x004018b0 at address 0x4018b0 (thread 0047), starting debugger...
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd 0x400e6
Unhandled exception: page fault on read access to 0x004018b0 in 32-bit code (0x004018b0).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:004018b0 ESP:0033fe94 EBP:0033fea8 EFLAGS:00010216(  R- --  I   -A-P- )
 EAX:00000000 EBX:7b881ff4 ECX:e9e68cc3 EDX:0033ff10
 ESI:7ffdf000 EDI:004018b0
Stack dump:
0x0033fe94:  7b85406c 7ffdf000 00000000 7b881ff4
0x0033fea4:  7ffdf000 0033fee8 7b8564db 7ffdf000
0x0033feb4:  004018b0 00000000 00000000 00000000
0x0033fec4:  00000000 00000000 00000000 00000000
0x0033fed4:  00000000 00000000 7bc9aff4 ffe29e04
0x0033fee4:  001108a0 0033fef8 7bc6fc80 7ffdf000
Backtrace:
=>0 0x004018b0 EntryPoint() in hl2 (0x0033fea8)
  1 0x7b8564db in kernel32 (+0x464da) (0x0033fee8)
  2 0x7bc6fc80 call_thread_func+0xb() in ntdll (0x0033fef8)
  3 0x7bc6fe50 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  4 0x7bc4ae0a in ntdll (+0x3ae09) (0x0033ffe8)
0x004018b0 EntryPoint in hl2: call	0x00404c0a
Modules:
Module	Address			Debug info	Name (45 modules)
PE	  400000-  41a000	Export          hl2
ELF	7b800000-7b97b000	Export          kernel32<elf>
  \-PE	7b810000-7b97b000	\               kernel32
ELF	7bc00000-7bcb7000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e7ab000-7e7b5000	Deferred        libxcursor.so.1
ELF	7e7b5000-7e7bb000	Deferred        libxfixes.so.3
ELF	7e7bb000-7e7bf000	Deferred        libxcomposite.so.1
ELF	7e7bf000-7e7c7000	Deferred        libxrandr.so.2
ELF	7e7c7000-7e7d1000	Deferred        libxrender.so.1
ELF	7e7d1000-7e7d7000	Deferred        libxxf86vm.so.1
ELF	7e7d7000-7e7db000	Deferred        libxinerama.so.1
ELF	7e7db000-7e7fc000	Deferred        imm32<elf>
  \-PE	7e7e0000-7e7fc000	\               imm32
ELF	7e7fc000-7e802000	Deferred        libxdmcp.so.6
ELF	7e802000-7e81c000	Deferred        libxcb.so.1
ELF	7e81c000-7e939000	Deferred        libx11.so.6
ELF	7e939000-7e949000	Deferred        libxext.so.6
ELF	7e949000-7e962000	Deferred        libice.so.6
ELF	7e962000-7e96b000	Deferred        libsm.so.6
ELF	7e96b000-7ea0d000	Deferred        winex11<elf>
  \-PE	7e980000-7ea0d000	\               winex11
ELF	7ea71000-7ea98000	Deferred        libexpat.so.1
ELF	7ea98000-7eac8000	Deferred        libfontconfig.so.1
ELF	7eae9000-7eb60000	Deferred        libfreetype.so.6
ELF	7eb81000-7ebdb000	Deferred        advapi32<elf>
  \-PE	7eb90000-7ebdb000	\               advapi32
ELF	7ebdb000-7ec66000	Deferred        gdi32<elf>
  \-PE	7ebf0000-7ec66000	\               gdi32
ELF	7ec66000-7ed96000	Deferred        user32<elf>
  \-PE	7ec80000-7ed96000	\               user32
ELF	7ed96000-7eda2000	Deferred        libnss_files.so.2
ELF	7eda2000-7edb9000	Deferred        libnsl.so.1
ELF	7efb9000-7efdf000	Deferred        libm.so.6
ELF	7efdf000-7efe4000	Deferred        libuuid.so.1
ELF	7efe4000-7eff9000	Deferred        libz.so.1
ELF	f74a0000-f74ab000	Deferred        libnss_nis.so.2
ELF	f74ac000-f74b0000	Deferred        libdl.so.2
ELF	f74b0000-f760b000	Deferred        libc.so.6
ELF	f760c000-f7625000	Deferred        libpthread.so.0
ELF	f7628000-f7630000	Deferred        libnss_compat.so.2
ELF	f7640000-f7644000	Deferred        libxau.so.6
ELF	f7646000-f7786000	Export          libwine.so.1
ELF	f7788000-f77a6000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
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
0000003c hl2.exe
	00000045    0
00000041 winedbg.exe
	0000003a    0
00000009 hl2.exe
	0000000c    0
0000000d winedbg.exe
	00000046    0
00000061 Steam.exe
	00000023    0
	0000001f    1
	00000031    1
	00000036    1
	00000055    1
	00000058    1
	0000004b    1
	00000038    1
	00000032    1
	0000001e    1
	0000001c    1
	00000067    1
	00000043    0
	00000062    0
	00000027    0
	0000002d    0
	00000059    0
	00000021    0
	00000066    0
	00000052    1
	00000039    1
	00000050    0
	00000057    0
	0000005d    0
	00000035    0
	00000037   15
	00000064    0
	00000016    0
	0000005f    0
	00000048    0
	00000056    0
	0000002a    0
	0000003e    0
	00000051    0
	00000054    0
	0000004f    0
	00000033    0
0000000b (D) C:\Program Files\Steam\steamapps\jellymann\half-life 2\hl2.exe
	00000047    0 <==
Backtrace:
=>0 0x004018b0 EntryPoint() in hl2 (0x0033fea8)
  1 0x7b8564db in kernel32 (+0x464da) (0x0033fee8)
  2 0x7bc6fc80 call_thread_func+0xb() in ntdll (0x0033fef8)
  3 0x7bc6fe50 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  4 0x7bc4ae0a in ntdll (+0x3ae09) (0x0033ffe8)

```

---

