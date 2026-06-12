---
title: "WOW Crashing"
date: 2011-03-11
forum: Wine
---

### Post by moncrief415 on 2011-03-11
Hello,

I have recently switched my OS to Ubuntu 10.10 64 bit from xp
Im currently having trouble with Wow (world of warcraft) everytime i run it in wine it works find up until i get into the game and it crashes. ive been looking everywhere to find out whats wrong but either i cant find people with the same problem or when i do i dont understand how they solve the problem since im completely new to the Linux os but everyone was new to linux at one point, so if anyone happens to have an answer to my problem it would be very greatly appreciated if it was explained in terms where a absolute beginner would understand it. Now i think what the problem is, is that im running Wow in 32 bit wine in a 64 bit ubuntu os but i cant be exactly sure thats what the problem is. I'm running wow from the program files in my windows partition using WINE. This is what my terminal puts out when i open Wow:

wine "/media/1A5076105075F2BD/Program Files/World of Warcraft/Wow.exe"
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
archive Data\enUS\base-enUS.MPQ opened
archive Data/Cache/SoundCache-3.MPQ opened
archive Data/Cache/SoundCache-2.MPQ opened
archive Data/Cache/SoundCache-1.MPQ opened
archive Data/Cache/SoundCache-0.MPQ opened
archive Data/Cache/enUS/SoundCache-enUS.MPQ opened
archive Data/wow-update-13164.MPQ opened
archive Data/Cache/enUS/patch-enUS-13164.MPQ opened
archive Data/Cache/patch-base-13164.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13164.MPQ opened
archive Data/Cache/SoundCache-patch-13164.MPQ opened
archive Data/wow-update-13205.MPQ opened
archive Data/Cache/enUS/patch-enUS-13205.MPQ opened
archive Data/Cache/patch-base-13205.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13205.MPQ opened
archive Data/Cache/SoundCache-patch-13205.MPQ opened
archive Data/wow-update-13287.MPQ opened
archive Data/Cache/enUS/patch-enUS-13287.MPQ opened
archive Data/Cache/patch-base-13287.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13287.MPQ opened
archive Data/Cache/SoundCache-patch-13287.MPQ opened
archive Data/wow-update-13329.MPQ opened
archive Data/Cache/enUS/patch-enUS-13329.MPQ opened
archive Data/Cache/patch-base-13329.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13329.MPQ opened
archive Data/Cache/SoundCache-patch-13329.MPQ opened
archive Data/wow-update-13596.MPQ opened
archive Data/Cache/enUS/patch-enUS-13596.MPQ opened
archive Data/Cache/patch-base-13596.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13596.MPQ opened
archive Data/Cache/SoundCache-patch-13596.MPQ opened
archive Data/wow-update-13623.MPQ opened
archive Data/Cache/enUS/patch-enUS-13623.MPQ opened
archive Data/Cache/patch-base-13623.MPQ opened
archive Data/Cache/enUS/SoundCache-patch-enUS-13623.MPQ opened
archive Data/Cache/SoundCache-patch-13623.MPQ opened
archive Data\art.MPQ opened
archive Data\world.MPQ opened
archive Data\sound.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed7c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ea48,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f198,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee64,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1400a0,0x13ffa0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1400a0,0x13ffa0): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x32f86c): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f338,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f004,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:imm:ImmReleaseContext (0x20052, 0x133a60): stub
Unable to read archive hash/block table: "Data/wow-update-13287.MPQ"
archive Data\expansion1.MPQ opened
archive Data\expansion2.MPQ opened
archive Data\expansion3.MPQ opened
archive Data\enUS\expansion1-locale-enUS.MPQ opened
archive Data\enUS\expansion2-locale-enUS.MPQ opened
archive Data\enUS\expansion3-locale-enUS.MPQ opened
archive Data\enUS\expansion1-speech-enUS.MPQ opened
archive Data\enUS\expansion2-speech-enUS.MPQ opened
archive Data\enUS\expansion3-speech-enUS.MPQ opened
wine: Unhandled page fault on execute access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on execute access to 0x00000000 in 32-bit code (0x00000000).

