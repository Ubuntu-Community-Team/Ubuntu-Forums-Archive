---
title: "C &amp; C tiberian sun"
date: 2010-03-27
forum: Wine
---

### Post by JoeWheeler on 2010-03-27
HI guys, I'm currently trying to get the free(and legal) tiberian sun to work under wine. I had to import the registry settings which I think worked but when i run game.exe it puts the tiberian sun icon in my lower panel and hangs.

Heres the output when i run it as "wine game.exe" from terminal:
```
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:vxd:VXD_Open Unknown/unsupported VxD L"mono.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"mono.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"mono.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"mono.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"mono.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:keyboard:RegisterHotKey (0x10032,1,0x00000007,77): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x159d88,0x159cd0): stub
fixme:dsalsa:CheckXRUN Unhandled state: 0
mixer.c:306: DSOUND_BufPtrDiff: Assertion `ptr2 < buflen' failed.
wine: Assertion failed at address 0x68000832 (thread 0021), starting debugger...
Unhandled exception: assertion failed in 32-bit code (0x68000832).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:68000832 ESP:0181e78c EBP:0181e798 EFLAGS:00200206(   - --  I   - -P- )
 EAX:00000000 EBX:0000094d ECX:00000965 EDX:00000006
 ESI:68290f5d EDI:682b1ff4
Stack dump:
0x0181e78c:  6819b4d1 682b1ff4 0181e8b8 0181e8c0
0x0181e79c:  6819e932 00000006 0181e838 00000000
0x0181e7ac:  681e185d 00000068 00000048 0181e7e0
0x0181e7bc:  0181e8d0 0181e7fc 00000068 00000048
0x0181e7cc:  00000043 7c5ceb48 682b1ff4 00000043
0x0181e7dc:  00000042 0181e8a8 681d0bc2 7c5ceb50
Backtrace:
=>0 0x68000832 GLIBC_2+0x832() in ld-linux.so.2 (0x0181e798)
  1 0x6819e932 abort+0x182() in libc.so.6 (0x0181e8c0)
  2 0x68194648 __assert_fail+0xf8() in libc.so.6 (0x0181e908)
  3 0x68bdd395 DSOUND_timer+0x1495() in dsound (0x0181e9e8)
  4 0x68a8e810 in winmm (+0x2e810) (0x0181ea68)
  5 0x7bc6b594 call_thread_func+0xc() in ntdll (0x0181ea78)
  6 0x7bc6b7a0 call_thread_entry_point+0x70() in ntdll (0x0181eb48)
  7 0x7bc739e5 in ntdll (+0x639e5) (0x0181f398)
  8 0x6815d80e start_thread+0xbe() in libpthread.so.0 (0x0181f498)
  9 0x6823d8de __clone+0x5e() in libc.so.6 (0x00000000)
0x68000832 GLIBC_2+0x832 in ld-linux.so.2: ret    
fixme:win:EnumDisplayDevicesW ((null),0,0x32edf0,0x00000000), stub!
Modules:
Module    Address            Debug info    Name (109 modules)
PE      400000-  86d000    Deferred        game
PE    10000000-1001e000    Deferred        language
PE    11000000-1102b000    Deferred        blowfish
ELF    20000000-20064000    Deferred        libgl.so.1
ELF    3222e000-32238000    Deferred        libdrm_intel.so.1
ELF    48b1d000-48dad000    Deferred        i915_dri.so
ELF    4b300000-4b303000    Deferred        libxdamage.so.1
ELF    6146a000-61474000    Deferred        libdrm.so.2
ELF    68000000-6801d000    Export          ld-linux.so.2
ELF    6801d000-68158000    Deferred        libwine.so.1
ELF    68158000-68171000    Export          libpthread.so.0
ELF    68171000-682b6000    Export          libc.so.6
ELF    682b6000-682ba000    Deferred        libdl.so.2
ELF    682ba000-682e0000    Deferred        libm.so.6
ELF    682e0000-682e8000    Deferred        libnss_compat.so.2
ELF    682e8000-682ff000    Deferred        libnsl.so.1
ELF    682ff000-6830a000    Deferred        libnss_nis.so.2
ELF    6830a000-68316000    Deferred        libnss_files.so.2
ELF    68316000-68461000    Deferred        user32<elf>
  \-PE    68330000-68461000    \               user32
