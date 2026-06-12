---
title: "Purble Place?? (the greatest game)"
date: 2009-02-08
forum: Wine
---

### Post by pbotros1234 on 2009-02-08
First off, let me just say that I have a bet with a friend that, if I can get Purble Place (the game that comes standard on Vista, and, yes, is for 6-year-olds) to work on linux, then I get to put linux on their computer.

Fun stuff lol.

This is apparently harder than it looks. Some people have made Purble Place work on Windows XP with a supplemental .DLL, so I figured I could download that, use the DLL and see if it works. Unfortunately, it doesn't.

This is what I've done:

1) Downloaded Purble Place and the Vista XP-ported DLL
   [Purble Place]("http://rapidshare.com/files/36887592/Vista_Games_XP_Part_3.zip")
   [Vista_Emulation.dll]("http://rapidshare.com/files/36774632/Vista_Games_XP_Part_1.zip") (this comes with other vista games, but includes the dll)

2) Extracted the zip files

3) Put the Vista_Emulation.dll in the .wine/drive_c/windows/system32/ folder

4) ran "wine Purble\ Place.exe" and got the following:
```
wine: Call from 0x1053e2b to unimplemented function KERNEL32.dll.WTSGetActiveConsoleSessionId, aborting
err:seh:cxx_frame_handler invalid frame magic 19930522
wine: Unimplemented function KERNEL32.dll.WTSGetActiveConsoleSessionId called at address 0x1053e2b (thread 001c), starting debugger...
Unhandled exception: unimplemented function KERNEL32.dll.WTSGetActiveConsoleSessionId called in 32-bit code (0x7bc46dcc).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc46dcc ESP:0033f990 EBP:0033f9f4 EFLAGS:00000202(   - 00      - - I1)
 EAX:0106e1d6 EBX:7bc914c4 ECX:00000004 EDX:00110058
 ESI:0033f99c EDI:00000000
Stack dump:
0x0033f990:  00000000 00000000 00000000 80000100
0x0033f9a0:  00000001 00000000 01053e2b 00000002
0x0033f9b0:  0106de8c 0106e1d6 00000000 00000000
0x0033f9c0:  00000000 00000000 00000000 00000000
0x0033f9d0:  00000000 00000000 00000000 00000000
0x0033f9e0:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x7bc46dcc in ntdll (+0x36dcc) (0x0033f9f4)
  1 0x0034004b (0x0033fe68)
  2 0x0103b45b in purbleplace (+0x3b45b) (0x0033fe7c)
  3 0x010491ca in purbleplace (+0x491ca) (0x0033ff08)
  4 0x7b877c47 in kernel32 (+0x57c47) (0x0033ffe8)
0x7bc46dcc: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (92 modules)
PE	 1000000- 10f2000	Export          purbleplace
PE	10000000-10011000	Deferred        vista.emulation
ELF	7b800000-7b93c000	Export          kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bcad000	Export          ntdll<elf>
  \-PE	7bc10000-7bcad000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7de76000-7de8a000	Deferred        midimap<elf>
  \-PE	7de80000-7de8a000	\               midimap
ELF	7de8a000-7deb1000	Deferred        msacm32<elf>
  \-PE	7de90000-7deb1000	\               msacm32
ELF	7deb1000-7dec8000	Deferred        msacm32<elf>
  \-PE	7dec0000-7dec8000	\               msacm32
ELF	7dec8000-7df8b000	Deferred        libasound.so.2
ELF	7df9d000-7dfd2000	Deferred        winealsa<elf>
  \-PE	7dfb0000-7dfd2000	\               winealsa
ELF	7e01e000-7e051000	Deferred        uxtheme<elf>
  \-PE	7e020000-7e051000	\               uxtheme
ELF	7e051000-7e05a000	Deferred        libxcursor.so.1
ELF	7e05a000-7e05f000	Deferred        libxfixes.so.3
ELF	7e05f000-7e062000	Deferred        libxcomposite.so.1
ELF	7e062000-7e068000	Deferred        libxrandr.so.2
ELF	7e068000-7e070000	Deferred        libxrender.so.1
ELF	7e070000-7e075000	Deferred        libxxf86vm.so.1
ELF	7e075000-7e078000	Deferred        libxinerama.so.1
ELF	7e078000-7e098000	Deferred        imm32<elf>
  \-PE	7e080000-7e098000	\               imm32
ELF	7e098000-7e09d000	Deferred        libxdmcp.so.6
ELF	7e09d000-7e0b5000	Deferred        libxcb.so.1
ELF	7e0b5000-7e0b8000	Deferred        libxau.so.6
ELF	7e0b8000-7e19f000	Deferred        libx11.so.6
ELF	7e19f000-7e1ad000	Deferred        libxext.so.6
ELF	7e1ad000-7e1c5000	Deferred        libice.so.6
ELF	7e1c5000-7e1cd000	Deferred        libsm.so.6
ELF	7e1df000-7e278000	Deferred        winex11<elf>
  \-PE	7e1f0000-7e278000	\               winex11
ELF	7e2b5000-7e2d6000	Deferred        libexpat.so.1
ELF	7e2d6000-7e300000	Deferred        libfontconfig.so.1
ELF	7e312000-7e327000	Deferred        libz.so.1
ELF	7e327000-7e394000	Deferred        libfreetype.so.6
ELF	7e394000-7e3a9000	Deferred        oleacc<elf>
  \-PE	7e3a0000-7e3a9000	\               oleacc
ELF	7e3a9000-7e43b000	Deferred        winmm<elf>
  \-PE	7e3b0000-7e43b000	\               winmm
ELF	7e43b000-7e485000	Deferred        dsound<elf>
  \-PE	7e440000-7e485000	\               dsound
ELF	7e485000-7e594000	Deferred        wined3d<elf>
  \-PE	7e4a0000-7e594000	\               wined3d
ELF	7e594000-7e5c5000	Deferred        d3d9<elf>
  \-PE	7e5a0000-7e5c5000	\               d3d9
ELF	7e5c5000-7e5f2000	Deferred        ws2_32<elf>
  \-PE	7e5d0000-7e5f2000	\               ws2_32
ELF	7e5f2000-7e605000	Deferred        libresolv.so.2
ELF	7e605000-7e624000	Deferred        iphlpapi<elf>
  \-PE	7e610000-7e624000	\               iphlpapi
ELF	7e624000-7e64a000	Deferred        netapi32<elf>
  \-PE	7e630000-7e64a000	\               netapi32
ELF	7e64a000-7e670000	Deferred        secur32<elf>
  \-PE	7e650000-7e670000	\               secur32
ELF	7e670000-7e6be000	Deferred        gdiplus<elf>
  \-PE	7e680000-7e6be000	\               gdiplus
ELF	7e6be000-7e723000	Deferred        rpcrt4<elf>
  \-PE	7e6d0000-7e723000	\               rpcrt4
ELF	7e723000-7e830000	Deferred        ole32<elf>
  \-PE	7e740000-7e830000	\               ole32
ELF	7e830000-7e916000	Deferred        oleaut32<elf>
  \-PE	7e850000-7e916000	\               oleaut32
ELF	7e916000-7e9d7000	Deferred        comctl32<elf>
  \-PE	7e920000-7e9d7000	\               comctl32
ELF	7e9d7000-7ea32000	Deferred        shlwapi<elf>
  \-PE	7e9e0000-7ea32000	\               shlwapi
ELF	7ea32000-7ebbb000	Deferred        shell32<elf>
  \-PE	7ea40000-7ebbb000	\               shell32
ELF	7ebbb000-7ec0f000	Deferred        advapi32<elf>
  \-PE	7ebd0000-7ec0f000	\               advapi32
ELF	7ec0f000-7ecad000	Deferred        gdi32<elf>
  \-PE	7ec20000-7ecad000	\               gdi32
ELF	7ecad000-7edf7000	Deferred        user32<elf>
  \-PE	7ecd0000-7edf7000	\               user32
ELF	7edf7000-7ee61000	Deferred        msvcrt<elf>
  \-PE	7ee10000-7ee61000	\               msvcrt
ELF	7ee61000-7ee6c000	Deferred        libnss_files.so.2
ELF	7ee6c000-7ee76000	Deferred        libnss_nis.so.2
ELF	7ee76000-7ee8e000	Deferred        libnsl.so.1
ELF	7ee8e000-7ee97000	Deferred        libnss_compat.so.2
ELF	7ee97000-7ee99000	Deferred        libxcb-xlib.so.0
ELF	7efc9000-7efee000	Deferred        libm.so.6
ELF	b7c82000-b7c86000	Deferred        libdl.so.2
ELF	b7c86000-b7dd5000	Deferred        libc.so.6
ELF	b7dd6000-b7dee000	Deferred        libpthread.so.0
ELF	b7e00000-b7f3b000	Deferred        libwine.so.1
ELF	b7f3d000-b7f59000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
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
0000001b (D) C:\Program Files\Microsoft Games\Purble Place\PurblePlace.exe
	0000001c    0 <==
Backtrace:
=>0 0x7bc46dcc in ntdll (+0x36dcc) (0x0033f9f4)
  1 0x0034004b (0x0033fe68)
  2 0x0103b45b in purbleplace (+0x3b45b) (0x0033fe7c)
  3 0x010491ca in purbleplace (+0x491ca) (0x0033ff08)
  4 0x7b877c47 in kernel32 (+0x57c47) (0x0033ffe8)
wine: Call from 0x1053e2b to unimplemented function KERNEL32.dll.WTSGetActiveConsoleSessionId, aborting
wine: Call from 0x1053e2b to unimplemented function KERNEL32.dll.WTSGetActiveConsoleSessionId, aborting
err:seh:cxx_frame_handler invalid frame magic 19930522
err:seh:cxx_frame_handler invalid frame magic 19930522

paul@paul-laptop:~$ wine Purble\ Place.exe > purbleplaceerrors.txt
fixme:shell:SHAutoComplete SHAutoComplete stub
fixme:shell:DllCanUnloadNow stub
fixme:exec:SHELL_execute flags ignored: 0x00000180
paul@paul-laptop:~$ fixme:shell:DllCanUnloadNow stub
wine: Call from 0x1053e2b to unimplemented function KERNEL32.dll.WTSGetActiveConsoleSessionId, aborting
err:seh:cxx_frame_handler invalid frame magic 19930522
wine: Unimplemented function KERNEL32.dll.WTSGetActiveConsoleSessionId called at address 0x1053e2b (thread 001c), starting debugger...
Unhandled exception: unimplemented function KERNEL32.dll.WTSGetActiveConsoleSessionId called in 32-bit code (0x7bc46dcc).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc46dcc ESP:0033f990 EBP:0033f9f4 EFLAGS:00000202(   - 00      - - I1)
 EAX:0106e1d6 EBX:7bc914c4 ECX:00000004 EDX:00110058
 ESI:0033f99c EDI:00000000
Stack dump:
0x0033f990:  00000000 00000000 00000000 80000100
0x0033f9a0:  00000001 00000000 01053e2b 00000002
0x0033f9b0:  0106de8c 0106e1d6 00000000 00000000
0x0033f9c0:  00000000 00000000 00000000 00000000
0x0033f9d0:  00000000 00000000 00000000 00000000
0x0033f9e0:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x7bc46dcc in ntdll (+0x36dcc) (0x0033f9f4)
  1 0x0034004b (0x0033fe68)
  2 0x0103b45b in purbleplace (+0x3b45b) (0x0033fe7c)
  3 0x010491ca in purbleplace (+0x491ca) (0x0033ff08)
  4 0x7b877c47 in kernel32 (+0x57c47) (0x0033ffe8)
0x7bc46dcc: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (92 modules)
PE	 1000000- 10f2000	Export          purbleplace
PE	10000000-10011000	Deferred        vista.emulation
ELF	7b800000-7b93c000	Export          kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bcad000	Export          ntdll<elf>
  \-PE	7bc10000-7bcad000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7de8f000-7dea3000	Deferred        midimap<elf>
  \-PE	7de90000-7dea3000	\               midimap
ELF	7dea3000-7deca000	Deferred        msacm32<elf>
  \-PE	7deb0000-7deca000	\               msacm32
ELF	7deca000-7dee1000	Deferred        msacm32<elf>
  \-PE	7ded0000-7dee1000	\               msacm32
ELF	7dee1000-7dfa4000	Deferred        libasound.so.2
ELF	7dfb6000-7dfeb000	Deferred        winealsa<elf>
  \-PE	7dfc0000-7dfeb000	\               winealsa
ELF	7e037000-7e06a000	Deferred        uxtheme<elf>
  \-PE	7e040000-7e06a000	\               uxtheme
ELF	7e06a000-7e073000	Deferred        libxcursor.so.1
ELF	7e073000-7e078000	Deferred        libxfixes.so.3
ELF	7e078000-7e07b000	Deferred        libxcomposite.so.1
ELF	7e07b000-7e081000	Deferred        libxrandr.so.2
ELF	7e081000-7e089000	Deferred        libxrender.so.1
ELF	7e089000-7e08e000	Deferred        libxxf86vm.so.1
ELF	7e08e000-7e091000	Deferred        libxinerama.so.1
ELF	7e091000-7e0b1000	Deferred        imm32<elf>
  \-PE	7e0a0000-7e0b1000	\               imm32
ELF	7e0b1000-7e0b6000	Deferred        libxdmcp.so.6
ELF	7e0b6000-7e0ce000	Deferred        libxcb.so.1
ELF	7e0ce000-7e0d1000	Deferred        libxau.so.6
ELF	7e0d1000-7e1b8000	Deferred        libx11.so.6
ELF	7e1b8000-7e1c6000	Deferred        libxext.so.6
ELF	7e1c6000-7e1de000	Deferred        libice.so.6
ELF	7e1de000-7e1e6000	Deferred        libsm.so.6
ELF	7e1f8000-7e291000	Deferred        winex11<elf>
  \-PE	7e210000-7e291000	\               winex11
ELF	7e2ca000-7e2eb000	Deferred        libexpat.so.1
ELF	7e2eb000-7e315000	Deferred        libfontconfig.so.1
ELF	7e327000-7e33c000	Deferred        libz.so.1
ELF	7e33c000-7e3a9000	Deferred        libfreetype.so.6
ELF	7e3a9000-7e3be000	Deferred        oleacc<elf>
  \-PE	7e3b0000-7e3be000	\               oleacc
ELF	7e3be000-7e450000	Deferred        winmm<elf>
  \-PE	7e3d0000-7e450000	\               winmm
ELF	7e450000-7e49a000	Deferred        dsound<elf>
  \-PE	7e460000-7e49a000	\               dsound
ELF	7e49a000-7e5a9000	Deferred        wined3d<elf>
  \-PE	7e4b0000-7e5a9000	\               wined3d
ELF	7e5a9000-7e5da000	Deferred        d3d9<elf>
  \-PE	7e5b0000-7e5da000	\               d3d9
ELF	7e5da000-7e607000	Deferred        ws2_32<elf>
  \-PE	7e5e0000-7e607000	\               ws2_32
ELF	7e607000-7e61a000	Deferred        libresolv.so.2
ELF	7e61a000-7e639000	Deferred        iphlpapi<elf>
  \-PE	7e620000-7e639000	\               iphlpapi
ELF	7e639000-7e65f000	Deferred        netapi32<elf>
  \-PE	7e640000-7e65f000	\               netapi32
ELF	7e65f000-7e685000	Deferred        secur32<elf>
  \-PE	7e670000-7e685000	\               secur32
ELF	7e685000-7e6d3000	Deferred        gdiplus<elf>
  \-PE	7e690000-7e6d3000	\               gdiplus
ELF	7e6d3000-7e738000	Deferred        rpcrt4<elf>
  \-PE	7e6e0000-7e738000	\               rpcrt4
ELF	7e738000-7e845000	Deferred        ole32<elf>
  \-PE	7e750000-7e845000	\               ole32
ELF	7e845000-7e92b000	Deferred        oleaut32<elf>
  \-PE	7e860000-7e92b000	\               oleaut32
ELF	7e92b000-7e9ec000	Deferred        comctl32<elf>
  \-PE	7e930000-7e9ec000	\               comctl32
ELF	7e9ec000-7ea47000	Deferred        shlwapi<elf>
  \-PE	7ea00000-7ea47000	\               shlwapi
ELF	7ea47000-7ebd0000	Deferred        shell32<elf>
  \-PE	7ea60000-7ebd0000	\               shell32
ELF	7ebd0000-7ec24000	Deferred        advapi32<elf>
  \-PE	7ebe0000-7ec24000	\               advapi32
ELF	7ec24000-7ecc2000	Deferred        gdi32<elf>
  \-PE	7ec30000-7ecc2000	\               gdi32
ELF	7ecc2000-7ee0c000	Deferred        user32<elf>
  \-PE	7ece0000-7ee0c000	\               user32
ELF	7ee0c000-7ee76000	Deferred        msvcrt<elf>
  \-PE	7ee20000-7ee76000	\               msvcrt
ELF	7ee76000-7ee8e000	Deferred        libnsl.so.1
ELF	7ee8e000-7ee97000	Deferred        libnss_compat.so.2
ELF	7efc9000-7efee000	Deferred        libm.so.6
ELF	7efee000-7eff0000	Deferred        libxcb-xlib.so.0
ELF	7eff5000-7f000000	Deferred        libnss_files.so.2
ELF	b7cb1000-b7cbb000	Deferred        libnss_nis.so.2
ELF	b7cbc000-b7cc0000	Deferred        libdl.so.2
ELF	b7cc0000-b7e0f000	Deferred        libc.so.6
ELF	b7e10000-b7e28000	Deferred        libpthread.so.0
ELF	b7e3a000-b7f75000	Deferred        libwine.so.1
ELF	b7f77000-b7f93000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
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
0000001b (D) C:\Program Files\Microsoft Games\Purble Place\PurblePlace.exe
	0000001c    0 <==
Backtrace:
=>0 0x7bc46dcc in ntdll (+0x36dcc) (0x0033f9f4)
  1 0x0034004b (0x0033fe68)
  2 0x0103b45b in purbleplace (+0x3b45b) (0x0033fe7c)
  3 0x010491ca in purbleplace (+0x491ca) (0x0033ff08)
  4 0x7b877c47 in kernel32 (+0x57c47) (0x0033ffe8)
wine: Call from 0x1053e2b to unimplemented function KERNEL32.dll.WTSGetActiveConsoleSessionId, aborting
err:seh:cxx_frame_handler invalid frame magic 19930522
err:seh:cxx_frame_handler invalid frame magic 19930522

```

