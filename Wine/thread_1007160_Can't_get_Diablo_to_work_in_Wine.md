---
title: "Can't get Diablo to work in Wine"
date: 2008-12-10
forum: Wine
---

### Post by TheOrangePeanut on 2008-12-10
It will play the intro video then immediately crash to desktop.  I see that other people are having the same problems.  Look here, at Sasa's post

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498)

I'm getting the same error message from wine.  I tried to use Winetricks to install DX9 as suggested in the thread, and although DX9 installed alright, the game still suffers that problem.  Any ideas?  I'm using the version of Wine available in the Intrepid repos.

---

### Post by stinger30au on 2008-12-10
use virtual box, install a copy of windows xp and try again

---

### Post by hikaricore on 2008-12-10
stinger... running Diablo on a VM is absurd.  
Please think a little more when you respond in this forum.

To the OP please provide more information about your hardware and any error output when running Diablo from a terminal window.

---

### Post by maddog46113 on 2008-12-10
> **TheOrangePeanut said:**
> It will play the intro video then immediately crash to desktop.  I see that other people are having the same problems.  Look here, at Sasa's post

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3498)

I'm getting the same error message from wine.  I tried to use Winetricks to install DX9 as suggested in the thread, and although DX9 installed alright, the game still suffers that problem.  Any ideas?  I'm using the version of Wine available in the Intrepid repos.

You might try using Winedoors and install all the w32 libraries. As the previous post states if you run it in terminal and give us the error message it would be much easier to solve.

---

