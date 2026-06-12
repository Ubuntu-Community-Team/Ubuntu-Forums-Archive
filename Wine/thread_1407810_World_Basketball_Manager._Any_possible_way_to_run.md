---
title: "World Basketball Manager. Any possible way to run?"
date: 2010-02-15
forum: Wine
---

### Post by keturidu on 2010-02-15
I'm in struggle to let the game run. The best result i've got is "run-time error 76" which led me to nothing.
Tried various ways to run the game. winetricks, playonlinux. No result. 

I'm using Ubuntu x64. Wine - 1.36. Nvidia 8600.

Install dependencies:
      Windows Installer 3.1 -> OK
      Microsoft .NET Framework 2.0 Service Pack 1
      Microsoft Jet 4.0 Database Engine
      Microsoft Visual C++ 2008 Redistributable

I install only WBM mini game 2009, then install with winetricks dotnet20, vcrun2008, jet40, gdiplus. The result i got:

```
keturidu@keturidu:~/.wine/drive_c/Program Files/WBM Euro 2009 Edition$ wine WBM.exe
fixme:sync:CreateMemoryResourceNotification (0) stub
err:ole:CoGetContextToken apartment not initialised
fixme:win:EnumDisplayDevicesW ((null),0,0x32da38,0x00000000), stub!
fixme:dciman:DCICreatePrimary 0x600 0x3a922ac
fixme:win:EnumDisplayDevicesW ((null),0,0x32ebcc,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
keturidu@keturidu:~/.wine/drive_c/Program Files/WBM Euro 2009 Edition$ 

```

