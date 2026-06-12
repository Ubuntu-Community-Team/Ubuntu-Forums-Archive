---
title: "unable to install mafia"
date: 2009-03-03
forum: Wine
---

### Post by dre_in_ham on 2009-03-03
Im unable to install Mafia on a fully updated Intrepid system.

**uname -a**
Linux waffe 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

**wine --version**
wine-1.1.16

**extracts from glxinfo**
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.1.8087 Release
OpenGL shading language version string: 1.20

When i run wine Mafia-Launcher.exe it displays the following in the terminal:

**wine MafiaLauncher.exe** 
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
wine: Unhandled page fault on write access to 0x00000000 at address 0xb7cfa697 (thread 0020), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0xb7cfa697).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7cfa697 ESP:0033fec0 EBP:0033fee0 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:7bc94ff4 ECX:3fffffff EDX:00000003
 ESI:7ffdf000 EDI:00000000
Stack dump:
0x0033fec0:  00401000 7bc6fcab 00000000 00000000
0x0033fed0:  ffffffff 0033fef4 7ee21245 00000003
0x0033fee0:  0033ffe8 0040201a 00000000 00000000
0x0033fef0:  ffffffff 004016f2 00000000 ffffffff
0x0033ff00:  00000000 004012d2 ffffffff 7b878700
0x0033ff10:  7ffdf000 00000000 00000000 00000000
Backtrace:
=>0 0xb7cfa697 memset+0x37() in libc.so.6 (0x0033fee0)
  1 0x0040201a in b2e (+0x201a) (0x0033ffe8)
  2 0xb7e11d97 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xb7cfa697 memset+0x37 in libc.so.6: repe stosl	%es:(%edi)
Modules:
Module	Address			Debug info	Name (61 modules)
PE	  400000-  405000	Export          b2e
ELF	7b800000-7b93f000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93f000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e3ab000-7e412000	Deferred        rpcrt4<elf>
  \-PE	7e3c0000-7e412000	\               rpcrt4
ELF	7e412000-7e524000	Deferred        ole32<elf>
  \-PE	7e430000-7e524000	\               ole32
ELF	7e54c000-7e57f000	Deferred        uxtheme<elf>
  \-PE	7e550000-7e57f000	\               uxtheme
ELF	7e57f000-7e588000	Deferred        libxcursor.so.1
ELF	7e588000-7e58d000	Deferred        libxfixes.so.3
ELF	7e58d000-7e591000	Deferred        libxcomposite.so.1
ELF	7e591000-7e598000	Deferred        libxrandr.so.2
ELF	7e598000-7e5a2000	Deferred        libxrender.so.1
ELF	7e5a2000-7e5a8000	Deferred        libxxf86vm.so.1
ELF	7e5a8000-7e5c9000	Deferred        imm32<elf>
  \-PE	7e5b0000-7e5c9000	\               imm32
ELF	7e5c9000-7e5ce000	Deferred        libxdmcp.so.6
ELF	7e5ce000-7e5e7000	Deferred        libxcb.so.1
ELF	7e5e7000-7e6d6000	Deferred        libx11.so.6
ELF	7e6d6000-7e6e5000	Deferred        libxext.so.6
ELF	7e6e5000-7e6fd000	Deferred        libice.so.6
ELF	7e6fd000-7e706000	Deferred        libsm.so.6
ELF	7e716000-7e7b2000	Deferred        winex11<elf>
  \-PE	7e720000-7e7b2000	\               winex11
ELF	7e809000-7e830000	Deferred        libexpat.so.1
ELF	7e830000-7e85d000	Deferred        libfontconfig.so.1
ELF	7e86d000-7e883000	Deferred        libz.so.1
ELF	7e883000-7e8f9000	Deferred        libfreetype.so.6
ELF	7e8f9000-7e9c0000	Deferred        comctl32<elf>
  \-PE	7e900000-7e9c0000	\               comctl32