And this is what it puts out after it crashes:
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00000000 ESP:0032fc04 EBP:0032fc64 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:000083f1 EBX:00002000 ECX:00000de1 EDX:17f41948
 ESI:00000000 EDI:150903f0
Stack dump:
0x0032fc04:  007c57e5 00000de1 00000000 000083f1
0x0032fc14:  00000080 00000080 00000000 00002000
0x0032fc24:  17f41948 00000080 150903f0 00000080
0x0032fc34:  00000000 00000000 00000080 00000080
0x0032fc44:  0000813d 00000007 00000000 00000100
0x0032fc54:  17f43948 00002000 17f41948 000083f1
Backtrace:
=>0 0x00000000 (0x0032fc64)
  1 0x007c59f9 in wow (+0x3c59f8) (0x0032fcb8)
  2 0x007c5aa2 in wow (+0x3c5aa1) (0x0032fcc8)
  3 0x007a996a in wow (+0x3a9969) (0x0032fcd4)
  4 0x007a6f95 in wow (+0x3a6f94) (0x0032fcf8)
  5 0x00662c9b in wow (+0x262c9a) (0x0032fd38)
  6 0x00808469 in wow (+0x408468) (0x0032fd68)
  7 0x008054ac in wow (+0x4054ab) (0x0032fd90)
  8 0x00806b2a in wow (+0x406b29) (0x0032fde4)
  9 0x00806b71 in wow (+0x406b70) (0x0032fdfc)
  10 0x004079e8 in wow (+0x79e7) (0x0032fe90)
  11 0x7b85406c call_process_entry+0xb() in kernel32 (0x0032fea8)
  12 0x7b8564db in kernel32 (+0x464da) (0x0032fee8)
  13 0x7bc6fc80 call_thread_func+0xb() in ntdll (0x0032fef8)
  14 0x7bc6fe50 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  15 0x7bc4ae0a in ntdll (+0x3ae09) (0x0032ffe8)
0x00000000: -- no code accessible --
Modules:
Module    Address            Debug info    Name (153 modules)
PE      400000-  f6c000    Export          wow
PE    3c8f0000-3d6fcb42    Deferred        battle.net
PE    78130000-781cb000    Deferred        msvcr80
ELF    79c81000-79cd9000    Deferred        dbghelp<elf>
  \-PE    79c90000-79cd9000    \               dbghelp
ELF    79cd9000-79d00000    Deferred        winhttp<elf>
  \-PE    79ce0000-79d00000    \               winhttp
ELF    79d00000-79d20000    Deferred        iphlpapi<elf>
  \-PE    79d10000-79d20000    \               iphlpapi
ELF    79d20000-79dbe000    Deferred        crypt32<elf>
  \-PE    79d30000-79dbe000    \               crypt32
ELF    79dbe000-79e3f000    Deferred        msvcrt<elf>
  \-PE    79dd0000-79e3f000    \               msvcrt
ELF    79e3f000-79e57000    Deferred        libsasl2.so.2
ELF    79e57000-79e9d000    Deferred        libldap_r-2.4.so.2
ELF    79ea2000-79eb8000    Deferred        psapi<elf>
  \-PE    79eb0000-79eb8000    \               psapi
ELF    79eb8000-79f0d000    Deferred        wldap32<elf>
  \-PE    79ec0000-79f0d000    \               wldap32
ELF    7b800000-7b97b000    Export          kernel32<elf>
  \-PE    7b810000-7b97b000    \               kernel32
ELF    7bb10000-7bb1d000    Deferred        liblber-2.4.so.2
ELF    7bc00000-7bcb7000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c446000-7c5be000    Deferred        libvorbisenc.so.2
ELF    7ca98000-7caae000    Deferred        midimap<elf>
  \-PE    7caa0000-7caae000    \               midimap
ELF    7caae000-7cac7000    Deferred        msacm32<elf>
  \-PE    7cab0000-7cac7000    \               msacm32
