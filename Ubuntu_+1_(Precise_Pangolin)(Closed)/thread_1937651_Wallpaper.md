---
title: "Wallpaper"
date: 2012-03-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ybytyruzu on 2012-03-08
Hi, when I change wallpaper if panel is set to full transparency the old wallpaper stay on panel. Only when I logout is fixed. Somebody experienced this behaviour on panel?

Regards,

JC

---

### Post by linux6994 on 2012-03-08
My panel is behaving normally, but I am using wallch wall paper changer.

---

### Post by grahammechanical on 2012-03-08
This has never happened to me and I have been using 12.04 since November 2011 with the top panel set to full transparency.

I does not happen when I use the wallpaper slide show or a static background image. It never happened when I was running a beta version of Compiz either.

Is your 12.04 up to date with all the updates? We have had a few updates to both Compiz and Unity as well as CCSM.

You could try re-installing Unity and its associated packages or Compiz or both but one at a time.

Regards.

---

### Post by ybytyruzu on 2012-03-08
Ok, maybe is because I use a python script for change automaticaly wallpapers. I will try Wallch.

---

### Post by rburkartjo on 2012-03-08
i am using walach and it works great in ubuntu 12.04.

---

### Post by mc4man on 2012-03-08
> **ybytyruzu said:**
> Hi, when I change wallpaper if panel is set to full transparency the old wallpaper stay on panel. Only when I logout is fixed. Somebody experienced this behaviour on panel?

Regards,

JC
This will happen unless your panel trans is set to 0.0000, anything higher draws the background on the panel vs. letting the background show thru, so a restart of unity/comiz is needed

Here I actually use the lowest above 0.0000, "0.0100", which will prevent a bug that can have appmenus 'show thru' in black. Apparently  that doesn't affect all as some in this post have mentioned using 'full' (0.0000) trans.

If affected by 'black text' on full trans - 
[https://bugs.launchpad.net/unity/+bug/924592](https://bugs.launchpad.net/unity/+bug/924592)

---

### Post by ybytyruzu on 2012-03-08
Hi mc4man,

Your solution worked here, I set to 0.0100 the panel transparency and is fixed. Now Wallch work ok. Thank You

---

### Post by VinDSL on 2012-03-08
> **ybytyruzu said:**
> Hi, when I change wallpaper if panel is set to full transparency the old wallpaper stay on panel. Only when I logout is fixed. Somebody experienced this behaviour on panel?
Heh!  I got that one beat (unless we're talking about the same thing)...

Yesterday, I changed walls.

The only thing that changed was the wallpaper UNDER the panel and launcher.  The wallpaper, itself, in the middle of the screen (let's call it the user space) remained the original.  It didn't change.  LoL!  :D

Haven't experienced it again, since I restarted Ubu.

---

