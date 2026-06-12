---
title: "gdiplus.dll.GdipDrawImageFX"
date: 2009-03-04
forum: Wine
---

### Post by abds on 2009-03-04
I am trying to run Geometers Sketchpad using wine. It loads fine. However it crashes if I try to do anything. Any help would be greatly appreciated. Here is the trace:

fixme:win:LockWindowUpdate (0x10020), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:gdiplus:GdipGetDC (0x15f910, 0x32fa98): stub
fixme:gdiplus:GdipReleaseDC (0x15f910, (nil)): stub
fixme:gdiplus:GdipGetDC (0x166740, 0x32b700): stub
fixme:gdiplus:GdipReleaseDC (0x166740, (nil)): stub
fixme:gdiplus:GdipGetDC (0x162650, 0x32b96c): stub
fixme:gdiplus:GdipReleaseDC (0x162650, (nil)): stub
fixme:gdiplus:GdipGetDC (0x166740, 0x32a7a0): stub
fixme:gdiplus:GdipReleaseDC (0x166740, (nil)): stub
fixme:gdiplus:GdipGetDC (0x166740, 0x32fcb8): stub
fixme:gdiplus:GdipReleaseDC (0x166740, (nil)): stub
fixme:gdiplus:GdipGetDC (0x166740, 0x32fbcc): stub
fixme:gdiplus:GdipReleaseDC (0x166740, (nil)): stub
wine: Call from 0x7b844c50 to unimplemented function gdiplus.dll.GdipDrawEllipse, aborting
wine: Unimplemented function gdiplus.dll.GdipDrawEllipse called at address 0x7b844c50 (thread 0009), starting debugger...
Unhandled exception: unimplemented function gdiplus.dll.GdipDrawEllipse called in 32-bit code (0x7b844cc6).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b844cc6 ESP:0032faf0 EBP:0032fb54 EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82eb09 EBX:7b8b3884 ECX:00000000 EDX:00728138
 ESI:00728138 EDI:00162820
Stack dump:
0x0032faf0:  0032fb7c 00000008 00538212 0000000a
0x0032fb00:  80000100 00000001 00000000 7b844c50
0x0032fb10:  00000002 7df48820 7df48f30 0032fb2c
0x0032fb20:  00000000 0032fb34 00000008 0010000f
0x0032fb30:  00538212 7df35774 00538018 7df30000
0x0032fb40:  0032fb80 004bdd77 7df30000 00538212
Backtrace:
=>1 0x7b844cc6 in kernel32 (+0x24cc6) (0x0032fb54)
  2 0x7df487c5 in gdiplus (+0x187c5) (0x0032fb84)
  3 0x7df35798 in gdiplus (+0x5798) (0x00741f48)
0x7b844cc6: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (82 modules)
PE	  400000-  605000	Deferred        gsp 4.06
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7df1e000-7df56000	Export          gdiplus<elf>
  \-PE	7df30000-7df56000	\               gdiplus
ELF	7e178000-7e17c000	Deferred        libgpg-error.so.0
ELF	7e17c000-7e1c9000	Deferred        libgcrypt.so.11
ELF	7e1c9000-7e1d9000	Deferred        libtasn1.so.3
ELF	7e1d9000-7e1e1000	Deferred        libkrb5support.so.0
ELF	7e1e1000-7e213000	Deferred        libcrypt.so.1
ELF	7e213000-7e288000	Deferred        libgnutls.so.13
ELF	7e288000-7e2ab000	Deferred        libk5crypto.so.3
ELF	7e2ab000-7e338000	Deferred        libkrb5.so.3
ELF	7e338000-7e361000	Deferred        libgssapi_krb5.so.2
ELF	7e361000-7e394000	Deferred        libcups.so.2
ELF	7e3f4000-7e427000	Deferred        uxtheme<elf>
  \-PE	7e400000-7e427000	\               uxtheme
ELF	7e427000-7e430000	Deferred        libxcursor.so.1
ELF	7e430000-7e435000	Deferred        libxfixes.so.3
ELF	7e435000-7e438000	Deferred        libxcomposite.so.1
ELF	7e438000-7e43e000	Deferred        libxrandr.so.2
ELF	7e43e000-7e446000	Deferred        libxrender.so.1
ELF	7e446000-7e449000	Deferred        libxinerama.so.1
ELF	7e449000-7e469000	Deferred        imm32<elf>
  \-PE	7e450000-7e469000	\               imm32
