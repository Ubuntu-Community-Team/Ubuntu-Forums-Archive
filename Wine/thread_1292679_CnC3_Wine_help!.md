---
title: "CnC3 Wine help!"
date: 2009-10-16
forum: Wine
---

### Post by tuahaa on 2009-10-16
Well, I installed Command and Conquer 3: Tiberium Wars through wine and I can't play it! When I try, it says:

"the program cnc3game.dat has encountered a serious error and needs to close. We are sorry for the inconvenience"

When I run it in terminal, it says this:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x32f7a0,0x00000000), stub!
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1669ed0): Stub!
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0x1669824,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x16693a4,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0xe52e10, 0x164afa4) stub
fixme:psapi:EnumPageFilesA (0xe52e10, 0x16194cc) stub
fixme:win:EnumDisplayDevicesW ((null),0,0x15c82ac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x15c7e2c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x15c82b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x15c7e30,0x00000000), stub!
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x1645a20,0x00000018,(nil)) stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d0c04 (device=2d access=0 func=301 method=0)
wine: Unhandled page fault on read access to 0x00000000 at address 0x10ebe2f (thread 001c), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x010ebe2f).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:010ebe2f ESP:01644894 EBP:01645204 EFLAGS:00010296(  R- --  I S -A-P- )
 EAX:00000000 EBX:00000000 ECX:7bc95da4 EDX:ffffffff
 ESI:0124ee8c EDI:0124ee8c
Stack dump:
0x01644894:  0000001c 00000088 012512bc 010e665d
0x016448a4:  016451d0 012512b4 01645224 01645630
0x016448b4:  0000000e 00000000 0164851f 00000000
0x016448c4:  00000000 00000000 00000000 00000000
0x016448d4:  00000000 00000000 00000000 00000000
0x016448e4:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x010ebe2f in cnc3game.dat (+0xcebe2f) (0x01645204)
  1 0x010ef858 in cnc3game.dat (+0xcef858) (0x01645a2c)
  2 0x01037f9a in cnc3game.dat (+0xc37f9a) (0x01648530)
  3 0x0104126f in cnc3game.dat (+0xc4126f) (0x0164eec8)
  4 0xa1bd2759 (0x013652ac)
  5 0x00f26378 in cnc3game.dat (+0xb26378) (0x00f2443f)
  6 0xf18b5601 (0x042444f6)
  7 0x00000000 (0x00000000)
0x010ebe2f: cmpb	$0x0,0x0(%ebx)
Modules:
Module	Address			Debug info	Name (116 modules)
PE	  400000- 147b000	Export          cnc3game.dat
PE	 1680000- 18d2000	Deferred        d3dx9_29
PE	78130000-781cb000	Deferred        msvcr80
ELF	7b800000-7b972000	Deferred        kernel32<elf>
  \-PE	7b820000-7b972000	\               kernel32
ELF	7bc00000-7bcb2000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb2000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d9d5000-7d9eb000	Deferred        psapi<elf>
  \-PE	7d9e0000-7d9eb000	\               psapi
ELF	7d9eb000-7d9f5000	Deferred        libdrm_intel.so.1
ELF	7d9f5000-7dc67000	Deferred        i965_dri.so
ELF	7dc67000-7dc71000	Deferred        libdrm.so.2
ELF	7dc71000-7dcd4000	Deferred        libgl.so.1
ELF	7dcd4000-7de06000	Deferred        wined3d<elf>
  \-PE	7dce0000-7de06000	\               wined3d
ELF	7de06000-7de35000	Deferred        d3d9<elf>
  \-PE	7de10000-7de35000	\               d3d9
ELF	7de35000-7de4a000	Deferred        midimap<elf>
  \-PE	7de40000-7de4a000	\               midimap
ELF	7de4a000-7de70000	Deferred        msacm32<elf>
  \-PE	7de50000-7de70000	\               msacm32
ELF	7de70000-7de88000	Deferred        msacm32<elf>
  \-PE	7de80000-7de88000	\               msacm32
