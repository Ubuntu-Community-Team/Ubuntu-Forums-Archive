---
title: "InkLearn won't work in Ubuntu/Wine"
date: 2009-01-18
forum: Wine
---

### Post by h2o4444 on 2009-01-18
InkLearn is a program for the tablet that allows you to write a Chinese character using the stylus and the program will tell you the pronunciation and the meaning of the character. It is very handy and a lot faster than looking up a Chinese character in the dictionary.

InkLearn, however, only works in Windows. It is installed after you download and unzip it. There is no installer, it works right away. I tried to run this application in Wine and nothing happens. I do not plan to run VirtualBox with Windows since it takes too much disk space (I only have 10 GB allocated to Ubuntu). This program is very useful to me since I am studying Chinese. I like Ubuntu very much but there are some things I don't like, such as my issue with InkLearn.

Can anyone help me? Or is there a similar program for Linux? I tried to look for it but found none. I tried appdb.winehq.org but nothing shows up for InkLearn either.

---

### Post by cogadh on 2009-01-18
Does anything tablet related actually work in Wine? The fact that this particular app doesn't even appear in AppDB is not a good sign at all. However, it might help if you were to provide a few more details, such as the terminal output from Wine.

---

### Post by h2o4444 on 2009-01-18
Since my computer was first an XP then added Ubuntu, I simply browse to the program files, or to the executable file in /host folder. Usually I just double click the .exe file. I've never used Wine in Terminal. I don't know if the way I'm using Wine is correct but it works for another program that only runs on Windows, NJStar.

How would I use Wine in Terminal? Would that make any difference?
Thanks!

---

### Post by cogadh on 2009-01-18
Running Wine from a terminal is as simple as opening a terminal, changing directories to where your app is installed and typing "wine foo.exe" (with "foo" being the actual name of the executable you are trying to run). It has one major advantage over double-clicking the executable, in that Wine will output its own error messages to the terminal window. Those error messages will almost always point to a reason for the problem and may actually provide a direction to follow for a solution.

---

### Post by h2o4444 on 2009-01-18
OK, after I did that in the Terminal I get:
> install the Windows version of Mono to run .NET executables
I tried to search for Mono in Synaptic but there are so many files with the mono prefix, which one should I install?
Thanks.
PS- Why can't Wine have an error message built in with the double click? Terminal is intimidating for newbies like me.

---

### Post by cogadh on 2009-01-19
None of the ones in Synaptic. You need to install the Windows version of Mono, or .NET itself, in Wine. It would probably be best to use [winetricks]("http://wiki.winehq.org/winetricks") to do that.

Wine is a terminal application, not a GUI application, hence why it doesn't produce its error messages when you double-click an EXE. If you want a GUI version of Wine, you might be better suited going with Wine's commercial version, [CrossOver]("http://www.codeweavers.com/"). Honestly, if you are going to use Linux, you really should get comfortable with using the terminal. At its heart, Linux is still a terminal/console OS, the GUI elements are just laid on top of it. The terminal itself is far more powerful than the GUI, in terms of the freedom it gives you to do whatever you want with the OS.

---

### Post by h2o4444 on 2009-01-19
I followed your link to winetricks and installed it. Then I installed "mono22" package (with the description of mono-2.2 as oppose to "mono20" with the description of mono-2.0.1). InkLearn did not work. Then I installed "dotnet20" package (with the description of MS .NET 2.0 as oppose to "dotnet11" with the description of MS .NET 1.1). InkLearn still did not work. I get the follow code in Terminal:

