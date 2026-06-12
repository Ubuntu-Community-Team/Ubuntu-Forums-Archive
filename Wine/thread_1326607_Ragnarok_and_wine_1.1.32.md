---
title: "Ragnarok and wine 1.1.32"
date: 2009-11-14
forum: Wine
---

### Post by Findarato on 2009-11-14
Hello everyone,

I have been trying for about 3h to get Ragnarok working on my machine, but I am getting the following errors :

```

fixme:shdocvw:PersistStreamInit_InitNew (0x154fa8)
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x154fa8)->(0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32e86c:3; TargetFrameName 0x32e85c:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:bind_to_object BindToObject failed: 80004005
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x154fa8)
fixme:shdocvw:OleObject_Close (0x154fa8)->(1)
joshua@Zeus:~/.wine/drive_c/Program Files/Gravity/RagnarokOnline$ fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1619c0,0x19a8d8): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1619c0,0x19a8d8): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2cc,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1680x1050x16 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1680x1050x32 @0! (XRandR)

```

and the program tells me it's a d3d error.

Does anyone know how to fix this ?

---

### Post by Findarato on 2009-11-14
The problem was that I am using dual-screens. I disabled one and the game launched correctly...

---

