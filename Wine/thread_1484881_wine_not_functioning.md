---
title: "wine not functioning"
date: 2010-05-16
forum: Wine
---

### Post by padeco on 2010-05-16
hi there,
i just installed wine, may be i did not completely remove previous install? but the new install went without any issues using ./tools/wineinstall etc...

however, when i try to run winecfg i get the error below: 

any ideas please.

~$ winecfg 
wine: Unhandled page fault on write access to 0x00540170 at address 0x68320b03 (thread 0016), starting debugger...
Unhandled exception: page fault on write access to 0x00540170 in 32-bit code (0x68320b03).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:68320b03 ESP:0053e690 EBP:0053e738 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000001 EBX:68322ff4 ECX:00001000 EDX:005400d0
 ESI:00540000 EDI:0054002a
Stack dump:
0x0053e690:  00540000 00001000 00000002 00000000
0x0053e6a0:  00110fda 00230000 00220000 00000058
0x0053e6b0:  0000002a 0053e71c 0053e718 0054002a
0x0053e6c0:  00140000 005400d0 00001000 00540000
0x0053e6d0:  00110000 7bc9bff4 0053e738 7bc479d3
0x0053e6e0:  00110060 0053e714 0053e70c 0053e71c
Backtrace:
=>0 0x68320b03 load_driver_module+0x283(name="?&#65533;") [/home/bull/programs/wine-1.1.44/programs/winedevice/device.c:103] in winedevice (0x0053e9c8)
  1 0x68320dc3 load_driver+0x2a2() [/home/bull/programs/wine-1.1.44/programs/winedevice/device.c:229] in winedevice (0x0053ea18)
  2 0x683213e6 ServiceMain+0xc5(argc=0x0001, argv=0x110a88) [/home/bull/programs/wine-1.1.44/programs/winedevice/device.c:287] in winedevice (0x0053ea68)
  3 0x6ab09ad4 service_thread+0xf3(arg=0x110948) [/home/bull/programs/wine-1.1.44/dlls/advapi32/service.c:294] in advapi32 (0x0053ea78)
  4 0x7bc6f1f0 call_thread_func+0xb() in ntdll (0x0053eb48)
  5 0x7bc6f3c0 call_thread_entry_point+0x6f(entry=0x6ab099e0, arg=0x110948) [/home/bull/programs/wine-1.1.44/dlls/ntdll/signal_i386.c:2466] in ntdll (0x0053f398)
  6 0x7bc77a75 start_thread+0xf4(info=0x7ffd0fb8) [/home/bull/programs/wine-1.1.44/dlls/ntdll/thread.c:399] in ntdll (0x0053f498)
  7 0x6816280e start_thread+0xbd() in libpthread.so.0 (0x00000000)
0x68320b03 load_driver_module+0x283 [/home/bull/programs/wine-1.1.44/programs/winedevice/device.c:103] in winedevice: movl	$0x0,0xa0(%edx)
103	            nt->OptionalHeader.DataDirectory[IMAGE_DIRECTORY_ENTRY_BASERELOC].VirtualAddress = 0;
Modules:
Module	Address			Debug info	Name (26 modules)
PE	  540000-  59b000	Deferred        aksfridge.sys
ELF	414f6000-4150e000	Deferred        hal<elf>
  \-PE	41500000-4150e000	\               hal
ELF	68000000-6801d000	Deferred        ld-linux.so.2
ELF	6801d000-6815d000	Deferred        libwine.so.1
ELF	6815d000-68176000	Export          libpthread.so.0
ELF	68176000-682bb000	Deferred        libc.so.6
ELF	682bb000-682bf000	Deferred        libdl.so.2
ELF	682bf000-682e5000	Deferred        libm.so.6
ELF	682e5000-682ed000	Deferred        libnss_compat.so.2
ELF	682ed000-68304000	Deferred        libnsl.so.1
ELF	68304000-6830f000	Deferred        libnss_nis.so.2
ELF	6830f000-68324000	Dwarf           winedevice<elf>
  \-PE	68310000-68324000	\               winedevice
ELF	68324000-68398000	Deferred        rpcrt4<elf>
  \-PE	68330000-68398000	\               rpcrt4
ELF	6aacb000-6ab25000	Dwarf           advapi32<elf>
  \-PE	6aae0000-6ab25000	\               advapi32
ELF	72a01000-72a46000	Deferred        ntoskrnl<elf>
  \-PE	72a10000-72a46000	\               ntoskrnl
ELF	79188000-79194000	Deferred        libnss_files.so.2
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b810000-7b93c000	\               kernel32
ELF	7bc00000-7bcb8000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcb8000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 ntdll.dll
	00000009    0
0000000a wineboot.exe
	0000000b    0
0000000c winemenubuilder.exe
	0000000d    0
0000000e services.exe
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 (D) C:\windows\system32\winedevice.exe
	00000016    0 <==
	00000013    0
	00000012    0
Backtrace:
=>0 0x68320b03 load_driver_module+0x283(name="?&#65533;") [/home/bull/programs/wine-1.1.44/programs/winedevice/device.c:103] in winedevice (0x0053e9c8)
  1 0x68320dc3 load_driver+0x2a2() [/home/bull/programs/wine-1.1.44/programs/winedevice/device.c:229] in winedevice (0x0053ea18)
  2 0x683213e6 ServiceMain+0xc5(argc=0x0001, argv=0x110a88) [/home/bull/programs/wine-1.1.44/programs/winedevice/device.c:287] in winedevice (0x0053ea68)
  3 0x6ab09ad4 service_thread+0xf3(arg=0x110948) [/home/bull/programs/wine-1.1.44/dlls/advapi32/service.c:294] in advapi32 (0x0053ea78)
  4 0x7bc6f1f0 call_thread_func+0xb() in ntdll (0x0053eb48)
  5 0x7bc6f3c0 call_thread_entry_point+0x6f(entry=0x6ab099e0, arg=0x110948) [/home/bull/programs/wine-1.1.44/dlls/ntdll/signal_i386.c:2466] in ntdll (0x0053f398)
  6 0x7bc77a75 start_thread+0xf4(info=0x7ffd0fb8) [/home/bull/programs/wine-1.1.44/dlls/ntdll/thread.c:399] in ntdll (0x0053f498)
  7 0x6816280e start_thread+0xbd() in libpthread.so.0 (0x00000000)
fixme:advapi:RegisterEventSourceW ((null),L"Print"): stub
fixme:ds:DsRoleGetPrimaryDomainInformation ((nil), 1, 0x32efc0) stub
fixme:advapi:LsaOpenPolicy ((null),0x32ef5c,0x00000001,0x32ef78) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:profile:CloseProfileUserMapping (), stub!
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x384170,L"Server",L"\\\\laptop",0x13c708,0xac,0x00000001,0x00000001,(nil),0,1,0x75bfb4f8)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x384170,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
err:winspool:CUPS_LoadPrinters printer 'Photosmart-C4340-series' not added by AddPrinterA (error 1797)
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17

---

### Post by beastrace91 on 2010-05-16
What new Wine version did you install? How did you install it? How did you install/remove the old version?

~Jeff

---

### Post by padeco on 2010-05-17
hi jeff,

i uninstalled wine using apt-get remove, also tried ubuntu software centre from the applications option. then, downloaded the latest wine 1.1.44. to install it i used the ./tools/wineinstall option. it did run for quite a while. that was about it.

now, should i delete the .wine folder and all its content and do a new install?

cheers,
padeco

---