```
fixme:service:ChangeServiceConfig2W STUB: 0x129ed8 2 0x33fbbc
fixme:powrprof:DllMain (0x7e810000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime Optimization Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000450,(nil),0x0001,0x00000000,0x7e55e4e4,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"HanLib"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shell:URL_ParseUrl failed to parse L"Accessibility"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:win:EnumDisplayDevicesW ((null),0,0x32d708,0x00000000), stub!
fixme:advapi:CheckTokenMembership (0x1ac 0x157548 0x32dac8) stub!

Unhandled Exception: System.ArgumentException: Font '?' cannot be found.
   at System.Drawing.FontFamily.GetGdipGenericSansSerif()
   at System.Drawing.FontFamily.get_GenericSansSerif()
   at System.Drawing.SystemFonts.get_DefaultFont()
   at System.Windows.Forms.Control.get_Font()
   at System.Windows.Forms.Control.get_FontHeight()
   at System.Windows.Forms.TextBoxBase.get_PreferredHeight()
   at System.Windows.Forms.TextBoxBase.get_DefaultSize()
   at System.Windows.Forms.Control..ctor(Boolean autoInstallSyncContext)
   at System.Windows.Forms.TextBoxBase..ctor()
   at System.Windows.Forms.TextBox..ctor()
   at InkLearnApp.MainForm.InitializeComponent()
   at InkLearnApp.MainForm..ctor()
   at InkLearnApp.MainForm.Main(String[] args)
wine: Unhandled exception 0xe0434f4d at address 0x7b845450 (thread 0009), starting debugger...
Unhandled exception: 0xe0434f4d in 32-bit code (0x7b8454c3).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b8454c3 ESP:0032ea68 EBP:0032eacc EFLAGS:00000246(   - 00      - IZP1)
 EAX:7b82ecb9 EBX:7b8b7ff4 ECX:00000000 EDX:0032eb04
 ESI:0032eb04 EDI:e0434f4d
Stack dump:
0x0032ea68:  0032eb04 00000004 0000003c e0434f4d
0x0032ea78:  00000001 00000000 7b845450 00000001
0x0032ea88:  80070057 e0434f4d 0032eb04 00392010
0x0032ea98:  02000036 0032eab0 79e814da 0032eabc
0x0032eaa8:  02000036 00000001 0032eb2c 79e87ff4
0x0032eab8:  0000012c 003f161c 7b84545a 00133e68
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x0032eacc)
  2 0x79f97065 in mscorwks (+0x127065) (0x0032eb2c)
  3 0x7a0945a4 in mscorwks (+0x2245a4) (0x0032ebf0)
  4 0x037bf193 (0x0032ec38)
  5 0x0377fb72 (0x0032ecf0)
  6 0x0377f8f1 (0x0032f3c0)
  7 0x02d57157 (0x0032f3e0)
  8 0x79e88ee4 in mscorwks (+0x18ee4) (0x0032f460)
  9 0x79e88e31 in mscorwks (+0x18e31) (0x0032f598)
  10 0x79e88d19 in mscorwks (+0x18d19) (0x0032f66c)
  11 0x037261e8 (0x037206a8)
  12 0x00200174 (0x0900001f)
  13 0x00000000 (0x00000000)
0x7b8454c3: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (78 modules)
PE	  400000-  426000	Deferred        inklearn
PE	11000000-1100a000	Deferred        hanlib
PE	5e380000-5e409000	Deferred        diasymreader
PE	60000000-60008000	Deferred        accessibility
PE	70d00000-70e91000	Deferred        gdiplus
PE	78130000-781cb000	Deferred        msvcr80
PE	79000000-79045000	Deferred        mscoree
PE	79060000-790b3000	Deferred        mscorjit
PE	790c0000-794de000	Deferred        mscorlib
PE	79e70000-7a3d1000	Export          mscorwks
PE	7a440000-7a724000	Deferred        system
PE	7ade0000-7ae8e000	Deferred        system.drawing
PE	7afd0000-7b4e6000	Deferred        system.windows.forms
ELF	7b800000-7b93d000	Export          kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e106000-7e11b000	Deferred        lz32<elf>
  \-PE	7e110000-7e11b000	\               lz32
ELF	7e11b000-7e136000	Deferred        version<elf>
  \-PE	7e120000-7e136000	\               version
ELF	7e278000-7e2ab000	Deferred        uxtheme<elf>
  \-PE	7e280000-7e2ab000	\               uxtheme
ELF	7e2ab000-7e370000	Deferred        comctl32<elf>
  \-PE	7e2b0000-7e370000	\               comctl32
ELF	7e370000-7e484000	Deferred        shell32<elf>
  \-PE	7e380000-7e484000	\               shell32
ELF	7e497000-7e4ab000	Deferred        libresolv.so.2
ELF	7e4ab000-7e4ca000	Deferred        iphlpapi<elf>
  \-PE	7e4b0000-7e4ca000	\               iphlpapi
ELF	7e4ca000-7e52d000	Deferred        rpcrt4<elf>
  \-PE	7e4e0000-7e52d000	\               rpcrt4
ELF	7e52d000-7e5d3000	Deferred        ole32<elf>
  \-PE	7e540000-7e5d3000	\               ole32
ELF	7e7f5000-7e861000	Deferred        msvcrt<elf>
  \-PE	7e810000-7e861000	\               msvcrt
ELF	7e861000-7e86a000	Deferred        libxcursor.so.1
ELF	7e86a000-7e86f000	Deferred        libxfixes.so.3
ELF	7e86f000-7e873000	Deferred        libxcomposite.so.1
ELF	7e873000-7e87a000	Deferred        libxrandr.so.2
ELF	7e87a000-7e884000	Deferred        libxrender.so.1
ELF	7e884000-7e887000	Deferred        libxinerama.so.1
ELF	7e887000-7e8a8000	Deferred        imm32<elf>
  \-PE	7e890000-7e8a8000	\               imm32
ELF	7e8a8000-7e8ad000	Deferred        libxdmcp.so.6
ELF	7e8ad000-7e8c6000	Deferred        libxcb.so.1
ELF	7e8c6000-7e8c9000	Deferred        libxcb-xlib.so.0
ELF	7e8c9000-7e8cc000	Deferred        libxau.so.6
ELF	7e8cc000-7e9bb000	Deferred        libx11.so.6
ELF	7e9bb000-7e9ca000	Deferred        libxext.so.6
ELF	7e9ca000-7e9d0000	Deferred        libxxf86vm.so.1
ELF	7e9d0000-7e9e8000	Deferred        libice.so.6
ELF	7e9e8000-7e9f1000	Deferred        libsm.so.6
ELF	7ea08000-7eaa3000	Deferred        winex11<elf>
  \-PE	7ea20000-7eaa3000	\               winex11
ELF	7eada000-7eb01000	Deferred        libexpat.so.1
ELF	7eb01000-7eb2e000	Deferred        libfontconfig.so.1
ELF	7eb2e000-7eb44000	Deferred        libz.so.1
ELF	7eb44000-7ebba000	Deferred        libfreetype.so.6
ELF	7ebd1000-7ec70000	Deferred        gdi32<elf>
  \-PE	7ebe0000-7ec70000	\               gdi32
ELF	7ec70000-7edbc000	Deferred        user32<elf>
  \-PE	7ec90000-7edbc000	\               user32
ELF	7edbc000-7ee17000	Deferred        shlwapi<elf>
  \-PE	7edd0000-7ee17000	\               shlwapi
ELF	7ee17000-7ee6a000	Deferred        advapi32<elf>
  \-PE	7ee20000-7ee6a000	\               advapi32
ELF	7ef8a000-7ef96000	Deferred        libnss_files.so.2
ELF	7ef96000-7efa1000	Deferred        libnss_nis.so.2
ELF	7efa1000-7efba000	Deferred        libnsl.so.1
ELF	7efba000-7efc3000	Deferred        libnss_compat.so.2
ELF	7efc3000-7efe9000	Deferred        libm.so.6
ELF	b7c82000-b7c86000	Deferred        libdl.so.2
ELF	b7c86000-b7de4000	Deferred        libc.so.6
ELF	b7de5000-b7dfe000	Deferred        libpthread.so.0
ELF	b7e15000-b7f4c000	Deferred        libwine.so.1
ELF	b7f4e000-b7f6b000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\hiatt\Desktop\InkLearn_0_9_2\InkLearn.exe
	00000023    0
	00000022    2
	00000021    0
	00000009    0 <==
0000000c 
	0000001a    0
	0000000e    0
	0000000d    0
00000017 
	0000001c    0
	0000001b    0
	00000019    0
	00000018    0
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x0032eacc)
  2 0x79f97065 in mscorwks (+0x127065) (0x0032eb2c)
  3 0x7a0945a4 in mscorwks (+0x2245a4) (0x0032ebf0)
  4 0x037bf193 (0x0032ec38)
  5 0x0377fb72 (0x0032ecf0)
  6 0x0377f8f1 (0x0032f3c0)
  7 0x02d57157 (0x0032f3e0)
  8 0x79e88ee4 in mscorwks (+0x18ee4) (0x0032f460)
  9 0x79e88e31 in mscorwks (+0x18e31) (0x0032f598)
  10 0x79e88d19 in mscorwks (+0x18d19) (0x0032f66c)
  11 0x037261e8 (0x037206a8)
  12 0x00200174 (0x0900001f)
  13 0x00000000 (0x00000000)
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003ff,(nil),0x0001,0x00000000,0x32e5b0,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime version 2.0.50727.42 - Fatal Execution Engine Error (79F97075) (80131506)"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
```

