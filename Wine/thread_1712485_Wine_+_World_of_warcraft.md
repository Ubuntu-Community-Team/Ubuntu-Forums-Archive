---
title: "Wine + World of warcraft"
date: 2011-03-22
forum: Wine
---

### Post by j0mpa on 2011-03-22
Hey all,
Need a little help over here.
I just installed Linux Mint 10 before i used Ubuntu 10.10 but found Linux Mint faster some how.
Well my problem is i've been playing world of warcraft in Ubuntu whit no problem and iam using the same drivers from ati's homepage that i used in Ubuntu.
I have looked over the xorg.conf and it looks the same as the one in Ubuntu.

But still when i start World of Warcraft i get a strange picture. I've upload the picture.

And fglrxinfo give me this.

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 5400 Series 
OpenGL version string: 4.1.10524 Compatibility Profile Context
```


And glxinfo | grep rendering gives me
```
direct rendering: Yes
```


This is my Xorg.conf
```

Section "ServerLayout"
   Identifier     "aticonfig Layout"
   Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
   Identifier   "aticonfig-Monitor[0]-0"
   Option       "VendorName" "ATI Proprietary Driver"
   Option       "ModelName" "Generic Autodetecting Monitor"
   Option       "DPMS" "true"
EndSection

Section "Monitor"
   Identifier   "0-LVDS"
   Option       "VendorName" "ATI Proprietary Driver"
   Option       "ModelName" "Generic Autodetecting Monitor"
   Option       "DPMS" "true"
   Option       "PreferredMode" "1366x768"
   Option       "TargetRefresh" "60"
   Option       "Position" "0 0"
   Option       "Rotate" "normal"
   Option       "Disable" "false"
EndSection

Section "Device"
   Identifier  "aticonfig-Device[0]-0"
   Driver      "fglrx"
   Option       "Monitor-LVDS" "0-LVDS"
   BusID       "PCI:1:0:0"
EndSection

Section "Screen"
   Identifier "aticonfig-Screen[0]-0"
   Device     "aticonfig-Device[0]-0"
   DefaultDepth     24
   SubSection "Display"
      Viewport   0 0
      Depth     24
   EndSubSection
