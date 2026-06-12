---
title: "Photoshop CS4 extended"
date: 2009-04-17
forum: Wine
---

### Post by Rackstar on 2009-04-17
Hi,

I know PS CS4 is a long shot. But if I look at the appdb, I can see a lot of people getting it to work. 

There is a how-to here:
[http://ubuntuforums.org/showthread.php?t=1004998&page=4](http://ubuntuforums.org/showthread.php?t=1004998&page=4)

I can start the setup.exe but I get the following:
[http://www.ninetynine.be/screens/b71aba0d26dcf390b8da9dae535038c0c592dc7f.png](http://www.ninetynine.be/screens/b71aba0d26dcf390b8da9dae535038c0c592dc7f.png)

EDIT: the error in english: The setup has discovered an error. Please contact customer support.

Can anybody help me? I'm a photographer and I paid for photoshop, I have been using a different desktop with vista for now, but getting sick of the space it takes in my office. Would be great if I could run it here.

---

### Post by Rackstar on 2009-04-17
Sorry forgot my specs:

Ubuntu 8.10
Wine 1.1.19 (latest)
winetricks
installed all the dll's said in the post above. (And probably more)

---

### Post by Rackstar on 2009-04-17
Hi again,

I tried copying my install of my vista to my ubuntu.

It seems that he doesn't find some dll's, but the dll's are in that directory or in another Adobe directory. How do I get it to recognize them?

```
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library data_flow.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library image_runtime.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library image_flow.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library image_runtime.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library data_flow.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\PlugPlug.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\PlugPlug.dll") not found
err:module:import_dll Library PlugPlug.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\AdobeOwl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\AdobeOwl.dll") not found
err:module:import_dll Library AdobeOwl.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\AdobeOwlCanvas.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\AdobeOwlCanvas.dll") not found
err:module:import_dll Library AdobeOwlCanvas.dll (which is needed by L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Programma Bestanden\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe" failed, status c0000135

```

EDIT: I copied the two dll's msvcp80.dll and msvcr80.dll to the photoshop directory and then it show the popup to accept the license. I click accept, it crashes:

```
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SetProcessDPIAware stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2e8,0x00000000), stub!
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x1c25ec 0x1c25f8 0x1c2640 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x1c5244 0x1c5250 0x1c2a10 (nil)
fixme:shdocvw:PersistStreamInit_InitNew (0x1c6c98)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32cf0c:3; TargetFrameName 0x32cefc:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:bind_to_object BindToObject failed: 80004005
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1c6c98)->(0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32cf30:3; TargetFrameName 0x32cf20:8)
fixme:keyboard:RegisterHotKey (0x1002e,1634497586,0x00000001,50): stub
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32c88c
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800012c)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800012c)
fixme:iphlpapi:NotifyAddrChange (Handle 0x8dfe898, overlapped 0x8dfe8a0): stub
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[1cdeb8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1c6d38)->((null) 1 0x32ce24 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->((null) 25 2 0x32ce38 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->((null) 26 2 0x32ce38 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1c6d38)->(0x32ce74)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32cf48 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32cfd8)
fixme:jscript:JScriptProperty_SetProperty (0x9388178)->(70000001 (nil) 0x32c2f8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c2e8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c2e8)
fixme:mshtml:OmNavigator_get_appName (0x98bacd8)->(0x32bd38)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->((null) 29 2 0x32d518 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1c6d38)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d428)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d428)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d428)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:shdocvw:ClientSite_GetContainer (0x1c6d38)->(0x32d644)
fixme:mshtml:fire_event node type 9 node supported
err:mshtml:handle_htmlevent Could not get nsIDOMNode: 80004002
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1c6d38)->(0xb7f96051)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->((null) 25 2 0x32d578 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->((null) 26 2 0x32d578 (nil))
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:HTMLElement_get_className NULL nselem
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32d6d0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32d6d0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->((null) 26 2 0x32d798 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->((null) 29 2 0x32d7a8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1c6d38)->(0x7bcaeb3b)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->((null) 28 2 0x32d6d0 (nil))
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x1c6d38)->((null) 21 2 (nil) (nil))
fixme:keyboard:UnregisterHotKey (0x1002e,1634497586): stub
fixme:mshtml:fire_event node type 9 node supported
err:mshtml:handle_htmlevent Could not get nsIDOMNode: 80004002
fixme:mshtml:fire_event node type 9 node supported
err:mshtml:handle_htmlevent Could not get nsIDOMNode: 80004002
err:ole:ITypeInfo_fnInvoke did not find member id 1088, flags 0x2!
fixme:shdocvw:OleObject_Close (0x1c6c98)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1c6c98)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x1c88f8)->((nil))
fixme:jscript:JScript_SetScriptState unimplemented state 3
fixme:shdocvw:OleObject_Close (0x1c6c98)->(1)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x98d97a4 0x98d97b0 0x9365318 (nil)

```

This is above all my knowledge. Any help would be hugely appreciated

---

### Post by NightMKoder on 2009-04-17
Really wouldn't suggest copying from your windows partition. Wine has a registry like windows, and you can't copy everything (ie some files install to other places).

First, try starting with a fresh wine prefix (delete your ~/.wine).
Next execute:
```

wget http://www.kegel.com/wine/winetricks
sh winetricks msxml6 gdiplus gecko vcrun2005

```
(last one is for msvcr80.dll, which photoshop apparently uses)

then try installing photoshop. If it still fails, post the console output for the install.

---

### Post by Rackstar on 2009-04-17
Hi,

Thanks for doing this for me. I really appreciate it.

```
Begin Adobe Setup

UI mode: Full GUI

fixme:console:AttachConsole stub ffffffff
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\.svg" 4 4 (nil) (nil) 0x132798 (nil)
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Classes\\.svgz" 4 4 (nil) (nil) 0x132798 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x1452bc 0x1452c8 0x144d78 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x144dd4 0x144de0 0x1462d8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x145f54 0x145f60 0x145c88 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x144c4c 0x144c58 0x1462d8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x145f54 0x145f60 0x146240 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x145fc4 0x145fd0 0x1476d8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x147654 0x147660 0x1462d8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x147654 0x147660 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x147e5c 0x147e68 0x147688 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x1486c4 0x1486d0 0x147eb8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x148734 0x148740 0x1462d8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x146254 0x146260 0x147eb8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x1462c4 0x1462d0 0x147688 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x145c9c 0x145ca8 0x145cd8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x147b54 0x147b60 0x147b90 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x147b9c 0x147ba8 0x147688 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x1476e4 0x1476f0 0x147bb0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x147ecc 0x147ed8 0x147f08 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x146b7c 0x146b88 0x146c50 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x14ad9c 0x14ada8 0x14ae70 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x153d24 0x153d30 0x153df8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x14a5a4 0x14a5b0 0x14a678 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x14a614 0x14a620 0x14a6e8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x14a684 0x14a690 0x153d80 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x14a6f4 0x14a700 0x153e18 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x153d94 0x153da0 0x153e68 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x153e04 0x153e10 0x153ed8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x155c0c 0x155c18 0x153e60 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x155c7c 0x155c88 0x146bb0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x153e74 0x153e80 0x153eb0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x1454a4 0x1454b0 0x153ed0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x1454ec 0x1454f8 0x1455c0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x14555c 0x145568 0x145598 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x1455cc 0x1455d8 0x14ae90 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x149e5c 0x149e68 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x146c54 0x146c60 0x14adf8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x146cc4 0x146cd0 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x14c84c 0x14c858 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x15a074 0x15a080 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x15a0e4 0x15a0f0 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x15a154 0x15a160 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x15a1c4 0x15a1d0 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x15b274 0x15b280 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x15ac6c 0x15ac78 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x163044 0x163050 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x16308c 0x163098 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x160ffc 0x161008 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x14c84c 0x14c858 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x14c8bc 0x14c8c8 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x14c92c 0x14c938 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x1620dc 0x1620e8 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x16214c 0x162158 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x161e0c 0x161e18 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x161e7c 0x161e88 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x15acfc 0x15ad08 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x15ad44 0x15ad50 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x15adb4 0x15adc0 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x14ae54 0x14ae60 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x14ae54 0x14ae60 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x1610b4 0x1610c0 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x161124 0x161130 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x149e5c 0x149e68 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x16b7b4 0x16b7c0 0x1455e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x16b824 0x16b830 0x1471e0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x16b824 0x16b830 0x14aed8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x16a674 0x16a680 0x16a578 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x16a674 0x16a680 0x16a560 (nil)
fixme:shdocvw:PersistStreamInit_InitNew (0x14ae40)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32e794:3; TargetFrameName 0x32e784:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:bind_to_object BindToObject failed: 80004005
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32e7b8:3; TargetFrameName 0x32e7a8:8)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x14ae40)->(0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32e7e0:3; TargetFrameName 0x32e7d0:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32e9f0
fixme:iphlpapi:NotifyAddrChange (Handle 0x654e898, overlapped 0x654e8a0): stub
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[182db8]: nsNativeModuleLoader::LoadModule("c:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x14aee0)->((null) 1 0x32ef88 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 25 2 0x32ef9c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 26 2 0x32ef9c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x14aee0)->(0x32efd8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32f0ac (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f13c)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x173298)->((nil))
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x14aee0)->((null) 1 0x32ef68 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 25 2 0x32ef7c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 26 2 0x32ef7c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x14aee0)->(0x32efb8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32f08c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f11c)
fixme:jscript:JScriptProperty_SetProperty (0x696a898)->(70000001 (nil) 0x32e43c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e42c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e42c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e42c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e42c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e42c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 29 2 0x32f40c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x14aee0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f31c)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f31c)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
err:mshtml:nsChannelBSC_stop_binding RemoveRequest failed: 80004005
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f31c)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32f31c)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:shdocvw:ClientSite_GetContainer (0x14aee0)->(0x32f788)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x14aee0)->(0xb7e12051)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 25 2 0x32f6bc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 26 2 0x32f6bc (nil))
fixme:shdocvw:ClientSite_GetContainer (0x14aee0)->(0x32f788)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x14aee0)->(0xb7e12051)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 25 2 0x32f6bc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 26 2 0x32f6bc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32f6ec)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32f6ec)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 26 2 0x32f7b4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 29 2 0x32f7c4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x14aee0)->(0x7bcae9a0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 28 2 0x32f6ec (nil))
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x21ff8c 0x21ff98 0x6b49e38 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x6b4fddc 0x6b4fde8 0x6b501a0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x6be2bac 0x6be2bb8 0x6be2cb0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x717874c 0x7178758 0x7178850 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x7178a44 0x7178a50 0x7177be8 (nil)
fixme:advapi:LookupAccountNameW (null) L"ruben" (nil) 0x706dbb8 (nil) 0x706dbbc 0x706dbb0 - stub
fixme:advapi:LookupAccountNameW (null) L"ruben" 0x718f258 0x706dbb8 0x718edf8 0x706dbbc 0x706dbb0 - stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x719a914 0x719a920 0x7186e68 (nil)
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x14aee0)->((null) 21 2 (nil) (nil))
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetNamedSecurityInfoW L"C:\\Programma Bestanden\\Gemeenschappelijke Bestanden\\Adobe\\caps" 1 -2147483644 0x719970c 0x7199718 0x71997e0 (nil)
err:msi:ITERATE_Actions Execution halted, action L"ProcessPropertyFile.E35C3ECB_5FDA_49E1_AB1F_D472B7CB9017" returned 1603
fixme:shdocvw:PersistStreamInit_InitNew (0x71f6618)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32cc10:3; TargetFrameName 0x32cc00:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:bind_to_object BindToObject failed: 80004005
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32cc34:3; TargetFrameName 0x32cc24:8)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x71f6618)->(0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32cc5c:3; TargetFrameName 0x32cc4c:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x71f66b8)->((null) 1 0x32c950 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 25 2 0x32c964 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 26 2 0x32c964 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x71f66b8)->(0x32c9a0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32ca74 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32cb04)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x71e8860)->((nil))
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x71f66b8)->((null) 1 0x32ccf8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 25 2 0x32cd0c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 26 2 0x32cd0c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x71f66b8)->(0x32cd48)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32ce1c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32ceac)
fixme:jscript:JScriptProperty_SetProperty (0x7215ed8)->(70000001 (nil) 0x32c1cc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c1bc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c1bc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c1bc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c1bc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c1bc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 29 2 0x32d19c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x71f66b8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d0ac)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:shdocvw:ClientSite_GetContainer (0x71f66b8)->(0x32d518)
fixme:mshtml:fire_event node type 9 node supported
err:mshtml:handle_htmlevent Could not get nsIDOMNode: 80004002
fixme:shdocvw:InPlaceFrame_SetStatusText (0x71f66b8)->(0xb7e12051)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 25 2 0x32d44c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 26 2 0x32d44c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32d47c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32d47c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 26 2 0x32d544 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 29 2 0x32d554 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x71f66b8)->(0x7bcaea02)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 28 2 0x32d47c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d474)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:shdocvw:ClientSite_GetContainer (0x71f66b8)->(0x32d518)
fixme:mshtml:fire_event node type 9 node supported
err:mshtml:handle_htmlevent Could not get nsIDOMNode: 80004002
fixme:mshtml:fire_event node type 9 node supported
err:mshtml:handle_htmlevent Could not get nsIDOMNode: 80004002
fixme:shdocvw:InPlaceFrame_SetStatusText (0x71f66b8)->(0xb7e12051)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 25 2 0x32d44c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 26 2 0x32d44c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->((null) 21 2 (nil) (nil))
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32ce24)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:ClOleCommandTarget_Exec (0x71f66b8)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32d474)
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x71f6618)->(0x130898)
fixme:mshtml:fire_event node type 9 node supported
err:mshtml:handle_htmlevent Could not get nsIDOMNode: 80004002
fixme:shdocvw:OleObject_Close (0x71f6618)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x71f6618)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x71da640)->((nil))
fixme:shdocvw:OleObject_Close (0x71f6618)->(1)
fixme:mshtml:hidden_proc (0x10042 49209 64 0)
fixme:shdocvw:OleObject_Close (0x14ae40)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x14ae40)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x173228)->((nil))
fixme:shdocvw:OleObject_Close (0x14ae40)->(1)
fixme:shell:DllCanUnloadNow stub

```

I also put a screenshot of the display as an attachment. I don't think it really changed since my first post. But is good to start with a fresh config, because I had done some tricky things.

EDIT: If you can't understand something because it is in dutch, don't wait to ask. I put a translation of the error dialogs in my first post, also I did not delete my .wine, but renamed it. I hope this is not a problem? (I had some other programs on it already)

Thank you!

---

### Post by Rackstar on 2009-04-17
If someone could help me. This would be fantastic!

---

### Post by Rackstar on 2009-04-17
I went back to wine 1.1.16. And I got PS CS4 to install! But when I try to run I get the error:

Some files are missing in the application folder. Please reinstall the application.

I'll investigate this further

EDIT:

I don't get the error no more, didn't change anything. If I try to run Photoshop:
```
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SetProcessDPIAware stub!

```
Anybody?

EDIT:

Photoshop.exe was still running

The error appears again and this is the output:
```
ruben@ruben-laptop:~/.wine/drive_c/Programma Bestanden/Adobe/Adobe Photoshop CS4$ wine Photoshop.exe 
fixme:ntdll:NtMakeTemporaryObject (0x44), stub.
wine: Call from 0x7b8450f0 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Unimplemented function ntoskrnl.exe.ExInitializeResourceLite called at address 0x7b8450f0 (thread 0014), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.ExInitializeResourceLite called in 32-bit code (0x7b845163).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b845163 ESP:0064e614 EBP:0064e678 EFLAGS:00200246(   - 00      - IZP1)
 EAX:7b82f03d EBX:7b8b7ff4 ECX:00000000 EDX:0064e69c
 ESI:0064e69c EDI:00650270
Stack dump:
0x0064e614:  0064e69c 00000008 0000003c 80000100
0x0064e624:  00000001 00000000 7b8450f0 00000002
0x0064e634:  7ede8d60 7ede9848 0000003a 00000000
0x0064e644:  00000000 00000000 00000000 00000000
0x0064e654:  00000000 7edf2ff4 0064e700 0064e6dc
0x0064e664:  0064e6b4 7ede88ed 7b8450fa 7ee6aff4
Backtrace:
=>0 0x7b845163 in kernel32 (+0x25163) (0x0064e678)
  1 0x7ede8cf8 in ntoskrnl (+0x18cf8) (0x0064e6a8)
  2 0x7edde428 in ntoskrnl (+0xe428) (0x0064e708)
  3 0x7ee68e67 in winedevice (+0x8e67) (0x0064e988)
  4 0x7ee69396 in winedevice (+0x9396) (0x0064e9d8)
  5 0x7ee3e97c in advapi32 (+0x2e97c) (0x0064ea28)
  6 0x7bc73a4e call_thread_entry_point+0xe() in ntdll (0x0064ea38)
  7 0x7bc75482 in ntdll (+0x65482) (0x0064ead8)
  8 0x7bc75650 in ntdll (+0x65650) (0x0064f3c8)
  9 0xb7efb50f start_thread+0xbf() in libpthread.so.0 (0x0064f4c8)
  10 0xb7e77a0e __clone+0x5e() in libc.so.6 (0x00000000)
0x7b845163: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (28 modules)
PE	  650000-  660e80	Deferred        adfs.sys
ELF	7b800000-7b93f000	Export          kernel32<elf>
  \-PE	7b820000-7b93f000	\               kernel32
ELF	7bc00000-7bcb1000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ecbb000-7ecd2000	Deferred        hal<elf>
  \-PE	7ecc0000-7ecd2000	\               hal
ELF	7ecd2000-7ed40000	Deferred        msvcrt<elf>
  \-PE	7ece0000-7ed40000	\               msvcrt
ELF	7ed40000-7eda7000	Deferred        rpcrt4<elf>
  \-PE	7ed50000-7eda7000	\               rpcrt4
ELF	7edc8000-7ee02000	Export          ntoskrnl<elf>
  \-PE	7edd0000-7ee02000	\               ntoskrnl
ELF	7ee02000-7ee57000	Export          advapi32<elf>
  \-PE	7ee10000-7ee57000	\               advapi32
ELF	7ee57000-7ee6c000	Export          winedevice<elf>
  \-PE	7ee60000-7ee6c000	\               winedevice
ELF	7ee6c000-7ee78000	Deferred        libnss_files.so.2
ELF	7ee78000-7ee91000	Deferred        libnsl.so.1
ELF	7ee91000-7ee9a000	Deferred        libnss_compat.so.2
ELF	7efca000-7eff0000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d92000-b7d96000	Deferred        libdl.so.2
ELF	b7d96000-b7ef4000	Export          libc.so.6
ELF	b7ef5000-b7f0e000	Export          libpthread.so.0
ELF	b7f1e000-b8059000	Deferred        libwine.so.1
ELF	b805b000-b8078000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f (D) C:\windows\system32\winedevice.exe
	00000014    0 <==
	00000011    0
	00000010    0
Backtrace:
=>0 0x7b845163 in kernel32 (+0x25163) (0x0064e678)
  1 0x7ede8cf8 in ntoskrnl (+0x18cf8) (0x0064e6a8)
  2 0x7edde428 in ntoskrnl (+0xe428) (0x0064e708)
  3 0x7ee68e67 in winedevice (+0x8e67) (0x0064e988)
  4 0x7ee69396 in winedevice (+0x9396) (0x0064e9d8)
  5 0x7ee3e97c in advapi32 (+0x2e97c) (0x0064ea28)
  6 0x7bc73a4e call_thread_entry_point+0xe() in ntdll (0x0064ea38)
  7 0x7bc75482 in ntdll (+0x65482) (0x0064ead8)
  8 0x7bc75650 in ntdll (+0x65650) (0x0064f3c8)
  9 0xb7efb50f start_thread+0xbf() in libpthread.so.0 (0x0064f4c8)
  10 0xb7e77a0e __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b8450f0 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Call from 0x7b8450f0 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SetProcessDPIAware stub!
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
fixme:keyboard:RegisterHotKey (0x1002a,1634497586,0x00000001,50): stub

```

Thank you if you take the time to help me.

---

### Post by NightMKoder on 2009-04-17
Ok, debugging this is...hard to say the least. The main problem is that you have multiple dll overrides. I'm assuming you don't want to destroy your wine prefix, so create a new one - just for photoshop (some people call these bottles).

Basically what this involves doing is typing
```

env WINEPREFIX=~/.wine_photoshop

```
ie

```

env WINEPREFIX=~/.wine_photoshop wine Setup.exe
env WINEPREFIX=~/.wine_photoshop sh winetricks gecko
env WINEPREFIX=~/.wine_photoshop winecfg

```

before every wine command (including winetricks). So follow the guide again and see if it helps now that you don't have conflicting dll overrides.

---

### Post by Rackstar on 2009-04-18
Hi,

I did the bottling and I successfully installed photoshop. But when I try to run it I still get this error.

```
op wine Photoshop.exe 
fixme:ntdll:NtMakeTemporaryObject (0x44), stub.
wine: Call from 0x7b8450f0 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Unimplemented function ntoskrnl.exe.ExInitializeResourceLite called at address 0x7b8450f0 (thread 0014), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.ExInitializeResourceLite called in 32-bit code (0x7b845163).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b845163 ESP:0064e614 EBP:0064e678 EFLAGS:00200246(   - 00      - IZP1)
 EAX:7b82f03d EBX:7b8b7ff4 ECX:00000000 EDX:0064e69c
 ESI:0064e69c EDI:00650270
Stack dump:
0x0064e614:  0064e69c 00000008 0000003c 80000100
0x0064e624:  00000001 00000000 7b8450f0 00000002
0x0064e634:  7ede8d60 7ede9848 0000003a 00000000
0x0064e644:  00000000 00000000 00000000 00000000
0x0064e654:  00000000 7edf2ff4 0064e700 0064e6dc
0x0064e664:  0064e6b4 7ede88ed 7b8450fa 7ee6aff4
Backtrace:
=>0 0x7b845163 in kernel32 (+0x25163) (0x0064e678)
  1 0x7ede8cf8 in ntoskrnl (+0x18cf8) (0x0064e6a8)
  2 0x7edde428 in ntoskrnl (+0xe428) (0x0064e708)
  3 0x7ee68e67 in winedevice (+0x8e67) (0x0064e988)
  4 0x7ee69396 in winedevice (+0x9396) (0x0064e9d8)
  5 0x7ee3e97c in advapi32 (+0x2e97c) (0x0064ea28)
  6 0x7bc73a4e call_thread_entry_point+0xe() in ntdll (0x0064ea38)
  7 0x7bc75482 in ntdll (+0x65482) (0x0064ead8)
  8 0x7bc75650 in ntdll (+0x65650) (0x0064f3c8)
  9 0xb7e4a50f start_thread+0xbf() in libpthread.so.0 (0x0064f4c8)
  10 0xb7dc6a0e __clone+0x5e() in libc.so.6 (0x00000000)
0x7b845163: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (28 modules)
PE	  650000-  660e80	Deferred        adfs.sys
ELF	7b800000-7b93f000	Export          kernel32<elf>
  \-PE	7b820000-7b93f000	\               kernel32
ELF	7bc00000-7bcb1000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ecbb000-7ecd2000	Deferred        hal<elf>
  \-PE	7ecc0000-7ecd2000	\               hal
ELF	7ecd2000-7ed40000	Deferred        msvcrt<elf>
  \-PE	7ece0000-7ed40000	\               msvcrt
ELF	7ed40000-7eda7000	Deferred        rpcrt4<elf>
  \-PE	7ed50000-7eda7000	\               rpcrt4
ELF	7edc8000-7ee02000	Export          ntoskrnl<elf>
  \-PE	7edd0000-7ee02000	\               ntoskrnl
ELF	7ee02000-7ee57000	Export          advapi32<elf>
  \-PE	7ee10000-7ee57000	\               advapi32
ELF	7ee57000-7ee6c000	Export          winedevice<elf>
  \-PE	7ee60000-7ee6c000	\               winedevice
ELF	7ee6c000-7ee78000	Deferred        libnss_files.so.2
ELF	7ee78000-7ee91000	Deferred        libnsl.so.1
ELF	7ee91000-7ee9a000	Deferred        libnss_compat.so.2
ELF	7efca000-7eff0000	Deferred        libm.so.6
ELF	7eff4000-7efff000	Deferred        libnss_nis.so.2
ELF	b7ce1000-b7ce5000	Deferred        libdl.so.2
ELF	b7ce5000-b7e43000	Export          libc.so.6
ELF	b7e44000-b7e5d000	Export          libpthread.so.0
ELF	b7e6d000-b7fa8000	Deferred        libwine.so.1
ELF	b7faa000-b7fc7000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f (D) C:\windows\system32\winedevice.exe
	00000014    0 <==
	00000011    0
	00000010    0
Backtrace:
=>0 0x7b845163 in kernel32 (+0x25163) (0x0064e678)
  1 0x7ede8cf8 in ntoskrnl (+0x18cf8) (0x0064e6a8)
  2 0x7edde428 in ntoskrnl (+0xe428) (0x0064e708)
  3 0x7ee68e67 in winedevice (+0x8e67) (0x0064e988)
  4 0x7ee69396 in winedevice (+0x9396) (0x0064e9d8)
  5 0x7ee3e97c in advapi32 (+0x2e97c) (0x0064ea28)
  6 0x7bc73a4e call_thread_entry_point+0xe() in ntdll (0x0064ea38)
  7 0x7bc75482 in ntdll (+0x65482) (0x0064ead8)
  8 0x7bc75650 in ntdll (+0x65650) (0x0064f3c8)
  9 0xb7e4a50f start_thread+0xbf() in libpthread.so.0 (0x0064f4c8)
  10 0xb7dc6a0e __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b8450f0 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Call from 0x7b8450f0 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SetProcessDPIAware stub!
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
fixme:keyboard:RegisterHotKey (0x1002a,1634497586,0x00000001,50): stub
fixme:keyboard:UnregisterHotKey (0x1002a,1634497586): stub

```


EDIT: I seem to miss the ntosknl.exe file. So this is a fault in the installer?

Thanks!

---

### Post by alex.rayu on 2009-04-18
Wine is calling for an unimplemented function. Yeah - the Wine is too raw still for such a monster as Photoshop cs4.

---

### Post by Rackstar on 2009-04-18
Hey,

I tried upgrading to 1.1.19, and now when I try to run it, I get this:

```
err:process:__wine_kernel_init boot event wait timed out
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SetProcessDPIAware stub!
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
fixme:keyboard:RegisterHotKey (0x3002c,1634497586,0x00000001,50): stub
fixme:keyboard:UnregisterHotKey (0x3002c,1634497586): stub

```

Is there any hope, or should I just give up and wait for next release?

How come other people can install it? 

Thanks for all the trouble

---

### Post by NightMKoder on 2009-04-18
> **Rackstar said:**
> Hi,

I did the bottling and I successfully installed photoshop. But when I try to run it I still get this error.

```
op wine Photoshop.exe 
fixme:ntdll:NtMakeTemporaryObject (0x44), stub.
wine: Call from 0x7b8450f0 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Unimplemented function ntoskrnl.exe.ExInitializeResourceLite called at address 0x7b8450f0 (thread 0014), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.ExInitializeResourceLite called in 32-bit code (0x7b845163).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b845163 ESP:0064e614 EBP:0064e678 EFLAGS:00200246(   - 00      - IZP1)
 EAX:7b82f03d EBX:7b8b7ff4 ECX:00000000 EDX:0064e69c
 ESI:0064e69c EDI:00650270
Stack dump:
0x0064e614:  0064e69c 00000008 0000003c 80000100
0x0064e624:  00000001 00000000 7b8450f0 00000002
0x0064e634:  7ede8d60 7ede9848 0000003a 00000000
0x0064e644:  00000000 00000000 00000000 00000000
0x0064e654:  00000000 7edf2ff4 0064e700 0064e6dc
0x0064e664:  0064e6b4 7ede88ed 7b8450fa 7ee6aff4
Backtrace:
=>0 0x7b845163 in kernel32 (+0x25163) (0x0064e678)
  1 0x7ede8cf8 in ntoskrnl (+0x18cf8) (0x0064e6a8)
  2 0x7edde428 in ntoskrnl (+0xe428) (0x0064e708)
  3 0x7ee68e67 in winedevice (+0x8e67) (0x0064e988)
  4 0x7ee69396 in winedevice (+0x9396) (0x0064e9d8)
  5 0x7ee3e97c in advapi32 (+0x2e97c) (0x0064ea28)
  6 0x7bc73a4e call_thread_entry_point+0xe() in ntdll (0x0064ea38)
  7 0x7bc75482 in ntdll (+0x65482) (0x0064ead8)
  8 0x7bc75650 in ntdll (+0x65650) (0x0064f3c8)
  9 0xb7e4a50f start_thread+0xbf() in libpthread.so.0 (0x0064f4c8)
  10 0xb7dc6a0e __clone+0x5e() in libc.so.6 (0x00000000)
0x7b845163: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (28 modules)
PE	  650000-  660e80	Deferred        adfs.sys
ELF	7b800000-7b93f000	Export          kernel32<elf>
  \-PE	7b820000-7b93f000	\               kernel32
ELF	7bc00000-7bcb1000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ecbb000-7ecd2000	Deferred        hal<elf>
  \-PE	7ecc0000-7ecd2000	\               hal
ELF	7ecd2000-7ed40000	Deferred        msvcrt<elf>
  \-PE	7ece0000-7ed40000	\               msvcrt
ELF	7ed40000-7eda7000	Deferred        rpcrt4<elf>
  \-PE	7ed50000-7eda7000	\               rpcrt4
ELF	7edc8000-7ee02000	Export          ntoskrnl<elf>
  \-PE	7edd0000-7ee02000	\               ntoskrnl
ELF	7ee02000-7ee57000	Export          advapi32<elf>
  \-PE	7ee10000-7ee57000	\               advapi32
ELF	7ee57000-7ee6c000	Export          winedevice<elf>
  \-PE	7ee60000-7ee6c000	\               winedevice
ELF	7ee6c000-7ee78000	Deferred        libnss_files.so.2
ELF	7ee78000-7ee91000	Deferred        libnsl.so.1
ELF	7ee91000-7ee9a000	Deferred        libnss_compat.so.2
ELF	7efca000-7eff0000	Deferred        libm.so.6
ELF	7eff4000-7efff000	Deferred        libnss_nis.so.2
ELF	b7ce1000-b7ce5000	Deferred        libdl.so.2
ELF	b7ce5000-b7e43000	Export          libc.so.6
ELF	b7e44000-b7e5d000	Export          libpthread.so.0
ELF	b7e6d000-b7fa8000	Deferred        libwine.so.1
ELF	b7faa000-b7fc7000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f (D) C:\windows\system32\winedevice.exe
	00000014    0 <==
	00000011    0
	00000010    0
Backtrace:
=>0 0x7b845163 in kernel32 (+0x25163) (0x0064e678)
  1 0x7ede8cf8 in ntoskrnl (+0x18cf8) (0x0064e6a8)
  2 0x7edde428 in ntoskrnl (+0xe428) (0x0064e708)
  3 0x7ee68e67 in winedevice (+0x8e67) (0x0064e988)
  4 0x7ee69396 in winedevice (+0x9396) (0x0064e9d8)
  5 0x7ee3e97c in advapi32 (+0x2e97c) (0x0064ea28)
  6 0x7bc73a4e call_thread_entry_point+0xe() in ntdll (0x0064ea38)
  7 0x7bc75482 in ntdll (+0x65482) (0x0064ead8)
  8 0x7bc75650 in ntdll (+0x65650) (0x0064f3c8)
  9 0xb7e4a50f start_thread+0xbf() in libpthread.so.0 (0x0064f4c8)
  10 0xb7dc6a0e __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b8450f0 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Call from 0x7b8450f0 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SetProcessDPIAware stub!
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
fixme:keyboard:RegisterHotKey (0x1002a,1634497586,0x00000001,50): stub
fixme:keyboard:UnregisterHotKey (0x1002a,1634497586): stub

```


EDIT: I seem to miss the ntosknl.exe file. So this is a fault in the installer?

Thanks!

You're not missing the ntsoknl file - that's the Windows NT kernel. Wine has one that's an emulated kernel. Point is - wine doesn't implement all the functions of the kernel (they try to implement only what is needed). That's why you're getting that error about unimplemented function.

But that's not the end of the story. From what I can tell (browsing around winehq), try doing `winetricks gdiplus` (remember to add WINEPREFIX if you bottled it). If that doesn't work [http://bugs.winehq.org/show_bug.cgi?id=16681](http://bugs.winehq.org/show_bug.cgi?id=16681) says that apparently the installer "forgets" to install some file. If this is the case - scrap your bottle, create the prefix again (just run any wine application - ie WINEPREFIX=~/.wine_photoshop wine notepad), and copy the photoshop program files into the bottle.

If none of those work - I give.

EDIT:
> **Rackstar said:**
> Hey,

I tried upgrading to 1.1.19, and now when I try to run it, I get this:

```
err:process:__wine_kernel_init boot event wait timed out
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SetProcessDPIAware stub!
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
fixme:keyboard:RegisterHotKey (0x3002c,1634497586,0x00000001,50): stub
fixme:keyboard:UnregisterHotKey (0x3002c,1634497586): stub

```

Is there any hope, or should I just give up and wait for next release?

How come other people can install it? 

Thanks for all the trouble

Thats an evil message (the top one). Kill that prefix.

---

### Post by quitte on 2009-04-18
I got the CS4 demo to install and run on debian sid on amd64 thanks to the tip that 1.1.16 works for the installer.
But once I try to open a file or create a new project it sits there and makes the whole system irresponsive.
I had some trouble with PS getting confused by the localization. It looked for some files in Program\ Files\\Common\ Files when they where in Programme\\Gemeinsame\ Dateien.
So I'd recommend running all commands with LANG=C prefixed, even before the .wine directory was created.
As I can't understand the gold rating in the appdb at all I think there might be something else causing us trouble. Are you using an amd64 install, too?

---

### Post by Rackstar on 2009-04-18
> **NightMKoder said:**
>  [http://bugs.winehq.org/show_bug.cgi?id=16681](http://bugs.winehq.org/show_bug.cgi?id=16681) says that apparently the installer "forgets" to install some file. If this is the case - scrap your bottle, create the prefix again (just run any wine application - ie WINEPREFIX=~/.wine_photoshop wine notepad), and copy the photoshop program files into the bottle.


So if I understand correctly I should:
Install PS CS4 on Windows
Delete my .wine_photoshop "bottle"
Create .wine_photoshop again
Copy the files from my windows to .wine_photoshop/path ?

Or before copying, installing it with wine? And then override the files with my windows files?

Thank you!

---

### Post by Rackstar on 2009-04-18
> **quitte said:**
> I got the CS4 demo to install and run on debian sid on amd64 thanks to the tip that 1.1.16 works for the installer.
But once I try to open a file or create a new project it sits there and makes the whole system irresponsive.
I had some trouble with PS getting confused by the localization. It looked for some files in Program\ Files\\Common\ Files when they where in Programme\\Gemeinsame\ Dateien.
So I'd recommend running all commands with LANG=C prefixed, even before the .wine directory was created.
As I can't understand the gold rating in the appdb at all I think there might be something else causing us trouble. Are you using an amd64 install, too?

No I'm not using amd64, but a intel32. It makes sense it could be a language problem! Little question. How do I set the LANG=C ?

Thank you!!

---

### Post by quitte on 2009-04-18
I'll just post step by step what I did. either set the WINEPREFIX yourself or move the .wine directory to a temporary location.
I extracted the ADBEPHSPCS4_LS4.7z in my home directory. Also I put the latest version of winetricks there ([http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)).
now I remove the .wine directory: 
rm -rf .wine
and install wine 1.1.16:
dpkg -i /home/quitte/Desktop/wine_1.1.16~winehq1-1_amd64.deb
next winetricks:
LANG=C sh winetricks msxml6 gdiplus gecko
now change into the PS install directory and run Setup.exe:
LANG=C wine Setup.exe

This should result in an installation that works as good or bad as mine. Changing the wine version to something later didn't make much of a difference for me.
Please tell me if you are able to make a new file. In that case I'd try running wine from a chroot.

Edit:
got the en_us version to actually work. Now I'm trying to figure out how.

---

### Post by GepettoBR on 2009-04-18
I'm also interested in getting this to work. I'm installing on a new wine prefix, with winetricks, and I still get the same error OP wa scomplaining about in his first post. I even downloaded a torrent for Photoshop CS4 Portable but it crashes in the splash screen.

---

### Post by Rackstar on 2009-04-18
> **GepettoBR said:**
> I'm also interested in getting this to work. I'm installing on a new wine prefix, with winetricks, and I still get the same error OP wa scomplaining about in his first post. I even downloaded a torrent for Photoshop CS4 Portable but it crashes in the splash screen.

I got PS CS4 Extend running without any problems. (Only fonts seem little strange).

Start with a fresh .wine or .wine prefix.
Download the needed plugins with winetricks as previously posted
First command u run with wine on that prefix has to have LANG=C before it. (So it create "Program Files" and not a folder with the translation of Program Files)
Install with the setup with wine 1.1.16 (use LANG=C wine Setup.exe just to make sure, normally not required, but helped me)
Run with 1.1.19 to get the menu-bar bug fixed. 
To fix the text tool freeze. Download atmlib.dll and put in the system32 folder. (No need to put an override in winecfg). Also you need msttcorefonts.

Hope this helped. I got it working with big help from quitte. At a certain time I got Segment failures. I upgraded to Jaunty and problem disappeared. Probably a broken package somewhere. 

Hope this helps. I'll make a write-up soon.

---

### Post by GepettoBR on 2009-04-18
Thanks for trying to help, but I can't install at all. During the first window, checking system configuration, it immediately greets me with an error and exits.

---

### Post by Rackstar on 2009-04-19
Look on to your virtual C drive, are you sure you have "Program Files" and not some local translation?

---

### Post by GepettoBR on 2009-04-19
Yes, I'm sure. My Ubuntu installation is in English, as is my Photoshop CD.

---

### Post by Rackstar on 2009-04-19
Can you give us your output of wine? Don't know if I'm going to be able to help you.

---

### Post by dannymichel on 2009-08-16
im not sure whats wrong. i had photoshop and dreamweaver working before but now i get
```
danny@danny-desktop:~$ cd "/home/danny/.wine/dosdevices/c:/Program Files/Adobe/Adobe Dreamweaver CS4"
danny@danny-desktop:~/.wine/dosdevices/c:/Program Files/Adobe/Adobe Dreamweaver CS4$ wine Dreamweaver.exe
fixme:ntdll:NtMakeTemporaryObject (0x44), stub.
wine: Call from 0x7b844430 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Unimplemented function ntoskrnl.exe.ExInitializeResourceLite called at address 0x7b844430 (thread 0014), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.ExInitializeResourceLite called in 32-bit code (0x7b8444a3).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b8444a3 ESP:0064e604 EBP:0064e668 EFLAGS:00000246(   - 00      - IZP1)
 EAX:7b82ebfd EBX:7b8b6ff4 ECX:00000000 EDX:0064e68c
 ESI:0064e68c EDI:00650270
Stack dump:
0x0064e604:  0064e68c 00000008 0000003c 80000100
0x0064e614:  00000001 00000000 7b844430 00000002
0x0064e624:  7edefdc0 7edf08a8 0000003a 00000000
0x0064e634:  00000000 00000000 00000000 00000000
0x0064e644:  00000000 7edf9ff4 0064e6f0 0064e6cc
0x0064e654:  0064e6a4 7edef94d 7b84443a 7ee96ff4
Backtrace:
=>0 0x7b8444a3 in kernel32 (+0x244a3) (0x0064e668)

```
and
```
danny@danny-desktop:~$ cd "/home/danny/.wine/dosdevices/c:/Program Files/Adobe/Adobe Photoshop CS4"
danny@danny-desktop:~/.wine/dosdevices/c:/Program Files/Adobe/Adobe Photoshop CS4$ wine Photoshop.exe
fixme:ntdll:NtMakeTemporaryObject (0x44), stub.
wine: Call from 0x7b844430 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Unimplemented function ntoskrnl.exe.ExInitializeResourceLite called at address 0x7b844430 (thread 0014), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.ExInitializeResourceLite called in 32-bit code (0x7b8444a3).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b8444a3 ESP:0064e604 EBP:0064e668 EFLAGS:00000246(   - 00      - IZP1)
 EAX:7b82ebfd EBX:7b8b6ff4 ECX:00000000 EDX:0064e68c
 ESI:0064e68c EDI:00650270
Stack dump:
0x0064e604:  0064e68c 00000008 0000003c 80000100
0x0064e614:  00000001 00000000 7b844430 00000002
0x0064e624:  7edefdc0 7edf08a8 0000003a 00000000
0x0064e634:  00000000 00000000 00000000 00000000
0x0064e644:  00000000 7edf9ff4 0064e6f0 0064e6cc
0x0064e654:  0064e6a4 7edef94d 7b84443a 7ee96ff4
Backtrace:
=>0 0x7b8444a3 in kernel32 (+0x244a3) (0x0064e668)
  1 0x7edefd58 in ntoskrnl (+0xfd58) (0x0064e698)
  2 0x7ede5448 in ntoskrnl (+0x5448) (0x0064e6f8)
  3 0x7ee94e67 in winedevice (+0x4e67) (0x0064e978)
  4 0x7ee95396 in winedevice (+0x5396) (0x0064e9c8)
  5 0x7ee45b0c in advapi32 (+0x25b0c) (0x0064ea18)
  6 0x7bc7496e call_thread_entry_point+0xe() in ntdll (0x0064ea28)
  7 0x7bc766f2 in ntdll (+0x666f2) (0x0064eac8)
  8 0x7bc768c0 in ntdll (+0x668c0) (0x0064f3b8)
  9 0xf7e4d4ff start_thread+0xbf() in libpthread.so.0 (0x0064f4b8)
  10 0xf7dc9b9e __clone+0x5e() in libc.so.6 (0x00000000)
0x7b8444a3: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (27 modules)
PE	  650000-  660e80	Deferred        adfs.sys
PE	78000000-78044000	Deferred        msvcrt
ELF	7b800000-7b93e000	Export          kernel32<elf>
  \-PE	7b820000-7b93e000	\               kernel32
ELF	7bc00000-7bcb1000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ed51000-7ed68000	Deferred        hal<elf>
  \-PE	7ed60000-7ed68000	\               hal
ELF	7ed68000-7edcf000	Deferred        rpcrt4<elf>
  \-PE	7ed70000-7edcf000	\               rpcrt4
ELF	7edcf000-7ee09000	Export          ntoskrnl<elf>
  \-PE	7ede0000-7ee09000	\               ntoskrnl
ELF	7ee09000-7ee5e000	Export          advapi32<elf>
  \-PE	7ee20000-7ee5e000	\               advapi32
ELF	7ee5e000-7ee77000	Deferred        libnsl.so.1
ELF	7ee77000-7ee80000	Deferred        libnss_compat.so.2
ELF	7ee83000-7ee98000	Export          winedevice<elf>
  \-PE	7ee90000-7ee98000	\               winedevice
ELF	7efc2000-7efe8000	Deferred        libm.so.6
ELF	7eff4000-7f000000	Deferred        libnss_files.so.2
ELF	f7cd1000-f7cdc000	Deferred        libnss_nis.so.2
ELF	f7cdf000-f7ce3000	Deferred        libdl.so.2
ELF	f7ce3000-f7e46000	Export          libc.so.6
ELF	f7e47000-f7e60000	Export          libpthread.so.0
ELF	f7e78000-f7fb3000	Deferred        libwine.so.1
ELF	f7fb5000-f7fd6000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000015    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f (D) C:\windows\system32\winedevice.exe
	00000014    0 <==
	00000011    0
	00000010    0
Backtrace:
=>0 0x7b8444a3 in kernel32 (+0x244a3) (0x0064e668)
  1 0x7edefd58 in ntoskrnl (+0xfd58) (0x0064e698)
  2 0x7ede5448 in ntoskrnl (+0x5448) (0x0064e6f8)
  3 0x7ee94e67 in winedevice (+0x4e67) (0x0064e978)
  4 0x7ee95396 in winedevice (+0x5396) (0x0064e9c8)
  5 0x7ee45b0c in advapi32 (+0x25b0c) (0x0064ea18)
  6 0x7bc7496e call_thread_entry_point+0xe() in ntdll (0x0064ea28)
  7 0x7bc766f2 in ntdll (+0x666f2) (0x0064eac8)
  8 0x7bc768c0 in ntdll (+0x668c0) (0x0064f3b8)
  9 0xf7e4d4ff start_thread+0xbf() in libpthread.so.0 (0x0064f4b8)
  10 0xf7dc9b9e __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b844430 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Call from 0x7b844430 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a060 0x1001818 1 0x33fe78 (null) (null) 0x100a068
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a080 0x1001808 1 0x33fe78 (null) (null) 0x100a088
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0a0 0x10017f8 1 0x33fe78 (null) (null) 0x100a0a8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0c0 0x10017e8 1 0x33fe78 (null) (null) 0x100a0c8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0e0 0x10017d8 1 0x33fe78 (null) (null) 0x100a0e8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a100 0x10017c8 1 0x33fe78 (null) (null) 0x100a108
fixme:win:RegisterDeviceNotificationW (hwnd=0x1351a8, filter=0x76e8ec,flags=0x00000001),
	returns a fake device notification handle!
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library data_flow.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library image_runtime.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library image_flow.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library image_runtime.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library data_flow.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\PlugPlug.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\PlugPlug.dll") not found
err:module:import_dll Library PlugPlug.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\AdobeOwl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\AdobeOwl.dll") not found
err:module:import_dll Library AdobeOwl.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\AdobeOwlCanvas.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\AdobeOwlCanvas.dll") not found
err:module:import_dll Library AdobeOwlCanvas.dll (which is needed by L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe" failed, status c0000135
danny@danny-desktop:~/.wine/dosdevices/c:/Program Files/Adobe/Adobe Photoshop CS4$ 

```

---

### Post by alex.rayu on 2009-08-17
Wow I have never seen this kind of an error. Dud it happen by itself or did you do anything prior to it happening?

---

### Post by dannymichel on 2009-08-17
> **alex.rayu said:**
> Wow I have never seen this kind of an error. Dud it happen by itself or did you do anything prior to it happening?
i just followed the directions in the 'how to'

---

### Post by alex.rayu on 2009-08-17
Please try setting the Wine to WinXP mode, disabling the compiz/desktop effects, and trying to run Photoshop again. Also, make sure that the Wine's gdiplus is used rather than Windows'.

---

### Post by dannymichel on 2009-08-18
> **alex.rayu said:**
> Please try setting the Wine to WinXP mode, disabling the compiz/desktop effects, and trying to run Photoshop again. Also, make sure that the Wine's gdiplus is used rather than Windows'.

[[IMG]http://img2.imagetitan.com/img2/small/28/28_screenshot.png[/IMG]](http://img2.imagetitan.com/img.php?image=28_screenshot.png)[[IMG]http://img2.imagetitan.com/img2/small/28/28_screenshot-1.png[/IMG]](http://img2.imagetitan.com/img.php?image=28_screenshot-1.png)[[IMG]http://img2.imagetitan.com/img2/small/28/28_screenshot-2.png[/IMG]](http://img2.imagetitan.com/img.php?image=28_screenshot-2.png)
```
danny@danny-desktop:~$ cd "/home/danny/.wine/drive_c/Program Files/Adobe/Adobe Photoshop CS4"
danny@danny-desktop:~/.wine/drive_c/Program Files/Adobe/Adobe Photoshop CS4$ wine Photoshop.exe
fixme:ntdll:NtMakeTemporaryObject (0x44), stub.
wine: Call from 0x7b844430 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Unimplemented function ntoskrnl.exe.ExInitializeResourceLite called at address 0x7b844430 (thread 0015), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.ExInitializeResourceLite called in 32-bit code (0x7b8444a3).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b8444a3 ESP:0064e604 EBP:0064e668 EFLAGS:00000246(   - 00      - IZP1)
 EAX:7b82ebfd EBX:7b8b6ff4 ECX:00000000 EDX:0064e68c
 ESI:0064e68c EDI:00650270
Stack dump:
0x0064e604:  0064e68c 00000008 0000003c 80000100
0x0064e614:  00000001 00000000 7b844430 00000002
0x0064e624:  7edf8dc0 7edf98a8 0000003a 00000000
0x0064e634:  00000000 00000000 00000000 00000000
0x0064e644:  00000000 7ee02ff4 0064e6f0 0064e6cc
0x0064e654:  0064e6a4 7edf894d 7b84443a 7ee94ff4
Backtrace:
=>0 0x7b8444a3 in kernel32 (+0x244a3) (0x0064e668)
  1 0x7edf8d58 in ntoskrnl (+0x18d58) (0x0064e698)
  2 0x7edee448 in ntoskrnl (+0xe448) (0x0064e6f8)
  3 0x7ee92e67 in winedevice (+0x2e67) (0x0064e978)
  4 0x7ee93396 in winedevice (+0x3396) (0x0064e9c8)
  5 0x7ee4eb0c in advapi32 (+0x2eb0c) (0x0064ea18)
  6 0x7bc7496e call_thread_entry_point+0xe() in ntdll (0x0064ea28)
  7 0x7bc766f2 in ntdll (+0x666f2) (0x0064eac8)
  8 0x7bc768c0 in ntdll (+0x668c0) (0x0064f3b8)
  9 0xf7e4c4ff start_thread+0xbf() in libpthread.so.0 (0x0064f4b8)
  10 0xf7dc8b9e __clone+0x5e() in libc.so.6 (0x00000000)
0x7b8444a3: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (28 modules)
PE	  650000-  660e80	Deferred        adfs.sys
ELF	7b800000-7b93e000	Export          kernel32<elf>
  \-PE	7b820000-7b93e000	\               kernel32
ELF	7bc00000-7bcb1000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7eced000-7ed04000	Deferred        hal<elf>
  \-PE	7ecf0000-7ed04000	\               hal
ELF	7ed04000-7ed71000	Deferred        msvcrt<elf>
  \-PE	7ed10000-7ed71000	\               msvcrt
ELF	7ed71000-7edd8000	Deferred        rpcrt4<elf>
  \-PE	7ed80000-7edd8000	\               rpcrt4
ELF	7edd8000-7ee12000	Export          ntoskrnl<elf>
  \-PE	7ede0000-7ee12000	\               ntoskrnl
ELF	7ee12000-7ee67000	Export          advapi32<elf>
  \-PE	7ee20000-7ee67000	\               advapi32
ELF	7ee67000-7ee73000	Deferred        libnss_files.so.2
ELF	7ee73000-7ee7c000	Deferred        libnss_compat.so.2
ELF	7ee81000-7ee96000	Export          winedevice<elf>
  \-PE	7ee90000-7ee96000	\               winedevice
ELF	7efc0000-7efe6000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        libnsl.so.1
ELF	f7cd2000-f7cdd000	Deferred        libnss_nis.so.2
ELF	f7cde000-f7ce2000	Deferred        libdl.so.2
ELF	f7ce2000-f7e45000	Export          libc.so.6
ELF	f7e46000-f7e5f000	Export          libpthread.so.0
ELF	f7e79000-f7fb4000	Deferred        libwine.so.1
ELF	f7fb6000-f7fd7000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f (D) C:\windows\system32\winedevice.exe
	00000015    0 <==
	00000011    0
	00000010    0
Backtrace:
=>0 0x7b8444a3 in kernel32 (+0x244a3) (0x0064e668)
  1 0x7edf8d58 in ntoskrnl (+0x18d58) (0x0064e698)
  2 0x7edee448 in ntoskrnl (+0xe448) (0x0064e6f8)
  3 0x7ee92e67 in winedevice (+0x2e67) (0x0064e978)
  4 0x7ee93396 in winedevice (+0x3396) (0x0064e9c8)
  5 0x7ee4eb0c in advapi32 (+0x2eb0c) (0x0064ea18)
  6 0x7bc7496e call_thread_entry_point+0xe() in ntdll (0x0064ea28)
  7 0x7bc766f2 in ntdll (+0x666f2) (0x0064eac8)
  8 0x7bc768c0 in ntdll (+0x668c0) (0x0064f3b8)
  9 0xf7e4c4ff start_thread+0xbf() in libpthread.so.0 (0x0064f4b8)
  10 0xf7dc8b9e __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b844430 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Call from 0x7b844430 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SetProcessDPIAware stub!
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x1e958c 0x1e9598 0x1e9338 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x1e92b4 0x1e92c0 0x1e9308 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x1e92b4 0x1e92c0 0x1e9308 (nil)
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ole:CoUninitialize Mismatched CoUninitialize
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4100c
fixme:mountmgr:harddisk_ioctl unsupported ioctl 41018
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d0c10
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data/FLEXnet" 1 1 0x5c8f10 (nil) (nil) (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data/FLEXnet" 1 4 (nil) (nil) 0x5ccc38 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data/FLEXnet" 1 4 (nil) (nil) 0x5ccc90 (nil)
fixme:win:EnumDisplayDevicesW ((null),0,0x32e5bc,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10030 0x00000000
fixme:keyboard:RegisterHotKey (0x1002a,1634497586,0x00000001,50): stub
fixme:xrender:X11DRV_AlphaBlend Ignoring SourceConstantAlpha 0 for AC_SRC_ALPHA
fixme:imm:ImmReleaseContext (0x10034, 0x205ed8): stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data/FLEXnet/adobe_00080000_event.log" 1 4 (nil) (nil) 0x71af140 (nil)
fixme:win:LockWindowUpdate (0x10034), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:imm:ImeHandleNotify WM_IME_NOTIFY:IMN_SETOPENSTATUS
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x10030
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\temp\\swtag.log" 1 -2147483644 0x1fec24 0x1fec30 0x207d18 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\Adobe\\ISO-19770" 1 -2147483644 0x1fec24 0x1fec30 0x207d18 (nil)
fixme:win:EnumDisplayDevicesW ((null),0,0x32e7a4,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20102 0x00000000
wine: Unhandled page fault on read access to 0x00000048 at address 0x39875b8a (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000048 in 32-bit code (0x39875b8a).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:39875b8a ESP:0032e130 EBP:0032e140 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00110000 EBX:07b61e38 ECX:00000048 EDX:00000011
 ESI:07b62008 EDI:00000000
Stack dump:
0x0032e130:  07b61f4c 07b62008 00110000 07b61df0
0x0032e140:  0032e15c 39921f44 00110000 0032e158
0x0032e150:  000001ca 07b61eb8 00110002 0032e188
0x0032e160:  398b6029 0000000e 07b61df0 00000000
0x0032e170:  07b61cf8 07b61e90 00000005 07b61ebc
0x0032e180:  00000000 00000007 0032e1c4 3987649b
Backtrace:
=>0 0x39875b8a in gdiplus (+0x75b8a) (0x0032e140)
  1 0x39921f44 in gdiplus (+0x121f44) (0x0032e15c)
  2 0x398b6029 in gdiplus (+0xb6029) (0x0032e188)
  3 0x3987649b in gdiplus (+0x7649b) (0x0032e1c4)
  4 0x39875084 in gdiplus (+0x75084) (0x0032e1e4)
  5 0x39874b4a in gdiplus (+0x74b4a) (0x0032e31c)
  6 0x398f4d5c in gdiplus (+0xf4d5c) (0x0032e53c)
  7 0x398f4f82 in gdiplus (+0xf4f82) (0x0032e5d8)
  8 0x00720054 in photoshop (+0x320054) (0x00280020)
  9 0x00000000 (0x00000000)
0x39875b8a: movl	0x0(%edi,%ecx,1),%ecx
Modules:
Module	Address			Debug info	Name (149 modules)
PE	  340000-  3e1000	Deferred        image_flow
PE	  400000- 36e1000	Export          photoshop
PE	 36f0000- 38bb000	Deferred        aif_ogl
PE	 38c0000- 38e9000	Deferred        data_flow
PE	 38f0000- 3910000	Deferred        image_runtime
PE	 3910000- 39f5000	Deferred        libifcoremd
PE	 3a00000- 3cc3000	Deferred        libmmd
PE	 3de0000- 3e36000	Deferred        plugplug
PE	 3e40000- 3e8a000	Deferred        bib
PE	 3e90000- 3f3a000	Deferred        axedomcore
PE	 3f40000- 407c000	Deferred        adobeowl
PE	 4080000- 42ab000	Deferred        adobeowlcanvas
PE	 42b0000- 42dc000	Deferred        ahclient
PE	 42e0000- 473c000	Deferred        mps
PE	 5970000- 59dd000	Deferred        adobexmp
PE	 5af0000- 5d9b000	Deferred        photoshop
PE	 5da0000- 5fce000	Deferred        psviews
PE	 5fd0000- 6273000	Deferred        psart
PE	 6690000- 6999000	Deferred        amtlib
PE	 6ab0000- 6b4d000	Deferred        amtservices
PE	 6d60000- 6d97000	Deferred        adobe_caps
PE	 6da0000- 6dc0000	Deferred        asneu
PE	 6ed0000- 7153000	Deferred        adobelm_libfnp
PE	10000000-10062000	Deferred        aif_core
PE	12000000-122f8000	Deferred        adobelm
PE	39800000-399b2000	Export          gdiplus
PE	70bd0000-70c35000	Deferred        shlwapi
PE	78130000-781cb000	Deferred        msvcr80
ELF	7b800000-7b93e000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93e000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c2b4000-7c2c8000	Deferred        shfolder<elf>
  \-PE	7c2c0000-7c2c8000	\               shfolder
ELF	7c2c8000-7c2dc000	Deferred        icmp<elf>
  \-PE	7c2d0000-7c2dc000	\               icmp
ELF	7c2dc000-7c2f1000	Deferred        wtsapi32<elf>
  \-PE	7c2e0000-7c2f1000	\               wtsapi32
ELF	7c2f1000-7c349000	Deferred        riched20<elf>
  \-PE	7c300000-7c349000	\               riched20
ELF	7c349000-7c364000	Deferred        wsock32<elf>
  \-PE	7c350000-7c364000	\               wsock32
ELF	7c364000-7c3e6000	Deferred        crypt32<elf>
  \-PE	7c370000-7c3e6000	\               crypt32
ELF	7c3e6000-7c420000	Deferred        rsaenh<elf>
  \-PE	7c3f0000-7c420000	\               rsaenh
PE	7c420000-7c4a7000	Deferred        msvcp80
ELF	7c4b3000-7c4c7000	Deferred        msimg32<elf>
  \-PE	7c4c0000-7c4c7000	\               msimg32
ELF	7c4c7000-7c534000	Deferred        setupapi<elf>
  \-PE	7c4d0000-7c534000	\               setupapi
ELF	7c534000-7c54b000	Deferred        snmpapi<elf>
  \-PE	7c540000-7c54b000	\               snmpapi
ELF	7c54b000-7c56e000	Deferred        winhttp<elf>
  \-PE	7c550000-7c56e000	\               winhttp
ELF	7c56e000-7c58d000	Deferred        iphlpapi<elf>
  \-PE	7c570000-7c58d000	\               iphlpapi
ELF	7c791000-7c7b8000	Deferred        netapi32<elf>
  \-PE	7c7a0000-7c7b8000	\               netapi32
ELF	7c7b8000-7c7cc000	Deferred        sti<elf>
  \-PE	7c7c0000-7c7cc000	\               sti
ELF	7c7cc000-7c7e0000	Deferred        lz32<elf>
  \-PE	7c7d0000-7c7e0000	\               lz32
ELF	7c7e0000-7c7fb000	Deferred        version<elf>
  \-PE	7c7f0000-7c7fb000	\               version
ELF	7ca78000-7caab000	Deferred        uxtheme<elf>
  \-PE	7ca80000-7caab000	\               uxtheme
ELF	7caab000-7cb14000	Deferred        libgcrypt.so.11
ELF	7cb14000-7cb26000	Deferred        libtasn1.so.3
ELF	7cb26000-7cb3c000	Deferred        libresolv.so.2
ELF	7cb3c000-7cb60000	Deferred        libk5crypto.so.3
ELF	7cb60000-7cbf2000	Deferred        libkrb5.so.3
ELF	7cbf2000-7cc8f000	Deferred        libgnutls.so.26
ELF	7cc8f000-7ccc6000	Deferred        libcups.so.2
ELF	7cf07000-7cf0b000	Deferred        libgpg-error.so.0
ELF	7cf0b000-7cf36000	Deferred        libgssapi_krb5.so.2
ELF	7cf71000-7cf7a000	Deferred        libxcursor.so.1
ELF	7cf7a000-7cf7f000	Deferred        libxfixes.so.3
ELF	7cf7f000-7cf83000	Deferred        libxcomposite.so.1
ELF	7cf83000-7cf8b000	Deferred        libxrandr.so.2
ELF	7cf8b000-7cf95000	Deferred        libxrender.so.1
ELF	7cf95000-7cf9b000	Deferred        libxxf86vm.so.1
ELF	7cf9b000-7cf9e000	Deferred        libxinerama.so.1
ELF	7cf9e000-7cfa2000	Deferred        libkeyutils.so.1
ELF	7cfa2000-7cfab000	Deferred        libkrb5support.so.0
ELF	7cfab000-7cfaf000	Deferred        libcom_err.so.2
ELF	7cfb8000-7cfd9000	Deferred        imm32<elf>
  \-PE	7cfc0000-7cfd9000	\               imm32
ELF	7cfd9000-7d075000	Deferred        winex11<elf>
  \-PE	7cff0000-7d075000	\               winex11
ELF	7d0b7000-7d0de000	Deferred        libexpat.so.1
ELF	7d0de000-7d10b000	Deferred        libfontconfig.so.1
ELF	7d1e2000-7d1f8000	Deferred        libz.so.1
ELF	7d1f8000-7d26f000	Deferred        libfreetype.so.6
ELF	7d289000-7d2b6000	Deferred        ws2_32<elf>
  \-PE	7d290000-7d2b6000	\               ws2_32
ELF	7d2b6000-7d39d000	Deferred        oleaut32<elf>
  \-PE	7d2d0000-7d39d000	\               oleaut32
ELF	7d39d000-7d44e000	Deferred        comdlg32<elf>
  \-PE	7d3a0000-7d44e000	\               comdlg32
ELF	7d44e000-7d516000	Deferred        comctl32<elf>
  \-PE	7d460000-7d516000	\               comctl32
ELF	7d516000-7d6a3000	Deferred        shell32<elf>
  \-PE	7d530000-7d6a3000	\               shell32
ELF	7d6a3000-7d6b9000	Deferred        psapi<elf>
  \-PE	7d6b0000-7d6b9000	\               psapi
ELF	7d6b9000-7d707000	Deferred        dbghelp<elf>
  \-PE	7d6c0000-7d707000	\               dbghelp
ELF	7d707000-7d73d000	Deferred        winspool<elf>
  \-PE	7d710000-7d73d000	\               winspool
ELF	7d73d000-7d74c000	Deferred        libgcc_s.so.1
ELF	7d83b000-7d8ad000	Deferred        libglu.so.1
ELF	7d8af000-7d8c7000	Deferred        imagehlp<elf>
  \-PE	7d8b0000-7d8c7000	\               imagehlp
ELF	7d8c7000-7d8cc000	Deferred        libxdmcp.so.6
ELF	7d8cc000-7d8ce000	Deferred        libnvidia-tls.so.1
ELF	7d8ce000-7e7e6000	Deferred        libglcore.so.1
ELF	7e7e6000-7e800000	Deferred        libxcb.so.1
ELF	7e800000-7e8ba000	Deferred        libgl.so.1
ELF	7e8ba000-7e9a9000	Deferred        libx11.so.6
ELF	7e9aa000-7e9c1000	Deferred        glu32<elf>
  \-PE	7e9b0000-7e9c1000	\               glu32
ELF	7e9c3000-7ea58000	Deferred        opengl32<elf>
  \-PE	7e9e0000-7ea58000	\               opengl32
ELF	7ea58000-7eac5000	Deferred        msvcrt<elf>
  \-PE	7ea70000-7eac5000	\               msvcrt
ELF	7eac5000-7eb2c000	Deferred        rpcrt4<elf>
  \-PE	7ead0000-7eb2c000	\               rpcrt4
ELF	7eb2c000-7ec24000	Deferred        ole32<elf>
  \-PE	7eb40000-7ec24000	\               ole32
ELF	7ec24000-7ec79000	Deferred        advapi32<elf>
  \-PE	7ec30000-7ec79000	\               advapi32
ELF	7ec79000-7ed1a000	Deferred        gdi32<elf>
  \-PE	7ec90000-7ed1a000	\               gdi32
ELF	7ed1a000-7ee66000	Deferred        user32<elf>
  \-PE	7ed30000-7ee66000	\               user32
ELF	7ef90000-7ef9c000	Deferred        libnss_files.so.2
ELF	7ef9c000-7efa7000	Deferred        libnss_nis.so.2
ELF	7efa7000-7efc0000	Deferred        libnsl.so.1
ELF	7efc0000-7efe6000	Deferred        libm.so.6
ELF	7efe7000-7efeb000	Deferred        libxau.so.6
ELF	7efeb000-7effb000	Deferred        libxext.so.6
ELF	f7cf5000-f7cf9000	Deferred        libdl.so.2
ELF	f7cf9000-f7e5c000	Deferred        libc.so.6
ELF	f7e5d000-f7e76000	Deferred        libpthread.so.0
ELF	f7e77000-f7e80000	Deferred        libnss_compat.so.2
ELF	f7e90000-f7fcb000	Deferred        libwine.so.1
ELF	f7fcd000-f7fee000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Adobe\Adobe Photoshop CS4\Photoshop.exe
	0000003d    0
	00000023    0
	00000022    0
	00000021    0
	00000020    0
	00000009    0 <==
0000000c 
	0000002b    0
	0000002a    0
	00000026    0
	0000001b    0
	00000014    0
	00000013    0
	0000000e    0
	0000000d    0
00000018 
	0000001d    0
	0000001c    0
	0000001a    0
	00000019    0
0000001e 
	0000001f    0
00000027 
	00000030    0
	0000002f    0
	0000002e    0
	0000002c    0
	00000029    0
	00000028    0
Backtrace:
=>0 0x39875b8a in gdiplus (+0x75b8a) (0x0032e140)
  1 0x39921f44 in gdiplus (+0x121f44) (0x0032e15c)
  2 0x398b6029 in gdiplus (+0xb6029) (0x0032e188)
  3 0x3987649b in gdiplus (+0x7649b) (0x0032e1c4)
  4 0x39875084 in gdiplus (+0x75084) (0x0032e1e4)
  5 0x39874b4a in gdiplus (+0x74b4a) (0x0032e31c)
  6 0x398f4d5c in gdiplus (+0xf4d5c) (0x0032e53c)
  7 0x398f4f82 in gdiplus (+0xf4f82) (0x0032e5d8)
  8 0x00720054 in photoshop (+0x320054) (0x00280020)
  9 0x00000000 (0x00000000)
err:seh:setup_exception_record nested exception on signal stack in thread 0009 eip 7bc6f620 esp 7ffdbc7c stack 0x232000-0x330000



```

still stuck at the splash screen

---

### Post by alex.rayu on 2009-08-18
In my wine setup window, there is only 1 library: gdiplus - you have more than a dozen.

1. I unstalled wine 1.1.6
2. I installed gecko, corefonts, gdiplus, vcrun2005 and msxml3 
3. I installed CS4
4. I updated wine.

It does not gurarantee that it will work for you though. It's all very cranky (

---

### Post by dannymichel on 2009-08-18
> **alex.rayu said:**
> 
1. I unstalled wine 1.1.6
It does not gurarantee that it will work for you though. It's all very cranky (
u mean 
1. I [COLOR="Red"]installed[/COLOR] wine 1.1.6
?
> **alex.rayu said:**
> In my wine setup window, there is only 1 library: gdiplus - you have more than a dozen.
if thats true i have no idea y.
how do i fix that?

---

### Post by onedemian on 2009-08-18
> **dannymichel said:**
> u mean 
1. I [COLOR="Red"]installed[/COLOR] wine 1.1.6
?

if thats true i have no idea y.
how do i fix that?

Hi,

I am getting the same problem. Using a spanish version but I think this is the same case.

I installed a portable version, whih required to install, and after that i just tried to run "Adobe Photoshop.exe". 

I saw the splash screen for a while and never more, this is the output:


```
jvargas@pregon-ca:~/.wine/drive_c/Archivos de programa/Adobe/Photoshop CS4$ wine Adobe\ Photoshop\ CS4.exe 
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\AdobeOwl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\AdobeOwl.dll") not found
err:module:import_dll Library AdobeOwl.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\AdobeOwlCanvas.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\AdobeOwlCanvas.dll") not found
err:module:import_dll Library AdobeOwlCanvas.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library data_flow.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library data_flow.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library image_runtime.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library image_flow.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library image_runtime.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\PlugPlug.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\PlugPlug.dll") not found
err:module:import_dll Library PlugPlug.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe" failed, status c0000135

```

Keep me updated...
Thanks in advance.

---

### Post by onedemian on 2009-08-18
I forgot to mention that I am using wine 1.1.27 (latest). This is a fresh ubuntu 9.04 install.

---

### Post by NightMKoder on 2009-08-19
> **onedemian said:**
> Hi,

I am getting the same problem. Using a spanish version but I think this is the same case.

I installed a portable version, whih required to install, and after that i just tried to run "Adobe Photoshop.exe". 

I saw the splash screen for a while and never more, this is the output:


```
jvargas@pregon-ca:~/.wine/drive_c/Archivos de programa/Adobe/Photoshop CS4$ wine Adobe\ Photoshop\ CS4.exe 
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\AdobeOwl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\AdobeOwl.dll") not found
err:module:import_dll Library AdobeOwl.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\AdobeOwlCanvas.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\AdobeOwlCanvas.dll") not found
err:module:import_dll Library AdobeOwlCanvas.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library data_flow.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library data_flow.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library image_runtime.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library image_flow.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library image_runtime.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\PlugPlug.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\PlugPlug.dll") not found
err:module:import_dll Library PlugPlug.dll (which is needed by L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Archivos de programa\\Adobe\\Photoshop CS4\\Adobe Photoshop CS4.exe" failed, status c0000135

```

Keep me updated...
Thanks in advance.

try:
winetricks vcrun2005 vcrun2005sp1

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by onedemian on 2009-08-19
Already did that. Even with 2008 and 2008sp1 version.

Tried also running Setup.exe from retail version, and it fails during launch.

I've decided to get a standalone version, hoping I could find it. If you have a link, please send me a PM.

Thanks.

---

### Post by alex.rayu on 2009-08-19
No you see "even 2008 and 2008sp1" does not help at all. It may sound crazy, but if you install some library that is not helpful, you will break things. You know how? 2008 mscvrt will call for a function that was newly added to that version and which is not implemented yet. And it will break rather than help.

If you screwed your wine up - this is what you do: delete the the .wine folder where you installed the libraries (wine itself will not be affected. As soon as you start wine again it will recreate the .wine folder - but a clean one).

And then follow the steps. It won't install in newer wine. You have to install older wine, and after the CS4 is installed, install the latest wine.

ie6 - try with gecko, without ie6. You may need it to run the Photoshop though.

Internalization - Spanish - I read it will make additional problems.

Also, you need to copy amtlib.dll from your windows into wine windows/system32 folder to make the text tool work.

---

### Post by CoolMeEddy on 2009-08-21
so did any of you guys got it to work?
It's just that I switched from WinXP to UBUNTU 9.04 because I knew that Linux uses less resources. I'm also into photography and some time's I'm dealing with some pretty big pictures where even my laptop (dell xps m1710) starts sweating. 
If I won't be able to run PS CS4 is there any analogue application which is **VERY, VERY SIMILAR** to photoshop. I doubt I'll have time to learn another application as I know photoshop today. 
Maybe adobe photoshop cs3 works good with Ubuntu? I don't think I should come back to cs2 though. 
Any replies would be much appreciated from users with much more experience with linux. 

By the way, so far I'm quite psyched with Ubuntu. It loads fast, looks great - all it needs is PS CS4 :lolflag:

---

### Post by dannymichel on 2009-08-21
> **CoolMeEddy said:**
> so did any of you guys got it to work?
It's just that I switched from WinXP to UBUNTU 9.04 because I knew that Linux uses less resources. I'm also into photography and some time's I'm dealing with some pretty big pictures where even my laptop (dell xps m1710) starts sweating. 
If I won't be able to run PS CS4 is there any analogue application which is **VERY, VERY SIMILAR** to photoshop. I doubt I'll have time to learn another application as I know photoshop today. 
Maybe adobe photoshop cs3 works good with Ubuntu? I don't think I should come back to cs2 though. 
Any replies would be much appreciated from users with much more experience with linux. 

By the way, so far I'm quite psyched with Ubuntu. It loads fast, looks great - all it needs is PS CS4 :lolflag:

You seem like a nice guy so I'm going to give it to you straight. There are no similar apps. Some may tell you gimp but they are lying. Gimp is not a quater of the application Photoshop is. I'm just trying to save you some time. You NEED to get Photoshop working

---

### Post by dannymichel on 2009-08-21
> **onedemian said:**
> I forgot to mention that I am using wine 1.1.27 (latest). This is a fresh ubuntu 9.04 install.

did u ever get ur working?

now im just getting ```
danny@danny-desktop ~ $ wine /home/danny/.wine/dosdevices/c:/Program\ Files/Adobe/Adobe\ Photoshop\ CS4/Photoshop.exe
fixme:ntdll:NtMakeTemporaryObject (0x44), stub.
fixme:ntoskrnl:ExInitializeResourceLite stub: 0x114040
fixme:ntoskrnl:MmQuerySystemSize stub
fixme:ntoskrnl:ExInitializeNPagedLookasideList stub: 0x65f3a0, (nil), (nil), 16, 44, 1936090177, 16
fixme:ntoskrnl:ExInitializeResourceLite stub: 0x65f360
fixme:ntoskrnl:ObfReferenceObject ((nil)): stub
fixme:ntoskrnl:IoRegisterFileSystem (0x115da8): stub
fixme:ntoskrnl:FsRtlRegisterUncProvider (0x64e724 0x64e714 0): stub
fixme:ntoskrnl:IoUnregisterFileSystem (0x115da8): stub
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SetProcessDPIAware stub!
err:shell:SHGetFolderPathAndSubDirW Failed to create directory L"".
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x1c56bc 0x1c56c8 0x1c5480 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x1c53fc 0x1c5408 0x1c5450 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x1c53fc 0x1c5408 0x1c5450 (nil)
fixme:win:EnumDisplayDevicesW ((null),0,0x32e7a4,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10044 0x00000000
wine: Unhandled page fault on read access to 0x00000048 at address 0x39875b8a (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000048 in 32-bit code (0x39875b8a).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:39875b8a ESP:0032e130 EBP:0032e140 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00110000 EBX:07530c98 ECX:00000048 EDX:00000011
 ESI:07530e68 EDI:00000000
Stack dump:
0x0032e130:  07530dac 07530e68 00110000 07530c50
0x0032e140:  0032e15c 39921f44 00110000 0032e158
0x0032e150:  000001ca 07530d18 00110002 0032e188
0x0032e160:  398b6029 0000000e 07530c50 00000000
0x0032e170:  07530b58 07530cf0 00000005 07530d1c
0x0032e180:  00000000 00000007 0032e1c4 3987649b
Backtrace:
=>0 0x39875b8a in gdiplus (+0x75b8a) (0x0032e140)
  1 0x39921f44 in gdiplus (+0x121f44) (0x0032e15c)
  2 0x398b6029 in gdiplus (+0xb6029) (0x0032e188)
  3 0x3987649b in gdiplus (+0x7649b) (0x0032e1c4)
  4 0x39875084 in gdiplus (+0x75084) (0x0032e1e4)
  5 0x39874b4a in gdiplus (+0x74b4a) (0x0032e31c)
  6 0x398f4d5c in gdiplus (+0xf4d5c) (0x0032e53c)
  7 0x398f4f82 in gdiplus (+0xf4f82) (0x0032e5d8)
  8 0x00720054 in photoshop (+0x320054) (0x00280020)
  9 0x00000000 (0x00000000)
0x39875b8a: movl	0x0(%edi,%ecx,1),%ecx
Modules:
Module	Address			Debug info	Name (138 modules)
PE	  340000-  3e1000	Deferred        image_flow
PE	  400000- 36e1000	Export          photoshop
PE	 36f0000- 38bb000	Deferred        aif_ogl
PE	 38c0000- 38e9000	Deferred        data_flow
PE	 38f0000- 3910000	Deferred        image_runtime
PE	 3910000- 39f5000	Deferred        libifcoremd
PE	 3a00000- 3cc3000	Deferred        libmmd
PE	 3de0000- 3e36000	Deferred        plugplug
PE	 3e40000- 3e8a000	Deferred        bib
PE	 3e90000- 3f3a000	Deferred        axedomcore
PE	 3f40000- 407c000	Deferred        adobeowl
PE	 4080000- 42ab000	Deferred        adobeowlcanvas
PE	 42b0000- 42dc000	Deferred        ahclient
PE	 42e0000- 473c000	Deferred        mps
PE	 5970000- 59dd000	Deferred        adobexmp
PE	 5af0000- 5d9b000	Deferred        photoshop
PE	 5da0000- 5fce000	Deferred        psviews
PE	 5fd0000- 6273000	Deferred        psart
PE	 6690000- 6999000	Deferred        amtlib
PE	 6ab0000- 6b4d000	Deferred        amtservices
PE	 6d60000- 6d97000	Deferred        adobe_caps
PE	 6da0000- 6dc0000	Deferred        asneu
PE	10000000-10062000	Deferred        aif_core
PE	39800000-399b2000	Export          gdiplus
PE	70bd0000-70c35000	Deferred        shlwapi
PE	78130000-781cb000	Deferred        msvcr80
ELF	7b800000-7b954000	Deferred        kernel32<elf>
  \-PE	7b820000-7b954000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7be14000-7be28000	Deferred        msimg32<elf>
  \-PE	7be20000-7be28000	\               msimg32
ELF	7beeb000-7bf00000	Deferred        wtsapi32<elf>
  \-PE	7bef0000-7bf00000	\               wtsapi32
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7bf1b000-7bf3e000	Deferred        winhttp<elf>
  \-PE	7bf20000-7bf3e000	\               winhttp
ELF	7bf3e000-7bf5e000	Deferred        iphlpapi<elf>
  \-PE	7bf40000-7bf5e000	\               iphlpapi
ELF	7bf5e000-7bf85000	Deferred        netapi32<elf>
  \-PE	7bf60000-7bf85000	\               netapi32
ELF	7bf85000-7bf99000	Deferred        sti<elf>
  \-PE	7bf90000-7bf99000	\               sti
ELF	7bf99000-7bfad000	Deferred        lz32<elf>
  \-PE	7bfa0000-7bfad000	\               lz32
ELF	7bfad000-7bfc8000	Deferred        version<elf>
  \-PE	7bfb0000-7bfc8000	\               version
ELF	7c014000-7c048000	Deferred        uxtheme<elf>
  \-PE	7c020000-7c048000	\               uxtheme
ELF	7c048000-7c0b1000	Deferred        libgcrypt.so.11
ELF	7c0b1000-7c143000	Deferred        libkrb5.so.3
ELF	7c143000-7c1e0000	Deferred        libgnutls.so.26
PE	7c420000-7c4a7000	Deferred        msvcp80
ELF	7c4af000-7c4c5000	Deferred        libresolv.so.2
ELF	7c4c5000-7c4e9000	Deferred        libk5crypto.so.3
ELF	7c4e9000-7c514000	Deferred        libgssapi_krb5.so.2
ELF	7c514000-7c54b000	Deferred        libcups.so.2
ELF	7cde9000-7dd01000	Deferred        libglcore.so.1
ELF	7ddb6000-7ddba000	Deferred        libgpg-error.so.0
ELF	7ded5000-7dee7000	Deferred        libtasn1.so.3
ELF	7dee7000-7df00000	Deferred        spoolss<elf>
  \-PE	7def0000-7df00000	\               spoolss
ELF	7df00000-7df1e000	Deferred        localspl<elf>
  \-PE	7df10000-7df1e000	\               localspl
ELF	7df3f000-7df48000	Deferred        libxcursor.so.1
ELF	7df48000-7df4d000	Deferred        libxfixes.so.3
ELF	7df4d000-7df51000	Deferred        libxcomposite.so.1
ELF	7df51000-7df59000	Deferred        libxrandr.so.2
ELF	7df59000-7df63000	Deferred        libxrender.so.1
ELF	7df63000-7df69000	Deferred        libxxf86vm.so.1
ELF	7df69000-7df6d000	Deferred        libkeyutils.so.1
ELF	7df6d000-7df76000	Deferred        libkrb5support.so.0
ELF	7df76000-7df7a000	Deferred        libcom_err.so.2
ELF	7df83000-7dfa4000	Deferred        imm32<elf>
  \-PE	7df90000-7dfa4000	\               imm32
ELF	7dfa4000-7e040000	Deferred        winex11<elf>
  \-PE	7dfb0000-7e040000	\               winex11
ELF	7e088000-7e0af000	Deferred        libexpat.so.1
ELF	7e0af000-7e0dc000	Deferred        libfontconfig.so.1
ELF	7e0dc000-7e0f2000	Deferred        libz.so.1
ELF	7e0f2000-7e169000	Deferred        libfreetype.so.6
ELF	7e169000-7e16c000	Deferred        libxinerama.so.1
ELF	7e183000-7e1b1000	Deferred        ws2_32<elf>
  \-PE	7e190000-7e1b1000	\               ws2_32
ELF	7e1b1000-7e299000	Deferred        oleaut32<elf>
  \-PE	7e1d0000-7e299000	\               oleaut32
ELF	7e299000-7e34b000	Deferred        comdlg32<elf>
  \-PE	7e2a0000-7e34b000	\               comdlg32
ELF	7e34b000-7e413000	Deferred        comctl32<elf>
  \-PE	7e350000-7e413000	\               comctl32
ELF	7e413000-7e59f000	Deferred        shell32<elf>
  \-PE	7e420000-7e59f000	\               shell32
ELF	7e59f000-7e5b5000	Deferred        psapi<elf>
  \-PE	7e5a0000-7e5b5000	\               psapi
ELF	7e5b5000-7e604000	Deferred        dbghelp<elf>
  \-PE	7e5c0000-7e604000	\               dbghelp
ELF	7e604000-7e63a000	Deferred        winspool<elf>
  \-PE	7e610000-7e63a000	\               winspool
ELF	7e63a000-7e649000	Deferred        libgcc_s.so.1
ELF	7e738000-7e7aa000	Deferred        libglu.so.1
ELF	7e7ac000-7e7c4000	Deferred        imagehlp<elf>
  \-PE	7e7b0000-7e7c4000	\               imagehlp
ELF	7e7c4000-7e7c9000	Deferred        libxdmcp.so.6
ELF	7e7c9000-7e7e3000	Deferred        libxcb.so.1
ELF	7e7e3000-7e89d000	Deferred        libgl.so.1
ELF	7e89d000-7e98c000	Deferred        libx11.so.6
ELF	7e98c000-7e99c000	Deferred        libxext.so.6
ELF	7e99c000-7e9b4000	Deferred        libice.so.6
ELF	7e9b5000-7e9cc000	Deferred        glu32<elf>
  \-PE	7e9c0000-7e9cc000	\               glu32
ELF	7e9ce000-7ea66000	Deferred        opengl32<elf>
  \-PE	7e9e0000-7ea66000	\               opengl32
ELF	7ea66000-7ead5000	Deferred        msvcrt<elf>
  \-PE	7ea80000-7ead5000	\               msvcrt
ELF	7ead5000-7eb42000	Deferred        rpcrt4<elf>
  \-PE	7eae0000-7eb42000	\               rpcrt4
ELF	7eb42000-7ec3d000	Deferred        ole32<elf>
  \-PE	7eb60000-7ec3d000	\               ole32
ELF	7ec3d000-7ec93000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec93000	\               advapi32
ELF	7ec93000-7ed34000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed34000	\               gdi32
ELF	7ed34000-7ee7f000	Deferred        user32<elf>
  \-PE	7ed50000-7ee7f000	\               user32
ELF	7efa9000-7efb5000	Deferred        libnss_files.so.2
ELF	7efb5000-7efc0000	Deferred        libnss_nis.so.2
ELF	7efc0000-7efe6000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        libnsl.so.1
ELF	f7c02000-f7c06000	Deferred        libxau.so.6
ELF	f7c06000-f7c0f000	Deferred        libnss_compat.so.2
ELF	f7c10000-f7c14000	Deferred        libdl.so.2
ELF	f7c14000-f7d77000	Deferred        libc.so.6
ELF	f7d78000-f7d91000	Deferred        libpthread.so.0
ELF	f7d91000-f7d93000	Deferred        libnvidia-tls.so.1
ELF	f7d93000-f7d98000	Deferred        libuuid.so.1
ELF	f7d98000-f7da1000	Deferred        libsm.so.6
ELF	f7dab000-f7ee6000	Deferred        libwine.so.1
ELF	f7ee8000-f7f09000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Adobe\Adobe Photoshop CS4\Photoshop.exe
	00000022    0
	00000021    0
	00000020    0
	0000001f    0
	0000001e    0
	00000009    0 <==
0000000c 
	00000019    0
	00000015    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000014    0
	00000011    0
	00000010    0
00000016 
	0000001b    0
	0000001a    0
	00000018    0
	00000017    0
0000001c 
	0000001d    0
Backtrace:
=>0 0x39875b8a in gdiplus (+0x75b8a) (0x0032e140)
  1 0x39921f44 in gdiplus (+0x121f44) (0x0032e15c)
  2 0x398b6029 in gdiplus (+0xb6029) (0x0032e188)
  3 0x3987649b in gdiplus (+0x7649b) (0x0032e1c4)
  4 0x39875084 in gdiplus (+0x75084) (0x0032e1e4)
  5 0x39874b4a in gdiplus (+0x74b4a) (0x0032e31c)
  6 0x398f4d5c in gdiplus (+0xf4d5c) (0x0032e53c)
  7 0x398f4f82 in gdiplus (+0xf4f82) (0x0032e5d8)
  8 0x00720054 in photoshop (+0x320054) (0x00280020)
  9 0x00000000 (0x00000000)


```

---

### Post by GepettoBR on 2009-08-21
> **dannymichel said:**
> You seem like a nice guy so I'm going to give it to you straight. There are no similar apps. Some may tell you gimp but they are lying. Gimp is not a quater of the application Photoshop is. I'm just trying to save you some time. You NEED to get Photoshop working

While it's true that GIMP isn't even close to matching Photoshop's potential, onedemian said he wants Photoshop because he's gotten into photography. Photo enhancement and retouching is a task that touches even less of photoshop's capabilities. In my own experience, GIMP has always been more than sufficient in this field, and Photoshop is way overkill.

For more complex photomanipulations, designs, etc I wouldn't dream of saying that the GIMP is as good as, or even close to Photoshop. However, none of the extra features Adobe's product has are very useful or necessary in this particular field of activity.

@onedemian: if you want to try out GIMP and see if it matches your needs, but don't want to learn a new interface, try GIMPshop. It's GIMP with all the menus moved around to look like Photoshop, and it caters precisely to people like you.

---

### Post by Nugar on 2009-08-21
Just to let you know, guys: 1.1.28 breaks the installation.

Both Photoshop and Dreamweaver CS4 hang at launch.

---

### Post by dannymichel on 2009-08-21
> **Nugar said:**
> Just to let you know, guys: 1.1.28 breaks the installation.

Both Photoshop and Dreamweaver CS4 hang at launch.im still on .16

---

### Post by alex.rayu on 2009-08-22
**dannymichel**, I have installed and use Photoshop CS4 on both my wife's ATI video adapter machine and my Intel video adapter laptop. You CAN and you SHOULD be able to install and run Photoshop CS4. I use it all the time with type support and with complex PSD files, and it works just great. The only thing that does not work is the docking of the toolbox panels in one another, which is not important. This tells me that you are doing something wrong, and I can't see what from here. 

1. What is "dosdevices" doing in your Photoshop folder path? It should be installing to drive_c! (This may be unrelated to the current issue, but you can never tell).
2. You are showing a gdiplus error in your last dump. Which video adapter are you using? Does it have it's drivers installed? Try to set gdiplus to native in wine config and try again. Try set to built in and try again. You need to make sure compiz is off when you try it (it should run with compiz though - but you should try switching it off for an option).

---

### Post by dannymichel on 2009-08-22
> **alex.rayu said:**
> **dannymichel**, I have installed and use Photoshop CS4 on both my wife's ATI video adapter machine and my Intel video adapter laptop. You CAN and you SHOULD be able to install and run Photoshop CS4. I use it all the time with type support and with complex PSD files, and it works just great. The only thing that does not work is the docking of the toolbox panels in one another, which is not important. This tells me that you are doing something wrong, and I can't see what from here. 

1. What is "dosdevices" doing in your Photoshop folder path? It should be installing to drive_c! (This may be unrelated to the current issue, but you can never tell).
2. You are showing a gdiplus error in your last dump. Which video adapter are you using? Does it have it's drivers installed? Try to set gdiplus to native in wine config and try again. Try set to built in and try again. You need to make sure compiz is off when you try it (it should run with compiz though - but you should try switching it off for an option).
im on a fresh install
im not even going to install my graphics card 'restricted driver' or update anything.
the first thing im going to do it 
-download wine 1.1.16 from here
[http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_amd64.deb](http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_amd64.deb)
-install it
-copy and paste this into the terminal
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) (first)
then
sh winetricks msxml6 gdiplus gecko vcrun2005 (all in one shot second)
-'cd' into the directory with photoshop's 'Setup.exe' in it and type this into the terminal 'wine Setup.exe'
-Photoshop will install with default options checked
-i will then 'cd' into the directory with 'Photoshop.exe' in it and 'wine Photoshop.exe'
-I will run photoshop and post my errors

---

### Post by alex.rayu on 2009-08-23
Danny you forgot one thing: you then upgrade to 1.1.27 (or probably 1.1.28).

OLD wine is needed to INSTALL
NEW wine is needed to RUN

=)

---

### Post by Nugar on 2009-08-23
> **alex.rayu said:**
> Danny you forgot one thing: you then upgrade to 1.1.27 (or probably 1.1.28).

OLD wine is needed to INSTALL
NEW wine is needed to RUN

=)

1.1.28 broke my installation. Go for 1.1.27. Also, you can "Install" Photoshop portable under 1.1.26

---

### Post by dannymichel on 2009-08-23
> **alex.rayu said:**
> Danny you forgot one thing: you then upgrade to 1.1.27 (or probably 1.1.28).

OLD wine is needed to INSTALL
NEW wine is needed to RUN

=)[edit] i finally got it running on 1.1.27 but it looks like this 
[[IMG]http://img2.imagetitan.com/img2/small/28/28_screenshot201.png[/IMG]](http://img2.imagetitan.com/img.php?image=28_screenshot201.png)

---

### Post by CoolMeEddy on 2009-08-24
> **dannymichel said:**
> You seem like a nice guy so I'm going to give it to you straight. There are no similar apps. Some may tell you gimp but they are lying. Gimp is not a quater of the application Photoshop is. I'm just trying to save you some time. You NEED to get Photoshop working

Thank you for a straight and quick answer Danny. 
I'd like to add that my job doesn't consist of (only) quick retouches. I'm making adds, posters, banners and so on, so I really need the application to be very similar to photoshop. 
As I mentioned before, maybe CS3 is easier to set up? Maybe it's working more stable, less crashes? I can really live with cs3 if it's going to be reliable. Any one had experience with cs3? 

Again, I appreciate your time reading and replying to my question.

---

### Post by dannymichel on 2009-08-24
installing ie6 broke my instillation

---

### Post by alex.rayu on 2009-08-26
Yay! Danny you broke it? The way to fix your screenshot was to have the gdiplus and turn off the compiz while Photoshop runs. Congrats! You will be able to do it again!

---

### Post by CoolMeEddy on 2009-08-27
any information whether the Wacom Tablet will work with photoshop under UBUNTU?

---

### Post by dannymichel on 2009-08-28
> **alex.rayu said:**
> have the gdipluswhat does tha tmean?
i did gdiplus and set it as 'built in' to get it to work.

so ur saying noone can run photoshop properly via wine unless compiz is off?

im pretty sure i did have compiz running and i didnt have that 'menu bar problem' on another install

---

### Post by alex.rayu on 2009-08-28
No I cant run it with compiz on with Interl GMA but pretty sure can do it in latest wine with ATI.

---

### Post by dannymichel on 2009-08-28
> **alex.rayu said:**
> No I cant run it with compiz on with Interl GMA but pretty sure can do it in latest wine with ATI.

im on an nvidia

---

### Post by dannymichel on 2009-09-04
anyone try 1.1.29 with it yet?

---

### Post by eyeJ on 2009-09-07
Does someone have wacom intuos working with cs4 and pressure sensitivity?
I would like to use cs4 since i need some features it has over cs2 but last time I installed cs4 I couldn't get it to work with my intuos.
Can someone report if their intuos is working correctly with pressure sensitivity in Photoshop CS4? If so: are you using the manual xorg.conf method or the built in jaunty method to get the tablet to work? (see link here: [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) )

One last thing... my intuos works fine with cs2 on wine, gimp, cinepaint and other linux native apps and im currently using the xorg.conf method.

---

### Post by dannymichel on 2009-09-07
> **dannymichel said:**
> anyone try 1.1.29 with it yet?

bump?

---

### Post by eyeJ on 2009-09-07
> **dannymichel said:**
> anyone try 1.1.29 with it yet?

I'm quite sure you will need to turn off compiz to get it to work without those black things popping up. I think that I got some similar problems with cs4 when I used compiz but i cant tell for sure because it's been a while since i installed cs4 *currently im runing cs2. It's probably something to do with cs4 using open gl acceleration.

---

### Post by dannymichel on 2009-09-07
> **eyeJ said:**
> I'm quite sure you will need to turn off compiz to get it to work without those black things popping up. I think that I got some similar problems with cs4 when I used compiz but i cant tell for sure because it's been a while since i installed cs4 *currently im runing cs2. It's probably something to do with cs4 using open gl acceleration.i know i had cs4 installed and working with compiz on a 'hardy' install
but still... i was just wondering if anyone has use .29

---

### Post by lindix on 2009-09-09
> **alex.rayu said:**
> **dannymichel**, 

1. What is "dosdevices" doing in your Photoshop folder path? It should be installing to drive_c! (This may be unrelated to the current issue, but you can never tell).
2. You are showing a gdiplus error in your last dump. Which video adapter are you using? Does it have it's drivers installed? Try to set gdiplus to native in wine config and try again. Try set to built in and try again. You need to make sure compiz is off when you try it (it should run with compiz though - but you should try switching it off for an option).

Hi, can someone translate this for a beginner linux user.
I don't want to learn all this advanced stuff.
I have ubuntu 9.04 32 bit.
And I have hard time trying with all these wine versions.
Install only with wine 1.1.25 and only if I have ie6.
But hang at launch.
Thank you.

---

### Post by dannymichel on 2009-09-11
compiz is off. gdiplus is 'built in' because it work work any other way. but...
[[IMG]http://thumbnails8.imagebam.com/4848/f4d2f048477945.gif[/IMG]](http://www.imagebam.com/image/f4d2f048477945)
any ideas?

---

### Post by alex.rayu on 2009-09-12
Try toggle the gdiplus setting. If won't work, then no more ideas.

---

### Post by JustSteph on 2010-07-05
I'm also having problems making Photoshop CS4 to work in Ubuntu.

Is there any way of opening it in Ubuntu when it is installed and working on a Windows partition? I tried just copying the files from the Windows partition into my wine folder, but that didn't work. Nothing happened when I clicked on the program.

---

### Post by JustSteph on 2010-07-06
I've managed to get it to run the installation, but when I click on accept the license agreement, it closes. Running in terminal, I get this message after clicking accept:

err:mshtml:handle_htmlevent Could not get nsIDOMNode: 80004002
fixme:shdocvw:OleObject_Close (0x1cdad0)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1cdad0)
fixme:imm:ImmReleaseContext ((nil), 0x1cb340): stub
fixme:mshtml:HlinkTarget_SetBrowseContext (0x1d25f0)->((nil))
fixme:shdocvw:OleObject_Close (0x1cdad0)->(1)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x1cdf24 0x1cdf30 0x1059aa10 (nil)

I can't figure out what it's trying to tell me.

---

### Post by JustSteph on 2010-07-12
I read the thread again and some of it made more sense than it did last  few times I read through it (though most of it is still gobbledegook to  me) and I tried bottling. This is what I get:

steph@steph-laptop:~$ env WINEPREFIX=~/.wine_photoshop '/home/steph/.wine/drive_c/Program Files/Adobe/Adobe Photoshop CS4/Photoshop.exe' 
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library data_flow.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library image_runtime.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_flow.dll") not found
err:module:import_dll Library image_flow.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_ogl.dll") not found
err:module:import_dll Library aif_ogl.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\image_runtime.dll") not found
err:module:import_dll Library image_runtime.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\aif_core.dll") not found
err:module:import_dll Library aif_core.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\data_flow.dll") not found
err:module:import_dll Library data_flow.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\PlugPlug.dll") not found
err:module:import_dll Library PlugPlug.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\AdobeOwl.dll") not found
err:module:import_dll Library AdobeOwl.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\AdobeOwlCanvas.dll") not found
err:module:import_dll Library AdobeOwlCanvas.dll (which is needed by L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\steph\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Photoshop CS4\\Photoshop.exe" failed, status c0000135

Am I just missing a load of .dll files?

---

### Post by JustSteph on 2010-07-12
I'm running wine 1.2-rc7, how can I go back to 1.1.17 so I can at least install it?

---

### Post by proteusmoteus on 2010-07-14
In synaptic highlight the package you want to downgrade. Once the package is highlighted go to the "Package" menu and select "Force Version". As I am in Lucid that offers to downgrade my wine1.2 package to version 1.1.42. wine1.2-1.1.42 let me install a program that 1.2-rc7 coughed on.

Note the "wine" package in Lucid is a meta-package which if downgraded would do nothing. Look at the text description (from highlighting a package) to see if it is the same for you (assume you aren't running Lucid since 1.1.17 is really old).

---

### Post by JustSteph on 2010-07-14
I am running Lucid. I had 1.1.42 recently and Photoshop didn't install under it. Looking around, it seems that it only installs under 1.1.17. I've found a download of it, I just don't know how to then install it.

---

### Post by proteusmoteus on 2010-07-14
Well if you downloaded a deb from [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) then you have to first remove your wine1.2 and probably your wine package.
Use synaptic to search and mark to remove them then apply it. Afterwards installing the deb is done by double clicking the file.

---

### Post by JustSteph on 2010-07-14
Thank you. I have done that, installed Photoshop and updated to wine 1.2-rc7.

When I try to run photoshop I get a dialogue box telling me:
Licensing for this product has stopped working.
This product has encountered a problem which requires that you restart your computer before it can be launched.
If you continue to see this message after restarting your computer, please contact either your I administrator or Adobe technical support for help, and mention the error code shown at the bottom of this screen.
Error: 147:20
[http://www.adobe.com/support/](http://www.adobe.com/support/)

Restarting didn't work and the adobe website only has support for Windows and Mac.

---

### Post by proteusmoteus on 2010-07-14
I have never used Photoshop, much less via wine, so all I can do is offer some advice and links. First if a wine app tells you to restart your computer **dont** restart your computer. The app is talking about windows and you are running ubuntu. Instead check for and kill any wine processes that are running via 'ps -ef | grep -e .exe -e wine'. Next try the '[wineboot]("http://wiki.winehq.org/wineboot")' command. Second, when trying to get an application to work with wine don't assume the newest version of wine is the best. I currently favor wine 1.1.42 over 1.2-rc7 for running windows applications due to 1.1.42 working better for my use cases.

Looking at wine's appdb it says even if you do all the tricks to get Photoshop working there are going to be things in the program that don't work (understood from silver rating). 

[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop) which lists a known [URL="http://bugs.winehq.org/show_bug.cgi?id=10085"]license bug
[/URL][http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318)
above link rates Photoshop CS4 as [silver]("http://appdb.winehq.org/help/?sTopic=maintainer_ratings").
[http://forum.winehq.org/viewforum.php?f=2](http://forum.winehq.org/viewforum.php?f=2)

---