ELF    7cac7000-7cace000    Deferred        libogg.so.0
ELF    7cace000-7caf6000    Deferred        libvorbis.so.0
ELF    7caf6000-7cb42000    Deferred        libflac.so.8
ELF    7cb42000-7cbaa000    Deferred        libsndfile.so.1
ELF    7cbaa000-7cbb8000    Deferred        libxi.so.6
ELF    7cbb8000-7cc02000    Deferred        libpulsecommon-0.9.21.so
ELF    7cc02000-7ccc8000    Deferred        libasound.so.2
ELF    7d255000-7d25e000    Deferred        libwrap.so.0
ELF    7d25e000-7d263000    Deferred        libxcb-atom.so.1
ELF    7d263000-7d2a5000    Deferred        libpulse.so.0
ELF    7d2ba000-7d2c0000    Deferred        libasound_module_pcm_pulse.so
ELF    7d2c0000-7d2f7000    Deferred        winealsa<elf>
  \-PE    7d2d0000-7d2f7000    \               winealsa
ELF    7d2f7000-7d33f000    Deferred        dsound<elf>
  \-PE    7d300000-7d33f000    \               dsound
ELF    7d33f000-7d37b000    Deferred        libdbus-1.so.3
ELF    7d37b000-7d380000    Deferred        libgpg-error.so.0
ELF    7d380000-7d394000    Deferred        libresolv.so.2
ELF    7d394000-7d3b8000    Deferred        libk5crypto.so.3
ELF    7d5b9000-7d5ca000    Deferred        libtasn1.so.3
ELF    7d5ca000-7d5d2000    Deferred        libkrb5support.so.0
ELF    7d5d2000-7d680000    Deferred        libkrb5.so.3
ELF    7d680000-7d690000    Deferred        libavahi-client.so.3
ELF    7d690000-7d69c000    Deferred        libavahi-common.so.3
ELF    7d69c000-7d710000    Deferred        libgcrypt.so.11
ELF    7d710000-7d7ab000    Deferred        libgnutls.so.26
ELF    7d7ab000-7d7da000    Deferred        libgssapi_krb5.so.2
ELF    7d8dd000-7d8e1000    Deferred        libkeyutils.so.1
ELF    7d8e1000-7d92b000    Deferred        libcups.so.2
ELF    7d92d000-7d933000    Deferred        libxtst.so.6
ELF    7d933000-7d936000    Deferred        libx11-xcb.so.1
ELF    7d93c000-7d942000    Deferred        libnss_dns.so.2
ELF    7d942000-7d946000    Deferred        libnss_mdns4_minimal.so.2
ELF    7d973000-7d9a7000    Deferred        uxtheme<elf>
  \-PE    7d980000-7d9a7000    \               uxtheme
ELF    7d9d6000-7dce8000    Deferred        r300_dri.so
ELF    7dce8000-7dcf2000    Deferred        libxcursor.so.1
ELF    7dcf2000-7dcf6000    Deferred        libxcomposite.so.1
ELF    7dcf6000-7dcfe000    Deferred        libxrandr.so.2
ELF    7dcfe000-7dd08000    Deferred        libxrender.so.1
ELF    7dd08000-7dd0c000    Deferred        libxinerama.so.1
ELF    7dd10000-7dd14000    Deferred        libcom_err.so.2
ELF    7dd14000-7dd1b000    Deferred        libdrm_radeon.so.1
ELF    7dd1b000-7dd25000    Deferred        libtalloc.so.2
ELF    7dd27000-7ddc9000    Deferred        winex11<elf>
  \-PE    7dd30000-7ddc9000    \               winex11
ELF    7de0c000-7de33000    Deferred        libexpat.so.1
ELF    7de33000-7de63000    Deferred        libfontconfig.so.1
ELF    7de63000-7deda000    Deferred        libfreetype.so.6
ELF    7df2d000-7df54000    Deferred        msacm32<elf>
  \-PE    7df30000-7df54000    \               msacm32
ELF    7df54000-7dfe9000    Deferred        winmm<elf>
  \-PE    7df60000-7dfe9000    \               winmm
