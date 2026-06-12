---
title: "Blackberry Software in Ubuntu under Wine?"
date: 2008-12-18
forum: Wine
---

### Post by variableenigma on 2008-12-18
I just got my first RIM Blackberry (the Curve 8330), and I'm wondering if there's any way to use the software that comes along with it in Ubuntu. I've done a little searching on the subject, and I can't seem to find anything that addresses this particular problem..

When I try to run the start.exe file on the CDrom, I get this output:

```
amanda@amanda-laptop:~$ cd /media/cdrom0
amanda@amanda-laptop:/media/cdrom0$ wine start.exe
fixme:reg:GetNativeSystemInfo (0x32fe64) using GetSystemInfo()
err:ole:CoGetClassObject class {00000507-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000507-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject no class object {00000507-0000-0010-8000-00aa006d2ea4} could be created for context 0x5
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b844e10 (thread 0025), starting debugger...
First chance exception: 0xc0000025 in 32-bit code (0x7bc3bedc).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc3bedc ESP:0032f534 EBP:0032f598 EFLAGS:00200282(   - 00      - -IS1)
 EAX:0032f540 EBX:7bc8d624 ECX:00110050 EDX:00000000
 ESI:0032f91c EDI:0032f5a4
Stack dump:
0x0032f534:  004023ff 0000007b 0032f578 c0000025
0x0032f544:  00000001 0032f91c 0032f9b0 00000000
0x0032f554:  00c51e14 00405185 00c4f4f0 0032f578
0x0032f564:  004051c8 00c51e10 00c51e14 0057a8f4
0x0032f574:  00407931 6f727245 72632072 69746165
0x0032f584:  6f20676e 63656a62 20202e74 7bc3be90
Backtrace:
=>1 0x7bc3bedc __regs_RtlRaiseException+0x4c() in ntdll (0x0032f598)
  2 0x7bc7ac93 in ntdll (+0x6ac93) (0x0032f8f8)
  3 0x7bc3b5d6 RtlRaiseException+0x6() in ntdll (0x0032f970)
  4 0x0057dddf in start (+0x17dddf) (0x0032f9b0)
  5 0x00581e07 in start (+0x181e07) (0x0032f9e0)
  6 0x00582a7e in start (+0x182a7e) (0x0032f9f4)
  7 0x0058a3cc in start (+0x18a3cc) (0x0032fa18)
  8 0x00425084 in start (+0x25084) (0x0032fa44)
  9 0x004252b2 in start (+0x252b2) (0x0032fa98)
  10 0x004254fe in start (+0x254fe) (0x0032fac4)
  11 0x0042543d in start (+0x2543d) (0x0032fae0)
  12 0x00429c36 in start (+0x29c36) (0x0032fb10)
  13 0x0046e25a in start (+0x6e25a) (0x0032fb30)
  14 0x0042622c in start (+0x2622c) (0x0032fbb0)
  15 0x004239cf in start (+0x239cf) (0x0032fbd0)
  16 0x0041ff84 in start (+0x1ff84) (0x0032fbf4)
  17 0x0042010e in start (+0x2010e) (0x0032fd14)
  18 0x0042019f in start (+0x2019f) (0x0032fd44)
  19 0x004afcd6 in start (+0xafcd6) (0x0032fe98)
  20 0x004753b4 in start (+0x753b4) (0x0032febc)
  21 0x006e25bc in start (+0x2e25bc) (0x0032ff08)
  22 0x7b877c07 in kernel32 (+0x57c07) (0x0032ffe8)
0x7bc3bedc __regs_RtlRaiseException+0x4c in ntdll: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (113 modules)
PE	  400000-  a11000	Export          start
ELF	7b800000-7b93b000	Export          kernel32<elf>
  \-PE	7b820000-7b93b000	\               kernel32
ELF	7bc00000-7bca9000	Export          ntdll<elf>
  \-PE	7bc10000-7bca9000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7dc19000-7dc8e000	Deferred        crypt32<elf>
  \-PE	7dc20000-7dc8e000	\               crypt32
ELF	7dc8e000-7dca1000	Deferred        olepro32<elf>
  \-PE	7dc90000-7dca1000	\               olepro32
ELF	7dca1000-7dcc8000	Deferred        msacm32<elf>
  \-PE	7dcb0000-7dcc8000	\               msacm32
ELF	7dcc8000-7dcdf000	Deferred        msacm32<elf>
  \-PE	7dcd0000-7dcdf000	\               msacm32
ELF	7dcdf000-7dd2f000	Deferred        libpulse.so.0
ELF	7dd2f000-7dd43000	Deferred        midimap<elf>
  \-PE	7dd30000-7dd43000	\               midimap
ELF	7dd43000-7dd4c000	Deferred        librt.so.1
ELF	7dd4c000-7de14000	Deferred        libasound.so.2
ELF	7de14000-7de49000	Deferred        winealsa<elf>
  \-PE	7de20000-7de49000	\               winealsa
ELF	7de49000-7de4d000	Deferred        libgpg-error.so.0
ELF	7de4d000-7deb6000	Deferred        libgcrypt.so.11
ELF	7deb6000-7dec8000	Deferred        libtasn1.so.3
ELF	7dec8000-7ded1000	Deferred        libkrb5support.so.0
ELF	7ded1000-7df03000	Deferred        libcrypt.so.1
ELF	7df03000-7dfa0000	Deferred        libgnutls.so.26
ELF	7dfa0000-7dfc4000	Deferred        libk5crypto.so.3
ELF	7dfc4000-7e056000	Deferred        libkrb5.so.3
ELF	7e056000-7e080000	Deferred        libgssapi_krb5.so.2
ELF	7e080000-7e0b6000	Deferred        libcups.so.2
ELF	7e0bf000-7e0c3000	Deferred        libcap.so.1
ELF	7e0c3000-7e0ca000	Deferred        libasound_module_pcm_pulse.so
ELF	7e116000-7e149000	Deferred        uxtheme<elf>
  \-PE	7e120000-7e149000	\               uxtheme
ELF	7e149000-7e152000	Deferred        libxcursor.so.1
ELF	7e152000-7e157000	Deferred        libxfixes.so.3
ELF	7e157000-7e15b000	Deferred        libxcomposite.so.1
ELF	7e15b000-7e162000	Deferred        libxrandr.so.2
ELF	7e162000-7e16c000	Deferred        libxrender.so.1
ELF	7e16c000-7e172000	Deferred        libxxf86vm.so.1
ELF	7e172000-7e175000	Deferred        libxinerama.so.1
ELF	7e175000-7e195000	Deferred        imm32<elf>
  \-PE	7e180000-7e195000	\               imm32
ELF	7e195000-7e19a000	Deferred        libxdmcp.so.6
ELF	7e19a000-7e1b3000	Deferred        libxcb.so.1
ELF	7e1b3000-7e2a2000	Deferred        libx11.so.6
ELF	7e2a2000-7e2b1000	Deferred        libxext.so.6
ELF	7e2b1000-7e2c9000	Deferred        libice.so.6
ELF	7e2c9000-7e2d2000	Deferred        libsm.so.6
ELF	7e2d3000-7e2d7000	Deferred        libkeyutils.so.1
ELF	7e2e0000-7e2e4000	Deferred        libcom_err.so.2
ELF	7e2e6000-7e37f000	Deferred        winex11<elf>
  \-PE	7e2f0000-7e37f000	\               winex11
ELF	7e3d4000-7e3fb000	Deferred        libexpat.so.1
ELF	7e3fb000-7e428000	Deferred        libfontconfig.so.1
ELF	7e428000-7e43e000	Deferred        libz.so.1
ELF	7e43e000-7e4b4000	Deferred        libfreetype.so.6
ELF	7e4b5000-7e4b8000	Deferred        libxcb-xlib.so.0
ELF	7e4b8000-7e4bb000	Deferred        libxau.so.6
ELF	7e4c8000-7e4f4000	Deferred        ws2_32<elf>
  \-PE	7e4d0000-7e4f4000	\               ws2_32
ELF	7e4f4000-7e50e000	Deferred        wsock32<elf>
  \-PE	7e500000-7e50e000	\               wsock32
ELF	7e50e000-7e5a0000	Deferred        winmm<elf>
  \-PE	7e520000-7e5a0000	\               winmm
ELF	7e5a0000-7e5b9000	Deferred        version<elf>
  \-PE	7e5b0000-7e5b9000	\               version
ELF	7e5b9000-7e5db000	Deferred        mpr<elf>
  \-PE	7e5c0000-7e5db000	\               mpr
ELF	7e5db000-7e62a000	Deferred        wininet<elf>
  \-PE	7e5e0000-7e62a000	\               wininet
ELF	7e62a000-7e669000	Deferred        urlmon<elf>
  \-PE	7e630000-7e669000	\               urlmon
ELF	7e669000-7e750000	Deferred        oleaut32<elf>
  \-PE	7e680000-7e750000	\               oleaut32
ELF	7e750000-7e7b5000	Deferred        rpcrt4<elf>
  \-PE	7e760000-7e7b5000	\               rpcrt4
ELF	7e7b5000-7e8c4000	Deferred        ole32<elf>
  \-PE	7e7d0000-7e8c4000	\               ole32
ELF	7e8c4000-7e8d8000	Deferred        libresolv.so.2
ELF	7e8d8000-7e8ec000	Deferred        lz32<elf>
  \-PE	7e8e0000-7e8ec000	\               lz32
ELF	7e8ec000-7e90b000	Deferred        iphlpapi<elf>
  \-PE	7e8f0000-7e90b000	\               iphlpapi
ELF	7e90b000-7e91e000	Deferred        icmp<elf>
  \-PE	7e910000-7e91e000	\               icmp
ELF	7e91e000-7e953000	Deferred        winspool<elf>
  \-PE	7e930000-7e953000	\               winspool
ELF	7e953000-7e9ae000	Deferred        shlwapi<elf>
  \-PE	7e960000-7e9ae000	\               shlwapi
ELF	7e9ae000-7ead9000	Deferred        shell32<elf>
  \-PE	7e9c0000-7ead9000	\               shell32
ELF	7ead9000-7eb85000	Deferred        comdlg32<elf>
  \-PE	7eae0000-7eb85000	\               comdlg32
ELF	7eb85000-7ec23000	Deferred        gdi32<elf>
  \-PE	7eba0000-7ec23000	\               gdi32
ELF	7ec23000-7ed6c000	Deferred        user32<elf>
  \-PE	7ec40000-7ed6c000	\               user32
ELF	7ed6c000-7ee2d000	Deferred        comctl32<elf>
  \-PE	7ed80000-7ee2d000	\               comctl32
ELF	7ee2d000-7ee81000	Deferred        advapi32<elf>
  \-PE	7ee40000-7ee81000	\               advapi32
ELF	7efa1000-7efad000	Deferred        libnss_files.so.2
ELF	7efad000-7efc6000	Deferred        libnsl.so.1
ELF	7efc6000-7efec000	Deferred        libm.so.6
ELF	7efec000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7e19000-b7e1d000	Deferred        libdl.so.2
ELF	b7e1d000-b7f7b000	Deferred        libc.so.6
ELF	b7f7c000-b7f95000	Deferred        libpthread.so.0
ELF	b7fa9000-b80df000	Deferred        libwine.so.1
ELF	b80e1000-b80fe000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000019    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	0000001b    0
	00000018    0
	00000017    0
0000001c 
	0000001d    0
0000001e 
	0000001f    0
00000024 (D) D:\start.exe
	00000025    0 <==
Backtrace:
=>1 0x7bc3bedc __regs_RtlRaiseException+0x4c() in ntdll (0x0032f598)
  2 0x7bc7ac93 in ntdll (+0x6ac93) (0x0032f8f8)
  3 0x7bc3b5d6 RtlRaiseException+0x6() in ntdll (0x0032f970)
  4 0x0057dddf in start (+0x17dddf) (0x0032f9b0)
  5 0x00581e07 in start (+0x181e07) (0x0032f9e0)
  6 0x00582a7e in start (+0x182a7e) (0x0032f9f4)
  7 0x0058a3cc in start (+0x18a3cc) (0x0032fa18)
  8 0x00425084 in start (+0x25084) (0x0032fa44)
  9 0x004252b2 in start (+0x252b2) (0x0032fa98)
  10 0x004254fe in start (+0x254fe) (0x0032fac4)
  11 0x0042543d in start (+0x2543d) (0x0032fae0)
  12 0x00429c36 in start (+0x29c36) (0x0032fb10)
  13 0x0046e25a in start (+0x6e25a) (0x0032fb30)
  14 0x0042622c in start (+0x2622c) (0x0032fbb0)
  15 0x004239cf in start (+0x239cf) (0x0032fbd0)
  16 0x0041ff84 in start (+0x1ff84) (0x0032fbf4)
  17 0x0042010e in start (+0x2010e) (0x0032fd14)
  18 0x0042019f in start (+0x2019f) (0x0032fd44)
  19 0x004afcd6 in start (+0xafcd6) (0x0032fe98)
  20 0x004753b4 in start (+0x753b4) (0x0032febc)
  21 0x006e25bc in start (+0x2e25bc) (0x0032ff08)
  22 0x7b877c07 in kernel32 (+0x57c07) (0x0032ffe8)
```

A box also pops up that says: 

```
Application Error
Exception EAccessViolation in module start.exe at 00000000.
Access violation at address 00000000. Read of address 00000000.
```


What do we think?

---

### Post by Darrena on 2008-12-18
At this point you don't need to use that software.   Look for Barry in Synaptic or download the latest version from:
[http://www.netdirect.ca/software/packages/barry/](http://www.netdirect.ca/software/packages/barry/)

From the website:
> Today, it is possible to:

    * charge your Blackberry's battery from your USB port
    * retrieve Address Book, Email, Calendar, Service Book, Memos, Tasks, PIN Messages, Saved Email, and Folders
    * export Address Book contacts in text or LDAP LDIF format
    * make full data backups and restores of your device using a GUI
    * synchronize contacts and calendar items using the OpenSync framework
    * use the Blackberry as a modem


---

### Post by variableenigma on 2008-12-18
Oooh.. Maybe I wasn't finding the information I was looking for because I didn't know what I was looking for.. haha, I'll take a look at Barry, thanks :)

---