ELF    68461000-68501000    Deferred        gdi32<elf>
  \-PE    68470000-68501000    \               gdi32
ELF    68501000-68558000    Deferred        advapi32<elf>
  \-PE    68510000-68558000    \               advapi32
ELF    68558000-686e8000    Deferred        shell32<elf>
  \-PE    68570000-686e8000    \               shell32
ELF    686e8000-68745000    Deferred        shlwapi<elf>
  \-PE    68700000-68745000    \               shlwapi
ELF    68745000-6880d000    Deferred        comctl32<elf>
  \-PE    68750000-6880d000    \               comctl32
ELF    6880d000-68908000    Deferred        ole32<elf>
  \-PE    68830000-68908000    \               ole32
ELF    68908000-68975000    Deferred        rpcrt4<elf>
  \-PE    68910000-68975000    \               rpcrt4
ELF    68975000-68a58000    Deferred        oleaut32<elf>
  \-PE    68990000-68a58000    \               oleaut32
ELF    68a58000-68af4000    Export          winmm<elf>
  \-PE    68a60000-68af4000    \               winmm
ELF    68af4000-68b0f000    Deferred        wsock32<elf>
  \-PE    68b00000-68b0f000    \               wsock32
ELF    68b0f000-68b39000    Deferred        ws2_32<elf>
  \-PE    68b20000-68b39000    \               ws2_32
ELF    68b39000-68b59000    Deferred        iphlpapi<elf>
  \-PE    68b40000-68b59000    \               iphlpapi
ELF    68b59000-68bb0000    Deferred        ddraw<elf>
  \-PE    68b60000-68bb0000    \               ddraw
ELF    68bb0000-68bfc000    Export          dsound<elf>
  \-PE    68bc0000-68bfc000    \               dsound
ELF    68bfc000-68c16000    Deferred        version<elf>
  \-PE    68c00000-68c16000    \               version
ELF    68c16000-68c2a000    Deferred        lz32<elf>
  \-PE    68c20000-68c2a000    \               lz32
ELF    68c2a000-68c3f000    Deferred        system.drv16.so
PE    68c30000-68c3f000    Deferred        system.drv16
ELF    68c3f000-68cbe000    Deferred        libfreetype.so.6
ELF    68cbe000-68cd4000    Deferred        libz.so.1
ELF    68cd4000-68d01000    Deferred        libfontconfig.so.1
ELF    68d01000-68d28000    Deferred        libexpat.so.1
ELF    68d28000-68d3d000    Deferred        keyboard.drv16.so
PE    68d30000-68d3d000    Deferred        keyboard.drv16
ELF    68d3d000-68ddb000    Deferred        winex11<elf>
  \-PE    68d50000-68ddb000    \               winex11
ELF    68ddb000-68de4000    Deferred        libsm.so.6
ELF    68de4000-68dff000    Deferred        libice.so.6
ELF    68dff000-68e0f000    Deferred        libxext.so.6
ELF    68e0f000-68f3e000    Deferred        libx11.so.6
ELF    68f3e000-68f43000    Deferred        libuuid.so.1
ELF    68f43000-68f47000    Deferred        libxau.so.6
ELF    68f47000-68f65000    Deferred        libxcb.so.1
ELF    68f65000-68f6a000    Deferred        libxdmcp.so.6
ELF    68f6a000-68f8b000    Deferred        imm32<elf>
  \-PE    68f70000-68f8b000    \               imm32
ELF    68f8b000-68f8e000    Deferred        libxinerama.so.1
ELF    68f8e000-68f98000    Deferred        libxrender.so.1
ELF    68f98000-68fa1000    Deferred        libxrandr.so.2
ELF    68fa1000-68fa5000    Deferred        libxcomposite.so.1
ELF    68fa5000-68fab000    Deferred        libxfixes.so.3
ELF    68fab000-68fb6000    Deferred        libxcursor.so.1
ELF    68fb6000-68fe9000    Deferred        uxtheme<elf>
  \-PE    68fc0000-68fe9000    \               uxtheme
