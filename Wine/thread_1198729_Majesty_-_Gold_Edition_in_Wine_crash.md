---
title: "Majesty - Gold Edition in Wine crash"
date: 2009-06-27
forum: Wine
---

### Post by Zorgoth on 2009-06-27
Running Majesty - Gold Edition in the Wine from the ubuntu repository, whichever that is, Windows 98, I get the sound from the intro movies, with no picture, and then it crashes on the loading screen.

Note that I am a complete Wine noob and no nothing.

Here is the console output:

```

fixme:win:EnumDisplayDevicesW ((null),0,0x32f6ac,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:amstream:IAMMultiMediaStreamImpl_QueryInterface (0x15b378/0x15b378)->({bebe595c-9a6f-11d0-8fde-00c04fd9189d},0x15719e8)
fixme:amstream:IAMMultiMediaStreamImpl_Initialize (0x15b378/0x15b378)->(0,1,(nil)) partial stub!
fixme:amstream:IAMMultiMediaStreamImpl_AddMediaStream (0x15b378/0x15b378)->((nil),0x658ce0,0,(nil)) partial stub!
fixme:amstream:IAMMultiMediaStreamImpl_QueryInterface (0x15b378/0x15b378)->({bebe595c-9a6f-11d0-8fde-00c04fd9189d},0x15719e8)
fixme:amstream:IAMMultiMediaStreamImpl_Initialize (0x15b378/0x15b378)->(0,1,(nil)) partial stub!
fixme:amstream:IAMMultiMediaStreamImpl_AddMediaStream (0x15b378/0x15b378)->((nil),0x658ce0,0,(nil)) partial stub!
err:amstream:IMediaStreamImpl_QueryInterface (0x15bfb8)->({f7537560-a3be-11d0-8212-00c04fc32c45},0x15719ec),not found
wine: Unhandled page fault on read access to 0x00000000 at address 0x628e2c (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00628e2c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00628e2c ESP:0032f584 EBP:01571a00 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:000001cc
 ESI:01571010 EDI:01571960
Stack dump:
0x0032f584:  00000000 00000000 00000000 01571960
0x0032f594:  00629272 00a2aa2c 00a29060 00000000
0x0032f5a4:  00000002 01571960 0032f5c8 0064b923
0x0032f5b4:  00000000 00629410 01571010 00000000
0x0032f5c4:  01571960 0032fbd8 0064b95b 00000000
0x0032f5d4:  00575d57 0032f5ec 0032f7cf 015708e0
Backtrace:
=>1 0x00628e2c in majx (+0x228e2c) (0x01571a00)
0x00628e2c: movl	0x0(%eax),%ecx
Modules:
Module	Address			Debug info	Name (102 modules)
PE	  390000-  3d1000	Deferred        binkw32
PE	  400000-  6ea000	Export          majx
PE	10000000-1007d000	Deferred        tls7012d
PE	780c0000-78121000	Deferred        msvcp60
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d5fd000-7d69f000	Deferred        oleaut32<elf>
  \-PE	7d610000-7d69f000	\               oleaut32
ELF	7dacf000-7dae6000	Deferred        mcicda<elf>
  \-PE	7dad0000-7dae6000	\               mcicda
ELF	7dae6000-7db30000	Deferred        dsound<elf>
  \-PE	7daf0000-7db30000	\               dsound
ELF	7de2c000-7de54000	Deferred        msvfw32<elf>
  \-PE	7de30000-7de54000	\               msvfw32
ELF	7de54000-7dec0000	Deferred        quartz<elf>
  \-PE	7de60000-7dec0000	\               quartz
ELF	7dec0000-7deda000	Deferred        amstream<elf>
  \-PE	7ded0000-7deda000	\               amstream
ELF	7e0af000-7e0b9000	Deferred        libdrm.so.2
ELF	7e0b9000-7e11b000	Deferred        libgl.so.1
ELF	7e128000-7e133000	Deferred        libgcc_s.so.1
ELF	7e133000-7e236000	Deferred        wined3d<elf>
  \-PE	7e150000-7e236000	\               wined3d
ELF	7e264000-7e267000	Deferred        libxdamage.so.1
ELF	7e28f000-7e2c2000	Deferred        uxtheme<elf>
  \-PE	7e2a0000-7e2c2000	\               uxtheme
ELF	7e2c2000-7e2e8000	Deferred        msacm32<elf>
  \-PE	7e2d0000-7e2e8000	\               msacm32
ELF	7e2e8000-7e3ab000	Deferred        libasound.so.2
ELF	7e3ac000-7e3c3000	Deferred        msacm32<elf>
  \-PE	7e3b0000-7e3c3000	\               msacm32
ELF	7e3c3000-7e3f9000	Deferred        winealsa<elf>
  \-PE	7e3d0000-7e3f9000	\               winealsa
ELF	7e3f9000-7e402000	Deferred        libxcursor.so.1
ELF	7e402000-7e407000	Deferred        libxfixes.so.3
ELF	7e407000-7e40a000	Deferred        libxcomposite.so.1
ELF	7e40a000-7e410000	Deferred        libxrandr.so.2
ELF	7e410000-7e418000	Deferred        libxrender.so.1
ELF	7e418000-7e41b000	Deferred        libxinerama.so.1
ELF	7e41b000-7e43b000	Deferred        imm32<elf>
  \-PE	7e420000-7e43b000	\               imm32
ELF	7e43b000-7e440000	Deferred        libxdmcp.so.6
ELF	7e440000-7e458000	Deferred        libxcb.so.1
ELF	7e458000-7e45a000	Deferred        libxcb-xlib.so.0
ELF	7e45a000-7e45d000	Deferred        libxau.so.6
ELF	7e45d000-7e544000	Deferred        libx11.so.6
ELF	7e544000-7e552000	Deferred        libxext.so.6
ELF	7e552000-7e557000	Deferred        libxxf86vm.so.1
ELF	7e557000-7e56f000	Deferred        libice.so.6
ELF	7e56f000-7e577000	Deferred        libsm.so.6
ELF	7e579000-7e58d000	Deferred        midimap<elf>
  \-PE	7e580000-7e58d000	\               midimap
ELF	7e58f000-7e626000	Deferred        winex11<elf>
  \-PE	7e5a0000-7e626000	\               winex11
ELF	7e63f000-7e660000	Deferred        libexpat.so.1
ELF	7e660000-7e68a000	Deferred        libfontconfig.so.1
ELF	7e68a000-7e69f000	Deferred        libz.so.1
ELF	7e69f000-7e70c000	Deferred        libfreetype.so.6
ELF	7e70c000-7e763000	Deferred        ddraw<elf>
  \-PE	7e710000-7e763000	\               ddraw
ELF	7e763000-7e797000	Deferred        dplayx<elf>
  \-PE	7e770000-7e797000	\               dplayx
ELF	7e797000-7e7aa000	Deferred        libresolv.so.2
ELF	7e7c2000-7e7e0000	Deferred        iphlpapi<elf>
  \-PE	7e7d0000-7e7e0000	\               iphlpapi
ELF	7e7e0000-7e841000	Deferred        rpcrt4<elf>
  \-PE	7e7f0000-7e841000	\               rpcrt4
ELF	7e841000-7e8e5000	Deferred        ole32<elf>
  \-PE	7e850000-7e8e5000	\               ole32
ELF	7e8e5000-7e94f000	Deferred        msvcrt<elf>
  \-PE	7e900000-7e94f000	\               msvcrt
ELF	7e94f000-7e963000	Deferred        lz32<elf>
  \-PE	7e950000-7e963000	\               lz32
ELF	7e963000-7e97c000	Deferred        version<elf>
  \-PE	7e970000-7e97c000	\               version
ELF	7e97c000-7ea3b000	Deferred        comctl32<elf>
  \-PE	7e980000-7ea3b000	\               comctl32
ELF	7ea3b000-7ea94000	Deferred        shlwapi<elf>
  \-PE	7ea50000-7ea94000	\               shlwapi
ELF	7ea94000-7eba7000	Deferred        shell32<elf>
  \-PE	7eaa0000-7eba7000	\               shell32
ELF	7eba7000-7ebf9000	Deferred        advapi32<elf>
  \-PE	7ebb0000-7ebf9000	\               advapi32
ELF	7ebf9000-7ec94000	Deferred        gdi32<elf>
  \-PE	7ec10000-7ec94000	\               gdi32
ELF	7ec94000-7eddb000	Deferred        user32<elf>
  \-PE	7ecb0000-7eddb000	\               user32
ELF	7eddb000-7ee6d000	Deferred        winmm<elf>
  \-PE	7edf0000-7ee6d000	\               winmm
ELF	7ef8d000-7ef98000	Deferred        libnss_files.so.2
ELF	7ef98000-7efa2000	Deferred        libnss_nis.so.2
ELF	7efa2000-7efba000	Deferred        libnsl.so.1
ELF	7efba000-7efc3000	Deferred        libnss_compat.so.2
ELF	7efc3000-7efe8000	Deferred        libm.so.6
ELF	b7ce1000-b7ce5000	Deferred        libdl.so.2
ELF	b7ce5000-b7e34000	Deferred        libc.so.6
ELF	b7e35000-b7e4d000	Deferred        libpthread.so.0
ELF	b7e65000-b7f9b000	Deferred        libwine.so.1
ELF	b7f9d000-b7fb9000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Infogrames Interactive\Majesty - Gold Edition\MajX\MajX.exe
	0000001e    0
	00000019   15
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
Backtrace:
=>1 0x00628e2c in majx (+0x228e2c) (0x01571a00)

```

---

### Post by Zorgoth on 2009-06-27
I do actually know how to spell "know"  I just have a problem with homophones when typing.

---

### Post by Hamms on 2009-07-11
Hey, I know this thread is almost a year old, but I'm having an identical issue. I don't suppose anyone stumbled upon an answer in the last nine months?

---

### Post by Tyke91 on 2009-09-16
Also having this bug.

---

### Post by ghost779 on 2009-11-15
I don't have ubuntu. I have a completely updated Fedora Core 11 install
wine version wine-1.1.32
I too had the same problem, black intro video and crash at the loading screen
with the retail version of Majesty Gold Edition
I followed two remedies, the first which had no effect but possibly influenced
the second.

One site said to copy MajX into Majesty, that didn't help

Another site 
[http://forum.paradoxplaza.com/forum/showthread.php?t=400836](http://forum.paradoxplaza.com/forum/showthread.php?t=400836)

said to _remove/move(rename)_ the Music folder that is located in
the Majesty folder not MajX. This DID help. 
just renaming them anything other than Music helps. if you want
to listen to it, you can just load it on an mp3 player such as mpg123
or audacious or xmms. I can run the expansion MajX that includes all
the maps from the original, just scroll around the map, everything above the
snowy mountains is part of the expansion, yay!

---