ELF	7e469000-7e46e000	Deferred        libxdmcp.so.6
ELF	7e46e000-7e486000	Deferred        libxcb.so.1
ELF	7e486000-7e488000	Deferred        libxcb-xlib.so.0
ELF	7e488000-7e48b000	Deferred        libxau.so.6
ELF	7e48b000-7e572000	Deferred        libx11.so.6
ELF	7e572000-7e580000	Deferred        libxext.so.6
ELF	7e580000-7e585000	Deferred        libxxf86vm.so.1
ELF	7e587000-7e58a000	Deferred        libkeyutils.so.1
ELF	7e594000-7e597000	Deferred        libcom_err.so.2
ELF	7e599000-7e630000	Deferred        winex11<elf>
  \-PE	7e5b0000-7e630000	\               winex11
ELF	7e64d000-7e66e000	Deferred        libexpat.so.1
ELF	7e66e000-7e698000	Deferred        libfontconfig.so.1
ELF	7e698000-7e6ad000	Deferred        libz.so.1
ELF	7e6ad000-7e71d000	Deferred        libfreetype.so.6
ELF	7e731000-7e7d3000	Deferred        oleaut32<elf>
  \-PE	7e740000-7e7d3000	\               oleaut32
ELF	7e7d3000-7e7e6000	Deferred        libresolv.so.2
ELF	7e7e7000-7e7fa000	Deferred        olepro32<elf>
  \-PE	7e7f0000-7e7fa000	\               olepro32
ELF	7e7fa000-7e818000	Deferred        iphlpapi<elf>
  \-PE	7e800000-7e818000	\               iphlpapi
ELF	7e818000-7e879000	Deferred        rpcrt4<elf>
  \-PE	7e820000-7e879000	\               rpcrt4
ELF	7e879000-7e91d000	Deferred        ole32<elf>
  \-PE	7e890000-7e91d000	\               ole32
ELF	7e91d000-7e944000	Deferred        oledlg<elf>
  \-PE	7e920000-7e944000	\               oledlg
ELF	7e944000-7e97a000	Deferred        winspool<elf>
  \-PE	7e950000-7e97a000	\               winspool
ELF	7e97a000-7ea39000	Deferred        comctl32<elf>
  \-PE	7e980000-7ea39000	\               comctl32
ELF	7ea39000-7ea92000	Deferred        shlwapi<elf>
  \-PE	7ea50000-7ea92000	\               shlwapi
ELF	7ea92000-7eba5000	Deferred        shell32<elf>
  \-PE	7eaa0000-7eba5000	\               shell32
ELF	7eba5000-7ec50000	Deferred        comdlg32<elf>
  \-PE	7ebb0000-7ec50000	\               comdlg32
ELF	7ec50000-7eca2000	Deferred        advapi32<elf>
  \-PE	7ec60000-7eca2000	\               advapi32
ELF	7eca2000-7ed3d000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed3d000	\               gdi32
ELF	7ed3d000-7ee84000	Deferred        user32<elf>
  \-PE	7ed60000-7ee84000	\               user32
ELF	7efa4000-7efaf000	Deferred        libnss_files.so.2
ELF	7efaf000-7efc7000	Deferred        libnsl.so.1
ELF	7efc7000-7efec000	Deferred        libm.so.6
ELF	7efed000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	f7cb8000-f7cbc000	Deferred        libdl.so.2
ELF	f7cbc000-f7e0b000	Deferred        libc.so.6
ELF	f7e0c000-f7e24000	Deferred        libpthread.so.0
ELF	f7e38000-f7f6e000	Deferred        libwine.so.1
ELF	f7f70000-f7f8f000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\abasit\Desktop\GSP 4.06.exe
	00000019    0
	00000018    0
	00000009    0 <==
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
Backtrace:
=>1 0x7b844cc6 in kernel32 (+0x24cc6) (0x0032fb54)
  2 0x7df487c5 in gdiplus (+0x187c5) (0x0032fb84)
  3 0x7df35798 in gdiplus (+0x5798) (0x00741f48)
wine: Call from 0x7b844c50 to unimplemented function gdiplus.dll.GdipDrawEllipseI, aborting
wine: Call from 0x7b844c50 to unimplemented function gdiplus.dll.GdipDrawImageFX, aborting

---

### Post by cogadh on 2009-03-04
Use [winetricks]("http://wiki.winehq.org/winetricks") to install a native gdiplus, it may correct the issue.

---

### Post by abds on 2009-03-04
It fixed the problem! Thanks a lot

---

