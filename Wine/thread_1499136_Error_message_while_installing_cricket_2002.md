---
title: "Error message while installing cricket 2002"
date: 2010-06-01
forum: Wine
---

### Post by arnab_das on 2010-06-01
I have this really old game cricket 2002. when i run it i get the following message (if i run it from the terminal) and the game crashes:

```
$ wine Cricket2002.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32f644,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f730,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:quartz:AsyncReader_FindPin (L"Output", 0x62e1a4)
wine: Unhandled page fault on read access to 0x00000000 at address 0x7c59fc2c (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7c59fc2c).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7c59fc2c ESP:0032f81c EBP:0032fa44 EFLAGS:00010293(  R- --  I S -A- -C)
 EAX:00000001 EBX:7c610ff4 ECX:00000000 EDX:00000000
 ESI:0062e180 EDI:001b8600
Stack dump:
0x0032f81c:  001b3fe8 7bcb4f29 0032f934 f7596d04
0x0032f82c:  0032f848 7c5f6988 0032fa2c 7bcb4f29
0x0032f83c:  00000000 0032f848 000003de fbad8001
0x0032f84c:  7bcb4f29 7bcb4f29 7bcb4f29 7bcb4f29
0x0032f85c:  7bcb4f3f 7bcb5307 7bcb4f29 7bcb5307
0x0032f86c:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x7c59fc2c in quartz (+0x2fc2c) (0x0032fa44)
  1 0x00501678 in cricket2002 (+0x101677) (0x0062e19c)
  2 0x001b8600 (0x008aa07c)
  3 0x005566a4 in cricket2002 (+0x1566a3) (0x005566b8)
  4 0x00548a70 in cricket2002 (+0x148a6f) (0x005487c0)
  5 0x0c24548b (0x0424448b)
0x7c59fc2c: movl	0x0(%edx),%eax
Modules:
Module	Address			Debug info	Name (89 modules)
PE	  400000-  656000	Export          cricket2002
PE	78000000-78044000	Deferred        msvcrt
PE	780a0000-780b2000	Deferred        msvcirt
PE	780c0000-78121000	Deferred        msvcp60
ELF	7b800000-7b93a000	Deferred        kernel32<elf>
  \-PE	7b810000-7b93a000	\               kernel32
ELF	7bc00000-7bcb6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb6000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c2f5000-7c328000	Deferred        uxtheme<elf>
  \-PE	7c300000-7c328000	\               uxtheme
ELF	7c328000-7c387000	Deferred        shlwapi<elf>
  \-PE	7c340000-7c387000	\               shlwapi
ELF	7c387000-7c46d000	Deferred        oleaut32<elf>
  \-PE	7c3a0000-7c46d000	\               oleaut32
ELF	7c46d000-7c53b000	Deferred        comctl32<elf>
  \-PE	7c480000-7c53b000	\               comctl32
ELF	7c53b000-7c560000	Deferred        msvfw32<elf>
  \-PE	7c540000-7c560000	\               msvfw32
ELF	7c560000-7c613000	Export          quartz<elf>
  \-PE	7c570000-7c613000	\               quartz
ELF	7ca0b000-7ca53000	Deferred        dsound<elf>
  \-PE	7ca10000-7ca53000	\               dsound
ELF	7cba2000-7cbc8000	Deferred        msacm32<elf>
  \-PE	7cbb0000-7cbc8000	\               msacm32
ELF	7ccc6000-7e2d6000	Deferred        libglcore.so.1
ELF	7e2d6000-7e39b000	Deferred        libgl.so.1
ELF	7e3d0000-7e3da000	Deferred        libxcursor.so.1
ELF	7e3da000-7e3e0000	Deferred        libxfixes.so.3
ELF	7e3e0000-7e3e4000	Deferred        libxcomposite.so.1
ELF	7e3e4000-7e3ec000	Deferred        libxrandr.so.2
ELF	7e3ec000-7e3f6000	Deferred        libxrender.so.1
ELF	7e3f6000-7e3fc000	Deferred        libxxf86vm.so.1
ELF	7e3fc000-7e400000	Deferred        libxinerama.so.1
ELF	7e400000-7e421000	Deferred        imm32<elf>
  \-PE	7e410000-7e421000	\               imm32
ELF	7e421000-7e427000	Deferred        libxdmcp.so.6
ELF	7e427000-7e42b000	Deferred        libxau.so.6
ELF	7e42b000-7e445000	Deferred        libxcb.so.1
ELF	7e445000-7e44a000	Deferred        libuuid.so.1
ELF	7e44a000-7e567000	Deferred        libx11.so.6
ELF	7e567000-7e577000	Deferred        libxext.so.6
ELF	7e577000-7e590000	Deferred        libice.so.6
ELF	7e590000-7e599000	Deferred        libsm.so.6
ELF	7e5a0000-7e5a2000	Deferred        libnvidia-tls.so.1
ELF	7e5b8000-7e657000	Deferred        winex11<elf>
  \-PE	7e5d0000-7e657000	\               winex11
ELF	7e691000-7e6b8000	Deferred        libexpat.so.1
ELF	7e6b8000-7e6e8000	Deferred        libfontconfig.so.1
ELF	7e6e8000-7e6fd000	Deferred        libz.so.1
ELF	7e6fd000-7e773000	Deferred        libfreetype.so.6
ELF	7e792000-7e7a6000	Deferred        comm.drv16.so
PE	7e7a0000-7e7a6000	Deferred        comm.drv16
ELF	7e7a6000-7e7bb000	Deferred        system.drv16.so
PE	7e7b0000-7e7bb000	Deferred        system.drv16
ELF	7e7bb000-7e858000	Deferred        krnl386.exe16.so
PE	7e7d0000-7e858000	Deferred        krnl386.exe16
ELF	7e858000-7e891000	Deferred        dinput<elf>
  \-PE	7e860000-7e891000	\               dinput
ELF	7e891000-7e9c7000	Deferred        wined3d<elf>
  \-PE	7e8a0000-7e9c7000	\               wined3d
ELF	7e9c7000-7e9f6000	Deferred        d3d8<elf>
  \-PE	7e9d0000-7e9f6000	\               d3d8
ELF	7e9f6000-7ea7d000	Deferred        winmm<elf>
  \-PE	7ea00000-7ea7d000	\               winmm
ELF	7ea7d000-7eb07000	Deferred        gdi32<elf>
  \-PE	7ea90000-7eb07000	\               gdi32
ELF	7eb07000-7ec16000	Deferred        user32<elf>
  \-PE	7eb20000-7ec16000	\               user32
ELF	7ec16000-7ec87000	Deferred        rpcrt4<elf>
  \-PE	7ec20000-7ec87000	\               rpcrt4
ELF	7ec87000-7ece0000	Deferred        advapi32<elf>
  \-PE	7ec90000-7ece0000	\               advapi32
ELF	7ece0000-7eddc000	Deferred        ole32<elf>
  \-PE	7ed00000-7eddc000	\               ole32
ELF	7eddc000-7ee34000	Deferred        ddraw<elf>
  \-PE	7ede0000-7ee34000	\               ddraw
ELF	7ef98000-7efa4000	Deferred        libnss_files.so.2
ELF	7efa4000-7efbb000	Deferred        libnsl.so.1
ELF	7efbb000-7efe1000	Deferred        libm.so.6
ELF	7efe5000-7f000000	Deferred        dinput8<elf>
  \-PE	7eff0000-7f000000	\               dinput8
ELF	f74a5000-f74af000	Deferred        libnss_nis.so.2
ELF	f74b0000-f74b4000	Deferred        libdl.so.2
ELF	f74b4000-f760e000	Deferred        libc.so.6
ELF	f760f000-f7628000	Deferred        libpthread.so.0
ELF	f7628000-f7630000	Deferred        libnss_compat.so.2
ELF	f7647000-f7782000	Deferred        libwine.so.1
ELF	f7784000-f77a2000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\EA SPORTS\Cricket2002\Cricket2002.exe
	00000009    0 <==
0000000e services.exe
	0000001c    0
	00000017    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000018    0
	00000016    0
	00000013    0
	00000012    0
00000019 winedevice.exe
	0000001d    0
	0000001b    0
	0000001a    0
0000001e explorer.exe
	0000001f    0
Backtrace:
=>0 0x7c59fc2c in quartz (+0x2fc2c) (0x0032fa44)
  1 0x00501678 in cricket2002 (+0x101677) (0x0062e19c)
  2 0x001b8600 (0x008aa07c)
  3 0x005566a4 in cricket2002 (+0x1566a3) (0x005566b8)
  4 0x00548a70 in cricket2002 (+0x148a6f) (0x005487c0)
  5 0x0c24548b (0x0424448b)
```


