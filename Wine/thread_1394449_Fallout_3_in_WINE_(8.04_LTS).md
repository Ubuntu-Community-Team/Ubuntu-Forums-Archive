---
title: "Fallout 3 in WINE (8.04 LTS)"
date: 2010-01-30
forum: Wine
---

### Post by DarkW0lf on 2010-01-30
The installer for both Fallout and the DLC's worked and I have everything in Fallout's Data folder (ie not games for windows)

But I get the following errors when trying to run either Fallout3.exe or FalloutLauncher.exe

This is the GOTY edition (don't know if it the most recent version because I haven't been able to run it yet.)

```

$ wine Fallout3.exe
err:module:import_dll Library MSASN1.dll (which is needed by L"C:\\windows\\system32\\xlive.dll") not found
err:module:import_dll Library xlive.dll (which is needed by L"C:\\Program_Files\\Bethesda_Softworks\\Fallout_3\\Fallout3.exe") not found
err:module:import_dll Library d3dx9_38.dll (which is needed by L"C:\\Program_Files\\Bethesda_Softworks\\Fallout_3\\Fallout3.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program_Files\\Bethesda_Softworks\\Fallout_3\\Fallout3.exe" failed, status c0000135

(after overrides for xlive.dll and d3dx9_38.dll)
$ wine Fallout3.exe
err:module:import_dll Library MSASN1.dll (which is needed by L"C:\\windows\\system32\\xlive.dll") not found
err:module:import_dll Library xlive.dll (which is needed by L"C:\\Program_Files\\Bethesda_Softworks\\Fallout_3\\Fallout3.exe") not found
Trying to load PE image for unsupported architecture (AMD-64)
err:module:import_dll Loading library d3dx9_38.dll (which is needed by L"C:\\Program_Files\\Bethesda_Softworks\\Fallout_3\\Fallout3.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program_Files\\Bethesda_Softworks\\Fallout_3\\Fallout3.exe" failed, status c0000135


$ wine FalloutLauncher.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program_Files\\Bethesda_Softworks\\Fallout_3\\FalloutLauncher.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program_Files\\Bethesda_Softworks\\Fallout_3\\FalloutLauncher.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program_Files\\Bethesda_Softworks\\Fallout_3\\FalloutLauncher.exe" failed, status c0000135

```

I saw another thread with a link for msasn1.dll so I can copy that to wine's folder but xlive.dll is already in the system32 folder but wine/Fallout can't find it apparently. I also tried setting an override for it and d3dx9_38.dll but they still can't be found. (Does wine use 32 or 64 bit dll's ?)

Would anyone also know about the Games for WIndows disabler [http://www.fallout3nexus.com/downloads/file.php?id=1086](http://www.fallout3nexus.com/downloads/file.php?id=1086)

The same thread had a link for that, would that help at all for any of the above errors ?

---

### Post by beastrace91 on 2010-01-30
Wine uses 32bit Windows dll - that being said after you copy said dlls over to your Wine's system32 folder be sure to set them to a native override in your Wine CFG

Also the errors thrown by the third launch there are related the M$ vc2005 run time libraries, install them through winetricks to get that working (hopefully)

Regards,
~Jeff

---

### Post by DarkW0lf on 2010-01-31
> **beastrace91 said:**
> Wine uses 32bit Windows dll - that being said after you copy said dlls over to your Wine's system32 folder be sure to set them to a native override in your Wine CFG


I asked because I thought it was the 32 bit version of d3dx9_38.dll that I copied to system32 folder and now it gives some sort of platform error. Neither that d3dx9_38.dll or xlive.dll are detected even though there is an override.

Do you mean (native only) or (native, builtin) ?
(I think somewhere I saw that xlive.dll had to be native only, not sure)

> 
Also the errors thrown by the third launch there are related the M$ vc2005 run time libraries, install them through winetricks to get that working (hopefully)


I typically avoid wine tricks, only for the sake of not having some strange install that might give me problems later. Would you know if either of those dll's are on either fallout dvd ?

It might not be such a big issue that error is for the launcher that I don't usually use (I don't use the Oblivion launcher either). Game launchers don't usually play nice in WINE. The only reason I would like to get it to work is so the game can manage the plugins for me. But if it becomes an issue I'll write the plugins.txt file myself like I did for Oblivion.

[edit]
Ah snooping around I found one of the threads I was looking at and I see that the VC2005 runtimes should be on the fallut dvd.
So that's all good just need to get the other errors fixed.
[/edit]

---

### Post by DarkW0lf on 2010-02-01
Warning lots of copious notes

