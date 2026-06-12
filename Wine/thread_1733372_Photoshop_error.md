---
title: "Photoshop error"
date: 2011-04-19
forum: Wine
---

### Post by Dudutzu on 2011-04-19
Hello,

I recently reinstalled Ubuntu 10.10( the older one was a little crippled from multiple tests )

And now I can't use Photoshop CS5 Portable. The Software is OK because it worked perfectly before reinstalling .


Wine version is  : 1.3.18
  Wine has installed : Gecko; .net; CoreFonts
Drivers for graphic card are installed.(in ubuntu not in wine,lol)

Anyway this is the console output : 

```
dudutzu@Proteus:~/Downloads/PhotoshopPortable$ wine PhotoshopCS5Portable.
wine: cannot find L"C:\\windows\\system32\\PhotoshopCS5Portable."
dudutzu@Proteus:~/Downloads/PhotoshopPortable$ wine PhotoshopCS5Portable.exe
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
err:shell:HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:system:SetProcessDPIAware stub!
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:ntdll:NtSetInformationToken unimplemented class 24
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x1ee63c 0x1ee648 0x1ee710 (nil)
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x1ee808, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33d6c0)
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\dudutzu\\Temp\\swtag.log" 1 -2147483644 0x1eefec 0x1eeff8 0x1ef1d8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\regid.1986-12.com.adobe" 1 -2147483644 0x1eefec 0x1eeff8 0x1ef1d8 (nil)
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),1,3,(nil),0,(nil)) - stub!
fixme:keyboard:RegisterHotKey (0x1006e,1634497586,0x00000001,32): stub
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:wia:wiadevmgr_QueryInterface interface {00000003-0000-0000-c000-000000000046} not implemented
fixme:wia:wiadevmgr_QueryInterface interface {00000003-0000-0000-c000-000000000046} not implemented
fixme:font:WineEngRemoveFontResourceEx (L"Z:\\home\\mosfet\\Downloads\\PhotoshopPortable\\App\\PhotoshopCS5\\Required\\\\ADMUI3.fon", 0, (nil)): stub
fixme:dwmapi:DwmIsCompositionEnabled 0x33ed6c
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x1006e 0x00000001
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x66a6224 0x66a6230 0x66a6118 (nil)
fixme:win:DisableProcessWindowsGhosting : stub
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:win:LockWindowUpdate (0x1006e), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:win:LockWindowUpdate (0x1006e), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:x11drv:X11DRV_SelectPen PS_USERSTYLE is not supported
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipDrawPath graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
fixme:gdiplus:GdipDrawString graphics object has no HDC
wine: Unhandled exception 0xc06d007e at address 0x68271422 (thread 0024), starting debugger...

```

THX for your help

---

### Post by cogadh on 2011-04-19
Did you use winetricks to install the gdiplus, ie6, msxml3, vcrun2005sp1 and vcrun2008 "packages" as well as apply the DLL overrides for odbc32 and odbcint? I believe all of those are still required to get PS to run, even in portable form.

---

### Post by Dudutzu on 2011-04-20
Ok, First THANKS for your help. 


After installing all the "packages" and applying the DLL overrides, the application still has a error

Here is the console output : 

```
dudutzu@Proteus:~/Desktop/PhotoshopPortable$ wine PhotoshopCS5Portable.exe
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
err:shell:HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:system:SetProcessDPIAware stub!
fixme:ntdll:NtSetInformationToken unimplemented class 24
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x1f28fc 0x1f2908 0x1f29d0 (nil)
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x1f31e0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33d6c0)
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\mosfet\\Temp\\swtag.log" 1 -2147483644 0x1f32bc 0x1f32c8 0x1f3480 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\regid.1986-12.com.adobe" 1 -2147483644 0x1f32bc 0x1f32c8 0x1f3480 (nil)
fixme:keyboard:RegisterHotKey (0x1006e,1634497586,0x00000001,32): stub
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:keyboard:UnregisterHotKey (0x1006e,1634497586): stub

```

---