ELF    7dfe9000-7dffe000    Deferred        hid<elf>
  \-PE    7dff0000-7dffe000    \               hid
ELF    7dffe000-7e012000    Deferred        lz32<elf>
  \-PE    7e000000-7e012000    \               lz32
ELF    7e012000-7e02b000    Deferred        version<elf>
  \-PE    7e020000-7e02b000    \               version
ELF    7e02b000-7e062000    Deferred        winspool<elf>
  \-PE    7e030000-7e062000    \               winspool
ELF    7e062000-7e0c0000    Deferred        setupapi<elf>
  \-PE    7e070000-7e0c0000    \               setupapi
ELF    7e0c0000-7e133000    Deferred        rpcrt4<elf>
  \-PE    7e0d0000-7e133000    \               rpcrt4
ELF    7e133000-7e231000    Deferred        ole32<elf>
  \-PE    7e150000-7e231000    \               ole32
ELF    7e231000-7e26a000    Deferred        dinput<elf>
  \-PE    7e240000-7e26a000    \               dinput
ELF    7e26a000-7e297000    Deferred        ws2_32<elf>
  \-PE    7e270000-7e297000    \               ws2_32
ELF    7e297000-7e381000    Deferred        comctl32<elf>
  \-PE    7e2a0000-7e381000    \               comctl32
ELF    7e381000-7e55a000    Deferred        shell32<elf>
  \-PE    7e390000-7e55a000    \               shell32
ELF    7e55a000-7e5bb000    Deferred        shlwapi<elf>
  \-PE    7e570000-7e5bb000    \               shlwapi
ELF    7e5bb000-7e5df000    Deferred        mpr<elf>
  \-PE    7e5c0000-7e5df000    \               mpr
ELF    7e5df000-7e5f4000    Deferred        libz.so.1
ELF    7e5f4000-7e64f000    Deferred        wininet<elf>
  \-PE    7e600000-7e64f000    \               wininet
ELF    7e64f000-7e670000    Deferred        imm32<elf>
  \-PE    7e660000-7e670000    \               imm32
ELF    7e670000-7e7a8000    Deferred        wined3d<elf>
  \-PE    7e680000-7e7a8000    \               wined3d
ELF    7e7a8000-7e7dc000    Deferred        d3d9<elf>
  \-PE    7e7b0000-7e7dc000    \               d3d9
ELF    7e7dc000-7e7e5000    Deferred        librt.so.1
ELF    7e7e5000-7e7eb000    Deferred        libxdmcp.so.6
ELF    7e7eb000-7e807000    Deferred        libgcc_s.so.1
ELF    7e8f2000-7e8fc000    Deferred        libdrm.so.2
ELF    7e8fc000-7e902000    Deferred        libxxf86vm.so.1
ELF    7e902000-7e91c000    Deferred        libxcb.so.1
ELF    7e91c000-7e96f000    Deferred        libgl.so.1
ELF    7e96f000-7ea8c000    Deferred        libx11.so.6
ELF    7ea8c000-7ea9c000    Deferred        libxext.so.6
ELF    7ea9c000-7eab5000    Deferred        libice.so.6
ELF    7eab5000-7ead0000    Deferred        dinput8<elf>
  \-PE    7eac0000-7ead0000    \               dinput8
ELF    7ead0000-7eb74000    Deferred        opengl32<elf>
  \-PE    7eaf0000-7eb74000    \               opengl32
ELF    7eb74000-7ebce000    Deferred        advapi32<elf>
  \-PE    7eb80000-7ebce000    \               advapi32
ELF    7ebce000-7ec59000    Deferred        gdi32<elf>
  \-PE    7ebe0000-7ec59000    \               gdi32
ELF    7ec59000-7ed89000    Deferred        user32<elf>
  \-PE    7ec70000-7ed89000    \               user32
