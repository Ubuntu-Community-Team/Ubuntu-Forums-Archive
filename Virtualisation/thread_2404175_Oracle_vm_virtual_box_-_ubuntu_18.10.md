---
title: "Oracle vm virtual box - ubuntu 18.10"
date: 2018-10-21
forum: Virtualisation
---

### Post by AnupamMitra on 2018-10-21
Yesterday night my system was upgraded to 18.10 (64 Bit). Beforehand Oracle VM Virtual Box was installed in 18.04.1 set up. 

After such upgrade, I'm facing trouble while trying to run VM Virtual Box. Windows 7 (32 Bit) was installed in Virtual Box. Following error report emerged.

```

Unhandled exception: page fault on read access to 0x0000000f in 64-bit code (0x0000000140019e6f).
Register dump:
 rip:0000000140019e6f rsp:000000000023f4e0 rbp:0000000140094e00 eflags:00010246 (  R- --  I  Z- -P- )
 rax:00000000fffffff2 rbx:00000000000001c5 rcx:000000000000004b rdx:0000000140094774
 rsi:00000000000001c6 rdi:00000000000001c6  r8:00000001400d47b0  r9:000000007b420040 r10:000000007b65c470
 r11:00000000003ee000 r12:00000001400d46fc r13:0000000000000000 r14:0000000000000000 r15:0000000000000960
Stack dump:
0x000000000023f4e0:  00000001400d47b0 0000000000000003
0x000000000023f4f0:  0000000000000001 00000001400d47d8
0x000000000023f500:  23a5c1e997d5abe0 0000000140000000
0x000000000023f510:  000000000023f970 000000007bcb9db0
0x000000000023f520:  0000000000000000 0000000000000000
0x000000000023f530:  000000007b420000 0000000000000000
0x000000000023f540:  0000000000000000 0000000000000000
0x000000000023f550:  0000000000000000 000000000023fe40
0x000000000023f560:  0000000000000000 000000000023ffd0
0x000000000023f570:  0000000000000000 0000000140007a84
0x000000000023f580:  000000000000004b 0000000000000003
0x000000000023f590:  0000000000000003 0000000000000000
Backtrace:
=>0 0x0000000140019e6f in virtualbox (+0x19e6f) (0x0000000140094e00)
  1 0x0000000140007a84 in virtualbox (+0x7a83) (0x000000000023ffd0)
  2 0x000000007b47a61a in kernel32 (+0x5a619) (0x000000000023ffd0)
0x0000000140019e6f: movb    0x000000000000000f,%al
Modules:
Module    Address                    Debug info    Name (18 modules)
ELF            7b400000-        7b80e000    Dwarf           kernel32<elf>
  \-PE            7b420000-        7b80e000    \               kernel32
ELF            7bc00000-        7bd16000    Deferred        ntdll<elf>
  \-PE            7bc20000-        7bd16000    \               ntdll
ELF            7c000000-        7c004000    Deferred        <wine-loader>
PE           140000000-       14012c000    Export          virtualbox
ELF        7efef74aa000-    7efef74bf000    Deferred        libnss_files.so.2
ELF        7efef74bf000-    7efef74da000    Deferred        libnsl.so.1
ELF        7efef74da000-    7efef74e8000    Deferred        libnss_nis.so.2
ELF        7efef74e8000-    7efef74f3000    Deferred        libnss_compat.so.2
ELF        7efef7c62000-    7efef7c7c000    Deferred        libgcc_s.so.1
ELF        7efef7c7c000-    7efef7e09000    Deferred        libm.so.6
ELF        7efef7e0b000-    7efef7e11000    Deferred        libdl.so.2
ELF        7efef7e11000-    7efef7ffb000    Deferred        libc.so.6
ELF        7efef7ffb000-    7efef801c000    Deferred        libpthread.so.0
ELF        7efef803f000-    7efef83e4000    Dwarf           libwine.so.1
ELF        7efef83e6000-    7efef8412000    Deferred        ld-linux-x86-64.so.2
ELF        7ffd8ea56000-    7ffd8ea57000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000c winemenubuilder.exe
    0000000d    0
0000000e services.exe
    00000025    0
    00000022    0
    0000001d    0
    00000015    0
    00000014    0
    00000013    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    0000001a    0
    00000019    0
    00000018    0
    00000017    0
    00000016    0
    00000012    0
0000001b plugplay.exe
    0000001f    0
    0000001e    0
    0000001c    0
00000020 winedevice.exe
    0000002a    0
    00000027    0
    00000026    0
    00000024    0
    00000023    0
    00000021    0
00000028 explorer.exe
    0000002d    0
    0000002c    0
    0000002b    0
    00000029    0
0000002e (D) C:\Program Files (x86)\Oracle\VirtualBox\VirtualBox.exe
    0000002f    0 <==
System information:
    Wine build: wine-3.0.3
    Platform: x86_64
    Version: Windows 7
    Host system: Linux
    Host version: 4.18.0-10-generic

```

I'm unable to understand the error report. Seek expert's cooperation as to how it could be restored.

---

### Post by wildmanne39 on 2018-10-21
*Thread moved to **Virtualisation for a more appropriate fit**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by deadflowr on 2018-10-21
Are you really running virtualbox in wine?

---

### Post by AnupamMitra on 2018-10-21
> **deadflowr said:**
> Are you really running virtualbox in wine?

No. 
For more clarity, I would like to add that during the process of upgrade, the Oracle VM Virtual Box icon was lost from desktop launcher, though all other icons were intact.

---

### Post by AnupamMitra on 2018-10-21
Thanks deadflowr.

I got the hints from your question. Just now I downloaded Oracle VM Virtual Box afresh. It came back to my launcher and after opening I find everything is in order. The installed OS in Virtual Box also opened without any hindrance. Thanks.

---

