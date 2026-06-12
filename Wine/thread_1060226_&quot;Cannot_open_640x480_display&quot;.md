---
title: "&quot;Cannot open 640x480 display&quot;"
date: 2009-02-04
forum: Wine
---

### Post by GNU Gnerd on 2009-02-04
Does anyone know how to fix this error?

```
cannot open 640x480 display: DirectDrawSurface::Release: Unknown
DirectDraw error: 0x1
[sdlout.c:229]
```

I tried asking this question last year, and got no responses; after some more research on my own, I still can't find anything that will help.  Any pointers in the right direction would be appreciated.

Thanks in advance.

---

### Post by gjoellee on 2009-02-04
This might be an DirectX error...which game/program is it?

---

### Post by GNU Gnerd on 2009-02-04
The game is Chip's Workshop, a level editor/level tester/game pack for the old Chip's Challenge game.  You can take a look [here](http://www.jsreed5.com/chipchallenge/chipw.exe) if that would help; basically, you can run it and make levels and such just fine, but when you try to test levels (and thus try to pop up a 640x480 window with the game in it) you get that error.

How would I go about fixing a DirectX error?

---

### Post by DOS4dinner on 2009-02-04
I get the same over here.
What is your graphics card? I have an ATI 9800, and it failed the same way. 

Here's the terminal output for ya:

fixme:win:EnumDisplayDevicesW ((null),0,0x243f16c,0x00000000), stub!
fixme:gl_compat:add_gl_compat_wrappers GL implementation supports GL_ARB_fragment_program but not GL_EXT_fog_coord
fixme:gl_compat:add_gl_compat_wrappers The fog coord emulation will most likely fail

Not sure if that helps though.

---

### Post by Ferrat on 2009-02-04
```
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
[COLOR="Red"]**fixme:win:EnumDisplayDevicesW ((null),0,0x243f1c4,0x00000000), stub!**[/COLOR]
fixme:d3d:IWineD3DDeviceImpl_Release (0x1524e0) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x157230 with type 1,WINED3DRTYPE_SURFACE

```

Got simillar output, my guess would be the fixme about the Device not being there, running a full debug now, see where it stops and what is says there

EDIT:
*doh* I'm blind, the error that popped up even said where the problem probably is

sdlout.c line 229

---

### Post by GNU Gnerd on 2009-02-05
> **DOS4dinner said:**
> I get the same over here.
What is your graphics card? I have an ATI 9800, and it failed the same way. 

I have a Nvidia Quadro 140M; the laptop's a Lenovo T61p, if that matters too.

> Here's the terminal output for ya:

fixme:win:EnumDisplayDevicesW ((null),0,0x243f16c,0x00000000), stub!
fixme:gl_compat:add_gl_compat_wrappers GL implementation supports GL_ARB_fragment_program but not GL_EXT_fog_coord
fixme:gl_compat:add_gl_compat_wrappers The fog coord emulation will most likely fail

Not sure if that helps though.

...kind of.  I'm not sure exactly what "fog coord emulation" would have to do with a relatively simple 2D display.  But at least we're getting closer to figuring out what's wrong.

[quote=Ferrat]Got simillar output, my guess would be the fixme about the Device not being there, running a full debug now, see where it stops and what is says there

EDIT:
*doh* I'm blind, the error that popped up even said where the problem probably is

sdlout.c line 229 [/quote]

So now the question is, what exactly would sdlout.c be?  Google doesn't seem to have any hints as to what it is, and even if it did it doesn't say what the problem is precisely.  Argh.  Well, let's just hope debugging turns up something useful.


Thanks to both of you for your help!

---

### Post by Dizzle7677 on 2009-02-05
It's just a funky old app it looks like.
::
Fog vs fragment shader: If we are using GL_ARB_fragment_program with the fog option, the glDisable(GL_FOG) here won't matter. However, if we have GL_ARB_fragment_program, it is pretty unlikely that we don't have GL_EXT_fog_coord. Besides, we probably have GL_ARB_vertex_program too, which would allow fog coord emulation in a fixed function vertex pipeline replacement.
::
"Chips Challenge is copyright 1992 the Microsoft Corp." A-HA!

---

### Post by GNU Gnerd on 2009-02-08
> **Dizzle7677 said:**
> It's just a funky old app it looks like.
::
Fog vs fragment shader: If we are using GL_ARB_fragment_program with the fog option, the glDisable(GL_FOG) here won't matter. However, if we have GL_ARB_fragment_program, it is pretty unlikely that we don't have GL_EXT_fog_coord. Besides, we probably have GL_ARB_vertex_program too, which would allow fog coord emulation in a fixed function vertex pipeline replacement.


So I'm guessing there's nothing I can do about it, then?

---

### Post by Dizzle7677 on 2009-02-09
> **GNU Gnerd said:**
> So I'm guessing there's nothing I can do about it, then?

It looks like one of those 1% apps that don't like some part of the Wine implemantation. You can always submit a ticket/search for a similar app bug/etc @ [bugs.winehq.org]("http://bugs.winehq.org/").

---

### Post by GNU Gnerd on 2009-02-09
> **Dizzle7677 said:**
> It looks like one of those 1% apps that don't like some part of the Wine implemantation. You can always submit a ticket/search for a similar app bug/etc @ [bugs.winehq.org]("http://bugs.winehq.org/").

Argh.  Well, searching for a similar bug hasn't turned up any results, but I suppose I could submit a bug for that.

Thanks for your help, everyone.

---