ELF    7ef89000-7ef95000    Deferred        libnss_files.so.2
ELF    7ef95000-7efa0000    Deferred        libnss_nis.so.2
ELF    7efa0000-7efb7000    Deferred        libnsl.so.1
ELF    7efb7000-7efbf000    Deferred        libnss_compat.so.2
ELF    7efbf000-7efe5000    Deferred        libm.so.6
ELF    7efe6000-7efea000    Deferred        libxau.so.6
ELF    7efea000-7eff0000    Deferred        libxfixes.so.3
ELF    7eff0000-7eff9000    Deferred        libsm.so.6
ELF    f7503000-f7507000    Deferred        libdl.so.2
ELF    f7507000-f7662000    Deferred        libc.so.6
ELF    f7663000-f767c000    Deferred        libpthread.so.0
ELF    f767c000-f7680000    Deferred        libxdamage.so.1
ELF    f7691000-f7696000    Deferred        libuuid.so.1
ELF    f7697000-f77d7000    Export          libwine.so.1
ELF    f77d9000-f77f7000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\media\1A5076105075F2BD\Program Files\World of Warcraft\Wow.exe
    00000015    0
    0000000c    0
    0000000d    0
    0000000b    0
    00000047    0
    00000046    0
    00000045    0
    00000044    0
    00000043    0
    00000042    0
    00000041    0
    00000040    0
    0000003f    0
    0000003e    0
    0000003d    0
    0000003c    0
    0000003b    0
    0000003a    0
    00000036    0
    00000034    1
    00000033    0
    00000032    1
    0000002f    0
    0000002e    0
    0000002d    0
    0000002c    0
    0000002b    2
    0000002a   15
    00000029   15
    00000027    0
    00000026    0
    00000025    0
    00000024    0
    00000023    0
    00000022    0
    00000021    0
    00000020    0
    0000001f    0
    0000001e    0
    0000001d    0
    0000001c    0
    00000009    0 <==
0000000e services.exe
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000017    0
    00000013    0
    00000012    0
00000019 explorer.exe
    0000001a    0
Backtrace:
=>0 0x00000000 (0x0032fc64)
  1 0x007c59f9 in wow (+0x3c59f8) (0x0032fcb8)
  2 0x007c5aa2 in wow (+0x3c5aa1) (0x0032fcc8)
  3 0x007a996a in wow (+0x3a9969) (0x0032fcd4)
  4 0x007a6f95 in wow (+0x3a6f94) (0x0032fcf8)
  5 0x00662c9b in wow (+0x262c9a) (0x0032fd38)
  6 0x00808469 in wow (+0x408468) (0x0032fd68)
  7 0x008054ac in wow (+0x4054ab) (0x0032fd90)
  8 0x00806b2a in wow (+0x406b29) (0x0032fde4)
  9 0x00806b71 in wow (+0x406b70) (0x0032fdfc)
  10 0x004079e8 in wow (+0x79e7) (0x0032fe90)
  11 0x7b85406c call_process_entry+0xb() in kernel32 (0x0032fea8)
  12 0x7b8564db in kernel32 (+0x464da) (0x0032fee8)
  13 0x7bc6fc80 call_thread_func+0xb() in ntdll (0x0032fef8)
  14 0x7bc6fe50 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  15 0x7bc4ae0a in ntdll (+0x3ae09) (0x0032ffe8)
Killed

My specs are: amd athlon 64 x2 dual core processor 4600+
2gb RAM
ati radeon x1650 gfx card

any help would be greatly appreciated Thank You.

---

### Post by davidmohammed on 2011-03-11
are you using wine 1.2 or wine 1.3?

---

### Post by moncrief415 on 2011-03-11
1.2.2 thats what it says in the Wine Configuration

---

### Post by ericrichards420 on 2011-03-11
The thing about wine, if you want windows programs to work right than you should stay with windows.
there is just some things wine can do, but most of the time it fails

---

### Post by davidmohammed on 2011-03-11
I would try wine 1.3 - often the latest fixes are in this version

on winehq version 4 of WOW is given a platinum rating with wine version 1.3.15

---

### Post by moncrief415 on 2011-03-11
unfortunately that didnt help it, its still doing the exact same thing 

