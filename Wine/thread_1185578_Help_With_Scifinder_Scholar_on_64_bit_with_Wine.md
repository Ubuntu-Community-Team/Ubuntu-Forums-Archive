---
title: "Help With Scifinder Scholar on 64 bit with Wine"
date: 2009-06-12
forum: Wine
---

### Post by rmccarri on 2009-06-12
Hi Everyone,
I recently decided to take the 64 bit plunge on my laptop.  Everything is working well with the exception fo Wine with Scifinder Scholar.  I had the program working jaunty i386.

However, with 64bit jaunty, I get the following error from the setup.exe installer:

```
wine: Unhandled page fault on write access to 0x7e9ceec4 at address 0x7e9f65bd (thread 001e), starting debugger...
Unhandled exception: page fault on write access to 0x7e9ceec4 in 32-bit code (0x7e9f65bd).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e9f65bd ESP:0033e994 EBP:0033e9bc EFLAGS:00010212(  R- --  I   -A- - )
 EAX:7e9f3de0 EBX:7ea3cff4 ECX:7e9ceec4 EDX:00000001
 ESI:7e9d5590 EDI:00000004
Stack dump:
0x0033e994:  00000070 0033e9f0 0033ea2c 7bc51ae2
0x0033e9a4:  0033e9b0 7eb36ff4 ffffffff 7ea3cff4
0x0033e9b4:  7e9d5590 00000004 0033ea2c 7e9f577b
0x0033e9c4:  7e9ceec4 00000007 00000000 00000000
0x0033e9d4:  00000000 00000000 00000000 00000000
0x0033e9e4:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x7e9f65bd fill_delegated_proxy_table+0x4d() in rpcrt4 (0x0033e9bc)
  1 0x7e9f577b NdrDllGetClassObject+0x33b() in rpcrt4 (0x0033ea2c)
  2 0x7e9ba759 in oleaut32 (+0xaa759) (0x0033ea5c)
  3 0x7e91834b in oleaut32 (+0x834b) (0x0033ea9c)
  4 0x7e9308f4 in oleaut32 (+0x208f4) (0x0033eb3c)
  5 0x7ea990c4 in ole32 (+0x390c4) (0x0033ebfc)
  6 0x7ea99660 in ole32 (+0x39660) (0x0033ecac)
  7 0x7ea96ec5 CoUnmarshalInterface+0x195() in ole32 (0x0033ed2c)
  8 0x7e92b5d1 in oleaut32 (+0x1b5d1) (0x0033ed9c)
  9 0x7e92cb3f in oleaut32 (+0x1cb3f) (0x0033ee0c)
  10 0x7e92c438 in oleaut32 (+0x1c438) (0x0033ee7c)
  11 0x7e92c79a in oleaut32 (+0x1c79a) (0x0033eeec)
  12 0x7e92f5f9 in oleaut32 (+0x1f5f9) (0x0033efdc)
  13 0x0034004c (0x0033f16c)
  14 0x00403259 in setup (+0x3259) (0x0033f1c8)
  15 0x00402d4e in setup (+0x2d4e) (0x0033f88c)
  16 0x00402a07 in setup (+0x2a07) (0x0033fea4)
  17 0x0040254e in setup (+0x254e) (0x0033ff08)
  18 0x7b878690 in kernel32 (+0x58690) (0x0033ffe8)
  19 0xf7dbfde7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7e9f65bd fill_delegated_proxy_table+0x4d in rpcrt4: movl	%eax,0x0(%ecx)
Modules:
Module	Address			Debug info	Name (59 modules)
PE	  400000-  411000	Export          setup
ELF	7b800000-7b954000	Export          kernel32<elf>
  \-PE	7b820000-7b954000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e550000-7e584000	Deferred        uxtheme<elf>
  \-PE	7e560000-7e584000	\               uxtheme
ELF	7e584000-7e58d000	Deferred        libxcursor.so.1
ELF	7e58d000-7e592000	Deferred        libxfixes.so.3
ELF	7e592000-7e596000	Deferred        libxcomposite.so.1
ELF	7e596000-7e59e000	Deferred        libxrandr.so.2
ELF	7e59e000-7e5a8000	Deferred        libxrender.so.1
ELF	7e5a8000-7e5ae000	Deferred        libxxf86vm.so.1
ELF	7e5ae000-7e5b1000	Deferred        libxinerama.so.1
ELF	7e5b1000-7e5d2000	Deferred        imm32<elf>
  \-PE	7e5c0000-7e5d2000	\               imm32
ELF	7e5d2000-7e5d7000	Deferred        libxdmcp.so.6
ELF	7e5d7000-7e5f1000	Deferred        libxcb.so.1
ELF	7e5f1000-7e5f5000	Deferred        libxau.so.6
ELF	7e5f5000-7e5fa000	Deferred        libuuid.so.1
ELF	7e5fa000-7e6e9000	Deferred        libx11.so.6
ELF	7e6e9000-7e6f9000	Deferred        libxext.so.6
ELF	7e6f9000-7e711000	Deferred        libice.so.6
ELF	7e711000-7e71a000	Deferred        libsm.so.6
ELF	7e730000-7e7cd000	Deferred        winex11<elf>
  \-PE	7e740000-7e7cd000	\               winex11
ELF	7e7f8000-7e81f000	Deferred        libexpat.so.1
ELF	7e81f000-7e84c000	Deferred        libfontconfig.so.1
ELF	7e84c000-7e862000	Deferred        libz.so.1
ELF	7e862000-7e8d9000	Deferred        libfreetype.so.6
ELF	7e8ef000-7e9d6000	Export          oleaut32<elf>
  \-PE	7e910000-7e9d6000	\               oleaut32
ELF	7e9d6000-7ea43000	Export          rpcrt4<elf>
  \-PE	7e9e0000-7ea43000	\               rpcrt4
ELF	7ea43000-7eb3d000	Export          ole32<elf>
  \-PE	7ea60000-7eb3d000	\               ole32
ELF	7eb3d000-7eb58000	Deferred        version<elf>
  \-PE	7eb40000-7eb58000	\               version
ELF	7eb58000-7ebae000	Deferred        advapi32<elf>
  \-PE	7eb60000-7ebae000	\               advapi32
ELF	7ebae000-7ec4f000	Deferred        gdi32<elf>
  \-PE	7ebc0000-7ec4f000	\               gdi32
ELF	7ec4f000-7ed9a000	Deferred        user32<elf>
  \-PE	7ec70000-7ed9a000	\               user32
ELF	7ed9a000-7ee62000	Deferred        comctl32<elf>
  \-PE	7eda0000-7ee62000	\               comctl32
ELF	7ee62000-7ee7b000	Deferred        libnsl.so.1
ELF	7ee7b000-7ee84000	Deferred        libnss_compat.so.2
ELF	7ee86000-7ee9a000	Deferred        lz32<elf>
  \-PE	7ee90000-7ee9a000	\               lz32
ELF	7efc4000-7efea000	Deferred        libm.so.6
ELF	7eff4000-7f000000	Deferred        libnss_files.so.2
ELF	f7c21000-f7c25000	Deferred        libdl.so.2
ELF	f7c25000-f7d88000	Deferred        libc.so.6
ELF	f7d89000-f7da2000	Deferred        libpthread.so.0
ELF	f7da3000-f7dae000	Deferred        libnss_nis.so.2
ELF	f7db8000-f7ef3000	Export          libwine.so.1
ELF	f7ef5000-f7f16000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000019 
	0000001a    0
0000001b 
	0000001c    0
0000001d (D) C:\windows\temp\WZSE13.TMP\DISK1\SETUP.EXE
	00000029    0
	0000001e    0 <==
00000021 
	0000002c    0
	0000002b    0
	0000002a    0
	00000028    0
	00000027    0
	00000026    0
	00000024    0
	00000023    0
	00000022    0
Backtrace:
=>0 0x7e9f65bd fill_delegated_proxy_table+0x4d() in rpcrt4 (0x0033e9bc)
  1 0x7e9f577b NdrDllGetClassObject+0x33b() in rpcrt4 (0x0033ea2c)
  2 0x7e9ba759 in oleaut32 (+0xaa759) (0x0033ea5c)
  3 0x7e91834b in oleaut32 (+0x834b) (0x0033ea9c)
  4 0x7e9308f4 in oleaut32 (+0x208f4) (0x0033eb3c)
  5 0x7ea990c4 in ole32 (+0x390c4) (0x0033ebfc)
  6 0x7ea99660 in ole32 (+0x39660) (0x0033ecac)
  7 0x7ea96ec5 CoUnmarshalInterface+0x195() in ole32 (0x0033ed2c)
  8 0x7e92b5d1 in oleaut32 (+0x1b5d1) (0x0033ed9c)
  9 0x7e92cb3f in oleaut32 (+0x1cb3f) (0x0033ee0c)
  10 0x7e92c438 in oleaut32 (+0x1c438) (0x0033ee7c)
  11 0x7e92c79a in oleaut32 (+0x1c79a) (0x0033eeec)
  12 0x7e92f5f9 in oleaut32 (+0x1f5f9) (0x0033efdc)
  13 0x0034004c (0x0033f16c)
  14 0x00403259 in setup (+0x3259) (0x0033f1c8)
  15 0x00402d4e in setup (+0x2d4e) (0x0033f88c)
  16 0x00402a07 in setup (+0x2a07) (0x0033fea4)
  17 0x0040254e in setup (+0x254e) (0x0033ff08)
  18 0x7b878690 in kernel32 (+0x58690) (0x0033ffe8)
  19 0xf7dbfde7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)


```

I've seen posts about a similar message that suggested using different video drivers.  I've used the 2.6.28 kernel drivers for my intel integrated card and also the downgraded drivers to no avail.

Since I had it working with the i386 version, it's either a 64 bit version issue or a problem with Wine since I installed the program before using version 1.1.20 and the current version is 1.1.23.
Any help would be greatly appreciated!
Rob

---

### Post by rmccarri on 2009-06-12
Hi everyone,
In a last ditch effort to get it to work, I downgraded to Win 1.1.19 and installed it.  It worked.  Then I upgraded back to the current version and it seems OK.

---

