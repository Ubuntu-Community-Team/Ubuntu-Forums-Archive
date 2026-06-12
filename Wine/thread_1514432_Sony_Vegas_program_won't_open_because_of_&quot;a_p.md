---
title: "Sony Vegas program won't open because of &quot;a problem or a deficency in WINE&quot;, HELP?"
date: 2010-06-21
forum: Wine
---

### Post by geeee on 2010-06-21
Hello! I just installed my Sony Vegas 8.0, with the help of "WINE" and a number of codes. Now, when I try to activate my Sony Vegas, an error occurs. It says it's caused by the program or something went wrong with the "WINE". I have a file below. Is there any way I can use my Sony Vegas? I don't understand. Give me your wisdom, please and thank you.

---

### Post by jchase45 on 2010-06-21
You need to run the program from a terminal using the wine command followed by the path and program name of the .exe file , then what ever error or problem will show in the terminal , copy that and paste it here

---

### Post by geeee on 2010-06-21
> **jchase45 said:**
> You need to run the program from a terminal using the wine command followed by the path and program name of the .exe file , then what ever error or problem will show in the terminal , copy that and paste it here

I am very sorry, but I don't quite understand. You're telling me to run the SonyVegas file from a terminal using a wine command? Which wine command do I use? (I am very new, forgive me if I didn't state that earlier.) What do you mean a path and program name? May I please see an example. I am sorry if I am asking for too much. Please, I hope you can still help me.

---

### Post by jchase45 on 2010-06-21
Go to applications / accessories / terminal 

then you need to find the exe file you want to execute, right click it , select properties , you can see the path and the file name , add em to the terminal 

[PHP]

jared@jared-desktop:~/.wine/drive_c/Program Files/Electronic Arts/Battlefield Bad Company 2$ wine BFBC2Game.exe 

[/PHP]

everything before the $ sign is the path ( I changed to that folder using the cd ( change directory ) command )

---

### Post by geeee on 2010-06-21
I don't know if I am doing this right so I did it two ways. When I pressed properties, nothing said, 
“Path” , there was “Command” and “Location”. When I put the location onto the terminal, it said there was no such file. Then I tried “Command”. In the first way, I copied all of it, in the second, I copied a small section. Is this what you meant? 
 

 WAY 1 :
 

[PHP]gizelle@ZELL:~$ env WINEPREFIX="/home/gizelle/.wine" wine C:\\Program\ Files\\Sony\\Vegas\ Pro\ 8.0\\vegas80.exe  
 fixme:heap:HeapSetInformation 0x110000 0 0x32fdcc 4
 fixme:heap:HeapSetInformation 0x15a1000 0 0x32fdcc 4
 fixme:msvideo:DrawDibBegin wFlags == 0x00001000 not handled
 libpng warning: Ignoring incorrect gAMA value when sRGB is also present
 igamma = 45455
 fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1b5ce8,0x197d88): stub
 fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1981f0,0x198108): stub
 fixme:dmusic:IDirectMusic8Impl_SetDirectSound (0x1b3f80, (nil), (nil)): stub
 fixme:advapi:RegisterTraceGuidsW (0x68ce90, 0xadd3c8, {70a1a1b1-28e0-4cae-b659-48ef64164c5c}, 1, 0xaa0da4, (null), (null), 0xadd3d8,)
 fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
 fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
 fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
 fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
 wine: Unhandled page fault on read access to 0x045ec2b3 at address 0x115b320 (thread 0009), starting debugger...
 fixme:event:wait_for_withdrawn_state window 0x2007e/4600001 wait timed out
 Unhandled exception: page fault on read access to 0x045ec2b3 in 32-bit code (0x0115b320).
 Register dump:
  CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
  EIP:0115b320 ESP:0032eb60 EBP:014434e8 EFLAGS:00010206(  R- --  I   - -P- )
  EAX:0032ebbc EBX:00000000 ECX:045ec2b3 EDX:0032ebbc
  ESI:00000010 EDI:028e60c0
 Stack dump:
 0x0032eb60:  028e60c0 045ec2a3 011ec84e 045ec2b3
 0x0032eb70:  0032ebbc 0016a6dc 0016a6dc 028e60c0
 0x0032eb80:  0032eee0 028e76d8 028e7350 0016a6dc
 0x0032eb90:  028e6174 00000006 00000001 0032eee0
 0x0032eba0:  00000000 00000000 028e60c0 00000000
 0x0032ebb0:  00000004 00000000 00200003 00000000
 Backtrace:
 =>0 0x0115b320 in vegas80k (+0xb320) (0x014434e8)
 0x0115b320: movl    0x0(%ecx),%edx
 Modules:
 Module    Address            Debug info    Name (156 modules)
 PE      340000-  398000    Deferred        sfwbdmux
 PE      400000- 1145000    Deferred        vegas80
 PE     1150000- 15a1000    Export          vegas80k
 PE     1ad0000- 1af6000    Deferred        pluginwrapper
 PE     1de0000- 1fb8000    Deferred        vfplugs
 PE     20d0000- 23ad000    Deferred        vidpcore
 PE    10000000-100a1000    Deferred        sonymvd2pro_xp
 ELF    20000000-20026000    Deferred        msacm32<elf>
   \-PE    20010000-20026000    \               msacm32
 ELF    20026000-20064000    Deferred        avifil32<elf>
   \-PE    20030000-20064000    \               avifil32
 ELF    20064000-20119000    Deferred        comdlg32<elf>
   \-PE    20070000-20119000    \               comdlg32
 ELF    20119000-20150000    Deferred        winealsa<elf>
   \-PE    20120000-20150000    \               winealsa
 ELF    20150000-20192000    Deferred        libpulse.so.0
 ELF    20192000-20198000    Deferred        libxtst.so.6
 ELF    20198000-20294000    Deferred        libvorbisenc.so.2
 ELF    20294000-2029b000    Deferred        libogg.so.0
 ELF    2029b000-202b0000    Deferred        avicap32<elf>
   \-PE    202a0000-202b0000    \               avicap32
 ELF    213c4000-213ec000    Deferred        dmusic<elf>
   \-PE    213d0000-213ec000    \               dmusic
 ELF    22155000-22163000    Deferred        libxi.so.6
 ELF    28559000-28562000    Deferred        libwrap.so.0
 ELF    2914e000-2919b000    Deferred        libflac.so.8
 PE    31f90000-321bb000    Deferred        aviplug
 PE    32420000-3262a000    Deferred        colorcorrector
 PE    35260000-352d7000    Deferred        sfasio
 PE    35e70000-35eda000    Deferred        sfdsound
 PE    36340000-364e6000    Deferred        sfmarket2
 PE    36b50000-36d90000    Deferred        sfpagepeel
 PE    37510000-37641000    Deferred        sfs4rw
 PE    379f0000-37d79000    Deferred        sftrans1
 PE    39bc0000-39e62000    Deferred        vfx1
 ELF    3b6e8000-3b742000    Deferred        riched20<elf>
   \-PE    3b6f0000-3b742000    \               riched20
 ELF    42bd1000-42bf3000    Deferred        devenum<elf>
   \-PE    42be0000-42bf3000    \               devenum
 ELF    4504f000-4509a000    Deferred        libpulsecommon-0.9.21.so
 ELF    4ac00000-4ac26000    Deferred        msvfw32<elf>
   \-PE    4ac10000-4ac26000    \               msvfw32
 ELF    4e3d3000-4e49b000    Deferred        libasound.so.2
 ELF    52cf5000-52cfc000    Deferred        libasound_module_pcm_pulse.so
 ELF    56f8a000-56fb3000    Deferred        libvorbis.so.0
 ELF    591b6000-59269000    Deferred        quartz<elf>
   \-PE    591d0000-59269000    \               quartz
 ELF    67dec000-67e54000    Deferred        libsndfile.so.1
 ELF    68000000-6801d000    Deferred        ld-linux.so.2
 ELF    6801d000-6815d000    Deferred        libwine.so.1
 ELF    6815d000-68176000    Deferred        libpthread.so.0
 ELF    68176000-682d0000    Deferred        libc.so.6
 ELF    682d0000-682f6000    Deferred        libm.so.6
 ELF    682f6000-682fe000    Deferred        libnss_compat.so.2
 ELF    682fe000-68315000    Deferred        libnsl.so.1
 ELF    68315000-6831f000    Deferred        libnss_nis.so.2
 ELF    6831f000-6832b000    Deferred        libnss_files.so.2
 ELF    6832b000-6838d000    Deferred        shlwapi<elf>
   \-PE    68340000-6838d000    \               shlwapi
 ELF    6838d000-684bd000    Deferred        user32<elf>
   \-PE    683a0000-684bd000    \               user32
 ELF    684bd000-68548000    Deferred        gdi32<elf>
   \-PE    684d0000-68548000    \               gdi32
 ELF    68548000-685a2000    Deferred        advapi32<elf>
   \-PE    68550000-685a2000    \               advapi32
 ELF    685a2000-68617000    Deferred        rpcrt4<elf>
   \-PE    685b0000-68617000    \               rpcrt4
 ELF    68617000-68699000    Deferred        msvcrt<elf>
   \-PE    68630000-68699000    \               msvcrt
 ELF    68699000-68782000    Deferred        oleaut32<elf>
   \-PE    686b0000-68782000    \               oleaut32
 ELF    68782000-687ac000    Deferred        netapi32<elf>
   \-PE    68790000-687ac000    \               netapi32
 ELF    687ac000-687c0000    Deferred        libresolv.so.2
 ELF    687c0000-687ed000    Deferred        ws2_32<elf>
   \-PE    687d0000-687ed000    \               ws2_32
 ELF    687ed000-689c0000    Deferred        shell32<elf>
   \-PE    68800000-689c0000    \               shell32
 ELF    689c0000-68aab000    Deferred        comctl32<elf>
   \-PE    689d0000-68aab000    \               comctl32
 ELF    68aab000-68b06000    Deferred        wininet<elf>
   \-PE    68ab0000-68b06000    \               wininet
 ELF    68b06000-68b1b000    Deferred        libz.so.1
 ELF    68b1b000-68b3f000    Deferred        mpr<elf>
   \-PE    68b20000-68b3f000    \               mpr
 ELF    68b3f000-68b9c000    Deferred        setupapi<elf>
   \-PE    68b50000-68b9c000    \               setupapi
 ELF    68b9c000-68bd3000    Deferred        winspool<elf>
   \-PE    68ba0000-68bd3000    \               winspool
 ELF    68bd3000-68bec000    Deferred        version<elf>
   \-PE    68be0000-68bec000    \               version
 ELF    68bec000-68c00000    Deferred        lz32<elf>
   \-PE    68bf0000-68c00000    \               lz32
 ELF    68c00000-68c88000    Deferred        winmm<elf>
   \-PE    68c10000-68c88000    \               winmm
 ELF    68c88000-68cfe000    Deferred        libfreetype.so.6
 ELF    68cfe000-68d07000    Deferred        libsm.so.6
 ELF    68d07000-68d20000    Deferred        libice.so.6
 ELF    68d20000-68d30000    Deferred        libxext.so.6
 ELF    68d30000-68e4d000    Deferred        libx11.so.6
 ELF    68e4d000-68e52000    Deferred        libuuid.so.1
 ELF    68e52000-68e6c000    Deferred        libxcb.so.1
 ELF    68e6c000-68e70000    Deferred        libxau.so.6
 ELF    68e70000-68e76000    Deferred        libxdmcp.so.6
 ELF    68e76000-68e98000    Deferred        imm32<elf>
   \-PE    68e80000-68e98000    \               imm32
 ELF    68e98000-68e9c000    Deferred        libxinerama.so.1
 ELF    68e9c000-68ea2000    Deferred        libxxf86vm.so.1
 ELF    68ea2000-68eac000    Deferred        libxrender.so.1
 ELF    68eac000-68eb0000    Deferred        libxcomposite.so.1
 ELF    68eb0000-68eb6000    Deferred        libxfixes.so.3
 ELF    68eb6000-68eea000    Deferred        uxtheme<elf>
   \-PE    68ec0000-68eea000    \               uxtheme
 ELF    68eea000-68f19000    Deferred        libgssapi_krb5.so.2
 ELF    68f19000-68fb4000    Deferred        libgnutls.so.26
 ELF    68fb4000-68fc0000    Deferred        libavahi-common.so.3
 ELF    68fc0000-69071000    Deferred        libkrb5.so.3
 ELF    69071000-69075000    Deferred        libcom_err.so.2
 ELF    69075000-6907d000    Deferred        libkrb5support.so.0
 ELF    6907d000-6908e000    Deferred        libtasn1.so.3
 ELF    6908e000-690c7000    Deferred        libdbus-1.so.3
 ELF    690c7000-690d0000    Deferred        librt.so.1
 ELF    690d0000-690d5000    Deferred        libgpg-error.so.0
 ELF    6b40c000-6b452000    Deferred        libcups.so.2
 ELF    6b59e000-6b5ce000    Deferred        libfontconfig.so.1
 ELF    6b8e8000-6b930000    Deferred        dsound<elf>
   \-PE    6b8f0000-6b930000    \               dsound
 ELF    6bd33000-6bda6000    Deferred        libgcrypt.so.11
 ELF    6c034000-6c05b000    Deferred        libexpat.so.1
 ELF    6cf79000-6cf8a000    Deferred        libavahi-client.so.3
 ELF    6dd7c000-6de1e000    Deferred        winex11<elf>
   \-PE    6dd90000-6de1e000    \               winex11
 ELF    6e425000-6e42f000    Deferred        libxcursor.so.1
 ELF    6f11b000-6f134000    Deferred        msacm32<elf>
   \-PE    6f120000-6f134000    \               msacm32
 ELF    71d1a000-71d2e000    Deferred        msimg32<elf>
   \-PE    71d20000-71d2e000    \               msimg32
 ELF    72070000-72086000    Deferred        midimap<elf>
   \-PE    72080000-72086000    \               midimap
 PE    72880000-72890000    Deferred        vcomp
 ELF    72e6a000-72e6e000    Deferred        libdl.so.2
 ELF    749d1000-749f2000    Deferred        iphlpapi<elf>
   \-PE    749e0000-749f2000    \               iphlpapi
 ELF    76576000-7657a000    Deferred        libkeyutils.so.1
 ELF    77689000-77789000    Deferred        ole32<elf>
   \-PE    776a0000-77789000    \               ole32
 PE    78130000-781cb000    Deferred        msvcr80
 ELF    78bc7000-78beb000    Deferred        libk5crypto.so.3
 ELF    7a2c7000-7a2e6000    Deferred        libgcc_s.so.1
 ELF    7b800000-7b946000    Deferred        kernel32<elf>
   \-PE    7b810000-7b946000    \               kernel32
 ELF    7bc00000-7bcb8000    Deferred        ntdll<elf>
   \-PE    7bc10000-7bcb8000    \               ntdll
 ELF    7bf00000-7bf04000    Deferred        <wine-loader>
 ELF    7bf69000-7bf71000    Deferred        libxrandr.so.2
 PE    7c340000-7c396000    Deferred        msvcr71
 Threads:
 process  tid      prio (all id:s are in hex)
 00000008 (D) C:\Program Files\Sony\Vegas Pro 8.0\vegas80.exe
     00000031    0
     00000030    0
     0000002f    0
     0000002e    1
     0000002d    0
     0000002c    0
     0000002b    0
     0000002a    0
     00000029    0
     00000028    0
     0000001d    0
     0000001c    0
     0000001b    0
     00000009    0 <==
 0000000e services.exe
     00000016    0
     00000015    0
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
 =>0 0x0115b320 in vegas80k (+0xb320) (0x014434e8)
 [/PHP]
 

 WAY 2 :
 

