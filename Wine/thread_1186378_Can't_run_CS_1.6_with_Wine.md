---
title: "Can't run CS 1.6 with Wine"
date: 2009-06-13
forum: Wine
---

### Post by stoned_again on 2009-06-13
Hi everyone..
So, it seems i have a problem here. I'm using Ubuntu Jaunty Jackalope and Wine 1.0.1 [SIZE="2"](i tried the latest version, but i couldn't install apps... i've got "unhandled exception" errors at the beginning of the installations) [/SIZE].

I've installed Adobe Photoshop CS2 and Pokerstars, and they're working fine.
Installed CS 1.6 too, but i get a bunch of errors when i run it...

```
wolvz@wolvz-laptop:~$ env WINEPREFIX="/home/wolvz/.wine" wine "C:\Program Files\Valve\hl.exe" -game cstrike
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5f0,0x00000000), stub!
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:shdocvw:ViewObject_SetAdvise (0x1721a8)->(1 00000002 0x666848)
fixme:shdocvw:PersistStreamInit_InitNew (0x1721a8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1721a8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1721a8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x6d124a0)->(1 00000002 0xf8b6c0)
fixme:shdocvw:PersistStreamInit_InitNew (0x6d124a0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x6d124a0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x6d124a0)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x6cf0028)->(1 00000002 0x10880b0)
fixme:shdocvw:PersistStreamInit_InitNew (0x6cf0028)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x6cf0028)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x6cf0028)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x6d124a0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x6d124a0)
fixme:shdocvw:OleObject_Close (0x6d124a0)->(1)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x172244)->((null) 1 0x32e8d8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->((null) 25 2 0x32e8ec (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->((null) 26 2 0x32e8ec (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 000000f0
fixme:shdocvw:ClientSite_GetContainer (0x172244)->(0x32e928)
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32e9fc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32ea8c)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->((null) 29 2 0x32f538 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x172244)
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32f480)
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32f480)
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->((null) 26 2 0x32f518 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->((null) 29 2 0x32f528 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->((null) 28 2 0x32f480 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x172244)->(0x32f3c4)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x172244)->(0xb7e94d31)
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->((null) 25 2 0x32f2f8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->((null) 26 2 0x32f2f8 (nil))
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x6cf0028)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x6cf0028)
fixme:shdocvw:OleObject_Close (0x6cf0028)->(1)
fixme:shdocvw:ViewObject_Draw (0x1721a8)->(1 -1 (nil) (nil) 0xae8 0xb04 0x32f9b0 (nil) (nil) 00000000)
fixme:shdocvw:ClOleCommandTarget_Exec (0x172244)->((null) 21 2 (nil) (nil))
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
File c:\program files\valve\cstrike\demoheader.dmf was never closed
```

I can get to the game menu and choose new game and a map, but the loading stops almost in the end, and i'm forced to quit, using ESC.
Sometimes, when i enter the game menu, only Options and Quit show up...

My video card is ATi Mobility Radeon HD3470.

Could you help me?

---

### Post by lightstream on 2009-06-13
you've tried to install the latest wine as described [on this page]("http://www.winehq.org/download/deb")? 

If there's a problem installing the latest Wine, recommend you fix that first as it is much improved over the one in the ubuntu repo.

Also check your settings on the Audio tab of winecfg

---

### Post by skyline. on 2010-01-09
Hi stoned,
[FONT=monospace]-1.Do you download cs or install it with original or classic . 
If you downlaod it from net that's probably a virus because errors say you fixme. Now i will say you how to fix it . 
1. Download this version of cs 1.6 ( here's link ( [http://thepiratebay.org/torrent/4480757/Counter_Strike_1.6_Full_%28With_Bots%29___Maps_%28By_IRAN_Torrents%29](http://thepiratebay.org/torrent/4480757/Counter_Strike_1.6_Full_%28With_Bots%29___Maps_%28By_IRAN_Torrents%29) ) sorry for the torrent link i use it ) 
2. Then install it
3. Try to run it.
4. If it don't work i think it's some virus for games.
If you install from original then is problem with windows.
If you install classic then is virus.
| You can't go to online servers with bad latency it will from some 50 sec say you | Sorry but your latency is too big or something |
SORRY FOR THE BAD ENGLISH.IM 9 YEAR OLD BUT IM NOW HOW COMPUTER WORKS
[/FONT]

---

