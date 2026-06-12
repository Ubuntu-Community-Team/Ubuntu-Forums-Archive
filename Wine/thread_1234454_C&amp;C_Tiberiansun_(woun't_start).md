---
title: "C&amp;C Tiberiansun (woun't start)"
date: 2009-08-07
forum: Wine
---

### Post by niiize on 2009-08-07
Ok, I've done what's adviced and read on wineHQ, C&C seem to work in general with no issues. In my case I beleve it might be a problem caused by acessability or something... 

When I try to run wine *c:/spel/tiberiansun/sun.exe* from console, as normal user, the startup logo apphears, then after a while it disaphears and a Windows "program error" alert pops up saying "*The program sun.exe has encountered a fatal error and has to terminate. We apologize for the inconviniance*" :) Then just general information on where to search for further information on Wine bugs etc. at appdb.winehq.org and so on. 

In the console the error message say:

[B]wine: Unhandled page fault on read access to 0x00000000 at address 0x411590 (thread 0043), starting debugger...
[/B]Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00411590).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00411590 ESP:0033fb18 EBP:0033fb24 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:00688bf0 ECX:00000000 EDX:00000000
 ESI:00405874 EDI:00688c74
Stack dump:
0x0033fb18:  0041b3cd 00000000 0033fed7 0033fe53
0x0033fb28:  004055d4 00000000 00000004 0042bd30
0x0033fb38:  4a7cdba9 00400000 7b865ff0 00000084
0x0033fb48:  000000b5 7bc61851 7b865100 7b820000
0x0033fb58:  7b866e50 0001003f 00000000 00000000
0x0033fb68:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x00411590 in game (+0x11590) (0x0033fb24)
  1 0x004055d4 in game (+0x55d4) (0x0033fe53)
0x00411590: movl    0x0(%ecx),%eax
Modules:
Module    Address            Debug info    Name (50 modules)
PE      400000-  441000    Export          game
PE    10000000-1000c000    Deferred        drvmgt
ELF    7b800000-7b95e000    Deferred        kernel32<elf>
  \-PE    7b820000-7b95e000    \               kernel32
ELF    7bc00000-7bcae000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcae000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7e8d0000-7e8d9000    Deferred        libxcursor.so.1
ELF    7e8d9000-7e8de000    Deferred        libxfixes.so.3
ELF    7e8de000-7e8e1000    Deferred        libxcomposite.so.1
ELF    7e8e1000-7e8e7000    Deferred        libxrandr.so.2
ELF    7e8e7000-7e8ef000    Deferred        libxrender.so.1
ELF    7e8ef000-7e8f4000    Deferred        libxxf86vm.so.1
ELF    7e8f4000-7e8f7000    Deferred        libxinerama.so.1
ELF    7e8f7000-7e916000    Deferred        imm32<elf>
  \-PE    7e900000-7e916000    \               imm32
ELF    7e916000-7e91b000    Deferred        libxdmcp.so.6
ELF    7e91b000-7e933000    Deferred        libxcb.so.1
ELF    7e933000-7e936000    Deferred        libxau.so.6
ELF    7e936000-7ea1d000    Deferred        libx11.so.6
ELF    7ea1d000-7ea2b000    Deferred        libxext.so.6
ELF    7ea2b000-7ea43000    Deferred        libice.so.6
ELF    7ea43000-7ea4b000    Deferred        libsm.so.6
ELF    7ea58000-7eaf2000    Deferred        winex11<elf>
  \-PE    7ea70000-7eaf2000    \               winex11
ELF    7eb00000-7eb21000    Deferred        libexpat.so.1
ELF    7eb21000-7eb4b000    Deferred        libfontconfig.so.1
ELF    7eb58000-7eb6d000    Deferred        libz.so.1
ELF    7eb6d000-7ebda000    Deferred        libfreetype.so.6
ELF    7ec05000-7ec18000    Deferred        lz32<elf>
  \-PE    7ec10000-7ec18000    \               lz32
ELF    7ec18000-7ec31000    Deferred        version<elf>
  \-PE    7ec20000-7ec31000    \               version
ELF    7ec31000-7ec86000    Deferred        advapi32<elf>
  \-PE    7ec40000-7ec86000    \               advapi32
ELF    7ec86000-7ed25000    Deferred        gdi32<elf>
  \-PE    7eca0000-7ed25000    \               gdi32
ELF    7ed25000-7ee6b000    Deferred        user32<elf>
  \-PE    7ed40000-7ee6b000    \               user32
ELF    7ee6b000-7ee76000    Deferred        libnss_files.so.2
ELF    7ee76000-7ee80000    Deferred        libnss_nis.so.2
ELF    7ee80000-7ee98000    Deferred        libnsl.so.1
ELF    7ee98000-7eea1000    Deferred        libnss_compat.so.2
ELF    7efce000-7eff3000    Deferred        libm.so.6
ELF    7eff3000-7eff5000    Deferred        libxcb-xlib.so.0
ELF    b7c71000-b7c75000    Deferred        libdl.so.2
ELF    b7c75000-b7dc4000    Deferred        libc.so.6
ELF    b7dc5000-b7ddd000    Deferred        libpthread.so.0
ELF    b7dea000-b7f25000    Deferred        libwine.so.1
ELF    b7f27000-b7f43000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e 
    00000020    0
    00000014    0
    00000010    0
    0000000f    0
00000011 
    00000017    0
    00000016    0
    00000013    0
    00000012    0
0000001a 
    0000001b    0
0000001d 
    00000022    0
    0000001f    0
    0000001e    0
00000025 
    00000026    0
0000002f 
    00000030    0
0000003b 
    0000003c    0
0000000b 
    0000000d    0
00000021 
    00000015    0
0000003e 
    00000039    0
0000000c 
    00000045    0
00000019 
    00000009    0
00000032 
    00000027    0
0000003a 
    0000002a    0
00000040 
    00000036    0
0000003d 
    00000031    0
00000033 (D) C:\spel\tiberiansun\game.exe
    00000043    0 <==
0000002d 
    00000046    0
Backtrace:
=>0 0x00411590 in game (+0x11590) (0x0033fb24)
  1 0x004055d4 in game (+0x55d4) (0x0033fe53)


If I try sudo I get:
wine: /home/niiize/.wine is not owned by you

And as superuser:
wine: cannot find 'c:/spel/tiberiansun/sun.exe'


Something that might be of importance to trace the problem is that the installation went fine with no obstacles, and that was fullscreen graphics mode with sound and all.

Here are my Wine settings:

**Windows-version: **
Windows NT4.0
**Sound: **
ALSA Drive
**Decivemapping:**
C: ../drive_c
D: /media/cdrom0
H: /home/niiize
Z: /




Thanx, any idéas

---

