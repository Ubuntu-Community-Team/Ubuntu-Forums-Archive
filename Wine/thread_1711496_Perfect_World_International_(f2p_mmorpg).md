---
title: "Perfect World International (f2p mmorpg)"
date: 2011-03-21
forum: Wine
---

### Post by MilesLuminis on 2011-03-21
heyaz ^^
well, im back to LINUX.. after a bit of using my comps for gaming purpose only with Vista, had the idea of finally trashing Windows... said and done.. my lappy is running Kubuntu 10.10 full updated and everything is fine after i got used to it again..
now to my problem:
im still gaming active, and know that wine and PlayOnLinux makes possible to run most stuff, and im used to it more or less, but this game just refuses to run.. i created the Direct3D in Registry, set the values provided here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923&iTestingId=61888](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923&iTestingId=61888) and ye.. trying since 3days now to make it work *lol* ...i refuse to install windows again and i rly want to get it to work.. but im done with my knowledge and tryed all guides i found.. 
tell me what u want to know.. will upload a video so u see what happens when i try to run it... 
what might be intresting for u also is that the game was running like 6months ago w/o problems with POL on 10.04 i didnt need to do anything else than set the .exe i want it to run from.. also that i didnt installed it, since this game works fine with copying and did so last time with LINUX...


PS: any suggestions what programm to use for recording my screen?

---

### Post by cogadh on 2011-03-21
We don't need a video of it. Just run it from the terminal and post Wine's error output, it will probably be much more informative than the video would be anyway.

---

### Post by MilesLuminis on 2011-03-25
> **cogadh said:**
> We don't need a video of it. Just run it from the terminal and post Wine's error output, it will probably be much more informative than the video would be anyway.