ELF    68fe9000-69020000    Deferred        winealsa<elf>
  \-PE    68ff0000-69020000    \               winealsa
ELF    69020000-690e7000    Deferred        libasound.so.2
ELF    690ea000-6912a000    Deferred        libpulse.so.0
ELF    6912a000-69174000    Deferred        libpulsecommon-0.9.19.so
ELF    69174000-691e0000    Deferred        libsndfile.so.1
ELF    691e0000-69219000    Deferred        libdbus-1.so.3
ELF    69219000-69269000    Deferred        libflac.so.8
ELF    69269000-69365000    Deferred        libvorbisenc.so.2
ELF    69365000-6938e000    Deferred        libvorbis.so.0
ELF    6938e000-69395000    Deferred        libogg.so.0
ELF    69395000-693ad000    Deferred        msacm32<elf>
  \-PE    693a0000-693ad000    \               msacm32
ELF    693ad000-693d3000    Deferred        msacm32<elf>
  \-PE    693b0000-693d3000    \               msacm32
ELF    693d3000-693e9000    Deferred        midimap<elf>
  \-PE    693e0000-693e9000    \               midimap
ELF    6c0f8000-6c227000    Deferred        wined3d<elf>
  \-PE    6c100000-6c227000    \               wined3d
ELF    6fe12000-6fe1b000    Deferred        librt.so.1
ELF    73269000-73272000    Deferred        libwrap.so.0
ELF    7419c000-741b0000    Deferred        libresolv.so.2
ELF    74b86000-74b8c000    Deferred        libxxf86vm.so.1
ELF    7ad88000-7ad8e000    Deferred        libxtst.so.6
ELF    7b800000-7b971000    Deferred        kernel32<elf>
  \-PE    7b820000-7b971000    \               kernel32
ELF    7bc00000-7bcb1000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb1000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\EA Games\Command & Conquer The First Decade\Command & Conquer(tm) Tiberian Sun(tm)\SUN\game.exe
    00000021   15 <==
    0000001a    0
    00000009    0
0000000e 
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
    00000019    0
0000001b 
    00000020    0
    0000001f    0
    0000001e    0
    0000001d    0
    0000001c    0
Backtrace:
=>0 0x68000832 GLIBC_2+0x832() in ld-linux.so.2 (0x0181e798)
  1 0x6819e932 abort+0x182() in libc.so.6 (0x0181e8c0)
  2 0x68194648 __assert_fail+0xf8() in libc.so.6 (0x0181e908)
  3 0x68bdd395 DSOUND_timer+0x1495() in dsound (0x0181e9e8)
  4 0x68a8e810 in winmm (+0x2e810) (0x0181ea68)
  5 0x7bc6b594 call_thread_func+0xc() in ntdll (0x0181ea78)
  6 0x7bc6b7a0 call_thread_entry_point+0x70() in ntdll (0x0181eb48)
  7 0x7bc739e5 in ntdll (+0x639e5) (0x0181f398)
  8 0x6815d80e start_thread+0xbe() in libpthread.so.0 (0x0181f498)
  9 0x6823d8de __clone+0x5e() in libc.so.6 (0x00000000)
Aborted

```

Heres EAs website where i downloaded it: [http://www.commandandconquer.com/classic](http://www.commandandconquer.com/classic)
Any help would be appreciated

---

### Post by JoeWheeler on 2010-03-27
I'm also trying to install c & c gold but whenever i run the setup.exe it says "unable to locate the necessary files" heres the output from when i tried using wine cmd prompt:

```
joe@laptop:~$ wine cmd
CMD Version 1.1.41


Z:\home\joe>d:

D:\>setup.exe

D:\>fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
err:ntdll:RtlpWaitForCriticalSection section 0x684aa760 "syslevel.c: Win16Mutex" wait timed out in thread 001a, blocked by 001d, retrying (60 sec)
fixme:win:LockWindowUpdate (0x20052), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!

```

---

### Post by JoeWheeler on 2010-03-27
OK so i managed to install C and C gold but i can't get it to actually play, anyone no how to find out what's wrong with it?... I've also tried it in dosbox but to no avail :/

I think I might just give up and stick to playing red alert through dosbox

---

