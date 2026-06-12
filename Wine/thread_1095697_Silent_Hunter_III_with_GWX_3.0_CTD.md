---
title: "Silent Hunter III with GWX 3.0 CTD"
date: 2009-03-14
forum: Wine
---

### Post by rifleman13 on 2009-03-14
Hello to all there!

This is my first post here. I've been using 8.10 for over a week now and I haven't any complaints.

I looked over Wine and thought the testing of Silent Hunter III has some great reviews. So I installed SH3 in Intrepid and ran it and everything seemed fine. The Naval Academy missions seem to run flawlessly, more flawless than in XP, except for those missing exhaust on the ships' funnels.
Everything seem fine so I installed over the GWX 3.0 mod and ran again the Naval Academy missions and everything seemed fine.

So I decided to play the whole campaign. Everything loaded up, and started playing. Then about 15 real-life minutes into playing, the game suddenly CTDed and that's it. Playing up to x512 time compression, location just entering the Netherlands' seas.

Wine version: 1.1.16
Wine configuration:
No overidden libraries.
Vertex Shader Support: Hardware
Allow Pixel Shader
Nothing done in Desktop Integration
Nothing done in Audio
Hardware: P4 2.0 GHz, 1.2 GB RAM
No other wine apps.
From the terminal: wine sh3.exe
```
wine: Unhandled page fault on write access to 0x00650180 at address 0x7ee68ae3 (thread 001b), starting debugger...
Unhandled exception: page fault on write access to 0x00650180 in 32-bit code (0x7ee68ae3).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ee68ae3 ESP:0064e670 EBP:0064e708 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:006500e0 EBX:7ee6aff4 ECX:00001000 EDX:0064e658
 ESI:006608cc EDI:0064e6f4
Stack dump:
0x0064e670:  0065d000 00001000 00000080 00000000
0x0064e680:  00113f30 00113df0 00000038 7bc439ee
0x0064e690:  0064e6f8 006500e0 00001000 00640000
0x0064e6a0:  00650000 006608cc 0065d000 7bc344cf
0x0064e6b0:  00110014 7bc94ff4 0064e708 7bc44f80
0x0064e6c0:  00110054 0064e6f0 0064e6e8 0064e6f8
Backtrace:
=>0 0x7ee68ae3 in winedevice (+0x8ae3) (0x0064e708)
  1 0x7ee68d77 in winedevice (+0x8d77) (0x0064e988)
  2 0x7ee69396 in winedevice (+0x9396) (0x0064e9d8)
  3 0x7ee3e97c in advapi32 (+0x2e97c) (0x0064ea28)
  4 0x7bc73a4e call_thread_entry_point+0xe() in ntdll (0x0064ea38)
  5 0x7bc75482 in ntdll (+0x65482) (0x0064ead8)
  6 0x7bc75650 in ntdll (+0x65650) (0x0064f3c8)
  7 0xb7e5250f start_thread+0xbf() in libpthread.so.0 (0x0064f4c8)
  8 0xb7dcea0e __clone+0x5e() in libc.so.6 (0x00000000)
0x7ee68ae3: movl	$0x0,0xa0(%eax)
Modules:
Module	Address			Debug info	Name (28 modules)
PE	  650000-  661000	Deferred        sfdrv01.sys
ELF	7b800000-7b93f000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93f000	\               kernel32
ELF	7bc00000-7bcb1000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ecdc000-7ed4a000	Deferred        msvcrt<elf>
  \-PE	7ecf0000-7ed4a000	\               msvcrt
ELF	7ed4a000-7ed61000	Deferred        hal<elf>
  \-PE	7ed50000-7ed61000	\               hal
ELF	7ed61000-7edc8000	Deferred        rpcrt4<elf>
  \-PE	7ed70000-7edc8000	\               rpcrt4
ELF	7edc8000-7ee02000	Deferred        ntoskrnl<elf>
  \-PE	7edd0000-7ee02000	\               ntoskrnl
ELF	7ee02000-7ee57000	Export          advapi32<elf>
  \-PE	7ee10000-7ee57000	\               advapi32
ELF	7ee57000-7ee6c000	Export          winedevice<elf>
  \-PE	7ee60000-7ee6c000	\               winedevice
ELF	7ee6c000-7ee78000	Deferred        libnss_files.so.2
ELF	7ee78000-7ee91000	Deferred        libnsl.so.1
ELF	7ee91000-7ee9a000	Deferred        libnss_compat.so.2
ELF	7efca000-7eff0000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7ce9000-b7ced000	Deferred        libdl.so.2
ELF	b7ced000-b7e4b000	Export          libc.so.6
ELF	b7e4c000-b7e65000	Export          libpthread.so.0
ELF	b7e75000-b7fb0000	Deferred        libwine.so.1
ELF	b7fb2000-b7fcf000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	0000001a    0
	00000019    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 (D) C:\windows\system32\winedevice.exe
	0000001b    0 <==
	00000018    0
	00000017    0
Backtrace:
=>0 0x7ee68ae3 in winedevice (+0x8ae3) (0x0064e708)
  1 0x7ee68d77 in winedevice (+0x8d77) (0x0064e988)
  2 0x7ee69396 in winedevice (+0x9396) (0x0064e9d8)
  3 0x7ee3e97c in advapi32 (+0x2e97c) (0x0064ea28)
  4 0x7bc73a4e call_thread_entry_point+0xe() in ntdll (0x0064ea38)
  5 0x7bc75482 in ntdll (+0x65482) (0x0064ead8)
  6 0x7bc75650 in ntdll (+0x65650) (0x0064f3c8)
  7 0xb7e5250f start_thread+0xbf() in libpthread.so.0 (0x0064f4c8)
  8 0xb7dcea0e __clone+0x5e() in libc.so.6 (0x00000000)
wine: Unhandled page fault on write access to 0x00650178 at address 0x7ee68ae3 (thread 0022), starting debugger...
Unhandled exception: page fault on write access to 0x00650178 in 32-bit code (0x7ee68ae3).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ee68ae3 ESP:0064e670 EBP:0064e708 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:006500d8 EBX:7ee6aff4 ECX:00001000 EDX:0064e658
 ESI:006570bc EDI:0064e6f4
Stack dump:
0x0064e670:  00655000 00001000 00000080 00000000
0x0064e680:  00113f30 00113df0 00000038 7bc439ee
0x0064e690:  0064e6f8 006500d8 00001000 00640000
0x0064e6a0:  00650000 006570bc 00655000 7bc344cf
0x0064e6b0:  00110014 7bc94ff4 0064e708 7bc44f80
0x0064e6c0:  00110054 0064e6f0 0064e6e8 0064e6f8
Backtrace:
=>0 0x7ee68ae3 in winedevice (+0x8ae3) (0x0064e708)
  1 0x7ee68d77 in winedevice (+0x8d77) (0x0064e988)
  2 0x7ee69396 in winedevice (+0x9396) (0x0064e9d8)
  3 0x7ee3e97c in advapi32 (+0x2e97c) (0x0064ea28)
  4 0x7bc73a4e call_thread_entry_point+0xe() in ntdll (0x0064ea38)
  5 0x7bc75482 in ntdll (+0x65482) (0x0064ead8)
  6 0x7bc75650 in ntdll (+0x65650) (0x0064f3c8)
  7 0xb7df050f start_thread+0xbf() in libpthread.so.0 (0x0064f4c8)
  8 0xb7d6ca0e __clone+0x5e() in libc.so.6 (0x00000000)
0x7ee68ae3: movl	$0x0,0xa0(%eax)
Modules:
Module	Address			Debug info	Name (24 modules)
PE	  650000-  658000	Deferred        sfhlp02.sys
ELF	7b800000-7b93f000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93f000	\               kernel32
ELF	7bc00000-7bcb1000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ed61000-7edc8000	Deferred        rpcrt4<elf>
  \-PE	7ed70000-7edc8000	\               rpcrt4
ELF	7edc8000-7ee02000	Deferred        ntoskrnl<elf>
  \-PE	7edd0000-7ee02000	\               ntoskrnl
ELF	7ee02000-7ee57000	Export          advapi32<elf>
  \-PE	7ee10000-7ee57000	\               advapi32
ELF	7ee57000-7ee6c000	Export          winedevice<elf>
  \-PE	7ee60000-7ee6c000	\               winedevice
ELF	7ee6c000-7ee78000	Deferred        libnss_files.so.2
ELF	7ee78000-7ee91000	Deferred        libnsl.so.1
ELF	7ee91000-7ee9a000	Deferred        libnss_compat.so.2
ELF	7efca000-7eff0000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c87000-b7c8b000	Deferred        libdl.so.2
ELF	b7c8b000-b7de9000	Export          libc.so.6
ELF	b7dea000-b7e03000	Export          libpthread.so.0
ELF	b7e13000-b7f4e000	Deferred        libwine.so.1
ELF	b7f50000-b7f6d000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000021    0
	0000001a    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
0000001e (D) C:\windows\system32\winedevice.exe
	00000022    0 <==
	00000020    0
	0000001f    0
Backtrace:
=>0 0x7ee68ae3 in winedevice (+0x8ae3) (0x0064e708)
  1 0x7ee68d77 in winedevice (+0x8d77) (0x0064e988)
  2 0x7ee69396 in winedevice (+0x9396) (0x0064e9d8)
  3 0x7ee3e97c in advapi32 (+0x2e97c) (0x0064ea28)
  4 0x7bc73a4e call_thread_entry_point+0xe() in ntdll (0x0064ea38)
  5 0x7bc75482 in ntdll (+0x65482) (0x0064ead8)
  6 0x7bc75650 in ntdll (+0x65650) (0x0064f3c8)
  7 0xb7df050f start_thread+0xbf() in libpthread.so.0 (0x0064f4c8)
  8 0xb7d6ca0e __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b8450f0 to unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry, aborting
wine: Unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry called at address 0x7b8450f0 (thread 0029), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry called in 32-bit code (0x7b845163).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b845163 ESP:0064e624 EBP:0064e688 EFLAGS:00000246(   - 00      - IZP1)
 EAX:7b82f03d EBX:7b8b7ff4 ECX:00000000 EDX:0064e6ac
 ESI:0064e6ac EDI:00000000
Stack dump:
0x0064e624:  0064e6ac 00000008 0000003c 80000100
0x0064e634:  00000001 00000000 7b8450f0 00000002
0x0064e644:  7ede8d60 7edea7fc 0064e658 00000000
0x0064e654:  ffffffff 00000000 00000000 00000000
0x0064e664:  00000000 00000000 00000000 00000000
0x0064e674:  00000000 00000000 7b8450fa 00000000
Backtrace:
=>0 0x7b845163 in kernel32 (+0x25163) (0x0064e688)
  1 0x7ede8cf8 in ntoskrnl (+0x18cf8) (0x0064e6b8)
  2 0x7eddfbc8 in ntoskrnl (+0xfbc8) (0x00000000)
0x7b845163: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (28 modules)
PE	  650000-  655040	Deferred        sfsync02.sys
ELF	7b800000-7b93f000	Export          kernel32<elf>
  \-PE	7b820000-7b93f000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ecdc000-7ed4a000	Deferred        msvcrt<elf>
  \-PE	7ecf0000-7ed4a000	\               msvcrt
ELF	7ed4a000-7ed61000	Deferred        hal<elf>
  \-PE	7ed50000-7ed61000	\               hal
ELF	7ed61000-7edc8000	Deferred        rpcrt4<elf>
  \-PE	7ed70000-7edc8000	\               rpcrt4
ELF	7edc8000-7ee02000	Export          ntoskrnl<elf>
  \-PE	7edd0000-7ee02000	\               ntoskrnl
ELF	7ee02000-7ee57000	Deferred        advapi32<elf>
  \-PE	7ee10000-7ee57000	\               advapi32
ELF	7ee57000-7ee6c000	Deferred        winedevice<elf>
  \-PE	7ee60000-7ee6c000	\               winedevice
ELF	7ee6c000-7ee78000	Deferred        libnss_files.so.2
ELF	7ee78000-7ee91000	Deferred        libnsl.so.1
ELF	7ee91000-7ee9a000	Deferred        libnss_compat.so.2
ELF	7efca000-7eff0000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d29000-b7d2d000	Deferred        libdl.so.2
ELF	b7d2d000-b7e8b000	Deferred        libc.so.6
ELF	b7e8c000-b7ea5000	Deferred        libpthread.so.0
ELF	b7eb5000-b7ff0000	Deferred        libwine.so.1
ELF	b7ff2000-b800f000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000028    0
	0000001a    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000025 (D) C:\windows\system32\winedevice.exe
	00000029    0 <==
	00000027    0
	00000026    0
Backtrace:
=>0 0x7b845163 in kernel32 (+0x25163) (0x0064e688)
  1 0x7ede8cf8 in ntoskrnl (+0x18cf8) (0x0064e6b8)
  2 0x7eddfbc8 in ntoskrnl (+0xfbc8) (0x00000000)
wine: Call from 0x7b8450f0 to unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry, aborting
wine: Call from 0x7b8450f0 to unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry, aborting
wine: could not load L"C:\\windows\\system32\\sh3.exe": Module not found

```

Any advice?

---

