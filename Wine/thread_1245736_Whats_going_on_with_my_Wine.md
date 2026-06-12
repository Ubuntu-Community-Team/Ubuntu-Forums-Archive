---
title: "Whats going on with my Wine?"
date: 2009-08-20
forum: Wine
---

### Post by dividebyzer0 on 2009-08-20
I am really new to ubuntu and so I am just trying to find an answer to why this isnt working.

I installed wine and I am trying to run a .exe it is a cheat code editor program for my nintendo DS.. I tried right click>open with wine but it doesnt do anything. I opened the terminal and ran "wine (filename)" and it gave me an error saying MFC42.DLL was missing. I found that on google and put it in the folder of the .exe and then ran the same command.. it then gave me some crazy stuff that I didnt quite understand. 

before adding the DLL to the folder:
```
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\dividebyzer0\\Desktop\\Windows Applications\\CCe\\Cheat code editor\\Cheat Code Editor.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\dividebyzer0\\Desktop\\Windows Applications\\CCe\\Cheat code editor\\Cheat Code Editor.exe" failed, status c0000135

```After Adding it:
```
wine: Call from 0x7bc48af0 to unimplemented function MFC42.DLL.6625, aborting
wine: Unimplemented function MFC42.DLL.6625 called at address 0x7bc48af0 (thread 0009), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6625 called in 32-bit code (0x7bc48af0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc48af0 ESP:0032edbc EBP:0032ee20 EFLAGS:00000202(   - --  I   - - - )
 EAX:000019e1 EBX:7bc94ff4 ECX:0042a898 EDX:00000000
 ESI:0032edc8 EDI:0032ee40
Stack dump:
0x0032edbc:  00000000 00000009 00010036 80000100
0x0032edcc:  00000001 00000000 7bc48af0 00000002
0x0032eddc:  004094ac 000019e1 00000001 00000001
0x0032edec:  0032ee2c 5f423270 00010036 0000110d
0x0032edfc:  00000000 0032ee04 00000004 001391d8
0x0032ee0c:  00000000 00000000 00000000 7ec5e430
Backtrace:
=>0 0x7bc48af0 in ntdll (+0x38af0) (0x0032ee20)
  1 0x0033000f (0x0032fd10)
  2 0x00000001 (0x004087d8)
  3 0x00401560 in cheat code editor (+0x1560) (0x00406f9e)
  4 0x25ff0040 (0x80b425ff)
  5 0x00000000 (0x00000000)
0x7bc48af0: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (52 modules)
PE      400000-  82d000    Export          cheat code editor
PE    5f400000-5f4ed000    Deferred        mfc42
ELF    7b800000-7b96e000    Deferred        kernel32<elf>
  \-PE    7b820000-7b96e000    \               kernel32
ELF    7bc00000-7bcb1000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb1000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7e711000-7e744000    Deferred        uxtheme<elf>
  \-PE    7e720000-7e744000    \               uxtheme
ELF    7e76e000-7e777000    Deferred        libxcursor.so.1
ELF    7e777000-7e77c000    Deferred        libxfixes.so.3
ELF    7e77c000-7e780000    Deferred        libxcomposite.so.1
ELF    7e780000-7e788000    Deferred        libxrandr.so.2
ELF    7e788000-7e792000    Deferred        libxrender.so.1
ELF    7e792000-7e798000    Deferred        libxxf86vm.so.1
ELF    7e798000-7e79b000    Deferred        libxinerama.so.1
ELF    7e79b000-7e7bc000    Deferred        imm32<elf>
  \-PE    7e7a0000-7e7bc000    \               imm32
ELF    7e7bc000-7e7c1000    Deferred        libxdmcp.so.6
ELF    7e7c1000-7e7db000    Deferred        libxcb.so.1
ELF    7e7db000-7e7df000    Deferred        libxau.so.6
ELF    7e7df000-7e7e4000    Deferred        libuuid.so.1
ELF    7e7e4000-7e8d3000    Deferred        libx11.so.6
ELF    7e8d3000-7e8e3000    Deferred        libxext.so.6
ELF    7e8e3000-7e8fb000    Deferred        libice.so.6
ELF    7e8fb000-7e904000    Deferred        libsm.so.6
ELF    7e913000-7e9b2000    Deferred        winex11<elf>
  \-PE    7e920000-7e9b2000    \               winex11
ELF    7ea10000-7ea37000    Deferred        libexpat.so.1
ELF    7ea37000-7ea64000    Deferred        libfontconfig.so.1
ELF    7ea64000-7ea7a000    Deferred        libz.so.1
ELF    7ea7a000-7eaf1000    Deferred        libfreetype.so.6
ELF    7eb00000-7ebc8000    Deferred        comctl32<elf>
  \-PE    7eb10000-7ebc8000    \               comctl32
ELF    7ebc8000-7ed14000    Deferred        user32<elf>
  \-PE    7ebe0000-7ed14000    \               user32
ELF    7ed14000-7ed6b000    Deferred        advapi32<elf>
  \-PE    7ed20000-7ed6b000    \               advapi32
ELF    7ed6b000-7ee0d000    Deferred        gdi32<elf>
  \-PE    7ed80000-7ee0d000    \               gdi32
ELF    7ee0d000-7ee7c000    Deferred        msvcrt<elf>
  \-PE    7ee20000-7ee7c000    \               msvcrt
ELF    7efa6000-7efb2000    Deferred        libnss_files.so.2
ELF    7efb2000-7efcb000    Deferred        libnsl.so.1
ELF    7efcb000-7eff1000    Deferred        libm.so.6
ELF    7eff5000-7f000000    Deferred        libnss_nis.so.2
ELF    b7d05000-b7d0e000    Deferred        libnss_compat.so.2
ELF    b7d0f000-b7d13000    Deferred        libdl.so.2
ELF    b7d13000-b7e76000    Deferred        libc.so.6
ELF    b7e77000-b7e90000    Deferred        libpthread.so.0
ELF    b7e9f000-b7fdb000    Deferred        libwine.so.1
ELF    b7fdd000-b7ffb000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\dividebyzer0\Desktop\Windows Applications\CCe\Cheat code editor\Cheat Code Editor.exe
    00000009    0 <==
0000000e 
    00000018    0
    00000015    0
    00000014    0
    00000010    0
    0000000f    0
00000011 
    00000017    0
    00000016    0
    00000013    0
    00000012    0
00000019 
    0000001a    0
Backtrace:
=>0 0x7bc48af0 in ntdll (+0x38af0) (0x0032ee20)
  1 0x0033000f (0x0032fd10)
  2 0x00000001 (0x004087d8)
  3 0x00401560 in cheat code editor (+0x1560) (0x00406f9e)
  4 0x25ff0040 (0x80b425ff)
  5 0x00000000 (0x00000000)
wine: Call from 0x7bc48af0 to unimplemented function MFC42.DLL.6625, aborting
```uhh so yeah lol any help?? I am running Ubuntu 9.04

---

### Post by stinger30au on 2009-08-20
from memeory mfc42.dll can be installed using wine tricks

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by doas777 on 2009-08-20
usually my recomendation is to get a copy of the windows  version of the mfc file. then place it in the application directory (NOT winedrive\Windows\System32) and create a native override for that app in the wine config console.
[http://www.winehq.org/docs/wineusr-guide/config-wine-main](http://www.winehq.org/docs/wineusr-guide/config-wine-main)

---

### Post by dividebyzer0 on 2009-08-21
I actually found another version of the application I was trying to run, and it works fine, thanks!

---

