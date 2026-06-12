---
title: "VirtualBox mouse bug."
date: 2009-10-05
forum: Virtualisation
---

### Post by artheus on 2009-10-05
Hi!

I'm using a Ubuntu 9.04 set-up with multiple screens, using Nvidia Xinerama.

And in one of these screens I'm using a fullscreen windows xp machine (VirtualBox). When I use the capture mouse function, and in Windows move the mouse fast to the left it will freeze, exactly as it does if I hit the most-left point of the screen, but it freezes in the middle of the screen. Or the exakt freeze-point depends on the speed I use to move the mouse.

If I instead make the XP virtual machine capture the mouse as an USB Device, it works great!

Is this a known bug?

I guess it might have something to do with Xinerama, as Xinerama uses different cursors for different screens, and the cursor freezes at mouse-out-of-x-screen.

Cheers,
Artheus

---

### Post by artheus on 2009-10-07
Well.. changed from Xinerama and Separate X Screens, to TwinView.. And now it seems to work properly..

But I'm still curious to why this problem accured in Xinerama?

Artheus

---

