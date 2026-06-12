---
title: "Last Chaos"
date: 2009-07-29
forum: Wine
---

### Post by W4l0ck on 2009-07-29
Ok, so I got the game last chaos and it dosn't work past the splash screen. please answer via PM.

---

### Post by gawynus on 2010-01-28
I have similar problem 
  I have lately downloaded Last Chaos client and installed it through wine.
  It installed correctly, entered th client window and downloaded upadates. So far so good. But when I try to start a game it just crashes. The update window disappears, some bigger window show promising sth but the only thing I get is "Report error?" with possibility to choose yes/no.
  Here I paste all information from the console from the start of application to the crash.
  Please help 
  
  /.wine/drive_c/GAMIGO/LastChaosPoland $ ./LC.exe 
  fixme: shdocvw: PersistStreamInit_InitNew (0x12c978 )
  err: ole:ITypeInfo_fnInvoke did not find member id -518, flags 0 x 4!
  err: ole:ITypeInfo_fnInvoke did not find member id -517, flags 0 x 4!
  fixme: shdocvw: PersistStreamInit_InitNew (0 x148728 )
  err: ole:ITypeInfo_fnInvoke did not find member id -518, flags 0 x4!
  err: ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x 4!
  fixme: shdocvw:navigate_url Unsupported args (Flags 0x32dd80:3; TargetFrameName 0x32dd70:8 )
  fixme: iphlpapi:NotifyAddrChange (Handle 0x7e34d9b8, overlapped 0x7e34d99c): stub
  fixme: system:SetProcessDPIAware stub!
  fixme: msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x13eef34)
  fixme: ole: CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
  fixme: shdocvw:ClOleCommandTarget_QueryStatus (0x12ca14)->((null) 1 0x32d448 (nil)) 
  fixme: shdocvw:ClOleCommandTarget_Exec (0x12ca14)->((null) 25 2 0x32d45c (nil))
  fixme: shdocvw:ClOleCommandTarget_Exec (0x12ca14)->((null) 26 2 0x32d45c (nil))
  fixme: shdocvw:ClientSite_GetContainer (0x12ca14)->(0x32d4a0)
  fixme: shdocvw:ClOleCommandTarget_Exec (0x12ca14)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32d55c (nil))
  fixme: shdocvw:HttpNegotiate_BeginningTransaction (0x149020)->(L"" L"" 0 0x32d594)
  fixme: shdocvw:navigate_url Unsupported args (Flags 0x32dd80:3; TargetFrameName 0x32dd70: 8 )
  fixme: shdocvw:ClOleCommandTarget_QueryStatus (0x1487c4)->((null) 1 0x32d448 (nil))
  fixme: shdocvw:ClOleCommandTarget_Exec (0x1487c4)->((null) 25 2 0x32d45c (nil))
  fixme: shdocvw:ClOleCommandTarget_Exec (0x1487c4)->((null) 26 2 0x32d45c (nil))
  fixme: shdocvw:ClientSite_GetContainer (0x1487c4)->(0x32d4a0)
  fixme: shdocvw:ClOleCommandTarget_Exec (0x1487c4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32d55c (nil))
  fixme: shdocvw:HttpNegotiate_BeginningTransaction (0x137b890)->(L"" L"" 0 0x32d594)
  fixme: shdocvw: ClOleCommandTarget_Exec (0x12ca14)->((null) 29 2 0x32e4d4 (nil))
  fixme: shdocvw: DocHostUIHandler_GetDropTarget (0x12ca14)
  fixme: shdocvw: ClOleCommandTarget_Exec (0x1487c4)->((null) 29 2 0x32e4d4 (nil))
  fixme: shdocvw: DocHostUIHandler_GetDropTarget (0x1487c4)
  fixme: shdocvw: ClientSite_GetContainer (0x12ca14)->(0x32e44c)
  fixme: shdocvw: InPlaceFrame_SetStatusText (0x12ca14)->(0x6003eb71)
  fixme: shdocvw: ClOleCommandTarget_Exec (0x12ca14)->((null) 25 2 0x32e358 (nil))
  fixme: shdocvw: ClOleCommandTarget_Exec (0x12ca14)->((null) 26 2 0x32e358 (nil))
  fixme: shdocvw: ClientSite_GetContainer (0x1487c4)->(0x32e44c)
  fixme: shdocvw: InPlaceFrame_SetStatusText (0x1487c4)->(0x6003eb71)
  fixme: shdocvw: ClOleCommandTarget_Exec (0x1487c4)->((null) 25 2 0x32e358 (nil))
  fixme: shdocvw: ClOleCommandTarget_Exec (0x1487c4)->((null) 26 2 0x32e358 (nil))
  fixme: shdocvw: ClOleCommandTarget_Exec (0x12ca14)->((null) 21 2 (nil) (nil))
  fixme: shdocvw: ClOleCommandTarget_Exec (0x12ca14)->((null) 28 2 0x32e5c8 (nil))
  fixme: shdocvw: ClOleCommandTarget_Exec (0x1487c4)->((null) 21 2 (nil) (nil))
  fixme: shdocvw: ClOleCommandTarget_Exec (0x1487c4)->((null) 28 2 0x32e5c8 (nil))
  fixme: bidi:mirror stub: mirroring of characters not yet implemented
  fixme: shdocvw: OleInPlaceObject_InPlaceDeactivate (0x12c978 )
  fixme: mshtml:HlinkTarget_SetBrowseContext (0x14a560)->((nil))
  fixme: shdocvw: OleObject_Close (0x12c978 )->(1)
  fixme:shdocvw: OleInPlaceObject_InPlaceDeactivate (0x148728 )
  fixme:mshtml:HlinkTarget_SetBrowseContext (0x1380dd8 )->((nil))
  fixme:shdocvw: OleObject_Close (0x148728 )->(1)
  fixme:shell: DllCanUnloadNow stub
  fixme:msimtf: DllCanUnloadNow ()
  lukas@lukas-laptop ~/.wine/drive_c/GAMIGO/LastChaosPoland $ fixme:process:GetProcessWorkingSetSize (0xffffffff,0x33fbfc,0x33fc00): stub
  err: x11settings: X11DRV_ChangeDisplaySettingsEx No matching mode found 800x500x0 @0! (XRandR)
  err: x11settings: X11DRV_ChangeDisplaySettingsEx No matching mode found 1152x864x0 @0! (XRandR)
  err: x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1280x960x0 @0! (XRandR)
  err: x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1280x1024x0 @0! (XRandR)
  err: x11settings: X11DRV_ChangeDisplaySettingsEx No matching mode found 1600x1200x0 @0! (XRandR)
  fixme:win:EnumDisplayDevicesW ((null),0,0x33f084,0x00000000), stub!
  err: ole: CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
  err: ole: CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1
  fixme:dinput:DllCanUnloadNow (void): stub
  fixme:win:EnumDisplayDevicesW ((null),0,0x33f7fc,0x00000000), stub!
  fixme: d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
  err: d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
  fixme: d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
  fixme: d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
  err: d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
  fixme: d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
  do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
  Try adjusting the vblank_mode configuration parameter.
  fixme :d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
  err: d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
  fixme: d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
  fixme: d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
  err: d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
  fixme: d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
  fixme: d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
  err: d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
  fixme: d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
  fixme: d3d8:ValidateVertexShader (0xce39f0 (nil) (nil) 0 (nil)): stub
  fixme: d3d8:ValidatePixelShader (0xce3ef8 (nil) 0 (nil)): stub
  fixme: d3d8:ValidateVertexShader (0xce3f88 (nil) (nil) 0 (nil)): stub
  fixme: d3d8:ValidatePixelShader (0xc96120 (nil) 0 (nil)): stub
  fixme: d3d8:ValidateVertexShader (0xc96198 (nil) (nil) 0 (nil)): stub
  fixme: d3d8:ValidatePixelShader (0x2c50fa0 (nil) 0 (nil)): stub
  fixme: d3d8:ValidateVertexShader (0x2c513f0 (nil) (nil) 0 (nil)): stub
  fixme: d3d8:ValidatePixelShader (0x2c519a8 (nil) 0 (nil)): stub
  fixme: d3d8:ValidateVertexShader (0x2c51db8 (nil) (nil) 0 (nil)): stub
  fixme: d3d8:ValidatePixelShader (0x2c523a8 (nil) 0 (nil)): stub
  fixme: d3d8:ValidateVertexShader (0x2c527b0 (nil) (nil) 0 (nil)): stub
  fixme: d3d8:ValidatePixelShader (0x2c52db0 (nil) 0 (nil)): stub
  fixme: wininet:InternetCheckConnectionW 
  wine: Unhandled exception 0xe06d7363 at address 0x7b8453f0 (thread 0024), starting debugger...
  Unhandled exception: C++ exception(object = 0x0033f9a0, type = 0x1052ec8c) in 32-bit code (0x7b845442).
  Register dump:
   CS: 0073 SS: 007b DS: 007b ES: 007b FS:0033 GS: 003b
   EIP:7b845442 ESP: 0033f280 EBP: 0033f2e4 EFLAGS: 00000246(   - 00      - IZP1)
   EAX:7b82ecc9 EBX:7b8b6ff4 ECX: 00000000 EDX:e06d7363
   ESI:e06d7363 EDI:03401fa8
  Stack dump:
  0x0033f280:  0033f300 0000000c 0000003c e06d7363
  0x0033f290:  00000001 00000000 7b8453f0 00000003
  0x0033f2a0:  19930520 0033f9a0 1052ec8c 0033f2c0
  0x0033f2b0:  00000000 00000002 00110000 0033f2ec
  0x0033f2c0:  10411a41 03401fa8 60655ff4 03401fa8
  0x0033f2d0:  03401fa8 0033f304 7b8453fa 60655ff4
  Backtrace:
  =>1 0x7b845442 in kernel32 (+0x25442) (0x0033f2e4)
    2 0x6062a00c _CxxThrowException+0x3c() in msvcrt (0x0033f314)
    3 0x100e5b8e in engine (+0xe5b8e) (0x0033fa9c)
    4 0x102dc8f2 in engine (+0x2dc8f2) (0x0033fd58 )
    5 0x004040be in nksp (+0x40be) (0x0033fdb4)
    6 0x0040502b in nksp (+0x502b) (0x0033fe20)
    7 0x00405828 in nksp (+0x5828) (0x0033fe6c)
    8 0x00407d2c in nksp (+0x7d2c) (0x0033ff08)
    9 0x7b877f48 in kernel32 (+0x57f48) (0x0033ffe8 )
    10 0x60024b77 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
  0x7b845442: subl    $4,%esp
  Modules:
  Module    Address            Debug info    Name (114 modules)
  PE      340000-  347000    Deferred        vorbisfile
  PE      350000-  356000    Deferred        ogg
  PE      3a0000-  3b7000    Deferred        vorbis
  PE      3c0000-  3da000    Deferred        gamemp
  PE      400000-  44c000    Export          nksp
  PE      450000-  697000    Deferred        entitiesmp
  PE    10000000-106b4000    Export          engine
  ELF    60000000-6001d000    Deferred        ld-linux.so.2
  ELF    6001d000-60153000    Export          libwine.so.1
  ELF    60153000-6015b000    Deferred        libnss_compat.so.2
  ELF    6015b000-60172000    Deferred        libnsl.so.1
  ELF    60172000-6017d000    Deferred        libnss_nis.so.2
  ELF    6017d000-60189000    Deferred        libnss_files.so.2
  ELF    60189000-602d4000    Deferred        user32<elf>
    \-PE    601a0000-602d4000    \               user32
  ELF    602d4000-60373000    Deferred        gdi32<elf>
    \-PE    602e0000-60373000    \               gdi32
  ELF    60373000-603c5000    Deferred        advapi32<elf>
    \-PE    60380000-603c5000    \               advapi32
  ELF    603c5000-60415000    Deferred        wininet<elf>
    \-PE    603d0000-60415000    \               wininet
  ELF    60415000-60438000    Deferred        mpr<elf>
    \-PE    60420000-60438000    \               mpr
  ELF    60438000-60493000    Deferred        shlwapi<elf>
    \-PE    60450000-60493000    \               shlwapi
  ELF    60493000-605a7000    Deferred        shell32<elf>
    \-PE    604a0000-605a7000    \               shell32
  ELF    605a7000-605d4000    Deferred        ws2_32<elf>
    \-PE    605b0000-605d4000    \               ws2_32
  ELF    605d4000-605f3000    Deferred        iphlpapi<elf>
    \-PE    605e0000-605f3000    \               iphlpapi
  ELF    605f3000-60607000    Deferred        libresolv.so.2
  ELF    60607000-60671000    Export          msvcrt<elf>
    \-PE    60620000-60671000    \               msvcrt
  ELF    60671000-60692000    Deferred        imm32<elf>
    \-PE    60680000-60692000    \               imm32
  ELF    60692000-60711000    Deferred        libfreetype.so.6
  ELF    60711000-60727000    Deferred        libz.so.1
  ELF    60727000-6074e000    Deferred        libexpat.so.1
  ELF    6074e000-60769000    Deferred        libice.so.6
  ELF    60769000-6076f000    Deferred        libxxf86vm.so.1
  ELF    6076f000-6077f000    Deferred        libxext.so.6
  ELF    6077f000-608ae000    Deferred        libx11.so.6
  ELF    608ae000-608b3000    Deferred        libuuid.so.1
  ELF    608b3000-608b7000    Deferred        libxau.so.6
  ELF    608b7000-608d5000    Deferred        libxcb.so.1
  ELF    608d5000-608da000    Deferred        libxdmcp.so.6
  ELF    608da000-608dd000    Deferred        libxinerama.so.1
  ELF    608dd000-608e6000    Deferred        libxrandr.so.2
  ELF    608e6000-608ea000    Deferred        libxcomposite.so.1
  ELF    608ea000-608f0000    Deferred        libxfixes.so.3
  ELF    608f0000-60923000    Deferred        uxtheme<elf>
    \-PE    60900000-60923000    \               uxtheme
  ELF    60923000-60986000    Deferred        rpcrt4<elf>
    \-PE    60930000-60986000    \               rpcrt4
  ELF    60986000-609bd000    Deferred        winealsa<elf>
    \-PE    60990000-609bd000    \               winealsa
  ELF    609bd000-60a84000    Deferred        libasound.so.2
  ELF    60a84000-60a8d000    Deferred        librt.so.1
  ELF    60a8d000-60a90000    Deferred        libxdamage.so.1
  ELF    60a90000-60ad0000    Deferred        libpulse.so.0
  ELF    60ad0000-60ad6000    Deferred        libxtst.so.6
  ELF    60ad6000-60adf000    Deferred        libwrap.so.0
  ELF    60adf000-60b18000    Deferred        libdbus-1.so.3
  ELF    60b18000-60b41000    Deferred        libvorbis.so.0
  ELF    60b41000-60b48000    Deferred        libogg.so.0
  ELF    60b48000-60b4f000    Deferred        libasound_module_pcm_pulse.so
  ELF    60b4f000-60b67000    Deferred        msacm32<elf>
    \-PE    60b50000-60b67000    \               msacm32
  ELF    60b67000-60b8f000    Deferred        msacm32<elf>
    \-PE    60b70000-60b8f000    \               msacm32
  ELF    60b8f000-60ba5000    Deferred        midimap<elf>
    \-PE    60b90000-60ba5000    \               midimap
  ELF    60ba5000-60bd1000    Deferred        d3d8<elf>
    \-PE    60bb0000-60bd1000    \               d3d8
  ELF    60bd1000-60bd5000    Deferred        libnss_mdns4_minimal.so.2
  ELF    60bd5000-60c0d000    Deferred        dinput<elf>
    \-PE    60be0000-60c0d000    \               dinput
  ELF    60ce1000-60d45000    Deferred        libgl.so.1
  ELF    60d45000-60fd5000    Deferred        i915_dri.so
  ELF    60fd5000-610e5000    Deferred        wined3d<elf>
    \-PE    60ff0000-610e5000    \               wined3d
  ELF    61723000-61868000    Deferred        libc.so.6
  ELF    64a57000-64a61000    Deferred        libdrm.so.2
  ELF    6535b000-653ab000    Deferred        libflac.so.8
  ELF    671ee000-671f8000    Deferred        libdrm_intel.so.1
  ELF    683ca000-683d3000    Deferred        libsm.so.6
  ELF    68f33000-68f48000    Deferred        winejoystick<elf>
    \-PE    68f40000-68f48000    \               winejoystick
  ELF    6918d000-69250000    Deferred        comctl32<elf>
    \-PE    691a0000-69250000    \               comctl32
  ELF    693d0000-693f6000    Deferred        libm.so.6
  ELF    69c04000-69c08000    Deferred        libdl.so.2
  ELF    6b0be000-6b0d7000    Deferred        libpthread.so.0
  ELF    6d101000-6d16d000    Deferred        libsndfile.so.1
  ELF    6deaa000-6ded7000    Deferred        libfontconfig.so.1
  ELF    6e043000-6e0e9000    Deferred        ole32<elf>
    \-PE    6e050000-6e0e9000    \               ole32
  ELF    6e13c000-6e15a000    Deferred        libgcc_s.so.1
  ELF    6f4be000-6f5ba000    Deferred        libvorbisenc.so.2
  ELF    6f7e0000-6f7e7000    Deferred        libnss_dns.so.2
  ELF    71576000-71610000    Deferred        winex11<elf>
    \-PE    71580000-71610000    \               winex11
  ELF    71b15000-71ba9000    Deferred        winmm<elf>
    \-PE    71b20000-71ba9000    \               winmm
  ELF    7246f000-724b9000    Deferred        libpulsecommon-0.9.19.so
  PE    780c0000-78121000    Deferred        msvcp60
  ELF    7934d000-79358000    Deferred        libxcursor.so.1
  ELF    7b800000-7b93c000    Export          kernel32<elf>
    \-PE    7b820000-7b93c000    \               kernel32
  ELF    7bc00000-7bca7000    Deferred        ntdll<elf>
    \-PE    7bc10000-7bca7000    \               ntdll
  ELF    7bf00000-7bf04000    Deferred        <wine-loader>
  ELF    7ca13000-7ca1d000    Deferred        libxrender.so.1
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
  00000023 (D) C:\GAMIGO\LastChaosPoland\Bin\Nksp.exe
      00000027   15
      00000025   15
      00000024    0 <==
  Backtrace:
  =>1 0x7b845442 in kernel32 (+0x25442) (0x0033f2e4)
    2 0 x 6062a00c _CxxThrowException+0x3c() in msvcrt (0x0033f314)
    3 0 x 100e5b8e in engine (+0xe5b8e) (0 x 0033fa9c )
    4 0 x 102dc8f2 in engine (+0x2dc8f2) (0 x 0033fd58 )
    5 0 x 004040be in nksp (+0x40be) (0 x 0033fdb4)
    6 0 x 0040502b in nksp (+0x502b) (0 x 0033fe20 )
    7 0 x 00405828 in nksp (+0x5828) (0 x 0033fe6c )
    8 0 x 00407d2c in nksp (+0x7d2c) (0 x 0033ff08 )
    9 0 x 7b877f48 in kernel32 (+0x57f48) (0 x 0033ffe8 )
    10 0 x 60024b77 wine_switch_to_stack+0x17() in libwine.so.1 (0 x 00000000 )
  err:seh:raise_exception Unhandled exception code e06d7363 flags 1 addr 0x7b8453f0

---

### Post by drone0050 on 2010-04-25
Anyone have a Solution for this? I really dont want to use windows anymore....

---

### Post by cogadh on 2010-04-25
The game doesn't have consistent results according to AppDB, you might be stuck until Wine matures a bit more:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4394](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4394)

---

