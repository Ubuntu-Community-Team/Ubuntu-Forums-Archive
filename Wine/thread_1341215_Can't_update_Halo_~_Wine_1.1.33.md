---
title: "Can't update Halo ~ Wine 1.1.33"
date: 2009-11-29
forum: Wine
---

### Post by Dark Aspect on 2009-11-29
I can't update Halo via haloupdate.exe, I tried to download halopc108patch.exe manually and install it but I have the same error.

[IMG]http://ubuntuforums.org/picture.php?albumid=1514&pictureid=5238[/IMG]

Ideas? I tried a few things with winetricks.

Here is the output:

```
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
wine: Unhandled page fault on read access to 0x00000000 at address 0x7b84c3e4 (thread 0032), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7b84c3e4).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b84c3e4 ESP:0033f14c EBP:0033f174 EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000000 EBX:7b8b5ff4 ECX:00000001 EDX:00000001
 ESI:00157186 EDI:0033f434
Stack dump:
0x0033f14c:  f74e216b 0033f264 7bc4a080 7bc6028a
0x0033f15c:  7bc96ff4 00000001 00000002 7b8b5ff4
0x0033f16c:  00157186 0033f434 0033f3d4 7b84c491
0x0033f17c:  0033f428 f778bff4 f778bff4 7bc6000d
0x0033f18c:  7bc49259 00000001 7b8bf950 00000001
0x0033f19c:  001403ba 00000001 00110058 00110000
Backtrace:
=>0 0x7b84c3e4 in kernel32 (+0x2c3e4) (0x0033f174)
  1 0x7b84c491 in kernel32 (+0x2c491) (0x0033f3d4)
  2 0x7b84d1db FormatMessageW+0x49b() in kernel32 (0x0033f444)
  3 0x00408b74 in haloupdate (+0x8b74) (0x00000000)
0x7b84c3e4: movl	0xfffffffc(%eax,%edx,4),%eax
Modules:
Module	Address			Debug info	Name (115 modules)
PE	  400000-  43a000	Export          haloupdate
PE	10000000-1003a000	Deferred        patchw32
PE	3f800000-3f912000	Deferred        strings
ELF	7b800000-7b973000	Export          kernel32<elf>
  \-PE	7b820000-7b973000	\               kernel32
ELF	7bc00000-7bcb3000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7daf4000-7db28000	Deferred        uxtheme<elf>
  \-PE	7db00000-7db28000	\               uxtheme
ELF	7db28000-7db2d000	Deferred        libgpg-error.so.0
ELF	7db2d000-7dba9000	Deferred        libgcrypt.so.11
ELF	7dba9000-7dbbb000	Deferred        libtasn1.so.3
ELF	7dbbb000-7dbc4000	Deferred        libkrb5support.so.0
ELF	7dbc4000-7dbef000	Deferred        libk5crypto.so.3
ELF	7dbef000-7dca1000	Deferred        libkrb5.so.3
ELF	7dca1000-7dcb2000	Deferred        libavahi-client.so.3
ELF	7dcb2000-7dcbe000	Deferred        libavahi-common.so.3
ELF	7dcbe000-7dd66000	Deferred        libgnutls.so.26
ELF	7dd66000-7dd93000	Deferred        libgssapi_krb5.so.2
ELF	7dd93000-7ddd8000	Deferred        libcups.so.2
ELF	7ddf9000-7de0e000	Deferred        midimap<elf>
  \-PE	7de00000-7de0e000	\               midimap
ELF	7de0e000-7de34000	Deferred        msacm32<elf>
  \-PE	7de10000-7de34000	\               msacm32
ELF	7de34000-7de3b000	Deferred        libogg.so.0
ELF	7de3b000-7de66000	Deferred        libvorbis.so.0
ELF	7de66000-7df60000	Deferred        libvorbisenc.so.2
ELF	7df60000-7dfb0000	Deferred        libflac.so.8
ELF	7dfb0000-7dfe9000	Deferred        libdbus-1.so.3
ELF	7dfe9000-7e055000	Deferred        libsndfile.so.1
ELF	7e055000-7e05e000	Deferred        libwrap.so.0
ELF	7e05e000-7e064000	Deferred        libxtst.so.6
ELF	7e064000-7e0ae000	Deferred        libpulsecommon-0.9.19.so
ELF	7e0ae000-7e0ee000	Deferred        libpulse.so.0
ELF	7e0f1000-7e0fa000	Deferred        librt.so.1
ELF	7e0fa000-7e1c2000	Deferred        libasound.so.2
ELF	7e1c2000-7e1fa000	Deferred        winealsa<elf>
  \-PE	7e1d0000-7e1fa000	\               winealsa
ELF	7e1fa000-7e205000	Deferred        libxcursor.so.1
ELF	7e205000-7e20b000	Deferred        libxfixes.so.3
ELF	7e20b000-7e20f000	Deferred        libxcomposite.so.1
ELF	7e20f000-7e218000	Deferred        libxrandr.so.2
ELF	7e218000-7e222000	Deferred        libxrender.so.1
ELF	7e222000-7e228000	Deferred        libxxf86vm.so.1
ELF	7e228000-7e22b000	Deferred        libxinerama.so.1
ELF	7e22b000-7e24c000	Deferred        imm32<elf>
  \-PE	7e230000-7e24c000	\               imm32
ELF	7e24c000-7e251000	Deferred        libxdmcp.so.6
ELF	7e251000-7e26f000	Deferred        libxcb.so.1
ELF	7e26f000-7e274000	Deferred        libuuid.so.1
ELF	7e274000-7e3a3000	Deferred        libx11.so.6
ELF	7e3a3000-7e3b3000	Deferred        libxext.so.6
ELF	7e3b3000-7e3ce000	Deferred        libice.so.6
ELF	7e3ce000-7e3d7000	Deferred        libsm.so.6
ELF	7e3d8000-7e3dc000	Deferred        libkeyutils.so.1
ELF	7e3dc000-7e3e0000	Deferred        libcom_err.so.2
ELF	7e3e0000-7e3f8000	Deferred        msacm32<elf>
  \-PE	7e3f0000-7e3f8000	\               msacm32
ELF	7e3f8000-7e498000	Deferred        winex11<elf>
  \-PE	7e410000-7e498000	\               winex11
ELF	7e498000-7e4bf000	Deferred        libexpat.so.1
ELF	7e4bf000-7e4ec000	Deferred        libfontconfig.so.1
ELF	7e4ec000-7e56b000	Deferred        libfreetype.so.6
ELF	7e58c000-7e5a0000	Deferred        libresolv.so.2
ELF	7e5a0000-7e5a4000	Deferred        libxau.so.6
ELF	7e5ac000-7e5c1000	Deferred        system.drv16.so
PE	7e5b0000-7e5c1000	Deferred        system.drv16
ELF	7e5c1000-7e5e1000	Deferred        iphlpapi<elf>
  \-PE	7e5d0000-7e5e1000	\               iphlpapi
ELF	7e5e1000-7e60b000	Deferred        ws2_32<elf>
  \-PE	7e5f0000-7e60b000	\               ws2_32
ELF	7e60b000-7e6db000	Deferred        comctl32<elf>
  \-PE	7e610000-7e6db000	\               comctl32
ELF	7e6db000-7e86b000	Deferred        shell32<elf>
  \-PE	7e6f0000-7e86b000	\               shell32
ELF	7e86b000-7e8c9000	Deferred        shlwapi<elf>
  \-PE	7e880000-7e8c9000	\               shlwapi
ELF	7e8c9000-7e8ec000	Deferred        mpr<elf>
  \-PE	7e8d0000-7e8ec000	\               mpr
ELF	7e8ec000-7e902000	Deferred        libz.so.1
ELF	7e908000-7e923000	Deferred        wsock32<elf>
  \-PE	7e910000-7e923000	\               wsock32
ELF	7e923000-7e97a000	Deferred        wininet<elf>
  \-PE	7e930000-7e97a000	\               wininet
ELF	7e97a000-7e9ae000	Deferred        winspool<elf>
  \-PE	7e980000-7e9ae000	\               winspool
ELF	7e9ae000-7ea06000	Deferred        setupapi<elf>
  \-PE	7e9c0000-7ea06000	\               setupapi
ELF	7ea06000-7ea1a000	Deferred        lz32<elf>
  \-PE	7ea10000-7ea1a000	\               lz32
ELF	7ea1a000-7ea88000	Deferred        rpcrt4<elf>
  \-PE	7ea30000-7ea88000	\               rpcrt4
ELF	7ea88000-7eb84000	Deferred        ole32<elf>
  \-PE	7eaa0000-7eb84000	\               ole32
ELF	7eb84000-7ebdd000	Deferred        advapi32<elf>
  \-PE	7eb90000-7ebdd000	\               advapi32
ELF	7ebdd000-7ec7d000	Deferred        gdi32<elf>
  \-PE	7ebf0000-7ec7d000	\               gdi32
ELF	7ec7d000-7edc6000	Deferred        user32<elf>
  \-PE	7eca0000-7edc6000	\               user32
ELF	7edc6000-7ee4d000	Deferred        winmm<elf>
  \-PE	7edd0000-7ee4d000	\               winmm
ELF	7ee4d000-7ee59000	Deferred        libnss_files.so.2
ELF	7ee59000-7ee64000	Deferred        libnss_nis.so.2
ELF	7ee64000-7ee6c000	Deferred        libnss_compat.so.2
ELF	7ee73000-7ee8d000	Deferred        version<elf>
  \-PE	7ee80000-7ee8d000	\               version
ELF	7efb9000-7efdf000	Deferred        libm.so.6
ELF	7efe9000-7f000000	Deferred        libnsl.so.1
ELF	f74e1000-f74e5000	Deferred        libdl.so.2
ELF	f74e5000-f7629000	Deferred        libc.so.6
ELF	f762a000-f7643000	Deferred        libpthread.so.0
ELF	f7664000-f77a0000	Deferred        libwine.so.1
ELF	f77a2000-f77c0000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e 
	0000001b    0
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000018 
	0000001c    0
	0000001a    0
	00000019    0
0000001d 
	0000001e    0
00000031 (D) C:\Program Files\Microsoft Games\Halo\haloupdate.exe
	00000032    0 <==
Backtrace:
=>0 0x7b84c3e4 in kernel32 (+0x2c3e4) (0x0033f174)
  1 0x7b84c491 in kernel32 (+0x2c491) (0x0033f3d4)
  2 0x7b84d1db FormatMessageW+0x49b() in kernel32 (0x0033f444)
  3 0x00408b74 in haloupdate (+0x8b74) (0x00000000)
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7b84c3e4

```

---

### Post by Dark Aspect on 2009-11-29
Regression - If anyone has the same error download Wine 1.1.32 and let the system update you back.

[Wine archive for Debian]("http://wine.budgetdedicated.com/archive/index.html")

---

### Post by sombertattoo on 2009-12-03
Perfect! Works now and just exactly what I needed

Thanks!

---

### Post by rocky5051 on 2009-12-04
Or you could extract the files from the patcher that replace the old ones and drop them in Halo's folder. That way you wouldn't have to drop back to 1.1.32

---

