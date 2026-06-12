---
title: "Cortex Command build 23"
date: 2009-06-08
forum: Wine
---

### Post by crazyfuturamanoob on 2009-06-08
I downloaded and installed CC build 23. All good.


When I tried to run it, it told me Microsoft.VC80.CRT was missing.

I found it from another application installation (blocktality) so I just copied it from there to CC directory.


Now it doesn't start, no error messages. This is probably DRM. I downloaded a crack from [_crack.ms_](http://www.crack.ms/cracks/search.crack?software=cortex+command&mode=AND)

But this crack doesn't work. It makes "page fault" and memory dump:
```

arho@arho-laptop:~/Games/Cortex Command$ wine Cortex\ Command.exe 
wine: Unhandled page fault on read access to 0x7c80003c at address 0x74ab57 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x7c80003c in 32-bit code (0x0074ab57).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0074ab57 ESP:0032fd88 EBP:0032feb0 EFLAGS:00010206(  R- --  I   - -P- )
 EAX:7c80003c EBX:7b8b6ff4 ECX:0032fec8 EDX:3cc6743c
 ESI:7ffdf000 EDI:00538167
Stack dump:
0x0032fd88:  00000000 00000000 00000000 00000000
0x0032fd98:  00000000 00000000 00000000 00000000
0x0032fda8:  00000000 00000000 00000000 00000000
0x0032fdb8:  00000000 00000000 00000000 00000000
0x0032fdc8:  00000000 00000000 00000000 00000000
0x0032fdd8:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x0074ab57 in cortex command (+0x34ab57) (0x0032feb0)
  1 0x006f60b5 in cortex command (+0x2f60b5) (0x0032ff04)
  2 0x00787822 in cortex command (+0x387822) (0x0032ffe8)
  3 0xf7dc1de7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0074ab57: movl	0x0(%eax),%eax
Modules:
Module	Address			Debug info	Name (78 modules)
PE	  330000-  3cd000	Deferred        libcurl
PE	  400000-  95a000	Export          cortex command
PE	10000000-10096000	Deferred        fmod
PE	78130000-781cb000	Deferred        msvcr80
ELF	7b800000-7b948000	Deferred        kernel32<elf>
  \-PE	7b820000-7b948000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
PE	7c420000-7c4a7000	Deferred        msvcp80
ELF	7e464000-7e479000	Deferred        midimap<elf>
  \-PE	7e470000-7e479000	\               midimap
ELF	7e479000-7e4b7000	Deferred        wineoss<elf>
  \-PE	7e480000-7e4b7000	\               wineoss
ELF	7e4b7000-7e4c0000	Deferred        libxcursor.so.1
ELF	7e4c0000-7e4c5000	Deferred        libxfixes.so.3
ELF	7e4c5000-7e4c9000	Deferred        libxcomposite.so.1
ELF	7e4c9000-7e4d1000	Deferred        libxrandr.so.2
ELF	7e4d1000-7e4db000	Deferred        libxrender.so.1
ELF	7e4db000-7e4e1000	Deferred        libxxf86vm.so.1
ELF	7e4e1000-7e4e4000	Deferred        libxinerama.so.1
ELF	7e4e4000-7e505000	Deferred        imm32<elf>
  \-PE	7e4f0000-7e505000	\               imm32
ELF	7e505000-7e50a000	Deferred        libxdmcp.so.6
ELF	7e50a000-7e524000	Deferred        libxcb.so.1
ELF	7e524000-7e528000	Deferred        libxau.so.6
ELF	7e528000-7e52d000	Deferred        libuuid.so.1
ELF	7e52d000-7e61c000	Deferred        libx11.so.6
ELF	7e61c000-7e62c000	Deferred        libxext.so.6
ELF	7e62c000-7e644000	Deferred        libice.so.6
ELF	7e644000-7e64d000	Deferred        libsm.so.6
ELF	7e658000-7e670000	Deferred        msacm32<elf>
  \-PE	7e660000-7e670000	\               msacm32
ELF	7e672000-7e70e000	Deferred        winex11<elf>
  \-PE	7e680000-7e70e000	\               winex11
ELF	7e74b000-7e772000	Deferred        libexpat.so.1
ELF	7e772000-7e79f000	Deferred        libfontconfig.so.1
ELF	7e79f000-7e7b5000	Deferred        libz.so.1
ELF	7e7b5000-7e82c000	Deferred        libfreetype.so.6
ELF	7e82c000-7e842000	Deferred        libresolv.so.2
ELF	7e867000-7e887000	Deferred        iphlpapi<elf>
  \-PE	7e870000-7e887000	\               iphlpapi
ELF	7e887000-7e8ad000	Deferred        msacm32<elf>
  \-PE	7e890000-7e8ad000	\               msacm32
ELF	7e8ad000-7e8db000	Deferred        ws2_32<elf>
  \-PE	7e8c0000-7e8db000	\               ws2_32
ELF	7e8db000-7e949000	Deferred        msvcrt<elf>
  \-PE	7e8f0000-7e949000	\               msvcrt
ELF	7e949000-7e9e0000	Deferred        winmm<elf>
  \-PE	7e950000-7e9e0000	\               winmm
ELF	7e9e0000-7ea2c000	Deferred        dsound<elf>
  \-PE	7e9f0000-7ea2c000	\               dsound
ELF	7ea2c000-7ea65000	Deferred        dinput<elf>
  \-PE	7ea30000-7ea65000	\               dinput
ELF	7ea65000-7ead1000	Deferred        rpcrt4<elf>
  \-PE	7ea70000-7ead1000	\               rpcrt4
ELF	7ead1000-7eb72000	Deferred        gdi32<elf>
  \-PE	7eae0000-7eb72000	\               gdi32
ELF	7eb72000-7ecbd000	Deferred        user32<elf>
  \-PE	7eb90000-7ecbd000	\               user32
ELF	7ecbd000-7edb8000	Deferred        ole32<elf>
  \-PE	7ece0000-7edb8000	\               ole32
ELF	7edb8000-7ee10000	Deferred        ddraw<elf>
  \-PE	7edc0000-7ee10000	\               ddraw
ELF	7ee10000-7ee66000	Deferred        advapi32<elf>
  \-PE	7ee20000-7ee66000	\               advapi32
ELF	7ef90000-7ef9c000	Deferred        libnss_files.so.2
ELF	7ef9c000-7efb5000	Deferred        libnsl.so.1
ELF	7efb5000-7efdb000	Deferred        libm.so.6
ELF	7efdd000-7eff8000	Deferred        wsock32<elf>
  \-PE	7efe0000-7eff8000	\               wsock32
ELF	f7c14000-f7c18000	Deferred        libdl.so.2
ELF	f7c18000-f7d7b000	Deferred        libc.so.6
ELF	f7d7c000-f7d95000	Deferred        libpthread.so.0
ELF	f7d95000-f7da0000	Deferred        libnss_nis.so.2
ELF	f7db1000-f7dba000	Deferred        libnss_compat.so.2
ELF	f7dba000-f7ef5000	Export          libwine.so.1
ELF	f7ef7000-f7f18000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\arho\Games\Cortex Command\Cortex Command.exe
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
00000019 
	0000001a    0
Backtrace:
=>0 0x0074ab57 in cortex command (+0x34ab57) (0x0032feb0)
  1 0x006f60b5 in cortex command (+0x2f60b5) (0x0032ff04)
  2 0x00787822 in cortex command (+0x387822) (0x0032ffe8)
  3 0xf7dc1de7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

Any way to get it working? Another crack that works?

---

### Post by asdfoo on 2009-06-09
which Wine version are you using? Try with atleast Wine 1.1.22, is there a demo to download somewhere please include a link

---

### Post by crazyfuturamanoob on 2009-06-09
```

arho@arho-laptop:~$ wine --version
wine-1.1.23

```

Got build 23 here: [http://www.datarealms.com/downloads/ccsetup23.exe](http://www.datarealms.com/downloads/ccsetup23.exe)

I also tried build 18, which is the last build without DRM. Works great, but it lacks a lot features and it has some bugs.

---

### Post by NightMKoder on 2009-06-09
Don't copy dlls mindlessly. Always a good idea to check winetricks first: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) . You need vcrun2005 & vcrun2005sp1 for safe measure.

---

### Post by crazyfuturamanoob on 2009-06-10
> **NightMKoder said:**
> Don't copy dlls mindlessly. Always a good idea to check winetricks first: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) . You need vcrun2005 & vcrun2005sp1 for safe measure.

I removed Microsoft.VC80.CRT directory and the files, and installed those with winetricks. CC quits still silently.

---

### Post by crazyfuturamanoob on 2009-06-10
I downloaded, installed and tested all test builds 18-23. 20-22 need crack to work.

---

### Post by Red_Kaos on 2010-01-12
has there been any progress on this?

---

