---
title: "Vega Strike"
date: 2007-04-07
forum: Ubuntu Gamers Arena
---

### Post by NiksaVel on 2007-04-07
Hey all,

does anyone have any experience with the game Vega Strike, available from the repos?

When I install it I have no sound, only music.

On the other hand, when I install it from a package from their homepage, I have sound, but it doesn't detect my joystick...


here's a thread where I already posted couple of logs:
[http://vegastrike.sourceforge.net/forums/viewtopic.php?p=80059](http://vegastrike.sourceforge.net/forums/viewtopic.php?p=80059)


thanks in advance if any1 can help...

---

### Post by compiledkernel on 2007-04-07
eh, A.I. wanna jump in here?

---

### Post by Perfect Storm on 2007-04-07
Well, it aren't the first to report that Vega Strike in the repo is broke, I'll see what I can do with a howto on the CVS (no promises).

---

### Post by NiksaVel on 2007-04-08
thank you for any assistance....   I really really like this game so far, but a) I need sound b) I need joystick too  :confused:


There are also other differences I've noticed from the repos version and the original package available from the Vega strike homepage...


this is a terminal log from the repos version:
> OpenGL::GL_EXT_compiled_vertex_array unsupported
OpenGL::Accurate Fog Distance unsupported
OpenGL::Generic Texture Compression unsupported
OpenGL::S3TC Texture Compression unsupported
OpenGL::Multitexture unsupported
OpenGL::TextureCubeMapExt unsupported
OpenGL::EXTColorTable unsupported
1 joysticks were found.

The names of the joysticks are:
    Microsoft Microsoft SideWinder Precision Pro (USB)
axes: 6 buttons: 9 hats: 0
FactionXML:LoadXML factions.xml



and here is the same part from the package available on this page:
> OpenGL::GL_EXT_compiled_vertex_array supported
OpenGL::Accurate Fog Distance supported
OpenGL::Generic Texture Compression supported
OpenGL::S3TC Texture Compression supported
OpenGL::Multitexture supported
OpenGL::TextureCubeMapExt supported
OpenGL::EXTColorTable unsupported
0 joysticks were found.

The names of the joysticks are:
FactionXML:LoadXML factions.xml


seems to be much more compatibility in the original package, but no joystick support...

---

### Post by Perfect Storm on 2007-04-08
It's properly because it have been compiled without joystick support.

---

### Post by NiksaVel on 2007-04-08
what should I do?  I would really like to play this game with joystick and sound :)

---

### Post by Perfect Storm on 2007-04-08
Go for the lastest development versions (heard alot have improved since the last stable release 2 years ago) I can't remember if they use subversion or CVS but you can check it on their site. While compiling make sure you have the libs that enable joystick.

---

### Post by v1nsai on 2009-03-16
When I tried to run vega strike, the screen would black out, a few errors similar to the OP's errors would show up in terminal, and I would lose the ability to use my mouse until I restarted gdm.  I ran 'vssetup' and turned down my graphics and disabled the joystick and fixed it.  Try that maybe?

---