Is there any hope?

---

### Post by dgrafix on 2009-01-19
Hang on, if its a mono executable you may find it will run natively under the linux version of mono. Mono is a jit (just-in-time (a bit like java)) compiler for C#. Designed to allow C# coded apps to run on windows/unix/linux/osx.

I think you need to apt-get mono and mono-common then just type "mono whatever.exe" from the terminal. As long as the app doesnt use directX or other win32 only bindings it should just run.

---

### Post by h2o4444 on 2009-01-19
I looked in Synaptic and "mono-common" is already installed. There is no package for "mono", not even using Terminal: "sudo apt-get mono".

I did the "mono InkLearn.exe" in Terminal and I got this message:

```
** (InkLearn.exe:8581): WARNING **: The following assembly referenced from /host/Documents and Settings/Administrator/My Documents/InkLearn_0_9_2/InkLearn.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=0)
     Version:    1.0.5000.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/host/Documents and Settings/Administrator/My Documents/InkLearn_0_9_2/).


** (InkLearn.exe:8581): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
The entry point method could not be loaded
```

I don't know what this means.

---

### Post by dgrafix on 2009-01-20
Well that makes more sense than the wine one.

That means that it uses the system.windows libraries i think these must be a win32 only part of mono (never used them myself and they are not available to autocomplete in monodevelop) so you may need to struggle on with wine after all :/
I hate it when mono programmers resort to using win only stuff, kinda defeats the whole idea of mono and they may as well use MS C#. As a programmer myself i tend to program on linux for everything else, that way you dont get these issues.

