---
title: "microsoft office 07 word"
date: 2010-08-27
forum: Wine
---

### Post by jeslinmx on 2010-08-27
I am trying to run Microsoft Office 07 on Ubuntu 10.04 Desktop 64-bit. My wine is version 1.2-0ubuntu1~lucidppa1 (from synaptic). I get "WINWORD.exe has an encountered a serious problem etc." Running from terminal i get
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:msvcrt:_controlfp_s ((nil) 65536 196608) semi-stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:system:SetProcessDPIAware stub!
fixme:mscoree:GetVersionFromProcess (0xffffffff, 0x32bea4, 30, (nil)): stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:msvcrt:_controlfp_s ((nil) 65536 196608) semi-stub
fixme:imm:ImmDisableIME (-1): stub
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:msvcrt:_controlfp_s ((nil) 65536 196608) semi-stub
fixme:ver:RtlGetProductInfo (6,1,0,0,0x33fc5c): stub
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x000000c9,(nil),0x0000,0x00000000,0x3f4000,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:OpenEventLogW ((null),L"Application") stub
fixme:advapi:CloseEventLog (0xcafe4242) stub
fixme:advapi:OpenEventLogW ((null),L"System") stub
fixme:advapi:CloseEventLog (0xcafe4242) stub
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x000000d5,(nil),0x0000,0x00000000,0x3f4000,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:OpenEventLogW ((null),L"Microsoft Office 12 Sessions") stub
fixme:advapi:ReadEventLogW (0xcafe4242,0x00000009,0x00000000,0x720000,0x0007d000,0x33fd4c,0x33fd54) stub
fixme:advapi:CloseEventLog (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000140,(nil),0x0002,0x00000000,0x439010,(nil)): stub
err:eventlog:ReportEventW L"2kgl"
err:eventlog:ReportEventW L"N/A"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x000000cd,(nil),0x0000,0x00000000,0x3f4000,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x000003e7,(nil),0x0000,0x00000000,0x3f4000,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ver:RtlGetProductInfo (6,1,0,0,0x33fc54): stub
fixme:netapi32:NetGetJoinInformation Stub (null) 0x33fd8c 0x33fd80
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs
fixme:ver:RtlGetProductInfo (6,1,0,0,0x33fad4): stub
fixme:netapi32:NetGetJoinInformation Stub (null) 0x33fc0c 0x33fc00

and then the error window opens.

wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00000000 ESP:0032f2c4 EBP:0032f838 EFLAGS:00010202(  R- --  I   - - - )
 EAX:3342c418 EBX:00000000 ECX:3342c418 EDX:0000000e
 ESI:00000104 EDI:334caaf8
Stack dump:
0x0032f2c4:  32bd7ce1 334caaf8 00000002 00000003
0x0032f2d4:  0032fdd6 7eda89d0 0032f92c 00000010
0x0032f2e4:  0032f37c 00000000 0032f394 f75ab3f1
0x0032f2f4:  00000000 003a0043 0075005c 00650073
0x0032f304:  00730072 006a005c 00730065 00750068
0x0032f314:  005c0061 00650054 0070006d 0000005c
Backtrace:
=>0 0x00000000 (0x0032f838)
  1 0x32604aa5 in mso (+0x4aa4) (0x0032f848)
  2 0x312446cd in wwlib (+0x46cc) (0x0032fddc)
  3 0x300015d7 in winword (+0x15d6) (0x0032fe00)
  4 0x3000155d in winword (+0x155c) (0x0032fe90)
  5 0x7b855bcc call_process_entry+0xb() in kernel32 (0x0032fea8)
  6 0x7b857dfb in kernel32 (+0x47dfa) (0x0032fee8)
  7 0x7bc710c0 call_thread_func+0xb() in ntdll (0x0032fef8)
  8 0x7bc71290 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  9 0x7bc4c19a in ntdll (+0x3c199) (0x0032ffe8)
0x00000000: -- no code accessible --
Modules:
Module	Address			Debug info	Name (82 modules)
PE	30000000-30057000	Export          winword
PE	31240000-322ec000	Export          wwlib
PE	32600000-33618000	Export          mso
PE	3a9d0000-3b750000	Deferred        oart
ELF	7b800000-7b972000	Export          kernel32<elf>
  \-PE	7b810000-7b972000	\               kernel32
