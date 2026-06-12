---
title: "Zero Online"
date: 2009-05-21
forum: Wine
---

### Post by Drianos on 2009-05-21
Just wondering if someone have manage to play this game through wine , cedega, crossover or playonlinux. This company also create Conquer Online, ,there are some ppl that have manage to run this one ( [http://ubuntuforums.org/showthread.php?t=783616](http://ubuntuforums.org/showthread.php?t=783616) ) and they are almost the same game.
Page: 
[http://zo.91.com/](http://zo.91.com/)
Client:
[http://zo.91.com/download/client.shtml](http://zo.91.com/download/client.shtml)

And if you can explain the process will be great:p, since i am not a big expert.

---

### Post by Drianos on 2009-05-24
have someone atleast play it?

---

### Post by asdfoo on 2009-05-24
how about you try it and tell us how far you get...

---

### Post by Drianos on 2009-05-24
> **asdfoo said:**
> how about you try it and tell us how far you get...

iam not a expert in making work programs, i have try it with wine ,cedega, playonlinux and crossover. There is no problem in the installation, the problem is that the game doesnt open?

---

### Post by NightMKoder on 2009-05-25
Yea...I'm not downloading a gig (i dont have enough space, hehe).

Post your terminal output from running wine zo.exe or whatever its called and we can point you in the right direction.

---

### Post by Drianos on 2009-05-25
ok, I installed on windows then move all the file to ubuntu so the game is in the last version, since before running it you have to go throw a autopatch. This is what i get:

adrian@adrian-desktop:~/ZeroOnline$  wine play.exe 
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\adrian\\ZeroOnline\\play.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\adrian\\ZeroOnline\\play.exe" failed, status c0000135

so i search for MFC42.DLL an put it in windows system32 and then this happen

adrian@adrian-desktop:~/ZeroOnline$ wine play.exe 
fixme:shdocvw:PersistMemory_Load (0x142300)->(0x40d064 9c)
fixme:shdocvw:OleControl_FreezeEvents (0x142300)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x142300)->(0)
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32bba4
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
fixme:iphlpapi:NotifyAddrChange (Handle 0x218e888, overlapped 0x218e890): stub
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[1bfb70]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1423a0)->((null) 1 0x32c13c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1423a0)->((null) 25 2 0x32c150 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1423a0)->((null) 26 2 0x32c150 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1423a0)->(0x32c18c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1423a0)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32c260 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1a8da0)->(L"" L"" 0 0x32c298)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1423a0)->((null) 29 2 0x32df74 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1423a0)
fixme:shdocvw:ClientSite_GetContainer (0x1423a0)->(0x32dd90)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1423a0)->(0xb7f79051)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1423a0)->((null) 25 2 0x32dcc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1423a0)->((null) 26 2 0x32dcc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1423a0)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1423a0)->((null) 28 2 0x32e9f0 (nil))
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
0[1bfb70]: NPN Logging Active!
0[1bfb70]: General Plugin Logging Active! (nsPluginHostImpl::ctor)
0[1bfb70]: NPP Logging Active!
0[1bfb70]: nsPluginHostImpl::ctor



this is just the autorun, in the autorun i click enter (to open the game) and this lines follow the ones I just put:

fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x142300)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x1be3d0)->((nil))
fixme:shdocvw:OleObject_Close (0x142300)->(1)
fixme:shell:DllCanUnloadNow stub
adrian@adrian-desktop:~/ZeroOnline$ fixme:win:EnumDisplayDevicesW ((null),0,0x33b62c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33b628,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
wine: Unhandled page fault on read access to 0x00000000 at address 0x780cb6 (thread 0046), starting debugger...

---

### Post by Drianos on 2009-05-25
and the game music start but the windows freezes and it is in a black transparent color and a wine windows appear saying that program ZeroOnline Exe has encounter a serious problem and need to close. So i closed and this appear 

Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00780cb6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00780cb6 ESP:0033d650 EBP:0033d674 EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000000 EBX:0054fa90 ECX:00921930 EDX:7e9a4934
 ESI:00000000 EDI:000000fc
Stack dump:
0x0033d650:  00000000 0054fafa 023aaa18 000000fc
0x0033d660:  0054fa90 00000007 7bc3445f 6c240b68
0x0033d670:  023aaa18 0033d6f8 6c17206f 00000000
0x0033d680:  000001e6 000000fc 008d0738 023aaa18
0x0033d690:  7e989ff4 00000000 00000000 00000000
0x0033d6a0:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x00780cb6 in zeroonline (+0x380cb6) (0x0033d674)
  1 0x6c17206f in mfc42 (+0x206f) (0x0033d6f8)
  2 0x6c171cea in mfc42 (+0x1cea) (0x0033d718)
  3 0x005a32e3 in zeroonline (+0x1a32e3) (0x0033f57c)
  4 0x6c171c73 in mfc42 (+0x1c73) (0x0033f5dc)
  5 0x6c171bfb in mfc42 (+0x1bfb) (0x0033f5f8)
  6 0x6c171bba in mfc42 (+0x1bba) (0x0033f624)
  7 0x7ec64f2a WINPROC_wrapper+0x1a() in user32 (0x0033f654)
  8 0x7ec6537a WINPROC_wrapper+0x46a() in user32 (0x0033f694)
  9 0x7ec681a5 in user32 (+0xb81a5) (0x0033fb64)
  10 0x7ec6a73e in user32 (+0xba73e) (0x0033fba4)
  11 0x7ec298b6 DispatchMessageW+0x96() in user32 (0x0033fbe4)
  12 0x7ebf5919 IsDialogMessageW+0x129() in user32 (0x0033fd64)
  13 0x7ec2a338 IsDialogMessageA+0x68() in user32 (0x0033fda4)
  14 0x6c18690f in mfc42 (+0x1690f) (0x0033fe18)
  15 0x6c1711bc in mfc42 (+0x11bc) (0x009136bc)
  16 0x00000200 (0x00050054)
  17 0x00000000 (0x00000000)
0x00780cb6: movl	0x0(%eax),%edx
Modules:
Module	Address			Debug info	Name (148 modules)
PE	  340000-  379000	Deferred        graphicdata
PE	  380000-  3cb000	Deferred        graphic
PE	  3d0000-  3de000	Deferred        tqpackage
PE	  3e0000-  3ef000	Deferred        datathread
PE	  3f0000-  3ff000	Deferred        ndsound
PE	  400000-  b17000	Export          zeroonline
PE	  b20000-  bf0000	Deferred        c3_core_dll
PE	  bf0000-  c10000	Deferred        roleview
PE	  c10000-  c35000	Deferred        role3d
PE	  c40000-  cff000	Deferred        guidll
PE	  d00000-  d37000	Deferred        chat
PE	  d40000-  d55000	Deferred        assist
PE	 6f10000- 70b3000	Deferred        flash
PE	10000000-10076000	Deferred        gamedata
PE	6c170000-6c262000	Export          mfc42
PE	780c0000-78121000	Deferred        msvcp60
ELF	7b800000-7b948000	Deferred        kernel32<elf>
  \-PE	7b820000-7b948000	\               kernel32
ELF	7bc00000-7bcb0000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb0000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c1ac000-7c1ce000	Deferred        mlang<elf>
  \-PE	7c1b0000-7c1ce000	\               mlang
ELF	7c1ce000-7c1e2000	Deferred        olepro32<elf>
  \-PE	7c1d0000-7c1e2000	\               olepro32
ELF	7c2e2000-7c2e6000	Deferred        libgpg-error.so.0
ELF	7c2e6000-7c34f000	Deferred        libgcrypt.so.11
ELF	7c549000-7c55b000	Deferred        libtasn1.so.3
ELF	7c55b000-7c55f000	Deferred        libkeyutils.so.1
ELF	7c55f000-7c568000	Deferred        libkrb5support.so.0
ELF	7c568000-7c56c000	Deferred        libcom_err.so.2
ELF	7c56c000-7c590000	Deferred        libk5crypto.so.3
ELF	7c590000-7c622000	Deferred        libkrb5.so.3
ELF	7c622000-7c6bf000	Deferred        libgnutls.so.26
ELF	7c6bf000-7c6ea000	Deferred        libgssapi_krb5.so.2
ELF	7c6ea000-7c721000	Deferred        libcups.so.2
ELF	7c734000-7c74d000	Deferred        spoolss<elf>
  \-PE	7c740000-7c74d000	\               spoolss
ELF	7c74d000-7c76b000	Deferred        localspl<elf>
  \-PE	7c750000-7c76b000	\               localspl
ELF	7c76b000-7c786000	Deferred        wsock32<elf>
  \-PE	7c770000-7c786000	\               wsock32
ELF	7c786000-7c838000	Deferred        comdlg32<elf>
  \-PE	7c790000-7c838000	\               comdlg32
ELF	7cbca000-7cc00000	Deferred        winspool<elf>
  \-PE	7cbd0000-7cc00000	\               winspool
ELF	7cc00000-7cc14000	Deferred        lz32<elf>
  \-PE	7cc10000-7cc14000	\               lz32
ELF	7cc14000-7cc2f000	Deferred        version<elf>
  \-PE	7cc20000-7cc2f000	\               version
ELF	7cc2f000-7cc6f000	Deferred        urlmon<elf>
  \-PE	7cc40000-7cc6f000	\               urlmon
ELF	7cced000-7dc05000	Deferred        libglcore.so.1
ELF	7dc05000-7dcbf000	Deferred        libgl.so.1
ELF	7dd87000-7ddba000	Deferred        uxtheme<elf>
  \-PE	7dd90000-7ddba000	\               uxtheme
ELF	7dde4000-7ddf9000	Deferred        midimap<elf>
  \-PE	7ddf0000-7ddf9000	\               midimap
ELF	7ddf9000-7de1f000	Deferred        msacm32<elf>
  \-PE	7de00000-7de1f000	\               msacm32
ELF	7de1f000-7de37000	Deferred        msacm32<elf>
  \-PE	7de20000-7de37000	\               msacm32
ELF	7de37000-7de3d000	Deferred        libattr.so.1
ELF	7de3d000-7de44000	Deferred        libgdbm.so.3
ELF	7de44000-7de49000	Deferred        libcap.so.2
ELF	7de49000-7dea8000	Deferred        libpulse.so.0
ELF	7dea8000-7df70000	Deferred        libasound.so.2
ELF	7df81000-7df83000	Deferred        libnvidia-tls.so.1
ELF	7df83000-7dfba000	Deferred        winealsa<elf>
  \-PE	7df90000-7dfba000	\               winealsa
ELF	7dfba000-7dfc3000	Deferred        libxcursor.so.1
ELF	7dfc3000-7dfc8000	Deferred        libxfixes.so.3
ELF	7dfc8000-7dfcc000	Deferred        libxcomposite.so.1
ELF	7dfcc000-7dfd4000	Deferred        libxrandr.so.2
ELF	7dfd4000-7dfde000	Deferred        libxrender.so.1
ELF	7dfde000-7dfe4000	Deferred        libxxf86vm.so.1
ELF	7dfe4000-7dfe7000	Deferred        libxinerama.so.1
ELF	7dfe7000-7dfec000	Deferred        libxdmcp.so.6
ELF	7dfec000-7e006000	Deferred        libxcb.so.1
ELF	7e006000-7e00a000	Deferred        libxau.so.6
ELF	7e00a000-7e00f000	Deferred        libuuid.so.1
ELF	7e00f000-7e0fe000	Deferred        libx11.so.6
ELF	7e0fe000-7e10e000	Deferred        libxext.so.6
ELF	7e10e000-7e126000	Deferred        libice.so.6
ELF	7e126000-7e12f000	Deferred        libsm.so.6
ELF	7e130000-7e137000	Deferred        libasound_module_pcm_pulse.so
ELF	7e137000-7e140000	Deferred        librt.so.1
ELF	7e142000-7e1de000	Deferred        winex11<elf>
  \-PE	7e150000-7e1de000	\               winex11
ELF	7e210000-7e237000	Deferred        libexpat.so.1
ELF	7e237000-7e264000	Deferred        libfontconfig.so.1
ELF	7e277000-7e28d000	Deferred        libz.so.1
ELF	7e28d000-7e304000	Deferred        libfreetype.so.6
ELF	7e304000-7e48e000	Deferred        shell32<elf>
  \-PE	7e310000-7e48e000	\               shell32
ELF	7e48e000-7e4ec000	Deferred        shlwapi<elf>
  \-PE	7e4a0000-7e4ec000	\               shlwapi
ELF	7e4ec000-7e50f000	Deferred        mpr<elf>
  \-PE	7e4f0000-7e50f000	\               mpr
ELF	7e50f000-7e561000	Deferred        wininet<elf>
  \-PE	7e520000-7e561000	\               wininet
ELF	7e561000-7e59a000	Deferred        dinput<elf>
  \-PE	7e570000-7e59a000	\               dinput
ELF	7e59a000-7e5b4000	Deferred        dinput8<elf>
  \-PE	7e5a0000-7e5b4000	\               dinput8
ELF	7e5b4000-7e69b000	Deferred        oleaut32<elf>
  \-PE	7e5d0000-7e69b000	\               oleaut32
ELF	7e69b000-7e764000	Deferred        comctl32<elf>
  \-PE	7e6a0000-7e764000	\               comctl32
ELF	7e764000-7e785000	Deferred        imm32<elf>
  \-PE	7e770000-7e785000	\               imm32
ELF	7e785000-7e7f2000	Deferred        rpcrt4<elf>
  \-PE	7e790000-7e7f2000	\               rpcrt4
ELF	7e7f2000-7e8eb000	Deferred        ole32<elf>
  \-PE	7e810000-7e8eb000	\               ole32
ELF	7e8eb000-7e938000	Deferred        dsound<elf>
  \-PE	7e8f0000-7e938000	\               dsound
ELF	7e938000-7e9a6000	Deferred        msvcrt<elf>
  \-PE	7e950000-7e9a6000	\               msvcrt
ELF	7e9a6000-7eacd000	Deferred        wined3d<elf>
  \-PE	7e9c0000-7eacd000	\               wined3d
ELF	7eacd000-7eaf9000	Deferred        d3d8<elf>
  \-PE	7ead0000-7eaf9000	\               d3d8
ELF	7eaf9000-7eb99000	Deferred        gdi32<elf>
  \-PE	7eb10000-7eb99000	\               gdi32
ELF	7eb99000-7ece4000	Export          user32<elf>
  \-PE	7ebb0000-7ece4000	\               user32
ELF	7ece4000-7ed7b000	Deferred        winmm<elf>
  \-PE	7ecf0000-7ed7b000	\               winmm
ELF	7ed7b000-7eda9000	Deferred        ws2_32<elf>
  \-PE	7ed80000-7eda9000	\               ws2_32
ELF	7eda9000-7edff000	Deferred        advapi32<elf>
  \-PE	7edc0000-7edff000	\               advapi32
ELF	7edff000-7ee15000	Deferred        libresolv.so.2
ELF	7ee15000-7ee35000	Deferred        iphlpapi<elf>
  \-PE	7ee20000-7ee35000	\               iphlpapi
ELF	7ee35000-7ee5c000	Deferred        netapi32<elf>
  \-PE	7ee40000-7ee5c000	\               netapi32
ELF	7ee5c000-7ee68000	Deferred        libnss_files.so.2
ELF	7ee68000-7ee81000	Deferred        libnsl.so.1
ELF	7ee81000-7ee8a000	Deferred        libnss_compat.so.2
ELF	7efc7000-7efed000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c1a000-b7c1e000	Deferred        libdl.so.2
ELF	b7c1e000-b7d81000	Deferred        libc.so.6
ELF	b7d82000-b7d9b000	Deferred        libpthread.so.0
ELF	b7dae000-b7ee9000	Deferred        libwine.so.1
ELF	b7eeb000-b7f09000	Deferred        ld-linux.so.2
Threads:
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
00000016 
	00000017    0
0000002a 
	0000002f    0
	0000002e    0
	0000002d    0
	0000002c    0
00000045 (D) Z:\home\adrian\ZeroOnline\ZeroOnline.exe
	00000021    0
	00000020    0
	0000000b    0
	00000047    0
	00000046    0 <==
Backtrace:
=>0 0x00780cb6 in zeroonline (+0x380cb6) (0x0033d674)
  1 0x6c17206f in mfc42 (+0x206f) (0x0033d6f8)
  2 0x6c171cea in mfc42 (+0x1cea) (0x0033d718)
  3 0x005a32e3 in zeroonline (+0x1a32e3) (0x0033f57c)
  4 0x6c171c73 in mfc42 (+0x1c73) (0x0033f5dc)
  5 0x6c171bfb in mfc42 (+0x1bfb) (0x0033f5f8)
  6 0x6c171bba in mfc42 (+0x1bba) (0x0033f624)
  7 0x7ec64f2a WINPROC_wrapper+0x1a() in user32 (0x0033f654)
  8 0x7ec6537a WINPROC_wrapper+0x46a() in user32 (0x0033f694)
  9 0x7ec681a5 in user32 (+0xb81a5) (0x0033fb64)
  10 0x7ec6a73e in user32 (+0xba73e) (0x0033fba4)
  11 0x7ec298b6 DispatchMessageW+0x96() in user32 (0x0033fbe4)
  12 0x7ebf5919 IsDialogMessageW+0x129() in user32 (0x0033fd64)
  13 0x7ec2a338 IsDialogMessageA+0x68() in user32 (0x0033fda4)
  14 0x6c18690f in mfc42 (+0x1690f) (0x0033fe18)
  15 0x6c1711bc in mfc42 (+0x11bc) (0x009136bc)
  16 0x00000200 (0x00050054)
  17 0x00000000 (0x00000000)
adrian@adrian-desktop:~/ZeroOnline$ 


and the geame is still open so i have to kill it, i hope i give you all that you ask me for since i dont know much about this.

---

### Post by del_diablo on 2009-05-25
Possible errors:
1. It needs some bizzare register files, and thus autofails itself
2. Wanting spesific font over, just rip over the font map in Windows(Z:\Windows\Fonts)

Install it under Wine, so it will get the register correct.

Edit: Is not 0.9.1 old?

---

### Post by NightMKoder on 2009-05-25
Gecko 0.9.1 is the newest one. But first: you should probably install the program in wine. And since you're testing its best to start with a fresh prefix (either delete .wine or change your WINEPREFIX env variable). For mfc42, use winetricks instead of copying dlls:

```

wget http://winezeug.googlecode.com/svn/trunk/winetricks
sh winetricks mfc42

```

run your installer, and if it doesn't install then post here. You shouldn't be trying to run games from your windows partition and expect them to work.

---

### Post by Duskao on 2009-05-25
This is completely on the side from this thread, but I'm amazed that you guys can descipher anything from those long scrips. You guys are amazing!!!!
Game looks neat, kinda japanese. Best of luck, I might give it a try.

---

### Post by Drianos on 2009-05-25
ok, i intall it with wine, install mfc42 , directx9 and flash with winetricks since the game need those to be run in windows. The game download and install the patches, but happens the same, when it runs the program appear a black windows that doesnt respond.

```
adrian@adrian-desktop:~/.wine/dosdevices/c:/Program Files/ZeroOnline$ wine play.exe 
fixme:shdocvw:PersistMemory_Load (0x1428d8)->(0x40d064 9c)
fixme:shdocvw:OleControl_FreezeEvents (0x1428d8)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x1428d8)->(0)
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32bba4
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
fixme:iphlpapi:NotifyAddrChange (Handle 0x366e888, overlapped 0x366e890): stub
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[187958]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x142978)->((null) 1 0x32c13c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x142978)->((null) 25 2 0x32c150 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x142978)->((null) 26 2 0x32c150 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x142978)->(0x32c18c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x142978)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32c260 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1709d0)->(L"" L"" 0 0x32c298)
fixme:shdocvw:ClOleCommandTarget_Exec (0x142978)->((null) 29 2 0x32df74 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x142978)
fixme:shdocvw:ClientSite_GetContainer (0x142978)->(0x32dd90)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x142978)->(0xb7f00051)
fixme:shdocvw:ClOleCommandTarget_Exec (0x142978)->((null) 25 2 0x32dcc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x142978)->((null) 26 2 0x32dcc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x142978)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x142978)->((null) 28 2 0x32e9f0 (nil))
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
0[187958]: NPN Logging Active!
0[187958]: General Plugin Logging Active! (nsPluginHostImpl::ctor)
0[187958]: NPP Logging Active!
0[187958]: nsPluginHostImpl::ctor
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1428d8)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x186008)->((nil))
fixme:shdocvw:OleObject_Close (0x1428d8)->(1)
fixme:shell:DllCanUnloadNow stub
adrian@adrian-desktop:~/.wine/dosdevices/c:/Program Files/ZeroOnline$ fixme:win:EnumDisplayDevicesW ((null),0,0x33b62c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33b628,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:shdocvw:PersistStreamInit_InitNew (0x56a4e20)
fixme:shdocvw:PersistStreamInit_InitNew (0x58194c0)
fixme:shdocvw:PersistStreamInit_InitNew (0x581aea8)
fixme:shdocvw:PersistStreamInit_InitNew (0x530a668)
fixme:shdocvw:PersistStreamInit_InitNew (0x60f5c00)
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:d3d8:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0x41
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 301 requests (301 known processed) with 0 events remaining.


```

---

### Post by NightMKoder on 2009-05-25
You shouldn't have installed directx. Wine comes with its own directx implementation, so I suggest starting with a clean wine prefix (rm -Rf ~/.wine), installing flash, gecko, installing the game, and running it.

---

### Post by Drianos on 2009-05-25
ok, i erase .wine , put in terminal "winetricks mfc42 flash gecko", reinstalled the game, it install the patches and when it is going to open the game the program error window appear (thats the only change) and i have to kill the game window since it is black transparent and doest respond.

```
adrian@adrian-desktop:~/.wine/dosdevices/c:/Program Files/ZeroOnline$ wine play.exe 
fixme:shdocvw:PersistMemory_Load (0x142438)->(0x40d064 9c)
fixme:shdocvw:OleControl_FreezeEvents (0x142438)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x142438)->(0)
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32bba4
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
fixme:iphlpapi:NotifyAddrChange (Handle 0x366e888, overlapped 0x366e890): stub
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1424d8)->((null) 1 0x32c13c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 25 2 0x32c150 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 26 2 0x32c150 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1424d8)->(0x32c18c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32c260 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x170510)->(L"" L"" 0 0x32c298)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 29 2 0x32df74 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1424d8)
fixme:shdocvw:ClientSite_GetContainer (0x1424d8)->(0x32dd90)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1424d8)->(0xb7fa5051)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 25 2 0x32dcc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 26 2 0x32dcc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 28 2 0x32e9f0 (nil))
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
0[187498]: NPN Logging Active!
0[187498]: General Plugin Logging Active! (nsPluginHostImpl::ctor)
0[187498]: NPP Logging Active!
0[187498]: nsPluginHostImpl::ctor
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x142438)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x185b48)->((nil))
fixme:shdocvw:OleObject_Close (0x142438)->(1)
fixme:shell:DllCanUnloadNow stub
adrian@adrian-desktop:~/.wine/dosdevices/c:/Program Files/ZeroOnline$ fixme:win:EnumDisplayDevicesW ((null),0,0x33b62c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33b628,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
wine: Unhandled page fault on read access to 0x00000000 at address 0x780cb6 (thread 0021), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00780cb6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00780cb6 ESP:0033d650 EBP:0033d674 EFLAGS:00210202(  R- --  I   - - - )
 EAX:00000000 EBX:0054fa90 ECX:00921930 EDX:7e9a2934
 ESI:00000000 EDI:00000264
Stack dump:
0x0033d650:  00000000 0054fafa 023aaaf0 00000264
0x0033d660:  0054fa90 00000007 7bc3442f 5f4d0b68
0x0033d670:  023aaaf0 0033d6f8 5f40206f 00000000
0x0033d680:  000001b1 00000264 008d0738 023aaaf0
0x0033d690:  7e987ff4 00000000 00000000 00000000
0x0033d6a0:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x00780cb6 in zeroonline (+0x380cb6) (0x0033d674)
  1 0x5f40206f in mfc42 (+0x206f) (0x0033d6f8)
  2 0x5f401cea in mfc42 (+0x1cea) (0x0033d718)
  3 0x005a32e3 in zeroonline (+0x1a32e3) (0x0033f57c)
  4 0x5f401c73 in mfc42 (+0x1c73) (0x0033f5dc)
  5 0x5f401bfb in mfc42 (+0x1bfb) (0x0033f5f8)
  6 0x5f401bba in mfc42 (+0x1bba) (0x0033f624)
  7 0x7ec64f1a WINPROC_wrapper+0x1a() in user32 (0x0033f654)
  8 0x7ec6536a WINPROC_wrapper+0x46a() in user32 (0x0033f694)
  9 0x7ec68195 in user32 (+0xb8195) (0x0033fb64)
  10 0x7ec6a72e in user32 (+0xba72e) (0x0033fba4)
  11 0x7ec298a6 DispatchMessageW+0x96() in user32 (0x0033fbe4)
  12 0x7ebf5919 IsDialogMessageW+0x129() in user32 (0x0033fd64)
  13 0x7ec2a328 IsDialogMessageA+0x68() in user32 (0x0033fda4)
  14 0x5f41690f in mfc42 (+0x1690f) (0x0033fe18)
  15 0x5f4011bc in mfc42 (+0x11bc) (0x009136bc)
  16 0x00000200 (0x00050054)
  17 0x00000000 (0x00000000)
0x00780cb6: movl	0x0(%eax),%edx
Modules:
Module	Address			Debug info	Name (155 modules)
PE	  340000-  379000	Deferred        graphicdata
PE	  380000-  3cb000	Deferred        graphic
PE	  3d0000-  3de000	Deferred        tqpackage
PE	  3e0000-  3ef000	Deferred        datathread
PE	  3f0000-  3ff000	Deferred        ndsound
PE	  400000-  b17000	Export          zeroonline
PE	  b20000-  bf0000	Deferred        c3_core_dll
PE	  bf0000-  c10000	Deferred        roleview
PE	  c10000-  c35000	Deferred        role3d
PE	  c40000-  cff000	Deferred        guidll
PE	  d00000-  d37000	Deferred        chat
PE	  d40000-  d55000	Deferred        assist
PE	 6f10000- 7398000	Deferred        flash10b
PE	10000000-10076000	Deferred        gamedata
PE	5f400000-5f4f2000	Export          mfc42
PE	780c0000-78121000	Deferred        msvcp60
ELF	7a8e8000-7b800000	Deferred        libglcore.so.1
ELF	7b800000-7b948000	Deferred        kernel32<elf>
  \-PE	7b820000-7b948000	\               kernel32
ELF	7bc00000-7bcb0000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb0000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d2cc000-7d2ef000	Deferred        mlang<elf>
  \-PE	7d2d0000-7d2ef000	\               mlang
ELF	7d2ef000-7d304000	Deferred        schannel<elf>
  \-PE	7d2f0000-7d304000	\               schannel
ELF	7d304000-7d32f000	Deferred        secur32<elf>
  \-PE	7d310000-7d32f000	\               secur32
ELF	7d32f000-7d333000	Deferred        libgpg-error.so.0
ELF	7d333000-7d39c000	Deferred        libgcrypt.so.11
ELF	7d39c000-7d3ae000	Deferred        libtasn1.so.3
ELF	7d3ae000-7d3b2000	Deferred        libkeyutils.so.1
ELF	7d3b2000-7d3bb000	Deferred        libkrb5support.so.0
ELF	7d3bb000-7d3bf000	Deferred        libcom_err.so.2
ELF	7d3bf000-7d3e3000	Deferred        libk5crypto.so.3
ELF	7d3e3000-7d475000	Deferred        libkrb5.so.3
ELF	7d475000-7d512000	Deferred        libgnutls.so.26
ELF	7d512000-7d53d000	Deferred        libgssapi_krb5.so.2
ELF	7d53d000-7d574000	Deferred        libcups.so.2
ELF	7d574000-7d58d000	Deferred        spoolss<elf>
  \-PE	7d580000-7d58d000	\               spoolss
ELF	7d58d000-7d5ab000	Deferred        localspl<elf>
  \-PE	7d590000-7d5ab000	\               localspl
ELF	7d5ab000-7d5df000	Deferred        liblcms.so.1
ELF	7d5df000-7d615000	Deferred        winspool<elf>
  \-PE	7d5f0000-7d615000	\               winspool
ELF	7d615000-7d6c7000	Deferred        comdlg32<elf>
  \-PE	7d620000-7d6c7000	\               comdlg32
ELF	7d6c7000-7d74a000	Deferred        crypt32<elf>
  \-PE	7d6d0000-7d74a000	\               crypt32
ELF	7dadd000-7daf1000	Deferred        olepro32<elf>
  \-PE	7dae0000-7daf1000	\               olepro32
ELF	7daf1000-7db10000	Deferred        mscms<elf>
  \-PE	7db00000-7db10000	\               mscms
ELF	7db10000-7db24000	Deferred        lz32<elf>
  \-PE	7db20000-7db24000	\               lz32
ELF	7db24000-7db3f000	Deferred        version<elf>
  \-PE	7db30000-7db3f000	\               version
ELF	7db3f000-7db82000	Deferred        urlmon<elf>
  \-PE	7db50000-7db82000	\               urlmon
ELF	7dc01000-7dcbb000	Deferred        libgl.so.1
ELF	7dd83000-7ddb6000	Deferred        uxtheme<elf>
  \-PE	7dd90000-7ddb6000	\               uxtheme
ELF	7dde0000-7ddf5000	Deferred        midimap<elf>
  \-PE	7ddf0000-7ddf5000	\               midimap
ELF	7ddf5000-7de1b000	Deferred        msacm32<elf>
  \-PE	7de00000-7de1b000	\               msacm32
ELF	7de1b000-7de33000	Deferred        msacm32<elf>
  \-PE	7de20000-7de33000	\               msacm32
ELF	7de33000-7de39000	Deferred        libattr.so.1
ELF	7de39000-7de98000	Deferred        libpulse.so.0
ELF	7dea9000-7deab000	Deferred        libnvidia-tls.so.1
ELF	7deab000-7deb4000	Deferred        librt.so.1
ELF	7deb4000-7df7c000	Deferred        libasound.so.2
ELF	7df7c000-7dfb3000	Deferred        winealsa<elf>
  \-PE	7df90000-7dfb3000	\               winealsa
ELF	7dfb3000-7dfbc000	Deferred        libxcursor.so.1
ELF	7dfbc000-7dfc1000	Deferred        libxfixes.so.3
ELF	7dfc1000-7dfc5000	Deferred        libxcomposite.so.1
ELF	7dfc5000-7dfcd000	Deferred        libxrandr.so.2
ELF	7dfcd000-7dfd7000	Deferred        libxrender.so.1
ELF	7dfd7000-7dfdd000	Deferred        libxxf86vm.so.1
ELF	7dfdd000-7dfe0000	Deferred        libxinerama.so.1
ELF	7dfe0000-7dfe5000	Deferred        libxdmcp.so.6
ELF	7dfe5000-7dfff000	Deferred        libxcb.so.1
ELF	7dfff000-7e003000	Deferred        libxau.so.6
ELF	7e003000-7e008000	Deferred        libuuid.so.1
ELF	7e008000-7e0f7000	Deferred        libx11.so.6
ELF	7e0f7000-7e107000	Deferred        libxext.so.6
ELF	7e107000-7e11f000	Deferred        libice.so.6
ELF	7e11f000-7e128000	Deferred        libsm.so.6
ELF	7e128000-7e12f000	Deferred        libgdbm.so.3
ELF	7e12f000-7e134000	Deferred        libcap.so.2
ELF	7e134000-7e13b000	Deferred        libasound_module_pcm_pulse.so
ELF	7e13b000-7e1d7000	Deferred        winex11<elf>
  \-PE	7e150000-7e1d7000	\               winex11
ELF	7e20f000-7e236000	Deferred        libexpat.so.1
ELF	7e236000-7e263000	Deferred        libfontconfig.so.1
ELF	7e276000-7e28c000	Deferred        libz.so.1
ELF	7e28c000-7e303000	Deferred        libfreetype.so.6
ELF	7e303000-7e48d000	Deferred        shell32<elf>
  \-PE	7e310000-7e48d000	\               shell32
ELF	7e48d000-7e4eb000	Deferred        shlwapi<elf>
  \-PE	7e4a0000-7e4eb000	\               shlwapi
ELF	7e4eb000-7e50e000	Deferred        mpr<elf>
  \-PE	7e4f0000-7e50e000	\               mpr
ELF	7e50e000-7e560000	Deferred        wininet<elf>
  \-PE	7e520000-7e560000	\               wininet
ELF	7e560000-7e599000	Deferred        dinput<elf>
  \-PE	7e570000-7e599000	\               dinput
ELF	7e599000-7e5b3000	Deferred        dinput8<elf>
  \-PE	7e5a0000-7e5b3000	\               dinput8
ELF	7e5b3000-7e69a000	Deferred        oleaut32<elf>
  \-PE	7e5d0000-7e69a000	\               oleaut32
ELF	7e69a000-7e762000	Deferred        comctl32<elf>
  \-PE	7e6a0000-7e762000	\               comctl32
ELF	7e762000-7e783000	Deferred        imm32<elf>
  \-PE	7e770000-7e783000	\               imm32
ELF	7e783000-7e7ef000	Deferred        rpcrt4<elf>
  \-PE	7e790000-7e7ef000	\               rpcrt4
ELF	7e7ef000-7e8ea000	Deferred        ole32<elf>
  \-PE	7e810000-7e8ea000	\               ole32
ELF	7e8ea000-7e936000	Deferred        dsound<elf>
  \-PE	7e8f0000-7e936000	\               dsound
ELF	7e936000-7e9a4000	Deferred        msvcrt<elf>
  \-PE	7e950000-7e9a4000	\               msvcrt
ELF	7e9a4000-7eacc000	Deferred        wined3d<elf>
  \-PE	7e9c0000-7eacc000	\               wined3d
ELF	7eacc000-7eaf8000	Deferred        d3d8<elf>
  \-PE	7ead0000-7eaf8000	\               d3d8
ELF	7eaf8000-7eb99000	Deferred        gdi32<elf>
  \-PE	7eb10000-7eb99000	\               gdi32
ELF	7eb99000-7ece4000	Export          user32<elf>
  \-PE	7ebb0000-7ece4000	\               user32
ELF	7ece4000-7ed7b000	Deferred        winmm<elf>
  \-PE	7ecf0000-7ed7b000	\               winmm
ELF	7ed7b000-7eda9000	Deferred        ws2_32<elf>
  \-PE	7ed80000-7eda9000	\               ws2_32
ELF	7eda9000-7edff000	Deferred        advapi32<elf>
  \-PE	7edc0000-7edff000	\               advapi32
ELF	7edff000-7ee15000	Deferred        libresolv.so.2
ELF	7ee15000-7ee35000	Deferred        iphlpapi<elf>
  \-PE	7ee20000-7ee35000	\               iphlpapi
ELF	7ee35000-7ee5c000	Deferred        netapi32<elf>
  \-PE	7ee40000-7ee5c000	\               netapi32
ELF	7ee5c000-7ee68000	Deferred        libnss_files.so.2
ELF	7ee68000-7ee81000	Deferred        libnsl.so.1
ELF	7ee81000-7ee8a000	Deferred        libnss_compat.so.2
ELF	7efc7000-7efed000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7dd5000-b7dd9000	Deferred        libdl.so.2
ELF	b7dd9000-b7f3c000	Deferred        libc.so.6
ELF	b7f3d000-b7f56000	Deferred        libpthread.so.0
ELF	b7f69000-b80a4000	Deferred        libwine.so.1
ELF	b80a6000-b80c4000	Deferred        ld-linux.so.2
Threads:
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
00000016 
	00000017    0
00000029 
	00000030    0
	0000002f    0
	0000002e    0
	0000002d    0
	0000002c    0
	0000002b    0
0000000b (D) C:\Program Files\ZeroOnline\ZeroOnline.exe
	0000001b    0
	0000001a    0
	00000020    0
	00000019    0
	00000018    0
	00000023    0
	00000021    0 <==
Backtrace:
=>0 0x00780cb6 in zeroonline (+0x380cb6) (0x0033d674)
  1 0x5f40206f in mfc42 (+0x206f) (0x0033d6f8)
  2 0x5f401cea in mfc42 (+0x1cea) (0x0033d718)
  3 0x005a32e3 in zeroonline (+0x1a32e3) (0x0033f57c)
  4 0x5f401c73 in mfc42 (+0x1c73) (0x0033f5dc)
  5 0x5f401bfb in mfc42 (+0x1bfb) (0x0033f5f8)
  6 0x5f401bba in mfc42 (+0x1bba) (0x0033f624)
  7 0x7ec64f1a WINPROC_wrapper+0x1a() in user32 (0x0033f654)
  8 0x7ec6536a WINPROC_wrapper+0x46a() in user32 (0x0033f694)
  9 0x7ec68195 in user32 (+0xb8195) (0x0033fb64)
  10 0x7ec6a72e in user32 (+0xba72e) (0x0033fba4)
  11 0x7ec298a6 DispatchMessageW+0x96() in user32 (0x0033fbe4)
  12 0x7ebf5919 IsDialogMessageW+0x129() in user32 (0x0033fd64)
  13 0x7ec2a328 IsDialogMessageA+0x68() in user32 (0x0033fda4)
  14 0x5f41690f in mfc42 (+0x1690f) (0x0033fe18)
  15 0x5f4011bc in mfc42 (+0x11bc) (0x009136bc)
  16 0x00000200 (0x00050054)
  17 0x00000000 (0x00000000)

adrian@adrian-desktop:~/.wine/dosdevices/c:/Program Files/ZeroOnline$ 
```

---

### Post by NightMKoder on 2009-05-25
Hmmm...nothing sticks out at me. Try downgrading wine 1 version (from [http://wine.budgetdedicated.com/archive/index.html):](http://wine.budgetdedicated.com/archive/index.html):)

```

sudo apt-get remove wine
wget http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.21~winehq0~ubuntu~9.04-0ubuntu1_i386.deb
sudo dpkg -i wine_1.1.21~winehq0~ubuntu~9.04-0ubuntu1_i386.deb

```

and see if your output is any different.

---

### Post by Drianos on 2009-05-25
this is the new output with wine 1.1.21, was using before version 1.1.22.
```

adrian@adrian-desktop:~/.wine/dosdevices/c:/Program Files/ZeroOnline$ wine play.exe 
fixme:shdocvw:PersistMemory_Load (0x142438)->(0x40d064 9c)
fixme:shdocvw:OleControl_FreezeEvents (0x142438)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x142438)->(0)
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32bba4
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
fixme:iphlpapi:NotifyAddrChange (Handle 0x366e888, overlapped 0x366e890): stub
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[187498]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1424d8)->((null) 1 0x32c13c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 25 2 0x32c150 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 26 2 0x32c150 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1424d8)->(0x32c18c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32c260 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x170510)->(L"" L"" 0 0x32c298)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 29 2 0x32df74 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1424d8)
fixme:shdocvw:ClientSite_GetContainer (0x1424d8)->(0x32dd90)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1424d8)->(0xb7eb0051)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 25 2 0x32dcc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 26 2 0x32dcc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1424d8)->((null) 28 2 0x32e9f0 (nil))
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
0[187498]: NPN Logging Active!
0[187498]: General Plugin Logging Active! (nsPluginHostImpl::ctor)
0[187498]: NPP Logging Active!
0[187498]: nsPluginHostImpl::ctor
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x142438)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x185b48)->((nil))
fixme:shdocvw:OleObject_Close (0x142438)->(1)
fixme:shell:DllCanUnloadNow stub
adrian@adrian-desktop:~/.wine/dosdevices/c:/Program Files/ZeroOnline$ fixme:win:EnumDisplayDevicesW ((null),0,0x33b62c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33b628,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
wine: Unhandled page fault on read access to 0x00000000 at address 0x780cb6 (thread 003c), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00780cb6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00780cb6 ESP:0033d650 EBP:0033d674 EFLAGS:00210202(  R- --  I   - - - )
 EAX:00000000 EBX:0054fa90 ECX:00921930 EDX:7e9b0934
 ESI:00000000 EDI:000000df
Stack dump:
0x0033d650:  00000000 0054fafa 023aaaf0 000000df
0x0033d660:  0054fa90 00000007 7bc3445f 5f4d0b68
0x0033d670:  023aaaf0 0033d6f8 5f40206f 00000000
0x0033d680:  00000308 000000df 008d0738 023aaaf0
0x0033d690:  7e995ff4 00000000 00000000 00000000
0x0033d6a0:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x00780cb6 in zeroonline (+0x380cb6) (0x0033d674)
  1 0x5f40206f in mfc42 (+0x206f) (0x0033d6f8)
  2 0x5f401cea in mfc42 (+0x1cea) (0x0033d718)
  3 0x005a32e3 in zeroonline (+0x1a32e3) (0x0033f57c)
  4 0x5f401c73 in mfc42 (+0x1c73) (0x0033f5dc)
  5 0x5f401bfb in mfc42 (+0x1bfb) (0x0033f5f8)
  6 0x5f401bba in mfc42 (+0x1bba) (0x0033f624)
  7 0x7ec70f2a WINPROC_wrapper+0x1a() in user32 (0x0033f654)
  8 0x7ec7137a WINPROC_wrapper+0x46a() in user32 (0x0033f694)
  9 0x7ec741a5 in user32 (+0xb41a5) (0x0033fb64)
  10 0x7ec7673e in user32 (+0xb673e) (0x0033fba4)
  11 0x7ec358b6 DispatchMessageW+0x96() in user32 (0x0033fbe4)
  12 0x7ec01919 IsDialogMessageW+0x129() in user32 (0x0033fd64)
  13 0x7ec36338 IsDialogMessageA+0x68() in user32 (0x0033fda4)
  14 0x5f41690f in mfc42 (+0x1690f) (0x0033fe18)
  15 0x5f4011bc in mfc42 (+0x11bc) (0x009136bc)
  16 0x00000200 (0x000b0046)
  17 0x00000000 (0x00000000)
0x00780cb6: movl	0x0(%eax),%edx
Modules:
Module	Address			Debug info	Name (155 modules)
PE	  340000-  379000	Deferred        graphicdata
PE	  380000-  3cb000	Deferred        graphic
PE	  3d0000-  3de000	Deferred        tqpackage
PE	  3e0000-  3ef000	Deferred        datathread
PE	  3f0000-  3ff000	Deferred        ndsound
PE	  400000-  b17000	Export          zeroonline
PE	  b20000-  bf0000	Deferred        c3_core_dll
PE	  bf0000-  c10000	Deferred        roleview
PE	  c10000-  c35000	Deferred        role3d
PE	  c40000-  cff000	Deferred        guidll
PE	  d00000-  d37000	Deferred        chat
PE	  d40000-  d55000	Deferred        assist
PE	 6f10000- 7398000	Deferred        flash10b
PE	10000000-10076000	Deferred        gamedata
PE	5f400000-5f4f2000	Export          mfc42
PE	780c0000-78121000	Deferred        msvcp60
ELF	7b800000-7b948000	Deferred        kernel32<elf>
  \-PE	7b820000-7b948000	\               kernel32
ELF	7bc00000-7bcb0000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb0000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c0b9000-7c0db000	Deferred        mlang<elf>
  \-PE	7c0c0000-7c0db000	\               mlang
ELF	7c0db000-7c0f0000	Deferred        schannel<elf>
  \-PE	7c0e0000-7c0f0000	\               schannel
ELF	7c0f0000-7c11b000	Deferred        secur32<elf>
  \-PE	7c100000-7c11b000	\               secur32
ELF	7c11b000-7c12f000	Deferred        olepro32<elf>
  \-PE	7c120000-7c12f000	\               olepro32
ELF	7c22f000-7c233000	Deferred        libgpg-error.so.0
ELF	7c233000-7c29c000	Deferred        libgcrypt.so.11
ELF	7c29c000-7c2ae000	Deferred        libtasn1.so.3
ELF	7c2ae000-7c2b2000	Deferred        libkeyutils.so.1
ELF	7c2b2000-7c2d6000	Deferred        libk5crypto.so.3
ELF	7c2d6000-7c368000	Deferred        libkrb5.so.3
ELF	7c368000-7c405000	Deferred        libgnutls.so.26
ELF	7c405000-7c430000	Deferred        libgssapi_krb5.so.2
ELF	7c629000-7c632000	Deferred        libkrb5support.so.0
ELF	7c632000-7c636000	Deferred        libcom_err.so.2
ELF	7c636000-7c66d000	Deferred        libcups.so.2
ELF	7c66d000-7c686000	Deferred        spoolss<elf>
  \-PE	7c670000-7c686000	\               spoolss
ELF	7c686000-7c6a4000	Deferred        localspl<elf>
  \-PE	7c690000-7c6a4000	\               localspl
ELF	7c6a4000-7c6d8000	Deferred        liblcms.so.1
ELF	7c6eb000-7c70a000	Deferred        mscms<elf>
  \-PE	7c6f0000-7c70a000	\               mscms
ELF	7c70a000-7c7bc000	Deferred        comdlg32<elf>
  \-PE	7c710000-7c7bc000	\               comdlg32
ELF	7c7bc000-7c83f000	Deferred        crypt32<elf>
  \-PE	7c7d0000-7c83f000	\               crypt32
ELF	7cbd2000-7cc08000	Deferred        winspool<elf>
  \-PE	7cbe0000-7cc08000	\               winspool
ELF	7cc08000-7cc1c000	Deferred        lz32<elf>
  \-PE	7cc10000-7cc1c000	\               lz32
ELF	7cc1c000-7cc37000	Deferred        version<elf>
  \-PE	7cc20000-7cc37000	\               version
ELF	7cc37000-7cc77000	Deferred        urlmon<elf>
  \-PE	7cc40000-7cc77000	\               urlmon
ELF	7ccf6000-7dc0e000	Deferred        libglcore.so.1
ELF	7dc0e000-7dcc8000	Deferred        libgl.so.1
ELF	7dd90000-7ddc3000	Deferred        uxtheme<elf>
  \-PE	7dda0000-7ddc3000	\               uxtheme
ELF	7dded000-7de02000	Deferred        midimap<elf>
  \-PE	7ddf0000-7de02000	\               midimap
ELF	7de02000-7de28000	Deferred        msacm32<elf>
  \-PE	7de10000-7de28000	\               msacm32
ELF	7de28000-7de40000	Deferred        msacm32<elf>
  \-PE	7de30000-7de40000	\               msacm32
ELF	7de40000-7de46000	Deferred        libattr.so.1
ELF	7de46000-7dea5000	Deferred        libpulse.so.0
ELF	7deb6000-7deb8000	Deferred        libnvidia-tls.so.1
ELF	7deb8000-7dec1000	Deferred        librt.so.1
ELF	7dec1000-7df89000	Deferred        libasound.so.2
ELF	7df89000-7dfc0000	Deferred        winealsa<elf>
  \-PE	7df90000-7dfc0000	\               winealsa
ELF	7dfc0000-7dfc9000	Deferred        libxcursor.so.1
ELF	7dfc9000-7dfce000	Deferred        libxfixes.so.3
ELF	7dfce000-7dfd2000	Deferred        libxcomposite.so.1
ELF	7dfd2000-7dfda000	Deferred        libxrandr.so.2
ELF	7dfda000-7dfe4000	Deferred        libxrender.so.1
ELF	7dfe4000-7dfea000	Deferred        libxxf86vm.so.1
ELF	7dfea000-7dfef000	Deferred        libxdmcp.so.6
ELF	7dfef000-7e009000	Deferred        libxcb.so.1
ELF	7e009000-7e00e000	Deferred        libuuid.so.1
ELF	7e00e000-7e0fd000	Deferred        libx11.so.6
ELF	7e0fd000-7e10d000	Deferred        libxext.so.6
ELF	7e10d000-7e125000	Deferred        libice.so.6
ELF	7e125000-7e12e000	Deferred        libsm.so.6
ELF	7e12e000-7e1ca000	Deferred        winex11<elf>
  \-PE	7e140000-7e1ca000	\               winex11
ELF	7e21c000-7e243000	Deferred        libexpat.so.1
ELF	7e243000-7e270000	Deferred        libfontconfig.so.1
ELF	7e271000-7e274000	Deferred        libxinerama.so.1
ELF	7e283000-7e299000	Deferred        libz.so.1
ELF	7e299000-7e310000	Deferred        libfreetype.so.6
ELF	7e310000-7e49a000	Deferred        shell32<elf>
  \-PE	7e320000-7e49a000	\               shell32
ELF	7e49a000-7e4f8000	Deferred        shlwapi<elf>
  \-PE	7e4b0000-7e4f8000	\               shlwapi
ELF	7e4f8000-7e51b000	Deferred        mpr<elf>
  \-PE	7e500000-7e51b000	\               mpr
ELF	7e51b000-7e56d000	Deferred        wininet<elf>
  \-PE	7e520000-7e56d000	\               wininet
ELF	7e56d000-7e5a6000	Deferred        dinput<elf>
  \-PE	7e580000-7e5a6000	\               dinput
ELF	7e5a6000-7e5c0000	Deferred        dinput8<elf>
  \-PE	7e5b0000-7e5c0000	\               dinput8
ELF	7e5c0000-7e6a7000	Deferred        oleaut32<elf>
  \-PE	7e5e0000-7e6a7000	\               oleaut32
ELF	7e6a7000-7e770000	Deferred        comctl32<elf>
  \-PE	7e6b0000-7e770000	\               comctl32
ELF	7e770000-7e791000	Deferred        imm32<elf>
  \-PE	7e780000-7e791000	\               imm32
ELF	7e791000-7e7fe000	Deferred        rpcrt4<elf>
  \-PE	7e7a0000-7e7fe000	\               rpcrt4
ELF	7e7fe000-7e8f7000	Deferred        ole32<elf>
  \-PE	7e820000-7e8f7000	\               ole32
ELF	7e8f7000-7e944000	Deferred        dsound<elf>
  \-PE	7e900000-7e944000	\               dsound
ELF	7e944000-7e9b2000	Deferred        msvcrt<elf>
  \-PE	7e950000-7e9b2000	\               msvcrt
ELF	7e9b2000-7ead9000	Deferred        wined3d<elf>
  \-PE	7e9c0000-7ead9000	\               wined3d
ELF	7ead9000-7eb05000	Deferred        d3d8<elf>
  \-PE	7eae0000-7eb05000	\               d3d8
ELF	7eb05000-7eba5000	Deferred        gdi32<elf>
  \-PE	7eb20000-7eba5000	\               gdi32
ELF	7eba5000-7ecf0000	Export          user32<elf>
  \-PE	7ebc0000-7ecf0000	\               user32
ELF	7ecf0000-7ed87000	Deferred        winmm<elf>
  \-PE	7ed00000-7ed87000	\               winmm
ELF	7ed87000-7edb5000	Deferred        ws2_32<elf>
  \-PE	7ed90000-7edb5000	\               ws2_32
ELF	7edb5000-7ee0b000	Deferred        advapi32<elf>
  \-PE	7edc0000-7ee0b000	\               advapi32
ELF	7ee0b000-7ee21000	Deferred        libresolv.so.2
ELF	7ee21000-7ee41000	Deferred        iphlpapi<elf>
  \-PE	7ee30000-7ee41000	\               iphlpapi
ELF	7ee41000-7ee68000	Deferred        netapi32<elf>
  \-PE	7ee50000-7ee68000	\               netapi32
ELF	7ee68000-7ee81000	Deferred        libnsl.so.1
ELF	7ee81000-7ee8a000	Deferred        libnss_compat.so.2
ELF	7ee8a000-7ee91000	Deferred        libgdbm.so.3
ELF	7ee91000-7ee96000	Deferred        libcap.so.2
ELF	7ee96000-7ee9d000	Deferred        libasound_module_pcm_pulse.so
ELF	7efc7000-7efed000	Deferred        libm.so.6
ELF	7eff4000-7f000000	Deferred        libnss_files.so.2
ELF	b7d70000-b7d74000	Deferred        libxau.so.6
ELF	b7d74000-b7d7f000	Deferred        libnss_nis.so.2
ELF	b7d80000-b7d84000	Deferred        libdl.so.2
ELF	b7d84000-b7ee7000	Deferred        libc.so.6
ELF	b7ee8000-b7f01000	Deferred        libpthread.so.0
ELF	b7f14000-b804f000	Deferred        libwine.so.1
ELF	b8051000-b806f000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000036    0
	00000035    0
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
00000029 
	00000030    0
	0000002f    0
	0000002e    0
	0000002d    0
	0000002c    0
	0000002b    0
0000000b 
	0000001b    0
	0000001a    0
	00000020    0
	00000019    0
	00000018    0
	00000023    0
00000045 (D) C:\Program Files\ZeroOnline\ZeroOnline.exe
	00000009    0
	0000001f    0
	00000022    0
	0000001c    0
	0000001e    0
	0000003b    0
	0000003c    0 <==
Backtrace:
=>0 0x00780cb6 in zeroonline (+0x380cb6) (0x0033d674)
  1 0x5f40206f in mfc42 (+0x206f) (0x0033d6f8)
  2 0x5f401cea in mfc42 (+0x1cea) (0x0033d718)
  3 0x005a32e3 in zeroonline (+0x1a32e3) (0x0033f57c)
  4 0x5f401c73 in mfc42 (+0x1c73) (0x0033f5dc)
  5 0x5f401bfb in mfc42 (+0x1bfb) (0x0033f5f8)
  6 0x5f401bba in mfc42 (+0x1bba) (0x0033f624)
  7 0x7ec70f2a WINPROC_wrapper+0x1a() in user32 (0x0033f654)
  8 0x7ec7137a WINPROC_wrapper+0x46a() in user32 (0x0033f694)
  9 0x7ec741a5 in user32 (+0xb41a5) (0x0033fb64)
  10 0x7ec7673e in user32 (+0xb673e) (0x0033fba4)
  11 0x7ec358b6 DispatchMessageW+0x96() in user32 (0x0033fbe4)
  12 0x7ec01919 IsDialogMessageW+0x129() in user32 (0x0033fd64)
  13 0x7ec36338 IsDialogMessageA+0x68() in user32 (0x0033fda4)
  14 0x5f41690f in mfc42 (+0x1690f) (0x0033fe18)
  15 0x5f4011bc in mfc42 (+0x11bc) (0x009136bc)
  16 0x00000200 (0x000b0046)
  17 0x00000000 (0x00000000)

adrian@adrian-desktop:~/.wine/dosdevices/c:/Program Files/ZeroOnline$ 

```

---

### Post by NightMKoder on 2009-05-25
Alright, seems like there is a bug in wine. Although from your logs it doesn't seem like there is anything to go on. I suggest filing a bug @ bugs.winehq.org . Also if you're really interested in seeing this game work on wine, sign up for the maintainer position: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=6627](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6627) . 

Wild guess says that the bug is in the order in which window events are sent, but I have no idea.

---

### Post by Drianos on 2009-05-25
damm =/, well thx for the help.

---

