---
title: "Divx on Windows Guest?"
date: 2011-07-01
forum: Virtualisation
---

### Post by marshall1001 on 2011-07-01
I've recently set up a few Windows Guest machines using Virtualbox 4.0.6 on an Ubuntu 10.10 host system. I've installed Guest Additions with no problems and can achieve a good resolution with full-screen, seamless etc working no problem at all. However in my Windows 7 VM Aero won't work.

I don't need it to work really but for aesthetic purposes I really want to make it work for me. After a few quick searches I found that although I've given the guests both the 2D Video and 3D Acceleration of the Host, because Linux uses OpenGL and not Divx this won't allow me Aero or to run a few games that I'd like to run either.

As far as I can see there are two possible solutions

[LIST]
[*]Install/Emulate DivX on the Ubuntu host, and then pass this down to the guest system
[*]Install DivX onto the Guest system manually - possibly through using my Graphics Card driver disc.
[/LIST]

I was wondering if either or both of those things are possible. If I installed or emulated DivX on the host it would need to function as it does at the moment, not affecting Compiz or my nVidia Twinview. If I installed replacement drivers in virtualbox I would still like the ability to have Mouse Pointer Integration.

(I installed the Guest Additions in safemode to enable the 3D stuff to be installed)

EDIT: I just thought, is it possible to make the Windows 7 VM use OpenGl for rendering Aero at all? This would be a good Option 3

---

