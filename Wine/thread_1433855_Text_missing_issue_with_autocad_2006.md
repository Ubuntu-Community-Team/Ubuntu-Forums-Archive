---
title: "Text missing issue with autocad 2006"
date: 2010-03-19
forum: Wine
---

### Post by 2LSS on 2010-03-19
Hi,
I installed autocad 2006 using the guide [from winehq]("http://appdb.winehq.org/appview.php?iVersionId=6035"). 

    > 1. Use recent version of Wine(tested with Wine-1.1.17)

    2. Download winetricks by following command

 ```
wget http://www.kegel.com/wine/winetricks
```

    3. Install required components by following command

```
sh winetricks gecko gdiplus msxml3 dotnet20 corefonts tahoma
```

    It will take some time because winetricks will download all above components

    4. navigate to your AutoCAD 2006 CD and run

```
wine setup.exe
``` 
The program works good but there is a glitch where some text is not displayed on dropdown menus and the activation screen. Both can be seen in the attached screen shots. 
I have tried:
-Running with and without metacity's composting. 
-Windows versions 98, 2000, and xp
-Disable the "Allow the window manager to decorate the windows" and "Allow the window manager to control the windows" boxes in winecfg.
-Installing every font I could find with winetricks
-Adding the file norender.txt to the registry found in the [wine faq]("http://wiki.winehq.org/FAQ#head-3b18ce54edb7ea108c8f08945bc52812c4e3ef71"). The faq also mentions a few other bugs but they don't apply to my situation.

Here are my specs.
wine version: 1.1.39
Ubuntu: 8.04
chipset: Intel Mobile GM965/GL960
Here is the terminal output:
```
user@user:~/.wine/drive_c/Program Files/AutoCAD 2006$ wine ACAD.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32f620,0x00000000), stub!
fixme:shell:IQueryAssociations_fnInit unsupported flags: 2
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0xde0a30): stub
fixme:dciman:DCICreatePrimary 0x82c 0x14022ac
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x32f26c,0x32f270): stub
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4100c
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"
fixme:shdocvw:PersistStreamInit_Load (0x21ba40)->(0x32db78)
fixme:shdocvw:OleControl_FreezeEvents (0x21ba40)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x21ba40)->(0)
fixme:wininet:InternetCheckConnectionW 
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x329890
fixme:iphlpapi:NotifyAddrChange (Handle 0x7bfe928, overlapped 0x7bfe930): stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
0[61134b0]: IMM32: InitKeyboardLayout, aKeyboardLayout=04090409, sCodePage=1252, sIMEProperty=00090000
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x21bae0)->((null) 1 0x32a768 (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->((null) 25 2 0x32a77c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->((null) 26 2 0x32a77c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x21bae0)->(0x32a7b8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32a844 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32a86c)
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000001
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000002
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->((null) 29 2 0x32dfbc (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x21bae0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32df94)
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32df94)
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:shdocvw:ClientSite_GetContainer (0x21bae0)->(0x32e0e4)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x21bae0)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->((null) 25 2 0x32e018 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->((null) 26 2 0x32e018 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->((null) 26 2 0x32d6ac (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->((null) 29 2 0x32d6bc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x21bae0)->(L"Done")
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->((null) 28 2 0x32d664 (nil))
fixme:jscript:to_object unsupported vt 0
fixme:mshtml:HTMLDocument_get_charset (0x610a968)->(0x32df4c)
fixme:mshtml:HTMLDocument_get_defaultCharset (0x610a968)->(0x32df50)
fixme:shdocvw:ClOleCommandTarget_Exec (0x21bae0)->((null) 21 2 (nil) (nil))
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x21ba40)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x610a968)->((nil))
fixme:shdocvw:OleObject_Close (0x21ba40)->(1)
fixme:shell:IShellLinkA_fnGetPath (0x18d1d8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x18d1d8): WIN32_FIND_DATA is not yet filled.
```

Does anybody know what could be going on? Other than a few other minor things autocad 2006 runs very well in wine and I would love to be able to activate and use it.

---