ELF	7de88000-7de8e000	Deferred        libattr.so.1
ELF	7de8e000-7deed000	Deferred        libpulse.so.0
ELF	7defe000-7df07000	Deferred        librt.so.1
ELF	7df07000-7dfcf000	Deferred        libasound.so.2
ELF	7dfcf000-7dfd2000	Deferred        libxdamage.so.1
ELF	7dfd2000-7dfd9000	Deferred        libgdbm.so.3
ELF	7dfd9000-7dfe0000	Deferred        libasound_module_pcm_pulse.so
ELF	7dfe0000-7e018000	Deferred        winealsa<elf>
  \-PE	7dff0000-7e018000	\               winealsa
ELF	7e066000-7e099000	Deferred        uxtheme<elf>
  \-PE	7e070000-7e099000	\               uxtheme
ELF	7e099000-7e0a2000	Deferred        libxcursor.so.1
ELF	7e0a2000-7e0a7000	Deferred        libxfixes.so.3
ELF	7e0a7000-7e0ab000	Deferred        libxcomposite.so.1
ELF	7e0ab000-7e0b3000	Deferred        libxrandr.so.2
ELF	7e0b3000-7e0bd000	Deferred        libxrender.so.1
ELF	7e0bd000-7e0c3000	Deferred        libxxf86vm.so.1
ELF	7e0c3000-7e0c6000	Deferred        libxinerama.so.1
ELF	7e0c6000-7e0cb000	Deferred        libxdmcp.so.6
ELF	7e0cb000-7e0e5000	Deferred        libxcb.so.1
ELF	7e0e5000-7e0e9000	Deferred        libxau.so.6
ELF	7e0e9000-7e1d8000	Deferred        libx11.so.6
ELF	7e1d8000-7e1e8000	Deferred        libxext.so.6
ELF	7e1e8000-7e200000	Deferred        libice.so.6
ELF	7e200000-7e209000	Deferred        libsm.so.6
ELF	7e213000-7e218000	Deferred        libcap.so.2
ELF	7e21a000-7e2b9000	Deferred        winex11<elf>
  \-PE	7e230000-7e2b9000	\               winex11
ELF	7e2fa000-7e321000	Deferred        libexpat.so.1
ELF	7e321000-7e34e000	Deferred        libfontconfig.so.1
ELF	7e34e000-7e353000	Deferred        libuuid.so.1
ELF	7e35f000-7e3d6000	Deferred        libfreetype.so.6
ELF	7e3d6000-7e3eb000	Deferred        system.drv16.so
PE	7e3e0000-7e3eb000	Deferred        system.drv16
ELF	7e3eb000-7e406000	Deferred        wsock32<elf>
  \-PE	7e3f0000-7e406000	\               wsock32
ELF	7e406000-7e41a000	Deferred        lz32<elf>
  \-PE	7e410000-7e41a000	\               lz32
ELF	7e41a000-7e434000	Deferred        version<elf>
  \-PE	7e420000-7e434000	\               version
ELF	7e434000-7e519000	Deferred        oleaut32<elf>
  \-PE	7e450000-7e519000	\               oleaut32
ELF	7e519000-7e52f000	Deferred        libresolv.so.2
ELF	7e52f000-7e54f000	Deferred        iphlpapi<elf>
  \-PE	7e540000-7e54f000	\               iphlpapi
ELF	7e54f000-7e576000	Deferred        netapi32<elf>
  \-PE	7e560000-7e576000	\               netapi32
ELF	7e576000-7e5a0000	Deferred        ws2_32<elf>
  \-PE	7e580000-7e5a0000	\               ws2_32
ELF	7e5a0000-7e5c3000	Deferred        mpr<elf>
  \-PE	7e5b0000-7e5c3000	\               mpr
ELF	7e5c3000-7e5d9000	Deferred        libz.so.1
ELF	7e5d9000-7e62f000	Deferred        wininet<elf>
  \-PE	7e5e0000-7e62f000	\               wininet
ELF	7e62f000-7e650000	Deferred        imm32<elf>
  \-PE	7e640000-7e650000	\               imm32
