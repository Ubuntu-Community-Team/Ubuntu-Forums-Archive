---
title: "Crashes on games with X-Server 1.11.3/nvidia-current 290.10"
date: 2012-01-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Sworddragon on 2012-01-25
I have upgrade the X-Server/nvidia-current to the newest version and after a reboot I get a crash on all games with Wine. I tried already version 1.3.37 from the ppa and version 1.3.28 from the official repository but there was no change.

I have downgraded the X-Server and nvidia-current to an earlier version and all is working fine. These are my current pins:

```
Package: nvidia-current
Pin: version 280.*
Pin-Priority: 1001

Package: xserver-xorg
Pin: version 1:7.6+7*
Pin-Priority: 1001

Package: xserver-common
Pin: version 2:1.10.*
Pin-Priority: 1001

Package: xserver-xorg-core
Pin: version 2:1.10.*
Pin-Priority: 1001

Package: xserver-xorg-input-evdev
Pin: version 1:2.6.0*
Pin-Priority: 1001

```

If I remove the pins and upgrade these packages the crashes will appear again. Here is the output from such a crash:

```
*** glibc detected *** /home/sworddragon/.wine/drive_c/Programme/GUILD WARS/Gw.exe: malloc(): memory corruption: 0x7c6f0140 ***
======= Backtrace: =========
/lib32/libc.so.6(+0x72772)[0xf7549772]
/lib32/libc.so.6(+0x74107)[0xf754b107]
/lib32/libc.so.6(__libc_calloc+0xa7)[0xf754e017]
/usr/lib32/libXi.so.6(XIQueryDevice+0x1c8)[0x7e0c29a8]
/usr/bin/../lib32/wine/winex11.drv.so(+0x3863e)[0x7e2ce63e]
/usr/bin/../lib32/wine/winex11.drv.so(+0x38e81)[0x7e2cee81]
/usr/bin/../lib32/wine/winex11.drv.so(+0x273bf)[0x7e2bd3bf]
/usr/bin/../lib32/wine/winex11.drv.so(+0x2872b)[0x7e2be72b]
/usr/bin/../lib32/wine/user32.dll.so(PeekMessageW+0x5a)[0x7ebf04fa]
/usr/bin/../lib32/wine/user32.dll.so(PeekMessageA+0xc9)[0x7ebf0689]
[0x5baf51]
[0x5ac591]
[0x5fc10b]
[0x5f9251]
[0x5f8e41]
[0x5b1502]
[0x5b515b]
[0x5af026]
[0x81c118]
/usr/bin/../lib32/wine/ntdll.dll.so[0x7bc72f40]
/usr/bin/../lib32/wine/ntdll.dll.so(call_thread_func+0x7d)[0x7bc759cd]
/usr/bin/../lib32/wine/ntdll.dll.so[0x7bc72f1e]
/usr/bin/../lib32/wine/ntdll.dll.so[0x7bc7b9d8]
/lib32/libpthread.so.0(+0x6c60)[0xf7658c60]
/lib32/libc.so.6(clone+0x5e)[0xf75ab08e]
======= Memory map: ========
00010000-00110000 rw-p 00000000 00:00 0 
00110000-001f0000 rwxp 00000000 00:00 0 
001f0000-00220000 ---p 00000000 00:00 0 
00220000-00223000 rwxp 00000000 00:00 0 
00223000-00224000 ---p 00000000 00:00 0 
00224000-00230000 ---p 00000000 00:00 0 
00230000-00232000 ---p 00000000 00:00 0 
00232000-00331000 rwxp 00000000 00:00 0 
00331000-00340000 ---p 00000000 00:00 0 
00340000-00341000 rwxp 00000000 00:00 0 
00341000-00350000 ---p 00000000 00:00 0 
00350000-00351000 rwxp 00000000 00:00 0 
00351000-00360000 ---p 00000000 00:00 0 
00360000-00361000 rwxp 00000000 00:00 0 
00361000-00380000 ---p 00000000 00:00 0 
00380000-00389000 rwxp 00000000 00:00 0 
00389000-00390000 ---p 00000000 00:00 0 
00390000-003b4000 rwxp 00000000 00:00 0 
003b4000-00400000 ---p 00000000 00:00 0 
00400000-00899000 r-xp 00000000 08:01 1186231                            /wine/drive_c/Programme/GUILD WARS/Gw.exe
00899000-0089a000 r-xp 00499000 08:01 1186231                            /wine/drive_c/Programme/GUILD WARS/Gw.exe
0089a000-009c5000 r-xp 0049a000 08:01 1186231                            /wine/drive_c/Programme/GUILD WARS/Gw.exe
009c5000-00a27000 rwxp 005c5000 08:01 1186231                            /wine/drive_c/Programme/GUILD WARS/Gw.exe
00a27000-00e19000 rwxp 00000000 00:00 0 
00e19000-00e1a000 rwxp 00627000 08:01 1186231                            /wine/drive_c/Programme/GUILD WARS/Gw.exe
00e1a000-00fb4000 r-xp 00628000 08:01 1186231                            /wine/drive_c/Programme/GUILD WARS/Gw.exe
00fb4000-00fc4000 rwxp 00000000 00:00 0 
00fc4000-010c4000 ---p 00000000 00:00 0 
010c4000-011d4000 rwxp 00000000 00:00 0 
011d4000-011e0000 ---p 00000000 00:00 0 
011e0000-011e2000 ---p 00000000 00:00 0 
011e2000-012e0000 rwxp 00000000 00:00 0 
012e0000-012e2000 ---p 00000000 00:00 0 
012e2000-013e0000 rwxp 00000000 00:00 0 
013e0000-013e2000 ---p 00000000 00:00 0 
013e2000-01fda000 rwxp 00000000 00:00 0 
01fda000-01fe0000 ---p 00000000 00:00 0 
01fe0000-01fe2000 ---p 00000000 00:00 0 
01fe2000-020e0000 rwxp 00000000 00:00 0 
020e0000-020e2000 ---p 00000000 00:00 0 
020e2000-021e0000 rwxp 00000000 00:00 0 
021e0000-021e2000 ---p 00000000 00:00 0 
021e2000-022e0000 rwxp 00000000 00:00 0 
022e0000-022e2000 ---p 00000000 00:00 0 
022e2000-023e0000 rwxp 00000000 00:00 0 
023e0000-023e2000 ---p 00000000 00:00 0 
023e2000-024e0000 rwxp 00000000 00:00 0 
024e0000-02567000 ---p 00000000 00:00 0 
02567000-02677000 rwxp 00000000 00:00 0 
02677000-026e0000 ---p 00000000 00:00 0 
026e0000-026e2000 ---p 00000000 00:00 0 
026e2000-029f0000 rwxp 00000000 00:00 0 
029f0000-02a00000 ---p 00000000 00:00 0 
02a00000-02a1a000 ---p 00000000 00:00 0 
02a1a000-02fb6000 rwxp 00000000 00:00 0 
02fb6000-02fc0000 ---p 00000000 00:00 0 
02fc0000-02fc2000 ---p 00000000 00:00 0 
02fc2000-030c0000 rwxp 00000000 00:00 0 
030c0000-030e0000 ---p 00000000 00:00 0 
030e0000-030e2000 ---p 00000000 00:00 0 
030e2000-03620000 rwxp 00000000 00:00 0 
03620000-04a51000 rwxp 00000000 00:00 0 
04a51000-04a60000 ---p 00000000 00:00 0 
04a60000-04a62000 ---p 00000000 00:00 0 
04a62000-04b60000 rwxp 00000000 00:00 0 
04b60000-04b62000 ---p 00000000 00:00 0 
04b62000-04d5f000 rwxp 00000000 00:00 0 
04d5f000-0501c000 ---p 00000000 00:00 0 
0501c000-05abd000 rwxp 00000000 00:00 0 
05abd000-05b0d000 ---p 00000000 00:00 0 
05b0d000-05d41000 rwxp 00000000 00:00 0 
05d41000-68000000 ---p 00000000 00:00 0 
7b800000-7b810000 r-xp 00000000 08:01 1187445                            /usr/lib32/wine/kernel32.dll.so
7b810000-7b811000 r-xp 00000000 00:00 0 
7b811000-7b894000 r-xp 00011000 08:01 1187445                            /usr/lib32/wine/kernel32.dll.so
7b894000-7b895000 r--p 00093000 08:01 1187445                            /usr/lib32/wine/kernel32.dll.so
7b895000-7b9b7000 rwxp 00094000 08:01 1187445                            /usr/lib32/wine/kernel32.dll.so
7bc00000-7bc10000 r-xp 00000000 08:01 1187415                            /usr/lib32/wine/ntdll.dll.so
7bc10000-7bc11000 r-xp 00000000 00:00 0 
7bc11000-7bca6000 r-xp 00011000 08:01 1187415                            /usr/lib32/wine/ntdll.dll.so
7bca6000-7bca7000 r--p 000a6000 08:01 1187415                            /usr/lib32/wine/ntdll.dll.so
7bca7000-7bcb0000 rwxp 000a7000 08:01 1187415                            /usr/lib32/wine/ntdll.dll.so
7bcb0000-7bcc3000 rwxp 00000000 00:00 0 
7bf00000-7bf02000 r-xp 00000000 08:01 1056137                            /usr/bin/wine
7bf02000-7bf03000 r--p 00001000 08:01 1056137                            /usr/bin/wine
7bf03000-7bf04000 rw-p 00002000 08:01 1056137                            /usr/bin/wine
7c400000-7c402000 r-xp 00001000 08:01 1056301                            /usr/bin/wine-preloader
7c402000-7c403000 rw-p 00003000 08:01 1056301                            /usr/bin/wine-preloader
7c63b000-7cafe000 rw-p 00000000 00:00 0                                  [heap]
7dfa6000-7dfbc000 r--p 00000000 08:01 1188687                            /usr/share/wine/fonts/tahomabd.ttf
7dfbc000-7dfd4000 r--p 00000000 08:01 1188101                            /usr/share/wine/fonts/tahoma.ttf
7dfd4000-7dfe0000 r-xp 00000000 08:01 1187205                            /usr/lib32/wine/uxtheme.dll.so
7dfe0000-7dfe1000 rw-p 00000000 00:00 0 
7dfe1000-7e005000 r-xp 0000d000 08:01 1187205                            /usr/lib32/wine/uxtheme.dll.so
7e005000-7e006000 r--p 00030000 08:01 1187205                            /usr/lib32/wine/uxtheme.dll.so
7e006000-7e007000 rwxp 00031000 08:01 1187205                            /usr/lib32/wine/uxtheme.dll.so
7e007000-7e008000 rw-p 00032000 08:01 1187205                            /usr/lib32/wine/uxtheme.dll.so
7e008000-7e011000 r-xp 00000000 08:01 1186381                            /usr/lib32/libXcursor.so.1.0.2
7e011000-7e012000 r--p 00008000 08:01 1186381                            /usr/lib32/libXcursor.so.1.0.2
7e012000-7e013000 rw-p 00009000 08:01 1186381                            /usr/lib32/libXcursor.so.1.0.2
7e028000-7e02a000 r--p 00000000 08:01 1188664                            /usr/share/wine/fonts/vgasys.fon
7e02a000-7e030000 r--s 00000000 00:14 9569030                            /home/sworddragon/.fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
7e030000-7e033000 r--s 00000000 00:14 9569029                            /home/sworddragon/.fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
7e033000-7e037000 r--s 00000000 00:14 9569028                            /home/sworddragon/.fontconfig/eb48934c523a49add3824bfad8846c40-le32d4.cache-3
7e037000-7e038000 r--s 00000000 00:14 9569789                            /home/sworddragon/.fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
7e038000-7e05a000 r--s 00000000 08:01 2753667                            /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
7e05a000-7e080000 r-xp 00000000 08:01 7864422                            /lib32/libexpat.so.1.5.2
7e080000-7e081000 ---p 00026000 08:01 7864422                            /lib32/libexpat.so.1.5.2
7e081000-7e083000 r--p 00026000 08:01 7864422                            /lib32/libexpat.so.1.5.2
7e083000-7e084000 rw-p 00028000 08:01 7864422                            /lib32/libexpat.so.1.5.2
7e084000-7e0b6000 r-xp 00000000 08:01 1186408                            /usr/lib32/libfontconfig.so.1.4.4
7e0b6000-7e0b7000 ---p 00032000 08:01 1186408                            /usr/lib32/libfontconfig.so.1.4.4
7e0b7000-7e0b8000 r--p 00032000 08:01 1186408                            /usr/lib32/libfontconfig.so.1.4.4
7e0b8000-7e0b9000 rw-p 00033000 08:01 1186408                            /usr/lib32/libfontconfig.so.1.4.4
7e0b9000-7e0c7000 r-xp 00000000 08:01 1186387                            /usr/lib32/libXi.so.6.1.0
7e0c7000-7e0c8000 r--p 0000d000 08:01 1186387                            /usr/lib32/libXi.so.6.1.0
7e0c8000-7e0c9000 rw-p 0000e000 08:01 1186387                            /usr/lib32/libXi.so.6.1.0
7e0c9000-7e0cb000 r-xp 00000000 08:01 1186380                            /usr/lib32/libXcomposite.so.1.0.0
7e0cb000-7e0cc000 r--p 00001000 08:01 1186380                            /usr/lib32/libXcomposite.so.1.0.0
7e0cc000-7e0cd000 rw-p 00002000 08:01 1186380                            /usr/lib32/libXcomposite.so.1.0.0
7e0cd000-7e0d4000 r-xp 00000000 08:01 1186389                            /usr/lib32/libXrandr.so.2.2.0
7e0d4000-7e0d5000 r--p 00006000 08:01 1186389                            /usr/lib32/libXrandr.so.2.2.0
7e0d5000-7e0d6000 rw-p 00007000 08:01 1186389                            /usr/lib32/libXrandr.so.2.2.0
7e0d6000-7e0df000 r-xp 00000000 08:01 1186390                            /usr/lib32/libXrender.so.1.3.0
7e0df000-7e0e0000 r--p 00008000 08:01 1186390                            /usr/lib32/libXrender.so.1.3.0
7e0e0000-7e0e1000 rw-p 00009000 08:01 1186390                            /usr/lib32/libXrender.so.1.3.0
7e0e1000-7e0e5000 r-xp 00000000 08:01 1186393                            /usr/lib32/libXxf86vm.so.1.0.0
7e0e5000-7e0e6000 r--p 00003000 08:01 1186393                            /usr/lib32/libXxf86vm.so.1.0.0
7e0e6000-7e0e7000 rw-p 00004000 08:01 1186393                            /usr/lib32/libXxf86vm.so.1.0.0
7e0e7000-7e0e9000 r-xp 00000000 08:01 1186388                            /usr/lib32/libXinerama.so.1.0.0
7e0e9000-7e0ea000 r--p 00001000 08:01 1186388                            /usr/lib32/libXinerama.so.1.0.0
7e0ea000-7e0eb000 rw-p 00002000 08:01 1186388                            /usr/lib32/libXinerama.so.1.0.0
7e0eb000-7e0f0000 r-xp 00000000 08:01 1187586                            /usr/lib32/wine/imm32.dll.so
7e0f0000-7e0f1000 rw-p 00000000 00:00 0 
7e0f1000-7e10a000 r-xp 00006000 08:01 1187586                            /usr/lib32/wine/imm32.dll.so
7e10a000-7e10b000 r--p 0001e000 08:01 1187586                            /usr/lib32/wine/imm32.dll.so
7e10b000-7e10c000 rwxp 0001f000 08:01 1187586                            /usr/lib32/wine/imm32.dll.so
7e10c000-7e10d000 rw-p 00020000 08:01 1187586                            /usr/lib32/wine/imm32.dll.so
7e10d000-7e112000 r-xp 00000000 08:01 1186383                            /usr/lib32/libXdmcp.so.6.0.0
7e112000-7e113000 r--p 00004000 08:01 1186383                            /usr/lib32/libXdmcp.so.6.0.0
7e113000-7e114000 rw-p 00005000 08:01 1186383                            /usr/lib32/libXdmcp.so.6.0.0
7e114000-7e131000 r-xp 00000000 08:01 1186477                            /usr/lib32/libxcb.so.1.1.0
7e131000-7e132000 r--p 0001c000 08:01 1186477                            /usr/lib32/libxcb.so.1.1.0
7e132000-7e133000 rw-p 0001d000 08:01 1186477                            /usr/lib32/libxcb.so.1.1.0
7e133000-7e149000 r-xp 00000000 08:01 1186374                            /usr/lib32/libICE.so.6.3.0
7e149000-7e14a000 r--p 00015000 08:01 1186374                            /usr/lib32/libICE.so.6.3.0
7e14a000-7e14b000 rw-p 00016000 08:01 1186374                            /usr/lib32/libICE.so.6.3.0
7e14b000-7e14d000 rw-p 00000000 00:00 0 
7e14d000-7e27e000 r-xp 00000000 08:01 1186378                            /usr/lib32/libX11.so.6.3.0
7e27e000-7e27f000 ---p 00131000 08:01 1186378                            /usr/lib32/libX11.so.6.3.0
7e27f000-7e280000 r--p 00131000 08:01 1186378                            /usr/lib32/libX11.so.6.3.0
7e280000-7e282000 rw-p 00132000 08:01 1186378                            /usr/lib32/libX11.so.6.3.0
7e282000-7e283000 rw-p 00000000 00:00 0 
7e283000-7e294000 r-xp 00000000 08:01 1186384                            /usr/lib32/libXext.so.6.4.0
7e294000-7e295000 r--p 00010000 08:01 1186384                            /usr/lib32/libXext.so.6.4.0
7e295000-7e296000 rw-p 00011000 08:01 1186384                            /usr/lib32/libXext.so.6.4.0
7e296000-7e2a0000 r-xp 00000000 08:01 1187515                            /usr/lib32/wine/winex11.drv.so
7e2a0000-7e2a1000 rw-p 00000000 00:00 0 
7e2a1000-7e31e000 r-xp 0000b000 08:01 1187515                            /usr/lib32/wine/winex11.drv.so
7e31e000-7e320000 r--p 00088000 08:01 1187515                            /usr/lib32/wine/winex11.drv.so
7e320000-7e321000 rw-p 0008a000 08:01 1187515                            /usr/lib32/wine/winex11.drv.so
7e321000-7e322000 rwxp 0008b000 08:01 1187515                            /usr/lib32/wine/winex11.drv.so
7e322000-7e324000 rw-p 0008c000 08:01 1187515                            /usr/lib32/wine/winex11.drv.so
7e324000-7e328000 rw-p 00000000 00:00 0 
7e328000-7e33c000 r-xp 00000000 08:01 1182284                            /usr/lib32/libz.so.1.2.3.4
7e33c000-7e33d000 r--p 00013000 08:01 1182284                            /usr/lib32/libz.so.1.2.3.4
7e33d000-7e33e000 rw-p 00014000 08:01 1182284                            /usr/lib32/libz.so.1.2.3.4
7e33e000-7e3cf000 r-xp 00000000 08:01 1186409                            /usr/lib32/libfreetype.so.6.6.2
7e3cf000-7e3d0000 ---p 00091000 08:01 1186409                            /usr/lib32/libfreetype.so.6.6.2
7e3d0000-7e3d4000 r--p 00091000 08:01 1186409                            /usr/lib32/libfreetype.so.6.6.2
7e3d4000-7e3d5000 rw-p 00095000 08:01 1186409                            /usr/lib32/libfreetype.so.6.6.2
7e3d5000-7e3d9000 r-xp 00000000 08:01 1186385                            /usr/lib32/libXfixes.so.3.1.0
7e3d9000-7e3da000 r--p 00003000 08:01 1186385                            /usr/lib32/libXfixes.so.3.1.0
7e3da000-7e3db000 rw-p 00004000 08:01 1186385                            /usr/lib32/libXfixes.so.3.1.0
7e3db000-7e3e8000 r--s 00000000 00:14 9568606                            /home/sworddragon/.fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
7e3e8000-7e3ec000 r--s 00000000 00:14 9568604                            /home/sworddragon/.fontconfig/3f7329c5293ffd510edef78f73874cfd-le32d4.cache-3
7e3ec000-7e3f0000 r-xp 00000000 08:01 1187778                            /usr/lib32/wine/msacm32.dll.so
7e3f0000-7e3f1000 rw-p 00000000 00:00 0 
7e3f1000-7e40d000 r-xp 00005000 08:01 1187778                            /usr/lib32/wine/msacm32.dll.so
7e40d000-7e40e000 r--p 00020000 08:01 1187778                            /usr/lib32/wine/msacm32.dll.so
7e40e000-7e40f000 rwxp 00021000 08:01 1187778                            /usr/lib32/wine/msacm32.dll.so
7e40f000-7e414000 rw-p 00022000 08:01 1187778                            /usr/lib32/wine/msacm32.dll.so
7e414000-7e420000 r-xp 00000000 08:01 1187133                            /usr/lib32/wine/winmm.dll.so
7e420000-7e421000 rw-p 00000000 00:00 0 
7e421000-7e44f000 r-xp 0000d000 08:01 1187133                            /usr/lib32/wine/winmm.dll.so
7e44f000-7e450000 r--p 0003a000 08:01 1187133                            /usr/lib32/wine/winmm.dll.so
7e450000-7e451000 rw-p 0003b000 08:01 1187133                            /usr/lib32/wine/winmm.dll.so
7e451000-7e452000 rwxp 0003c000 08:01 1187133                            /usr/lib32/wine/winmm.dll.so
7e452000-7e4b8000 rw-p 0003d000 08:01 1187133                            /usr/lib32/wine/winmm.dll.so
7e4b8000-7e4b9000 rw-p 00000000 00:00 0 
7e4b9000-7e4d0000 r-xp 00000000 08:01 1185019                            /usr/lib32/wine/oleaut32.dll.so
7e4d0000-7e4d1000 rw-p 00000000 00:00 0 
7e4d1000-7e59d000 r-xp 00018000 08:01 1185019                            /usr/lib32/wine/oleaut32.dll.so
7e59d000-7e59e000 ---p 000e4000 08:01 1185019                            /usr/lib32/wine/oleaut32.dll.so
7e59e000-7e5a1000 r--p 000e4000 08:01 1185019                            /usr/lib32/wine/oleaut32.dll.so
7e5a1000-7e5a3000 rw-p 000e7000 08:01 1185019                            /usr/lib32/wine/oleaut32.dll.so
7e5a3000-7e5a5000 rwxp 000e9000 08:01 1185019                            /usr/lib32/wine/oleaut32.dll.so
7e5a5000-7e5ab000 rw-p 000eb000 08:01 1185019                            /usr/lib32/wine/oleaut32.dll.so
7e5ab000-7e5ac000 rw-p 00000000 00:00 0 
7e5ac000-7e5c0000 r-xp 00000000 08:01 1187963                            /usr/lib32/wine/rpcrt4.dll.so
7e5c0000-7e5c1000 rw-p 00000000 00:00 0 
7e5c1000-7e61a000 r-xp 00015000 08:01 1187963                            /usr/lib32/wine/rpcrt4.dll.so
7e61a000-7e61b000 ---p 0006e000 08:01 1187963                            /usr/lib32/wine/rpcrt4.dll.so
7e61b000-7e61c000 r--p 0006e000 08:01 1187963                            /usr/lib32/wine/rpcrt4.dll.so
7e61c000-7e620000 rw-p 0006f000 08:01 1187963                            /usr/lib32/wine/rpcrt4.dll.so
7e620000-7e621000 rwxp 00073000 08:01 1187963                            /usr/lib32/wine/rpcrt4.dll.so
7e621000-7e622000 rw-p 00074000 08:01 1187963                            /usr/lib32/wine/rpcrt4.dll.so
7e622000-7e640000 r-xp 00000000 08:01 1187089                            /usr/lib32/wine/ole32.dll.so
7e640000-7e641000 rw-p 00000000 00:00 0 
7e641000-7e71c000 r-xp 0001f000 08:01 1187089                            /usr/lib32/wine/ole32.dll.so
7e71c000-7e71d000 ---p 000fa000 08:01 1187089                            /usr/lib32/wine/ole32.dll.so
7e71d000-7e721000 r--p 000fa000 08:01 1187089                            /usr/lib32/wine/ole32.dll.so
7e721000-7e723000 rw-p 000fe000 08:01 1187089                            /usr/lib32/wine/ole32.dll.so
7e723000-7e724000 rwxp 00100000 08:01 1187089                            /usr/lib32/wine/ole32.dll.so
7e724000-7e72a000 rw-p 00101000 08:01 1187089                            /usr/lib32/wine/ole32.dll.so
7e72a000-7e730000 r-xp 00000000 08:01 1187952                            /usr/lib32/wine/comctl32.dll.so
7e730000-7e731000 rw-p 00000000 00:00 0 
7e731000-7e7f1000 r-xp 00007000 08:01 1187952                            /usr/lib32/wine/comctl32.dll.so
7e7f1000-7e7f2000 r--p 000c6000 08:01 1187952                            /usr/lib32/wine/comctl32.dll.so
7e7f2000-7e7f3000 rw-p 000c7000 08:01 1187952                            /usr/lib32/wine/comctl32.dll.so

```

Does somebody have the same problem or maybe know which of the pinned packages are causing the problem?

---

### Post by vhaarr on 2012-01-25
The problem might actually be that WINE needs to be updated to work with the latest XInput version.

---

### Post by Sworddragon on 2012-01-30
Do you know or think this? If Wine 1.3.38 is in the ppa I will test this again.

---

### Post by vhaarr on 2012-01-31
I think so, but I am pretty certain. I've held back upgrading the XOrg packages myself until I see some XInput-related commits in the wine git log. 1.3.38 will not work either.

---

### Post by Sworddragon on 2012-02-01
I have opened a ticket for this: [http://bugs.winehq.org/show_bug.cgi?id=29762](http://bugs.winehq.org/show_bug.cgi?id=29762)

Somebody says that he is running the same X-Server and NVIDIA driver as me but he is using Fedora. On his system all is working fine. So Wine seems to support already the newest XInput version.

---

