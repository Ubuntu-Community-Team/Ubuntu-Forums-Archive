---
title: "Please help -- Hitman Blood Money won't start at all"
date: 2009-07-03
forum: Wine
---

### Post by Leopardson on 2009-07-03
Hi,
I have looked all over WineHQ and the forums. I have not found a solution to the following problem and seem to be the only one on earth with the problem.

Whenever I try to start Hitman: Blood Money through the executable OR config.exe, I get a "HitmanBloodMoney has a encountered a serious problem and needs to close" error. 

My wine version is 1.1.2.5. I have also tried this game in 1.1.2.4 and 1.1.0 getting the same error every time.
My wine has no overrides or changed settings and everything is default. The emulated OS is Windows XP though I have tried both Windows Vista and Windows 2000.

According to WineHQ, the game must be started through config.exe.
This is the error I get:

```

wine configure.exe
leopardson@Probably-not-hacking-your-network:~/.wine/dosdevices/c:/Program Files/Eidos/Hitman Blood Money$ fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x12482f4): Stub!
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0x1246748,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x12462c8,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0xb40800, 0x12293e0) stub
fixme:psapi:EnumPageFilesA (0xb40800, 0x11f7908) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d0c04 (device=2d access=0 func=301 method=0)
wine: Unhandled page fault on read access to 0x00000000 at address 0xd2bcbc (thread 001a), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00d2bcbc).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00d2bcbc ESP:01221888 EBP:012221f8 EFLAGS:00210296(  R- --  I S -A-P- )
 EAX:00000000 EBX:00000000 ECX:7bc94da4 EDX:ffffffff
 ESI:00eee984 EDI:00eee984
Stack dump:
0x01221888:  0000008c 00000072 00ef09b4 00d2712a
0x01221898:  012221c4 00ef09ac 01222218 01222624
0x012218a8:  0000000e 00000000 01226967 00000000
0x012218b8:  00000000 00000000 00000000 00000000
0x012218c8:  00000000 00000000 00000000 00000000
0x012218d8:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x00d2bcbc in hitmanbloodmoney (+0x92bcbc) (0x012221f8)
  1 0x00d2eb70 in hitmanbloodmoney (+0x92eb70) (0x01222a20)
  2 0x00d01d20 in hitmanbloodmoney (+0x901d20) (0x01226974)
  3 0x00d0be53 in hitmanbloodmoney (+0x90be53) (0x0122d304)
  4 0x0122d304 (0x00fdb840)
  5 0x009d5352 in hitmanbloodmoney (+0x5d5352) (0x009d51f4)
  6 0xe18bb035 (0x39f63356)
  7 0x00000000 (0x00000000)
0x00d2bcbc: cmpb    $0x0,0x0(%ebx)
Modules:
Module    Address            Debug info    Name (107 modules)
PE      400000- 1053000    Export          hitmanbloodmoney
PE     1260000- 14af000    Deferred        d3dx9_27
PE    30000000-3006d000    Deferred        binkw32
ELF    7a29c000-7b800000    Deferred        fglrx_dri.so
ELF    7b800000-7b954000    Deferred        kernel32<elf>
  \-PE    7b820000-7b954000    \               kernel32
ELF    7bc00000-7bcb1000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb1000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7cd9b000-7cdb1000    Deferred        psapi<elf>
  \-PE    7cda0000-7cdb1000    \               psapi
ELF    7ce6c000-7ce95000    Deferred        libatiadlxx.so
ELF    7d5ab000-7d5ba000    Deferred        libgcc_s.so.1
ELF    7d5ba000-7d648000    Deferred        libgl.so.1
ELF    7d68f000-7d6c2000    Deferred        uxtheme<elf>
  \-PE    7d6a0000-7d6c2000    \               uxtheme
ELF    7d6c2000-7d6e8000    Deferred        msacm32<elf>
  \-PE    7d6d0000-7d6e8000    \               msacm32
ELF    7d6e8000-7d700000    Deferred        msacm32<elf>
  \-PE    7d6f0000-7d700000    \               msacm32
ELF    7df01000-7df07000    Deferred        libattr.so.1
ELF    7df07000-7df66000    Deferred        libpulse.so.0
ELF    7df67000-7df7c000    Deferred        midimap<elf>
  \-PE    7df70000-7df7c000    \               midimap
ELF    7df7c000-7df85000    Deferred        librt.so.1
ELF    7df85000-7e04d000    Deferred        libasound.so.2
ELF    7e050000-7e057000    Deferred        libgdbm.so.3
ELF    7e057000-7e05c000    Deferred        libcap.so.2
ELF    7e05c000-7e063000    Deferred        libasound_module_pcm_pulse.so
ELF    7e063000-7e09a000    Deferred        winealsa<elf>
  \-PE    7e070000-7e09a000    \               winealsa
ELF    7e0ae000-7e0b7000    Deferred        libxcursor.so.1
ELF    7e0b7000-7e0bc000    Deferred        libxfixes.so.3
ELF    7e0bc000-7e0c0000    Deferred        libxcomposite.so.1
ELF    7e0c0000-7e0c8000    Deferred        libxrandr.so.2
ELF    7e0c8000-7e0d2000    Deferred        libxrender.so.1
ELF    7e0d2000-7e0d8000    Deferred        libxxf86vm.so.1
ELF    7e0d8000-7e0db000    Deferred        libxinerama.so.1
ELF    7e0db000-7e0fc000    Deferred        imm32<elf>
  \-PE    7e0e0000-7e0fc000    \               imm32
ELF    7e0fc000-7e101000    Deferred        libxdmcp.so.6
ELF    7e101000-7e11b000    Deferred        libxcb.so.1
ELF    7e11b000-7e11f000    Deferred        libxau.so.6
ELF    7e11f000-7e124000    Deferred        libuuid.so.1
ELF    7e124000-7e213000    Deferred        libx11.so.6
ELF    7e213000-7e223000    Deferred        libxext.so.6
ELF    7e223000-7e23b000    Deferred        libice.so.6
ELF    7e23b000-7e244000    Deferred        libsm.so.6
ELF    7e25a000-7e2f6000    Deferred        winex11<elf>
  \-PE    7e270000-7e2f6000    \               winex11
ELF    7e343000-7e36a000    Deferred        libexpat.so.1
ELF    7e36a000-7e397000    Deferred        libfontconfig.so.1
ELF    7e397000-7e3ad000    Deferred        libz.so.1
ELF    7e3ad000-7e424000    Deferred        libfreetype.so.6
ELF    7e424000-7e43a000    Deferred        libresolv.so.2
ELF    7e450000-7e470000    Deferred        iphlpapi<elf>
  \-PE    7e460000-7e470000    \               iphlpapi
ELF    7e470000-7e48b000    Deferred        wsock32<elf>
  \-PE    7e480000-7e48b000    \               wsock32
ELF    7e48b000-7e4a6000    Deferred        version<elf>
  \-PE    7e490000-7e4a6000    \               version
ELF    7e4a6000-7e56e000    Deferred        comctl32<elf>
  \-PE    7e4b0000-7e56e000    \               comctl32
ELF    7e56e000-7e5cc000    Deferred        shlwapi<elf>
  \-PE    7e580000-7e5cc000    \               shlwapi
ELF    7e5cc000-7e758000    Deferred        shell32<elf>
  \-PE    7e5e0000-7e758000    \               shell32
ELF    7e758000-7e786000    Deferred        ws2_32<elf>
  \-PE    7e760000-7e786000    \               ws2_32
ELF    7e786000-7e7a5000    Deferred        msvcr71<elf>
  \-PE    7e790000-7e7a5000    \               msvcr71
ELF    7e7a5000-7e814000    Deferred        msvcrt<elf>
  \-PE    7e7c0000-7e814000    \               msvcrt
ELF    7e814000-7e8ab000    Deferred        winmm<elf>
  \-PE    7e820000-7e8ab000    \               winmm
ELF    7e8ab000-7e8f8000    Deferred        dsound<elf>
  \-PE    7e8b0000-7e8f8000    \               dsound
ELF    7e8f8000-7e965000    Deferred        rpcrt4<elf>
  \-PE    7e900000-7e965000    \               rpcrt4
ELF    7e965000-7ea60000    Deferred        ole32<elf>
  \-PE    7e980000-7ea60000    \               ole32
ELF    7ea60000-7ea99000    Deferred        dinput<elf>
  \-PE    7ea70000-7ea99000    \               dinput
ELF    7ea99000-7eab3000    Deferred        dinput8<elf>
  \-PE    7eaa0000-7eab3000    \               dinput8
ELF    7eab3000-7ebe3000    Deferred        wined3d<elf>
  \-PE    7ead0000-7ebe3000    \               wined3d
ELF    7ebe3000-7ec14000    Deferred        d3d9<elf>
  \-PE    7ebf0000-7ec14000    \               d3d9
ELF    7ec14000-7ec6a000    Deferred        advapi32<elf>
  \-PE    7ec20000-7ec6a000    \               advapi32
ELF    7ec6a000-7ed0b000    Deferred        gdi32<elf>
  \-PE    7ec80000-7ed0b000    \               gdi32
ELF    7ed0b000-7ee56000    Deferred        user32<elf>
  \-PE    7ed20000-7ee56000    \               user32
ELF    7ee56000-7ee62000    Deferred        libnss_files.so.2
ELF    7ee62000-7ee7b000    Deferred        libnsl.so.1
ELF    7ee7b000-7ee84000    Deferred        libnss_compat.so.2
ELF    7ee86000-7ee9a000    Deferred        lz32<elf>
  \-PE    7ee90000-7ee9a000    \               lz32
ELF    7efc4000-7efea000    Deferred        libm.so.6
ELF    7eff5000-7f000000    Deferred        libnss_nis.so.2
ELF    b7de1000-b7de5000    Deferred        libdl.so.2
ELF    b7de5000-b7f48000    Deferred        libc.so.6
ELF    b7f49000-b7f62000    Deferred        libpthread.so.0
ELF    b7f78000-b80b3000    Deferred        libwine.so.1
ELF    b80b5000-b80d3000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
    00000016    0
    00000013    0
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    00000015    0
    00000014    0
    00000011    0
    00000010    0
00000017 
    00000018    0
00000019 (D) C:\Program Files\Eidos\Hitman Blood Money\HitmanBloodMoney.exe
    0000001a    0 <==
Backtrace:
=>0 0x00d2bcbc in hitmanbloodmoney (+0x92bcbc) (0x012221f8)
  1 0x00d2eb70 in hitmanbloodmoney (+0x92eb70) (0x01222a20)
  2 0x00d01d20 in hitmanbloodmoney (+0x901d20) (0x01226974)
  3 0x00d0be53 in hitmanbloodmoney (+0x90be53) (0x0122d304)
  4 0x0122d304 (0x00fdb840)
  5 0x009d5352 in hitmanbloodmoney (+0x5d5352) (0x009d51f4)
  6 0xe18bb035 (0x39f63356)
  7 0x00000000 (0x00000000)

```
Specs:
Ubuntu 9.04 Jaunty
AMD Sempron 3100+ (Irrelevant)
1GB DDR Ram, memtested (Probably Irrelevant)
ATi Radeon HD 3650 1GB (This is probably relevant)
ATi drivers 9.6 (Latest Drivers)