```
miles@miles-HP-G6000-GH831EA-ABD:~/Perfect World Entertainment/Perfect World International/launcher$ wine start 'launcher.exe'
fixme:exec:SHELL_execute flags ignored: 0x00000100
miles@miles-HP-G6000-GH831EA-ABD:~/Perfect World Entertainment/Perfect World International/launcher$ fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 90000
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 90000
fixme:win:EnumDisplayDevicesW ((null),0,0x33f718,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f680,0x00000000), stub!
fixme:shdocvw:PersistStreamInit_InitNew (0x15eca8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 90000
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 90000
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x6ad408
fixme:iphlpapi:NotifyAddrChange (Handle 0x35de8d8, overlapped 0x35de8e0): stub
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x15ed50)->((null) 1 0x6adb40 (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x384b460)->()
fixme:shdocvw:ClientSite_GetContainer (0x15ed50)->(0x6adb10)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetRequestHeader (0x384b460)->(0x6ac664 0x384bc94)
fixme:mshtml:nsChannel_GetRequestMethod (0x384b460)->(0x6ac824)
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:mshtml:nsChannel_GetReferrer (0x384b460)->(0x6acd44)
fixme:mshtml:nsChannel_IsNoStoreResponse (0x384b460)->(0x6acc30)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x384b460)->(0x6acc2c)
fixme:mshtml:nsChannel_GetReferrer (0x384b460)->(0x6acd84)
fixme:mshtml:nsChannel_SetResponseHeader (0x384b460)->(0x6ace84 0x6acd04 1)
fixme:mshtml:nsChannel_SetRequestHeader (0x385f330)->(0x6aca04 0x6aca14 0)
fixme:mshtml:nsChannel_SetReferrer (0x385f330)->(0x384cb40)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x15ed50)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x385f478)->(0x6adaac 0x6ada98 0)
fixme:shdocvw:ClientSite_GetContainer (0x15ed50)->(0x6ae604)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x15ed50)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:mshtml:nsChannel_SetRequestHeader (0x3845588)->(0x6ae2b4 0x6ae2c4 0)
fixme:mshtml:nsChannel_SetReferrer (0x3845588)->(0x384cb40)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x37b99f0)->(0x6adaac 0x6ada98 0)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 21
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 90000
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x385f330)->(0x6ad6ec)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x3845588)->(0x6ad6ec)
fixme:mshtml:nsChannel_Open (0x6e0a228)->(0x6ac454)
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsChannel_SetRequestHeader (0x6d49ad0)->(0x6adc24 0x37c42e4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x6d49ad0)->()
fixme:mshtml:nsChannel_SetReferrer (0x6d49ad0)->(0x384cb40)
fixme:mshtml:nsChannel_SetRequestHeader (0x6cda5c0)->(0x6adc24 0x37c42e4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x6cda5c0)->()
fixme:mshtml:nsChannel_SetReferrer (0x6cda5c0)->(0x384cb40)
fixme:mshtml:nsChannel_SetRequestHeader (0x6ce9668)->(0x6adc24 0x37c42e4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x6ce9668)->()
fixme:mshtml:nsChannel_SetReferrer (0x6ce9668)->(0x384cb40)
fixme:mshtml:nsChannel_SetRequestHeader (0x6ce2bd0)->(0x6adc24 0x37c42e4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x6ce2bd0)->()
fixme:mshtml:nsChannel_SetReferrer (0x6ce2bd0)->(0x384cb40)
fixme:mshtml:nsChannel_SetRequestHeader (0x6f766e8)->(0x6adc24 0x37c42e4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x6f766e8)->()
fixme:mshtml:nsChannel_SetReferrer (0x6f766e8)->(0x384cb40)
fixme:mshtml:nsChannel_SetRequestHeader (0x6cf5248)->(0x6adc24 0x37c42e4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x6cf5248)->()
fixme:mshtml:nsChannel_SetReferrer (0x6cf5248)->(0x384cb40)
fixme:mshtml:nsChannel_SetRequestHeader (0x6d619c0)->(0x6adc24 0x37c42e4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x6d619c0)->()
fixme:mshtml:nsChannel_SetReferrer (0x6d619c0)->(0x384cb40)
fixme:mshtml:nsChannel_SetRequestHeader (0x6d73800)->(0x6adc24 0x37c42e4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x6d73800)->()
fixme:mshtml:nsChannel_SetReferrer (0x6d73800)->(0x384cb40)
fixme:mshtml:nsChannel_SetRequestHeader (0x6d7f9b8)->(0x6adc24 0x37c42e4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x6d7f9b8)->()
fixme:mshtml:nsChannel_SetReferrer (0x6d7f9b8)->(0x384cb40)
fixme:mshtml:nsChannel_SetRequestHeader (0x6d981c0)->(0x6ad594 0x37c42e4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x6d981c0)->()
fixme:mshtml:nsChannel_SetReferrer (0x6d981c0)->(0x384cb40)
fixme:mshtml:nsChannel_SetRequestHeader (0x6db9520)->(0x6ad594 0x37c42e4 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x6db9520)->()
fixme:mshtml:nsChannel_SetReferrer (0x6db9520)->(0x384cb40)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6cd2630)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x37a4c18)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6e07420)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6cef3c8)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6cf8570)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6d66230)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6d75b70)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6d70aa0)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x37c2068)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6daf3f8)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6db1948)->(0x6adaac 0x6ada98 0)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x6ce9668)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x6ce9668)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x6f766e8)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x6f766e8)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x6ce2bd0)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x6ce2bd0)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x6cda5c0)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x6cda5c0)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x6d49ad0)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x6d49ad0)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x6d7f9b8)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x6d7f9b8)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x6d73800)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x6d73800)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x6cf5248)->(0x6ad0a8)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x6cf5248)->(0x6ad0a8)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x6d619c0)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x6d619c0)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x6db9520)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x6db9520)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x6d981c0)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x6d981c0)->(0x6ad55c)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:InPlaceFrame_SetStatusText (0x15ed50)->(L"Done")
fixme:mshtml:nsChannel_IsNoStoreResponse (0x384b460)->(0x6ade70)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x384b460)->(0x6ade6c)
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 90000
fixme:win:EnumDisplayDevicesW ((null),0,0x33e718,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e680,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x4fb4c70,0x4fb5200): stub
err:ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err:ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x33e6c0,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d8:ValidateVertexShader (0x50ff5d0 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidatePixelShader (0x55334d0 (nil) 0 (nil)): stub
err:mmtime:TIME_MMTimeStop Timer still active?!


```