EndSection
```


Any one who had the same problem or might know what the problem is ? 
And i also have made some tweaks to the wow config.

---

### Post by dino99 on 2011-03-23
check that its not a xorg.conf issue:

rename it to xorg.confold then reboot

---

### Post by j0mpa on 2011-03-24
> **dino99 said:**
> check that its not a xorg.conf issue:

rename it to xorg.confold then reboot

Thanks for the reply and this was the first thing i tried and that did not work either. 

Sorry maybe should have wrote that :)

---

### Post by Soulcage on 2011-03-24
Does disabling UseGLSL do anything? If you haven't already done it.
[http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys")

---

### Post by j0mpa on 2011-03-24
> **Soulcage said:**
> Does disabling UseGLSL do anything? If you haven't already done it.
[http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys")

Well i haven't tried and i cant try either because i want back to Ubuntu.

---

### Post by Soulcage on 2011-03-26
UseGLSL is a wine setting... :confused:

---

### Post by Fiiras on 2011-03-26
Its NOT work :( :(:(:(
```
err:service:validate_service_config Service L"Evesetbosvm" is Win32 but has no image path set
err:service:scmdatabase_load_services Invalid configuration of service L"Evesetbosvm" - skipping
fixme:reg:RegSetKeySecurity :(0x78,4,0x13d100): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (15000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 15000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
root@firas-desktop:~# fixme:reg:RegSetKeySecurity :(0x70,4,0x13d710): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (15000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 15000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:shell:InitNetworkAddressControl stub
fixme:shdocvw:PersistStreamInit_Load (0x17ae38)->(0x33df38)
fixme:shdocvw:OleControl_FreezeEvents (0x17ae38)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x17ae38)->(0)
fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x19f768, 0x33db00
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33d46c
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800012c)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800012c)
fixme:iphlpapi:NotifyAddrChange (Handle 0xc4be8d8, overlapped 0xc4be8e0): stub
0[21be50]: IMM32: InitKeyboardLayout, aKeyboardLayout=10091009, sCodePage=1252, sIMEProperty=00090000
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x17aee0)->((null) 1 0x33dba4 (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3bf2ea8)->()
fixme:shdocvw:ClientSite_GetContainer (0x17aee0)->(0x33db74)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetRequestHeader (0x3bf2ea8)->(0x33c6c8 0x3bf36fc)
fixme:mshtml:nsChannel_GetRequestMethod (0x3bf2ea8)->(0x33c888)
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:mshtml:nsChannel_GetReferrer (0x3bf2ea8)->(0x33cda8)
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3bf2ea8)->(0x33cc94)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3bf2ea8)->(0x33cc90)
fixme:mshtml:nsChannel_GetReferrer (0x3bf2ea8)->(0x33cde8)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c07188)->(0x33ca98 0x33cb28 0)
fixme:mshtml:nsChannel_SetReferrer (0x3c07188)->(0x3bf3bc8)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c07898)->(0x33ca98 0x33cb28 0)
fixme:mshtml:nsChannel_SetReferrer (0x3c07898)->(0x3bf3bc8)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c07d88)->(0x33ca68 0x33ca78 0)
fixme:mshtml:nsChannel_SetReferrer (0x3c07d88)->(0x3bf3bc8)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x17aee0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c072d8)->(0x33dfc4 0x33dfb0 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c079c8)->(0x33dfc4 0x33dfb0 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c07ea0)->(0x33dfc4 0x33dfb0 0)
fixme:shdocvw:ClientSite_GetContainer (0x17aee0)->(0x33e4d8)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x17aee0)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:mshtml:nsChannel_Open (0x3a0d4a8)->(0x33b718)
fixme:mshtml:nsChannel_SetRequestHeader (0x3be1db8)->(0x33e228 0x3b5a7f4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3be1db8)->()
fixme:mshtml:nsChannel_SetReferrer (0x3be1db8)->(0x3bf3bc8)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3befd80)->(0x33dfc4 0x33dfb0 0)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 21
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x3c07d88)->(0x33d750)
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Mon, 25-Mar-2013 10:52:54 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Mon, 25-Mar-2013 10:52:54 GMT")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Mon, 25-Mar-2013 10:52:54 GMT")
fixme:mshtml:nsChannel_SetRequestHeader (0x3c17638)->(0x33d678 0x3b5a7f4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c17638)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c17638)->(0x3bf3bc8)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c03c18)->(0x33dc88 0x3b5a7f4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c03c18)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c03c18)->(0x3bf3bc8)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c23f28)->(0x33c278 0x3b5a7f4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c23f28)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c23f28)->(0x3bf3bc8)
fixme:mshtml:nsChannel_SetRequestHeader (0x3b5a740)->(0x33c278 0x3b5a7f4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3b5a740)->()
fixme:mshtml:nsChannel_SetReferrer (0x3b5a740)->(0x3bf3bc8)
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsURL_GetQuery default action not implemented
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsURL_GetRef default action not implemented
0[21be50]: file (null), line 0: uncaught exception: [Exception... "Component returned failure code: 0x80004001 (NS_ERROR_NOT_IMPLEMENTED) [nsIDOMLocation.hash]"  nsresult: "0x80004001 (NS_ERROR_NOT_IMPLEMENTED)"  location: "JS frame :: wine:http://launcher.wow-europe.com/2.0/_js/swfobject.js :: anonymous :: line 8"  data: no]
fixme:mshtml:nsChannel_SetRequestHeader (0x3c2cf78)->(0x33dc88 0x3b5a7f4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c2cf78)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c2cf78)->(0x3bf3bc8)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c2eca0)->(0x33dc88 0x3b5a7f4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c2eca0)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c2eca0)->(0x3bf3bc8)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c30730)->(0x33c724 0x33c734 0)
fixme:mshtml:nsChannel_SetReferrer (0x3c30730)->(0x3bf3bc8)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c17a38)->(0x33db0c 0x33daf8 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c1ceb0)->(0x33db0c 0x33daf8 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c24320)->(0x33db0c 0x33daf8 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c24b38)->(0x33db0c 0x33daf8 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c2d368)->(0x33db0c 0x33daf8 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c2f048)->(0x33db0c 0x33daf8 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c2f9e0)->(0x33db0c 0x33daf8 0)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c48458)->(0x33d3c8 0x3b5a7f4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c48458)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c48458)->(0x3c075a8)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c4b330)->(0x33d3c8 0x3b5a7f4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c4b330)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c4b330)->(0x3c06b60)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c4bb60)->(0x33cf08 0x3b5a7f4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c4bb60)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c4bb60)->(0x3c06b60)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c4c8d0)->(0x33ca48 0x3b5a7f4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c4c8d0)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c4c8d0)->(0x3c06b60)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c4c498)->(0x33d3c8 0x3b5a7f4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c4c498)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c4c498)->(0x3c075a8)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c49a50)->(0x33d888 0x3b5a7f4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c49a50)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c49a50)->(0x3c06b60)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c4b1b0)->(0x33dfc4 0x33dfb0 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c4b720)->(0x33dfc4 0x33dfb0 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c4bf50)->(0x33dfc4 0x33dfb0 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c4ccb0)->(0x33dfc4 0x33dfb0 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c4f1d8)->(0x33dfc4 0x33dfb0 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c50950)->(0x33dfc4 0x33dfb0 0)
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c17638)->(0x33d5c0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c17638)->(0x33d5c0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c03c18)->(0x33d5c0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c03c18)->(0x33d5c0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c23f28)->(0x33d5c0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c23f28)->(0x33d5c0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3b5a740)->(0x33d5c0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3b5a740)->(0x33d5c0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c2cf78)->(0x33d5c0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c2cf78)->(0x33d5c0)
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Sat, 26-Mar-2011 11:07:56 GMT; path=/; domain=.doubleclick.net")
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c4b330)->(0x33d5c0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c4b330)->(0x33d5c0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c4c8d0)->(0x33d5c0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c4c8d0)->(0x33d5c0)
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Monday, 25-Mar-2013 00:00:00 GMT; path=/; domain=.atdmt.com")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Wednesday, 12-Oct-2011 00:00:00 GMT; path=/; domain=.atdmt.com")
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c2eca0)->(0x33d5c0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c2eca0)->(0x33d5c0)
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Mon, 25-Mar-2013 10:52:56 GMT; path=/; domain=.doubleclick.net")
fixme:wininet:set_cookie Unknown additional option L"Max-Age=0; expires=Mon, 21-July-2008 23:59:00 GMT"
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x3c30730)->(0x33d750)
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsChannel_SetRequestHeader (0x3c4c6b8)->(0x33c724 0x33c734 0)
fixme:mshtml:nsChannel_SetReferrer (0x3c4c6b8)->(0x3bf3bc8)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3c4c748)->(0x33db0c 0x33daf8 0)
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Mon, 25-Mar-2013 10:52:57 GMT; path=/; domain=.doubleclick.net")
fixme:wininet:set_cookie Unknown additional option L"Max-Age=0; expires=Mon, 21-July-2008 23:59:00 GMT"
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3be1db8)->(0x33d5c0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3be1db8)->(0x33d5c0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x3c4c6b8)->(0x33d750)
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsURI_GetUserPass default action not implemented
0[21be50]: NPN Logging Active!
0[21be50]: General Plugin Logging Active! (nsPluginHost::ctor)
0[21be50]: NPP Logging Active!
0[21be50]: nsPluginHost::ctor
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsURI_GetHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsURL_GetQuery default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsURL_GetRef default action not implemented
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c4c498)->(0x33d5c0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c4c498)->(0x33d5c0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c4bb60)->(0x33d5c0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c4bb60)->(0x33d5c0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c49a50)->(0x33d5c0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c49a50)->(0x33d5c0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c48458)->(0x33d5c0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c48458)->(0x33d5c0)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:InPlaceFrame_SetStatusText (0x17aee0)->(L"Done")
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3bf2ea8)->(0x33d4f4)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3bf2ea8)->(0x33d4f0)
err:header:HEADER_WindowProc unknown msg 105f wp=0000 lp=0033da14
err:header:HEADER_WindowProc unknown msg 105f wp=0001 lp=0033da14
err:header:HEADER_WindowProc unknown msg 105f wp=0002 lp=0033da14
err:header:HEADER_WindowProc unknown msg 105f wp=0003 lp=0033da14
err:header:HEADER_WindowProc unknown msg 105f wp=0004 lp=0033da14
err:header:HEADER_WindowProc unknown msg 105f wp=0005 lp=0033da14
err:header:HEADER_WindowProc unknown msg 105f wp=0006 lp=0033da14
err:header:HEADER_WindowProc unknown msg 105f wp=0007 lp=0033da14
err:header:HEADER_WindowProc unknown msg 105f wp=0008 lp=0033da14
err:header:HEADER_WindowProc unknown msg 105f wp=0009 lp=0033da14
err:header:HEADER_WindowProc unknown msg 105f wp=000a lp=0033da14

```

---

