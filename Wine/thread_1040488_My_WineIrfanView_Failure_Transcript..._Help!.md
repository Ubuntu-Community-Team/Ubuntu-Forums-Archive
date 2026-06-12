---
title: "My Wine/IrfanView Failure Transcript... Help!"
date: 2009-01-15
forum: Wine
---

### Post by jaschaveruschka on 2009-01-15
I'm using Ubuntu 8.10 (also Windows XP as dual boot) on a Dell Inspiron 1000.
I installed Wine 1.0.1 using Add/Remove Applications.
I downloaded the current Irfanview install files (IrfanView plus Plugins) and copied them into Wine's Program Files folder.
I copied mfc42.dll from Windows into Wine's Program Files folder, following a suggestion from the web; on previous attempts I failed to get the IrfanView installation dialog to open.
[B]Terminal session:

[email]jason@3Jane:~/.wine[/email]/dosdevices/c:/Program Files/IrfanView$ cd "/home/jason/.wine/dosdevices/c:/Program Files"
[email]jason@3Jane:~/.wine[/email]/dosdevices/c:/Program Files$ ls
Common Files  Internet Explorer  IrfanView  irfanview_plugins_422_setup.exe  iview423_setup.exe  mfc42.dll
[email]jason@3Jane:~/.wine[/email]/dosdevices/c:/Program Files$ wine iview423_setup.exe
fixme:advapi:CheckTokenMembership ((nil) 0x1258b0 0x32f31c) stub!
fixme:system:SystemParametersInfoW Unimplemented action: 88 (SPI_SETICONS)

The IrfanView installation dialog opened despite these messages: deselected shortcuts options, selected none for file associations, deselected toolbars, hoping this would avoid conflicts.  Chose C:\Program Files\IrfanView, and INI file in IrfanView folder.  Deselected "Open IrfanView".  IrfanView dialog closed.
Terminal session:

[email]jason@3Jane:~/.wine[/email]/dosdevices/c:/Program Files$ ls
Common Files  Internet Explorer  IrfanView  irfanview_plugins_422_setup.exe  iview423_setup.exe  mfc42.dll
[email]jason@3Jane:~/.wine[/email]/dosdevices/c:/Program Files$ cd IrfanView
[email]jason@3Jane:~/.wine[/email]/dosdevices/c:/Program Files/IrfanView$ ls
Html         i_changes.txt    i_options.txt  i_view32.chm  i_view32.ini      Languages  Plugins
i_about.txt  i_languages.txt  i_plugins.txt  i_view32.exe  iv_uninstall.exe  mfc42.dll  Toolbars
[email]jason@3Jane:~/.wine[/email]/dosdevices/c:/Program Files/IrfanView$ wine i_view32.exe
wine: Unhandled page fault on read access to 0x00000390 at address 0x7ebdfcf3 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000390 in 32-bit code (0x7ebdfcf3).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ebdfcf3 ESP:0032e2c0 EBP:0032e2e8 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00132a20 EBX:7ec09ff4 ECX:00e6e6e6 EDX:00000388
 ESI:00000000 EDI:00000384
Stack dump:
0x0032e2c0:  00000384 0000ffff 000004b8 00000017
0x0032e2d0:  00000060 0011f780 0011f780 7ee20ff4
0x0032e2e0:  7ecba330 00134610 0032e368 7eda445a
0x0032e2f0:  00000384 00000018 0032e344 00000010
0x0032e300:  00000010 00000448 00000020 00000040
0x0032e310:  00220326 7ee20ff4 000004a0 00134610
Backtrace:
=>1 0x7ebdfcf3 GetObjectW+0x43() in gdi32 (0x0032e2e8)
  2 0x7eda445a ImageList_AddMasked+0xaa() in comctl32 (0x0032e368)
  3 0x00460997 in i_view32 (+0x60997) (0x00000378)
  4 0x00000000 (0x00000000)
0x7ebdfcf3 GetObjectW+0x43 in gdi32: movl	0x8(%edx),%edx
Modules:
Module	Address			Debug info	Name (76 modules)
PE	  400000-  542000	Export          i_view32
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e1a5000-7e20e000	Deferred        libgcrypt.so.11
ELF	7e20e000-7e220000	Deferred        libtasn1.so.3
ELF	7e220000-7e229000	Deferred        libkrb5support.so.0
ELF	7e229000-7e25b000	Deferred        libcrypt.so.1
ELF	7e25b000-7e2f8000	Deferred        libgnutls.so.26
ELF	7e2f8000-7e31c000	Deferred        libk5crypto.so.3
ELF	7e31c000-7e3ae000	Deferred        libkrb5.so.3
ELF	7e3ae000-7e3d8000	Deferred        libgssapi_krb5.so.2
ELF	7e3d8000-7e40e000	Deferred        libcups.so.2
ELF	7e471000-7e4a4000	Deferred        uxtheme<elf>
  \-PE	7e480000-7e4a4000	\               uxtheme
