---
title: "how to run CS 1.6 (non-steam/steam)"
date: 2010-05-24
forum: Wine
---

### Post by ecchis on 2010-05-24
Hi guys, anyone can help how to launch counter-strike on ubuntu 10.04?  It always crashes on logging screen or after connection to server (when we must choose team).


tested ubuntu versions 10.04/9.10...
tested win xp/win98 modes...
tested run as -opengl (using opengl rendering) -wavonly (remove sounds) -d3d (using D3 rendering)...



some specified errors:

fixme:win:EnumDisplayDevicesW ((null),0,0x32f350,0x00000000), stub!
fixme:shdocvw:ViewObject_SetAdvise  (0x1c86f0)->(1 00000002 0xedf148)
fixme:shdocvw:PersistStreamInit_InitNew  (0x1c86f0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser  (0x1c86f0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget  (0x1c86f0)->(ffffffff)


err:d3d7:IDirect3DDeviceImpl_3_GetRenderState Unexpected texture stage  state setup, returning D3DTBLEND_MODULATE - likely erroneous
err:d3d7:IDirect3DDeviceImpl_3_GetRenderState  Unexpected texture stage state setup, returning D3DTBLEND_MODULATE -  likely erroneous
err:d3d7:IDirect3DDeviceImpl_3_GetRenderState  Unexpected texture stage state setup, returning D3DTBLEND_MODULATE -  likely erroneous
fixme:msg:handle_internal_message unknown internal  message ff000000


fixme:win:EnumDisplayDevicesW ((null),0,0x32f350,0x00000000), stub!
fixme:shdocvw:ViewObject_SetAdvise  (0x1c8760)->(1 00000002 0xedf14
fixme:shdocvwersistStreamInit_InitNew  (0x1c8760)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser  (0x1c8760)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget  (0x1c8760)->(ffffffff)


fixme:shdocvw:ViewObject_SetAdvise (0x69f7d50)->(1 00000002 0xd0731
fixme:shdocvwersistStreamInit_InitNew  (0x69f7d50)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser  (0x69f7d50)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget  (0x69f7d50)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate  (0x69f7d50)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x69f7d50)
fixme:shdocvw:OleObject_Close  (0x69f7d50)->(1)
fixme:urlmon:URLMoniker_BindToObject use running  object table
fixme:shdocvw:BindStatusCallback_OnProgress status code  11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:system:SetProcessDPIAware  stub!
fixme:dwmapiwmIsCompositionEnabled 0x32d9a0
fixme:iphlpapi:NotifyAddrChange  (Handle 0x9f2e8d8, overlapped 0x9f2e8e0): stub
0[6a01168]: IMM32:  InitKeyboardLayout, aKeyboardLayout=04090409, sCodePage=1252,  sIMEProperty=00090000
fixme:shdocvw:ClOleCommandTarget_QueryStatus  (0x1c880->((null) 1 0x32e0e0 (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus  command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec  Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec  Unimplemented cmdid 26
fixme:mshtmln_change_dlcontrol unsupported  dlcontrol 000000f0
fixme:shdocvw:ClOleCommandTarget_Exec  Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer  (0x1c880->(0x32e0a)
fixme:shdocvw:ClOleCommandTarget_Exec  Unimplemented group {000214d1-0000-0000-c000-000000000046}
File  c:\program files\cs\cstrike\demoheader.dmf was never closed



Please help me :) thanks. :P

---

### Post by cogadh on 2010-05-24
You can pretty much always ignore "fixme" errors, they are just developer notes on what they still need to work on in Wine. The only time they really matter is when the "fixme" specifies a function that your application requires and those are usually immediately followed by a relevant "err" message. In your case, the only "err" message you list points to a graphics card problem. What do you have for video hardware and do you have the restricted drivers for it installed?

---

### Post by ecchis on 2010-05-24
cpu: amd x4 620 3.0Ghz
VGA: hd4770 512MB Gddr5 bla bla bla..
RAM: 4 GB.


All drivers are installed. that err: errors appear only when I am trying run counter strike as d3d application ( - d3d command on console).

P.S. Lineage2 works better than on windows for me. only mouse pointer problem and dual box problem I didn't fixed :)

---

### Post by ecchis on 2010-05-26
so anyone can help?

---

### Post by techdude3177 on 2010-05-26
I just upgraded to the latest wine... installed winetricks... installed steam through there and the fonts.... steam runs fine.  I can launch CS but whenever I click on any of the options within CS xorg locks up.

Are you seeing the same thing?

---

### Post by asdfoo on 2010-05-29
if xorg locks up it most likely a bug in your video drivers, try updating them.

---

