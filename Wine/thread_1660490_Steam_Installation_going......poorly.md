---
title: "Steam Installation going......poorly"
date: 2011-01-05
forum: Wine
---

### Post by DJWorkSafety on 2011-01-05
Basically, I'm running 64 bit Ubuntu 9.10 with wine 1.1.31 attempting to install Steam and heres what I get


```
fixme:ntdll:NtMakeTemporaryObject (0x44), stub.
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x1310c8
fixme:ntoskrnl:KeInitializeEvent stub: 0x1310cc 1 0
fixme:ntoskrnl:ObReferenceObjectByHandle stub: 0x64 1f03ff (nil) 0 0x1310dc (nil)
wine: Call from 0x7b843bf2 to unimplemented function ntoskrnl.exe.KeSetEvent, aborting
wine: Unimplemented function ntoskrnl.exe.KeSetEvent called at address 0x7b843bf2 (thread 0022), starting debugger...
wine: Call from 0x7b843bf2 to unimplemented function ntoskrnl.exe.KeGetCurrentThread, aborting
Unhandled exception: unimplemented function ntoskrnl.exe.KeGetCurrentThread called in 32-bit code (0x7b843bf2).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b843bf2 ESP:0075e9ac EBP:0075ea10 EFLAGS:00000246(   - --  I  Z- -P- )
 EAX:7b82e7a1 EBX:7b8b3ff4 ECX:00000000 EDX:80000100
 ESI:80000100 EDI:00650650
Stack dump:
0x0075e9ac:  0075ea30 00000008 0000003c 80000100
0x0075e9bc:  00000001 00000000 7b843bf2 00000002
0x0075e9cc:  7ede4680 7ede71b4 7ece0000 00000002
0x0075e9dc:  00000000 0075e9e8 00000008 7bc6b6cb
0x0075e9ec:  7bc94ff4 7ffcc000 00000000 00000002
0x0075e9fc:  00650000 ffffffff 7b843baa 7bc94ff4
Backtrace:
=>0 0x7b843bf2 in kernel32 (+0x23bf2) (0x0075ea10)
  1 0x7ede4608 in ntoskrnl (+0x14608) (0x0075ea40)
  2 0x7eddc92c in ntoskrnl (+0xc92c) (0x001310a0)
  3 0x00000000 (0x00000000)
0x7b843bf2: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (28 modules)
PE      650000-  65da60    Deferred        scdemu.sys
ELF    7b800000-7b971000    Export          kernel32<elf>
  \-PE    7b820000-7b971000    \               kernel32
ELF    7bc00000-7bcb1000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb1000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7ecd4000-7ed41000    Deferred        msvcrt<elf>
  \-PE    7ece0000-7ed41000    \               msvcrt
ELF    7ed41000-7edae000    Deferred        rpcrt4<elf>
  \-PE    7ed50000-7edae000    \               rpcrt4
ELF    7edae000-7edc3000    Deferred        system.drv16.so
PE    7edb0000-7edc3000    Deferred        system.drv16
ELF    7edc3000-7edfe000    Export          ntoskrnl<elf>
  \-PE    7edd0000-7edfe000    \               ntoskrnl
ELF    7edfe000-7ee55000    Deferred        advapi32<elf>
  \-PE    7ee10000-7ee55000    \               advapi32
ELF    7ee55000-7ee61000    Deferred        libnss_files.so.2
ELF    7ee61000-7ee6c000    Deferred        libnss_nis.so.2
ELF    7ee6c000-7ee74000    Deferred        libnss_compat.so.2
ELF    7ee7c000-7ee91000    Deferred        winedevice<elf>
  \-PE    7ee80000-7ee91000    \               winedevice
ELF    7efbd000-7efe3000    Deferred        libm.so.6
ELF    7efe9000-7f000000    Deferred        libnsl.so.1
ELF    f7476000-f747a000    Deferred        libdl.so.2
ELF    f747a000-f75bf000    Deferred        libc.so.6
ELF    f75bf000-f75d8000    Deferred        libpthread.so.0
ELF    f75f6000-f7731000    Deferred        libwine.so.1
ELF    f7733000-f7751000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
    00000009    0
0000000a 
    0000000b    0
0000000e 
    00000023    0
    00000021    0
    0000001b    0
    00000015    0
    00000014    0
    00000010    0
    0000000f    0
00000011 
    00000017    0
    00000016    0
    00000013    0
    00000012    0
00000018 
    0000001f    0
    0000001c    0
    0000001a    0
    00000019    0
0000001d (D) C:\windows\system32\winedevice.exe
    00000024    0 <==
    00000022    0
    00000020    0
    0000001e    0
Backtrace:
=>0 0x7b843bf2 in kernel32 (+0x23bf2) (0x0075ea10)
  1 0x7ede4608 in ntoskrnl (+0x14608) (0x0075ea40)
  2 0x7eddc92c in ntoskrnl (+0xc92c) (0x001310a0)
  3 0x00000000 (0x00000000)
wine: Call from 0x7b843bf2 to unimplemented function ntoskrnl.exe.KeGetCurrentThread, aborting
fixme:advapi:LookupAccountNameW (null) L"daniel" (nil) 0x32f784 (nil) 0x32f788 0x32f77c - stub
fixme:advapi:LookupAccountNameW (null) L"daniel" 0x153898 0x32f784 0x153518 0x32f788 0x32f77c - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 2 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 3 ignored L"Shortcut" table values
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1627

```


I also get "Fatal error, Installation ended prematurely because of an error"

Not quite sure what to do.

---

### Post by Mr. ViC on 2011-01-05
You using Wine? Try to install it with PlayOnLinux, they have STEAM there. Here's the list:

```
http://www.playonlinux.com/repository/?cat=1
```

---

### Post by DJWorkSafety on 2011-01-05
> **Mr. ViC said:**
> You using Wine? Try to install it with PlayOnLinux, they have STEAM there. Here's the list:

```
http://www.playonlinux.com/repository/?cat=1
```


Forgive me for not really knowing what to do with this.

Could I get a walkthrough on how to use this?

---

### Post by DJWorkSafety on 2011-01-05
I got it working, kind of. 


Basically when I try to start up steam, it starts, but the window for it is invisible. I can see "Steam" in my taskbar, but the actual window for it seems to be invisible.

I have the same problem as this guy [http://ubuntuforums.org/showthread.php?t=1620223](http://ubuntuforums.org/showthread.php?t=1620223)

---

