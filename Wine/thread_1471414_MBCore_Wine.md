---
title: "MBCore Wine"
date: 2010-05-03
forum: Wine
---

### Post by tjdevens on 2010-05-03
Hi. I recently switched to Ubuntu (mostly on purpose).

I've been poking around and learning my way, and I have a little understanding of what's going on. All in all I'm glad I switched, I'm enjoying how cleanly my pc is running and I really like all the features. 

However - A big part of my switching over involved my interest in MUDs and the like, and there lies the problem. I use Tinyfugue (which is not the problem) but I connect through a 'middle man' program called MBCore, which is as far as I know a small program privately developed and with no port to this OS. After poking around more, I learned that I can use Wine to run MBCore, and have the program up and running fine.

This is where I get lost - MBCore utilizes some .dll files that load up the various modules - without these it's not doing much of anything. The program runs fine until it encounters and attempts to load one of these files, after which it crashes. 

I would really appreciate some help getting this up and running, it's pretty much a big roadblock in my Ubuntu Experience and I'd like to remove it and continue enjoying it!

Here's what happens when I run from terminal

```
cariv@TJs-Computer:~/Desktop/MBCore$ wine mb-core.exe
wine: Unhandled page fault on read access to 0x0000001c at address 0x6833dc2d (thread 0039), starting debugger...
Unhandled exception: page fault on read access to 0x0000001c in 32-bit code (0x6833dc2d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6833dc2d ESP:0067e970 EBP:0067e998 EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000000 EBX:68364ff4 ECX:00110064 EDX:00000000
 ESI:00000000 EDI:00401240
Stack dump:
0x0067e970:  7ffdf000 00401240 0067e998 6833fc6c
0x0067e980:  678aa1ab 678a9aa9 0067e998 00137f60
0x0067e990:  7ffdf000 00401240 0067fb08 67889684
0x0067e9a0:  00000000 678a9aa9 0000000d 683a97de
0x0067e9b0:  00130e40 00000000 0067ea38 00000000
0x0067e9c0:  00000000 00000001 00000000 00000000
Backtrace:
=>0 0x6833dc2d MSVCRT_fclose+0x1d() in msvcrt (0x0067e998)
  1 0x67889684 in i_mapper (+0x9683) (0x0067fb08)
  2 0x6788e5b6 in i_mapper (+0xe5b5) (0x0067fbd8)
  3 0x00402768 in mb-core (+0x2767) (0x0067fbe8)
  4 0x004082e7 in mb-core (+0x82e6) (0x0067fbf8)
  5 0x00408883 in mb-core (+0x8882) (0x0067fde8)
  6 0x0040b0ca in mb-core (+0xb0c9) (0x0067fe68)
  7 0x004011e7 in mb-core (+0x11e6) (0x0067fe98)
  8 0x00401258 in mb-core (+0x1257) (0x0067fea8)
  9 0x7b858574 in kernel32 (+0x48573) (0x0067fee8)
  10 0x7bc6f7b4 call_thread_func+0xb() in ntdll (0x0067fef8)
  11 0x7bc6f980 call_thread_entry_point+0x6f() in ntdll (0x0067ffc8)
  12 0x7bc4b59a in ntdll (+0x3b599) (0x0067ffe8)
0x6833dc2d MSVCRT_fclose+0x1d in msvcrt: movl    0x1c(%esi),%eax
Modules:
Module    Address            Debug info    Name (68 modules)
PE      400000-  471000    Export          mb-core
PE    10000000-10013000    Deferred        zlib1
PE    67880000-678c9000    Export          i_mapper
ELF    68000000-6813b000    Export          libwine.so.1
ELF    6813b000-68154000    Deferred        libpthread.so.0
ELF    68154000-682ae000    Deferred        libc.so.6
ELF    682ae000-682b2000    Deferred        libdl.so.2
ELF    682b2000-682d8000    Deferred        libm.so.6
ELF    682d8000-682e0000    Deferred        libnss_compat.so.2
ELF    682e0000-682f7000    Deferred        libnsl.so.1
ELF    682f7000-68301000    Deferred        libnss_nis.so.2
ELF    68301000-6830d000    Deferred        libnss_files.so.2
ELF    6830d000-68381000    Export          msvcrt<elf>
  \-PE    68320000-68381000    \               msvcrt
ELF    68381000-68452000    Deferred        comctl32<elf>
  \-PE    68390000-68452000    \               comctl32
ELF    68452000-68582000    Deferred        user32<elf>
  \-PE    68460000-68582000    \               user32
ELF    68582000-6860d000    Deferred        gdi32<elf>
  \-PE    68590000-6860d000    \               gdi32
ELF    6860d000-68667000    Deferred        advapi32<elf>
  \-PE    68620000-68667000    \               advapi32
ELF    68667000-686db000    Deferred        rpcrt4<elf>
  \-PE    68670000-686db000    \               rpcrt4
ELF    686db000-688a5000    Deferred        shell32<elf>
  \-PE    686f0000-688a5000    \               shell32
ELF    688a5000-68907000    Deferred        shlwapi<elf>
  \-PE    688b0000-68907000    \               shlwapi
ELF    68907000-68922000    Deferred        wsock32<elf>
  \-PE    68910000-68922000    \               wsock32
ELF    68922000-6894e000    Deferred        ws2_32<elf>
  \-PE    68930000-6894e000    \               ws2_32
ELF    6894e000-6896f000    Deferred        iphlpapi<elf>
  \-PE    68950000-6896f000    \               iphlpapi
ELF    6896f000-68983000    Deferred        libresolv.so.2
ELF    68983000-689f9000    Deferred        libfreetype.so.6
ELF    689f9000-68a0e000    Deferred        libz.so.1
ELF    68a0e000-68a3e000    Deferred        libfontconfig.so.1
ELF    68a3e000-68a65000    Deferred        libexpat.so.1
ELF    68a65000-68b06000    Deferred        winex11<elf>
  \-PE    68a70000-68b06000    \               winex11
ELF    68b06000-68b0f000    Deferred        libsm.so.6
ELF    68b0f000-68b28000    Deferred        libice.so.6
ELF    68b28000-68b38000    Deferred        libxext.so.6
ELF    68b38000-68c55000    Deferred        libx11.so.6
ELF    68c55000-68c5a000    Deferred        libuuid.so.1
ELF    68c5a000-68c74000    Deferred        libxcb.so.1
ELF    68c74000-68c78000    Deferred        libxau.so.6
ELF    68c78000-68c7e000    Deferred        libxdmcp.so.6
ELF    68c7e000-68ca0000    Deferred        imm32<elf>
  \-PE    68c80000-68ca0000    \               imm32
ELF    68ca0000-68ca6000    Deferred        libxxf86vm.so.1
ELF    68ca6000-68cb0000    Deferred        libxrender.so.1
ELF    68cb0000-68cb8000    Deferred        libxrandr.so.2
ELF    68cb8000-68cbc000    Deferred        libxcomposite.so.1
ELF    68cbc000-68cc2000    Deferred        libxfixes.so.3
ELF    68cc2000-68ccc000    Deferred        libxcursor.so.1
ELF    68ccc000-68d00000    Deferred        uxtheme<elf>
  \-PE    68cd0000-68d00000    \               uxtheme
ELF    68d00000-68dfe000    Deferred        ole32<elf>
  \-PE    68d20000-68dfe000    \               ole32
ELF    690a6000-690c3000    Deferred        ld-linux.so.2
ELF    77aef000-77af3000    Deferred        libxinerama.so.1
ELF    7b800000-7b93d000    Export          kernel32<elf>
  \-PE    7b810000-7b93d000    \               kernel32
ELF    7bc00000-7bcb8000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb8000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000017    0
    00000013    0
    00000012    0
00000019 mb-core.exe
    0000001a    0
0000001b explorer.exe
    0000001c    0
00000038 (D) Z:\home\cariv\Desktop\MBCore\mb-core.exe
    00000039    0 <==
Backtrace:
=>0 0x6833dc2d MSVCRT_fclose+0x1d() in msvcrt (0x0067e998)
  1 0x67889684 in i_mapper (+0x9683) (0x0067fb08)
  2 0x6788e5b6 in i_mapper (+0xe5b5) (0x0067fbd8)
  3 0x00402768 in mb-core (+0x2767) (0x0067fbe8)
  4 0x004082e7 in mb-core (+0x82e6) (0x0067fbf8)
  5 0x00408883 in mb-core (+0x8882) (0x0067fde8)
  6 0x0040b0ca in mb-core (+0xb0c9) (0x0067fe68)
  7 0x004011e7 in mb-core (+0x11e6) (0x0067fe98)
  8 0x00401258 in mb-core (+0x1257) (0x0067fea8)
  9 0x7b858574 in kernel32 (+0x48573) (0x0067fee8)
  10 0x7bc6f7b4 call_thread_func+0xb() in ntdll (0x0067fef8)
  11 0x7bc6f980 call_thread_entry_point+0x6f() in ntdll (0x0067ffc8)
  12 0x7bc4b59a in ntdll (+0x3b599) (0x0067ffe8)
```
If seeing the programs will help I can link to them. Thanks in advance!

---

### Post by cogadh on 2010-05-03
Looks like a problem with Wine's default implementation of msvcrt.dll. You could try using [winetricks]("http://wiki.winehq.org/winetricks") to install the Visual C++ 6 runtime that includes the "real" msvcrt.dll.

---

### Post by tjdevens on 2010-05-03
I'm pretty sure I followed the instructions properly with Winetricks, but running the file produces the same results as before.

---