Any suggestions?

Hardy Heron 8.04, fully up-to-date, using wine 1.1.14 from wine repository, Intel graphics and processor

---

### Post by zami on 2009-02-08
Not a clue.

But let me tell you my six year old would be thrilled if I got this going.

If I figure anything out I'll post - meanwhile I'll be loitering in this thread to see if someone else gets it figured out!

-zami

---

### Post by Dizzle7677 on 2009-02-08
Is it a 64-bit app? Change the version from Xp to Vista in Winecfg. Make the Dll->Dll.old. Run in a link(pref) or in terminal: env WINEPREFIX="/path/to/.wine" wine "C:\Program Files\Microsoft Games\Purble Place\PurblePlace.exe
" Install vcrun5000? Replace the wine msvcrt.dll with a [ms one]("http://www.dll-files.com/dllindex/dll-files.shtml?msvcrt") just for s&giggles.

---

### Post by pbotros1234 on 2009-02-08
> Is it a 64-bit app? Change the version from Xp to Vista in Winecfg. Make the Dll->Dll.old. Run in a link(pref) or in terminal: env WINEPREFIX="/path/to/.wine" wine "C:\Program Files\Microsoft Games\Purble Place\PurblePlace.exe
" Install vcrun5000? Replace the wine msvcrt.dll with a ms one just for s&giggles. 

