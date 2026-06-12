---
title: "Spore won't even start?"
date: 2009-10-14
forum: Wine
---

### Post by Mike_IronFist on 2009-10-14
I haven't been able to get Spore running on Wine, regardless of running it with or without any kind of crack.

Can anyone help me get it started?

---

### Post by asdfoo on 2009-10-16
> **Mike_IronFist said:**
> I haven't been able to get Spore running on Wine, regardless of running it with or without any kind of crack.

Can anyone help me get it started?

care to provide some elementary information?

wine --version

glxinfo | grep -i version


terminal output? (cd to install dir, then run wine spore.exe or whatever)

---

### Post by Mike_IronFist on 2009-10-16
> **asdfoo said:**
> care to provide some elementary information?

wine --version

glxinfo | grep -i version


terminal output? (cd to install dir, then run wine spore.exe or whatever)

Ah yes, excuse me for not mentioning this beforehand!
Just as a note, I'm running Ubuntu Jaunty, 64-bit. I've tried, and failed, on the 32-bit version as well.

Wine is version 1.1.9, but once again I've tried, and failed on the original version that comes with Ubuntu as well.

Glx Info:```
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.3
OpenGL version string: 3.0.0 NVIDIA 185.18.36
OpenGL shading language version string: 1.30 NVIDIA via Cg compiler

```