archive Data\enUS\expansion3-speech-enUS.MPQ opened
wine: Unhandled page fault on execute access to 0x00000000 at address (nil) (thread 0050), starting debugger...
Unhandled exception: page fault on execute access to 0x00000000 in 32-bit code (0x00000000).

and i even took it a step further and changed the config.wtf and added the regestry value OpenGL and also I copyed the WOW program folder over to the .wine/drive_c/program files which made it run smoother but still crashes after i log in and load up the game.
Any suggestions on what i should do?

---

### Post by cwwilson721 on 2011-03-11
Have you installed the propriatary drivers for your ATi card/chip? (System > Administration > Additional Drivers. Not sure if ATi will do it for your card/chip, tho)

Updated to wine 1.3? (Go to wineHQ to find out how to add the 1.3 ppa)

---

### Post by moncrief415 on 2011-03-12
Whenever i go to system>administration>additional drivers nothing shows up and it says at the top that i have no proprietary drivers
i went to my xorg.conf and it says basically nothing so i got a feeling that might be the cause
i did look up how to get my ati driver and i got a x1650 i went to the ati/amd driver download site dl'd the proprietary driver ran the .run file in terminal and it says its not supported by this distribution so the Catalyst control center isnt supported by ubuntu. Thanks for the continued help on the problem tho. But does anyone know where i can find a third party driver or something that is supported by ubuntu 10.10. Cause i just keep finding in every forum i read with people with this problem for them to go to your addition drivers and get one which is no help cause when i open it, it says nothing

And i did uninstall my 1.2.2 ver of WINE and installed 1.3.5 does that mean i should still go get the 1.3 ppa?

---

### Post by Tweak42 on 2011-03-14
I looked a the AMD site and it looks like they dropped development for their Catalyst drivers for your series card (last updated 3/2009).  

There's a gap in the hardware where AMD/ATI dropped official support of the older hardware and let the open source driver pickup, but continue support for newer hardware.  I think your card falls into the older hardware area, so probably your best bet is the open source driver.  Try searching/asking for assistance in the Multimedia & Video forum on how to best get your card working for opengl.

The [Ubuntu wine PPA]("https://launchpad.net/~ubuntu-wine/+archive/ppa") maintains both 1.2 and 1.3 versions.  It's convenient to have in your repositories because the update manager will prompt for updates, no matter which version you are using.

---

### Post by IHeequ5i on 2011-03-15
Instead of copying your Windows installation of WoW, do a new install of the game using wine or PlayOnLinux. Then see if it runs.

---

### Post by Tweak42 on 2011-03-15
> **Doomspark said:**
> Instead of copying your Windows installation of WoW, do a new install of the game using wine or PlayOnLinux. Then see if it runs.

I've used the wow repair utility in wine to repair files that were corrupted.  It saved me from complete reinstall.  This was after copying a windows install over to ext4 partition because for me running on ntfs caused really long load and logout times.

---

### Post by MikeyPooh on 2011-03-18
Have You Tried To Set opengl in Your Config.wtf so that it uses Opengl And Not D3d?

---

### Post by khelben1979 on 2011-04-04
I suggest you upgrade to the latest Ubuntu (11.04) once it get's released and then you continue to use the open source AMD/ATi driver with that to see if it solves your issues.

The new open source [RADEON]("https://help.ubuntu.com/community/RadeonDriver") driver which get's shipped with newer Linux kernels works a lot better than the previous ones (uses Gallium3D), so if you got patience, I think you'll gonna see some good news (hopefully!) at the end of this month. And if not, then you should consider getting a cheap nVidia card, because those works better with Linux and especially if you go for heavier games which require the WINE software. Also, the non-free driver with nVidia is the way to go in your case.

Using open source ATi/AMD driver with Ubuntu 10.10 just doesn't make sense if you intend to play World of Warcraft with your video card, in my opinion.

---

### Post by Dupointx on 2011-04-04
My honest advice is to just dual-boot Windows if your a WoW player. It's going to save you time, trust me I know, I've been there, done that.

---

### Post by khelben1979 on 2011-04-04
> **Dupointx said:**
> My honest advice is to just dual-boot Windows if your a WoW player. It's going to save you time, trust me I know, I've been there, done that.

