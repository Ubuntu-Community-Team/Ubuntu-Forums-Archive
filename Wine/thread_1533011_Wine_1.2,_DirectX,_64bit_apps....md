---
title: "Wine 1.2, DirectX, 64bit apps..."
date: 2010-07-17
forum: Wine
---

### Post by yaji on 2010-07-17
So, Wine 1.2 is here. Fresh, new and shiny. And I am having some new problems :P After upgrade I lost support for OpenGL, every time I try to play some games I'm ending with:

```
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.

```

I already tried reinstalling Wine and the Graphic drivers (fglrx), I checked if Direct Rendering is working and it is:

```
yaji@yaji-desktop:~$ glxinfo | grep dir
direct rendering: Yes

```

Anyone have any idea what could be wrong ?

Oh and my next problem is about running the 64bit apps. Every time I try I'm getting this:

```
Trying to load PE image for unsupported architecture (AMD-64)

```

It should work, right ?

(I'm using Ubuntu 10.4 64bit and HD4850 [fglrx 10.6])

---

### Post by dino99 on 2010-07-17
i've not these issues but i use a 32 bits system

report on winehq/bugzilla

---

### Post by asdfoo on 2010-07-18
> **yaji said:**
> So, Wine 1.2 is here. Fresh, new and shiny. And I am having some new problems :P After upgrade I lost support for OpenGL, every time I try to play some games I'm ending with:

```
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.

```

I already tried reinstalling Wine and the Graphic drivers (fglrx), I checked if Direct Rendering is working and it is:

```
yaji@yaji-desktop:~$ glxinfo | grep dir
direct rendering: Yes

```

If you're on a 64bit system, then you're running a 64bit glxinfo.  Wine requires 32bit OpenGL drivers to be installed, which 64bit systems should normally do.  I know when I install nvidia drivers it asks if I want to install 32bit aswell.
> 

Anyone have any idea what could be wrong ?

Oh and my next problem is about running the 64bit apps. Every time I try I'm getting this:

```
Trying to load PE image for unsupported architecture (AMD-64)

```

It should work, right ?

(I'm using Ubuntu 10.4 64bit and HD4850 [fglrx 10.6])

Are you using Wine from a package or building from source?
If you use a package, is there also a 64bit package?  It might come in two pieces, I'm not sure.

---

### Post by yaji on 2010-07-18
> **asdfoo said:**
> If you're on a 64bit system, then you're running a 64bit glxinfo.  Wine requires 32bit OpenGL drivers to be installed, which 64bit systems should normally do.  I know when I install nvidia drivers it asks if I want to install 32bit aswell.

Everything was working fine until 1.2rc7. Then *BAM* no OpenGL for me. Even downgrading didn't helped.

> **asdfoo said:**
> Are you using Wine from a package or building from source?
If you use a package, is there also a 64bit package?  It might come in two pieces, I'm not sure.

I installed it form the package and there is no other packages than "wine" and "wine1.0" and "wine1.2".

---

### Post by VinisLentoje on 2010-07-22
I have the same issue with the OpenGL
Everything worked fine before, including in the RCs, but today when I tried running a 3D game (it was my first time running a 3D game on 1.2 stable), it gave me the same four lines as for the Gentleman who started this thread.
I tried running a couple of different 3D games and got the same error on all of those.

---

### Post by asdfoo on 2010-07-22
Not a Wine problem.  You guys need to have the correct 32bit video drivers installed for Wine to use.

---

### Post by VinisLentoje on 2010-07-23
> **asdfoo said:**
> Not a Wine problem.  You guys need to have the correct 32bit video drivers installed for Wine to use.

What would be considered as *correct* 32bit video drivers? 'Cause I do not have a clue what needs to be changed in order for the drivers to be "correct".

Also, could anyone explain, why did the same drivers that worked perfectly with wine a little more than a week ago, suddenly became "incorrect" after Wine got itself upgraded? I'm curious, since the answer might help me learn a little more about how stuff works, etc. So, please give as much detail as possible. Thank You!

---

### Post by brelkl on 2010-07-25
I had this problem, same specs as original poster (Ubuntu 10.4 64bit, fglrx 10.6). After upgrading to wine 1.2 (1.2rc7) all 3d in wine was broken. On a whim I re-istalled the catalyst drivers and everything works again. I don't know why--it's doesn't seem intuitive to me, but it seems to have worked.

---

### Post by darkshines87 on 2010-07-26
Brekl you saved my day :D reinstalling catalyst solved it.

---

### Post by VinisLentoje on 2010-08-25
Well, yes, this "fix" works and all, but having to reinstall the video card drivers with every new wine version is a major annoyance. ¬_¬

---

### Post by raucous1 on 2010-12-23
Perfect, this worked for me too!

I had downloaded the latest ATI fglrx/catalyst drivers from the ATI website and then tried installing steam, but was getting those errors:

> Direct3D9 is not available without OpenG

Reinstalling the driver worked for me though. I still have a long way to go, but good deal. Steam now will load without crashing (-dxlevel 81), at the very least.

---