### Post by TheOrangePeanut on 2008-12-10
```
nelson@alpha-pc:~/.wine/drive_c/Program Files/Diablo$ wine Diablo.exe 
nelson@alpha-pc:~/.wine/drive_c/Program Files/Diablo$ fixme:win:EnumDisplayDevicesW ((null),0,0x33f7e8,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x131a70)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x131a70)->(1,(nil)): Stub
wine: Unhandled page fault on read access to 0x017fc000 at address 0x7d4df8 (thread 0017), starting debugger...
Unhandled exception: page fault on read access to 0x017fc000 in 32-bit code (0x007d4df8).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:007d4df8 ESP:0033f298 EBP:00000000 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000000 EBX:00000000 ECX:0033f3f4 EDX:00000001
 ESI:017fbfff EDI:01711b43
Stack dump:
0x0033f298:  003f0118 00000013 0033f37c 00000023
0x0033f2a8:  00000000 0033f2f8 016701a4 7edf67e0
0x0033f2b8:  7edf67e0 016701a4 0167008c 44444353
0x0033f2c8:  44444444 1500b5d0 0033f3a8 3d442023
0x0033f2d8:  00000097 1500b5f0 00000000 1500b5d0
0x0033f2e8:  00000001 00000974 0000025d 003b1630
Backtrace:
=>1 0x007d4df8 (0x00000000)
0x007d4df8: movl	0x0(%esi),%eax
Modules:
Module	Address			Debug info	Name (112 modules)
PE	  400000-  6b4000	Deferred        diablo
PE	 13e0000- 13fa000	Deferred        smackw32
PE	10000000-10048000	Deferred        diabloui
PE	15000000-15041000	Deferred        storm
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c088000-7c097000	Deferred        libgcc_s.so.1
ELF	7c097000-7c0ac000	Deferred        midimap<elf>
  \-PE	7c0a0000-7c0ac000	\               midimap
ELF	7c0ac000-7c0d4000	Deferred        msacm32<elf>
  \-PE	7c0b0000-7c0d4000	\               msacm32
ELF	7c0d4000-7c124000	Deferred        libpulse.so.0
ELF	7c124000-7c1ec000	Deferred        libasound.so.2
ELF	7c1ec000-7c280000	Deferred        winmm<elf>
  \-PE	7c200000-7c280000	\               winmm
ELF	7c89e000-7c8b7000	Deferred        msacm32<elf>
  \-PE	7c8a0000-7c8b7000	\               msacm32
ELF	7c8b7000-7c8ee000	Deferred        winealsa<elf>
  \-PE	7c8c0000-7c8ee000	\               winealsa
ELF	7c8ee000-7c93a000	Deferred        dsound<elf>
  \-PE	7c900000-7c93a000	\               dsound
ELF	7ce3a000-7db7a000	Deferred        libglcore.so.1
ELF	7dcc5000-7dcce000	Deferred        librt.so.1
ELF	7de31000-7ded6000	Deferred        libgl.so.1
ELF	7ded6000-7dfeb000	Deferred        wined3d<elf>
  \-PE	7def0000-7dfeb000	\               wined3d
ELF	7e026000-7e02a000	Deferred        libcap.so.1
ELF	7e08e000-7e0e6000	Deferred        ddraw<elf>
  \-PE	7e0a0000-7e0e6000	\               ddraw
ELF	7e0e6000-7e0ea000	Deferred        libgpg-error.so.0
ELF	7e0ea000-7e153000	Deferred        libgcrypt.so.11
ELF	7e153000-7e165000	Deferred        libtasn1.so.3
ELF	7e165000-7e169000	Deferred        libkeyutils.so.1
ELF	7e169000-7e172000	Deferred        libkrb5support.so.0
ELF	7e172000-7e1a4000	Deferred        libcrypt.so.1
ELF	7e1a4000-7e241000	Deferred        libgnutls.so.26
ELF	7e241000-7e265000	Deferred        libk5crypto.so.3
ELF	7e265000-7e2f7000	Deferred        libkrb5.so.3
ELF	7e2f7000-7e321000	Deferred        libgssapi_krb5.so.2
ELF	7e321000-7e357000	Deferred        libcups.so.2
ELF	7e37b000-7e38f000	Deferred        libresolv.so.2
ELF	7e390000-7e397000	Deferred        libasound_module_pcm_pulse.so
ELF	7e39e000-7e3bd000	Deferred        iphlpapi<elf>
  \-PE	7e3a0000-7e3bd000	\               iphlpapi
ELF	7e3bd000-7e420000	Deferred        rpcrt4<elf>
  \-PE	7e3d0000-7e420000	\               rpcrt4
ELF	7e420000-7e4c6000	Deferred        ole32<elf>
  \-PE	7e430000-7e4c6000	\               ole32
ELF	7e4ee000-7e521000	Deferred        uxtheme<elf>
  \-PE	7e4f0000-7e521000	\               uxtheme
ELF	7e521000-7e52a000	Deferred        libxcursor.so.1
ELF	7e52a000-7e52f000	Deferred        libxfixes.so.3
ELF	7e52f000-7e533000	Deferred        libxcomposite.so.1
ELF	7e533000-7e53a000	Deferred        libxrandr.so.2
ELF	7e53a000-7e544000	Deferred        libxrender.so.1
ELF	7e544000-7e547000	Deferred        libxinerama.so.1
ELF	7e547000-7e568000	Deferred        imm32<elf>
  \-PE	7e550000-7e568000	\               imm32
ELF	7e568000-7e56d000	Deferred        libxdmcp.so.6
ELF	7e56d000-7e586000	Deferred        libxcb.so.1
ELF	7e586000-7e675000	Deferred        libx11.so.6
ELF	7e675000-7e684000	Deferred        libxext.so.6
ELF	7e684000-7e68a000	Deferred        libxxf86vm.so.1
ELF	7e68a000-7e6a2000	Deferred        libice.so.6
ELF	7e6a2000-7e6ab000	Deferred        libsm.so.6
ELF	7e6ab000-7e6ad000	Deferred        libnvidia-tls.so.1
ELF	7e6b6000-7e6ba000	Deferred        libcom_err.so.2
ELF	7e6ba000-7e755000	Deferred        winex11<elf>
  \-PE	7e6d0000-7e755000	\               winex11
ELF	7e77e000-7e7a5000	Deferred        libexpat.so.1
ELF	7e7a5000-7e7d2000	Deferred        libfontconfig.so.1
ELF	7e7e1000-7e7f7000	Deferred        libz.so.1
ELF	7e7f7000-7e86d000	Deferred        libfreetype.so.6
ELF	7e86d000-7e8d9000	Deferred        msvcrt<elf>
  \-PE	7e880000-7e8d9000	\               msvcrt
ELF	7e8d9000-7e8f3000	Deferred        crtdll<elf>
  \-PE	7e8e0000-7e8f3000	\               crtdll
ELF	7e8f3000-7e908000	Deferred        lz32<elf>
  \-PE	7e900000-7e908000	\               lz32
ELF	7e908000-7e923000	Deferred        version<elf>
  \-PE	7e910000-7e923000	\               version
ELF	7e923000-7e95a000	Deferred        winspool<elf>
  \-PE	7e930000-7e95a000	\               winspool
ELF	7e95a000-7ea08000	Deferred        comdlg32<elf>
  \-PE	7e960000-7ea08000	\               comdlg32
ELF	7ea08000-7eacd000	Deferred        comctl32<elf>
  \-PE	7ea10000-7eacd000	\               comctl32
ELF	7eacd000-7eb28000	Deferred        shlwapi<elf>
  \-PE	7eae0000-7eb28000	\               shlwapi
ELF	7eb28000-7ec3c000	Deferred        shell32<elf>
  \-PE	7eb40000-7ec3c000	\               shell32
ELF	7ec3c000-7ec8f000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec8f000	\               advapi32
ELF	7ec8f000-7ed2e000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed2e000	\               gdi32
ELF	7ed2e000-7ee7a000	Deferred        user32<elf>
  \-PE	7ed50000-7ee7a000	\               user32
ELF	7ee7a000-7ee93000	Deferred        libnsl.so.1
ELF	7ee93000-7ee9c000	Deferred        libnss_compat.so.2
ELF	7ee9d000-7eea0000	Deferred        libxcb-xlib.so.0
ELF	7efcb000-7eff1000	Deferred        libm.so.6
ELF	7eff1000-7eff4000	Deferred        libxau.so.6
ELF	7eff4000-7f000000	Deferred        libnss_files.so.2
ELF	b7c81000-b7c8c000	Deferred        libnss_nis.so.2
ELF	b7c90000-b7c94000	Deferred        libdl.so.2
ELF	b7c94000-b7df2000	Deferred        libc.so.6
ELF	b7df2000-b7e0b000	Deferred        libpthread.so.0
ELF	b7e1a000-b7f51000	Deferred        libwine.so.1
ELF	b7f53000-b7f70000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
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
00000016 (D) C:\Program Files\Diablo\Diablo.exe
	0000001d    1
	0000001c   15
	0000001b   15
	00000017    0 <==
00000018 
	00000019    0
Backtrace:
=>1 0x007d4df8 (0x00000000)
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

There is the output when I try to run it from the command line.  I'm using an Nvidia 5200 with the restricted drivers in Intrepid (173.xx I think is what they are.)

---