ELF	7bc00000-7bcb9000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb9000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7dfe4000-7e018000	Deferred        uxtheme<elf>
  \-PE	7dff0000-7e018000	\               uxtheme
ELF	7e018000-7e031000	Deferred        version<elf>
  \-PE	7e020000-7e031000	\               version
ELF	7e031000-7e053000	Deferred        cabinet<elf>
  \-PE	7e040000-7e053000	\               cabinet
ELF	7e053000-7e077000	Deferred        mpr<elf>
  \-PE	7e060000-7e077000	\               mpr
ELF	7e077000-7e0d3000	Deferred        wininet<elf>
  \-PE	7e080000-7e0d3000	\               wininet
ELF	7e0d3000-7e1be000	Deferred        comctl32<elf>
  \-PE	7e0e0000-7e1be000	\               comctl32
ELF	7e1be000-7e220000	Deferred        shlwapi<elf>
  \-PE	7e1d0000-7e220000	\               shlwapi
ELF	7e220000-7e3f8000	Deferred        shell32<elf>
  \-PE	7e230000-7e3f8000	\               shell32
ELF	7e3f8000-7e4e1000	Deferred        oleaut32<elf>
  \-PE	7e410000-7e4e1000	\               oleaut32
ELF	7e4e1000-7e53e000	Deferred        urlmon<elf>
  \-PE	7e4f0000-7e53e000	\               urlmon
ELF	7e53e000-7e60e000	Deferred        msi<elf>
  \-PE	7e550000-7e60e000	\               msi
ELF	7e60e000-7e618000	Deferred        libxcursor.so.1
ELF	7e618000-7e61e000	Deferred        libxfixes.so.3
ELF	7e61e000-7e622000	Deferred        libxcomposite.so.1
ELF	7e622000-7e62a000	Deferred        libxrandr.so.2
ELF	7e62a000-7e634000	Deferred        libxrender.so.1
ELF	7e634000-7e63a000	Deferred        libxxf86vm.so.1
ELF	7e63a000-7e63e000	Deferred        libxinerama.so.1
ELF	7e63e000-7e660000	Deferred        imm32<elf>
  \-PE	7e640000-7e660000	\               imm32
ELF	7e660000-7e666000	Deferred        libxdmcp.so.6
ELF	7e666000-7e66a000	Deferred        libxau.so.6
ELF	7e66a000-7e684000	Deferred        libxcb.so.1
ELF	7e684000-7e689000	Deferred        libuuid.so.1
ELF	7e689000-7e7a6000	Deferred        libx11.so.6
ELF	7e7a6000-7e7b6000	Deferred        libxext.so.6
ELF	7e7b6000-7e7cf000	Deferred        libice.so.6
ELF	7e7cf000-7e7d8000	Deferred        libsm.so.6
ELF	7e7dc000-7e7f0000	Deferred        lz32<elf>
  \-PE	7e7e0000-7e7f0000	\               lz32
ELF	7e7f2000-7e895000	Deferred        winex11<elf>
  \-PE	7e800000-7e895000	\               winex11
ELF	7e8c4000-7e8eb000	Deferred        libexpat.so.1
ELF	7e8eb000-7e91b000	Deferred        libfontconfig.so.1
ELF	7e91b000-7e930000	Deferred        libz.so.1
ELF	7e930000-7e9a6000	Deferred        libfreetype.so.6
ELF	7e9c0000-7ea34000	Deferred        rpcrt4<elf>
  \-PE	7e9d0000-7ea34000	\               rpcrt4
ELF	7ea34000-7eb65000	Deferred        user32<elf>
  \-PE	7ea50000-7eb65000	\               user32
ELF	7eb65000-7ec65000	Deferred        ole32<elf>
  \-PE	7eb80000-7ec65000	\               ole32
ELF	7ec65000-7ecf0000	Deferred        gdi32<elf>
  \-PE	7ec70000-7ecf0000	\               gdi32
ELF	7ecf0000-7ed4b000	Deferred        advapi32<elf>
  \-PE	7ed00000-7ed4b000	\               advapi32
ELF	7ed4b000-7ed7d000	Deferred        msvcr90<elf>
  \-PE	7ed50000-7ed7d000	\               msvcr90