plz help.

---

### Post by cogadh on 2010-06-01
Looks like the problem started in quartz.dll. Wine's version of that is not the greatest, so you should probably try installing the Windows version using [winetricks]("http://wiki.winehq.org/winetricks").

---

### Post by arnab_das on 2010-06-01
> **cogadh said:**
> Looks like the problem started in quartz.dll. Wine's version of that is not the greatest, so you should probably try installing the Windows version using [winetricks]("http://wiki.winehq.org/winetricks").

hey thanks for the help! installed winetricks. disabled alsa and oss audio drivers and mmdevapi and now i can at least see the first splash screen of the game! :)

but still getting the following error:

```
$ couldn't load main module (2)
Process of pid=0020 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001c    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000018    0
	00000017    0
	00000013    0
	00000012    0
00000019 winedevice.exe
	0000001d    0
	0000001b    0
	0000001a    0
00000022 explorer.exe
	00000023    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'
^C
$ 

```

and if i enable mmdevapi i get the following error:

```
$ couldn't load main module (2)
Process of pid=0020 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001c    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000018    0
	00000016    0
	00000013    0
	00000012    0
00000019 winedevice.exe
	0000001d    0
	0000001b    0
	0000001a    0
00000022 explorer.exe
	00000023    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'
^C

```

erm...some more help plz?

---

### Post by jejemon on 2010-06-02
I have encountered this error as well before when I installed FIFA 2002 under WINE. What I did to resolve the issue was reinstalling my WINE client using WINETRICKS. I am not really sure how did reinstalling the the WINE client resolved the issue but it did the trick. Looks like the issue is with the graphics card. Have you tried disabling the or using the builtin video card drivers for your graphics card? this could be a conflict with the video card drivers.

---

### Post by arnab_das on 2010-06-02
> **jejemon said:**
> I have encountered this error as well before when I installed FIFA 2002 under WINE. What I did to resolve the issue was reinstalling my WINE client using WINETRICKS. I am not really sure how did reinstalling the the WINE client resolved the issue but it did the trick. Looks like the issue is with the graphics card. Have you tried disabling the or using the builtin video card drivers for your graphics card? this could be a conflict with the video card drivers.

actually disabling my video card drivers makes the alignment of my desktop go haywire.

---

