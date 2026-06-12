---
title: "Mount and Blade crash - have output - help?"
date: 2010-08-02
forum: Wine
---

### Post by Zorgoth on 2010-08-02
I am using an ATI mobility radeon hd 5470 and have tried both Catalyst 10.6 and 10.7.  Most games work fine, but mount and blade crashes at regular intervals, usually when I am entering a new area.  The same thing will not always crash it generally.

Here is the output from one of the crashes:

```

fixme:d3d:color_convert_argb_to_fmt Add a COLORFILL conversion for format WINED3DFMT_D16_UNORM
fixme:d3d_texture:basetexture_generate_mipmaps iface 0xea2cb60 stub!
fixme:d3d_texture:basetexture_generate_mipmaps iface 0x3ffa3ed0 stub!
fixme:d3d_texture:basetexture_generate_mipmaps iface 0xe39beb8 stub!
fixme:d3d:color_convert_argb_to_fmt Add a COLORFILL conversion for format WINED3DFMT_D16_UNORM
fixme:d3d_texture:basetexture_generate_mipmaps iface 0xedc8560 stub!
fixme:d3d_texture:basetexture_generate_mipmaps iface 0xed2c5b8 stub!
fixme:d3d_texture:basetexture_generate_mipmaps iface 0xee90c50 stub!
fixme:d3d_texture:basetexture_generate_mipmaps iface 0xee64210 stub!
fixme:d3d_texture:basetexture_generate_mipmaps iface 0xee64480 stub!
fixme:d3d_texture:basetexture_generate_mipmaps iface 0xea2cb60 stub!
fixme:d3d_texture:basetexture_generate_mipmaps iface 0x3ffa3ed0 stub!
fixme:d3d_texture:basetexture_generate_mipmaps iface 0xe39beb8 stub!
fixme:d3d_texture:basetexture_generate_mipmaps iface 0xea2cb60 stub!
fixme:d3d_texture:basetexture_generate_mipmaps iface 0x3ffa3ed0 stub!
fixme:d3d_texture:basetexture_generate_mipmaps iface 0xe39beb8 stub!
wine: Unhandled exception 0xc0000417 at address 0x7e720023:0x0069cbd3 (thread 0034), starting debugger...
CellID: Connecting to 208.111.156.52:27031. . .
CellID: Connect to 208.111.156.52:27031 took 38 MS
CellID: Nothing beat our old best time of 47 MS
fixme:keyboard:X11DRV_ActivateKeyboardLayout 0x4090409, 0000: semi-stub!

```

Any ideas what could be causing this or how I could debug it better?

And when I do "glxinfo | grep direct,"

I get direct rendering, but I also get something saying

"GL_ARB_draw_indirect, GL_ARB_draw_instanced"

That have anything to do with it?

---

### Post by asdfoo on 2010-08-05
> **Zorgoth said:**
> I am using an ATI mobility radeon hd 5470 and have tried both Catalyst 10.6 and 10.7.  Most games work fine, but mount and blade crashes at regular intervals, usually when I am entering a new area.  The same thing will not always crash it generally.

Here is the output from one of the crashes:


Any ideas what could be causing this or how I could debug it better?

And when I do "glxinfo | grep direct,"

I get direct rendering, but I also get something saying

"GL_ARB_draw_indirect, GL_ARB_draw_instanced"

That have anything to do with it?


which `wine --version` are you using? try 1.3.0

---

