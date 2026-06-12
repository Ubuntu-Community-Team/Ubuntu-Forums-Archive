---
title: "Request: XMESS"
date: 2005-06-03
forum: Ubuntu Backports
---

### Post by mattblack_uk on 2005-06-03
The package in Multiverse for XMESS is only at 0.86 whereas several versions have been released since then. It is now on 0.96.

---

### Post by Amaranth on 2005-06-03
[QUOTE=mattblack_uk]The package in Multiverse for XMESS is only at 0.86 whereas several versions have been released since then. It is now on 0.96.[/QUOTE]
 Someone needs to get the MOTU to update xmess in breezy before it can be backported.

---

### Post by jdong on 2005-06-03
This is in Sid; I'll go into #ubuntu-motu right now and see what I can do...

---

### Post by jdong on 2005-06-03
LOL, it's already in Multiverse :)

Boy I feel dumb. I'm backporting right now.


BTW, last time I had some really bad luck with the xmame package, so I don't know how successful this will be :(

---

### Post by McQuaid on 2005-06-03
Ya,  I was waiting on a more recent version of xmame.  I hope you won't run into the same issues this time.

---

### Post by jdong on 2005-06-03
```

(first use in this function)
src/unix/video-drivers/xf86_dga1.c:44: error: (Each undeclared identifier is reported only once
src/unix/video-drivers/xf86_dga1.c:44: error: for each function it appears in.)
src/unix/video-drivers/xf86_dga1.c:53: warning: implicit declaration of function `XF86DGAGetVideo'
src/unix/video-drivers/xf86_dga1.c: In function `xf86_dga1_set_mode':
src/unix/video-drivers/xf86_dga1.c:333: warning: implicit declaration of function `XF86DGAForkApp'
src/unix/video-drivers/xf86_dga1.c:341: warning: implicit declaration of function `XF86DGADirectVideo'
src/unix/video-drivers/xf86_dga1.c:342: error: `XF86DGADirectGraphics' undeclared (first use in this function)
src/unix/video-drivers/xf86_dga1.c:342: error: `XF86DGADirectMouse' undeclared (first use in this function)
src/unix/video-drivers/xf86_dga1.c:342: error: `XF86DGADirectKeyb' undeclared (first use in this function)
src/unix/video-drivers/xf86_dga1.c:348: warning: implicit declaration of function `XF86DGASetViewPort'
make[1]: *** [xmame.obj/unix.x11/video-drivers/xf86_dga1.o] Error 1
make[1]: Leaving directory `/home/jdong/ubp-compile-temp/xmame-0.96'
make: *** [build] Error 2
Build FAILED... 512
Do you want to rebuild w/o dep checks, or get a shell? [Y/s/n] ?

```

Bad news :(


Seems like xmess is designed for Xfree86, while Hoary uses Xorg. That also explains why it hasn't been imported into Hoary yet.


Perhaps I'll try repatching later with Ubuntu patches...

---

### Post by McQuaid on 2005-06-04
Well, I always found it kind of inefficient but xmame usually has seperate builds for each type of way to access graphics modes.  Besides X11, SDL is usually compiled.  Unfortunately, the opengl is not done through sdl but X11 as well so thats no good, but I don't see why the SDL version of xmame would give you issue.

In the make file find DISPLAY_METHOD = x11 and change it to SDL.  It's not ideal as we wouldn't get a opengl version but it would be great for now.  Personally I've preferred the sdl version over x11 anyways.

---