Ill see if i can find out anything for you.

---

### Post by h2o4444 on 2009-01-20
Thank you very much. I don't know how to program even though I've taken/dropped out of a computer class in college, which was the worst class I've ever taken. I will try to contact the author of InkLearn and see if he can help as well.

---

### Post by directhex on 2009-01-21
> **h2o4444 said:**
> I looked in Synaptic and "mono-common" is already installed. There is no package for "mono", not even using Terminal: "sudo apt-get mono".

I did the "mono InkLearn.exe" in Terminal and I got this message:

```
** (InkLearn.exe:8581): WARNING **: The following assembly referenced from /host/Documents and Settings/Administrator/My Documents/InkLearn_0_9_2/InkLearn.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=0)
     Version:    1.0.5000.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/host/Documents and Settings/Administrator/My Documents/InkLearn_0_9_2/).


** (InkLearn.exe:8581): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
The entry point method could not be loaded
```

I don't know what this means.

libmono-winforms1.0-cil

---

### Post by h2o4444 on 2009-01-22
I installed "libmono-winforms1.0-cil" in Synaptics and run "wine InkLearn.exe" in the Terminal and this is what I got:

```
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"HanLib"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shell:URL_ParseUrl failed to parse L"Accessibility"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:win:EnumDisplayDevicesW ((null),0,0x32d708,0x00000000), stub!
fixme:advapi:CheckTokenMembership (0x1c8 0x142d80 0x32cfbc) stub!

Unhandled Exception: System.AccessViolationException: Attempted to read or write protected memory. This is often an indication that other memory is corrupt.
   at System.Drawing.SafeNativeMethods.Gdip.GdipCreateFontFromLogfontW(HandleRef hdc, Object lf, IntPtr& font)
   at System.Drawing.Font.FromLogFont(Object lf, IntPtr hdc)
   at System.Drawing.Font.FromHfont(IntPtr hfont)
   at System.Drawing.SystemFonts.get_DefaultFont()
   at System.Windows.Forms.Control.get_Font()
   at System.Windows.Forms.Control.get_FontHeight()
   at System.Windows.Forms.TextBoxBase.get_PreferredHeight()
   at System.Windows.Forms.TextBoxBase.get_DefaultSize()
   at System.Windows.Forms.Control..ctor(Boolean autoInstallSyncContext)
   at System.Windows.Forms.TextBoxBase..ctor()
   at System.Windows.Forms.TextBox..ctor()
   at InkLearnApp.MainForm.InitializeComponent()
   at InkLearnApp.MainForm..ctor()
   at InkLearnApp.MainForm.Main(String[] args)
wine: Unhandled page fault on read access to 0x00000021 at address 0x70d37550 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000021 in 32-bit code (0x70d37550).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:70d37550 ESP:0032df40 EBP:0032df50 EFLAGS:00010256(   - 00      RIZAP1)
 EAX:00110000 EBX:03ea1ad0 ECX:00000021 EDX:00000011
 ESI:03ea5abc EDI:00000000
Stack dump:
0x0032df40:  03ea5b78 03ea5abc 00110000 03ea1a88
0x0032df50:  0032df70 70de75be 00110000 0032df68
0x0032df60:  000001ca 03ea5a28 00110002 0000000e
0x0032df70:  0032df9c 70d7bbae 000001ca 03ea1a88
0x0032df80:  03ea5c86 00000000 03ea58b8 00000005
0x0032df90:  03ea5a2c 00000000 00000007 0032dfd8
Backtrace:
=>1 0x70d37550 in gdiplus (+0x37550) (0x0032df50)
  2 0x70de75be in gdiplus (+0xe75be) (0x0032df70)
  3 0x70d7bbae in gdiplus (+0x7bbae) (0x0032df9c)
  4 0x70d37ee2 in gdiplus (+0x37ee2) (0x0032dfd8)
  5 0x70d3822d in gdiplus (+0x3822d) (0x0032dff8)
  6 0x70d391b7 in gdiplus (+0x391b7) (0x0032e12c)
  7 0x70db6205 in gdiplus (+0xb6205) (0x0032e348)
  8 0x70db6404 in gdiplus (+0xb6404) (0x0032e9a4)
  9 0x70d7524c in gdiplus (+0x7524c) (0x0032e9f0)
0x70d37550: movl	0x0(%edi,%ecx,1),%ecx
Modules:
Module	Address			Debug info	Name (78 modules)
PE	  400000-  426000	Deferred        inklearn
PE	11000000-1100a000	Deferred        hanlib
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
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e11d000-7e132000	Deferred        lz32<elf>
  \-PE	7e120000-7e132000	\               lz32
ELF	7e132000-7e14d000	Deferred        version<elf>
  \-PE	7e140000-7e14d000	\               version
ELF	7e28f000-7e2c2000	Deferred        uxtheme<elf>
  \-PE	7e2a0000-7e2c2000	\               uxtheme
ELF	7e2c2000-7e387000	Deferred        comctl32<elf>
  \-PE	7e2d0000-7e387000	\               comctl32
ELF	7e387000-7e49b000	Deferred        shell32<elf>
  \-PE	7e3a0000-7e49b000	\               shell32
ELF	7e49b000-7e4af000	Deferred        libresolv.so.2
ELF	7e4c6000-7e4e5000	Deferred        iphlpapi<elf>
  \-PE	7e4d0000-7e4e5000	\               iphlpapi
ELF	7e4e5000-7e548000	Deferred        rpcrt4<elf>
  \-PE	7e4f0000-7e548000	\               rpcrt4
ELF	7e548000-7e5ee000	Deferred        ole32<elf>
  \-PE	7e560000-7e5ee000	\               ole32
ELF	7e810000-7e87c000	Deferred        msvcrt<elf>
  \-PE	7e820000-7e87c000	\               msvcrt
ELF	7e87c000-7e885000	Deferred        libxcursor.so.1
ELF	7e885000-7e88a000	Deferred        libxfixes.so.3
ELF	7e88a000-7e88e000	Deferred        libxcomposite.so.1
ELF	7e88e000-7e895000	Deferred        libxrandr.so.2
ELF	7e895000-7e89f000	Deferred        libxrender.so.1
ELF	7e89f000-7e8a2000	Deferred        libxinerama.so.1
ELF	7e8a2000-7e8c3000	Deferred        imm32<elf>
  \-PE	7e8b0000-7e8c3000	\               imm32
ELF	7e8c3000-7e8c8000	Deferred        libxdmcp.so.6
ELF	7e8c8000-7e8e1000	Deferred        libxcb.so.1
ELF	7e8e1000-7e8e4000	Deferred        libxcb-xlib.so.0
ELF	7e8e4000-7e8e7000	Deferred        libxau.so.6
ELF	7e8e7000-7e9d6000	Deferred        libx11.so.6
ELF	7e9d6000-7e9e5000	Deferred        libxext.so.6
ELF	7e9e5000-7e9eb000	Deferred        libxxf86vm.so.1
ELF	7e9eb000-7ea03000	Deferred        libice.so.6
ELF	7ea03000-7ea0c000	Deferred        libsm.so.6
ELF	7ea23000-7eabe000	Deferred        winex11<elf>
  \-PE	7ea30000-7eabe000	\               winex11
ELF	7eafa000-7eb21000	Deferred        libexpat.so.1
ELF	7eb21000-7eb4e000	Deferred        libfontconfig.so.1
ELF	7eb4e000-7eb64000	Deferred        libz.so.1
ELF	7eb64000-7ebda000	Deferred        libfreetype.so.6
ELF	7ebf1000-7ec90000	Deferred        gdi32<elf>
  \-PE	7ec00000-7ec90000	\               gdi32
ELF	7ec90000-7eddc000	Deferred        user32<elf>
  \-PE	7ecb0000-7eddc000	\               user32
ELF	7eddc000-7ee37000	Deferred        shlwapi<elf>
  \-PE	7edf0000-7ee37000	\               shlwapi
ELF	7ee37000-7ee8a000	Deferred        advapi32<elf>
  \-PE	7ee40000-7ee8a000	\               advapi32
ELF	7efaa000-7efc3000	Deferred        libnsl.so.1
ELF	7efc3000-7efe9000	Deferred        libm.so.6
ELF	7efe9000-7eff5000	Deferred        libnss_files.so.2
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c60000-b7c69000	Deferred        libnss_compat.so.2
ELF	b7c6a000-b7c6e000	Deferred        libdl.so.2
ELF	b7c6e000-b7dcc000	Deferred        libc.so.6
ELF	b7dcd000-b7de6000	Deferred        libpthread.so.0
ELF	b7dfd000-b7f34000	Deferred        libwine.so.1
ELF	b7f36000-b7f53000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\host\Documents and Settings\Administrator\My Documents\InkLearn_0_9_2\InkLearn.exe
	0000001b    0
	00000018    2
	00000017    0
	00000009    0 <==
0000000c 
	00000016    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000019 
	0000001a    0
Backtrace:
=>1 0x70d37550 in gdiplus (+0x37550) (0x0032df50)
  2 0x70de75be in gdiplus (+0xe75be) (0x0032df70)
  3 0x70d7bbae in gdiplus (+0x7bbae) (0x0032df9c)
  4 0x70d37ee2 in gdiplus (+0x37ee2) (0x0032dfd8)
  5 0x70d3822d in gdiplus (+0x3822d) (0x0032dff8)
  6 0x70d391b7 in gdiplus (+0x391b7) (0x0032e12c)
  7 0x70db6205 in gdiplus (+0xb6205) (0x0032e348)
  8 0x70db6404 in gdiplus (+0xb6404) (0x0032e9a4)
  9 0x70d7524c in gdiplus (+0x7524c) (0x0032e9f0)

Unhandled Exception: System.AccessViolationException: Attempted to read or write protected memory. This is often an indication that other memory is corrupt.
   at System.Drawing.SafeNativeMethods.Gdip.GdipCreateFontFromLogfontW(HandleRef hdc, Object lf, IntPtr& font)
   at System.Drawing.Font.FromLogFont(Object lf, IntPtr hdc)
   at System.Drawing.Font.FromHfont(IntPtr hfont)
   at System.Drawing.SystemFonts.get_DefaultFont()
   at System.Windows.Forms.Control.get_Font()
   at System.Windows.Forms.Control.get_FontHeight()
   at System.Windows.Forms.TextBoxBase.get_PreferredHeight()
   at System.Windows.Forms.TextBoxBase.get_DefaultSize()
   at System.Windows.Forms.Control..ctor(Boolean autoInstallSyncContext)
   at System.Windows.Forms.TextBoxBase..ctor()
   at System.Windows.Forms.TextBox..ctor()
   at InkLearnApp.MainForm.InitializeComponent()
   at InkLearnApp.MainForm..ctor()
   at InkLearnApp.MainForm.Main(String[] args)
```

