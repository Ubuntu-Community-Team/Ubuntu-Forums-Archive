---
title: "gbalink in ubuntu?"
date: 2009-02-26
forum: Wine
---

### Post by bgugi on 2009-02-26
so i'm trying to play emulated gba games with a friend. it seems linux is vastly ignored when it comes to linked gba emulation. i'm trying to use gbalink in wine, but i'm getting some fun. first it complained about a certain dll missing, so i searched the blogosphere to get a hold of this dll, and now i get an even more interesting problem: it can't open the "open" window (if that makes any sense)

so i start the game with:```

bgugi@OPERATOR:~$ wine '/home/bgugi/VisualBoyAdvance.exe' 
```

which results in the following when opened, with the window displayed:```

fixme:win:EnumDisplayDevicesW ((null),0,0x32ed20,0x00000000), stub!
```

it seems like most of it works, except when i navigate to file > open...:
```
wine: Call from 0x4aa236 to unimplemented function MFC42.DLL.6876, aborting
wine: Unimplemented function MFC42.DLL.6876 called at address 0x4aa236 (thread 0031), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6876 called in 32-bit code (0x7bc47040).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc47040 ESP:0032fa14 EBP:0032fa78 EFLAGS:00000202(   - 00      - - I1)
 EAX:00001adc EBX:7bc8aff4 ECX:0032faac EDX:0015cc40
 ESI:0032fa20 EDI:00147848
Stack dump:
0x0032fa14:  0032fa34 7b888603 00400000 80000100
0x0032fa24:  00000001 00000000 004aa236 00000002
0x0032fa34:  00526850 00001adc 00400000 00000045
0x0032fa44:  00000006 00147848 00000445 0032fb64
0x0032fa54:  00540744 5f40e6f1 0015cc40 5f401756
0x0032fa64:  0015cc40 0032faac 004bc6c6 00540744
Backtrace:
=>1 0x7bc47040 in ntdll (+0x37040) (0x0032fa78)
  2 0x004aa236 in visualboyadvance (+0xaa236) (0x0032fb64)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file "MFC42.dbg" ("")
```
and all functionality is lost (opening menus, etc)
can this be fixed? would it be easier to just compile the source for linux?

---