```

$ wine /media/'Fallout 3'/G4WL/vcredist_x86.exe
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP001.TMP\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"sean" (nil) 0x33f7fc (nil) 0x33f800 0x33f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"sean" 0x133180 0x33f7fc 0x12f438 0x33f800 0x33f7f4 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly
err:msi:ITERATE_PublishAssembly Component not set for install, not publishing assembly

```

Just for completeness as I try to avoid launchers. The above errors are when I try to run the vc runtime installer in WINE.
Actually I don't understand why the game asks for the 2005 runtime when it comes with a newer version. (MSVCR90.dll, MSVCP90.dll)

```

(After installing d3dx9_38.dll from Jun2008_d3dx9_38_x86.cab)
$ wine Fallout3.exe
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F

Then Fallout3.exe tries to run the launcher and crashes with:
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x147aa0c,0x00000004,0x147aa08) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x14797f8): Stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugFlags
fixme:win:EnumDisplayDevicesW ((null),0,0x1479744,0x00000000), stub!
wine: Unhandled page fault on write access to 0x7ff72000 at address 0x6db8d4 (thread 0020), starting debugger...
Unhandled exception: page fault on write access to 0x7ff72000 in 32-bit code (0x006db8d4).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:006db8d4 ESP:0147adcc EBP:0147addc EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:ffffffff ECX:3fff3801 EDX:00000003
 ESI:7ff40000 EDI:7ff71ffe
Stack dump:
0x0147adcc:  0147ae10 00000000 7ff40006 48590000
0x0147addc:  0147b228 006c5bdc 7ff40006 ffffffff
0x0147adec:  00ccc784 00000000 0146d4a6 00c9b998
0x0147adfc:  00f26000 00000001 00000000 00032000
0x0147ae0c:  00000030 5c3f3f5c 756c6f56 307b656d
0x0147ae1c:  30303030 2d303030 30303030 3030302d
Backtrace:
=>1 0x006db8d4 in falloutlauncher (+0x2db8d4) (0x0147addc)
  2 0x006c5bdc in falloutlauncher (+0x2c5bdc) (0x0147b228)
  3 0x00669e21 in falloutlauncher (+0x269e21) (0x0148f890)
  4 0x005d72ba in falloutlauncher (+0x1d72ba) (0x0148fdbc)
  5 0x00d6641c in falloutlauncher (+0x96641c) (0x00a789be)
  6 0xc0850c24 (0x448bccc3)
0x006db8d4: repe stosl	%es:(%edi)
Modules:
Module	Address			Debug info	Name (90 modules)
PE	  400000-  f86000	Export          falloutlauncher
PE	78130000-781cb000	Deferred        msvcr80
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c420000-7c4a7000	Deferred        msvcp80
ELF	7cfb5000-7e050000	Deferred        libglcore.so.1
ELF	7e050000-7e10f000	Deferred        libgl.so.1
ELF	7e10f000-7e212000	Deferred        wined3d<elf>
  \-PE	7e120000-7e212000	\               wined3d
ELF	7e212000-7e242000	Deferred        d3d9<elf>
  \-PE	7e220000-7e242000	\               d3d9
ELF	7e28e000-7e2c1000	Deferred        uxtheme<elf>
  \-PE	7e290000-7e2c1000	\               uxtheme
ELF	7e2c1000-7e2d5000	Deferred        midimap<elf>
  \-PE	7e2d0000-7e2d5000	\               midimap
ELF	7e2d5000-7e2fb000	Deferred        msacm32<elf>
  \-PE	7e2e0000-7e2fb000	\               msacm32
ELF	7e2fb000-7e312000	Deferred        msacm32<elf>
  \-PE	7e300000-7e312000	\               msacm32
ELF	7e312000-7e3d5000	Deferred        libasound.so.2
ELF	7e3e7000-7e41d000	Deferred        winealsa<elf>
  \-PE	7e3f0000-7e41d000	\               winealsa
ELF	7e41d000-7e426000	Deferred        libxcursor.so.1
ELF	7e426000-7e42b000	Deferred        libxfixes.so.3
ELF	7e42b000-7e42e000	Deferred        libxcomposite.so.1
ELF	7e42e000-7e434000	Deferred        libxrandr.so.2
ELF	7e434000-7e43c000	Deferred        libxrender.so.1
ELF	7e43c000-7e43f000	Deferred        libxinerama.so.1
ELF	7e43f000-7e45f000	Deferred        imm32<elf>
  \-PE	7e450000-7e45f000	\               imm32
ELF	7e45f000-7e464000	Deferred        libxdmcp.so.6
ELF	7e464000-7e47c000	Deferred        libxcb.so.1
ELF	7e47c000-7e47e000	Deferred        libxcb-xlib.so.0
ELF	7e47e000-7e481000	Deferred        libxau.so.6
ELF	7e481000-7e568000	Deferred        libx11.so.6
ELF	7e568000-7e576000	Deferred        libxext.so.6
ELF	7e576000-7e57b000	Deferred        libxxf86vm.so.1
ELF	7e589000-7e58b000	Deferred        libnvidia-tls.so.1
ELF	7e58d000-7e624000	Deferred        winex11<elf>
  \-PE	7e5a0000-7e624000	\               winex11
ELF	7e63e000-7e65f000	Deferred        libexpat.so.1
ELF	7e65f000-7e689000	Deferred        libfontconfig.so.1
ELF	7e69b000-7e6b0000	Deferred        libz.so.1
ELF	7e6b0000-7e71d000	Deferred        libfreetype.so.6
ELF	7e71d000-7e749000	Deferred        ws2_32<elf>
  \-PE	7e720000-7e749000	\               ws2_32
ELF	7e749000-7e763000	Deferred        wsock32<elf>
  \-PE	7e750000-7e763000	\               wsock32
ELF	7e763000-7e7ad000	Deferred        dsound<elf>
  \-PE	7e770000-7e7ad000	\               dsound
ELF	7e7ad000-7e7c1000	Deferred        lz32<elf>
  \-PE	7e7b0000-7e7c1000	\               lz32
ELF	7e7c1000-7e7da000	Deferred        version<elf>
  \-PE	7e7d0000-7e7da000	\               version
ELF	7e7da000-7e844000	Deferred        msvcrt<elf>
  \-PE	7e7f0000-7e844000	\               msvcrt
ELF	7e844000-7e857000	Deferred        libresolv.so.2
ELF	7e857000-7e875000	Deferred        iphlpapi<elf>
  \-PE	7e860000-7e875000	\               iphlpapi
ELF	7e875000-7e8d6000	Deferred        rpcrt4<elf>
  \-PE	7e880000-7e8d6000	\               rpcrt4
ELF	7e8d6000-7e97a000	Deferred        ole32<elf>
  \-PE	7e8e0000-7e97a000	\               ole32
ELF	7e97a000-7ea39000	Deferred        comctl32<elf>
  \-PE	7e980000-7ea39000	\               comctl32
ELF	7ea39000-7ea92000	Deferred        shlwapi<elf>
  \-PE	7ea50000-7ea92000	\               shlwapi
ELF	7ea92000-7eba5000	Deferred        shell32<elf>
  \-PE	7eaa0000-7eba5000	\               shell32
ELF	7eba5000-7ebf7000	Deferred        advapi32<elf>
  \-PE	7ebb0000-7ebf7000	\               advapi32
ELF	7ebf7000-7ec92000	Deferred        gdi32<elf>
  \-PE	7ec10000-7ec92000	\               gdi32
ELF	7ec92000-7edd9000	Deferred        user32<elf>
  \-PE	7ecb0000-7edd9000	\               user32
ELF	7edd9000-7ee6b000	Deferred        winmm<elf>
  \-PE	7ede0000-7ee6b000	\               winmm
ELF	7ee6b000-7ee76000	Deferred        libnss_files.so.2
ELF	7ee76000-7ee8e000	Deferred        libnsl.so.1
ELF	7ee8e000-7ee97000	Deferred        libnss_compat.so.2
ELF	7efc9000-7efee000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	f7c66000-f7c6a000	Deferred        libdl.so.2
ELF	f7c6a000-f7db9000	Deferred        libc.so.6
ELF	f7dba000-f7dd2000	Deferred        libpthread.so.0
ELF	f7de4000-f7f1a000	Deferred        libwine.so.1
ELF	f7f1c000-f7f3b000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000022    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
0000001d 
	0000001e    0
0000001f (D) C:\Program_Files\Bethesda_Softworks\Fallout_3\FalloutLauncher.exe
	00000020    0 <==
Backtrace:
=>1 0x006db8d4 in falloutlauncher (+0x2db8d4) (0x0147addc)
  2 0x006c5bdc in falloutlauncher (+0x2c5bdc) (0x0147b228)
  3 0x00669e21 in falloutlauncher (+0x269e21) (0x0148f890)
  4 0x005d72ba in falloutlauncher (+0x1d72ba) (0x0148fdbc)
  5 0x00d6641c in falloutlauncher (+0x96641c) (0x00a789be)
  6 0xc0850c24 (0x448bccc3)

```

