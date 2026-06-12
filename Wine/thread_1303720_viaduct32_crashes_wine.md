---
title: "viaduct32 crashes wine"
date: 2009-10-28
forum: Wine
---

### Post by T3kn0m0nk3Y on 2009-10-28
I'm trying to run a win32 app called Viaduct. It's a terminal emulation program with addition features above and beyond basic telnet with VT220 emulation.

I'd love to find a linux or .deb package that can do the same functionality as this or accuterm, or Procomm, but there just simply doesn't seem to be any alternatives.

Anyway, when I launch the app it simply crashes with a generic wine error:

"The program viaduct.exe has encountered a  serious problem and needs to close. We are sorry for the inconvenience.

This may be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.oef](http://appdb.winehq.oef) for tips about running this application...." bla bla

When running from the command line

wine viaduct.exe

```
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7cdd283 (thread 002f), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7cdd283).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7cdd283 ESP:0032f6b4 EBP:0032f6f0 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7e009114 ECX:00000000 EDX:feff7364
 ESI:0000000b EDI:0047ad20
Stack dump:
0x0032f6b4:  7dff63a0 00000000 7b8b17f8 7ee28600
0x0032f6c4:  0032f6e4 7ed9528b 001a0154 0000012c
0x0032f6d4:  0000000c 00000000 0039a400 00000007
0x0032f6e4:  7b8b17f8 0000000b 0047ad20 0032f920
0x0032f6f4:  00391a7a 000d017e 000007e8 0039a264
0x0032f704:  00000000 00150d1c 00000400 7bc4508f
Backtrace:
=>0 0xb7cdd283 strlen+0x33() in libc.so.6 (0x0032f6f0)
  1 0x00391a7a in vni_sock (+0x1a7a) (0x0032f920)
  2 0x0040439c in viaduct (+0x439c) (0x0032fbfc)
  3 0x00403756 in viaduct (+0x3756) (0x0032fc54)
  4 0x00402e1a in viaduct (+0x2e1a) (0x0032fc5c)
  5 0x0046d291 in viaduct (+0x6d291) (0x0032fdbc)
  6 0x0046c8d5 in viaduct (+0x6c8d5) (0x0032fe2c)
  7 0x0047ae5f in viaduct (+0x7ae5f) (0x0032feb8)
  8 0x7b875305 in kernel32 (+0x55305) (0x0032fee8)
  9 0x7bc6ae74 call_thread_func+0xc() in ntdll (0x0032fef8)
  10 0x7bc6ce51 in ntdll (+0x5ce51) (0x0032ffc8)
  11 0x7bc4820a in ntdll (+0x3820a) (0x0032ffe8)
0xb7cdd283 strlen+0x33 in libc.so.6: movl	0x0(%eax),%ecx
Modules:
Module	Address			Debug info	Name (94 modules)
PE	  390000-  3a3000	Export          vni_sock
PE	  400000-  4bc000	Export          viaduct
PE	10000000-10051000	Deferred        accuisr5
ELF	7b800000-7b96e000	Export          kernel32<elf>
  \-PE	7b820000-7b96e000	\               kernel32
ELF	7bc00000-7bcaf000	Export          ntdll<elf>
  \-PE	7bc10000-7bcaf000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7dfc3000-7dfe1000	Deferred        iphlpapi<elf>
  \-PE	7dfd0000-7dfe1000	\               iphlpapi
ELF	7dfe1000-7e00b000	Deferred        ws2_32<elf>
  \-PE	7dff0000-7e00b000	\               ws2_32
ELF	7e00b000-7e025000	Deferred        wsock32<elf>
  \-PE	7e010000-7e025000	\               wsock32
ELF	7e0e0000-7e14b000	Deferred        rpcrt4<elf>
  \-PE	7e0f0000-7e14b000	\               rpcrt4
ELF	7e14b000-7e243000	Deferred        ole32<elf>
  \-PE	7e160000-7e243000	\               ole32
ELF	7e26d000-7e2a0000	Deferred        uxtheme<elf>
  \-PE	7e270000-7e2a0000	\               uxtheme
ELF	7e2a0000-7e2a4000	Deferred        libgpg-error.so.0
ELF	7e2a4000-7e2f1000	Deferred        libgcrypt.so.11
ELF	7e2f1000-7e301000	Deferred        libtasn1.so.3
ELF	7e301000-7e314000	Deferred        libresolv.so.2
ELF	7e314000-7e317000	Deferred        libkeyutils.so.1
ELF	7e317000-7e349000	Deferred        libcrypt.so.1
ELF	7e349000-7e3bf000	Deferred        libgnutls.so.13
ELF	7e3bf000-7e3e2000	Deferred        libk5crypto.so.3
ELF	7e3e2000-7e46f000	Deferred        libkrb5.so.3
ELF	7e46f000-7e498000	Deferred        libgssapi_krb5.so.2
ELF	7e498000-7e4cb000	Deferred        libcups.so.2
ELF	7e4d8000-7e4f0000	Deferred        spoolss<elf>
  \-PE	7e4e0000-7e4f0000	\               spoolss
ELF	7e4f0000-7e50f000	Deferred        localspl<elf>
  \-PE	7e500000-7e50f000	\               localspl
ELF	7e50f000-7e518000	Deferred        libxcursor.so.1
ELF	7e518000-7e51d000	Deferred        libxfixes.so.3
ELF	7e51d000-7e520000	Deferred        libxcomposite.so.1
ELF	7e520000-7e526000	Deferred        libxrandr.so.2
ELF	7e526000-7e52e000	Deferred        libxrender.so.1
ELF	7e52e000-7e533000	Deferred        libxxf86vm.so.1
ELF	7e533000-7e536000	Deferred        libxinerama.so.1
ELF	7e536000-7e556000	Deferred        imm32<elf>
  \-PE	7e540000-7e556000	\               imm32
ELF	7e556000-7e55b000	Deferred        libxdmcp.so.6
ELF	7e55b000-7e573000	Deferred        libxcb.so.1
ELF	7e573000-7e575000	Deferred        libxcb-xlib.so.0
ELF	7e575000-7e65c000	Deferred        libx11.so.6
ELF	7e65c000-7e66a000	Deferred        libxext.so.6
ELF	7e66a000-7e682000	Deferred        libice.so.6
ELF	7e682000-7e68a000	Deferred        libsm.so.6
ELF	7e68a000-7e692000	Deferred        libkrb5support.so.0
ELF	7e692000-7e695000	Deferred        libcom_err.so.2
ELF	7e697000-7e732000	Deferred        winex11<elf>
  \-PE	7e6b0000-7e732000	\               winex11
ELF	7e777000-7e798000	Deferred        libexpat.so.1
ELF	7e798000-7e7c2000	Deferred        libfontconfig.so.1
ELF	7e7c2000-7e7c5000	Deferred        libxau.so.6
ELF	7e7cf000-7e7e4000	Deferred        libz.so.1
ELF	7e7e4000-7e851000	Deferred        libfreetype.so.6
ELF	7e85e000-7e872000	Deferred        system.drv16.so
PE	7e860000-7e872000	Deferred        system.drv16
ELF	7e872000-7e886000	Deferred        ctl3d32<elf>
  \-PE	7e880000-7e886000	\               ctl3d32
ELF	7e886000-7e899000	Deferred        lz32<elf>
  \-PE	7e890000-7e899000	\               lz32
ELF	7e899000-7e8b1000	Deferred        version<elf>
  \-PE	7e8a0000-7e8b1000	\               version
ELF	7e8b1000-7e978000	Deferred        comctl32<elf>
  \-PE	7e8c0000-7e978000	\               comctl32
ELF	7e978000-7e9d3000	Deferred        shlwapi<elf>
  \-PE	7e990000-7e9d3000	\               shlwapi
ELF	7e9d3000-7eb62000	Deferred        shell32<elf>
  \-PE	7e9e0000-7eb62000	\               shell32
ELF	7eb62000-7ec13000	Deferred        comdlg32<elf>
  \-PE	7eb70000-7ec13000	\               comdlg32
ELF	7ec13000-7ec46000	Deferred        winspool<elf>
  \-PE	7ec20000-7ec46000	\               winspool
ELF	7ec46000-7ec9c000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec9c000	\               advapi32
ELF	7ec9c000-7ed3b000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed3b000	\               gdi32
ELF	7ed3b000-7ee81000	Deferred        user32<elf>
  \-PE	7ed50000-7ee81000	\               user32
ELF	7efa1000-7efac000	Deferred        libnss_files.so.2
ELF	7efac000-7efb6000	Deferred        libnss_nis.so.2
ELF	7efb6000-7efce000	Deferred        libnsl.so.1
ELF	7efce000-7eff3000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7c67000-b7c6b000	Deferred        libdl.so.2
ELF	b7c6b000-b7dba000	Export          libc.so.6
ELF	b7dbb000-b7dd3000	Deferred        libpthread.so.0
ELF	b7de0000-b7f1b000	Deferred        libwine.so.1
ELF	b7f1d000-b7f39000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000e 
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
0000001a 
	0000001b    0
0000002e (D) C:\VIADCT32\viaduct.exe
	0000002f    0 <==
Backtrace:
=>0 0xb7cdd283 strlen+0x33() in libc.so.6 (0x0032f6f0)
  1 0x00391a7a in vni_sock (+0x1a7a) (0x0032f920)
  2 0x0040439c in viaduct (+0x439c) (0x0032fbfc)
  3 0x00403756 in viaduct (+0x3756) (0x0032fc54)
  4 0x00402e1a in viaduct (+0x2e1a) (0x0032fc5c)
  5 0x0046d291 in viaduct (+0x6d291) (0x0032fdbc)
  6 0x0046c8d5 in viaduct (+0x6c8d5) (0x0032fe2c)
  7 0x0047ae5f in viaduct (+0x7ae5f) (0x0032feb8)
  8 0x7b875305 in kernel32 (+0x55305) (0x0032fee8)
  9 0x7bc6ae74 call_thread_func+0xc() in ntdll (0x0032fef8)
  10 0x7bc6ce51 in ntdll (+0x5ce51) (0x0032ffc8)
  11 0x7bc4820a in ntdll (+0x3820a) (0x0032ffe8)

```

Any help would be very appreciated. We need to come up with a solution to our terminal emulation needs, and I would love for that solution to a Linux one over Micro$oft.

-TM

---