errr yeah.. the game needs to be started from a launcher, after all this the launcher keeps open in a "runed" way... u only can use it once since more than one client isnt allowed... :lolflag: ...tell me if u need more informations ^^
(sry bout being that late, hadnt internet connection last few days >.> )

---

### Post by cogadh on 2011-03-25
Is there a reason you needed to use "wine start" and not just the normal (for want of a better word) method "wine launcher.exe"?

---

### Post by MilesLuminis on 2011-03-28
```
miles@miles-HP-G6000-GH831EA-ABD:~/Perfect World Entertainment/Perfect World International/launcher$ wine launcher.exe
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 90000
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 90000
miles@miles-HP-G6000-GH831EA-ABD:~/Perfect World Entertainment/Perfect World International/launcher$ fixme:win:EnumDisplayDevicesW ((null),0,0x33f718,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f680,0x00000000), stub!
fixme:shdocvw:PersistStreamInit_InitNew (0x15eca8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 90000
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 90000
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 90000
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x6ad408
fixme:iphlpapi:NotifyAddrChange (Handle 0x56ce8d8, overlapped 0x56ce8e0): stub
0[1eed58]: IMM32: InitKeyboardLayout, aKeyboardLayout=04090409, sCodePage=1252, sIMEProperty=00090000
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x15ed50)->((null) 1 0x6adb40 (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3eaad60)->()
fixme:shdocvw:ClientSite_GetContainer (0x15ed50)->(0x6adb10)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetRequestHeader (0x3eaad60)->(0x6ac664 0x3eb1334)
fixme:mshtml:nsChannel_GetRequestMethod (0x3eaad60)->(0x6ac824)
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:mshtml:nsChannel_GetReferrer (0x3eaad60)->(0x6acd44)
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3eaad60)->(0x6acc30)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3eaad60)->(0x6acc2c)
fixme:mshtml:nsChannel_GetReferrer (0x3eaad60)->(0x6acd84)
fixme:mshtml:nsChannel_SetResponseHeader (0x3eaad60)->(0x6ace84 0x6acd04 1)
fixme:mshtml:nsChannel_SetRequestHeader (0x3f660c8)->(0x6aca04 0x6aca14 0)
fixme:mshtml:nsChannel_SetReferrer (0x3f660c8)->(0x3eb1190)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x15ed50)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3f66210)->(0x6adaac 0x6ada98 0)
fixme:mshtml:nsChannel_SetRequestHeader (0x321a0b0)->(0x6ae2b4 0x6ae2c4 0)
fixme:mshtml:nsChannel_SetReferrer (0x321a0b0)->(0x3eb1190)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x395bfd0)->(0x6adaac 0x6ada98 0)
fixme:shdocvw:ClientSite_GetContainer (0x15ed50)->(0x6ae604)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x15ed50)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 21
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x3f660c8)->(0x6ad6ec)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x321a0b0)->(0x6ad6ec)
fixme:mshtml:nsChannel_Open (0x39b4ef0)->(0x6ac454)
fixme:mshtml:nsURI_GetUserPass default action not implemented
fixme:mshtml:nsChannel_SetRequestHeader (0x3c6cd90)->(0x6adc24 0x37a1bbc 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c6cd90)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c6cd90)->(0x3eb1190)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c953a8)->(0x6adc24 0x37a1bbc 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c953a8)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c953a8)->(0x3eb1190)
fixme:mshtml:nsChannel_SetRequestHeader (0x3c5c610)->(0x6adc24 0x37a1bbc 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3c5c610)->()
fixme:mshtml:nsChannel_SetReferrer (0x3c5c610)->(0x3eb1190)
fixme:mshtml:nsChannel_SetRequestHeader (0x39d2320)->(0x6adc24 0x37a1bbc 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x39d2320)->()
fixme:mshtml:nsChannel_SetReferrer (0x39d2320)->(0x3eb1190)
fixme:mshtml:nsChannel_SetRequestHeader (0x3a63d30)->(0x6adc24 0x37a1bbc 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3a63d30)->()
fixme:mshtml:nsChannel_SetReferrer (0x3a63d30)->(0x3eb1190)
fixme:mshtml:nsChannel_SetRequestHeader (0x39f71e0)->(0x6adc24 0x37a1bbc 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x39f71e0)->()
fixme:mshtml:nsChannel_SetReferrer (0x39f71e0)->(0x3eb1190)
fixme:mshtml:nsChannel_SetRequestHeader (0x65355d8)->(0x6ad584 0x37a1bbc 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x65355d8)->()
fixme:mshtml:nsChannel_SetReferrer (0x65355d8)->(0x3eb1190)
fixme:mshtml:nsChannel_SetRequestHeader (0x75cc068)->(0x6adc24 0x37a1bbc 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x75cc068)->()
fixme:mshtml:nsChannel_SetReferrer (0x75cc068)->(0x3eb1190)
fixme:mshtml:nsChannel_SetRequestHeader (0x368a4c8)->(0x6adc24 0x37a1bbc 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x368a4c8)->()
fixme:mshtml:nsChannel_SetReferrer (0x368a4c8)->(0x3eb1190)
fixme:mshtml:nsChannel_SetRequestHeader (0x3f4e0f8)->(0x6adc24 0x37a1bbc 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x3f4e0f8)->()
fixme:mshtml:nsChannel_SetReferrer (0x3f4e0f8)->(0x3eb1190)
fixme:mshtml:nsChannel_SetRequestHeader (0x173e70)->(0x6adb74 0x37a1bbc 0)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x173e70)->()
fixme:mshtml:nsChannel_SetReferrer (0x173e70)->(0x3eb1190)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3cd7f18)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3ca9d58)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3be30f0)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3aa0a38)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3a24cc8)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x336e918)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x35d68d0)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x7523248)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3623148)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x3fb15a8)->(0x6adaac 0x6ada98 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x5d19d30)->(0x6adaac 0x6ada98 0)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c953a8)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c953a8)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x39d2320)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x39d2320)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3a63d30)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3a63d30)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c5c610)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c5c610)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x65355d8)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x65355d8)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x39f71e0)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x39f71e0)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x75cc068)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x75cc068)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3c6cd90)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3c6cd90)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x173e70)->(0x6ad55c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x173e70)->(0x6ad55c)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x368a4c8)->(0x6ad0a8)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x368a4c8)->(0x6ad0a8)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3f4e0f8)->(0x6ad0a8)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3f4e0f8)->(0x6ad0a8)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:InPlaceFrame_SetStatusText (0x15ed50)->(L"Done")
fixme:mshtml:nsChannel_IsNoStoreResponse (0x3eaad60)->(0x6ade70)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x3eaad60)->(0x6ade6c)
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 90000
fixme:win:EnumDisplayDevicesW ((null),0,0x33e718,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e680,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x4fb50e8,0x4fb5008): stub
err:ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err:ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x33e6c0,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d8:ValidateVertexShader (0x50ff518 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidatePixelShader (0x5533418 (nil) 0 (nil)): stub

```

nope, none at all ^^ just used to it more or less to do it like that.. was the thing i found 2years ago first time some1 wanted me to start an .exe with the terminal..

---

