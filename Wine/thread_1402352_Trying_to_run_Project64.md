---
title: "Trying to run Project64"
date: 2010-02-09
forum: Wine
---

### Post by anthony62490 on 2010-02-09
Using Wine version 1.1.37
Ubuntu Jaunty
Wine running as WinXP

Okay, trying to get Project 64 v1.6 (Nintendo64 emulator) running. I was originally attempting to run it under Wine 1.0.1. I downloaded and installed the .exe like normal. When I attempted to run it for the first time, it asked for a language setting and then promptly sent back an error after I clicked OK. 
I decided to update wine. I enabled the Ubuntu Jaunty repository and ran the update. No visible changes, but I am still getting the error message immediately after running the program. An image of the message is attached. Also tried removing Project 64 and installing again, but now the installation brings up the error message as well.

```
anthony@anthony-desktop:~/.wine/dosdevices/c:/Program Files/Project64 1.6$ wine Project64.exe 
fixme:d3d_caps:wined3d_guess_vendor Received unrecognized GL_VENDOR "Eric Anholt". Returning VENDOR_WINE.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f0ec,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:context_create >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexEnvf(GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_COMBINE_EXT); @ context.c / 1413
wine: Unhandled page fault on write access to 0x5bf611f0 at address 0xb7e1e8aa (thread 0009), starting debugger...

```
At this point, the error message pops up. After clicking OK, the output resumes...
```

Unhandled exception: page fault on write access to 0x5bf611f0 in 32-bit code (0xb7e1e8aa).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7e1e8aa ESP:0032f44c EBP:0032f498 EFLAGS:00010257(  R- --  I  Z-A-P-C)
 EAX:7d340d20 EBX:7d060ff4 ECX:00000000 EDX:7c4b4618
 ESI:7c4b4800 EDI:5bf611f0
Stack dump:
0x0032f44c:  7ce6b042 5bf611f0 7c4b4800 00000001
0x0032f45c:  00001909 00000001 00000001 00000000
0x0032f46c:  00001909 00001401 0032f58b 7d361a30
0x0032f47c:  7d2e6ea8 7c4b4708 00001909 da40ba00
0x0032f48c:  7d060ff4 7d354e88 7c4b4708 0032f4f8
0x0032f49c:  7ceeee22 7d354e88 00000de1 00000000
Backtrace:
=>0 0xb7e1e8aa memcpy+0x5a() in libc.so.6 (0x0032f498)
  1 0x7ceeee22 _mesa_TexImage2D+0x2a2() in sis_dri.so (0x0032f4f8)
  2 0x7d12f65e in wined3d (+0x3f65e) (0x0032f598)
  3 0x7d13fe69 in wined3d (+0x4fe69) (0x0032f648)
  4 0x7d235bdc in d3d8 (+0x15bdc) (0x0032f6c8)
  5 0x7d236b84 in d3d8 (+0x16b84) (0x0032f708)
err:dbghelp_msc:pe_load_debug_directory Got a page fault while loading symbols
  6 0x008956be in jabo_direct3d8 (+0x56be) (0x0032f79c)
  7 0x00000280 (0x00000016)
  8 0x00000000 (0x00000000)
0xb7e1e8aa memcpy+0x5a in libc.so.6: movsb	(%esi),%es:(%edi)
Modules:
Module	Address			Debug info	Name (119 modules)
PE	  400000-  554000	Deferred        project64
PE	  890000-  930000	Export          jabo_direct3d8
ELF	7b800000-7b93a000	Deferred        kernel32<elf>
  \-PE	7b810000-7b93a000	\               kernel32
ELF	7bc00000-7bcb5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb5000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ce3c000-7d07c000	Export          sis_dri.so
ELF	7d07c000-7d086000	Deferred        libdrm.so.2
ELF	7d086000-7d0e9000	Deferred        libgl.so.1
ELF	7d0e9000-7d21b000	Export          wined3d<elf>
  \-PE	7d0f0000-7d21b000	\               wined3d
ELF	7d21b000-7d249000	Export          d3d8<elf>
  \-PE	7d220000-7d249000	\               d3d8
ELF	7d383000-7d387000	Deferred        libgpg-error.so.0
ELF	7d387000-7d3f0000	Deferred        libgcrypt.so.11
ELF	7d3f0000-7d402000	Deferred        libtasn1.so.3
ELF	7d402000-7d418000	Deferred        libresolv.so.2
ELF	7d418000-7d43c000	Deferred        libk5crypto.so.3
ELF	7d43c000-7d4ce000	Deferred        libkrb5.so.3
ELF	7d4ce000-7d56b000	Deferred        libgnutls.so.26
ELF	7de04000-7de07000	Deferred        libxdamage.so.1
ELF	7de07000-7de10000	Deferred        libkrb5support.so.0
ELF	7de10000-7de3b000	Deferred        libgssapi_krb5.so.2
ELF	7de3b000-7de72000	Deferred        libcups.so.2
ELF	7ded3000-7df06000	Deferred        uxtheme<elf>
  \-PE	7dee0000-7df06000	\               uxtheme
ELF	7df06000-7df1b000	Deferred        midimap<elf>
  \-PE	7df10000-7df1b000	\               midimap
ELF	7df1b000-7df41000	Deferred        msacm32<elf>
  \-PE	7df20000-7df41000	\               msacm32
ELF	7df41000-7df5a000	Deferred        msacm32<elf>
  \-PE	7df50000-7df5a000	\               msacm32
ELF	7df5a000-7df60000	Deferred        libattr.so.1
ELF	7df60000-7df67000	Deferred        libgdbm.so.3
ELF	7df67000-7df6c000	Deferred        libcap.so.2
ELF	7df6c000-7dfcb000	Deferred        libpulse.so.0
ELF	7dfcb000-7e093000	Deferred        libasound.so.2
ELF	7e095000-7e099000	Deferred        libkeyutils.so.1
ELF	7e0a2000-7e0a6000	Deferred        libcom_err.so.2
ELF	7e0a6000-7e0dd000	Deferred        winealsa<elf>
  \-PE	7e0b0000-7e0dd000	\               winealsa
ELF	7e0dd000-7e0e6000	Deferred        libxcursor.so.1
ELF	7e0e6000-7e0eb000	Deferred        libxfixes.so.3
ELF	7e0eb000-7e0ef000	Deferred        libxcomposite.so.1
ELF	7e0ef000-7e0f7000	Deferred        libxrandr.so.2
ELF	7e0f7000-7e101000	Deferred        libxrender.so.1
ELF	7e101000-7e107000	Deferred        libxxf86vm.so.1
ELF	7e107000-7e10a000	Deferred        libxinerama.so.1
ELF	7e10a000-7e12b000	Deferred        imm32<elf>
  \-PE	7e110000-7e12b000	\               imm32
ELF	7e12b000-7e130000	Deferred        libxdmcp.so.6
ELF	7e130000-7e14a000	Deferred        libxcb.so.1
ELF	7e14a000-7e14e000	Deferred        libxau.so.6
ELF	7e14e000-7e23d000	Deferred        libx11.so.6
ELF	7e23d000-7e24d000	Deferred        libxext.so.6
ELF	7e24d000-7e265000	Deferred        libice.so.6
ELF	7e265000-7e26e000	Deferred        libsm.so.6
ELF	7e26f000-7e276000	Deferred        libasound_module_pcm_pulse.so
ELF	7e276000-7e27f000	Deferred        librt.so.1
ELF	7e281000-7e321000	Deferred        winex11<elf>
  \-PE	7e290000-7e321000	\               winex11
ELF	7e321000-7e335000	Deferred        mouse.drv16.so
PE	7e330000-7e335000	Deferred        mouse.drv16
ELF	7e335000-7e34a000	Deferred        keyboard.drv16.so
PE	7e340000-7e34a000	Deferred        keyboard.drv16
ELF	7e34a000-7e35f000	Deferred        display.drv16.so
PE	7e350000-7e35f000	Deferred        display.drv16
ELF	7e35f000-7e382000	Deferred        mpr<elf>
  \-PE	7e370000-7e382000	\               mpr
ELF	7e382000-7e3c4000	Deferred        user.exe16.so
PE	7e390000-7e3c4000	Deferred        user.exe16
ELF	7e425000-7e44c000	Deferred        libexpat.so.1
ELF	7e44c000-7e479000	Deferred        libfontconfig.so.1
ELF	7e479000-7e48f000	Deferred        libz.so.1
ELF	7e48f000-7e506000	Deferred        libfreetype.so.6
ELF	7e506000-7e50b000	Deferred        libuuid.so.1
ELF	7e519000-7e544000	Deferred        gdi.exe16.so
PE	7e520000-7e544000	Deferred        gdi.exe16
ELF	7e544000-7e558000	Deferred        comm.drv16.so
PE	7e550000-7e558000	Deferred        comm.drv16
ELF	7e558000-7e56d000	Deferred        system.drv16.so
PE	7e560000-7e56d000	Deferred        system.drv16
ELF	7e56d000-7e60c000	Deferred        krnl386.exe16.so
PE	7e580000-7e60c000	Deferred        krnl386.exe16
ELF	7e60c000-7e6f0000	Deferred        oleaut32<elf>
  \-PE	7e620000-7e6f0000	\               oleaut32
ELF	7e6f0000-7e7ef000	Deferred        ole32<elf>
  \-PE	7e710000-7e7ef000	\               ole32
ELF	7e7ef000-7e825000	Deferred        winspool<elf>
  \-PE	7e800000-7e825000	\               winspool
ELF	7e825000-7e883000	Deferred        shlwapi<elf>
  \-PE	7e830000-7e883000	\               shlwapi
ELF	7e883000-7ea13000	Deferred        shell32<elf>
  \-PE	7e890000-7ea13000	\               shell32
ELF	7ea13000-7eabf000	Deferred        comdlg32<elf>
  \-PE	7ea20000-7eabf000	\               comdlg32
ELF	7eabf000-7eb8f000	Deferred        comctl32<elf>
  \-PE	7ead0000-7eb8f000	\               comctl32
ELF	7eb8f000-7ec00000	Deferred        rpcrt4<elf>
  \-PE	7eba0000-7ec00000	\               rpcrt4
ELF	7ec00000-7ec58000	Deferred        advapi32<elf>
  \-PE	7ec10000-7ec58000	\               advapi32
ELF	7ec58000-7ece2000	Deferred        gdi32<elf>
  \-PE	7ec60000-7ece2000	\               gdi32
ELF	7ece2000-7edf1000	Deferred        user32<elf>
  \-PE	7ecf0000-7edf1000	\               user32
ELF	7edf1000-7ee78000	Deferred        winmm<elf>
  \-PE	7ee00000-7ee78000	\               winmm
ELF	7efa2000-7efae000	Deferred        libnss_files.so.2
ELF	7efae000-7efc7000	Deferred        libnsl.so.1
ELF	7efc7000-7efed000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d96000-b7d9f000	Deferred        libnss_compat.so.2
ELF	b7da1000-b7da5000	Deferred        libdl.so.2
ELF	b7da5000-b7f08000	Export          libc.so.6
ELF	b7f08000-b7f21000	Deferred        libpthread.so.0
ELF	b7f34000-b8070000	Deferred        libwine.so.1
ELF	b8072000-b8090000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Project64 1.6\Project64.exe
	00000009    0 <==
0000000e services.exe
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000018 explorer.exe
	00000019    0
Backtrace:
=>0 0xb7e1e8aa memcpy+0x5a() in libc.so.6 (0x0032f498)
  1 0x7ceeee22 _mesa_TexImage2D+0x2a2() in sis_dri.so (0x0032f4f8)
  2 0x7d12f65e in wined3d (+0x3f65e) (0x0032f598)
  3 0x7d13fe69 in wined3d (+0x4fe69) (0x0032f648)
  4 0x7d235bdc in d3d8 (+0x15bdc) (0x0032f6c8)
  5 0x7d236b84 in d3d8 (+0x16b84) (0x0032f708)
  6 0x008956be in jabo_direct3d8 (+0x56be) (0x0032f79c)
  7 0x00000280 (0x00000016)
  8 0x00000000 (0x00000000)

```