Now, for the terminal output for running "wine SporeApp.exe":
```
mike@mike-laptop:~/.wine/dosdevices/c:/Program Files/Electronic Arts/SPORE$ wine SporeApp.exe
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x292a3b0,0x00000004,0x292a3ac) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x292929c): Stub!
wine: Unhandled page fault on write access to 0x62c06284 at address 0x7dbf6be6 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x62c06284 in 32-bit code (0x7dbf6be6).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7dbf6be6 ESP:02928708 EBP:00000009 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000018 EBX:f7cf56c0 ECX:7dc49ec0 EDX:62c06284
 ESI:f7cf56c0 EDI:00004a6b
Stack dump:
0x02928708:  00000000 7dbfe422 00000001 00000000
0x02928718:  7d320e00 01320e2c 00004a6b 7d320e00
0x02928728:  ffeec3e8 7dbfea11 f7cf56c0 00004a6b
0x02928738:  00000001 00000000 7dc24ac0 7dc25d60
0x02928748:  02928768 7ce8d9b2 f7fecff4 00000000
0x02928758:  f7e3be41 f7fecff4 7c512598 00000000
Backtrace:
=>1 0x7dbf6be6 in libgl.so.1 (+0x52be6) (0x00000009)
  2 0x00000000 (0x00000000)
0x7dbf6be6: movl	$0x7dc27000,0x0(%edx)
Modules:
Module	Address			Debug info	Name (114 modules)
PE	  400000- 243a000	Deferred        sporeapp
ELF	7b800000-7b940000	Deferred        kernel32<elf>
  \-PE	7b820000-7b940000	\               kernel32
ELF	7bc00000-7bcac000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcac000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7cc3b000-7dba4000	Deferred        libglcore.so.1
ELF	7dba4000-7dc4b000	Export          libgl.so.1
ELF	7dc68000-7dcfd000	Deferred        opengl32<elf>
ELF	7de69000-7de9c000	Deferred        uxtheme<elf>
  \-PE	7de70000-7de9c000	\               uxtheme
ELF	7de9c000-7deb1000	Deferred        midimap<elf>
  \-PE	7dea0000-7deb1000	\               midimap
ELF	7deb1000-7deda000	Deferred        msacm32<elf>
  \-PE	7dec0000-7deda000	\               msacm32
ELF	7deda000-7dee3000	Deferred        librt.so.1
ELF	7dee3000-7dfab000	Deferred        libasound.so.2
ELF	7dfab000-7dfd0000	Deferred        libaudiofile.so.0
ELF	7dfd0000-7dfdb000	Deferred        libesd.so.0
ELF	7dfdf000-7dff8000	Deferred        msacm32<elf>
  \-PE	7dfe0000-7dff8000	\               msacm32
ELF	7dff8000-7e001000	Deferred        libxcursor.so.1
ELF	7e001000-7e006000	Deferred        libxfixes.so.3
ELF	7e006000-7e00a000	Deferred        libxcomposite.so.1
ELF	7e00a000-7e012000	Deferred        libxrandr.so.2
ELF	7e012000-7e01c000	Deferred        libxrender.so.1
ELF	7e01c000-7e022000	Deferred        libxxf86vm.so.1
ELF	7e022000-7e025000	Deferred        libxinerama.so.1
ELF	7e025000-7e02a000	Deferred        libxdmcp.so.6
ELF	7e02a000-7e044000	Deferred        libxcb.so.1
ELF	7e044000-7e048000	Deferred        libxau.so.6
ELF	7e048000-7e04d000	Deferred        libuuid.so.1
ELF	7e04d000-7e13c000	Deferred        libx11.so.6
ELF	7e13c000-7e14c000	Deferred        libxext.so.6
ELF	7e14c000-7e164000	Deferred        libice.so.6
ELF	7e164000-7e16d000	Deferred        libsm.so.6
ELF	7e16d000-7e16f000	Deferred        libnvidia-tls.so.1
ELF	7e16f000-7e18a000	Deferred        wineesd<elf>
  \-PE	7e170000-7e18a000	\               wineesd
ELF	7e18a000-7e226000	Deferred        winex11<elf>
  \-PE	7e1a0000-7e226000	\               winex11
ELF	7e28a000-7e2b1000	Deferred        libexpat.so.1
ELF	7e2b1000-7e2de000	Deferred        libfontconfig.so.1
ELF	7e2de000-7e2f4000	Deferred        libz.so.1
ELF	7e2f4000-7e36b000	Deferred        libfreetype.so.6
ELF	7e388000-7e3a3000	Deferred        wsock32<elf>
  \-PE	7e390000-7e3a3000	\               wsock32
ELF	7e3a3000-7e4c7000	Deferred        wined3d<elf>
  \-PE	7e3c0000-7e4c7000	\               wined3d
ELF	7e4c7000-7e4f8000	Deferred        d3d9<elf>
  \-PE	7e4d0000-7e4f8000	\               d3d9
ELF	7e4f8000-7e519000	Deferred        d3dx8<elf>
  \-PE	7e500000-7e519000	\               d3dx8
ELF	7e519000-7e53a000	Deferred        d3dx9_36<elf>
  \-PE	7e520000-7e53a000	\               d3dx9_36
ELF	7e53a000-7e554000	Deferred        d3dx9_27<elf>
  \-PE	7e540000-7e554000	\               d3dx9_27
ELF	7e554000-7e58d000	Deferred        dinput<elf>
  \-PE	7e560000-7e58d000	\               dinput
ELF	7e58d000-7e5a7000	Deferred        dinput8<elf>
  \-PE	7e590000-7e5a7000	\               dinput8
ELF	7e5a7000-7e66e000	Deferred        comctl32<elf>
  \-PE	7e5b0000-7e66e000	\               comctl32
ELF	7e66e000-7e6cb000	Deferred        shlwapi<elf>
  \-PE	7e680000-7e6cb000	\               shlwapi
ELF	7e6cb000-7e7f7000	Deferred        shell32<elf>
  \-PE	7e6e0000-7e7f7000	\               shell32
ELF	7e7f7000-7e85e000	Deferred        rpcrt4<elf>
  \-PE	7e800000-7e85e000	\               rpcrt4
ELF	7e85e000-7e971000	Deferred        ole32<elf>
  \-PE	7e880000-7e971000	\               ole32
ELF	7e971000-7ea05000	Deferred        winmm<elf>
  \-PE	7e980000-7ea05000	\               winmm
ELF	7ea05000-7ea51000	Deferred        dsound<elf>
  \-PE	7ea10000-7ea51000	\               dsound
ELF	7ea51000-7ea9f000	Deferred        dbghelp<elf>
  \-PE	7ea60000-7ea9f000	\               dbghelp
ELF	7ea9f000-7eacc000	Deferred        ws2_32<elf>
  \-PE	7eab0000-7eacc000	\               ws2_32
ELF	7eacc000-7eae2000	Deferred        libresolv.so.2
ELF	7eae9000-7eaff000	Deferred        psapi<elf>
  \-PE	7eaf0000-7eaff000	\               psapi
ELF	7eaff000-7eb1f000	Deferred        iphlpapi<elf>
  \-PE	7eb10000-7eb1f000	\               iphlpapi
ELF	7eb1f000-7eb46000	Deferred        netapi32<elf>
  \-PE	7eb30000-7eb46000	\               netapi32
ELF	7eb46000-7eb67000	Deferred        imm32<elf>
  \-PE	7eb50000-7eb67000	\               imm32
ELF	7eb67000-7eb80000	Deferred        usp10<elf>
  \-PE	7eb70000-7eb80000	\               usp10
ELF	7eb80000-7eb95000	Deferred        lz32<elf>
  \-PE	7eb90000-7eb95000	\               lz32
ELF	7eb95000-7ec01000	Deferred        msvcrt<elf>
  \-PE	7ebb0000-7ec01000	\               msvcrt
ELF	7ec01000-7ec20000	Deferred        msvcr71<elf>
  \-PE	7ec10000-7ec20000	\               msvcr71
ELF	7ec20000-7ec75000	Deferred        advapi32<elf>
  \-PE	7ec30000-7ec75000	\               advapi32
ELF	7ec75000-7ed15000	Deferred        gdi32<elf>
  \-PE	7ec90000-7ed15000	\               gdi32
ELF	7ed15000-7ee63000	Deferred        user32<elf>
  \-PE	7ed30000-7ee63000	\               user32
ELF	7ef8d000-7ef99000	Deferred        libnss_files.so.2
ELF	7ef99000-7efa4000	Deferred        libnss_nis.so.2
ELF	7efa4000-7efbd000	Deferred        libnsl.so.1
ELF	7efbd000-7efe3000	Deferred        libm.so.6
ELF	7efe4000-7efff000	Deferred        version<elf>
  \-PE	7eff0000-7efff000	\               version
ELF	f7cf6000-f7cfa000	Deferred        libdl.so.2
ELF	f7cfa000-f7e5d000	Deferred        libc.so.6
ELF	f7e5e000-f7e77000	Deferred        libpthread.so.0
ELF	f7e77000-f7e80000	Deferred        libnss_compat.so.2
ELF	f7e94000-f7fcb000	Deferred        libwine.so.1
ELF	f7fcd000-f7fee000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Electronic Arts\SPORE\SporeApp.exe
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
00000021 
	00000022    0
Backtrace:
=>1 0x7dbf6be6 in libgl.so.1 (+0x52be6) (0x00000009)
  2 0x00000000 (0x00000000)

```

---

### Post by asdfoo on 2009-10-16
> **Mike_IronFist said:**
> Wine is version 1.1.9, but once again I've tried, and failed on the original version that comes with Ubuntu as well.
[/CODE]


Wine 1.1.9 was released 11 months ago, 1.1.31 was released two weeks ago, might be worth trying that one.

---

### Post by Mike_IronFist on 2009-10-17
> **asdfoo said:**
> Wine 1.1.9 was released 11 months ago, 1.1.31 was released two weeks ago, might be worth trying that one.

I just gave that a go..unfortunately, it didn't help.

---

### Post by zaksworld on 2009-10-17
I've tried to install spore to and it didn't work for me either, then I found this:
[http://linuxoutlaws.com/spore](http://linuxoutlaws.com/spore)

It explains how to customize your wine and make it able to run spore.

I customized my wine to be able to run iTunes, and now my iTunes runs nearly perfect on Ubuntu! (except it can't find my iPod :() Ha

---

