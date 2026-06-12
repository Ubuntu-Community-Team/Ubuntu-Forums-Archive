---
title: "server basic"
date: 2008-02-22
forum: Server Platforms
---

### Post by ttallos on 2008-02-22
Is there a way to load the server then do an apt-get and just load the desktop only without any software?

---

### Post by banewman on 2008-02-22
I'd install fluxbox or a similar lightweight desktop - but you could try just the core parts of the major ones e.g. gnome-core. kde-core - but I think they come with some apps.
:)

---

### Post by igknighted on 2008-02-22
The applications are part of what makes a DE a "Desktop Environment".  You can certainly install a plain window manager (Fluxbox, OpenBox, or my favorite, IceWM to name a few) and then put the apps you need on there (rox, web browser, etc.).  Xfce doesn't come with too many apps for a DE, that could be an option too (much easier to configure).

EDIT: This may sound nuts, but if you were going to run a GUI on a server and it has a graphics chip capable of compositing, you might want to try Xfce w/ composite on.  Any graphics work the CPU has to do will slow its server functions, but if you can offload it to the GPU you could save some cycles (in theory).  The last server I built had an ATI chip that composited with the xorg driver and actually helped speed up server functions.  Do not use compiz, while it also composites, it's resource hungry.  Xcompmgr, kwin4 or newer metacity releases are also capable of compositing, but I don't know if they are resource-efficient enough to help.

---

### Post by ttallos on 2008-02-22
Thanks....

---