---

### Post by asdfoo on 2010-03-12
> **anthony62490 said:**
> Using Wine version 1.1.37
Ubuntu Jaunty
Wine running as WinXP

Okay, trying to get Project 64 v1.6 (Nintendo64 emulator) running. I was originally attempting to run it under Wine 1.0.1. I downloaded and installed the .exe like normal. When I attempted to run it for the first time, it asked for a language setting and then promptly sent back an error after I clicked OK. 
I decided to update wine. I enabled the Ubuntu Jaunty repository and ran the update. No visible changes, but I am still getting the error message immediately after running the program. An image of the message is attached. Also tried removing Project 64 and installing again, but now the installation brings up the error message as well.

```
anthony@anthony-desktop:~/.wine/dosdevices/c:/Program Files/Project64 1.6$ wine Project64.exe 
fixme:d3d_caps:wined3d_guess_vendor Received unrecognized GL_VENDOR "Eric Anholt". Returning VENDOR_WINE.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f0ec,0x00000000), Backtrace:
=>0 0xb7e1e8aa memcpy+0x5a() in libc.so.6 (0x0032f498)
  1 0x7ceeee22 _mesa_TexImage2D+0x2a2() in sis_dri.so (0x0032f4f8)
  2 0x7d12f65e in wined3d (+0x3f65e) (0x0032f598)
  3 0x7d13fe69 in wined3d (+0x4fe69) (0x0032f648)
  4 0x7d235bdc in d3d8 (+0x15bdc) (0x0032f6c8)
  5 0x7d236b84 in d3d8 (+0x16b84) (0x0032f708)
  6 0x008956be in jabo_direct3d8 (+0x56be) (0x0032f79c)
  7 0x00000280 (0x00000016)
  8 0x00000000 (0x00000000)

```

The crash is in Mesa, not Wine.
You should look at upgrading to latest mesa/dri drivers, if the crash still occurs with reference to mesa, you may need to report the bug to them.

---