I made sure to have the 32 bit dll this time and I get hundreds of the getColorBits errors, each with a different format in question. Then the whole thing crashes and for some reason Fallout3.exe then tries to run the launcher, which crashes with that backtrace. (Note I did not run FalloutLauncher.exe , the Fallout3.exe program did.)

I tried to run the DirectX installer from the disc but it fails.

```

(When running geck.exe also lists getColorBits Unsupported format errors)
fixme:d3d_surface:flush_to_framebuffer_drawpixels >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 1180
fixme:d3d_surface:flush_to_framebuffer_drawpixels >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer(GL_BACK) @ surface.c / 1256

(When trying to preview heads in G.E.C.K. it crashes with below)
err:listview:LISTVIEW_WindowProc unknown msg 0400 wp=00000000 lp=00000000
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface MultisampleQuality set to -1, bstituting 0
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface MultisampleQuality set to -1, bstituting 0
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface MultisampleQuality set to -1, bstituting 0
wine: Unhandled exception 0x40000015 at address 0xf7db0023:0x00bc630f (thread 0009), starting debugger...
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
0000001d 
	0000001e    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'

```

I also played with the G.E.C.K. a little, it installed just fine but has the same getColorBits errors and the additional d3d:surface fixme's.

GECK crashes when trying to render models with that backtrace.

