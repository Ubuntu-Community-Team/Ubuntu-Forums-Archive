---
title: "Photomatix 3.2.3 works only on 1 of my two computers"
date: 2009-09-19
forum: Wine
---

### Post by boazarad on 2009-09-19
I've got two computers - one laptop and one desktop, both running 64bit Ubuntu 9.04, both with the exact same kernel version.

On my laptop, I installed wine (1.0.1 from the ubuntu repositories), downloaded winetricks, installed corefonts and dotnet20 - then installed photomatix. everything ran perfectly. 

My desktop, simply refuses to run Photomatix via wine.
After suspecting a previously installed program or hack under wine might be interfering, I uninstalled wine completely, deleted the configuration files and the .wine directory in my home folder.
I repeated the same steps as on my laptop - to no avail.
I tried the same thing with the latest version of wine (1.1.29), with the same results.

Here is the console output for wine on my desktop:
```
#wine PhotomatixPro.exe 
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:ole:CoGetContextToken stub
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"PhotomatixMisc"
fixme:shell:URL_ParseUrl failed to parse L"PhotomatixImaging"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shell:URL_ParseUrl failed to parse L"Accessibility"
fixme:shell:URL_ParseUrl failed to parse L"Photomatix.resources"
fixme:shell:URL_ParseUrl failed to parse L"Photomatix.resources"
fixme:win:EnumDisplayDevicesW ((null),0,0x32d028,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d028,0x00000000), stub!
fixme:advapi:CheckTokenMembership (0x1c8 0x16e370 0x32c8d0) stub!

Unhandled Exception: System.AccessViolationException: Attempted to read or write protected memory. This is often an indication that other memory is corrupt.
   at System.Drawing.SafeNativeMethods.Gdip.GdipCreateFontFromLogfontW(HandleRef hdc, Object lf, IntPtr& font)
   at System.Drawing.Font.FromLogFont(Object lf, IntPtr hdc)
   at System.Drawing.Font.FromHfont(IntPtr hfont)
   at System.Drawing.SystemFonts.get_DefaultFont()
   at System.Windows.Forms.Control.get_Font()
   at System.Windows.Forms.Control.set_Font(Font value)
   at Photomatix.Forms.xf266856f631ec016.x85601834555fb7d5()
   at Photomatix.Forms.xf266856f631ec016..ctor()
   at Photomatix.Forms.xf266856f631ec016..ctor(String[] args)
   at Photomatix.Forms.xf266856f631ec016.xc447809891322395(String[] xce8d8c7e3c2c2426)
wine: Unhandled page fault on read access to 0x00000048 at address 0x70d37550 (thread 002e), starting debugger...
Unhandled exception: page fault on read access to 0x00000048 in 32-bit code (0x70d37550).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:70d37550 ESP:0032d854 EBP:0032d864 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00110000 EBX:0416efa8 ECX:00000048 EDX:00000011
 ESI:0416f0bc EDI:00000000
Stack dump:
0x0032d854:  0416f178 0416f0bc 00110000 0416ef60
0x0032d864:  0032d884 70de75be 00110000 0032d87c
0x0032d874:  000001ca 0416f028 00110002 0000000e
0x0032d884:  0032d8b0 70d7bbae 000001ca 0416ef60
0x0032d894:  0416f286 00000000 0416ee68 00000005
0x0032d8a4:  0416f02c 00000000 00000007 0032d8ec
Backtrace:
=>1 0x70d37550 in gdiplus (+0x37550) (0x0032d864)
  2 0x70de75be in gdiplus (+0xe75be) (0x0032d884)
  3 0x70d7bbae in gdiplus (+0x7bbae) (0x0032d8b0)
  4 0x70d37ee2 in gdiplus (+0x37ee2) (0x0032d8ec)
  5 0x70d3822d in gdiplus (+0x3822d) (0x0032d90c)
  6 0x70d391b7 in gdiplus (+0x391b7) (0x0032da40)
  7 0x70db6205 in gdiplus (+0xb6205) (0x0032dc5c)
  8 0x70db6404 in gdiplus (+0xb6404) (0x0032e2b8)
  9 0x70d7524c in gdiplus (+0x7524c) (0x0032e304)
  10 0x7ec51ff4 in gdi32 (+0x71ff4) (0x41edb700)
  11 0x00000000 (0x00000000)
0x70d37550: movl	0x0(%edi,%ecx,1),%ecx
Modules:
Module	Address			Debug info	Name (79 modules)
PE	  400000-  782000	Deferred        photomatixpro
PE	 3ba0000- 3bd2000	Deferred        photomatiximaging
PE	10000000-10036000	Deferred        photomatixmisc
PE	5e380000-5e409000	Deferred        diasymreader
PE	60000000-60008000	Deferred        accessibility
PE	70d00000-70e91000	Export          gdiplus
PE	78130000-781cb000	Deferred        msvcr80
PE	79000000-79045000	Deferred        mscoree
PE	79060000-790b3000	Deferred        mscorjit
PE	790c0000-794de000	Deferred        mscorlib
PE	79e70000-7a3d1000	Deferred        mscorwks
PE	7a440000-7a724000	Deferred        system
PE	7ade0000-7ae8e000	Deferred        system.drawing
PE	7afd0000-7b4e6000	Deferred        system.windows.forms
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e062000-7e077000	Deferred        lz32<elf>
  \-PE	7e070000-7e077000	\               lz32
ELF	7e188000-7e24d000	Deferred        comctl32<elf>
  \-PE	7e190000-7e24d000	\               comctl32
ELF	7e24d000-7e362000	Deferred        shell32<elf>
  \-PE	7e260000-7e362000	\               shell32
ELF	7e3a8000-7e3c3000	Deferred        version<elf>
  \-PE	7e3b0000-7e3c3000	\               version
ELF	7e42a000-7e45d000	Deferred        uxtheme<elf>
  \-PE	7e430000-7e45d000	\               uxtheme
ELF	7e45d000-7e473000	Deferred        libresolv.so.2
ELF	7e48e000-7e4ad000	Deferred        iphlpapi<elf>
  \-PE	7e490000-7e4ad000	\               iphlpapi
ELF	7e4ad000-7e510000	Deferred        rpcrt4<elf>
  \-PE	7e4c0000-7e510000	\               rpcrt4
ELF	7e510000-7e5b6000	Deferred        ole32<elf>
  \-PE	7e520000-7e5b6000	\               ole32
ELF	7e7d8000-7e844000	Deferred        msvcrt<elf>
  \-PE	7e7f0000-7e844000	\               msvcrt
ELF	7e844000-7e84d000	Deferred        libxcursor.so.1
ELF	7e84d000-7e852000	Deferred        libxfixes.so.3
ELF	7e852000-7e856000	Deferred        libxcomposite.so.1
ELF	7e856000-7e85e000	Deferred        libxrandr.so.2
ELF	7e85e000-7e868000	Deferred        libxrender.so.1
ELF	7e868000-7e86b000	Deferred        libxinerama.so.1
ELF	7e86b000-7e88c000	Deferred        imm32<elf>
  \-PE	7e870000-7e88c000	\               imm32
ELF	7e88c000-7e891000	Deferred        libxdmcp.so.6
ELF	7e891000-7e8ab000	Deferred        libxcb.so.1
ELF	7e8ab000-7e8af000	Deferred        libxau.so.6
ELF	7e8af000-7e99e000	Deferred        libx11.so.6
ELF	7e99e000-7e9ae000	Deferred        libxext.so.6
ELF	7e9ae000-7e9b4000	Deferred        libxxf86vm.so.1
ELF	7e9b4000-7e9cc000	Deferred        libice.so.6
ELF	7e9cc000-7e9d5000	Deferred        libsm.so.6
ELF	7e9f0000-7ea8b000	Deferred        winex11<elf>
  \-PE	7ea00000-7ea8b000	\               winex11
ELF	7eae5000-7eb0c000	Deferred        libexpat.so.1
ELF	7eb0c000-7eb39000	Deferred        libfontconfig.so.1
ELF	7eb39000-7ebb0000	Deferred        libfreetype.so.6
ELF	7ebb0000-7ebb5000	Deferred        libuuid.so.1
ELF	7ebcb000-7ec6b000	Export          gdi32<elf>
  \-PE	7ebe0000-7ec6b000	\               gdi32
ELF	7ec6b000-7edb7000	Deferred        user32<elf>
  \-PE	7ec90000-7edb7000	\               user32
ELF	7edb7000-7ee12000	Deferred        shlwapi<elf>
  \-PE	7edc0000-7ee12000	\               shlwapi
ELF	7ee12000-7ee65000	Deferred        advapi32<elf>
  \-PE	7ee20000-7ee65000	\               advapi32
ELF	7ef8f000-7ef9b000	Deferred        libnss_files.so.2
ELF	7ef9b000-7efa6000	Deferred        libnss_nis.so.2
ELF	7efa6000-7efbf000	Deferred        libnsl.so.1
ELF	7efbf000-7efe5000	Deferred        libm.so.6
ELF	7efe6000-7effc000	Deferred        libz.so.1
ELF	f7cb5000-f7cb9000	Deferred        libdl.so.2
ELF	f7cb9000-f7e1c000	Deferred        libc.so.6
ELF	f7e1d000-f7e36000	Deferred        libpthread.so.0
ELF	f7e37000-f7e40000	Deferred        libnss_compat.so.2
ELF	f7e51000-f7f88000	Deferred        libwine.so.1
ELF	f7f8a000-f7fab000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	0000001b    0
	0000000e    0
	0000000d    0
00000018 
	0000001d    0
	0000001c    0
	0000001a    0
	00000019    0
0000001e 
	0000001f    0
00000026 
	0000002a    0
	00000029    2
	00000028    0
0000002d (D) C:\Program Files\PhotomatixPro3\PhotomatixPro.exe
	00000031    0
	00000030    2
	0000002f    0
	0000002e    0 <==
Backtrace:
=>1 0x70d37550 in gdiplus (+0x37550) (0x0032d864)
  2 0x70de75be in gdiplus (+0xe75be) (0x0032d884)
  3 0x70d7bbae in gdiplus (+0x7bbae) (0x0032d8b0)
  4 0x70d37ee2 in gdiplus (+0x37ee2) (0x0032d8ec)
  5 0x70d3822d in gdiplus (+0x3822d) (0x0032d90c)
  6 0x70d391b7 in gdiplus (+0x391b7) (0x0032da40)
  7 0x70db6205 in gdiplus (+0xb6205) (0x0032dc5c)
  8 0x70db6404 in gdiplus (+0xb6404) (0x0032e2b8)
  9 0x70d7524c in gdiplus (+0x7524c) (0x0032e304)
  10 0x7ec51ff4 in gdi32 (+0x71ff4) (0x41edb700)
  11 0x00000000 (0x00000000)

Unhandled Exception: System.AccessViolationException: Attempted to read or write protected memory. This is often an indication that other memory is corrupt.
   at System.Drawing.SafeNativeMethods.Gdip.GdipCreateFontFromLogfontW(HandleRef hdc, Object lf, IntPtr& font)
   at System.Drawing.Font.FromLogFont(Object lf, IntPtr hdc)
   at System.Drawing.Font.FromHfont(IntPtr hfont)
   at System.Drawing.SystemFonts.get_DefaultFont()
   at System.Windows.Forms.Control.get_Font()
   at System.Windows.Forms.Control.set_Font(Font value)
   at Photomatix.Forms.xf266856f631ec016.x85601834555fb7d5()
   at Photomatix.Forms.xf266856f631ec016..ctor()
   at Photomatix.Forms.xf266856f631ec016..ctor(String[] args)
   at Photomatix.Forms.xf266856f631ec016.xc447809891322395(String[] xce8d8c7e3c2c2426)
```

---

### Post by hikaricore on 2009-09-19
Have you tried simply copying your .wine folder from one system to the other?
This will rule out the possibility that WINE is the cause of the issue.
I suspect it is something else such as your video card or audio hardware, but this is just a guess.

---

