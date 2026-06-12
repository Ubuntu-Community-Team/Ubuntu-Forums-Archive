---
title: "Noob needs help interpretting error log"
date: 2009-12-20
forum: Wine
---

### Post by irenaios on 2009-12-20
I'm running Wine 1.0.0-1
Trying to run a math tutoring program "Teaching Textbooks" (specifically version 4).

Seems to install fine, but I cannot get it to run...I've tried numerous ways. When I go through terminal here's the log I get...I'm hoping someone will help me interpret. I've read about tinkering with .dll's and such, but I'm going to need "tinkering with dll's for dummies."

[email]james@james:~/.wine[/email]/drive_c/Program Files/Teaching Textbooks/Math 4$ wine Math4.exe
err:ole:CoGetClassObject class {56fdf344-fd6d-11d0-958a-006097c9a090} not registered
err:ole:CoGetClassObject no class object {56fdf344-fd6d-11d0-958a-006097c9a090} could be created for context 0x1
wine: Unhandled page fault on read access to 0x00000000 at address 0x41de31 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0041de31).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0041de31 ESP:0032fd8c EBP:00000007 EFLAGS:00010282(   - 00      - RIS1)
 EAX:80040154 EBX:00000000 ECX:00000000 EDX:00000071
 ESI:005033b0 EDI:00000000
Stack dump:
0x0032fd8c:  7ee523f0 00000000 0032ff08 7ee98884
0x0032fd9c:  005033b0 0032fdb0 004bec0d 0000000f
0x0032fdac:  0041de9c 0032fef8 004bec2e 00000000
0x0032fdbc:  0041f105 00400000 00000000 004e57f0
0x0032fdcc:  ffffffff 7ee331c5 0032fe98 00400000
0x0032fddc:  7ee98884 0032ff08 004a6f18 00400000
Backtrace:
0x0041de31: movl    0x0(%edi),%eax
Modules:
Module    Address            Debug info    Name (91 modules)
PE      400000-  7ea000    Export          math4
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7de41000-7de55000    Deferred        midimap<elf>
  \-PE    7de50000-7de55000    \               midimap
ELF    7de55000-7de79000    Deferred        msacm32<elf>
  \-PE    7de60000-7de79000    \               msacm32
ELF    7de79000-7de90000    Deferred        msacm32<elf>
  \-PE    7de80000-7de90000    \               msacm32
ELF    7de90000-7df47000    Deferred        libasound.so.2
ELF    7df47000-7df7a000    Deferred        winealsa<elf>
  \-PE    7df50000-7df7a000    \               winealsa
ELF    7df7a000-7df7e000    Deferred        libgpg-error.so.0
ELF    7df7e000-7dfcc000    Deferred        libgcrypt.so.11
ELF    7dfcc000-7dfdb000    Deferred        libtasn1.so.3
ELF    7dfdb000-7dfdd000    Deferred        libkeyutils.so.1
ELF    7dfdd000-7dfe4000    Deferred        libkrb5support.so.0
ELF    7dfe4000-7e016000    Deferred        libcrypt.so.1
ELF    7e016000-7e086000    Deferred        libgnutls.so.13
ELF    7e086000-7e0aa000    Deferred        libk5crypto.so.3
ELF    7e0aa000-7e12e000    Deferred        libkrb5.so.3
ELF    7e12e000-7e154000    Deferred        libgssapi_krb5.so.2
ELF    7e154000-7e185000    Deferred        libcups.so.2
ELF    7e1e0000-7e211000    Deferred        uxtheme<elf>
  \-PE    7e1f0000-7e211000    \               uxtheme
ELF    7e211000-7e21a000    Deferred        libxcursor.so.1
ELF    7e21a000-7e21f000    Deferred        libxfixes.so.3
ELF    7e21f000-7e222000    Deferred        libxcomposite.so.1
ELF    7e222000-7e229000    Deferred        libxrandr.so.2
ELF    7e229000-7e232000    Deferred        libxrender.so.1
ELF    7e232000-7e235000    Deferred        libxinerama.so.1
ELF    7e235000-7e253000    Deferred        imm32<elf>
  \-PE    7e240000-7e253000    \               imm32
