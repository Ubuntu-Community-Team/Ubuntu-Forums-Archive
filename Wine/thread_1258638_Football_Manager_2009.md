---
title: "Football Manager 2009"
date: 2009-09-05
forum: Wine
---

### Post by betterspud on 2009-09-05
Hi all. Am fairly new to Ubuntu (and Linux in general) and am trying to learn my way around still.

Have managed to get Football Manager 2009 installed, patched and activated with no problems, but it still fails to run. I know that my laptop is plenty capable of running the game, cos I've previously had it installed thru Windoze, but I'm stumped as to why it won't run.

Running it thru the Main Menu simply causes a screen flicker, then nothing, so I tried running it from Terminal and it failed after spewing out a bunch of stuff, none of which I understand. Am hoping that someone among you can shed some light.

```
simon@Simon-MedionLaptop:~$ env WINEPREFIX="/home/simon/.wine" wine "C:\Program Files\Sports Interactive\Football Manager 2009\fm.exe" 
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
fixme:powrprof:DllMain (0x613f0000, 1, (nil)) not fully implemented
wine: Call from 0x7b845450 to unimplemented function pdh.dll.PdhMakeCounterPathW, aborting
wine: Unimplemented function pdh.dll.PdhMakeCounterPathW called at address 0x7b845450 (thread 0009), starting debugger...
Unhandled exception: unimplemented function pdh.dll.PdhMakeCounterPathW called in 32-bit code (0x7b8454c3).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b8454c3 ESP:0032f2c4 EBP:0032f328 EFLAGS:00200246(   - 00      - IZP1)
 EAX:7b82ecb9 EBX:7b8b7ff4 ECX:00000000 EDX:0032f350
 ESI:0032f350 EDI:021999d0
Stack dump:
0x0032f2c4:  0032f350 00000008 0000003c 80000100
0x0032f2d4:  00000001 00000000 7b845450 00000002
0x0032f2e4:  607f61a0 607f6706 00000020 00000000
0x0032f2f4:  00000000 00000000 00000000 00000000
0x0032f304:  00000000 00000000 00000000 0013e7e0
0x0032f314:  00000000 00110000 7b84545a 00000000
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x0032f328)
  2 0x607f6125 in pdh (+0x6125) (0x0032f358)
0x7b8454c3: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (142 modules)
PE	  390000-  3b6000	Deferred        intellaptopgamingxp
PE	  400000- 21ec000	Deferred        fm
PE	 21f0000- 25a7000	Deferred        d3dx9_37
PE	10000000-10089000	Deferred        saauditmd
ELF	60000000-6001f000	Deferred        ld-linux.so.2
ELF	6001f000-60039000	Deferred        libpthread.so.0
ELF	60039000-60191000	Deferred        libc.so.6
ELF	60191000-60195000	Deferred        libdl.so.2
ELF	60195000-6019e000	Deferred        libnss_compat.so.2
ELF	6019e000-601b7000	Deferred        libnsl.so.1
ELF	601b7000-60303000	Deferred        user32<elf>
  \-PE	601d0000-60303000	\               user32
ELF	60303000-603a3000	Deferred        gdi32<elf>
  \-PE	60310000-603a3000	\               gdi32
ELF	603a3000-603f6000	Deferred        advapi32<elf>
  \-PE	603b0000-603f6000	\               advapi32
ELF	603f6000-6050a000	Deferred        shell32<elf>
  \-PE	60410000-6050a000	\               shell32
ELF	6050a000-60576000	Deferred        msvcrt<elf>
  \-PE	60520000-60576000	\               msvcrt
ELF	60576000-6063b000	Deferred        comctl32<elf>
  \-PE	60580000-6063b000	\               comctl32
ELF	6063b000-606e1000	Deferred        ole32<elf>
  \-PE	60650000-606e1000	\               ole32
ELF	606e1000-60700000	Deferred        iphlpapi<elf>
  \-PE	606f0000-60700000	\               iphlpapi
ELF	60700000-60716000	Deferred        libresolv.so.2
ELF	60716000-60747000	Deferred        d3d9<elf>
  \-PE	60720000-60747000	\               d3d9
ELF	60747000-607b0000	Deferred        setupapi<elf>
  \-PE	60750000-607b0000	\               setupapi
ELF	607b0000-607cb000	Deferred        version<elf>
  \-PE	607c0000-607cb000	\               version
ELF	607cb000-607e0000	Deferred        lz32<elf>
  \-PE	607d0000-607e0000	\               lz32
ELF	607e0000-607fb000	Export          pdh<elf>
  \-PE	607f0000-607fb000	\               pdh
ELF	607fb000-6081c000	Deferred        imm32<elf>
  \-PE	60800000-6081c000	\               imm32
ELF	6081c000-60849000	Deferred        ws2_32<elf>
  \-PE	60820000-60849000	\               ws2_32
ELF	60849000-6085e000	Deferred        wtsapi32<elf>
  \-PE	60850000-6085e000	\               wtsapi32
ELF	6085e000-60874000	Deferred        psapi<elf>
  \-PE	60860000-60874000	\               psapi
ELF	60874000-60908000	Deferred        winmm<elf>
  \-PE	60880000-60908000	\               winmm
ELF	60908000-60958000	Deferred        wininet<elf>
  \-PE	60910000-60958000	\               wininet
ELF	60958000-6097b000	Deferred        mpr<elf>
  \-PE	60960000-6097b000	\               mpr
ELF	6097b000-609e4000	Deferred        crypt32<elf>
  \-PE	60990000-609e4000	\               crypt32
ELF	609e4000-60a1b000	Deferred        winspool<elf>
  \-PE	609f0000-60a1b000	\               winspool
ELF	60a1b000-60ac9000	Deferred        comdlg32<elf>
  \-PE	60a20000-60ac9000	\               comdlg32
ELF	60ac9000-60af0000	Deferred        oledlg<elf>
  \-PE	60ad0000-60af0000	\               oledlg
ELF	60af0000-60b05000	Deferred        oleacc<elf>
  \-PE	60b00000-60b05000	\               oleacc
ELF	60b05000-60b84000	Deferred        libfreetype.so.6
ELF	60b84000-60b9a000	Deferred        libz.so.1
ELF	60b9a000-60bc7000	Deferred        libfontconfig.so.1
ELF	60bc7000-60bee000	Deferred        libexpat.so.1
ELF	60bee000-60c89000	Deferred        winex11<elf>
  \-PE	60c00000-60c89000	\               winex11
ELF	60c89000-60c92000	Deferred        libsm.so.6
ELF	60c92000-60cad000	Deferred        libice.so.6
ELF	60cad000-60cbd000	Deferred        libxext.so.6
ELF	60cbd000-60dec000	Deferred        libx11.so.6
ELF	60dec000-60df1000	Deferred        libuuid.so.1
ELF	60df1000-60df6000	Deferred        libxdmcp.so.6
ELF	60df6000-60df9000	Deferred        libxinerama.so.1
ELF	60df9000-60e03000	Deferred        libxrender.so.1
ELF	60e03000-60e0c000	Deferred        libxrandr.so.2
ELF	60e0c000-60e10000	Deferred        libxcomposite.so.1
ELF	60e10000-60e1b000	Deferred        libxcursor.so.1
ELF	60e1b000-60e4e000	Deferred        uxtheme<elf>
  \-PE	60e20000-60e4e000	\               uxtheme
ELF	60e4e000-60e85000	Deferred        winealsa<elf>
  \-PE	60e60000-60e85000	\               winealsa
ELF	60e85000-60f66000	Deferred        libasound.so.2
ELF	60f66000-60f6f000	Deferred        librt.so.1
ELF	60f72000-60fb5000	Deferred        libpulse.so.0
ELF	60fb5000-61005000	Deferred        libpulsecommon-0.9.16.so
ELF	61005000-61071000	Deferred        libsndfile.so.1
ELF	61071000-610b3000	Deferred        libdbus-1.so.3
ELF	610b3000-61103000	Deferred        libflac.so.8
ELF	61103000-6110a000	Deferred        libogg.so.0
ELF	6110a000-61132000	Deferred        msacm32<elf>
  \-PE	61110000-61132000	\               msacm32
ELF	61132000-61147000	Deferred        midimap<elf>
  \-PE	61140000-61147000	\               midimap
ELF	61147000-61191000	Deferred        libcups.so.2
ELF	61191000-611be000	Deferred        libgssapi_krb5.so.2
ELF	611be000-61266000	Deferred        libgnutls.so.26
ELF	61266000-61273000	Deferred        libavahi-common.so.3
ELF	61273000-61284000	Deferred        libavahi-client.so.3
ELF	61284000-61336000	Deferred        libkrb5.so.3
ELF	61336000-61361000	Deferred        libk5crypto.so.3
ELF	61361000-61365000	Deferred        libcom_err.so.2
ELF	61365000-6136e000	Deferred        libkrb5support.so.0
ELF	6136e000-61372000	Deferred        libkeyutils.so.1
ELF	61372000-613ee000	Deferred        libgcrypt.so.11
ELF	613ee000-61404000	Deferred        powrprof<elf>
  \-PE	613f0000-61404000	\               powrprof
ELF	642ee000-64319000	Deferred        libvorbis.so.0
ELF	64c9d000-64ce9000	Deferred        dbghelp<elf>
  \-PE	64cb0000-64ce9000	\               dbghelp
ELF	65e7f000-65ee2000	Deferred        rpcrt4<elf>
  \-PE	65e90000-65ee2000	\               rpcrt4
ELF	67ca3000-67cc1000	Deferred        libxcb.so.1
ELF	69ba2000-69ba6000	Deferred        libxau.so.6
ELF	6ac85000-6acad000	Deferred        libm.so.6
ELF	6b7c3000-6b7cc000	Deferred        libwrap.so.0
ELF	6dfe7000-6e0fc000	Deferred        wined3d<elf>
  \-PE	6e000000-6e0fc000	\               wined3d
ELF	6e743000-6e74e000	Deferred        libnss_nis.so.2
ELF	70391000-704c8000	Deferred        libwine.so.1
PE	70bd0000-70c35000	Deferred        shlwapi
ELF	71275000-7128e000	Deferred        msacm32<elf>
  \-PE	71280000-7128e000	\               msacm32
ELF	7143e000-71444000	Deferred        libxfixes.so.3
ELF	721df000-7222b000	Deferred        dsound<elf>
  \-PE	721f0000-7222b000	\               dsound
ELF	7498b000-74998000	Deferred        libnss_files.so.2
ELF	74f77000-74f7d000	Deferred        libxxf86vm.so.1
ELF	75aba000-75abf000	Deferred        libgpg-error.so.0
ELF	75e00000-75e15000	Deferred        faultrep<elf>
  \-PE	75e10000-75e15000	\               faultrep
ELF	76213000-76225000	Deferred        libtasn1.so.3
PE	78130000-781cb000	Deferred        msvcr80
ELF	79b7c000-79c76000	Deferred        libvorbisenc.so.2
ELF	7b5d5000-7b67b000	Deferred        oleaut32<elf>
  \-PE	7b5f0000-7b67b000	\               oleaut32
ELF	7b800000-7b93d000	Export          kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
PE	7c420000-7c4a7000	Deferred        msvcp80
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
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
0000001f 
	00000023    0
	00000022    0
	00000021    0
	00000020    0
0000001d (D) C:\Program Files\Sports Interactive\Football Manager 2009\fm.exe
	00000009    0 <==
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x0032f328)
  2 0x607f6125 in pdh (+0x6125) (0x0032f358)
wine: Call from 0x7b845450 to unimplemented function pdh.dll.PdhOpenLogA, aborting
```

That's what I get...

FWIW I'm on a cleanly installed Karmic setup to which I have added Wine and winetricks (directx9, vcrun2005, vcrun2005 sp1 & ie6 all installed)

Dunno what other clues to throw you. If anyone needs any more info, let me know. Would be very grateful for whatever help can be offered, especially if it works

Hopefully someone out there has found a solution to this already...

---

### Post by ackanao on 2009-09-05
Delete your ~/.wine folder and recreate it again:

```
winecfg
```
As far as I can tell from the instructions posted on this page you only need pdh.dll to make it work:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8597]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=8597")

Do not install DirectX in Wine because it will mess up your Wine setup:

[http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2]("http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2")

---

### Post by ScottNN on 2009-09-29
Hey,

Use

```
sh winetricks pdh
```

That should do the trick.

Cheers
Scott

---

