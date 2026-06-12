---
title: "Can Source games be run with OpenGL?"
date: 2009-04-21
forum: Wine
---

### Post by Noise... on 2009-04-21
I installed Half-Life 1 today, after being unable to get Half-life 2 working last week. HL1 works flawlessly, and under graphics type it shows "OpenGL"

Do source games (hl2, CSS, Gmod) run with OpenGL? Is it activated by default? If they do work with it, and it isn't, is there a way to run them with it?

---

### Post by asdfoo on 2009-04-21
> **Noise... said:**
> I installed Half-Life 1 today, after being unable to get Half-life 2 working last week. HL1 works flawlessly, and under graphics type it shows "OpenGL"

Do source games (hl2, CSS, Gmod) run with OpenGL? Is it activated by default? If they do work with it, and it isn't, is there a way to run them with it?

No, the source engine games only use Direct3D for rendering.  Depending on which video card and drivers you have you will get a better or worse experience.

Some of the source games let you specify a dxlevel7 8 or 9, I think you'll find the information on how to do that on the AppDB.

---

### Post by u235sentinel on 2009-04-22
> **asdfoo said:**
> No, the source engine games only use Direct3D for rendering.  Depending on which video card and drivers you have you will get a better or worse experience.

Some of the source games let you specify a dxlevel7 8 or 9, I think you'll find the information on how to do that on the AppDB.

I've mostly had good experiences with this.  I'm running Ubuntu 8.04 and thinking of upgrading my Nvidia driver from the 169 to 180 flavor.  I'm hoping it helps with some of the latency issues I've been seeing on occasion with running CSS under WINE>

I've also noticed that upgrading to WINE 1.1.18 seemed to fix most of the latency issues (not all) however there are a few maps that seem to crash the game when playing.  And it's the same maps that cause the crash.  Usually custom ones though.

---

### Post by Brynster on 2009-04-23
> **asdfoo said:**
> No, the source engine games only use Direct3D for rendering.  Depending on which video card and drivers you have you will get a better or worse experience.

Some of the source games let you specify a dxlevel7 8 or 9, I think you'll find the information on how to do that on the AppDB.


thats not quite correct and not quite incorrect either. They use natively D3d and DirectX however if you add th -opengl flag at the end of the launch prompt it forces OpenGL on earlier source games (HL2 CS: S DOD etc) it doesn't work though for later source games (portal Left4Dead TF2).

---

### Post by Bölvaður on 2009-04-23
Yes, all the older games (for me it feels strange calling them new) people preferred opengl (CounterStrike mainly) because it worked better and gave better fps.
So if you have games based on HL (the original) they will work very well.

---

### Post by asdfoo on 2009-04-24
> **u235sentinel said:**
> I've mostly had good experiences with this.  I'm running Ubuntu 8.04 and thinking of upgrading my Nvidia driver from the 169 to 180 flavor.  I'm hoping it helps with some of the latency issues I've been seeing on occasion with running CSS under WINE>

I've also noticed that upgrading to WINE 1.1.18 seemed to fix most of the latency issues (not all) however there are a few maps that seem to crash the game when playing.  And it's the same maps that cause the crash.  Usually custom ones though.

180.44 works quite well, it fixed some memory leaking issues that would make CS:S run out of memory after a round or two

---