ELF	7e650000-7e6ec000	Deferred        winmm<elf>
  \-PE	7e660000-7e6ec000	\               winmm
ELF	7e6ec000-7e739000	Deferred        dsound<elf>
  \-PE	7e6f0000-7e739000	\               dsound
ELF	7e739000-7e7a7000	Deferred        rpcrt4<elf>
  \-PE	7e750000-7e7a7000	\               rpcrt4
ELF	7e7a7000-7e8a4000	Deferred        ole32<elf>
  \-PE	7e7c0000-7e8a4000	\               ole32
ELF	7e8a4000-7e8dd000	Deferred        dinput<elf>
  \-PE	7e8b0000-7e8dd000	\               dinput
ELF	7e8dd000-7e8f7000	Deferred        dinput8<elf>
  \-PE	7e8e0000-7e8f7000	\               dinput8
ELF	7e8f7000-7e966000	Deferred        msvcrt<elf>
  \-PE	7e910000-7e966000	\               msvcrt
ELF	7e966000-7ea30000	Deferred        comctl32<elf>
  \-PE	7e970000-7ea30000	\               comctl32
ELF	7ea30000-7ea8d000	Deferred        shlwapi<elf>
  \-PE	7ea40000-7ea8d000	\               shlwapi
ELF	7ea8d000-7ec1d000	Deferred        shell32<elf>
  \-PE	7eaa0000-7ec1d000	\               shell32
ELF	7ec1d000-7ed69000	Deferred        user32<elf>
  \-PE	7ec40000-7ed69000	\               user32
ELF	7ed69000-7edc0000	Deferred        advapi32<elf>
  \-PE	7ed80000-7edc0000	\               advapi32
ELF	7edc0000-7ee60000	Deferred        gdi32<elf>
  \-PE	7edd0000-7ee60000	\               gdi32
ELF	7ee60000-7ee6c000	Deferred        libnss_files.so.2
ELF	7ee6c000-7ee85000	Deferred        libnsl.so.1
ELF	7ee85000-7ee8e000	Deferred        libnss_compat.so.2
ELF	7efc9000-7efef000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7ccb000-b7ccf000	Deferred        libdl.so.2
ELF	b7ccf000-b7e32000	Deferred        libc.so.6
ELF	b7e33000-b7e4c000	Deferred        libpthread.so.0
ELF	b7e5d000-b7f99000	Deferred        libwine.so.1
ELF	b7f9b000-b7fb9000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	0000001a    0
	00000009    0
0000000e 
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000018 
	00000019    0
0000001b (D) C:\Program Files\Electronic Arts\Command & Conquer 3\RetailExe\1.0\cnc3game.dat
	0000001c    0 <==
Backtrace:
=>0 0x010ebe2f in cnc3game.dat (+0xcebe2f) (0x01645204)
  1 0x010ef858 in cnc3game.dat (+0xcef858) (0x01645a2c)
  2 0x01037f9a in cnc3game.dat (+0xc37f9a) (0x01648530)
  3 0x0104126f in cnc3game.dat (+0xc4126f) (0x0164eec8)
  4 0xa1bd2759 (0x013652ac)
  5 0x00f26378 in cnc3game.dat (+0xb26378) (0x00f2443f)
  6 0xf18b5601 (0x042444f6)
  7 0x00000000 (0x00000000)
```

It worked in Windows, I don't know why it won't work. I would really appreciate some form of help. I tried PlayOnLinux as well. I can't get it to run  :(

---

### Post by tuahaa on 2009-10-16
bumpppp

---

### Post by hikaricore on 2009-10-16
Yea... you're going to wait more than 30 minutes to bump in the future.
Approximately 24-48 hours to be exact.

If/when someone has a solution for you they will post it.
In the mean time check the WINE AppDB for possible solutions.
Please don't respond to this post in further attempts to bump your thread up.

---

### Post by harliCobweb on 2010-05-25
had the same error as u, after reading around found it was down to driver support for my graphics card don't know what make u have but mines a nvidia - if so you installing winetricks and try nvidia physX may help - worked for me!

---

