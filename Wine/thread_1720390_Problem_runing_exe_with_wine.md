---
title: "Problem runing exe with wine"
date: 2011-04-03
forum: Wine
---

### Post by Solid Snake on 2011-04-03
hello all i'm having problem with runing exe with wine
 
exe : MTA Server.exe 
its Multi Theft Auto Server -game server - ([www.mtasa.com]("http://www.mtasa.com"))
 
about my OS:
 
VPS Hosting Ubuntu 10.04 LTS x86
 
wine 1.3.15
 
no GUI
 
I'm using ssh putty
 
i have root access
 
----------------
all what i have done is :
1- sudo aptitude install python-software-properties
2- sudo add-apt-repository ppa:ubuntu-wine/ppa
3- sudo apt-get update
3- sudo apt-get install wine1.3
 
then i go to exe after loacte to that folder : wine MTA Server.exe
 
```
wine: cannot find L"C:\\windows\\system32\\MTA.exe"
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:systray:initialize_systray Could not create tray window

```
 
when i changed name server to MTAserver.exe : wine MTAServer.exe
 
```
root@Ubuntu-1004-lucid-32-minimal ~/server # wine MTAServer.exe
fixme:actctx:p****_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:systray:initialize_systray Could not create tray window
wine: Call from 0x7b83aaf2 to unimplemented function msvcp90.dll.??$?8DU?$char_traits@D@std@@V?$allocator@D@1@@std@@YA_NABV?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@0@PBD@Z, aborting
fixme:dbghelp:elf_search_auxv can't find symbol in module
err:dbghelp:SymCleanup this process has not had SymInitialize() called for it!
wine: Unimplemented function msvcp90.dll.??$?8DU?$char_traits@D@std@@V?$allocator@D@1@@std@@YA_NABV?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@0@PBD@Z called at address 0x7b83aaf2 (thread 0009), starting debugger...
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Unhandled exception: unimplemented function msvcp90.dll.??$?8DU?$char_traits@D@std@@V?$allocator@D@1@@std@@YA_NABV?$bas called in 32-bit code (0x7b83aaf2).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
EIP:7b83aaf2 ESP:0033f4ec EBP:0033f550 EFLAGS:00000246( - -- I Z- -P- )
EAX:7b826fcd EBX:7b88aff4 ECX:00000000 EDX:80000100
ESI:80000100 EDI:00000001
Stack dump:
0x0033f4ec: 0033f570 00000008 00000000 80000100
0x0033f4fc: 00000001 00000000 7b83aaf2 00000002
0x0033f50c: 4d1ae9c0 4d1afd38 00000000 00000000
0x0033f51c: 00000000 00000000 00000000 00000000
0x0033f52c: 00000000 00000000 00000000 00000000
0x0033f53c: 00000000 00000000 7b83aaaa 0033f850
Backtrace:
=>0 0x7b83aaf2 in kernel32 (+0x2aaf2) (0x0033f550)
1 0x4d1ae938 in msvcp90 (+0x2e937) (0x0033f580)
2 0x4d1891f5 in msvcp90 (+0x91f4) (0x0033f580)
3 0x0033f570 (0x0033f830)
4 0x00000000 (0x10006720)
5 0x10002220 in core (+0x221f) (0x10002210)
0x7b83aaf2: subl $4,%esp
Modules:
Module Address Debug info Name (51 modules)
PE 400000- 420000 Deferred mtaserver
PE 10000000-1000c000 Export core
ELF 20000000-20021000 Deferred iphlpapi<elf>
\-PE 20010000-20021000 \ iphlpapi
ELF 20021000-2007e000 Deferred advapi32<elf>
\-PE 20030000-2007e000 \ advapi32
ELF 2007e000-20098000 Deferred imagehlp<elf>
\-PE 20080000-20098000 \ imagehlp
ELF 20098000-20131000 Deferred winmm<elf>
\-PE 200a0000-20131000 \ winmm
ELF 20ca6000-20cbb000 Deferred libz.so.1
ELF 227d2000-22906000 Deferred user32<elf>
\-PE 227e0000-22906000 \ user32
ELF 2b17b000-2b1f1000 Deferred libfreetype.so.6
ELF 2c9a3000-2ca31000 Deferred msvcrt<elf>
\-PE 2c9c0000-2ca31000 \ msvcrt
ELF 36cec000-36d13000 Deferred libexpat.so.1
ELF 37aa3000-37ab7000 Deferred libresolv.so.2
ELF 3ef1c000-3ef4d000 Deferred msvcr90<elf>
\-PE 3ef20000-3ef4d000 \ msvcr90
ELF 3fe3d000-3fe56000 Deferred version<elf>
\-PE 3fe40000-3fe56000 \ version
ELF 4be74000-4be8f000 Deferred wsock32<elf>
\-PE 4be80000-4be8f000 \ wsock32
ELF 4c041000-4c071000 Deferred libfontconfig.so.1
ELF 4d16d000-4d241000 Dwarf msvcp90<elf>
\-PE 4d180000-4d241000 \ msvcp90
ELF 50103000-50191000 Deferred gdi32<elf>
\-PE 50110000-50191000 \ gdi32
ELF 51bbc000-51bd2000 Deferred psapi<elf>
\-PE 51bc0000-51bd2000 \ psapi
ELF 61ecf000-61efe000 Deferred ws2_32<elf>
\-PE 61ee0000-61efe000 \ ws2_32
ELF 68000000-68141000 Dwarf libwine.so.1
ELF 68141000-6815a000 Deferred libpthread.so.0
ELF 6815a000-682b4000 Deferred libc.so.6
ELF 682b4000-682b8000 Deferred libdl.so.2
ELF 682b8000-682c0000 Deferred libnss_compat.so.2
ELF 682c0000-682d7000 Deferred libnsl.so.1
ELF 682d7000-682e3000 Deferred libnss_files.so.2
ELF 682e3000-6831b000 Deferred libncurses.so.5
ELF 6ba45000-6baa2000 Deferred dbghelp<elf>
\-PE 6ba50000-6baa2000 \ dbghelp
ELF 6ded6000-6def3000 Deferred ld-linux.so.2
ELF 70ad6000-70ae0000 Deferred libnss_nis.so.2
ELF 79077000-7909d000 Deferred libm.so.6
ELF 7b800000-7b992000 Dwarf kernel32<elf>
\-PE 7b810000-7b992000 \ kernel32
ELF 7bc00000-7bcba000 Deferred ntdll<elf>
\-PE 7bc10000-7bcba000 \ ntdll
ELF 7bf00000-7bf04000 Deferred <wine-loader>
Threads:
process tid prio (all id:s are in hex)
00000008 (D) Z:\root\server\MTAServer.exe
00000009 0 <==
0000000e services.exe
0000001b 0
00000016 0
00000015 0
00000014 0
00000010 0
0000000f 0
00000011 winedevice.exe
00000017 0
00000013 0
00000012 0
00000018 plugplay.exe
0000001c 0
0000001a 0
00000019 0
0000001d explorer.exe
0000001e 0
Backtrace:
=>0 0x7b83aaf2 in kernel32 (+0x2aaf2) (0x0033f550)
1 0x4d1ae938 in msvcp90 (+0x2e937) (0x0033f580)
2 0x4d1891f5 in msvcp90 (+0x91f4) (0x0033f580)
3 0x0033f570 (0x0033f830)
4 0x00000000 (0x10006720)
5 0x10002220 in core (+0x221f) (0x10002210)
wine: Call from 0x7b83aaf2 to unimplemented function msvcp90.dll.??$?8DU?$char_traits@D@std@@V?$allocator@D@1@@std@@YA_NABV?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@0@PBD@Z, aborting
wine: Call from 0x7b83aaf2 to unimplemented function msvcp90.dll.??$?8DU?$char_traits@D@std@@V?$allocator@D@1@@std@@YA_NABV?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@0@PBD@Z, aborting
fixme:dbghelp:elf_search_auxv can't find symbol in module
err:dbghelp:SymCleanup this process has not had SymInitialize() called for it!

```
 
 
btw i used winecfg
 
```

root@Ubuntu-1004-lucid-32-minimal ~ # winecfg
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:systray:initialize_systray Could not create tray window
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```
 
 
i heared its not work as root so how to make user & make it works ?

---

### Post by Soulcage on 2011-04-04
1. Never run wine with sudo it will mess up your permissions.
2. "Make sure that your X server is running"

Need I say more? You may also want to check out this page [http://wiki.winehq.org/]("http://wiki.winehq.org/")

---

