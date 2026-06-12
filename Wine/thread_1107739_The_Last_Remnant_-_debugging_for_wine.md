---
title: "The Last Remnant - debugging for wine?"
date: 2009-03-27
forum: Wine
---

### Post by waltons_pacman on 2009-03-27
OK, so i managed to get a copy of The Last Remnant and would LOVE to get it going in linux through wine.

install works with wine 1.1.17, as far as i can tell.
here is my output from attempting to run it through terminal:

```
fixme:mixer:ALSA_MixerInit No master control found on Vega USB 2.0 Camera., disabling mixer
fixme:powrprof:DllMain (0x7e410000, 1, 0x1) not fully implemented
fixme:faultrep:ReportFault 0x52c9f4 0x0 stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x11a2c5c7 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x11a2c5c7).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:11a2c5c7 ESP:0052fe34 EBP:0052fe78 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:10f38e10
 ESI:00000001 EDI:00000000
Stack dump:
0x0052fe34:  00000000 00000001 00000000 0000000c
0x0052fe44:  00000000 11a32b24 10903143 1272d47c
0x0052fe54:  00114501 00000000 00000001 0052fe50
0x0052fe64:  0052f978 0052fef8 11a28726 12460998
0x0052fe74:  ffffffff 0052ff08 11a28b1e 10900000
0x0052fe84:  00000000 00114501 0000000a 9e3bf63d
Backtrace:
=>0 0x11a2c5c7 in tlr (+0x112c5c7) (0x0052fe78)
  1 0x11a28b1e in tlr (+0x1128b1e) (0x0052ff08)
  2 0x7b878200 in kernel32 (+0x58200) (0x0052ffe8)
  3 0xf7e0add7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x11a2c5c7: cmpl	%ebx,0x0(%eax)
Modules:
Module	Address			Debug info	Name (146 modules)
PE	  530000-  545000	Deferred        steam_api
PE	  550000-  5b3000	Deferred        nxcooking
PE	  5c0000-  611000	Deferred        vorbis
PE	  620000-  628000	Deferred        ogg
PE	  630000-  722000	Deferred        vorbisenc
PE	  730000-  738000	Deferred        vorbisfile
PE	  740000-  770000	Deferred        wxdockitu
PE	  880000-  894000	Deferred        xinput1_3
PE	  8a0000-  8b2000	Deferred        libresample
PE	10000000-103d0000	Deferred        wxmsw262u
PE	10900000-12962000	Export          tlr
PE	18000000-18038000	Deferred        binkw32
PE	21100000-21199000	Deferred        mss32
PE	78130000-781cb000	Deferred        msvcr80
ELF	7a8ea000-7b800000	Deferred        libglcore.so.1
ELF	7b800000-7b93e000	Export          kernel32<elf>
  \-PE	7b820000-7b93e000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
PE	7c420000-7c4a7000	Deferred        msvcp80
ELF	7d88e000-7d948000	Deferred        libgl.so.1
ELF	7d948000-7d9b1000	Deferred        libgcrypt.so.11
ELF	7d9b1000-7d9c3000	Deferred        libtasn1.so.3
ELF	7d9c3000-7d9f5000	Deferred        libcrypt.so.1
ELF	7d9f5000-7d9fb000	Deferred        libnss_dns.so.2
ELF	7d9fb000-7d9fe000	Deferred        libnss_mdns4_minimal.so.2
ELF	7da00000-7da04000	Deferred        libgpg-error.so.0
ELF	7da04000-7da0d000	Deferred        libkrb5support.so.0
ELF	7da0d000-7daaa000	Deferred        libgnutls.so.26
ELF	7daaa000-7dace000	Deferred        libk5crypto.so.3
ELF	7dace000-7db60000	Deferred        libkrb5.so.3
ELF	7db60000-7db8a000	Deferred        libgssapi_krb5.so.2
ELF	7db8a000-7dbc0000	Deferred        libcups.so.2
ELF	7dc23000-7dc38000	Deferred        midimap<elf>
  \-PE	7dc30000-7dc38000	\               midimap
ELF	7dc38000-7dc5e000	Deferred        msacm32<elf>
  \-PE	7dc40000-7dc5e000	\               msacm32
ELF	7dc5e000-7dc77000	Deferred        msacm32<elf>
  \-PE	7dc60000-7dc77000	\               msacm32
ELF	7dc77000-7dc80000	Deferred        librt.so.1
ELF	7dc80000-7dd48000	Deferred        libasound.so.2
ELF	7dd48000-7dd7f000	Deferred        winealsa<elf>
  \-PE	7dd50000-7dd7f000	\               winealsa
ELF	7dd7f000-7ddb2000	Deferred        uxtheme<elf>
  \-PE	7dd90000-7ddb2000	\               uxtheme
ELF	7ddb2000-7ddbb000	Deferred        libxcursor.so.1
ELF	7ddbb000-7ddc0000	Deferred        libxfixes.so.3
ELF	7ddc0000-7ddc4000	Deferred        libxcomposite.so.1
ELF	7ddc4000-7ddcb000	Deferred        libxrandr.so.2
ELF	7ddcb000-7ddd5000	Deferred        libxrender.so.1
ELF	7ddd5000-7dddb000	Deferred        libxxf86vm.so.1
ELF	7dddb000-7ddde000	Deferred        libxinerama.so.1
ELF	7ddde000-7dde3000	Deferred        libxdmcp.so.6
ELF	7dde3000-7ddfc000	Deferred        libxcb.so.1
ELF	7ddfc000-7ddff000	Deferred        libxcb-xlib.so.0
ELF	7ddff000-7de02000	Deferred        libxau.so.6
ELF	7de02000-7def1000	Deferred        libx11.so.6
ELF	7def1000-7df00000	Deferred        libxext.so.6
ELF	7df03000-7df07000	Deferred        libkeyutils.so.1
ELF	7df10000-7df14000	Deferred        libcom_err.so.2
ELF	7df14000-7df17000	Deferred        libnss_mdns4.so.2
ELF	7df17000-7dfb3000	Deferred        winex11<elf>
  \-PE	7df30000-7dfb3000	\               winex11
ELF	7e009000-7e030000	Deferred        libexpat.so.1
ELF	7e030000-7e05d000	Deferred        libfontconfig.so.1
ELF	7e05d000-7e073000	Deferred        libz.so.1
ELF	7e073000-7e0e9000	Deferred        libfreetype.so.6
ELF	7e100000-7e114000	Deferred        lz32<elf>
  \-PE	7e110000-7e114000	\               lz32
ELF	7e114000-7e12f000	Deferred        version<elf>
  \-PE	7e120000-7e12f000	\               version
ELF	7e12f000-7e19c000	Deferred        setupapi<elf>
  \-PE	7e140000-7e19c000	\               setupapi
ELF	7e19c000-7e1d5000	Deferred        dinput<elf>
  \-PE	7e1a0000-7e1d5000	\               dinput
ELF	7e1d5000-7e1ef000	Deferred        dinput8<elf>
  \-PE	7e1e0000-7e1ef000	\               dinput8
ELF	7e1ef000-7e211000	Deferred        d3dx8<elf>
  \-PE	7e200000-7e211000	\               d3dx8
ELF	7e211000-7e232000	Deferred        d3dx9_36<elf>
  \-PE	7e220000-7e232000	\               d3dx9_36
ELF	7e232000-7e24c000	Deferred        d3dx9_35<elf>
  \-PE	7e240000-7e24c000	\               d3dx9_35
ELF	7e24c000-7e371000	Deferred        wined3d<elf>
  \-PE	7e260000-7e371000	\               wined3d
ELF	7e371000-7e3a3000	Deferred        d3d9<elf>
  \-PE	7e380000-7e3a3000	\               d3d9
ELF	7e3a3000-7e3b9000	Deferred        psapi<elf>
  \-PE	7e3b0000-7e3b9000	\               psapi
ELF	7e3b9000-7e407000	Deferred        dbghelp<elf>
  \-PE	7e3c0000-7e407000	\               dbghelp
ELF	7e407000-7e41d000	Deferred        powrprof<elf>
  \-PE	7e410000-7e41d000	\               powrprof
ELF	7e41d000-7e43e000	Deferred        imm32<elf>
  \-PE	7e420000-7e43e000	\               imm32
ELF	7e43e000-7e453000	Deferred        wtsapi32<elf>
  \-PE	7e440000-7e453000	\               wtsapi32
ELF	7e453000-7e4d5000	Deferred        crypt32<elf>
  \-PE	7e460000-7e4d5000	\               crypt32
ELF	7e4d5000-7e542000	Deferred        msvcrt<elf>
  \-PE	7e4f0000-7e542000	\               msvcrt
ELF	7e542000-7e629000	Deferred        oleaut32<elf>
  \-PE	7e560000-7e629000	\               oleaut32
ELF	7e629000-7e721000	Deferred        ole32<elf>
  \-PE	7e640000-7e721000	\               ole32
ELF	7e721000-7e757000	Deferred        winspool<elf>
  \-PE	7e730000-7e757000	\               winspool
ELF	7e757000-7e7b5000	Deferred        shlwapi<elf>
  \-PE	7e760000-7e7b5000	\               shlwapi
ELF	7e7b5000-7e942000	Deferred        shell32<elf>
  \-PE	7e7d0000-7e942000	\               shell32
ELF	7e942000-7e9f3000	Deferred        comdlg32<elf>
  \-PE	7e950000-7e9f3000	\               comdlg32
ELF	7e9f3000-7ea87000	Deferred        winmm<elf>
  \-PE	7ea00000-7ea87000	\               winmm
ELF	7ea87000-7ea9b000	Deferred        libresolv.so.2
ELF	7ea9b000-7eaba000	Deferred        iphlpapi<elf>
  \-PE	7eaa0000-7eaba000	\               iphlpapi
ELF	7eaba000-7eae7000	Deferred        ws2_32<elf>
  \-PE	7eac0000-7eae7000	\               ws2_32
ELF	7eae7000-7eb02000	Deferred        wsock32<elf>
  \-PE	7eaf0000-7eb02000	\               wsock32
ELF	7eb02000-7eba3000	Deferred        gdi32<elf>
  \-PE	7eb10000-7eba3000	\               gdi32
ELF	7eba3000-7ecef000	Deferred        user32<elf>
  \-PE	7ebc0000-7ecef000	\               user32
ELF	7ecef000-7edb7000	Deferred        comctl32<elf>
  \-PE	7ed00000-7edb7000	\               comctl32
ELF	7edb7000-7ee0c000	Deferred        advapi32<elf>
  \-PE	7edc0000-7ee0c000	\               advapi32
ELF	7ee0c000-7ee73000	Deferred        rpcrt4<elf>
  \-PE	7ee20000-7ee73000	\               rpcrt4
ELF	7ef93000-7ef9f000	Deferred        libnss_files.so.2
ELF	7ef9f000-7efaa000	Deferred        libnss_nis.so.2
ELF	7efaa000-7efc3000	Deferred        libnsl.so.1
ELF	7efc3000-7efe9000	Deferred        libm.so.6
ELF	7efe9000-7efeb000	Deferred        libnvidia-tls.so.1
ELF	7efeb000-7f000000	Deferred        faultrep<elf>
  \-PE	7eff0000-7f000000	\               faultrep
ELF	f7c66000-f7c6f000	Deferred        libnss_compat.so.2
ELF	f7c70000-f7c74000	Deferred        libdl.so.2
ELF	f7c74000-f7dd2000	Deferred        libc.so.6
ELF	f7dd3000-f7dec000	Deferred        libpthread.so.0
ELF	f7e03000-f7f3e000	Export          libwine.so.1
ELF	f7f40000-f7f60000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\pacman\.the_last_remnant\Binaries\TLR.exe
	0000000f    0
	00000009    0 <==
0000000c 
	0000000e    0
	0000000d    0
Backtrace:
=>0 0x11a2c5c7 in tlr (+0x112c5c7) (0x0052fe78)
  1 0x11a28b1e in tlr (+0x1128b1e) (0x0052ff08)
  2 0x7b878200 in kernel32 (+0x58200) (0x0052ffe8)
  3 0xf7e0add7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
```

