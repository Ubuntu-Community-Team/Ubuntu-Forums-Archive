---
title: "FEAR Combat"
date: 2009-05-14
forum: Wine
---

### Post by wolfyking2 on 2009-05-14
I'm trying to get FEAR Combat working, it installed ok and everything, but when I try to start the game, I get the message 'FEARMP.exe has encountered a serious problem and needs to close' then all that stuff about looking it up in wine APPDB.  I've looked it up their...It's giving me mixed results.  Some people have gotten the game too work, others haven't.  Here's a terminal output

```
user@ubuntu:~$ '/home/user/.wine/drive_c/Program Files/Sierra/FEARCombat/FEARMP.exe' 
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0xed664c): Stub!
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0xed493c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0xed493c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0xed493c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0xed493c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0xed4750,0x00000000), stub!
wine: Call from 0x7bc4721c to unimplemented function GDI32.dll.GdiEntry1, aborting
wine: Unimplemented function GDI32.dll.GdiEntry1 called at address 0x7bc4721c (thread 0009), starting debugger...
Unhandled exception: unimplemented function GDI32.dll.GdiEntry1 called in 32-bit code (0x7bc4721c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc4721c ESP:00ed4014 EBP:00ed4078 EFLAGS:00200206(   - 00      - -IP1)
 EAX:003babbe EBX:7bc91448 ECX:001362a8 EDX:001362e4
 ESI:00ed4020 EDI:00000000
Stack dump:
0x00ed4014:  00730077 0073005c 00730079 80000100
0x00ed4024:  00000001 00000000 7bc4721c 00000002
0x00ed4034:  003babf4 003babbe 0065002e 00650078
0x00ed4044:  00ed0000 00ed4684 00000000 00000000
0x00ed4054:  00000000 00000000 00000000 7bc84e14
0x00ed4064:  00000000 ffffffff 00000000 001362dc
Backtrace:
=>0 0x7bc4721c in ntdll (+0x3721c) (0x00ed4078)
  1 0x003f001e (0x00ed48d4)
  2 0x0025ae42 in d3d9 (+0x2ae42) (0x00ed4c88)
  3 0x0025c445 in d3d9 (+0x2c445) (0x00ed4cb0)
  4 0x00259f35 in d3d9 (+0x29f35) (0x00ed4eb4)
  5 0x0025a5dd in d3d9 (+0x2a5dd) (0x00ed4fcc)
  6 0x00668bbe in fearmp (+0x268bbe) (0x00ed5010)
  7 0x00668ffe in fearmp (+0x268ffe) (0x00ed6650)
  8 0x006223ef in fearmp (+0x2223ef) (0x00eef960)
  9 0x00597a76 in fearmp (+0x197a76) (0x00eefdbc)
  10 0x00000001 (0x7bc43c5d)
  11 0x00000090 (0x840fc085)
0x7bc4721c: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (88 modules)
PE	  230000-  3d9000	Export          d3d9
PE	  3e0000-  3e5000	Deferred        d3d8thk
PE	  400000-  ce7000	Export          fearmp
PE	  ef0000-  f9e000	Deferred        dinput8
PE	  fa0000- 11ef000	Deferred        d3dx9_27
ELF	7b800000-7b944000	Deferred        kernel32<elf>
  \-PE	7b820000-7b944000	\               kernel32
ELF	7bc00000-7bcad000	Export          ntdll<elf>
  \-PE	7bc10000-7bcad000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
ELF	7e2a0000-7e2d3000	Deferred        uxtheme<elf>
  \-PE	7e2b0000-7e2d3000	\               uxtheme
ELF	7e2d3000-7e2e7000	Deferred        midimap<elf>
  \-PE	7e2e0000-7e2e7000	\               midimap
ELF	7e2e7000-7e30c000	Deferred        msacm32<elf>
  \-PE	7e2f0000-7e30c000	\               msacm32
ELF	7e30c000-7e323000	Deferred        msacm32<elf>
  \-PE	7e310000-7e323000	\               msacm32
ELF	7e323000-7e35f000	Deferred        wineoss<elf>
  \-PE	7e330000-7e35f000	\               wineoss
ELF	7e35f000-7e368000	Deferred        libxcursor.so.1
ELF	7e368000-7e36d000	Deferred        libxfixes.so.3
ELF	7e36d000-7e370000	Deferred        libxcomposite.so.1
ELF	7e370000-7e376000	Deferred        libxrandr.so.2
ELF	7e376000-7e37e000	Deferred        libxrender.so.1
ELF	7e37e000-7e383000	Deferred        libxxf86vm.so.1
ELF	7e383000-7e386000	Deferred        libxinerama.so.1
ELF	7e386000-7e3a5000	Deferred        imm32<elf>
  \-PE	7e390000-7e3a5000	\               imm32
ELF	7e3a5000-7e3aa000	Deferred        libxdmcp.so.6
ELF	7e3aa000-7e3c2000	Deferred        libxcb.so.1
ELF	7e3c2000-7e4a9000	Deferred        libx11.so.6
ELF	7e4a9000-7e4b7000	Deferred        libxext.so.6
ELF	7e4b7000-7e4cf000	Deferred        libice.so.6
ELF	7e4cf000-7e4d7000	Deferred        libsm.so.6
ELF	7e4ea000-7e583000	Deferred        winex11<elf>
  \-PE	7e500000-7e583000	\               winex11
ELF	7e5cd000-7e5ee000	Deferred        libexpat.so.1
ELF	7e5ee000-7e618000	Deferred        libfontconfig.so.1
ELF	7e618000-7e62d000	Deferred        libz.so.1
ELF	7e62d000-7e69a000	Deferred        libfreetype.so.6
ELF	7e69a000-7e75d000	Deferred        comctl32<elf>
  \-PE	7e6a0000-7e75d000	\               comctl32
ELF	7e75d000-7e7b8000	Deferred        shlwapi<elf>
  \-PE	7e770000-7e7b8000	\               shlwapi
ELF	7e7b8000-7e942000	Deferred        shell32<elf>
  \-PE	7e7d0000-7e942000	\               shell32
ELF	7e942000-7e955000	Deferred        libresolv.so.2
ELF	7e956000-7e959000	Deferred        libxau.so.6
ELF	7e968000-7e986000	Deferred        iphlpapi<elf>
  \-PE	7e970000-7e986000	\               iphlpapi
ELF	7e986000-7e9b3000	Deferred        ws2_32<elf>
  \-PE	7e990000-7e9b3000	\               ws2_32
ELF	7e9b3000-7e9cd000	Deferred        wsock32<elf>
  \-PE	7e9c0000-7e9cd000	\               wsock32
ELF	7e9cd000-7eaaf000	Deferred        oleaut32<elf>
  \-PE	7e9e0000-7eaaf000	\               oleaut32
ELF	7eaaf000-7eb19000	Deferred        rpcrt4<elf>
  \-PE	7eac0000-7eb19000	\               rpcrt4
ELF	7eb19000-7ec0e000	Deferred        ole32<elf>
  \-PE	7eb30000-7ec0e000	\               ole32
ELF	7ec0e000-7ec9f000	Deferred        winmm<elf>
  \-PE	7ec20000-7ec9f000	\               winmm
ELF	7ec9f000-7ecb2000	Deferred        lz32<elf>
  \-PE	7eca0000-7ecb2000	\               lz32
ELF	7ecb2000-7eccb000	Deferred        version<elf>
  \-PE	7ecc0000-7eccb000	\               version
ELF	7eccb000-7ed1f000	Deferred        advapi32<elf>
  \-PE	7ece0000-7ed1f000	\               advapi32
ELF	7ed1f000-7edbd000	Deferred        gdi32<elf>
  \-PE	7ed30000-7edbd000	\               gdi32
ELF	7edbd000-7ef04000	Deferred        user32<elf>
  \-PE	7ede0000-7ef04000	\               user32
ELF	7ef04000-7ef6f000	Deferred        msvcrt<elf>
  \-PE	7ef10000-7ef6f000	\               msvcrt
ELF	7efa5000-7efb0000	Deferred        libnss_files.so.2
ELF	7efb0000-7efc8000	Deferred        libnsl.so.1
ELF	7efc8000-7efed000	Deferred        libm.so.6
ELF	7efed000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7ca0000-b7ca2000	Deferred        libxcb-xlib.so.0
ELF	b7ca9000-b7cad000	Deferred        libdl.so.2
ELF	b7cad000-b7dfc000	Deferred        libc.so.6
ELF	b7dfd000-b7e15000	Deferred        libpthread.so.0
ELF	b7e28000-b7f63000	Deferred        libwine.so.1
ELF	b7f65000-b7f81000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Sierra\FEARCombat\FEARMP.exe
	00000009    0 <==
0000000c 
	00000017    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000022 
	00000023    0
Backtrace:
=>0 0x7bc4721c in ntdll (+0x3721c) (0x00ed4078)
  1 0x003f001e (0x00ed48d4)
  2 0x0025ae42 in d3d9 (+0x2ae42) (0x00ed4c88)
  3 0x0025c445 in d3d9 (+0x2c445) (0x00ed4cb0)
  4 0x00259f35 in d3d9 (+0x29f35) (0x00ed4eb4)
  5 0x0025a5dd in d3d9 (+0x2a5dd) (0x00ed4fcc)
  6 0x00668bbe in fearmp (+0x268bbe) (0x00ed5010)
  7 0x00668ffe in fearmp (+0x268ffe) (0x00ed6650)
  8 0x006223ef in fearmp (+0x2223ef) (0x00eef960)
  9 0x00597a76 in fearmp (+0x197a76) (0x00eefdbc)
  10 0x00000001 (0x7bc43c5d)
  11 0x00000090 (0x840fc085)
wine: Call from 0x7bc4721c to unimplemented function GDI32.dll.GdiEntry1, aborting
user@ubuntu:~$ 


```