ELF	7e4a4000-7e4ad000	Deferred        libxcursor.so.1
ELF	7e4ad000-7e4b2000	Deferred        libxfixes.so.3
ELF	7e4b2000-7e4b6000	Deferred        libxcomposite.so.1
ELF	7e4b6000-7e4bd000	Deferred        libxrandr.so.2
ELF	7e4bd000-7e4c7000	Deferred        libxrender.so.1
ELF	7e4c7000-7e4ca000	Deferred        libxinerama.so.1
ELF	7e4ca000-7e4eb000	Deferred        imm32<elf>
  \-PE	7e4d0000-7e4eb000	\               imm32
ELF	7e4eb000-7e4f0000	Deferred        libxdmcp.so.6
ELF	7e4f0000-7e509000	Deferred        libxcb.so.1
ELF	7e509000-7e50c000	Deferred        libxcb-xlib.so.0
ELF	7e50c000-7e50f000	Deferred        libxau.so.6
ELF	7e50f000-7e5fe000	Deferred        libx11.so.6
ELF	7e5fe000-7e60d000	Deferred        libxext.so.6
ELF	7e60d000-7e613000	Deferred        libxxf86vm.so.1
ELF	7e613000-7e62b000	Deferred        libice.so.6
ELF	7e62b000-7e634000	Deferred        libsm.so.6
ELF	7e634000-7e638000	Deferred        libgpg-error.so.0
ELF	7e638000-7e63c000	Deferred        libkeyutils.so.1
ELF	7e63c000-7e640000	Deferred        libcom_err.so.2
ELF	7e642000-7e6dd000	Deferred        winex11<elf>
  \-PE	7e650000-7e6dd000	\               winex11
ELF	7e706000-7e72d000	Deferred        libexpat.so.1
ELF	7e72d000-7e75a000	Deferred        libfontconfig.so.1
ELF	7e75a000-7e770000	Deferred        libz.so.1
ELF	7e770000-7e7e6000	Deferred        libfreetype.so.6
ELF	7e7e6000-7e7fa000	Deferred        libresolv.so.2
ELF	7e808000-7e827000	Deferred        iphlpapi<elf>
  \-PE	7e810000-7e827000	\               iphlpapi
ELF	7e827000-7e88a000	Deferred        rpcrt4<elf>
  \-PE	7e830000-7e88a000	\               rpcrt4
ELF	7e88a000-7e930000	Deferred        ole32<elf>
  \-PE	7e8a0000-7e930000	\               ole32
ELF	7e930000-7e967000	Deferred        winspool<elf>
  \-PE	7e940000-7e967000	\               winspool
ELF	7e967000-7e9c2000	Deferred        shlwapi<elf>
  \-PE	7e970000-7e9c2000	\               shlwapi
ELF	7e9c2000-7ead6000	Deferred        shell32<elf>
  \-PE	7e9d0000-7ead6000	\               shell32
ELF	7ead6000-7eb84000	Deferred        comdlg32<elf>
  \-PE	7eae0000-7eb84000	\               comdlg32
ELF	7eb84000-7ec23000	Export          gdi32<elf>
  \-PE	7eb90000-7ec23000	\               gdi32
ELF	7ec23000-7ed6f000	Deferred        user32<elf>
  \-PE	7ec40000-7ed6f000	\               user32
ELF	7ed6f000-7ee34000	Export          comctl32<elf>
  \-PE	7ed80000-7ee34000	\               comctl32
ELF	7ee34000-7ee87000	Deferred        advapi32<elf>
  \-PE	7ee40000-7ee87000	\               advapi32
ELF	7efa7000-7efb3000	Deferred        libnss_files.so.2
ELF	7efb3000-7efcc000	Deferred        libnsl.so.1
ELF	7efcc000-7eff2000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d96000-b7d9f000	Deferred        libnss_compat.so.2
ELF	b7da0000-b7da4000	Deferred        libdl.so.2
ELF	b7da4000-b7f02000	Deferred        libc.so.6
ELF	b7f03000-b7f1c000	Deferred        libpthread.so.0
ELF	b7f2a000-b8061000	Deferred        libwine.so.1
ELF	b8063000-b8080000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\IrfanView\i_view32.exe
	00000009    0 <==
0000000c 
	00000013    0
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
=>1 0x7ebdfcf3 GetObjectW+0x43() in gdi32 (0x0032e2e8)
  2 0x7eda445a ImageList_AddMasked+0xaa() in comctl32 (0x0032e368)
  3 0x00460997 in i_view32 (+0x60997) (0x00000378)
  4 0x00000000 (0x00000000)
err:syslevel:_CheckNotSysLevel Holding lock 0x7ec11ee0 level 3
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed349e0, level 2): Holding 0x7ec11ee0, level 3. Expect deadlock!

That's all I've got and it is gibberish to me.

You countless people are my only hopes!

Jason

---

### Post by xzero1 on 2009-01-16
I could not get the wine Linux version working either but wine can run the windows version! Just run the installed windows Irfanview executable with wine. There could be issues since this is not usually done, but so far it has worked for me.

---

