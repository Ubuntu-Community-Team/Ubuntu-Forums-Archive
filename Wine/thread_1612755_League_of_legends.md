---
title: "League of legends"
date: 2010-11-03
forum: Wine
---

### Post by Gizmo_x on 2010-11-03
[IMG]http://oi54.tinypic.com/11b59y0.jpg[/IMG]

game is installed with success but when i try to start the game i get error like in photo.

---

### Post by cogadh on 2010-11-03
Windows error messages are pretty meaningless in Linux (and in Windows for that matter), so that can't really help us help you much. Try running the game from a terminal to get Wine's error output, it might explain what is happening.

However, it is worth noting that LoL barely works in Wine in the first place:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=10436](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10436)

---

### Post by Gizmo_x on 2010-11-03
how i can run from terminal?

---

### Post by Gizmo_x on 2010-11-03
```

fixme:shdocvw:PersistStreamInit_Load (0x163d80)->(0x32f018)
fixme:shdocvw:OleControl_FreezeEvents (0x163d80)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x163d80)->(0)
fixme:hnetcfg:fw_ports_Item 0x1666e0, 8395, 6, 0x32e104
fixme:hnetcfg:fw_port_put_Protocol 0x1666f8 6
fixme:hnetcfg:fw_port_put_Port 0x1666f8 8395
fixme:hnetcfg:fw_ports_Item 0x1666e0, 8395, 17, 0x32e100
fixme:hnetcfg:fw_port_put_Protocol 0x1666f8 17
fixme:hnetcfg:fw_port_put_Port 0x1666f8 8395
fixme:hnetcfg:fw_ports_Item 0x1666e0, 8393, 6, 0x32e104
fixme:hnetcfg:fw_port_put_Protocol 0x1666f8 6
fixme:hnetcfg:fw_port_put_Port 0x1666f8 8393
fixme:hnetcfg:fw_ports_Item 0x1666e0, 8393, 17, 0x32e100
fixme:hnetcfg:fw_port_put_Protocol 0x1666f8 17
fixme:hnetcfg:fw_port_put_Port 0x1666f8 8393
fixme:hnetcfg:fw_ports_Item 0x1666e0, 8390, 6, 0x32e104
fixme:hnetcfg:fw_port_put_Protocol 0x1666f8 6
fixme:hnetcfg:fw_port_put_Port 0x1666f8 8390
fixme:hnetcfg:fw_ports_Item 0x1666e0, 8390, 17, 0x32e100
fixme:hnetcfg:fw_port_put_Protocol 0x1666f8 17
fixme:hnetcfg:fw_port_put_Port 0x1666f8 8390
err:ole:create_server class {629f8434-0530-41e6-b7c5-61a82faa3df2} not registered
err:ole:CoGetClassObject no class object {629f8434-0530-41e6-b7c5-61a82faa3df2} could be created for context 0x4
err:ole:create_server class {629f8434-0530-41e6-b7c5-61a82faa3df2} not registered
err:ole:CoGetClassObject no class object {629f8434-0530-41e6-b7c5-61a82faa3df2} could be created for context 0x4
wine: Unhandled page fault on read access to 0x00000000 at address 0x440500 (thread 004a), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00440500).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00440500 ESP:0032d2ac EBP:0032d6b4 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:00691008 ECX:00000000 EDX:00000005
 ESI:0032fbec EDI:00691008
Stack dump:
0x0032d2ac:  dc100418 00691008 0032fbec 00000000
0x0032d2bc:  00691008 0044e19c 0032e700 1000eabc
0x0032d2cc:  00000000 5241575b 474e494e 414c205d
0x0032d2dc:  48434e55 52455245 54524f52 5f455059
0x0032d2ec:  56454c45 43455441 41464d4f 00004c49
0x0032d2fc:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x00440500 in lol.launcher (+0x40500) (0x0032d6b4)
  1 0x00440dd7 in lol.launcher (+0x40dd6) (0x0032e7a8)
  2 0x0043df5b in lol.launcher (+0x3df5a) (0x0032f17c)
  3 0x0040f3f5 in lol.launcher (+0xf3f4) (0x0032f1b0)
  4 0x7ec6a1cd in user32 (+0x9a1cc) (0x0032f210)
  5 0x7ec6ce3b in user32 (+0x9ce3a) (0x0032f260)
  6 0x7ebf85c4 DefDlgProcW+0x83() in user32 (0x0032f2b0)
  7 0x7ec69bfa WINPROC_wrapper+0x19() in user32 (0x0032f2e0)
  8 0x7ec6a34c in user32 (+0x9a34b) (0x0032f330)
  9 0x7ec6cbfa CallWindowProcW+0x59() in user32 (0x0032f380)
  10 0x004084b0 in lol.launcher (+0x84af) (0x0032f3a0)
  11 0x0040a137 in lol.launcher (+0xa136) (0x0032f45c)
  12 0x004085a9 in lol.launcher (+0x85a8) (0x0032f47c)
  13 0x0040a897 in lol.launcher (+0xa896) (0x0032f4e4)
  14 0x0040a924 in lol.launcher (+0xa923) (0x0032f504)
  15 0x7ec69bfa WINPROC_wrapper+0x19() in user32 (0x0032f534)
  16 0x7ec6a34c in user32 (+0x9a34b) (0x0032f584)
  17 0x7ec6c96d in user32 (+0x9c96c) (0x0032f5d4)
  18 0x7ec2cf21 in user32 (+0x5cf20) (0x0032f644)
  19 0x7ec33776 in user32 (+0x63775) (0x0032f6c4)
  20 0x7ec33bec SendMessageW+0x4b() in user32 (0x0032f714)
  21 0x7ebfe91c in user32 (+0x2e91b) (0x0032fa34)
  22 0x7ebffd8a CreateDialogIndirectParamAorW+0x39() in user32 (0x0032fa64)
  23 0x7ebffdd1 CreateDialogIndirectParamW+0x40() in user32 (0x0032fa94)
  24 0x0040fac1 in lol.launcher (+0xfac0) (0x0032fb08)
  25 0x0040fc68 in lol.launcher (+0xfc67) (0x0032fb5c)
  26 0x0043e1c5 in lol.launcher (+0x3e1c4) (0x0032fde8)
  27 0x0043a01c in lol.launcher (+0x3a01b) (0x0032fe90)
  28 0x7b85609c call_process_entry+0xb() in kernel32 (0x0032fea8)
  29 0x7b856d3f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  30 0x7bc715d0 call_thread_func+0xb() in ntdll (0x0032fef8)
  31 0x7bc74170 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  32 0x7bc49b8a call_dll_entry_point+0x659() in ntdll (0x0032ffe8)
0x00440500: movl	0x0(%eax),%edx
Modules:
Module	Address			Debug info	Name (109 modules)
PE	  330000-  34e000	Deferred        launcher.maestro
PE	  390000-  39e000	Deferred        launcher.lang-en
PE	  400000-  46b000	Export          lol.launcher
PE	10000000-100ee000	Deferred        launcher.lib
ELF	7b800000-7b980000	Export          kernel32<elf>
  \-PE	7b810000-7b980000	\               kernel32
ELF	7bc00000-7bcba000	Export          ntdll<elf>
  \-PE	7bc10000-7bcba000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d97b000-7d9d4000	Deferred        dbghelp<elf>
  \-PE	7d980000-7d9d4000	\               dbghelp
ELF	7d9d4000-7d9f1000	Deferred        hnetcfg<elf>
  \-PE	7d9e0000-7d9f1000	\               hnetcfg
PE	7da00000-7da03000	Deferred        sensapi
ELF	7da05000-7da59000	Deferred        shdocvw<elf>
  \-PE	7da10000-7da59000	\               shdocvw
ELF	7db68000-7dbc2000	Deferred        riched20<elf>
  \-PE	7db70000-7dbc2000	\               riched20
ELF	7dbc2000-7dbd6000	Deferred        riched32<elf>
  \-PE	7dbd0000-7dbd6000	\               riched32
ELF	7dbd6000-7dbdf000	Deferred        librt.so.1
ELF	7dbdf000-7dc1b000	Deferred        libdbus-1.so.3
ELF	7dc1b000-7dc2c000	Deferred        libtasn1.so.3
ELF	7dc2c000-7dc50000	Deferred        libk5crypto.so.3
ELF	7dc50000-7dcfe000	Deferred        libkrb5.so.3
ELF	7dcfe000-7dd0e000	Deferred        libavahi-client.so.3
ELF	7dd0e000-7dd82000	Deferred        libgcrypt.so.11
ELF	7dd82000-7de1d000	Deferred        libgnutls.so.26
ELF	7de1d000-7de67000	Deferred        libcups.so.2
ELF	7dee4000-7dee9000	Deferred        libgpg-error.so.0
ELF	7dee9000-7deed000	Deferred        libkeyutils.so.1
ELF	7deed000-7def9000	Deferred        libavahi-common.so.3
ELF	7def9000-7df28000	Deferred        libgssapi_krb5.so.2
ELF	7df2c000-7df32000	Deferred        libnss_dns.so.2
ELF	7df32000-7df36000	Deferred        libnss_mdns4_minimal.so.2
ELF	7df92000-7dfc6000	Deferred        uxtheme<elf>
  \-PE	7dfa0000-7dfc6000	\               uxtheme
ELF	7dfc6000-7dfd0000	Deferred        libxcursor.so.1
ELF	7dfd0000-7dfd6000	Deferred        libxfixes.so.3
ELF	7dfd6000-7dfda000	Deferred        libxcomposite.so.1
ELF	7dfda000-7dfe2000	Deferred        libxrandr.so.2
ELF	7dfe2000-7dfec000	Deferred        libxrender.so.1
ELF	7dfec000-7dff2000	Deferred        libxxf86vm.so.1
ELF	7dff2000-7dff6000	Deferred        libxinerama.so.1
ELF	7dff6000-7e017000	Deferred        imm32<elf>
  \-PE	7e000000-7e017000	\               imm32
ELF	7e017000-7e01d000	Deferred        libxdmcp.so.6
ELF	7e01d000-7e021000	Deferred        libxau.so.6
ELF	7e021000-7e03b000	Deferred        libxcb.so.1
ELF	7e03b000-7e040000	Deferred        libuuid.so.1
ELF	7e040000-7e15d000	Deferred        libx11.so.6
ELF	7e15d000-7e16d000	Deferred        libxext.so.6
ELF	7e16d000-7e186000	Deferred        libice.so.6
ELF	7e186000-7e18f000	Deferred        libsm.so.6
ELF	7e190000-7e198000	Deferred        libkrb5support.so.0
ELF	7e19a000-7e19e000	Deferred        libcom_err.so.2
ELF	7e19e000-7e245000	Deferred        winex11<elf>
  \-PE	7e1b0000-7e245000	\               winex11
ELF	7e283000-7e2aa000	Deferred        libexpat.so.1
ELF	7e2aa000-7e2da000	Deferred        libfontconfig.so.1
ELF	7e2da000-7e2ef000	Deferred        libz.so.1
ELF	7e2ef000-7e366000	Deferred        libfreetype.so.6
ELF	7e366000-7e395000	Deferred        oledlg<elf>
  \-PE	7e370000-7e395000	\               oledlg
ELF	7e395000-7e47f000	Deferred        oleaut32<elf>
  \-PE	7e3b0000-7e47f000	\               oleaut32
ELF	7e47f000-7e4f2000	Deferred        rpcrt4<elf>
  \-PE	7e490000-7e4f2000	\               rpcrt4
ELF	7e4f2000-7e5f3000	Deferred        ole32<elf>
  \-PE	7e510000-7e5f3000	\               ole32
ELF	7e5f3000-7e62b000	Deferred        winspool<elf>
  \-PE	7e600000-7e62b000	\               winspool
ELF	7e62b000-7e71b000	Deferred        comctl32<elf>
  \-PE	7e630000-7e71b000	\               comctl32
ELF	7e71b000-7e77e000	Deferred        shlwapi<elf>
  \-PE	7e730000-7e77e000	\               shlwapi
ELF	7e77e000-7e96d000	Deferred        shell32<elf>
  \-PE	7e790000-7e96d000	\               shell32
ELF	7e96d000-7ea2f000	Deferred        comdlg32<elf>
  \-PE	7e970000-7ea2f000	\               comdlg32
ELF	7ea2f000-7ea43000	Deferred        libresolv.so.2
ELF	7ea52000-7ea73000	Deferred        iphlpapi<elf>
  \-PE	7ea60000-7ea73000	\               iphlpapi
ELF	7ea73000-7eaa3000	Deferred        ws2_32<elf>
  \-PE	7ea80000-7eaa3000	\               ws2_32
ELF	7eaa3000-7eabe000	Deferred        wsock32<elf>
  \-PE	7eab0000-7eabe000	\               wsock32
ELF	7eabe000-7ead4000	Deferred        psapi<elf>
  \-PE	7eac0000-7ead4000	\               psapi
ELF	7ead4000-7eb2f000	Deferred        advapi32<elf>
  \-PE	7eae0000-7eb2f000	\               advapi32
ELF	7eb2f000-7ebbb000	Deferred        gdi32<elf>
  \-PE	7eb40000-7ebbb000	\               gdi32
ELF	7ebbb000-7ecef000	Export          user32<elf>
  \-PE	7ebd0000-7ecef000	\               user32
ELF	7ecef000-7ed84000	Deferred        winmm<elf>
  \-PE	7ed00000-7ed84000	\               winmm
ELF	7ed84000-7ed9d000	Deferred        version<elf>
  \-PE	7ed90000-7ed9d000	\               version
ELF	7ef9d000-7efa9000	Deferred        libnss_files.so.2
ELF	7efa9000-7efb4000	Deferred        libnss_nis.so.2
ELF	7efb4000-7efcb000	Deferred        libnsl.so.1
ELF	7efcb000-7eff1000	Deferred        libm.so.6
ELF	7eff8000-7f000000	Deferred        libnss_compat.so.2
ELF	b7557000-b755b000	Deferred        libdl.so.2
ELF	b755b000-b76b9000	Deferred        libc.so.6
ELF	b76ba000-b76d4000	Deferred        libpthread.so.0
ELF	b76e3000-b7823000	Export          libwine.so.1
ELF	b7825000-b7843000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000016    0
	00000013    0
	00000012    0
00000017 explorer.exe
	00000018    0
00000019 lol.launcher.exe
	0000001d    0
	0000001c    0
	0000001b    0
0000003a lol.launcher.exe
	0000003e    0
	0000003d    0
	0000003c    0
00000009 lol.launcher.exe
	00000020    0
	0000001e    0
	0000001f    0
0000001a lol.launcher.exe
	00000022    0
	00000025    0
	00000023    0
0000002b lol.launcher.exe
	00000040    0
	00000037    0
	00000026    0
00000027 lol.launcher.exe
	00000041    0
	00000034    0
	00000029    0
0000002d lol.launcher.exe
	0000002a    0
	00000035    0
	00000032    0
0000005d lol.launcher.exe
	00000061    0
	00000060    0
	0000005f    0
00000031 (D) Z:\home\gizmo\.wine\drive_c\RiotGames\LeagueofLegends\lol.launcher.exe
	0000004e    0
	0000004d    0
	0000004b    0
	0000004a    0 <==
Backtrace:
=>0 0x00440500 in lol.launcher (+0x40500) (0x0032d6b4)
  1 0x00440dd7 in lol.launcher (+0x40dd6) (0x0032e7a8)
  2 0x0043df5b in lol.launcher (+0x3df5a) (0x0032f17c)
  3 0x0040f3f5 in lol.launcher (+0xf3f4) (0x0032f1b0)
  4 0x7ec6a1cd in user32 (+0x9a1cc) (0x0032f210)
  5 0x7ec6ce3b in user32 (+0x9ce3a) (0x0032f260)
  6 0x7ebf85c4 DefDlgProcW+0x83() in user32 (0x0032f2b0)
  7 0x7ec69bfa WINPROC_wrapper+0x19() in user32 (0x0032f2e0)
  8 0x7ec6a34c in user32 (+0x9a34b) (0x0032f330)
  9 0x7ec6cbfa CallWindowProcW+0x59() in user32 (0x0032f380)
  10 0x004084b0 in lol.launcher (+0x84af) (0x0032f3a0)
  11 0x0040a137 in lol.launcher (+0xa136) (0x0032f45c)
  12 0x004085a9 in lol.launcher (+0x85a8) (0x0032f47c)
  13 0x0040a897 in lol.launcher (+0xa896) (0x0032f4e4)
  14 0x0040a924 in lol.launcher (+0xa923) (0x0032f504)
  15 0x7ec69bfa WINPROC_wrapper+0x19() in user32 (0x0032f534)
  16 0x7ec6a34c in user32 (+0x9a34b) (0x0032f584)
  17 0x7ec6c96d in user32 (+0x9c96c) (0x0032f5d4)
  18 0x7ec2cf21 in user32 (+0x5cf20) (0x0032f644)
  19 0x7ec33776 in user32 (+0x63775) (0x0032f6c4)
  20 0x7ec33bec SendMessageW+0x4b() in user32 (0x0032f714)
  21 0x7ebfe91c in user32 (+0x2e91b) (0x0032fa34)
  22 0x7ebffd8a CreateDialogIndirectParamAorW+0x39() in user32 (0x0032fa64)
  23 0x7ebffdd1 CreateDialogIndirectParamW+0x40() in user32 (0x0032fa94)
  24 0x0040fac1 in lol.launcher (+0xfac0) (0x0032fb08)
  25 0x0040fc68 in lol.launcher (+0xfc67) (0x0032fb5c)
  26 0x0043e1c5 in lol.launcher (+0x3e1c4) (0x0032fde8)
  27 0x0043a01c in lol.launcher (+0x3a01b) (0x0032fe90)
  28 0x7b85609c call_process_entry+0xb() in kernel32 (0x0032fea8)
  29 0x7b856d3f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  30 0x7bc715d0 call_thread_func+0xb() in ntdll (0x0032fef8)
  31 0x7bc74170 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  32 0x7bc49b8a call_dll_entry_point+0x659() in ntdll (0x0032ffe8)


```

---

### Post by cogadh on 2010-11-03
What you are seeing there is an error that cannot be fixed by tweaking Wine's configuration, it can only be fixed by compiling a custom patched version of Wine. Instructions on how to do that are found under the 1.0.0.x entry for LoL at that link I provided. However, I cannot stress enough, the game barely even works at all, even with using a patched version of Wine.

---

