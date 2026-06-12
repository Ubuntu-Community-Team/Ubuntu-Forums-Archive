---
title: "Virtualization and 3d accel"
date: 2007-06-26
forum: The Cafe
---

### Post by vexorian on 2007-06-26
I know for a fact vmware allows 3d support in Macs, When I tried it in Linux it didn't have the same "allow 3d acceleration" checkbox

I got to say, that otherwise it was running really well, I was "this close" to really stop booting windows and just use the virtual machine when I had to.

You see, I sometimes have to use windows, either to compile some program that is cross platform or what is worse, mod warcraft III.

I take it that modding warcraft III would be very easy if I had some little access to 3d accel in a virtual machine, even if it was slow, I would only need it to run the editor so I could test some stuff, warcraft III itself already works very well in WINE so that's not a problem if I can use the editor.

In WINE the editor simply fails, this is because blizzard has not allowed an open GL mode for it and also uses directx in a very weird way, direct3D surface is attached to a winapi window, and that is certainly not supported by WINE, then it also got some complex interface elements in some places that help it crash.

So, if there is a solution that would do something about virtualizing 3d acceleration, please point me out to it.

---

