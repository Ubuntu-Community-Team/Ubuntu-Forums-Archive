---
title: "Warcraft III + wine + Ubuntu 8.04 64 bit + Separate X window"
date: 2009-01-28
forum: Wine
---

### Post by andrijan on 2009-01-28
Hey guys,

I've been searching the forums for the solution to my problem but I'm not finding it.

Let's begin with the setup:

I have a Dell XPS M1530 and a Samsung SyncMaster 226BW 22" connected to it through HDMI
I'm running separate X windows on each screen.
I have the newest Wine (1.1.13) and it works perfectly with my Warcraft III

I have two problems though. 

1. When I alt+tab out of the game and back in to it the game gets messed up, it looks like it's in the early stages of the visual development (Textures messed up, everything "boxy" and white) and can't be fixed other than restarting the entire game. (The game still plays normally if that changes anything, just the visuals get messed up)

2. When I move to the right of my Warcraft game the mouse pointer moves on to the other screen since I'm running separate x windows. And if I accedentally click on the other screen Number 1 happens. Is there any way I can lock my pointer on the game while I'm in it?

Thanks in advance

---

### Post by argie on 2009-01-28
This may seem obvious, but have you set the "Let DirectX Applications prevent the mouse from leaving the window" option in winecfg? I don't have wine at the moment, but I distinctly remember it having that. Perhaps under the Input tab?

---

### Post by shae on 2009-01-28
In response to number 1, you have to use a patched version of wine to prevent Warcraft from loosing textures when minimized.  See my sig for details.

---

### Post by andrijan on 2009-01-29
> **shae said:**
> In response to number 1, you have to use a patched version of wine to prevent Warcraft from loosing textures when minimized.  See my sig for details.

That doensn't seem to work...

 > This may seem obvious, but have you set the "Let DirectX Applications prevent the mouse from leaving the window" option in winecfg? I don't have wine at the moment, but I distinctly remember it having that. Perhaps under the Input tab?

This doesn't seem to work either... It's like the wine I'm running is different from the one I patched and the one I change when I run winecfg...

---

