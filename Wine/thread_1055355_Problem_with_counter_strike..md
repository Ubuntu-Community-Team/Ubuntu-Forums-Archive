---
title: "Problem with counter strike."
date: 2009-01-30
forum: Wine
---

### Post by Mokou on 2009-01-30
Hi i am a new user of ubuntu linux,i use this operation system for almost 5 months . Today i tried to install counter strike 1.6 ,at first i did it but when i opened the game and put the map of my choice ,wine closed.When i run the game through terminal i see this:

env WINEPREFIX="/home/mokou/.wine"  wine "C:\Program Files\Counter-Strike 1.6\cstrike.exe"
fixme:ole:OleLoadPictureEx (0xa3e104,7790,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fae8), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x130d68)->(0x134a88, 0, (nil)), hacked stub.
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33f524,0x00000000), stub!
mokou@jinchuuriki:~$ fixme:shdocvw:ViewObject_SetAdvise (0x190470)->(1 00000002 0x11091c0)
fixme:shdocvw:PersistStreamInit_InitNew (0x190470)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x190470)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x190470)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1e3940)->(1 00000002 0xf1b1f8)
fixme:shdocvw:PersistStreamInit_InitNew (0x1e3940)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1e3940)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1e3940)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1e3940)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1e3940)
fixme:shdocvw:OleObject_Close (0x1e3940)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x190470)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x190470)
fixme:shdocvw:OleObject_Close (0x190470)->(1)


i dont know what to do,plz help me.Sorry about my english.

---

