---
title: "Left 4 Dead Randomly Crashes"
date: 2010-09-26
forum: Wine
---

### Post by Joseph Schwenker on 2010-09-26
Using Wine 1.3.3, I am able to run Left 4 Dead and Alien Swarm with fairly good FPS at lowest settings.  However, the first time I launch Left 4 Dead (and some other source games), the game crashes if I click any of the buttons.  The second time I run the game, the game will crash at the map.  The third time, the map will load and let me play, but may still randomly crash sometime during the gameplay.  It is more common for the audio to stop working than the game to crash after the third time.  I have found that opening the scoreboard will crash the game/audio sometimes.
After the third time, I ran the game from the terminal (which causes me to be disconnected because Steam cannot authenticate me), and got this output.  During the game, the audio crashed, and I ran snd_restart several times, after which voice chat no longer worked.  I then tried changing the settings, and was eventually kicked from a server as the game was applying the settings.  The game exited normally when I decided to quit.  Here's the output:

```
joseph@joseph:~/.wine/drive_c/Program Files/Steam/steamapps/common/left 4 dead$ wine left4dead.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32dfec,0x00000000), stub!
Unable to remove c:\program files\steam\steamapps\common\left 4 dead\left4dead\addonlist.txt!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d:debug_d3dformat Unrecognized 0x434f5441 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x434f5441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x41415353 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x41415353) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x4c4c554e (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x4c4c554e) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x434f5441 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x434f5441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x41415353 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x41415353) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x4c4c554e (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x4c4c554e) in the format lookup table
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x144b60, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x32e214)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1680x1050x32 @60! (XRandR)
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:debug_d3dformat Unrecognized 0x5a544e49 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a544e49) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a544e49 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a544e49) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a544e49 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a544e49) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a544e49 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a544e49) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a544e49 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a544e49) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a544e49 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a544e49) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a544e49 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a544e49) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a544e49 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a544e49) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x36314644 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x36314644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x4c4c554e (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x4c4c554e) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x4c4c554e (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x4c4c554e) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x4c4c554e (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x4c4c554e) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x4c4c554e (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x4c4c554e) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x4c4c554e (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x4c4c554e) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x4c4c554e (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x4c4c554e) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x4c4c554e (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x4c4c554e) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x4c4c554e (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x4c4c554e) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x31495441 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x31495441) in the format lookup table
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1c5448,0x1c53d0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1c5448,0x1c53d0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1c5448,0x1c53d0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1c5448,0x1c53d0): stub
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:thread:SetThreadIdealProcessor (0x210): stub
fixme:d3d:IWineD3DDeviceImpl_SetRenderTarget Surface 0x197078 doesn't have render target usage.
fixme:d3d:IWineD3DDeviceImpl_SetRenderTarget Surface 0x191148 doesn't have render target usage.
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:shdocvw:ViewObject_SetAdvise (0x140f7ef8)->(1 00000002 0x2d91460)
fixme:shdocvw:PersistStreamInit_InitNew (0x140f7ef8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x140f7ef8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x140f7ef8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x14117778)->(1 00000002 0x2d92ce0)
fixme:shdocvw:PersistStreamInit_InitNew (0x14117778)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x14117778)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x14117778)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x14117778)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x14117778)
fixme:shdocvw:OleObject_Close (0x14117778)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x14117838)->(1 00000002 0x2d92f68)
fixme:shdocvw:PersistStreamInit_InitNew (0x14117838)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x14117838)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x14117838)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1436a0e8)->(1 00000002 0x2d952c8)
fixme:shdocvw:PersistStreamInit_InitNew (0x1436a0e8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1436a0e8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1436a0e8)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x14117838)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x14117838)
fixme:shdocvw:OleObject_Close (0x14117838)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x14117850)->(1 00000002 0x2d95810)
fixme:shdocvw:PersistStreamInit_InitNew (0x14117850)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x14117850)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x14117850)->(ffffffff)
fixme:d3d:IWineD3DDeviceImpl_SetRenderTarget Surface 0x191148 doesn't have render target usage.
Unable to remove c:\program files\steam\steamapps\common\left 4 dead\left4dead\addonlist.txt!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1436a0e8)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1436a0e8)
fixme:shdocvw:OleObject_Close (0x1436a0e8)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x144219f0)->(1 00000002 0x277d758)
fixme:shdocvw:PersistStreamInit_InitNew (0x144219f0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x144219f0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x144219f0)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x14117850)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x14117850)
fixme:shdocvw:OleObject_Close (0x14117850)->(1)
fixme:shdocvw:ViewObject_SetAdvise (0x1437f760)->(1 00000002 0x277fbd8)
fixme:shdocvw:PersistStreamInit_InitNew (0x1437f760)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1437f760)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1437f760)->(ffffffff)
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1437fa18,0x13f0a610): stub
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
fixme:mixer:getsrccntfromchan No src found for 0 (L"Mic")?
fixme:d3d_surface:surface_load_location Unimplemented location SFLAG_INSRGBTEX for depth/stencil buffers.
err:d3d_surface:surface_modify_location Surface 0x191148 does not have any up to date location.
err:d3d_surface:surface_modify_location Surface 0x191148 does not have any up to date location.
fixme:d3d_surface:surface_load_location Downloading RGB surface 0x191870 to reload it as sRGB.
fixme:d3d_surface:surface_load_location Unimplemented location SFLAG_INSRGBTEX for depth/stencil buffers.
err:d3d_surface:surface_modify_location Surface 0x191148 does not have any up to date location.
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
fixme:mixer:getsrccntfromchan No src found for 0 (L"Mic")?
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141bb920) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x13ec2bb8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6da43370) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x140560a8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c2a3420) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x133b1c88) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d76e2d8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6cb97e98) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1436cbf8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x141988b8) : pBox=0x32e018 stub
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x130fcb58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x130fd4e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d26b0f0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d26ba78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3d6b90 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3ded18 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3e0ea0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3e1828 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d92fef8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d938080 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d93a208 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d93ab90 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d93b078 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d943200 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d945388 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d945d10 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1329e920 to reload it as RGB.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8420 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b83d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8690 Wrong thread, returning 1.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x142de048 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x142e01d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x142e0b58 to reload it as RGB.
fixme:d3d:state_zfunc D3DCMP_NOTEQUAL and D3DCMP_EQUAL do not work correctly yet.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13360338 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13364498 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x133655f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13365b58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13365de0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13365fa8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13366140 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x133662d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x143cbe78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x143cc7d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18bf1ad0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18bf3c58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18bf45e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da89e28 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da91fb0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da94138 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da94ac0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3e98d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3eba58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3ec3e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da435e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da4b770 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da4d8f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da4e280 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da67a60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da69be8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da6a570 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13123c48 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13125dd0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13126758 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13394cf8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13396e80 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13397808 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da2d2e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da35470 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da375f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da37f80 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c92de18 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c92e7a0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d394fd8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3a5160 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3a92e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3aa470 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3e68d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3e8a60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3e93e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da38468 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da405f0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da42778 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da43100 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da51760 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da598e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da5ba70 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da5c3f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da5c8e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da64a68 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da66bf0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da67578 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da6aa58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da6cbe0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da6d568 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d4078b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d409a40 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d40a3c8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18efa438 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13108b48 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x133ca0b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x133cc240 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x133ccbc8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14226540 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x142276c8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da6da50 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da75bd8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da77d60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da786e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cfa6000 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cfa6988 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da86e30 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da88fb8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da89940 to reload it as RGB.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003540 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003590 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa528 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa4d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca2c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8420 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdbf8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca1d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b83d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdba8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc48 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1456ca88 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1456cad8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003590 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003540 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa528 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa4d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1456cb78 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1456cbc8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc48 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdba8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdbf8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b83d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8420 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca2c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca1d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003310 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193676a8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc48 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdbf8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdba8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19351c38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x145a86f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003630 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190035e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca2c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa528 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa4d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003450 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190033b0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003360 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdd38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdce8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca368 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca318 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003770 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d90da70 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003720 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1346b758 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8690 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18a99760 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8420 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b83d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003310 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193676a8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc48 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdbf8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdba8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19351c38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x145a86f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003630 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190035e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca2c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003450 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190033b0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003360 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdd38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdce8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca368 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca318 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa528 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa4d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd6a8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd6f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1346b758 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d90da70 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003720 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003770 Wrong thread, returning 1.
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:ViewObject_Draw (0x1437f760)->(1 -1 (nil) (nil) 0x88c 0x2254 0x32e180 (nil) (nil) 00000000)
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x1ffce914, overlapped 0x1ffce918): stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1437f810)->((null) 1 0x32d3b4 (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 400087f0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:mshtml:nsURI_GetAsciiHost default action not implemented
fixme:mshtml:nsChannel_Open (0x57e80988)->(0x32c3ec)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x57e8b808)->()
fixme:shdocvw:ClientSite_GetContainer (0x1437f810)->(0x32d384)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x57e8b808)->(0x32c61c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x57e8b808)->(0x32c618)
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:mshtml:nsURI_GetHost default action not implemented
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x57ea7cc0)->()
fixme:mshtml:nsURI_GetHost default action not implemented
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1437f810)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x57e8b9d8)->(0x32d468 0x32d454 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x57aee678)->(0x32d468 0x32d454 0)
fixme:mshtml:nsChannel_SetResponseHeader (0x57e8b808)->("content-type" "text/html; charset=iso-8859-1" 1)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x1437f810)->(0x32dd34)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:mshtml:HTMLBodyElement_put_scroll (0x18e73468)->(L"no")
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 21
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x57ea7cc0)->(0x32ce30)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x57ea7cc0)->(0x32ce30)
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:mshtml:nsChannel_IsNoStoreResponse (0x57e8b808)->(0x32d81c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x57e8b808)->(0x32d818)
fixme:mshtml:HTMLBodyElement_put_scroll (0x18e73468)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x18e73468)->(L"no")
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x57ccf728,0x57ce7498): stub
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca318 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca368 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa4d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa528 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdd38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdce8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190033b0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003360 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003630 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190035e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003450 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc48 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19351c38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x145a86f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca2c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003540 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003590 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003720 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003770 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8690 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18a99760 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca368 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca318 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa528 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa4d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdd38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdce8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190033b0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003360 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003630 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190035e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003450 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc48 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19351c38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x145a86f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca2c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003590 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003540 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd6a8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd6f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdbf8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdba8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003310 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193676a8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdd38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdce8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190033b0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003360 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc48 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003770 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003720 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003630 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190035e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca368 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca318 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19351c38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x145a86f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa528 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa4d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d90da70 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1346b758 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca2c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003450 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd2a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8690 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdbf8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdba8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003310 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193676a8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdd38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdce8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190033b0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003360 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc48 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003770 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003720 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003630 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190035e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca368 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca318 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19351c38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x145a86f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa528 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa4d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d90da70 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1346b758 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca2c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003450 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd6a8 Wrong thread, returning 1.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d7513d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d755560 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d7566e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d9d1448 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d9d95d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d9db758 to reload it as RGB.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca1d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd798 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca1d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1456cad8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca1d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1456cb78 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca1d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1456cc68 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd140 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd2a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18a99760 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003770 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003720 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003450 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003630 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190035e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19351c38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x145a86f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd6f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd748 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003540 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003590 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003770 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003720 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003450 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003630 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190035e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19351c38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x145a86f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1456ca38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1456ca88 Wrong thread, returning 1.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d289db0 to reload it as RGB.
fixme:shdocvw:ViewObject_Draw (0x1437f760)->(1 -1 (nil) (nil) 0x88c 0x3734 0x32e180 (nil) (nil) 00000000)
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca1d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003540 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003590 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d073670 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b61f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd2a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca1d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003590 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003540 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b61f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d073670 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca368 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca318 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19351c38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x145a86f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b61f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d073670 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdbf8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdba8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc48 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdd38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdce8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003360 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190033b0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003450 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca1d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca2c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003770 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003720 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d8830f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6cb45a08 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003590 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003540 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3d1e90 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131d8e80 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57cd1288 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x142707a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8420 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b83d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d9ca380 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6cbd23b0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8690 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18a99760 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca368 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca318 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19351c38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x145a86f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190033b0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003360 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003450 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca1d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca2c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003770 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003720 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d8830f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6cb45a08 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003590 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003540 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3d1e90 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131d8e80 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57cd1288 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x142707a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8420 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b83d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d9ca380 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6cbd23b0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdd38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdbf8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b61f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdce8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc48 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdba8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d073670 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd6a8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd6f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca1d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdd38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdce8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8420 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b83d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003770 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003720 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003450 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57cd1288 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x142707a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca2c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd2a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8690 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca1d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdd38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdce8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8420 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b83d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003770 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003720 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003450 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57cd1288 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x142707a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca2c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd658 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131dd6a8 Wrong thread, returning 1.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131c6158 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131c6ae0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131c7468 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131c7df0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131c8778 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131c9100 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1aa060 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1ab1e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1ac370 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1ad4f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1ae680 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1af808 to reload it as RGB.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca228 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca1d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d9ca380 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6cbd23b0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193671d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57a2bdc0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003770 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003720 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b61f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d073670 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdc48 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57cd1288 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x142707a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190036d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003680 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b8420 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131b83d0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1456cb78 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1456cbc8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1456cc18 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdba8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdbf8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190034f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca2c8 Wrong thread, returning 1.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d40a8b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d40ea38 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d40fbc0 to reload it as RGB.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131d8e80 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3d1e90 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003450 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdce8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bdd38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x145a86f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19351c38 Wrong thread, returning 1.
fixme:d3d:IWineD3DDeviceImpl_SetRenderTarget Surface 0x191148 doesn't have render target usage.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca318 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130ca368 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367608 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19367658 Wrong thread, returning 1.
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf880) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0738) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x58dbf830) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6c3a0700) : pBox=0x32e018 stub
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6cb45a08 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d8830f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003540 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003590 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193676a8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003310 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003360 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190033b0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x190035e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19003630 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa4d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18afa528 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1346b758 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d90da70 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3ba758 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d3bd928 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131a8548 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x14517ad8 Wrong thread, returning 1.
fixme:d3d:IWineD3DDeviceImpl_SetRenderTarget Surface 0x143c09d0 doesn't have render target usage.
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6ccef998) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5792ec18) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9cc0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194b9ed0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba0e0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba2f0) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x194ba500) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18a47738) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14528c58) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18c11300) : pBox=0x32e204 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
err:d3d_surface:surface_modify_location Surface 0x143c09d0 does not have any up to date location.
fixme:d3d:IWineD3DDeviceImpl_SetRenderTarget Surface 0x143c09d0 doesn't have render target usage.
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a17e90) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57a4a920) : pBox=0x32e018 stub
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
fixme:mixer:getsrccntfromchan No src found for 0 (L"Mic")?
fixme:d3d_surface:surface_load_location Unimplemented location SFLAG_INSRGBTEX for depth/stencil buffers.
err:d3d_surface:surface_modify_location Surface 0x143c09d0 does not have any up to date location.
err:d3d_surface:surface_modify_location Surface 0x143c09d0 does not have any up to date location.
fixme:d3d_surface:surface_load_location Downloading RGB surface 0x6c287750 to reload it as sRGB.
fixme:d3d_surface:surface_load_location Unimplemented location SFLAG_INSRGBTEX for depth/stencil buffers.
err:d3d_surface:surface_modify_location Surface 0x143c09d0 does not have any up to date location.
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
fixme:mixer:getsrccntfromchan No src found for 0 (L"Mic")?
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x14707db8) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6d3b4108) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x57fa0dc0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b9c7918) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5b8b23d0) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32dbc0 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de54 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x19729628) : pBox=0x32de5c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32dd7c stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x6dc8bf80) : pBox=0x32e018 stub
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b9f4d48 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a29be98 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a298ea0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b3cbf88 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b3a0c78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1456bd58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c5ccfb0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c5cd0f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ca1d988 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ca2dae8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x141ad3a0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x141ae500 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b7dac90 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b7dadd8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b7daf20 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d0b7098 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c809670 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d0b71e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d0b6160 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b9dde70 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b941068 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b5936c8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b8ea360 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a22d450 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x143fa998 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b231f88 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5acf04b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5acf0db0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5acf1fe0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5acf11b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5acf1300 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5acf1700 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5acb2698 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5acb27e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ac9b6e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ac9b830 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18da7f00 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c43c328 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c43c470 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c43c5b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19187ae8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58114d48 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x597f15e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da84f58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5cadbce0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a8fed78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58100510 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b22f288 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b22f3d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dbb5458 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b1f89b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b1f8b00 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59f83370 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59f834b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b18cce0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b18ce28 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x145a0568 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x145a0ea0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14564488 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x145645d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5baf9110 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5baf9258 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bd3ba08 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bd43b68 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bd45cc8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bd46628 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dd07358 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cfb7b88 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cfb7cd0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cfb7e18 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13440908 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19188420 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19188568 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x191886b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59f40040 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59f40188 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59f402d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59f40418 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bee3a40 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bee3b88 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59359da0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1339af50 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a899058 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a0ebee8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a8991a0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5be935f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5be93740 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131c8100 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131c8248 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131c8390 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131c84d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d0b7328 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19792990 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19792ad8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19792c20 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19773d78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19773ec0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x589e4fc8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x589e5110 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x589e5258 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14586128 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b7dbc80 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b7ddde0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b7ddf28 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6df5dd18 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6df5de60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6df5dfa8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x589e2988 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x589e2ad0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x589e2c18 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58e16a50 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58e16b98 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b956b58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b956ca0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b956de8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c9c8bd0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c9c8a08 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c9c8780 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c9c7c30 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c9c81b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x197051d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19705340 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x197054d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19705670 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58fa1fb0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58fa20f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58fa2240 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bc50178 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bc502c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b39dc38 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b39dd80 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b39dec8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b39e010 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ba6b2b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ba6b3f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a1ac7b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a1ac900 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c120920 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c120a68 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59f81ff8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59f82140 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59f82288 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b64b030 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59f82be8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57a4a7f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b7db8f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b232a98 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c868750 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b1f94a0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b9921f0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57f8e9f0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57f90b78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57f90ce8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6ccb9d48 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13f956b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13f95820 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57fd33d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18a845f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18a84740 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58088010 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5807cd20 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5807d680 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ad838c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ad83a08 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x146b5390 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x146b54d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x146b5620 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5add8c38 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ae04d38 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ae04e80 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ae04fc8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x146b5768 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x146b58b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x146b59f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x146b5b40 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b0986c8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b098810 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14434670 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x144347b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14434900 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b0eda40 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b119a10 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b119b58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b119ca0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b119de8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14434a48 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14434b90 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b1a2000 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5af0f290 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5af0f3d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5af0f520 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c81fd10 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c81fe58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c81ffa0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c8200e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5af90708 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5af90850 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5af90998 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5af90ae0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bf97630 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5afe5d28 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5beaaee8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a4a0410 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a4c0570 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a4c86d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a4ca830 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a4ca978 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a0ed1b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a0f5310 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a0f7470 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a0f75b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a243358 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a2434a0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59fae680 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59fae7c8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d055a78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bb0ec90 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bb0edd8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c867c68 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3b6048 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d3b6190 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14664998 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14664ae0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14664c28 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57fd54d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57fd5620 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59c80218 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x144c7530 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x130485b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57f352c8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13048930 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1445a718 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1445a860 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18a80bb0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18a80cf8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6df1d8d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6df1da20 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d6b8110 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b759fc8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b982808 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a0ece28 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b9e95a0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b7b05e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18d83208 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18d83350 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18d83498 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18d835e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18d83728 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57e5cb20 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57e5dc80 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x578aec08 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57e49990 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x578ad398 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x578ae4f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x578abb28 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x578acc88 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x578aed50 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x578af2f0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58005400 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58005548 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58005690 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x580057d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18d83db8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14500410 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6ca27a30 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6ca29b90 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14500d70 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1927c0e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d7d5f30 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d7d6078 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1927bb10 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1927bc58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13283290 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18e67b30 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a244768 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5be29a08 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x197ecf98 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x197ef0f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x197efa58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x195da478 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x195da5c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cf8e2c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cf92420 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cf93580 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59d6fd38 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59d6fe80 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59c203e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59d80008 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59d80178 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59d802e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ab2ed58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ab2eea0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ab2efe8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dccf860 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dccf9a8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ab84200 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5abd42e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5abd4428 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5abd4570 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dccfaf0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dccfc38 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dccfd80 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ac297d0 to reload it as RGB.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x57ccf728,0x6c967a18): stub
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c5c3758 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c5c3d08 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c5c3e50 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57f44328 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c5c3f98 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c6324b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14504eb8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58fb7d98 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57f9bea0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b620c60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a17d9d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14117430 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c468d18 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18a74858 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a9cea20 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b7852d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b6ad388 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a044e98 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a050018 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b72ecb8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bcb2858 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57ea7278 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57ea73c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14398db0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18aa8418 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18aa8560 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a29c220 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d043ae8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d043c30 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5beab2a8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5beab3f0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58ed06b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57ea6850 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cda8198 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cda82e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cda8428 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a7882e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58005d98 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58005ee0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c18dcd8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x580066c8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58006810 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x580059c8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57cc89a8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57cc8af0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57cc8c38 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14563b70 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a9dfbd8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da9fa60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6da9fba8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c135d30 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c135e78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c135fc0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a6c1cd8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a6e1e38 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a6e9f98 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a6ec0f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c239cf8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a9e7f58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6ce61f30 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a96acf8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b4ae5e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a7f6b00 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57cc9988 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57cc9ad0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14398458 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x143985a0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d095090 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d0951d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a98e730 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a98e878 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c40c400 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c40c548 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c40c690 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c2443d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b72ce60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bc9c790 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bca4918 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bca6aa0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bca6c10 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b3fdd18 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b3fde60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5cabbbf0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5cabbd38 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14589018 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b6d7c00 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5807a6a8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5807a7f0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d8ba008 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d8ba150 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dc5f820 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d816b28 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d816c70 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d816db8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c5cb730 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13ff48f0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5becd0c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5becda20 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a0ec270 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a0ec3b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b702dc8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a277a70 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a277bb8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b702f10 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dccf550 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dccf698 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18eaf518 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18eaf660 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18eaf7a8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ac29918 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ac29a60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ac29ba8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ab84348 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ba4d958 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58ac82b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18a741c8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b9159f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bfb2930 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bfb2a78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ab845c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x189d5798 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x189d58e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x189d5a28 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5804faf8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x132040d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13204220 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a150c30 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a150d78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a150ec0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a151008 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a5726b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x579841f0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57984338 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cdabaa0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18a74ee8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18a75030 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b5c9b58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b5c9ca0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x142a4a10 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x142a4b58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14672518 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57f47a38 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57fa0718 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57fa0860 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x581b8cd8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x581b8e20 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1453bd48 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1453ca80 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1453cbc8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1454c618 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cab4bc8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x581d8cd8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cab5d28 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b9dda58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b9ddba0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b9ddce8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x193c2470 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x193c25b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a96aa10 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a96ab58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5aa80d08 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13229780 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5810a590 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5810aef0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a71ddb8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a71df00 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dc9be78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dc9bfc0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bc50570 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bc506b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b273928 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bd8f830 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bd846b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b18c958 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131f1958 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a24d5a8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18a85738 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18a85880 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18a859c8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18a85b10 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ac49360 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ac514c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ac53620 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ac53768 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19792150 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d07c470 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d07c5b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x197f9830 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x197f9978 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c5cc1c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bc71458 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bc795b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bc7b718 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c5ccb20 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x130474f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13047640 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c3986a0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c3987e8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c398930 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58006fb8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57ff6ed8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58010d58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5804ff60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c406680 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c3edae0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131cf620 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131cf768 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131cf8b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131cf9f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x131cfb40 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d0b6f50 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5d54d540 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57f9f658 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57f9f7a0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b5ed270 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b6d5f78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b5ef3f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b5efd80 to reload it as RGB.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x57ccf728,0x6c967a18): stub
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d00df50 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d00e098 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13082788 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x130828d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dcbbab0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dc94490 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dc965f0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c60bc20 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dc972b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d00b0b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d00d218 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dc97c10 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b981d58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b981ea0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b590818 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b590960 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58099060 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x580985b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58098700 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d9821a8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a89c470 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a89c5b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5acf2d88 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c9ade90 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b88dd38 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b891e98 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b892ff8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a87cd50 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a87ce98 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a87cfe0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a871cb8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5acf1b40 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a8a99f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a7e1488 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dfba2b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c2db8e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c2dba28 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c8e9cf8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c8e9e40 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c9c6760 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bee3df8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bee3f40 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bee4088 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bee41d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5be93240 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5be93388 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5913da30 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5913db78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d001720 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d001868 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dd8f940 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dd8fa88 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bc7b9f0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b224920 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bc7c3c8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bc510b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c8678e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b53d0a8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b223e60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b223fa8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bbca740 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bbce8a0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bbcfa00 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c403dc0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58ac9260 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d05dc58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18a75590 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b5ca640 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c83c5d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5beabfc8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d92e050 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a8de178 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a73e850 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b4d98f0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b2f4948 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b429b70 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b31fc58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5d919bf8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x581c90a8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x581c91f0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1443a500 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d02e4b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d02e600 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5beabcd8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57f377c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18ae8d28 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57f83bd0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5be29b58 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d03ce40 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a772788 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a7728d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a772a18 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a242ab0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a242bf8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bac7168 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bac72b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bac73f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b5f2550 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ca5a758 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ca5c8e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ca5d268 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b8a45b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b8a6718 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b8a7078 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b9566b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b9567f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bd4d520 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x581c4910 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x581c7660 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x581c77a8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5804fc40 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a788428 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58fb33e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57d96748 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x1459f738 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c632770 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x197157f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19715940 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19715a88 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58082f78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x197433f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c3a41c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x142a8510 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dc8b990 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dc8bad8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18b674d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x581ab998 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x581ac2f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b83ceb0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c26aa60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bac6e20 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a5f6618 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a606778 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a60a8d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a60ba38 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13084038 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13084180 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a6f6c88 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13084ae0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a6f6fe8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a6ffdf0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a701f50 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a702098 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59d6ee08 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c20f290 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6de640b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c8cf1c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57fd46c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57fd3730 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b5efec8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bb78288 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18e86ed8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58e6c678 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59045ec0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x59617220 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b8bf050 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c8ea080 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b22faa0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19716428 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a6a7de0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a64c680 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x587ba8f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b9f43c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x587bb258 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bac7540 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58fb0468 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c2a2328 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5aa9df78 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5aa9e0c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5aa92968 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x587bc1c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x145965e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x14596f40 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58fad860 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58faf9c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58fb0320 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58fb07b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58fb2910 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58fb3298 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b725820 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b7279a8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b728330 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a7023b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a702500 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a702648 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d8b1158 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0xaebe4d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d686f60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c8bed70 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c893a60 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b682078 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b915670 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b64bf70 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b1f8630 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58006578 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58005c10 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5aa29788 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ce69428 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x196faad0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x196fac18 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x193b8c80 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x193b8dc8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x13ef3cb8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x598c8218 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5d8cea38 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c89f6e0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c89f828 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x19788818 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x18bee150 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ef02dc8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d439ff8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6d6861b0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b5683b8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5c8395d8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b3fe860 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5ca914c0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b5f4f50 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5cabc7d0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b4757f8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b6d8698 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b98d988 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5b5f5950 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bd593a0 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5bd4e220 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6cbcd148 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x5a3f3460 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6c437fd8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6ce31360 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x58143d90 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57e5e550 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x57e5e698 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dcbaca8 to reload it as RGB.
fixme:d3d_surface:surface_load_location Downloading sRGB surface 0x6dcbadf0 to reload it as RGB.
fixme:d3d:IWineD3DDeviceImpl_SetRenderTarget Surface 0x143c09d0 doesn't have render target usage.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13209bd0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6c967e10 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d1675f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18db8840 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x5b2f4818 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18d52088 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x5a04f7a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x14455da0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6ca39098 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57ccfc68 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x5b2f47c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x5eb0a6f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19062a30 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x192f4598 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57de9458 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19ba80 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57ddcd98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6ca8e5a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6c8bc390 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x5c71cec8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1346fce0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57cd1638 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57cd2080 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13f021f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x131ef1c8 Wrong thread, returning 1.
fixme:d3d_surface:surface_load_location Downloading RGB surface 0x131d2d78 to reload it as sRGB.
fixme:d3d_surface:surface_load_location Downloading RGB surface 0x133dd2d8 to reload it as sRGB.
fixme:d3d_surface:surface_load_location Downloading RGB surface 0x6d3d14b8 to reload it as sRGB.
fixme:d3d_surface:surface_load_location Downloading RGB surface 0x6d3d1600 to reload it as sRGB.
fixme:d3d_surface:surface_load_location Downloading RGB surface 0x6d90f188 to reload it as sRGB.
fixme:d3d_surface:surface_load_location Downloading RGB surface 0x5bae1cb8 to reload it as sRGB.
fixme:d3d_surface:surface_load_location Downloading RGB surface 0x5bae1e00 to reload it as sRGB.
fixme:d3d_surface:surface_load_location Downloading RGB surface 0x5afa7030 to reload it as sRGB.
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x580f07a8) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13f48468 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13f48e20 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1456d580 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0xae9b468 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18ec6288 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57f58518 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13ee8c00 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6c725318 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d7336e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d2f2418 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57cd0c08 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57cd0d00 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6df46ef0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18a85410 Wrong thread, returning 1.
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5de0bf18) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dd68 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32dffc stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x5971aa08) : pBox=0x32e010 stub
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6df4dd98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13e95f78 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13eeb040 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1961f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6cfdc260 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130f1728 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13f40e48 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x146c5a18 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13f48468 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13f48e20 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x5c71cec8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57ddcd98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57cd0c08 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57cd0d00 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57cd1638 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6c8bc390 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d7336e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d2f2418 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19ba80 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57de9458 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13ee8c00 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6c725318 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13eeb040 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1961f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6df4dd98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13e95f78 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6cfdc260 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x130f1728 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1346fce0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6ca8e5a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6df46ef0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18a85410 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x192f4598 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19062a30 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6c967e10 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13209bd0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18ec6288 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x57f58518 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x13f40e48 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x146c5a18 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x58089250 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1333fa88 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18db8840 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x6d1675f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x5a04f7a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x14455da0 Wrong thread, returning 1.
Unable to remove c:\program files\steam\steamapps\common\left 4 dead\left4dead\textwindow_temp.html!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x140f7ef8)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x140f7ef8)
fixme:shdocvw:OleObject_Close (0x140f7ef8)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x144219f0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x144219f0)
fixme:shdocvw:OleObject_Close (0x144219f0)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1437f760)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1437f760)
fixme:shdocvw:OleObject_Close (0x1437f760)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x6d9c95c8)->((nil))
fixme:avifile:AVIFileExit (): stub!
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x191430 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x191480 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1914d0 Wrong thread, returning 1.
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x875b609
joseph@joseph:~/.wine/drive_c/Program Files/Steam/steamapps/common/left 4 dead$ 


```

I believe that the audio crashes may be related to Wine's lack of support for PulseAudio.

---

### Post by beastrace91 on 2010-09-27
> **Joseph Schwenker said:**
> 
I believe that the audio crashes may be related to Wine's lack of support for PulseAudio.

If this really is the case then just install a version of Wine that contains pulse audio support by following the directions [here]("http://www.webupd8.org/2010/05/install-wine-with-built-in-pulseaudio.html").

~Jeff

---

### Post by Joseph Schwenker on 2010-09-27
> **beastrace91 said:**
> If this really is the case then just install a version of Wine that contains pulse audio support by following the directions [here]("http://www.webupd8.org/2010/05/install-wine-with-built-in-pulseaudio.html").

~Jeff

I tried Winepulse before, but the maintainer did not update the PPA to the latest stable Wine.  I am currently using the development version of Wine, and want the PPA to use the latest development version.  Does this PPA do so?

---