i can program in a multitude of languages so i dont mind going through some source code.
but i need some help here, as i havent done anything for wine ever, and dont know where to start.

any help would be awesome!
thanks for the time.

---

### Post by tyle on 2009-03-27
> **waltons_pacman said:**
> 
any help would be awesome!


Well, seeing that you get fixme:s for powrprof and faultrep about unimplemented and stubbed functions, it is possible that you could get more info by turning on the powerprof and faultrep debug channels.

These fixme:s could of course be totally unrelated to the crash, but it is worth a shot. See [http://wiki.winehq.org/DebugChannels](http://wiki.winehq.org/DebugChannels) for a full list of Wine debug channels.

Winehq has some help on debugging: [http://www.winehq.org/docs/winedev-guide/wine-debugger](http://www.winehq.org/docs/winedev-guide/wine-debugger).

If you get stuck, you can file a bug on Wine Bugzilla with your findings.

Good luck in your debugging!

---

### Post by waltons_pacman on 2009-03-30
thanks for the post!

so my roomate brought up a good point tho.
are there any games working under wine with the unreal engine?
b/c my lone little efforts will def not be enough to get that going.

---

### Post by tyle on 2009-03-30
> **waltons_pacman said:**
> 
are there any games working under wine with the unreal engine?

Appdb is a good place to start.
[http://appdb.winehq.org](http://appdb.winehq.org)
Search for whatever application you are interested in, and you will see if anyone has tested it before, and how well it works.

EDIT: Apparently there even was an entry for the game you asked about.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15997](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15997)

---

