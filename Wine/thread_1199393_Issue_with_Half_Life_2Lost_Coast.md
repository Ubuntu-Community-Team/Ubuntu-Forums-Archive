---
title: "Issue with Half Life 2:Lost Coast"
date: 2009-06-28
forum: Wine
---

### Post by Blood//Stain//Child on 2009-06-28
It gets as far as the blurred 'loading' screen and then just cuts back to the desktop. I'm using Jaunty (32 Bit) with WINE 1.1.24 (pure WineHQ .DEB) on a 8800GT using the 185.18.14 driver.

Here's the terminal output;

```
yukatoshi@yukatoshi-desktop:~$ env WINEPREFIX="/home/yukatoshi/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 340
CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
CellID: CSDS returned 171 servers.
CellID: Connecting to 118.107.172.47:27031. . .
CellID: Connect to 118.107.172.47:27031 took 377 MS
CellID: Nothing beat our old best time of 124 MS
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x1a0770)->(1 00000002 0x19db790)
fixme:shdocvw:PersistStreamInit_InitNew (0x1a0770)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1a0770)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1a0770)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1a0d70)->(1 00000002 0x19db830)
fixme:shdocvw:PersistStreamInit_InitNew (0x1a0d70)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1a0d70)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1a0d70)->(ffffffff)
fixme:win:RegisterDeviceNotificationA (hwnd=0x10092, filter=0x32de60,flags=0x00000004),
    returns a fake device notification handle!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x32c1ac,0x00000000), stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x1bb458)->(1 00000002 0x19de3b8)
fixme:shdocvw:PersistStreamInit_InitNew (0x1bb458)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1bb458)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1bb458)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1bb458)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1bb458)
fixme:shdocvw:OleObject_Close (0x1bb458)->(1)
fixme:win:EnumDisplayDevicesW ((null),0,0x33e070,0x00000000), stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
err:ntdll:RtlpWaitForCriticalSection section 0xfd709c "?" wait timed out in thread 001d, blocked by 001e, retrying (60 sec)
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e2c8 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100bbf50) : pBox=0x33e31c stub
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x100cd438) : pBox=0x33e34c stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:avifile:AVIFileExit (): stub!
err:ole:RevokeDragDrop invalid hwnd 0x10040
err:ole:RevokeDragDrop invalid hwnd 0x10048
err:ole:RevokeDragDrop invalid hwnd 0x1004a
err:ole:RevokeDragDrop invalid hwnd 0x1004c
err:ole:RevokeDragDrop invalid hwnd 0x1004e
fixme:win:UnregisterDeviceNotification (handle=0xcafecafe), STUB!
err:ole:RevokeDragDrop invalid hwnd 0x10094
err:ole:RevokeDragDrop invalid hwnd 0x10096
err:ole:RevokeDragDrop invalid hwnd 0x10098
err:ole:RevokeDragDrop invalid hwnd 0x1009a
err:ole:RevokeDragDrop invalid hwnd 0x1009c
err:ole:RevokeDragDrop invalid hwnd 0x1009e
err:ole:RevokeDragDrop invalid hwnd 0x100a0
err:ole:RevokeDragDrop invalid hwnd 0x100a2
err:ole:RevokeDragDrop invalid hwnd 0x2003c
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1a0d70)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1a0d70)
fixme:shdocvw:OleObject_Close (0x1a0d70)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1a0770)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1a0770)
fixme:shdocvw:OleObject_Close (0x1a0770)->(1)
Shutting down. . .
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
yukatoshi@yukatoshi-desktop:~$ 

```

---

### Post by Blood//Stain//Child on 2009-06-28
Nevermind, I have solved the issue. It was a PulseAudio clash against OSS.

Please close this thread.

---

