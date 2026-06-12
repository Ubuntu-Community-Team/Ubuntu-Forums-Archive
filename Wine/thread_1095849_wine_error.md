---
title: "wine error"
date: 2009-03-14
forum: Wine
---

### Post by tubunu on 2009-03-14
I'm trying to run a program under wine, but it gives me errors. I'm running the latest wine 1.1.17. Basically the error reads: 

```
 wine start.exe
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/user/.wine' has been updated.
err:ole:CoGetClassObject class {00000507-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000507-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject no class object {00000507-0000-0010-8000-00aa006d2ea4} could be created for context 0x5
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b843a00 (thread 0009), starting debugger...
First chance exception: 0xc0000025 in 32-bit code (0x7bc3c6fc).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc3c6fc ESP:0032f534 EBP:0032f598 EFLAGS:00200282(   - 00      - -IS1)
 EAX:0032f540 EBX:7bc914c8 ECX:00110054 EDX:00000000
 ESI:0032f91c EDI:0032f5a4
Stack dump:
0x0032f534:  0032f54c 0000007b 0032f578 c0000025
0x0032f544:  00000001 0032f91c 0032f9b0 00000000
0x0032f554:  00b75624 00405185 00b75638 0032f578
0x0032f564:  004051c8 00b75620 00b75624 0057ab78
0x0032f574:  00407931 6f727245 72632072 69746165
0x0032f584:  6f20676e 63656a62 20202e74 7b8b2818
Backtrace:
=>0 0x7bc3c6fc __regs_RtlRaiseException+0x4c() in ntdll (0x0032f598)
  1 0x7bc7f75e in ntdll (+0x6f75e) (0x0032f8f4)
  2 0x7bc3bc2c RtlUnwind() in ntdll (0x0032f970)
  3 0x0057e063 in start (+0x17e063) (0x0032f9b0)
  4 0x0058208b in start (+0x18208b) (0x0032f9e0)
  5 0x00582d02 in start (+0x182d02) (0x0032f9f4)
  6 0x0058a650 in start (+0x18a650) (0x0032fa18)
  7 0x004253a4 in start (+0x253a4) (0x0032fa44)
  8 0x004255d2 in start (+0x255d2) (0x0032fa98)
  9 0x0042581e in start (+0x2581e) (0x0032fac4)
  10 0x0042575d in start (+0x2575d) (0x0032fae0)
  11 0x00429f56 in start (+0x29f56) (0x0032fb10)
  12 0x0046e57a in start (+0x6e57a) (0x0032fb30)
  13 0x0042654c in start (+0x2654c) (0x0032fbb0)
  14 0x00423cef in start (+0x23cef) (0x0032fbd0)
  15 0x004202a4 in start (+0x202a4) (0x0032fbf4)
  16 0x0042042e in start (+0x2042e) (0x0032fd14)
  17 0x004204bf in start (+0x204bf) (0x0032fd44)
  18 0x004afe7a in start (+0xafe7a) (0x0032fe98)
  19 0x004756d4 in start (+0x756d4) (0x0032febc)
  20 0x006de43f in start (+0x2de43f) (0x0032ff08)
  21 0x7b8769c9 in kernel32 (+0x569c9) (0x0032ffe8)
0x7bc3c6fc __regs_RtlRaiseException+0x4c in ntdll: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (113 modules)
PE	  400000-  93d000	Export          start
ELF	7b800000-7b939000	Export          kernel32<elf>
  \-PE	7b820000-7b939000	\               kernel32
ELF	7bc00000-7bcad000	Export          ntdll<elf>
  \-PE	7bc10000-7bcad000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d451000-7d4d1000	Deferred        crypt32<elf>
  \-PE	7d460000-7d4d1000	\               crypt32
ELF	7d4d1000-7d4ed000	Deferred        appwiz.cpl.so
PE	7d4e0000-7d4ed000	Deferred        appwiz.cpl
ELF	7d4ed000-7d500000	Deferred        olepro32<elf>
  \-PE	7d4f0000-7d500000	\               olepro32
ELF	7d500000-7d525000	Deferred        msacm32<elf>
  \-PE	7d510000-7d525000	\               msacm32
ELF	7d525000-7d53c000	Deferred        msacm32<elf>
  \-PE	7d530000-7d53c000	\               msacm32
ELF	7dd3d000-7dd8b000	Deferred        libpulse.so.0
ELF	7dd8b000-7dd9f000	Deferred        midimap<elf>
  \-PE	7dd90000-7dd9f000	\               midimap
ELF	7dd9f000-7dda8000	Deferred        librt.so.1
ELF	7dda8000-7de68000	Deferred        libasound.so.2
ELF	7de68000-7de9d000	Deferred        winealsa<elf>
  \-PE	7de70000-7de9d000	\               winealsa
ELF	7de9d000-7dea1000	Deferred        libgpg-error.so.0
ELF	7dea1000-7deee000	Deferred        libgcrypt.so.11
ELF	7deee000-7defe000	Deferred        libtasn1.so.3
ELF	7defe000-7df06000	Deferred        libkrb5support.so.0
ELF	7df06000-7df38000	Deferred        libcrypt.so.1
ELF	7df38000-7dfae000	Deferred        libgnutls.so.13
ELF	7dfae000-7dfd1000	Deferred        libk5crypto.so.3
ELF	7dfd1000-7e05e000	Deferred        libkrb5.so.3
ELF	7e05e000-7e087000	Deferred        libgssapi_krb5.so.2
ELF	7e087000-7e0ba000	Deferred        libcups.so.2
ELF	7e0c4000-7e0c8000	Deferred        libcap.so.1
ELF	7e0c8000-7e0ce000	Deferred        libasound_module_pcm_pulse.so
ELF	7e11a000-7e14d000	Deferred        uxtheme<elf>
  \-PE	7e120000-7e14d000	\               uxtheme
ELF	7e14d000-7e156000	Deferred        libxcursor.so.1
ELF	7e156000-7e15b000	Deferred        libxfixes.so.3
ELF	7e15b000-7e15e000	Deferred        libxcomposite.so.1
ELF	7e15e000-7e164000	Deferred        libxrandr.so.2
ELF	7e164000-7e16c000	Deferred        libxrender.so.1
ELF	7e16c000-7e171000	Deferred        libxxf86vm.so.1
ELF	7e171000-7e174000	Deferred        libxinerama.so.1
ELF	7e174000-7e194000	Deferred        imm32<elf>
  \-PE	7e180000-7e194000	\               imm32
ELF	7e194000-7e199000	Deferred        libxdmcp.so.6
ELF	7e199000-7e1b1000	Deferred        libxcb.so.1
ELF	7e1b1000-7e1b3000	Deferred        libxcb-xlib.so.0
ELF	7e1b3000-7e29a000	Deferred        libx11.so.6
ELF	7e29a000-7e2a8000	Deferred        libxext.so.6
ELF	7e2a8000-7e2c0000	Deferred        libice.so.6
ELF	7e2c0000-7e2c8000	Deferred        libsm.so.6
ELF	7e2ca000-7e2cd000	Deferred        libkeyutils.so.1
ELF	7e2d7000-7e2da000	Deferred        libcom_err.so.2
ELF	7e2dc000-7e375000	Deferred        winex11<elf>
  \-PE	7e2f0000-7e375000	\               winex11
ELF	7e3ba000-7e3db000	Deferred        libexpat.so.1
ELF	7e3db000-7e405000	Deferred        libfontconfig.so.1
ELF	7e405000-7e41a000	Deferred        libz.so.1
ELF	7e41a000-7e487000	Deferred        libfreetype.so.6
ELF	7e487000-7e49a000	Deferred        libresolv.so.2
ELF	7e49b000-7e49e000	Deferred        libxau.so.6
ELF	7e4ae000-7e4cc000	Deferred        iphlpapi<elf>
  \-PE	7e4b0000-7e4cc000	\               iphlpapi
ELF	7e4cc000-7e4f9000	Deferred        ws2_32<elf>
  \-PE	7e4d0000-7e4f9000	\               ws2_32
ELF	7e4f9000-7e513000	Deferred        wsock32<elf>
  \-PE	7e500000-7e513000	\               wsock32
ELF	7e513000-7e5a5000	Deferred        winmm<elf>
  \-PE	7e520000-7e5a5000	\               winmm
ELF	7e5a5000-7e5b8000	Deferred        lz32<elf>
  \-PE	7e5b0000-7e5b8000	\               lz32
ELF	7e5b8000-7e5d1000	Deferred        version<elf>
  \-PE	7e5c0000-7e5d1000	\               version
ELF	7e5d1000-7e5f3000	Deferred        mpr<elf>
  \-PE	7e5e0000-7e5f3000	\               mpr
ELF	7e5f3000-7e644000	Deferred        wininet<elf>
  \-PE	7e600000-7e644000	\               wininet
ELF	7e644000-7e683000	Deferred        urlmon<elf>
  \-PE	7e650000-7e683000	\               urlmon
ELF	7e683000-7e765000	Deferred        oleaut32<elf>
  \-PE	7e6a0000-7e765000	\               oleaut32
ELF	7e765000-7e7ca000	Deferred        rpcrt4<elf>
  \-PE	7e770000-7e7ca000	\               rpcrt4
ELF	7e7ca000-7e8bd000	Deferred        ole32<elf>
  \-PE	7e7e0000-7e8bd000	\               ole32
ELF	7e8bd000-7e8f2000	Deferred        winspool<elf>
  \-PE	7e8c0000-7e8f2000	\               winspool
ELF	7e8f2000-7e94d000	Deferred        shlwapi<elf>
  \-PE	7e900000-7e94d000	\               shlwapi
ELF	7e94d000-7ead9000	Deferred        shell32<elf>
  \-PE	7e960000-7ead9000	\               shell32
ELF	7ead9000-7eb89000	Deferred        comdlg32<elf>
  \-PE	7eae0000-7eb89000	\               comdlg32
ELF	7eb89000-7ec27000	Deferred        gdi32<elf>
  \-PE	7eba0000-7ec27000	\               gdi32
ELF	7ec27000-7ed6e000	Deferred        user32<elf>
  \-PE	7ec40000-7ed6e000	\               user32
ELF	7ed6e000-7ee30000	Deferred        comctl32<elf>
  \-PE	7ed80000-7ee30000	\               comctl32
ELF	7ee30000-7ee84000	Deferred        advapi32<elf>
  \-PE	7ee40000-7ee84000	\               advapi32
ELF	7efa4000-7efaf000	Deferred        libnss_files.so.2
ELF	7efaf000-7efc7000	Deferred        libnsl.so.1
ELF	7efc7000-7efec000	Deferred        libm.so.6
ELF	7efed000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7c56000-b7c5a000	Deferred        libdl.so.2
ELF	b7c5a000-b7da9000	Deferred        libc.so.6
ELF	b7daa000-b7dc2000	Deferred        libpthread.so.0
ELF	b7dd6000-b7f11000	Deferred        libwine.so.1
ELF	b7f13000-b7f2f000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\start.exe
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
Backtrace:
=>0 0x7bc3c6fc __regs_RtlRaiseException+0x4c() in ntdll (0x0032f598)
  1 0x7bc7f75e in ntdll (+0x6f75e) (0x0032f8f4)
  2 0x7bc3bc2c RtlUnwind() in ntdll (0x0032f970)
  3 0x0057e063 in start (+0x17e063) (0x0032f9b0)
  4 0x0058208b in start (+0x18208b) (0x0032f9e0)
  5 0x00582d02 in start (+0x182d02) (0x0032f9f4)
  6 0x0058a650 in start (+0x18a650) (0x0032fa18)
  7 0x004253a4 in start (+0x253a4) (0x0032fa44)
  8 0x004255d2 in start (+0x255d2) (0x0032fa98)
  9 0x0042581e in start (+0x2581e) (0x0032fac4)
  10 0x0042575d in start (+0x2575d) (0x0032fae0)
  11 0x00429f56 in start (+0x29f56) (0x0032fb10)
  12 0x0046e57a in start (+0x6e57a) (0x0032fb30)
  13 0x0042654c in start (+0x2654c) (0x0032fbb0)
  14 0x00423cef in start (+0x23cef) (0x0032fbd0)
  15 0x004202a4 in start (+0x202a4) (0x0032fbf4)
  16 0x0042042e in start (+0x2042e) (0x0032fd14)
  17 0x004204bf in start (+0x204bf) (0x0032fd44)
  18 0x004afe7a in start (+0xafe7a) (0x0032fe98)
  19 0x004756d4 in start (+0x756d4) (0x0032febc)
  20 0x006de43f in start (+0x2de43f) (0x0032ff08)
  21 0x7b8769c9 in kernel32 (+0x569c9) (0x0032ffe8)

```

The program uses flash, could this be the problem?

---

### Post by hikaricore on 2009-03-14
Please provide more info so that someone might actually be able to help.
At this point we don't even know what program you're trying to run.

---

### Post by tubunu on 2009-03-14
It's a maths program, it's not in WineHQ app database, it's one of those programs you get with some magazines.

---

### Post by tubunu on 2009-03-15
OK, I've just found out this CD I'm trying to install the program from has a copy protection in the form of a blank space (visible on the recorded side of the CD). Could that be bypassed somehow? The program works fine under Windows, so how come Wine cannot open it?

---

### Post by alex.rayu on 2009-03-15
Sometimes this happens.

---

### Post by aaronb on 2009-03-15
> **tubunu said:**
> It's a maths program, it's not in WineHQ app database, it's one of those programs you get with some magazines.

What is the name and version of the maths program?

---