ELF	7ed7d000-7edff000	Deferred        msvcrt<elf>
  \-PE	7ed90000-7edff000	\               msvcrt
ELF	7edff000-7ee2e000	Deferred        msvcr80<elf>
  \-PE	7ee10000-7ee2e000	\               msvcr80
ELF	7ef8b000-7ef97000	Deferred        libnss_files.so.2
ELF	7ef97000-7efa1000	Deferred        libnss_nis.so.2
ELF	7efa1000-7efb8000	Deferred        libnsl.so.1
ELF	7efb8000-7efc0000	Deferred        libnss_compat.so.2
ELF	7efc0000-7efe6000	Deferred        libm.so.6
ELF	f7441000-f7445000	Deferred        libdl.so.2
ELF	f7445000-f759f000	Deferred        libc.so.6
ELF	f75a0000-f75b9000	Deferred        libpthread.so.0
ELF	f75d3000-f7713000	Export          libwine.so.1
ELF	f7715000-f7733000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Microsoft Office\Office12\WINWORD.EXE
	00000009    0 <==
0000000e services.exe
	00000016    0
	00000015    0
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
Backtrace:
=>0 0x00000000 (0x0032f838)
  1 0x32604aa5 in mso (+0x4aa4) (0x0032f848)
  2 0x312446cd in wwlib (+0x46cc) (0x0032fddc)
  3 0x300015d7 in winword (+0x15d6) (0x0032fe00)
  4 0x3000155d in winword (+0x155c) (0x0032fe90)
  5 0x7b855bcc call_process_entry+0xb() in kernel32 (0x0032fea8)
  6 0x7b857dfb in kernel32 (+0x47dfa) (0x0032fee8)
  7 0x7bc710c0 call_thread_func+0xb() in ntdll (0x0032fef8)
  8 0x7bc71290 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  9 0x7bc4c19a in ntdll (+0x3c199) (0x0032ffe8)
fixme:mscoree:GetVersionFromProcess (0xffffffff, 0x32bea4, 30, (nil)): stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:msvcrt:_controlfp_s ((nil) 65536 196608) semi-stub
fixme:imm:ImmDisableIME (-1): stub
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:msvcrt:_controlfp_s ((nil) 65536 196608) semi-stub
fixme:ver:RtlGetProductInfo (6,1,0,0,0x33fc5c): stub
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x000000c9,(nil),0x0000,0x00000000,0x3f4000,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:OpenEventLogW ((null),L"Application") stub
fixme:advapi:CloseEventLog (0xcafe4242) stub
fixme:advapi:OpenEventLogW ((null),L"System") stub
fixme:advapi:CloseEventLog (0xcafe4242) stub
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x000000d5,(nil),0x0000,0x00000000,0x3f4000,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:OpenEventLogW ((null),L"Microsoft Office 12 Sessions") stub
fixme:advapi:ReadEventLogW (0xcafe4242,0x00000009,0x00000000,0x720000,0x0007d000,0x33fd4c,0x33fd54) stub
fixme:advapi:CloseEventLog (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000140,(nil),0x0002,0x00000000,0x439010,(nil)): stub
err:eventlog:ReportEventW L"2kgl"
err:eventlog:ReportEventW L"N/A"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x000000cd,(nil),0x0000,0x00000000,0x3f4000,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L"Microsoft Office 12 Diagnostics"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x000003e7,(nil),0x0000,0x00000000,0x3f4000,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ver:RtlGetProductInfo (6,1,0,0,0x33fc54): stub
fixme:netapi32:NetGetJoinInformation Stub (null) 0x33fd8c 0x33fd80

and it returns me to terminal.
I heard that this can be caused by running wine as sudo. i tried cd ~
sudo chown -R $USER:$USER .wine (from winehq faq) but it still doesn't work. help?

---

### Post by sxmaxchine on 2010-08-27
try installing it through [play on linux]("http://www.playonlinux.com/").  believe it installs the correct version of wine and all the winetricks needed to use office 07.

---

### Post by jeslinmx on 2010-08-27
erm, should i remove wine before installing pol? and there doesn't seem, to be a lucid version on the site.

---

### Post by jeslinmx on 2010-08-27
and for that matter, is pol sudo-safe?

---