ELF    7e253000-7e258000    Deferred        libxdmcp.so.6
ELF    7e258000-7e26f000    Deferred        libxcb.so.1
ELF    7e26f000-7e271000    Deferred        libxcb-xlib.so.0
ELF    7e271000-7e274000    Deferred        libxau.so.6
ELF    7e274000-7e358000    Deferred        libx11.so.6
ELF    7e358000-7e366000    Deferred        libxext.so.6
ELF    7e366000-7e36b000    Deferred        libxxf86vm.so.1
ELF    7e36b000-7e382000    Deferred        libice.so.6
ELF    7e382000-7e38a000    Deferred        libsm.so.6
ELF    7e394000-7e397000    Deferred        libcom_err.so.2
ELF    7e399000-7e427000    Deferred        winex11<elf>
  \-PE    7e3b0000-7e427000    \               winex11
ELF    7e47a000-7e49c000    Deferred        libexpat.so.1
ELF    7e49c000-7e4c5000    Deferred        libfontconfig.so.1
ELF    7e4c5000-7e4da000    Deferred        libz.so.1
ELF    7e4da000-7e546000    Deferred        libfreetype.so.6
ELF    7e546000-7e5d3000    Deferred        winmm<elf>
  \-PE    7e550000-7e5d3000    \               winmm
ELF    7e5d3000-7e669000    Deferred        oleaut32<elf>
  \-PE    7e5e0000-7e669000    \               oleaut32
ELF    7e669000-7e67c000    Deferred        libresolv.so.2
ELF    7e68b000-7e6a8000    Deferred        iphlpapi<elf>
  \-PE    7e690000-7e6a8000    \               iphlpapi
ELF    7e6a8000-7e703000    Deferred        rpcrt4<elf>
  \-PE    7e6b0000-7e703000    \               rpcrt4
ELF    7e703000-7e799000    Deferred        ole32<elf>
  \-PE    7e710000-7e799000    \               ole32
ELF    7e799000-7e7ea000    Deferred        ddraw<elf>
  \-PE    7e7a0000-7e7ea000    \               ddraw
ELF    7e7ea000-7e81b000    Deferred        winspool<elf>
  \-PE    7e7f0000-7e81b000    \               winspool
ELF    7e81b000-7e86d000    Deferred        shlwapi<elf>
  \-PE    7e830000-7e86d000    \               shlwapi
ELF    7e86d000-7e973000    Deferred        shell32<elf>
  \-PE    7e880000-7e973000    \               shell32
ELF    7e973000-7ea17000    Deferred        comdlg32<elf>
  \-PE    7e980000-7ea17000    \               comdlg32
ELF    7ea17000-7eaa8000    Deferred        gdi32<elf>
  \-PE    7ea30000-7eaa8000    \               gdi32
ELF    7eaa8000-7ebda000    Deferred        user32<elf>
  \-PE    7eac0000-7ebda000    \               user32
ELF    7ebda000-7ec87000    Deferred        comctl32<elf>
  \-PE    7ebe0000-7ec87000    \               comctl32
ELF    7ec87000-7ecd2000    Deferred        advapi32<elf>
  \-PE    7ec90000-7ecd2000    \               advapi32
ELF    7edf2000-7ef12000    Deferred        kernel32<elf>
  \-PE    7ee10000-7ef12000    \               kernel32
ELF    7ef12000-7ef1d000    Deferred        libnss_files.so.2
ELF    7ef1d000-7ef27000    Deferred        libnss_nis.so.2
ELF    7ef27000-7ef3d000    Deferred        libnsl.so.1
ELF    7ef3d000-7ef63000    Deferred        libm.so.6
ELF    7ef63000-7f000000    Deferred        ntdll<elf>
  \-PE    7ef80000-7f000000    \               ntdll
ELF    b7c45000-b7c4d000    Deferred        libnss_compat.so.2
ELF    b7c4e000-b7c52000    Deferred        libdl.so.2
ELF    b7c52000-b7d9b000    Deferred        libc.so.6
ELF    b7d9c000-b7db4000    Deferred        libpthread.so.0
ELF    b7dc3000-b7ef9000    Deferred        libwine.so.1
ELF    b7efb000-b7f19000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Teaching Textbooks\Math 4\Math4.exe
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


Any help is greatly appreciated.
James

---