Need some help please!  I have an intel graphics chip, but I've seen it run on one worse then mine.

---

### Post by wolfyking2 on 2009-05-15
bump

---

### Post by asdfoo on 2009-05-15
> **wolfyking2 said:**
> bump

you are using native dlls?

move or remove your ~/.wine prefix and install from scratch, do not install any native dlls from windows

---

### Post by Bios Element on 2009-05-15
Do yourself a favor and re-read the Wine AppDB Entry. I got FEAR working a week or so ago and it was running nearly perfect. You do need a DX9 (I think) DLL which is listed somewhere in the AppDB Entry.

EDIT: It's d3dx9_36.dll

---

### Post by wolfyking2 on 2009-05-15
I have that DLL...and the person who said get it from scratch, do you mean compile it?  I'll try to reinstall and see if that helps.

EDIT:  Got it too work, but now it says my video card is unsupported?  I've seen this game run on an intel 950 GMA (or whatever it's called) So how can my intel card be unsupported?

---

### Post by asdfoo on 2009-05-15
> **wolfyking2 said:**
> I have that DLL...and the person who said get it from scratch, do you mean compile it?  I'll try to reinstall and see if that helps.

EDIT:  Got it too work, but now it says my video card is unsupported?  I've seen this game run on an intel 950 GMA (or whatever it's called) So how can my intel card be unsupported?


from scratch, I meant reinstall in a clean prefix

mv ~/.wine ~/.wine-broken
wine /media/cdrom/setup.exe 

Perhaps the video card detection is not correct for GMA 950?  I suggest you post over at [http://forum.winehq.org](http://forum.winehq.org) saying that you have installed fear in a clean prefix and this is the message you get, ask if the autodetection is present for intel 950 GMA

---

### Post by NightMKoder on 2009-05-15
That's most definitely a broken wine prefix. You installed DX9 and its trying to do windows things that...wont work in wine. 

If you didn't install dx9 - make sure that none of the dx dlls are set to native in winecfg. You may have them in the wine prefix, just don't set them to native.

---

### Post by wolfyking2 on 2009-05-16
k, I'll try.

---

