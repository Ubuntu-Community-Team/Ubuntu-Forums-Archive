---
title: "What's DRI and Mesa, and how do they relate to OpenGL?"
date: 2007-06-28
forum: The Cafe
---

### Post by Extreme Coder on 2007-06-28
I see these terms mentioned a lot, and they apparently have to do with graphics rendering of OpenGL, but I have _no_ idea what are they. And what's their relationship with open source drivers, and closed source ones?


Thanks!

---

### Post by jiminycricket on 2007-06-28
Quick, hopefully semi-accurate explanation: Mesa is the open source implementation of OpenGL.  They just got OpenGL 2.0 compatibility BTW.

DRI basically lets you communicate X11 drivers with the kernel and user apps.

The closed source drivers have their own OpenGL implementations and don't use Mesa AFAIK.

---

### Post by igknighted on 2007-06-28
> **Extreme Coder said:**
> I see these terms mentioned a lot, and they apparently have to do with graphics rendering of OpenGL, but I have _no_ idea what are they. And what's their relationship with open source drivers, and closed source ones?


Thanks!

DRI stands for "Direct Rendering Infrastructure" (see wikipedia here: [http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure](http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure)).  It explains it better than I can.  Mesa is basically the GNU/Linux implementation of openGL (see wikipedia here: [http://en.wikipedia.org/wiki/Mesa_3D](http://en.wikipedia.org/wiki/Mesa_3D)).  Basically mesa provides 3d for the open source (xorg) drivers, while (if done properly) ATI and NVIDIA replace the mesa 3d libraries with their own when using proprietary drivers.  All of these are (to my understanding) just different libraries to implement DRI.

---

### Post by maniacmusician on 2007-06-28
> **Extreme Coder said:**
> I see these terms mentioned a lot, and they apparently have to do with graphics rendering of OpenGL, but I have _no_ idea what are they. And what's their relationship with open source drivers, and closed source ones?


Thanks!
I don't know **that** much about them, but here's what I've gathered from observation:

DRI means "direct rendering"...also known as hardware rendering. This is when the present GPU/accompanying video card does all of the rendering of the graphics. This means that good, complete drivers need to have been written for the card. 

Mesa, I believe, is a form of **indirect rendering**. This means that the video card does not handle all of the rendering, and so it has to be done by the CPU, which is ill-suited to such tasks. This is why indirect rendering is so slow, and you can't succesfully run 3D graphics with it. 

There's really no relation with open or closed source drivers. What you probably mean is what the current state of drivers is. Right now, ATI's open source drivers provide DRI, but the closed source drivers are often unable to provide complete direct rendering. ATI's closed source drivers are, to say the least, awful. 

With nVidia, the opposite is true. The open source nVidia drivers are very basic, and cannot provide DRI in any way, shape, or form. The closed source nVidia drivers are very well made and provide complete direct rendering, which is what makes them so much more efficient on Linux.  There's also the fact that nVidia focuses on OpenGL performance on its cards, whereas ATI focuses on DirectX performance.

edit: oops, I guess I was wrong about mesa.

---

### Post by igknighted on 2007-06-28
> **maniacmusician said:**
> I don't know **that** much about them, but here's what I've gathered from observation:

DRI means "direct rendering"...also known as hardware rendering. This is when the present GPU/accompanying video card does all of the rendering of the graphics. This means that good, complete drivers need to have been written for the card. 

Mesa, I believe, is a form of **indirect rendering**. This means that the video card does not handle all of the rendering, and so it has to be done by the CPU, which is ill-suited to such tasks. This is why indirect rendering is so slow, and you can't succesfully run 3D graphics with it. 

There's really no relation with open or closed source drivers. What you probably mean is what the current state of drivers is. Right now, ATI's open source drivers provide DRI, but the closed source drivers are often unable to provide complete direct rendering. ATI's closed source drivers are, to say the least, awful. 

With nVidia, the opposite is true. The open source nVidia drivers are very basic, and cannot provide DRI in any way, shape, or form. The closed source nVidia drivers are very well made and provide complete direct rendering, which is what makes them so much more efficient on Linux.  There's also the fact that nVidia focuses on OpenGL performance on its cards, whereas ATI focuses on DirectX performance.

edit: oops, I guess I was wrong about mesa.

This is not quite true.  The reason "Mesa" doesn't give direct rendering with the fglrx drivers is because the drivers are not built to use mesa libraries.  Also if you are using the open source ATI drivers then they use the mesa libs and still get direct rendering.  It is the mismatch that causes the problems for ATI users.

EDIT: Sry... didn't see your edit before I wrote all that

---

### Post by Extreme Coder on 2007-06-28
Thanks everyone for the explanation!
I hope we see Mesa 7 ( the one with OpenGL 2) in an update soon.

---