If you help me solve my problem, I'll post you 3 Lolcats.

---

### Post by Th3_uN1Qu3 on 2009-07-04
I have the same issue with a lot of things that should work (eg: Photoshop CS3, that was supposed to be fixed a few releases ago, doesn't even install for me). Maybe the Catalyst drivers are somehow at fault? Though, what would drivers have to do with a setup program...

---

### Post by Leopardson on 2009-07-06
I don't think it's likely to be catalyst as I switched from 9.4 to 9.6 in an attempt to fix this.
[conspiracytheory]Then again, it could be a nasty move by Microsoft in an attempt to turn us  to Windows.[/conspiracytheory]

---

### Post by alexandervanhoorn on 2009-07-10
What works for me is overriding [d3dx9_27.dll]("http://www.dll-files.com/dllindex/dll-files.shtml?d3dx9_27") and [d3dx9_36.dll]("http://www.dll-files.com/dllindex/dll-files.shtml?d3dx9_36").

To do this, first download those dll's and place them in your hitman dir. (I'll assume it's ~/.wine/drive_c/Program Files/Eidos/Hitman Blood Money/.). Then use

```
cd ~/.wine/drive_c/Program\ Files/Eidos/Hitman\ Blood\ Money/

winecfg
```

and go to the libraries tab, new override for library, add d3dx9_27 and d3dx9_36, OK. Then run wine HitmanBloodMoney.exe. If the game runs it will be very slow, so you will want to set "post effects" to "disabled" in the options menu to make everything faster. Don't change the resolution from the main menu or it will crash.

PS: if you don't want your wine tweaks for hitman blood money to interfere with other programs in wine, add env WINEPREFIX="$HOME/.wine-hm4/" before all commands (including the installer), so wine will use a clean environment for hitman blood money. Also, don't install directx from the game installer.

Good luck.

---