[PHP]gizelle@ZELL:~$ wine C:\\Program\ Files\\Sony\\Vegas\ Pro\ 8.0\\vegas80.exe  
 fixme:heap:HeapSetInformation 0x110000 0 0x32fdcc 4
 fixme:heap:HeapSetInformation 0x15a1000 0 0x32fdcc 4
 fixme:msvideo:DrawDibBegin wFlags == 0x00001000 not handled
 libpng warning: Ignoring incorrect gAMA value when sRGB is also present
 igamma = 45455
 fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1b5be8,0x1b6c20): stub
 fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1a99b8,0x197d38): stub
 fixme:dmusic:IDirectMusic8Impl_SetDirectSound (0x1b3ea0, (nil), (nil)): stub
 fixme:advapi:RegisterTraceGuidsW (0x68ce90, 0xadd3c8, {70a1a1b1-28e0-4cae-b659-48ef64164c5c}, 1, 0xaa0da4, (null), (null), 0xadd3d8,)
 fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
 fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
 fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
 fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
 wine: Unhandled page fault on read access to 0x045ec2b3 at address 0x115b320 (thread 0009), starting debugger...
 fixme:event:wait_for_withdrawn_state window 0x2007e/4200001 wait timed out
 Unhandled exception: page fault on read access to 0x045ec2b3 in 32-bit code (0x0115b320).
 Register dump:
  CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
  EIP:0115b320 ESP:0032eb60 EBP:014434e8 EFLAGS:00210206(  R- --  I   - -P- )
  EAX:0032ebbc EBX:00000000 ECX:045ec2b3 EDX:0032ebbc
  ESI:00000010 EDI:028e6078
 Stack dump:
 0x0032eb60:  028e6078 045ec2a3 011ec84e 045ec2b3
 0x0032eb70:  0032ebbc 0016a68c 0016a68c 028e6078
 0x0032eb80:  0032eee0 028e7690 028e7308 0016a68c
 0x0032eb90:  028e612c 00000006 00000001 0032eee0
 0x0032eba0:  00000000 00000000 028e6078 00000000
 0x0032ebb0:  00000004 00000000 00200003 00000000
 Backtrace:
 =>0 0x0115b320 in vegas80k (+0xb320) (0x014434e8)
 0x0115b320: movl    0x0(%ecx),%edx
 Modules:
 Module    Address            Debug info    Name (156 modules)
 PE      340000-  398000    Deferred        sfwbdmux
 PE      400000- 1145000    Deferred        vegas80
 PE     1150000- 15a1000    Export          vegas80k
 PE     1ad0000- 1af6000    Deferred        pluginwrapper
 PE     1de0000- 1fb8000    Deferred        vfplugs
 PE     20d0000- 23ad000    Deferred        vidpcore
 PE    10000000-100a1000    Deferred        sonymvd2pro_xp
 ELF    20000000-20026000    Deferred        msvfw32<elf>
   \-PE    20010000-20026000    \               msvfw32
 ELF    20026000-200db000    Deferred        comdlg32<elf>
   \-PE    20030000-200db000    \               comdlg32
 ELF    200db000-201a3000    Deferred        libasound.so.2
 ELF    201a6000-201f1000    Deferred        libpulsecommon-0.9.21.so
 ELF    201f1000-2023e000    Deferred        libflac.so.8
 ELF    2023e000-20266000    Deferred        dmusic<elf>
   \-PE    20240000-20266000    \               dmusic
 ELF    20266000-20319000    Deferred        quartz<elf>
   \-PE    20280000-20319000    \               quartz
 ELF    24c92000-24cb1000    Deferred        libgcc_s.so.1
 ELF    2d205000-2d20e000    Deferred        libwrap.so.0
 PE    31f90000-321bb000    Deferred        aviplug
 PE    32420000-3262a000    Deferred        colorcorrector
 PE    35260000-352d7000    Deferred        sfasio
 PE    35e70000-35eda000    Deferred        sfdsound
 PE    36340000-364e6000    Deferred        sfmarket2
 PE    36b50000-36d90000    Deferred        sfpagepeel
 PE    37510000-37641000    Deferred        sfs4rw
 PE    379f0000-37d79000    Deferred        sftrans1
 PE    39bc0000-39e62000    Deferred        vfx1
 ELF    40afd000-40b16000    Deferred        msacm32<elf>
   \-PE    40b00000-40b16000    \               msacm32
 ELF    41e1b000-41e29000    Deferred        libxi.so.6
 ELF    47ff7000-480f3000    Deferred        libvorbisenc.so.2
 ELF    50733000-50755000    Deferred        devenum<elf>
   \-PE    50740000-50755000    \               devenum
 ELF    55b76000-55bde000    Deferred        libsndfile.so.1
 ELF    55ff8000-56036000    Deferred        avifil32<elf>
   \-PE    56000000-56036000    \               avifil32
 ELF    57dd0000-57dd7000    Deferred        libasound_module_pcm_pulse.so
 ELF    5c223000-5c26b000    Deferred        dsound<elf>
   \-PE    5c230000-5c26b000    \               dsound
 ELF    5e657000-5e65d000    Deferred        libxtst.so.6
 ELF    61d86000-61d9c000    Deferred        midimap<elf>
   \-PE    61d90000-61d9c000    \               midimap
 ELF    68000000-6801d000    Deferred        ld-linux.so.2
 ELF    6801d000-6815d000    Deferred        libwine.so.1
 ELF    6815d000-68176000    Deferred        libpthread.so.0
 ELF    68176000-6817a000    Deferred        libdl.so.2
 ELF    6817a000-681a0000    Deferred        libm.so.6
 ELF    681a0000-681a8000    Deferred        libnss_compat.so.2
 ELF    681a8000-681bf000    Deferred        libnsl.so.1
 ELF    681bf000-681c9000    Deferred        libnss_nis.so.2
 ELF    681c9000-681d5000    Deferred        libnss_files.so.2
 ELF    681d5000-68237000    Deferred        shlwapi<elf>
   \-PE    681e0000-68237000    \               shlwapi
 ELF    68237000-68367000    Deferred        user32<elf>
   \-PE    68250000-68367000    \               user32
 ELF    68367000-683f2000    Deferred        gdi32<elf>
   \-PE    68370000-683f2000    \               gdi32
 ELF    683f2000-6844c000    Deferred        advapi32<elf>
   \-PE    68400000-6844c000    \               advapi32
 ELF    6844c000-684c1000    Deferred        rpcrt4<elf>
   \-PE    68460000-684c1000    \               rpcrt4
 ELF    684c1000-684d5000    Deferred        msimg32<elf>
   \-PE    684d0000-684d5000    \               msimg32
 ELF    684d5000-685d5000    Deferred        ole32<elf>
   \-PE    684f0000-685d5000    \               ole32
 ELF    685d5000-685ff000    Deferred        netapi32<elf>
   \-PE    685e0000-685ff000    \               netapi32
 ELF    685ff000-68620000    Deferred        iphlpapi<elf>
   \-PE    68610000-68620000    \               iphlpapi
 ELF    68620000-68634000    Deferred        libresolv.so.2
 ELF    68634000-68661000    Deferred        ws2_32<elf>
   \-PE    68640000-68661000    \               ws2_32
 ELF    68661000-68834000    Deferred        shell32<elf>
   \-PE    68670000-68834000    \               shell32
 ELF    68834000-6891f000    Deferred        comctl32<elf>
   \-PE    68840000-6891f000    \               comctl32
 ELF    6891f000-6897a000    Deferred        wininet<elf>
   \-PE    68930000-6897a000    \               wininet
 ELF    6897a000-6898f000    Deferred        libz.so.1
 ELF    6898f000-689b3000    Deferred        mpr<elf>
   \-PE    689a0000-689b3000    \               mpr
 ELF    689b3000-68a10000    Deferred        setupapi<elf>
   \-PE    689c0000-68a10000    \               setupapi
 ELF    68a10000-68a47000    Deferred        winspool<elf>
   \-PE    68a20000-68a47000    \               winspool
 ELF    68a47000-68a60000    Deferred        version<elf>
   \-PE    68a50000-68a60000    \               version
 ELF    68a60000-68a74000    Deferred        lz32<elf>
   \-PE    68a70000-68a74000    \               lz32
 ELF    68a74000-68aea000    Deferred        libfreetype.so.6
 ELF    68aea000-68b1a000    Deferred        libfontconfig.so.1
 ELF    68b1a000-68bbc000    Deferred        winex11<elf>
   \-PE    68b30000-68bbc000    \               winex11
 ELF    68bbc000-68bc5000    Deferred        libsm.so.6
 ELF    68bc5000-68bde000    Deferred        libice.so.6
 ELF    68bde000-68bee000    Deferred        libxext.so.6
 ELF    68bee000-68d0b000    Deferred        libx11.so.6
 ELF    68d0b000-68d10000    Deferred        libuuid.so.1
 ELF    68d10000-68d2a000    Deferred        libxcb.so.1
 ELF    68d2a000-68d2e000    Deferred        libxau.so.6
 ELF    68d2e000-68d34000    Deferred        libxdmcp.so.6
 ELF    68d34000-68d38000    Deferred        libxinerama.so.1
 ELF    68d38000-68d3e000    Deferred        libxxf86vm.so.1
 ELF    68d3e000-68d48000    Deferred        libxrender.so.1
 ELF    68d48000-68d4c000    Deferred        libxcomposite.so.1
 ELF    68d4c000-68d52000    Deferred        libxfixes.so.3
 ELF    68d52000-68d86000    Deferred        uxtheme<elf>
   \-PE    68d60000-68d86000    \               uxtheme
 ELF    68d86000-68dcc000    Deferred        libcups.so.2
 ELF    68dcc000-68dfb000    Deferred        libgssapi_krb5.so.2
 ELF    68dfb000-68e96000    Deferred        libgnutls.so.26
 ELF    68e96000-68ea2000    Deferred        libavahi-common.so.3
 ELF    68ea2000-68eb3000    Deferred        libavahi-client.so.3
 ELF    68eb3000-68f64000    Deferred        libkrb5.so.3
 ELF    68f64000-68f68000    Deferred        libcom_err.so.2
 ELF    68f68000-68f70000    Deferred        libkrb5support.so.0
 ELF    68f70000-68f74000    Deferred        libkeyutils.so.1
 ELF    68f74000-68f85000    Deferred        libtasn1.so.3
 ELF    68f85000-68ff8000    Deferred        libgcrypt.so.11
 ELF    68ff8000-69031000    Deferred        libdbus-1.so.3
 ELF    69031000-6903a000    Deferred        librt.so.1
 ELF    6903a000-6903f000    Deferred        libgpg-error.so.0
 ELF    6989d000-699f7000    Deferred        libc.so.6
 ELF    6a63f000-6a663000    Deferred        libk5crypto.so.3
 ELF    6afba000-6b014000    Deferred        riched20<elf>
   \-PE    6afd0000-6b014000    \               riched20
 ELF    6e8fe000-6e935000    Deferred        winealsa<elf>
   \-PE    6e910000-6e935000    \               winealsa
 ELF    6fa04000-6fa26000    Deferred        imm32<elf>
   \-PE    6fa10000-6fa26000    \               imm32
 ELF    71145000-7114f000    Deferred        libxcursor.so.1
 PE    72880000-72890000    Deferred        vcomp
 ELF    74771000-7485a000    Deferred        oleaut32<elf>
   \-PE    74790000-7485a000    \               oleaut32
 ELF    75dd2000-75dda000    Deferred        libxrandr.so.2
 ELF    76a6f000-76a98000    Deferred        libvorbis.so.0
 ELF    76f78000-76fba000    Deferred        libpulse.so.0
 ELF    77eae000-77ed4000    Deferred        msacm32<elf>
   \-PE    77eb0000-77ed4000    \               msacm32
 PE    78130000-781cb000    Deferred        msvcr80
 ELF    791ee000-79276000    Deferred        winmm<elf>
   \-PE    79200000-79276000    \               winmm
 ELF    7a352000-7a379000    Deferred        libexpat.so.1
 ELF    7aee7000-7aeee000    Deferred        libogg.so.0
 ELF    7b678000-7b6fa000    Deferred        msvcrt<elf>
   \-PE    7b690000-7b6fa000    \               msvcrt
 ELF    7b800000-7b946000    Deferred        kernel32<elf>
   \-PE    7b810000-7b946000    \               kernel32
 ELF    7bb07000-7bb1c000    Deferred        avicap32<elf>
   \-PE    7bb10000-7bb1c000    \               avicap32
 ELF    7bc00000-7bcb8000    Deferred        ntdll<elf>
   \-PE    7bc10000-7bcb8000    \               ntdll
 ELF    7bf00000-7bf04000    Deferred        <wine-loader>
 PE    7c340000-7c396000    Deferred        msvcr71
 Threads:
 process  tid      prio (all id:s are in hex)
 00000008 (D) C:\Program Files\Sony\Vegas Pro 8.0\vegas80.exe
     00000031    0
     00000030    0
     0000002f    0
     0000002e    1
     0000002d    0
     0000002c    0
     0000002b    0
     0000002a    0
     00000029    0
     00000028    0
     0000001d    0
     0000001c    0
     0000001b    0
     00000009    0 <==
 0000000e services.exe
     00000016    0
     00000015    0
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
 =>0 0x0115b320 in vegas80k (+0xb320) (0x014434e8)
 [/PHP]

---

### Post by asdfoo on 2010-06-21
Update to wine-1.2-rc4 and try again.

The Wine FAQ explains how to run programs if you are not sure.

If it still doesn't work then you may have to look at alternatives.

---

