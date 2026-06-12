---
title: "Mouse problem with XIII [game]"
date: 2009-02-10
forum: Wine
---

### Post by tehforum on 2009-02-10
Hello,

I have a big problem when it comes to playing XIII (a game). The mouse does not want to move much in full screen mode. I searched (yes I did), and I found several other games are affected by this.

[Here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7119") is the wineHQ page for the game.

And [THIS]("http://bugs.winehq.org/show_bug.cgi?id=6971#c26") comment has a "hack" so to speak, to fix my problem.

> This hack forces Wine to use mouse warping even if the cooperation level does
not include DISCL_EXCLUSIVE.

It's certainly NOT a permanent solution and is meant for testing only.

This patch enables mouse in the Raven Shield menu while the real implementation
is on the way.

The mission briefing menu however has a strange drawing bug so I had to guess
where to click START.

I don't know how this affects other applications.

And this is the attachment.

```
--- dlls/dinput/mouse.c.orig	2007-08-25 00:00:00.000000000 +0300
+++ dlls/dinput/mouse.c	2007-08-25 00:00:15.000000000 +0300
@@ -293,7 +293,7 @@
                 wdata = pt1.y;
             }
 
-            This->need_warp = (pt.x || pt.y) && dwCoop & DISCL_EXCLUSIVE;
+            This->need_warp = (pt.x || pt.y);
             break;
         }
         case WM_MOUSEWHEEL:

```

I would like to know if there are any other fixes for this problem, or how to apply the patch above so my problem can be fixed.

The only problem is that WINE has gone a lot further than in 2007, so I'm not sure whether the patch will work.

Any help is appreciated! :D

Thank you.

---

### Post by cogadh on 2009-02-10
In order to use that patch you need to get the Wine source code, apply the patch to it, then compile Wine yourself. However, as you say, Wine has progressed a lot since 2007, so you might not need to do that at all. Current versions of Wine allow you to force mouse warping with a registry change/addition.

Fire up regedit, go to HKEY_CURRENT_USER/Software/Wine and create a new key called "DirectInput". Within that key, create a new string called "MouseWarpOverride". You can set the string to one of three values:
enable:  (default) warp pointer when mouse exclusively acquired
disable: never warp the mouse pointer
force:   always warp the pointer

I believe the "force" option will do what you need it to do.

---