I also tried "mono InkLearn.exe" and I got this:

```
** (InkLearn.exe:6510): WARNING **: The following assembly referenced from /host/Documents and Settings/Administrator/My Documents/InkLearn_0_9_2/InkLearn.exe could not be loaded:
     Assembly:   Microsoft.Ink    (assemblyref_index=4)
     Version:    1.7.2600.2180
     Public Key: 31bf3856ad364e35
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/host/Documents and Settings/Administrator/My Documents/InkLearn_0_9_2/).


** (InkLearn.exe:6510): WARNING **: Could not load file or assembly 'Microsoft.Ink, Version=1.7.2600.2180, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'InkLearnApp.MainForm' from assembly 'InkLearn, Version=0.9.2.0, Culture=neutral'.
```

I saw another similar package called "libmono-winforms2.0-cil" and I installed it from Synaptics then tried wine and mono again, I get the same error messages in the Terminal.

---

### Post by cogadh on 2009-01-22
It is looking for the "Microsoft.Ink" assembly which is not present in Wine or any of the Linux Mono packages you installed. Essentially it is the thing that allows what you do with the stylus to appear as writing on the screen. You might be able to gain the necessary functionality in Wine by adding the Microsoft.Ink.dll and Microsoft.Ink.resources.dll from a Windows Tablet Edition installation to Wine's system32 directory or the app's installation directory.