World of Warcraft works just fine with Ubuntu. There is no need to use Windows for that, only if he cannot accept a lower fps performance.

To some of us, using Windows is simply not an alternative.

---

### Post by Dupointx on 2011-04-04
> **khelben1979 said:**
> World of Warcraft works just fine with Ubuntu. There is no need to use Windows for that, only if he cannot accept a lower fps performance.

To some of us, using Windows is simply not an alternative.
In my opinion it's always going to be easier just using Windows, since WoW is written for it to begin with. 

There is always going to be problems with WINE since the Windows API is not fully known and WINE only reverse engineered it. Add onto this 3D rendering and the graphics required for WoW and you have a recipe for failure.

But if you *absolutely have to* use Linux then I guess it's either WINE or a couple of paid apps.

---

### Post by cwwilson721 on 2011-04-04
> **Dupointx said:**
> In my opinion it's always going to be easier just using Windows, since WoW is written for it to begin with. 

There is always going to be problems with WINE since the Windows API is not fully known and WINE only reverse engineered it. Add onto this 3D rendering and the graphics required for WoW and you have a recipe for failure.

But if you *absolutely have to* use Linux then I guess it's either WINE or a couple of paid apps.
I dual-boot Ubuntu 10.10 64bit and Windows 7 64bit Ultimate.

I *choose* to use Ubuntu/wine to play WoW because [I HAVE HIGHER FPS THAN THE SAME SETTINGS IN WIN7]("http://www.youtube.com/watch?v=xQFBK1yNIxE").

WoW is one of the programs that wine keeps running real good because of the number of people who use it. WoW does not require special dlls, or registry changes for it to work, so wine does a fantastic job.

wine did not "reverse engineer" Windows. All it does is provide open source 'hooks' for some windows apps to use. wine does not "emulate" either. The 'hooks' provided allow these apps to run on native Linux hardware, thus 3D, etc., is NOT an issue.

If you want to run Windows to play WoW, go ahead.

I'll gank you later. On my faster machine. With Linux.

---

### Post by khelben1979 on 2011-04-05
To cwwilson721: I think you're right about higher fps in World of Warcraft with Ubuntu than using Windows 7 with your pc hardware and your configuration of Windows, although everyone does not have your pc setup and so that involves other video cards which performs differently and where the performance is better with Windows 7.

You got an nVidia card and he got an ATi card. To my knowledge he would never get a higher fps with that on Linux, only going for an nVidia card makes sense in his case.

Good video b.t.w. but make sure you don't forget to mention any important details about how the Windows system is configured, that has a lot to with how the measurement was done. Recording with [FRAPS]("http://en.wikipedia.org/wiki/FRAPS") for instance slows down the performance a lot on a Windows system, just a note.

---

### Post by nitric on 2011-09-05
any new ideas? I'm having the same issue: 

```
Unhandled exception: page fault on execute access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00000000 ESP:0032fc04 EBP:0032fc64 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:000083f1 EBX:00002000 ECX:00000de1 EDX:151148b0
 ESI:00000000 EDI:0da13388
Stack dump:
0x0032fc04:  0084a995 00000de1 00000000 000083f1
0x0032fc14:  00000080 00000080 00000000 00002000
0x0032fc24:  151148b0 00000080 0da13388 00000080
0x0032fc34:  00000000 00000000 00000080 00000080
0x0032fc44:  0000813d 00000007 00000000 00000100
0x0032fc54:  151168b0 00002000 151148b0 000083f1
Backtrace:
=>0 0x00000000 (0x0032fc64)
  1 0x0084aba9 in wow (+0x44aba8) (0x0032fcb8)
  2 0x0084ac52 in wow (+0x44ac51) (0x0032fcc8)
  3 0x0082dfaa in wow (+0x42dfa9) (0x0032fcd4)
  4 0x0082b3d5 in wow (+0x42b3d4) (0x0032fcf8)
  5 0x006e9de0 in wow (+0x2e9ddf) (0x0032fd38)
  6 0x0088c819 in wow (+0x48c818) (0x0032fd68)
  7 0x0088988c in wow (+0x48988b) (0x0032fd90)
  8 0x0088aeda in wow (+0x48aed9) (0x0032fde4)
  9 0x0088af21 in wow (+0x48af20) (0x0032fdfc)
  10 0x00407d97 in wow (+0x7d96) (0x0032fe90)
  11 0x7b85856c call_process_entry+0xb() in kernel32 (0x0032fea8)
  12 0x7b85920f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  13 0x7bc72f18 call_thread_func+0xb() in ntdll (0x0032fef8)
  14 0x7bc759c0 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  15 0x7bc4a9da call_dll_entry_point+0x629() in ntdll (0x0032ffe8)
0x00000000: -- no code accessible --

```
I have wine 1.3.5

