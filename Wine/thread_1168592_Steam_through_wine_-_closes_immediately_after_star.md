---
title: "Steam through wine - closes immediately after starting?"
date: 2009-05-24
forum: Wine
---

### Post by Neon_Knight on 2009-05-24
It just randomly started doing this.  I think it has something to do with the hardware survey, because when I start steam, it loads the main steam window, and the hardware survey window, but then it just closes instantly as soon as I do anything.  

I reinstalled steam, except now it doesn't load the hardware survey window, or fully load the steam window, it just loads the outline and closes.  Here is the wine output:

```

err:winedevice:ServiceMain driver L"SCDEmu" failed to load
CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
CellID: CSDS returned 173 servers.
CellID: Connecting to 69.28.151.182:27031. . .
CellID: Connect to 69.28.151.182:27031 took 205 MS
CellID: Nothing beat our old best time of 285 MS
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:shdocvw:ViewObject_SetAdvise (0x199e78)->(1 00000002 0x16307d0)
fixme:shdocvw:PersistStreamInit_InitNew (0x199e78)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x199e78)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x199e78)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x19a478)->(1 00000002 0x16309f8)
fixme:shdocvw:PersistStreamInit_InitNew (0x19a478)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x19a478)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x19a478)->(ffffffff)
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:win:RegisterDeviceNotificationA (hwnd=0x10088, filter=0x32e078,flags=0x00000004),
	returns a fake device notification handle!
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009c,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009a,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009c,0x00000000,0,2): stub!
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x199f14)->((null) 1 0x32a4ec (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->((null) 25 2 0x32a500 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->((null) 26 2 0x32a500 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000170
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x199f14)->(0x32a53c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32a600 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32a690)
fixme:urlmon:ObtainUserAgentString (0, 0x328e37, 0x328e30): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1c0a70, 0x328e30): stub
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x1be458)->(0x328e38 0x328e30 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->((null) 29 2 0x32d9f8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x199f14)
fixme:shdocvw:ClientSite_GetContainer (0x199f14)->(0x32d9ac)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x199f14)->(0xb7f576d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->((null) 25 2 0x32d8e0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->((null) 26 2 0x32d8e0 (nil))
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb

```

Any ideas?  Steam used to run brilliantly, it has a platinum rating on winehq, but it just doesn't seem to want to run for me anymore.

---

### Post by asdfoo on 2009-05-25
> **Neon_Knight said:**
> It just randomly started doing this.  I think it has something to do with the hardware survey, because when I start steam, it loads the main steam window, and the hardware survey window, but then it just closes instantly as soon as I do anything.  

I reinstalled steam, except now it doesn't load the hardware survey window, or fully load the steam window, it just loads the outline and closes.  Here is the wine output:

```

err:winedevice:ServiceMain driver L"SCDEmu" failed to load
CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
CellID: CSDS returned 173 servers.
CellID: Connecting to 69.28.151.182:27031. . .
CellID: Connect to 69.28.151.182:27031 took 205 MS
CellID: Nothing beat our old best time of 285 MS
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:shdocvw:ViewObject_SetAdvise (0x199e78)->(1 00000002 0x16307d0)
fixme:shdocvw:PersistStreamInit_InitNew (0x199e78)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x199e78)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x199e78)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x19a478)->(1 00000002 0x16309f8)
fixme:shdocvw:PersistStreamInit_InitNew (0x19a478)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x19a478)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x19a478)->(ffffffff)
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:win:RegisterDeviceNotificationA (hwnd=0x10088, filter=0x32e078,flags=0x00000004),
	returns a fake device notification handle!
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009c,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009a,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009c,0x00000000,0,2): stub!
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x199f14)->((null) 1 0x32a4ec (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->((null) 25 2 0x32a500 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->((null) 26 2 0x32a500 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000170
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x199f14)->(0x32a53c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32a600 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32a690)
fixme:urlmon:ObtainUserAgentString (0, 0x328e37, 0x328e30): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1c0a70, 0x328e30): stub
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x1be458)->(0x328e38 0x328e30 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->((null) 29 2 0x32d9f8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x199f14)
fixme:shdocvw:ClientSite_GetContainer (0x199f14)->(0x32d9ac)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x199f14)->(0xb7f576d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->((null) 25 2 0x32d8e0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x199f14)->((null) 26 2 0x32d8e0 (nil))
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb

```

Any ideas?  Steam used to run brilliantly, it has a platinum rating on winehq, but it just doesn't seem to want to run for me anymore.


err:winedevice:ServiceMain driver L"SCDEmu" failed to load

looks like you have something suspicious in your wine prefix, google scdemu and you'll see it's a device driver or something, probably a cdrom driver of some sort for copy protection or burning.

Either work out how to remove it or start from scratch with a new prefix, and reinstall steam there.

mv ~/.wine ~/.wine-broken

---

### Post by NightMKoder on 2009-05-25
That something suspicious seems like poweriso. May be the cause, but also you don't have gecko installed. I hear steam likes html, so do `wine iexplore` to set gecko up.

---

