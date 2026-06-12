---
title: "Request: Xmame, I know again"
date: 2005-06-08
forum: Ubuntu Backports
---

### Post by McQuaid on 2005-06-08
I posted this in the other forum where xmess was requested.  Just in case it was missed, I'll post it here:

Well, I always found it kind of inefficient but xmame usually has seperate builds for each type of way to access graphics modes. Besides X11, SDL is usually compiled. Unfortunately, the opengl is not done through sdl but X11 as well so thats no good, but I don't see why the SDL version of xmame would give you issue.

In the make file find DISPLAY_METHOD = x11 and change it to SDL. It's not ideal as we wouldn't get a opengl version but it would be great for now. Personally I've preferred the sdl version over x11 anyways.


I might be off course, but I think the SDL version should compile cleanly.  

Btw, I thought x.org gave 100% compatibility with XFree, are there any others apps that give issue with this?

---

### Post by McQuaid on 2005-06-15
Don't mean to bug, but I never got a response on this.  Am I incorrect in assuming the sdl version would avoid this xfree issue?

---

### Post by jdong on 2005-06-15
This completely changes the dependencies (runtime and buildtime) of xmame, not to mention its compatibility with the upcoming Breezy release.

If you can, get MOTU (#ubuntu-motu on FreeNode) to import Sid's Xmame into Universe by this method. I'll build with it from there.

---

### Post by McQuaid on 2005-06-15
Ok, I'll try that, but I thought the DISPLAY_METHOD would have to be changed for each  creation of each deb, as hoary does have xmame sdl albeit the .86 version.

Basically what i'm saying is there is already seperate packages:

xmame-x, xmame-svga, xmame-sdl

I was saying to just make the xmame-sdl pkg.

---

### Post by BoyOfDestiny on 2005-06-27
Uh... I had great luck compiling advmame .97 in my ubuntu hoary 5.04 (no backports or anything installed)

[http://advancemame.sourceforge.net/](http://advancemame.sourceforge.net/)
Also, alt+enter makes it full screen, as well as some other features. Also, I use advancemenu with it =) (although I'm sure it works with xmame as well) 

Not sure if this was unrelated to your request, but I suggest you give it a try. Plus you can use checkinstall to make a .deb if packagemanagement is an issue (yes I care too :) )

---