Tried using Windows 7 and Windows XP compatability.

I have a Sony Vaio VGN-NW265F
Pentium(R) Dual-Core CPU T4300 @ 2.10GHz
4 Gigs RAM
Mobile 4 Series Chipset Memory Controller Hub
Intel Mobile 4 Series Chipset Integrated Graphics Controller

tried:

wine Wow.exe and wine Wow.exe -opengl

also edited my /WTF/Config.wtf and it has SET gxApi "OpenGL"

Bummed out, don't use windows anymore but figured I'd give wow another shot with a 10 day free trial, but it crashes after loading my character, I can get logged in and select a character but once the city loads the game crashes.

---

### Post by Tweak42 on 2011-09-06
You can try the newer wine version, but the crashing is very likely caused by the poor Intel opengl graphics drivers.  I think a few people on this forum have gotten it working but performance is limited and quirky.  Intel drivers have been improving somewhat so you may have a chance, but do a thorough search on the forum before asking for help.

Also Blizzard made the wow trial unlimited time, so no worries about trying to cram 10 days of playing time in.


> **nitric said:**
> any new ideas? I'm having the same issue: 

I have wine 1.3.5

Tried using Windows 7 and Windows XP compatability.

I have a Sony Vaio VGN-NW265F
Pentium(R) Dual-Core CPU T4300 @ 2.10GHz
4 Gigs RAM
Mobile 4 Series Chipset Memory Controller Hub
Intel Mobile 4 Series Chipset Integrated Graphics Controller

tried:

wine Wow.exe and wine Wow.exe -opengl

also edited my /WTF/Config.wtf and it has SET gxApi "OpenGL"

Bummed out, don't use windows anymore but figured I'd give wow another shot with a 10 day free trial, but it crashes after loading my character, I can get logged in and select a character but once the city loads the game crashes.

---

### Post by kyletstrand on 2011-09-06
I had a similar issue a while back and I found this info straight from Blizzard that fixed any and all WoW crashes I was having.

Might be worth a try.

[http://us.battle.net/wow/en/forum/topic/2592648266](http://us.battle.net/wow/en/forum/topic/2592648266)

---

### Post by cwwilson721 on 2011-09-07
> **khelben1979 said:**
> To cwwilson721: I think you're right about higher fps in World of Warcraft with Ubuntu than using Windows 7 with your pc hardware and your configuration of Windows, although everyone does not have your pc setup and so that involves other video cards which performs differently and where the performance is better with Windows 7.

You got an nVidia card and he got an ATi card. To my knowledge he would never get a higher fps with that on Linux, only going for an nVidia card makes sense in his case.

Good video b.t.w. but make sure you don't forget to mention any important details about how the Windows system is configured, that has a lot to with how the measurement was done. Recording with [FRAPS]("http://en.wikipedia.org/wiki/FRAPS") for instance slows down the performance a lot on a Windows system, just a note.
It's stated in the notes of the video:

Same box
Same settings
ONLY diff is wine/WoW uses OpenGL, Win7 uses D3D
All other settings EXACTLY the same.

---

### Post by marams on 2011-12-14
try

```
export force_s3tc_enable=true
```this should solve the problem.

GL_EXT_texture_compression_s3tc is not (yet) implemented in Mesa due to patent stuff.

---

