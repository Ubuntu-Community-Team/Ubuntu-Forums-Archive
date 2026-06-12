---
title: "Blender 2.49a does not display properly. OpenGL problem?"
date: 2009-06-25
forum: Ubuntu Studio
---

### Post by Roinator on 2009-06-25
Ever since I got Ubuntu I have not been able to make OpenGL applications run properly.  This means a lot of games either display improperly, or not at all.  Similarly, blender, a program I have always been interested in using, has never displayed properly.  The issue, I am afraid, might be my graphics card (some integrated intel POS).  I hope this is not the case though.

Check out [this video]("http://files.getdropbox.com/u/1378350/blender.ogv") to see what glitches I am looking at.  I am running blender 2.49a with 9.04 on my cheap Compaq Presario C700.

---

### Post by lukeiamyourfather on 2009-06-25
I have an Intel GMA something rather in my notebook and there's no OpenGL support for it in Ubuntu 9.04. Was using Fedora before so I don't know if it worked in previous versions or not. If you want to use Blender or games or any 3D content for that matter get a discrete card in a desktop instead of integrated graphics in a laptop. A Radeon 4770 is a good bang for the buck these days when they get it working in the Linux driver. For a Radeon 4850 is another good option. If there's another driver available for the Intel GMA series that supports OpenGL I'd love to know too. Cheers!

---

### Post by Roinator on 2009-06-25
I understand discrete is better than integrated.  However, this being the cause of the problem does seem odd.  I always imagined integrated just being a bit slower than discrete, not completely incompattible.  Before I had ubuntu (running vista) I was able to play 3D games.

---

### Post by lukeiamyourfather on 2009-06-25
> **Roinator said:**
> I understand discrete is better than integrated.  However, this being the cause of the problem does seem odd.  I always imagined integrated just being a bit slower than discrete, not completely incompattible.  Before I had ubuntu (running vista) I was able to play 3D games.

Its not that the chipset is incapable of OpenGL but the drivers don't have it. I stumbled across this a few minutes ago after replying, it might be useful.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by Roinator on 2009-06-26
I saw that thread ealier in the week and disregarded it because it defines seems to depend on the jump from Intrepid to Jaunty.  I have been having my problem since Hardy.  It might help though. I'll give it a try tomorrow and update.

Thanks for the help :)

---

### Post by Roinator on 2009-06-26
Why can't I delete a post? (This was a double post) lol

---

### Post by waufrepi on 2009-07-10
If your running compiz that might be the problem.
wfpi

---

### Post by gus_the_mouse on 2009-07-14
I am experiencing what I assume the same problem, with Blender (openGL) on a laptop with an integrated Intel chip.  It does work fine in windows, but the strange thing is that it also works in Arch Linux, installed on the same computer.  On Arch the driver is just the generic vesa one. This seems to be the same one that Ubuntu has, "xserver-xorg-video-vesa."  Would this indicate that the driver is not the problem, but that it might be the desktop environment?

---

