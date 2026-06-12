---
title: "Tell me More"
date: 2009-09-30
forum: Wine
---

### Post by basraks on 2009-09-30
I have installed Tell me More Kids - English from Auralog on Ubuntu 9.04 with Wine 1.01.   Installation went fine but when I run application I can only hear sound while something wrong is happening with graphic. It seems that application is running in background and there is some sort of invisible layer on top of all other windows. I can only see field where I should enter my name and I can type in this box but I can't go any further. I also can't select anything in the background with my mouse.   I can run other two application from this package but I can't start main program from there.   I am newbie in Linux, specially in Wine so I don't have any idea what else can I try to run this application on Ubuntu. I'll appreciate any help.

---

### Post by castlefox on 2009-10-01
Do you know what graphic hardware you are running?

If you are using Intel for graphics, they are know to have problems with the 9.04 release.  

Search for you in [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by basraks on 2009-10-01
I have Sony Vaio VGN-A217M with Intel 1.6GHz Centrino, 2GB RAM and ATI Mobility Radeon 9700 64MB.

There is one issue on appdb with other version of Tell me More and Ubuntu 8.10. My problem isn't familiar with that.

EDIT: When I check emulate a virtual desktop in Wine configuration I get blue background with name field. I have tried to guess where should be forward button but I only managed to hit close button. :( I also tried winetricks with d3dx9, ie6, flash and few more tricks without any success.

---

### Post by basraks on 2009-10-02
When I run it from terminal it gives me next output:

```

fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x104ac28,0x00000004,0x104ac24) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1049f1c): Stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1049960,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x92cfa0, 0x102aff0) stub
fixme:psapi:EnumPageFilesA (0x92cfa0, 0xff9518) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x1025a6c,0x00000018,(nil)) stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
fixme:cursor:SetSystemCursor (0x10de,00007f00),stub!
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:SetSystemCursor (0x10de,00007f00),stub!
fixme:cursor:SetSystemCursor (0x112e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1146,00007f03),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11ce,00007f02),stub!
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x105f948): Stub!
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: pixel format conversion
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
fixme:quartz:MediaControl_StopWhenReady (0x1b7188/0x1b718c)->(): stub !!!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"0424041a", 0001: stub!

```

Does anyone know where could be a problem?

---

### Post by basraks on 2009-10-02
After upgrade Wine on version 1.1.30 and clean install of Tell me More I get next code in terminal:

```

fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1049ecc): Stub!
err:rpc:I_RpcGetBuffer no binding
fixme:gl_compat:add_gl_compat_wrappers GL implementation supports GL_ARB_fragment_program but not GL_EXT_fog_coord
fixme:gl_compat:add_gl_compat_wrappers The fog coord emulation will most likely fail
fixme:win:EnumDisplayDevicesW ((null),0,0x1049820,0x00000000), stub!
fixme:gl_compat:add_gl_compat_wrappers GL implementation supports GL_ARB_fragment_program but not GL_EXT_fog_coord
fixme:gl_compat:add_gl_compat_wrappers The fog coord emulation will most likely fail
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glFogi hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glFogiv hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glFogf hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glFogfv hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glEnable hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glDisable hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glVertex4f hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glVertex4fv hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glVertex3f hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glVertex3fv hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glColor4f hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glColor4fv hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glColor3f hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glColor3fv hook already applied
fixme:gl_compat:add_gl_compat_wrappers GL_EXT_fogcoord glColor4ub hook already applied
fixme:win:EnumDisplayDevicesW ((null),0,0x10493a0,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x92cfa0, 0x102afa0) stub
fixme:psapi:EnumPageFilesA (0x92cfa0, 0xff94c8) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d0c04 (device=2d access=0 func=301 method=0)
wine: Unhandled page fault on read access to 0x00000000 at address 0xa4ef47 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00a4ef47).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00a4ef47 ESP:01020c70 EBP:010215e0 EFLAGS:00210296(  R- --  I S -A-P- )
 EAX:00000000 EBX:00000000 ECX:7bc95da4 EDX:ffffffff
 ESI:00c0f50c EDI:00c0f50c
Stack dump:
0x01020c70:  00000010 00000088 00c1193c 00a49793
0x01020c80:  010215ac 00c11934 00c1473d 00000001
0x01020c90:  010244da 00000000 00000000 00000000
0x01020ca0:  00000000 00000000 00000000 00000000
0x01020cb0:  00000000 00000000 00000000 00000000
0x01020cc0:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x00a4ef47 in kids (+0x64ef47) (0x010215e0)
  1 0x00a5b047 in kids (+0x65b047) (0x01021668)
  2 0x009e1d7e in kids (+0x5e1d7e) (0x010259e4)
  3 0x009f6b08 in kids (+0x5f6b08) (0x0102852c)
  4 0x00a01ff5 in kids (+0x601ff5) (0x0102eec4)
  5 0x1d0e4f1c (0x00d0ec70)
  6 0x255f3776 (0x007905b9)
  7 0xf18b5601 (0x042444f6)
  8 0x00000000 (0x00000000)
0x00a4ef47: cmpb    $0x0,0x0(%ebx)
Modules:
Module    Address            Debug info    Name (119 modules)
PE      400000-  e56000    Export          kids
PE    70bd0000-70c35000    Deferred        shlwapi
ELF    77fe8000-78000000    Deferred        msacm32<elf>
  \-PE    77ff0000-78000000    \               msacm32
PE    78000000-78044000    Deferred        msvcrt
ELF    7b800000-7b974000    Deferred        kernel32<elf>
  \-PE    7b820000-7b974000    \               kernel32
ELF    7bc00000-7bcb2000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb2000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7da2e000-7da44000    Deferred        psapi<elf>
  \-PE    7da30000-7da44000    \               psapi
ELF    7da44000-7da4e000    Deferred        libdrm.so.2
ELF    7da4e000-7dab1000    Deferred        libgl.so.1
ELF    7dab1000-7dbe4000    Deferred        wined3d<elf>
  \-PE    7dac0000-7dbe4000    \               wined3d
ELF    7dbe4000-7dc13000    Deferred        d3d9<elf>
  \-PE    7dbf0000-7dc13000    \               d3d9
ELF    7dc13000-7dc17000    Deferred        libgpg-error.so.0
ELF    7dc17000-7dc80000    Deferred        libgcrypt.so.11
ELF    7dc80000-7dc92000    Deferred        libtasn1.so.3
ELF    7dc92000-7dc9b000    Deferred        libkrb5support.so.0
ELF    7dc9b000-7dcbf000    Deferred        libk5crypto.so.3
ELF    7dcbf000-7dd51000    Deferred        libkrb5.so.3
ELF    7dd51000-7ddee000    Deferred        libgnutls.so.26
ELF    7ddee000-7de19000    Deferred        libgssapi_krb5.so.2
ELF    7de19000-7de50000    Deferred        libcups.so.2
ELF    7de64000-7de7d000    Deferred        spoolss<elf>
  \-PE    7de70000-7de7d000    \               spoolss
ELF    7de7d000-7de9b000    Deferred        localspl<elf>
  \-PE    7de80000-7de9b000    \               localspl
ELF    7df24000-7df57000    Deferred        uxtheme<elf>
  \-PE    7df30000-7df57000    \               uxtheme
ELF    7df57000-7df6c000    Deferred        midimap<elf>
  \-PE    7df60000-7df6c000    \               midimap
ELF    7df6c000-7df72000    Deferred        libattr.so.1
ELF    7df72000-7df79000    Deferred        libgdbm.so.3
ELF    7df79000-7df7e000    Deferred        libcap.so.2
ELF    7df7e000-7dfdd000    Deferred        libpulse.so.0
ELF    7dfdd000-7e0a5000    Deferred        libasound.so.2
ELF    7e0a5000-7e0a8000    Deferred        libxdamage.so.1
ELF    7e0a8000-7e0ac000    Deferred        libkeyutils.so.1
ELF    7e0b5000-7e0b9000    Deferred        libcom_err.so.2
ELF    7e0b9000-7e0f0000    Deferred        winealsa<elf>
  \-PE    7e0c0000-7e0f0000    \               winealsa
ELF    7e0f0000-7e0f9000    Deferred        libxcursor.so.1
ELF    7e0f9000-7e0fe000    Deferred        libxfixes.so.3
ELF    7e0fe000-7e102000    Deferred        libxcomposite.so.1
ELF    7e102000-7e10a000    Deferred        libxrandr.so.2
ELF    7e10a000-7e114000    Deferred        libxrender.so.1
ELF    7e114000-7e11a000    Deferred        libxxf86vm.so.1
ELF    7e11a000-7e11d000    Deferred        libxinerama.so.1
ELF    7e11d000-7e122000    Deferred        libxdmcp.so.6
ELF    7e122000-7e13c000    Deferred        libxcb.so.1
ELF    7e13c000-7e140000    Deferred        libxau.so.6
ELF    7e140000-7e145000    Deferred        libuuid.so.1
ELF    7e145000-7e234000    Deferred        libx11.so.6
ELF    7e234000-7e244000    Deferred        libxext.so.6
ELF    7e244000-7e25c000    Deferred        libice.so.6
ELF    7e25c000-7e265000    Deferred        libsm.so.6
ELF    7e267000-7e26e000    Deferred        libasound_module_pcm_pulse.so
ELF    7e26e000-7e277000    Deferred        librt.so.1
ELF    7e279000-7e318000    Deferred        winex11<elf>
  \-PE    7e290000-7e318000    \               winex11
ELF    7e375000-7e39c000    Deferred        libexpat.so.1
ELF    7e39c000-7e3c9000    Deferred        libfontconfig.so.1
ELF    7e3c9000-7e3df000    Deferred        libz.so.1
ELF    7e3df000-7e456000    Deferred        libfreetype.so.6
ELF    7e456000-7e46c000    Deferred        libresolv.so.2
ELF    7e480000-7e4a0000    Deferred        iphlpapi<elf>
  \-PE    7e490000-7e4a0000    \               iphlpapi
ELF    7e4a0000-7e4ce000    Deferred        ws2_32<elf>
  \-PE    7e4b0000-7e4ce000    \               ws2_32
ELF    7e4ce000-7e4e9000    Deferred        wsock32<elf>
  \-PE    7e4d0000-7e4e9000    \               wsock32
ELF    7e4e9000-7e4fd000    Deferred        lz32<elf>
  \-PE    7e4f0000-7e4fd000    \               lz32
ELF    7e4fd000-7e518000    Deferred        version<elf>
  \-PE    7e500000-7e518000    \               version
ELF    7e518000-7e5fe000    Deferred        oleaut32<elf>
  \-PE    7e530000-7e5fe000    \               oleaut32
ELF    7e5fe000-7e634000    Deferred        winspool<elf>
  \-PE    7e610000-7e634000    \               winspool
ELF    7e634000-7e6fd000    Deferred        comctl32<elf>
  \-PE    7e640000-7e6fd000    \               comctl32
ELF    7e6fd000-7e88d000    Deferred        shell32<elf>
  \-PE    7e710000-7e88d000    \               shell32
ELF    7e88d000-7e93f000    Deferred        comdlg32<elf>
  \-PE    7e890000-7e93f000    \               comdlg32
ELF    7e93f000-7e960000    Deferred        imm32<elf>
  \-PE    7e950000-7e960000    \               imm32
ELF    7e960000-7e986000    Deferred        msacm32<elf>
  \-PE    7e970000-7e986000    \               msacm32
ELF    7e986000-7ea22000    Deferred        winmm<elf>
  \-PE    7e990000-7ea22000    \               winmm
ELF    7ea22000-7ea6f000    Deferred        dsound<elf>
  \-PE    7ea30000-7ea6f000    \               dsound
ELF    7ea6f000-7eadd000    Deferred        rpcrt4<elf>
  \-PE    7ea80000-7eadd000    \               rpcrt4
ELF    7eadd000-7eb7f000    Deferred        gdi32<elf>
  \-PE    7eaf0000-7eb7f000    \               gdi32
ELF    7eb7f000-7eccb000    Deferred        user32<elf>
  \-PE    7eba0000-7eccb000    \               user32
ELF    7eccb000-7ed22000    Deferred        advapi32<elf>
  \-PE    7ece0000-7ed22000    \               advapi32
ELF    7ed22000-7ee1f000    Deferred        ole32<elf>
  \-PE    7ed40000-7ee1f000    \               ole32
ELF    7ee1f000-7ee76000    Deferred        ddraw<elf>
  \-PE    7ee30000-7ee76000    \               ddraw
ELF    7efa1000-7efad000    Deferred        libnss_files.so.2
ELF    7efad000-7efc6000    Deferred        libnsl.so.1
ELF    7efc6000-7efec000    Deferred        libm.so.6
ELF    7efec000-7eff7000    Deferred        libnss_nis.so.2
ELF    7eff7000-7f000000    Deferred        libnss_compat.so.2
ELF    b7d14000-b7d18000    Deferred        libdl.so.2
ELF    b7d18000-b7e7b000    Deferred        libc.so.6
ELF    b7e7c000-b7e95000    Deferred        libpthread.so.0
ELF    b7ea9000-b7fe5000    Deferred        libwine.so.1
ELF    b7fe7000-b8005000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Auralog\TMMKids3.0\Kids_CD1\bin\kids.exe
    00000009    0 <==
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
00000022 
    00000023    0
Backtrace:
=>0 0x00a4ef47 in kids (+0x64ef47) (0x010215e0)
  1 0x00a5b047 in kids (+0x65b047) (0x01021668)
  2 0x009e1d7e in kids (+0x5e1d7e) (0x010259e4)
  3 0x009f6b08 in kids (+0x5f6b08) (0x0102852c)
  4 0x00a01ff5 in kids (+0x601ff5) (0x0102eec4)
  5 0x1d0e4f1c (0x00d0ec70)
  6 0x255f3776 (0x007905b9)
  7 0xf18b5601 (0x042444f6)
  8 0x00000000 (0x00000000)

```Any clue?

EDIT: After Wine upgrade on version 1.1.30 Tell me More doesn't start at all.

---

### Post by basraks on 2010-11-23
Me again. I havent solved this problem yet so I'll ask about this one more time. This time I am runnig Ubuntu 10.04 with Wine 1.2. And after running same application I get next code in terminal:
```

fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 4 and card vendor 0000.
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
fixme:win:EnumDisplayDevicesW ((null),0,0x10496b8,0x00000000), stub!
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 4 and card vendor 0000.
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
fixme:win:EnumDisplayDevicesW ((null),0,0x1049238,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x92cfa0, 0x102af78) stub
fixme:psapi:EnumPageFilesA (0x92cfa0, 0xff94a0) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:cdrom:CDROM_GetMediaType : faking success
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x10259f4,0x00000018,(nil)) stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
fixme:cursor:SetSystemCursor (0x20060,00007f00),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x1007c,00007f00),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x1007e,00007f8a),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x10080,00007f03),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x10082,00007f01),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x10084,00007f88),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x10086,00007f86),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x10088,00007f83),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x1008a,00007f82),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x1008c,00007f84),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x1008e,00007f04),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x10090,00007f02),stub!
fixme:cursor:SetSystemCursor (0x20060,00007f00),stub!
fixme:cursor:SetSystemCursor (0x50028,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x4005a,00007f00),stub!
fixme:cursor:SetSystemCursor (0x20066,00007f03),stub!
fixme:cursor:SetSystemCursor (0x20064,00007f01),stub!
fixme:cursor:SetSystemCursor (0x2005e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x20052,00007f86),stub!
fixme:cursor:SetSystemCursor (0x20020,00007f83),stub!
fixme:cursor:SetSystemCursor (0x1006a,00007f85),stub!
fixme:cursor:SetSystemCursor (0x1006e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x10072,00007f84),stub!
fixme:cursor:SetSystemCursor (0x10076,00007f04),stub!
fixme:cursor:SetSystemCursor (0x1007a,00007f02),stub!
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 4 and card vendor 0000.
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
fixme:win:EnumDisplayDevicesW ((null),0,0x105eec8,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x183148,0x183048): stub
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
fixme:quartz:MediaControl_StopWhenReady (0x1de3f8/0x1de3fc)->(): stub !!!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"0000041a", 0001: stub!
```
Is there any way how I can solve this issue? tnx

---

### Post by doolph on 2011-05-21
hello, I have the same problem, and I don't have any clue to fix the problem :(((

---