Nothing of that worked. Used winetricks to install vcrun2008 and various other things (the latest visual basic, something else), nothing worked. Tried switching from emulating Vista to XP at each impass.

Also tried redownloading kernel32.dll, ntdll.dll, and msvcrt.dll from DLL-files and replacing them in ~/.wine/drive_c/system32/. Didn't work :(

Ideas anyone?

---

### Post by pbotros1234 on 2009-02-10
Bump?

---

### Post by zami on 2009-02-11
> **pbotros1234 said:**
> Bump?

I still got nothin'!

I'm installing every possible doodad via winetricks hoping it's something silly and easy missing.  But I suspect we are stumped at this kernal32.dll error.  That sounds like a system wide library ever there was one.

Maybe one of our resident Wine gurus will have a smarter idea.  :D

-zami

---

### Post by donkyhotay on 2009-02-11
Problem looks like something specific to vista that hasn't been implemented in wine, take a look at the line at the top where the problem begins:
```
wine: Call from 0x1053e2b to unimplemented function KERNEL32.dll.WTSGetActiveConsoleSessionId, aborting
```
This is also repeated near the bottom as well. The wine kernel32 is missing the required function WTSGetActiveConsoleSessionId that purble place apparently uses and without that I don't think you'll get it to run. Using the windows kernel32 is a bad idea from what I know of how wine runs which means it will need to be coded into the wine kernel itself. This is going to basically take a reverse engineering guru to figure out exactly what that function does, what variables it is meant to accept, what variables it is meant to return, then code it into wine itself.

//edit: what do you want to bet this function doesn't do anything useful and is meant to break XP compatibility? (c;

---

