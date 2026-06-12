---
title: "How to make OpenGL work?"
date: 2009-03-01
forum: Wine
---

### Post by dmdyne on 2009-03-01
I'm new to the whole Ubuntu world, I successfully got it up and running with Wine and I even got WoW working. Whenever I change my .wtf file to say "opengl" the game loads up with black boxes and horrid visuals. When I change the .wtf file to "d3d" it loads and runs fine....at 4 fps.

I know running this on my laptop (Acer Aspire 5610z) is pushing it. It just has the integrated Intel 950 video card but I should definatly be able to pull out more then 4 fps....

How do I get the OpenGL to work properly? What else can I do to increase my fps? I already did the regedit fix.

---

### Post by dmdyne on 2009-03-01
I've been reading about different kernels....low latency kernels and image generic kernels...my latency is insanely low in WoW, like 20ms when I usually have about 150ms. Would switching kernels help? If so, is this the correct one?

[http://packages.ubuntu.com/intrepid/linux-image-generic](http://packages.ubuntu.com/intrepid/linux-image-generic)

---

### Post by cogadh on 2009-03-01
Before you go messing with custom kernels, it might help to know some more info about your machine, like are you running any desktop effects? If so, disable them and switch back to Metacity as the window manager. Running Compiz/desktop effects will essentially break OpenGL as far as Wine is concerned, so it is best to just not use them, if you plan on doing any Wine gaming.

---

### Post by dmdyne on 2009-03-01
I don't use anything. I installed Ubuntu, then Wine and finally WoW.

---

### Post by cogadh on 2009-03-01
I believe that the basic desktop effects are enabled by default, but I could be wrong about that. You should verify that, just in case.

---

### Post by TheHolm on 2009-03-01
Have you installed binary drivers for your video card?

Some video cards have only basic 3d support in X.org.

---