---

### Post by h2o4444 on 2009-01-22
I don't have the Windows installation CDs since the computer is my mom's and she got it from my uncle who, most likely, would not have it.

However, I did write a message to the creater of InkLearn and asked him for help and perhaps he can release the program to the open source community under GNU GPL so that other people can continue developing it (InkLearn ceased development in 2005). The program did not have a license indicated in the About option.

I really think InkLearn is the best way for people to learn foreign languages on the tablet laptop, especially Eastern langauges where the input method is more graphical. Right now InkLearn is made for Chinese but I'm sure someone can add Japanese, Korean, etc to it.

InkLearn is probably the only program that is stopping me making a complete shift from Windows to Linux.

---

### Post by cogadh on 2009-01-22
You can try searching online for those DLLs, however, I am not sure of the legal issues associated with it. Usually MS DLLs require you to own and accept the Microsoft license agreement before you can use them.

---

### Post by h2o4444 on 2009-03-26
Hello All,

 Recently my computer "died"/"crashed" when I tried to reinstalled Ubuntu through Wubi. The Windows XP Tablet Edition recovery CD-Rom that came with the computer was unable to load due to a win32 error. I think there was a mess up with the filesystems for Windows and Ubuntu that caused the crash. So I am "forced" to install GNU/Linux as the sole operating system on my computer.

 It worked well for the most part but the program that I value the most when I had Windows does not work in Ubuntu, even under Wine. This program is InkLearn.

 InkLearn is a language learning program for the tablet PC. You can google it to learn more about it but it is essentially a program where you use the stylus to write a Chinese character and the program will tell you its meaning, pronounciation, alternative character (traditional or simplified Chinese character of the same word), and associated words.

 The program is so essential to my Chinese learning experience that I simply cannot do without. Now that my computer is completely GNU/Linux I am both happy and sad.

 So I am writing this post to ask the GNU/Linux community if anyone knows of a similar program for the tablet that can do what InkLearn does. Also if there isn't such a program would anyone willing to write one. I don't know computer programming (even though I tried to learn it to no success) but I can offer my help in whatever means. The author of InkLearn is Jerome Punzalan and I had asked him to release the InkLearn codes to the open source community but he has not replied to my message.

 If you are using a tablet and running Windows I suggest you try InkLearn and see how it works. It really is a wonderful program and I hope it gets ported to Linux.

Thanks and Sincerely,
-Hiatt

---

