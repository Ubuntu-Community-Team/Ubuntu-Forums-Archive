---
title: "Keychamp 2.0 not running"
date: 2010-11-13
forum: Wine
---

### Post by koolblue3 on 2010-11-13
Hello,

I need Keychamp 2.0 for a school class. It installs, but does not run. Here is what happens when I try to run it "Unhandled exception: c0000005 At address: f756bcca." Wine then pops up saying that the program encountered an error and needs to close. I then tell it to close. It will then pop up saying the same thing as the first unhandled exception. Here is the terminal output if I try to run it from there ```
wine: Unhandled page fault on write access to 0x00c91000 at address 0xf752ccca (thread 0063), starting debugger...
Unhandled exception: page fault on write access to 0x00c91000 in 32-bit code (0xf752ccca).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:f752ccca ESP:0032f0e8 EBP:0032f178 EFLAGS:00010206(  R- --  I   - -P- )
 EAX:00b5a068 EBX:f756eff4 ECX:0004af60 EDX:00c90fa0
 ESI:00170dd0 EDI:00000001
Stack dump:
0x0032f0e8:  7ea7cff4 7ea6f794 00bb0000 00a79048
0x0032f0f8:  0012c000 000001e0 00a79020 ffffffff
0x0032f108:  ffffffff 00000000 0000000c 000044a1
0x0032f118:  0032f208 00000040 0032f180 7bc344a1
0x0032f128:  00000044 0032f1bc 0032f180 7ead18a0
0x0032f138:  00000044 0000000c 00320018 7eaf9ff4
Backtrace:
=>0 0xf752ccca in libc.so.6 (+0x113cca) (0x0032f178)
  1 0x004236e9 in keychamp (+0x236e8) (0x0032f288)
  2 0x00424473 in keychamp (+0x24472) (0x0032f540)
  3 0x00422d14 in keychamp (+0x22d13) (0x0032f570)
  4 0x0042312e in keychamp (+0x2312d) (0x0032f618)
  5 0x00423353 in keychamp (+0x23352) (0x0032f638)
  6 0x004233b6 in keychamp (+0x233b5) (0x0032f65c)
  7 0x00424839 in keychamp (+0x24838) (0x0032f6b8)
  8 0x7ebbbc8a WINPROC_wrapper+0x19() in user32 (0x0032f6e8)
  9 0x7ebbd79c in user32 (+0x9d79b) (0x0032f738)
  10 0x7ebbeaef in user32 (+0x9eaee) (0x0032f788)
  11 0x7eb80fc1 in user32 (+0x60fc0) (0x0032f7f8)
  12 0x7eb856b6 in user32 (+0x656b5) (0x0032f878)
  13 0x7eb85b03 SendMessageA+0x52() in user32 (0x0032f8c8)
  14 0x7ebb3ebd in user32 (+0x93ebc) (0x0032fab8)
  15 0x7ebad3da CreateWindowExA+0x89() in user32 (0x0032fd28)
  16 0x004234d9 in keychamp (+0x234d8) (0x0032fd90)
  17 0x0042366b in keychamp (+0x2366a) (0x0032fd9c)
  18 0x00448b8b in keychamp (+0x48b8a) (0x0032fde8)
  19 0x0046902e in keychamp (+0x6902d) (0x0032fe90)
  20 0x7b85430c call_process_entry+0xb() in kernel32 (0x0032fea8)
  21 0x7b85653b in kernel32 (+0x4653a) (0x0032fee8)
  22 0x7bc6f950 call_thread_func+0xb() in ntdll (0x0032fef8)
  23 0x7bc6fb20 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  24 0x7bc4aa8a in ntdll (+0x3aa89) (0x0032ffe8)
0xf752ccca: movntq    %mm6,0x60(%edx)
Modules:
Module    Address            Debug info    Name (109 modules)
PE      400000-  969000    Export          keychamp
ELF    7b800000-7b971000    Export          kernel32<elf>
  \-PE    7b810000-7b971000    \               kernel32
ELF    7bc00000-7bcb7000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d8f2000-7d90a000    Deferred        iccvid<elf>
  \-PE    7d900000-7d90a000    \               iccvid
ELF    7d90a000-7d920000    Deferred        midimap<elf>
  \-PE    7d910000-7d920000    \               midimap
ELF    7d920000-7d939000    Deferred        msacm32<elf>
  \-PE    7d930000-7d939000    \               msacm32
ELF    7d939000-7d940000    Deferred        libogg.so.0
ELF    7d940000-7d968000    Deferred        libvorbis.so.0
ELF    7d968000-7dae0000    Deferred        libvorbisenc.so.2
ELF    7dae0000-7db2c000    Deferred        libflac.so.8
ELF    7db2c000-7db94000    Deferred        libsndfile.so.1
ELF    7db94000-7db9d000    Deferred        libwrap.so.0
ELF    7db9d000-7dbab000    Deferred        libxi.so.6
ELF    7dbab000-7dbf5000    Deferred        libpulsecommon-0.9.21.so
ELF    7dbf5000-7dbfa000    Deferred        libxcb-atom.so.1
ELF    7dbfa000-7dc00000    Deferred        libxtst.so.6
ELF    7dc00000-7dc03000    Deferred        libx11-xcb.so.1
ELF    7dc03000-7dc45000    Deferred        libpulse.so.0
ELF    7dc48000-7dd0e000    Deferred        libasound.so.2
ELF    7dd0e000-7dd45000    Deferred        winealsa<elf>
  \-PE    7dd20000-7dd45000    \               winealsa
ELF    7dd45000-7dd4e000    Deferred        librt.so.1
ELF    7dd4e000-7dd8a000    Deferred        libdbus-1.so.3
ELF    7dd8a000-7dd8f000    Deferred        libgpg-error.so.0
ELF    7dd8f000-7dda0000    Deferred        libtasn1.so.3
ELF    7dda0000-7ddb4000    Deferred        libresolv.so.2
ELF    7ddb4000-7ddb8000    Deferred        libkeyutils.so.1
ELF    7ddb8000-7dddc000    Deferred        libk5crypto.so.3
ELF    7dddc000-7de8a000    Deferred        libkrb5.so.3
ELF    7de8a000-7de9a000    Deferred        libavahi-client.so.3
ELF    7de9a000-7dea6000    Deferred        libavahi-common.so.3
ELF    7dea6000-7df1a000    Deferred        libgcrypt.so.11
ELF    7df1a000-7dfb5000    Deferred        libgnutls.so.26
ELF    7dfb5000-7dfe4000    Deferred        libgssapi_krb5.so.2
ELF    7dfe4000-7e02e000    Deferred        libcups.so.2
ELF    7e040000-7e046000    Deferred        libasound_module_pcm_pulse.so
ELF    7e0cf000-7e103000    Deferred        uxtheme<elf>
  \-PE    7e0e0000-7e103000    \               uxtheme
ELF    7e103000-7e10d000    Deferred        libxcursor.so.1
ELF    7e10d000-7e113000    Deferred        libxfixes.so.3
ELF    7e113000-7e117000    Deferred        libxcomposite.so.1
ELF    7e117000-7e11f000    Deferred        libxrandr.so.2
ELF    7e11f000-7e129000    Deferred        libxrender.so.1
ELF    7e129000-7e12f000    Deferred        libxxf86vm.so.1
ELF    7e12f000-7e133000    Deferred        libxinerama.so.1
ELF    7e133000-7e154000    Deferred        imm32<elf>
  \-PE    7e140000-7e154000    \               imm32
ELF    7e154000-7e15a000    Deferred        libxdmcp.so.6
ELF    7e15a000-7e15e000    Deferred        libxau.so.6
ELF    7e15e000-7e178000    Deferred        libxcb.so.1
ELF    7e178000-7e17d000    Deferred        libuuid.so.1
ELF    7e17d000-7e29a000    Deferred        libx11.so.6
ELF    7e29a000-7e2aa000    Deferred        libxext.so.6
ELF    7e2aa000-7e2c3000    Deferred        libice.so.6
ELF    7e2c3000-7e2cc000    Deferred        libsm.so.6
ELF    7e2cc000-7e2d4000    Deferred        libkrb5support.so.0
ELF    7e2e0000-7e2e4000    Deferred        libcom_err.so.2
ELF    7e2e4000-7e385000    Deferred        winex11<elf>
  \-PE    7e2f0000-7e385000    \               winex11
ELF    7e3b4000-7e3db000    Deferred        libexpat.so.1
ELF    7e3db000-7e40b000    Deferred        libfontconfig.so.1
ELF    7e40b000-7e420000    Deferred        libz.so.1
ELF    7e420000-7e497000    Deferred        libfreetype.so.6
ELF    7e4af000-7e4e6000    Deferred        winspool<elf>
  \-PE    7e4c0000-7e4e6000    \               winspool
ELF    7e4e6000-7e5a0000    Deferred        comdlg32<elf>
  \-PE    7e4f0000-7e5a0000    \               comdlg32
ELF    7e5a0000-7e601000    Deferred        shlwapi<elf>
  \-PE    7e5b0000-7e601000    \               shlwapi
ELF    7e601000-7e7de000    Deferred        shell32<elf>
  \-PE    7e610000-7e7de000    \               shell32
ELF    7e7de000-7e801000    Deferred        mpr<elf>
  \-PE    7e7e0000-7e801000    \               mpr
ELF    7e801000-7e874000    Deferred        rpcrt4<elf>
  \-PE    7e810000-7e874000    \               rpcrt4
ELF    7e874000-7e972000    Deferred        ole32<elf>
  \-PE    7e890000-7e972000    \               ole32
ELF    7e972000-7ea5c000    Deferred        comctl32<elf>
  \-PE    7e980000-7ea5c000    \               comctl32
ELF    7ea5c000-7ea83000    Deferred        msvfw32<elf>
  \-PE    7ea60000-7ea83000    \               msvfw32
ELF    7ea83000-7eb0e000    Deferred        gdi32<elf>
  \-PE    7ea90000-7eb0e000    \               gdi32
ELF    7eb0e000-7ec3e000    Export          user32<elf>
  \-PE    7eb20000-7ec3e000    \               user32
ELF    7ec3e000-7eccf000    Deferred        winmm<elf>
  \-PE    7ec50000-7eccf000    \               winmm
ELF    7eccf000-7ecf5000    Deferred        msacm32<elf>
  \-PE    7ece0000-7ecf5000    \               msacm32
ELF    7ecf5000-7ed32000    Deferred        avifil32<elf>
  \-PE    7ed00000-7ed32000    \               avifil32
ELF    7ed32000-7ed8c000    Deferred        advapi32<elf>
  \-PE    7ed40000-7ed8c000    \               advapi32
ELF    7ef8c000-7ef98000    Deferred        libnss_files.so.2
ELF    7ef98000-7efa3000    Deferred        libnss_nis.so.2
ELF    7efa3000-7efba000    Deferred        libnsl.so.1
ELF    7efba000-7efc2000    Deferred        libnss_compat.so.2
ELF    7efc2000-7efe8000    Deferred        libm.so.6
ELF    f7415000-f7419000    Deferred        libdl.so.2
ELF    f7419000-f7573000    Export          libc.so.6
ELF    f7574000-f758d000    Deferred        libpthread.so.0
ELF    f75a5000-f76e5000    Export          libwine.so.1
ELF    f76e7000-f7705000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000017    0
    00000016    0
    00000013    0
    00000012    0
0000001a explorer.exe
    0000001b    0
00000036 Steam.exe
    0000004a    0
    00000049    1
    00000048    1
    0000002a    1
    00000040    1
    00000032    0
    00000026   15
    0000002b   15
    0000002e    0
    00000028    0
    00000027    0
    00000024    0
    00000025    0
    00000022    0
    00000023    1
    00000020    1
    0000001f    0
    0000001e    0
    0000001d    0
    00000009    0
    0000000c    0
    0000000b    0
    00000046   15
    00000044    0
    00000043    0
    00000041    0
    0000003e    0
    0000003d    0
    0000003c    0
    0000003b    0
    0000003a    0
    00000039    0
    00000038    0
    00000037    0
0000004b winemenubuilder.exe
    0000004c    0
0000004d winemenubuilder.exe
    0000004e    0
00000062 (D) C:\Program Files\KeyChamp 2.0\keychamp.exe
    00000063    0 <==
Backtrace:
=>0 0xf752ccca in libc.so.6 (+0x113cca) (0x0032f178)
  1 0x004236e9 in keychamp (+0x236e8) (0x0032f288)
  2 0x00424473 in keychamp (+0x24472) (0x0032f540)
  3 0x00422d14 in keychamp (+0x22d13) (0x0032f570)
  4 0x0042312e in keychamp (+0x2312d) (0x0032f618)
  5 0x00423353 in keychamp (+0x23352) (0x0032f638)
  6 0x004233b6 in keychamp (+0x233b5) (0x0032f65c)
  7 0x00424839 in keychamp (+0x24838) (0x0032f6b8)
  8 0x7ebbbc8a WINPROC_wrapper+0x19() in user32 (0x0032f6e8)
  9 0x7ebbd79c in user32 (+0x9d79b) (0x0032f738)
  10 0x7ebbeaef in user32 (+0x9eaee) (0x0032f788)
  11 0x7eb80fc1 in user32 (+0x60fc0) (0x0032f7f8)
  12 0x7eb856b6 in user32 (+0x656b5) (0x0032f878)
  13 0x7eb85b03 SendMessageA+0x52() in user32 (0x0032f8c8)
  14 0x7ebb3ebd in user32 (+0x93ebc) (0x0032fab8)
  15 0x7ebad3da CreateWindowExA+0x89() in user32 (0x0032fd28)
  16 0x004234d9 in keychamp (+0x234d8) (0x0032fd90)
  17 0x0042366b in keychamp (+0x2366a) (0x0032fd9c)
  18 0x00448b8b in keychamp (+0x48b8a) (0x0032fde8)
  19 0x0046902e in keychamp (+0x6902d) (0x0032fe90)
  20 0x7b85430c call_process_entry+0xb() in kernel32 (0x0032fea8)
  21 0x7b85653b in kernel32 (+0x4653a) (0x0032fee8)
  22 0x7bc6f950 call_thread_func+0xb() in ntdll (0x0032fef8)
  23 0x7bc6fb20 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  24 0x7bc4aa8a in ntdll (+0x3aa89) (0x0032ffe8)

```

My Wine config is stock except for I set the Windows version to Windows 7. It also did the same thing with the Windows XP setting.

Any help would be greatly appreciated.

---