[edit]
I also attached the DirectX installer logs
[/edit]

---

### Post by gsmanners on 2010-02-01
What version of Wine? The AppDB says you need 1.1.33 or newer. That means you need to not be using the repo version for sure.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322)

---

### Post by DarkW0lf on 2010-02-06
Repo version 1.0.0.1 (I think?)

Which repo has 1.1.33 or newer ?
I know that I can force synaptic to install certain version but most instructions seem to be for installing older software, how can I instruct Synaptic to install a new version.

(for instance, the hardy backport for wine is still 1.0.0.1 Isn't the backports supposed to be "new" software ?)

[edit]
Almost forgot,
Anyone have a md5sum of the 1.7 US patch.
Zenimax in their great and finite wisdom decided to halt distrib of patch just so they have the bandwidth for a damn trailer of a new game. So the only downloads were from crappy shareware sites (two required subscriptions, one paid), I'd like to check the patch.
[/edit]

---

### Post by gsmanners on 2010-02-06
The latest version (as the sticky thread informs you) is available as shown here:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

EDIT: About the patch:

```
0fa90d24fc17ffeb7ee8c41f19a30ba9  FalloutUpdate.exe
54179488 2009-07-28 09:23 FalloutUpdate.exe
```

1.7 may come back at some point so here's the link for anyone else wondering: [http://fallout.bethsoft.com/eng/downloads/updates.html](http://fallout.bethsoft.com/eng/downloads/updates.html)

---

### Post by DarkW0lf on 2010-02-25
Well 1.1.38 has the same issues and broke Oblivion.
(And thanks for the RTFM post)

I still get the getColorBits() errors when trying to run Fallout or GECK.
For Oblivion it broke audio (ALSA pcm underrun ??) and ran real slow.

Patch md5 did match, is 1.7 really a year old ? (6 months?)
(PC in question is not connected to net so could only download 1.1.38 deb)

---

### Post by gsmanners on 2010-02-25
I think that bug you've noticed in Oblivion has been reported.

[http://bugs.winehq.org/show_bug.cgi?id=21609](http://bugs.winehq.org/show_bug.cgi?id=21609)

Might try reverting to 1.1.36 and see how that works. [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

I was fairly prompt about getting that patch. It was officially released on the 26th of July last year.

[http://fallout.wikia.com/wiki/Fallout_3_patch_1.7](http://fallout.wikia.com/wiki/Fallout_3_patch_1.7)

---

### Post by DarkW0lf on 2010-02-27
I don't see how reverting will help the Fallout issues since they remain in the 1.1.38 version (unless it's fixed in 1.1.39)

I might try to see how Oblivion runs in 1.1.36 but I don't mind the performance as it is in 1.0.0.1 (it runs pretty well, just some issues with some game internals)

That bug report seems to match but doesnt mention the slow down (frame rate?) I also get. No mention of a fix other then to revert back.

My major issue however is with Fallout 3 reporting the getColorBits() errors. There doesn't seem to be a version with a fix for this.

[http://bugs.winehq.org/show_bug.cgi?id=16087](http://bugs.winehq.org/show_bug.cgi?id=16087)

I also don't know if it is the 1.7 patch or the 1.1.38 wine but it now reports some error with securom before the getColorBits() . But it goes by too fast and redirecting to a file with > gives me a blank txt file.
(Lately I have noticed that the terminal doesn't seem to like redirects anymore and I usually have to end up piping through tee -a instead).
But I think I have noticed some error or fixme about numerating the drive and thing a box telling me it can't find the disc (which is actually an iso). I had been getting a similar error from C&C Generals (uses a cd key) but that I think is different than whatever Fallout is now doing.

---

### Post by gsmanners on 2010-03-01
At this point, I think your technical problems are Fallout 3/Gamebryo issues. See the following threads for more information:

[http://www.bethsoft.com/bgsforums/index.php?showtopic=892715](http://www.bethsoft.com/bgsforums/index.php?showtopic=892715)
[http://www.bethsoft.com/bgsforums/index.php?showtopic=890373](http://www.bethsoft.com/bgsforums/index.php?showtopic=890373)

In particular, make sure your hardware meets the minimum requirements.

---

### Post by DarkW0lf on 2010-03-01
Well that was useless...

Bethesda forum won't even let me search for "getColorBits()" some damn crap about the menu being disabled or not logged in (damn crappy forum software).

> 
Minimum System Requirements:

Windows XP/Vista
1GB System RAM (XP)/ 2GB System RAM (Vista)
2.4 Ghz Intel Pentium 4 or equivalent processor
Direct X 9.0c compliant video card with 256MB RAM (NVIDIA 6800 or better/ATI X850 or better)

Recommended System Requirements:

Intel Core 2 Duo processor
2 GB System RAM
Direct X 9.0c compliant video card with 512MB RAM (NVIDIA 8800 series, ATI 3800 series) 


My system is dual-core (AMD not intel) 1.7 MHz
There is 2 GB of ram
The video card is Dx9 able and has somewhere between 128 and 512 MB
(I saw between because nvidia-settings reports a higher number than BIOS)
NVidia Geforce Go 6150 (or 6100, nvidia-settings reports a different value than product specs).

Oblivion runs fine with this notebook (or near fine).
Only issues are Bethesda related (some objects don't render right and I got two big exclamation points in SI for some reason).

I never put much stock in minimum requirements.
I haven't for twenty years, because for twenty years they have been wrong.

[edit]
And that damn securom support site for fallout 3 won't load.
It just sits there telling me I'll "be redirected shortly".
Why do people insist on this bullcrap scripting all the time.
[/edit]

---

### Post by gsmanners on 2010-03-02
> **DarkW0lf said:**
> The video card is Dx9 able and has somewhere between 128 and 512 MB
(I saw between because nvidia-settings reports a higher number than BIOS)
NVidia Geforce Go 6150 (or 6100, nvidia-settings reports a different value than product specs).

I'm not surprised Fallout 3 won't run on that. The lowest 6xxx card it will run on is a 6800 (which is roughly the same power as a 7600 or a 9400). On the other hand, Oblivion should run just fine on that card.

---

### Post by DarkW0lf on 2010-03-08
Fallout has nearly identical sysreqs to Oblivion.
I don't see why there would be any issue.

The retail box for Fallout 3 GOTY:

RAM 1GB
CPU 2.4GHz
NVIDIA 6800

Retail for Oblivion GOTY:
RAM 512MB/1GB
CPU 2/3 GHZ
NVIDIA 6800

My SYSTEM:
RAM 2GB
CPU 1.7 GHz Dual Core
NVIDIA 6150 (DX9 able)

What is missing that Fallout does not like ?
In other words why does a 6100/6150 not fit the bill ?
This card is good for Oblivion and Fallout uses same the Gamebryo engine.

---

### Post by DarkW0lf on 2010-03-08
>

---

### Post by gsmanners on 2010-03-08
Fallout 3 and Oblivion do indeed use the same Gamebryo engine, but not the same version. The newer lighting and particle effects require the substantial improvement in GPU power that you see in the 6800 and later.

With Fallout 3, the 6800 is barely able to render scenes. With Oblivion, the 6800 is overkill.

---

### Post by DarkW0lf on 2010-06-25
Well I had to use the factory image of windows to examine some other issues. While I had it on the drive (I have two drives for this laptop, long story) I went ahead and installed fallout to see what vista would do with this hardware.

It works and after some ini tweaking it isn't too bad, alot like oblivion's performance.

Once again min reqs are crap. Now to figure out why WINE or VB doesn't like it. The only thing Vista couldn't do was run the installer for the DLC (oh well I'll copy that from the Linux drive).

---