The game uses: [[IMG]http://img63.imageshack.us/img63/1480/wbmfiles.th.png[/IMG]](http://img63.imageshack.us/i/wbmfiles.png/)

Games loaded modules (currently running in virtualbox):

```
                       Loaded Modules...
                       C:\Program Files\World Basketball Manager 2009\WBM.exe 1.9.5.2666
                       C:\WINDOWS\system32\ntdll.dll 5.1.2600.5755 (xpsp_sp3_gdr.090206-1234)
                       C:\WINDOWS\system32\mscoree.dll 2.0.50727.3053 (netfxsp.050727-3000)
                       C:\WINDOWS\system32\KERNEL32.dll 5.1.2600.5781 (xpsp_sp3_gdr.090321-1317)
                       C:\WINDOWS\system32\advapi32.dll 5.1.2600.5755 (xpsp_sp3_gdr.090206-1234)
                       C:\WINDOWS\system32\RPCRT4.dll 5.1.2600.5795 (xpsp_sp3_gdr.090415-1241)
                       C:\WINDOWS\system32\Secur32.dll 5.1.2600.5834 (xpsp_sp3_gdr.090624-1305)
                       C:\Program Files\World Basketball Manager 2009\protect.dll 5.60.002.008
                       C:\WINDOWS\system32\USER32.dll 5.1.2600.5512 (xpsp.080413-2105)
                       C:\WINDOWS\system32\GDI32.dll 5.1.2600.5698 (xpsp_sp3_gdr.081022-1932)
                       C:\WINDOWS\system32\VERSION.dll 5.1.2600.5512 (xpsp.080413-2105)
                       C:\WINDOWS\system32\IMM32.DLL 5.1.2600.5512 (xpsp.080413-2105)
                       C:\WINDOWS\system32\setupapi.dll 5.1.2600.5512 (xpsp.080413-2111)
                       C:\WINDOWS\system32\msvcrt.dll 7.0.2600.5512 (xpsp.080413-2111)
                       C:\WINDOWS\system32\SHLWAPI.dll 6.00.2900.5512 (xpsp.080413-2105)
                       c:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\mscorwks.dll 2.0.50727.3082 (QFE.050727-3000)
                       C:\WINDOWS\WinSxS\x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.3053_x-ww_b80fa8ca\MSVCR80.dll 8.00.50727.3053
                       C:\WINDOWS\system32\shell32.dll 6.00.2900.5622 (xpsp_sp3_gdr.080617-1319)
                       C:\WINDOWS\WinSxS\x86_Microsoft.Windows.Common-Controls_6595b64144ccf1df_6.0.2600.5512_x-ww_35d4ce83\comctl32.dll 6.0 (xpsp.080413-2105)
                       C:\WINDOWS\system32\comctl32.dll 5.82 (xpsp.080413-2105)
                       C:\WINDOWS\assembly\NativeImages_v2.0.50727_32\mscorlib\6d667f19d687361886990f3ca0f49816\mscorlib.ni.dll 2.0.50727.3082 (QFE.050727-3000)
                       C:\WINDOWS\system32\ole32.dll 5.1.2600.5512 (xpsp.080413-2108)
                       C:\WINDOWS\system32\MSCTF.dll 5.1.2600.5512 (xpsp.080413-2105)
                       c:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\mscorjit.dll 2.0.50727.3082 (QFE.050727-3000)
                       C:\WINDOWS\system32\xpsp2res.dll 5.1.2600.5512 (xpsp.080413-2113)
                       C:\Program Files\World Basketball Manager 2009\Icehole.Framework.Core.dll 0.0.668
                       C:\WINDOWS\assembly\NativeImages_v2.0.50727_32\System\80978a322d7dd39f0a71be1251ae395a\System.ni.dll 2.0.50727.3053 (netfxsp.050727-3000)
                       C:\WINDOWS\assembly\NativeImages_v2.0.50727_32\System.Drawing\3da96ee075bab9202626ae44c18d226c\System.Drawing.ni.dll 2.0.50727.3053 (netfxsp.050727-3000)
                       C:\WINDOWS\assembly\NativeImages_v2.0.50727_32\System.Windows.Forms\63406259e94d5c0ff5b79401dfe113ce\System.Windows.Forms.ni.dll 2.0.50727.3053 (netfxsp.050727-3000)
                       C:\Program Files\World Basketball Manager 2009\WBM.Data.dll 1.9.5.2666
                       C:\Program Files\World Basketball Manager 2009\Icehole.Framework.Game.dll 0.0.668
                       C:\WINDOWS\system32\shfolder.dll 6.00.2900.5512 (xpsp.080413-2105)
                       C:\WINDOWS\assembly\NativeImages_v2.0.50727_32\System.Xml\773a9786013451d3baaeff003dc4230f\System.Xml.ni.dll 2.0.50727.3082 (QFE.050727-3000)
                       C:\WINDOWS\system32\uxtheme.dll 6.00.2900.5512 (xpsp.080413-2105)
                       C:\WINDOWS\WinSxS\x86_Microsoft.Windows.GdiPlus_6595b64144ccf1df_1.0.6001.22319_x-ww_f0b4c2df\gdiplus.dll 5.2.6001.22319 (vistasp1_ldr.081126-1506)
                       C:\WINDOWS\system32\msctfime.ime 5.1.2600.5512 (xpsp.080413-2105)
                       C:\WINDOWS\system32\dciman32.dll 5.1.2600.5512 (xpsp.080413-2105)
                       C:\WINDOWS\assembly\NativeImages_v2.0.50727_32\System.Data\c70731047b0022638b3f9fb158948a03\System.Data.ni.dll 2.0.50727.3053 (netfxsp.050727-3000)
                       C:\WINDOWS\assembly\GAC_32\System.Data\2.0.0.0__b77a5c561934e089\System.Data.dll 2.0.50727.3053 (netfxsp.050727-3000)
                       C:\WINDOWS\system32\WS2_32.dll 5.1.2600.5512 (xpsp.080413-0852)
                       C:\WINDOWS\system32\WS2HELP.dll 5.1.2600.5512 (xpsp.080413-0852)
                       C:\WINDOWS\system32\CRYPT32.dll 5.131.2600.5512 (xpsp.080413-2113)
                       C:\WINDOWS\system32\MSASN1.dll 5.1.2600.5875 (xpsp_sp3_gdr.090904-1413)
                       C:\WINDOWS\assembly\NativeImages_v2.0.50727_32\System.Configuration\b82c00e2d24305ad6cb08556e3779b75\System.Configuration.ni.dll 2.0.50727.3053 (netfxsp.050727-3000)
                       C:\WINDOWS\assembly\NativeImages_v2.0.50727_32\System.Transactions\5a555c9ae6984c40157cf940bb519f7c\System.Transactions.ni.dll 2.0.50727.3053 (netfxsp.050727-3000)
                       C:\WINDOWS\assembly\GAC_32\System.Transactions\2.0.0.0__b77a5c561934e089\System.Transactions.dll 2.0.50727.3053 (netfxsp.050727-3000)
                       C:\WINDOWS\system32\sxs.dll 5.1.2600.5512 (xpsp.080413-2111)
                       C:\WINDOWS\system32\CLBCATQ.DLL 2001.12.4414.700
                       C:\WINDOWS\system32\COMRes.dll 2001.12.4414.700
                       C:\WINDOWS\system32\OLEAUT32.dll 5.1.2600.5512
                       C:\Program Files\Common Files\System\Ole DB\oledb32.dll 2.81.1132.0 (xpsp.080413-0852)
                       C:\WINDOWS\system32\MSDART.DLL 2.81.1132.0 (xpsp.080413-0852)
                       C:\WINDOWS\system32\comdlg32.dll 6.00.2900.5512 (xpsp.080413-2105)
                       C:\Program Files\Common Files\System\Ole DB\OLEDB32R.DLL 2.81.1132.0 (xpsp.080413-0852)
                       C:\WINDOWS\system32\msjetoledb40.dll 4.00.9502.0
                       C:\WINDOWS\system32\msjet40.dll 4.00.9511.0
                       C:\WINDOWS\system32\mswstr10.dll 4.00.9502.0
                       C:\WINDOWS\system32\msjter40.dll 4.00.9502.0
                       C:\WINDOWS\system32\MSJINT40.DLL 4.00.9502.0
                       C:\WINDOWS\system32\comsvcs.dll 2001.12.4414.702
                       C:\WINDOWS\system32\colbact.DLL 2001.12.4414.700
                       C:\WINDOWS\system32\MTXCLU.DLL 2001.12.4414.706
                       C:\WINDOWS\system32\WSOCK32.dll 5.1.2600.5512 (xpsp.080413-0852)
                       C:\WINDOWS\system32\NETAPI32.dll 5.1.2600.5694 (xpsp_sp3_gdr.081015-1312)
                       C:\WINDOWS\system32\CLUSAPI.DLL 5.1.2600.5512 (xpsp.080413-2111)
                       C:\WINDOWS\system32\RESUTILS.DLL 5.1.2600.5512 (xpsp.080413-2111)
                       C:\WINDOWS\system32\USERENV.dll 5.1.2600.5512 (xpsp.080413-2113)
                       C:\WINDOWS\assembly\NativeImages_v2.0.50727_32\System.EnterpriseSe#\4267bd908175603006c6c90bb5d900c7\System.EnterpriseServices.ni.dll 2.0.50727.3053 (netfxsp.050727-3000)
                       C:\WINDOWS\assembly\NativeImages_v2.0.50727_32\System.EnterpriseSe#\4267bd908175603006c6c90bb5d900c7\System.EnterpriseServices.Wrapper.dll 2.0.50727.3053 (netfxsp.050727-3000)
                       C:\WINDOWS\assembly\GAC_32\System.EnterpriseServices\2.0.0.0__b03f5f7f11d50a3a\System.EnterpriseServices.Wrapper.dll 2.0.50727.3053 (netfxsp.050727-3000)
                       C:\WINDOWS\system32\msjtes40.dll 4.00.9502.0
                       C:\WINDOWS\system32\VBAJET32.DLL 6.1.9431
                       C:\WINDOWS\system32\expsrv.dll 6.0.9589
                       C:\Program Files\World Basketball Manager 2009\Icehole.WBM.Controls.dll 1.9.5.2666
                       C:\Program Files\World Basketball Manager 2009\SlimDX.dll 
                       C:\WINDOWS\WinSxS\x86_Microsoft.VC90.CRT_1fc8b3b9a1e18e3b_9.0.30729.1_x-ww_6f74963e\MSVCR90.dll 9.00.30729.1
                       C:\WINDOWS\system32\WINMM.dll 5.1.2600.5512 (xpsp.080413-0845)
                       C:\WINDOWS\WinSxS\x86_Microsoft.VC90.CRT_1fc8b3b9a1e18e3b_9.0.30729.1_x-ww_6f74963e\msvcm90.dll 9.00.30729.1
                       C:\WINDOWS\WinSxS\x86_Microsoft.VC90.CRT_1fc8b3b9a1e18e3b_9.0.30729.1_x-ww_6f74963e\MSVCP90.dll 9.00.30729.1
                       C:\WINDOWS\system32\rsaenh.dll 5.1.2600.5507 (xpsp.080318-1711)
                       C:\WINDOWS\system32\d3d9.dll 5.3.1.904
                       C:\WINDOWS\system32\wined3d.dll 
                       C:\WINDOWS\system32\libwine.dll 
                       C:\WINDOWS\system32\opengl32.dll 5.1.2600.5512 (xpsp.080413-0845)
                       C:\WINDOWS\system32\GLU32.dll 5.1.2600.5512 (xpsp.080413-0845)
                       C:\WINDOWS\system32\DDRAW.dll 5.03.2600.5512 (xpsp.080413-0845)
                       C:\WINDOWS\system32\VBoxOGL.dll 3.0.10.54097
                       C:\WINDOWS\system32\VBoxOGLcrutil.dll 3.0.10.54097
                       C:\WINDOWS\System32\mswsock.dll 5.1.2600.5625 (xpsp_sp3_gdr.080620-1249)
                       C:\WINDOWS\system32\DNSAPI.dll 5.1.2600.5625 (xpsp_sp3_gdr.080620-1249)
                       C:\WINDOWS\System32\winrnr.dll 5.1.2600.5512 (xpsp.080413-2113)
                       C:\WINDOWS\system32\WLDAP32.dll 5.1.2600.5512 (xpsp.080413-2113)
                       C:\WINDOWS\system32\VBoxOGLpackspu.dll 3.0.10.54097
                       C:\WINDOWS\system32\VBoxOGLerrorspu.dll 3.0.10.54097
                       C:\WINDOWS\system32\VBoxOGLfeedbackspu.dll 3.0.10.54097
                       C:\WINDOWS\system32\VBoxOGLpassthroughspu.dll 3.0.10.54097
                       C:\WINDOWS\system32\VBoxOGLarrayspu.dll 3.0.10.54097
                       C:\WINDOWS\system32\d3dx9_39.dll 9.24.949.2307
                       C:\Program Files\World Basketball Manager 2009\Icehole.Framework.UI.SlimDX.dll 0.0.668
                       C:\Program Files\World Basketball Manager 2009\Icehole.Framework.UI.dll 0.0.668
                       C:\WINDOWS\system32\psapi.dll 5.1.2600.5512 (xpsp.080413-2105)
```

[Free version minigame (it's actually the same game, just with some in game playing limitations)]("http://www.wbmgame.com/files/WBMEuro2009.exe")
[Demo version]("http://www.wbmgame.com/files/wbm10setup.exe")

---