ELF	7e9c0000-7ea15000	Deferred        advapi32<elf>
  \-PE	7e9d0000-7ea15000	\               advapi32
ELF	7ea15000-7eab6000	Deferred        gdi32<elf>
  \-PE	7ea30000-7eab6000	\               gdi32
ELF	7eab6000-7ec05000	Deferred        user32<elf>
  \-PE	7ead0000-7ec05000	\               user32
ELF	7ec05000-7ec63000	Deferred        shlwapi<elf>
  \-PE	7ec10000-7ec63000	\               shlwapi
ELF	7ec63000-7edf0000	Deferred        shell32<elf>
  \-PE	7ec70000-7edf0000	\               shell32
ELF	7edf0000-7ee5e000	Deferred        msvcrt<elf>
  \-PE	7ee00000-7ee5e000	\               msvcrt
ELF	7ee5e000-7ee78000	Deferred        crtdll<elf>
  \-PE	7ee60000-7ee78000	\               crtdll
ELF	7ee78000-7ee91000	Deferred        libnsl.so.1
ELF	7ee91000-7ee9a000	Deferred        libnss_compat.so.2
ELF	7ee9a000-7ee9d000	Deferred        libxinerama.so.1
ELF	7ee9d000-7eea0000	Deferred        libxcb-xlib.so.0
ELF	7efca000-7eff0000	Deferred        libm.so.6
ELF	7eff1000-7eff4000	Deferred        libxau.so.6
ELF	7eff4000-7f000000	Deferred        libnss_files.so.2
ELF	b7c71000-b7c7c000	Deferred        libnss_nis.so.2
ELF	b7c7e000-b7c82000	Deferred        libdl.so.2
ELF	b7c82000-b7de0000	Export          libc.so.6
ELF	b7de1000-b7dfa000	Deferred        libpthread.so.0
ELF	b7e0a000-b7f45000	Export          libwine.so.1
ELF	b7f47000-b7f64000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000c 
	0000001a    0
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000018    0
	00000015    0
	00000011    0
	00000010    0
00000016 
	0000001c    0
	0000001b    0
	00000019    0
	00000017    0
0000001f (D) C:\windows\temp\371.tmp\b2e.exe
	00000020    0 <==
00000021 
	00000022    0
00000025 
	00000026    0
Backtrace:
=>0 0xb7cfa697 memset+0x37() in libc.so.6 (0x0033fee0)
  1 0x0040201a in b2e (+0x201a) (0x0033ffe8)
  2 0xb7e11d97 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub



It shows the install menu but when i click install the menu disapears and nothing else happens. I have *mfc42.dll* in my system32 and system directories.

Please note i have searched google, the loki forums and elsewhere for help on this and have come up empty! Any suggestions? World of Warcraft runs on this system flawlessly!

Any ideas on what i should try next?

---

### Post by cogadh on 2009-03-03
You put the mfc42 in the directory, but did you apply an override for it in winecfg? Also, the comments in the WineHQ AppDB page for the game seem to indicate that you need to have VCrun6, not just the single mfc42.dll, installed in order to install the game:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2291](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2291)

---

### Post by dre_in_ham on 2009-03-04
Thanks for quick reply! I found this: 
*[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)*

which contains info on how to install vcrun6:
[I]wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
sh winetricks corefonts vcrun6[/I]

I will try winetricks (as well as the dll thing) tonight and report back :)

---

### Post by dre_in_ham on 2009-03-04
Hi,

i installed *vcrun6* with *winetricks* and still no go. Also tried after installing the *mfc40* and *mfc42* packages and still no go. Also tried adding them in the *wineconfig* program also without success.

crashing with:

[I]**wine MafiaLauncher.exe** 
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
wine: Unhandled page fault on write access to 0x00000000 at address 0xb7cf5697 (thread 0020), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0xb7cf5697).
[/I]

any further ideas

---

### Post by dre_in_ham on 2009-03-26
Ive posted this on the wine forums as well to see if they can help.
Will reply here once i have tested in Jaunty when it comes out...

---

