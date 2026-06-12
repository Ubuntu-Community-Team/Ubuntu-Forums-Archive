---
title: "DVD Authoring/Burning/Codec Conversion Guides for Linux"
date: 2008-08-23
forum: The Cafe
---

### Post by Changturkey on 2008-08-23
Anyone know of Linux specific burning guides for burning a basic DVD to play on your DVD player? I have a bunch of .VOB files. In relation, I would also like to ask is .VOB the only kind of file that can be burned to a DVD to be played on a regular DVD player?

---

### Post by mips on 2008-08-23
> **Changturkey said:**
> I would also like to ask is .VOB the only kind of file that can be burned to a DVD to be played on a regular DVD player?

Many DVD players these days support DivX so you can just create a normal data dvd with the files on it and the player should play them if it supports DivX

---

### Post by ghindo on 2008-08-23
> **Changturkey said:**
> Anyone know of Linux specific burning guides for burning a basic DVD to play on your DVD player? I have a bunch of .VOB files. In relation, I would also like to ask is .VOB the only kind of file that can be burned to a DVD to be played on a regular DVD player?I actually have the exact same question.  The Wikipedia article on .Vob says that it can be "easily done" with software like K3b, but I'm still unsure :(

---

### Post by Changturkey on 2008-08-23
Yeah I am just trying to find a guide with screen shots hopefully. I am not sure my parent's DVD supports Divx so that's why I am concerned about changing video formats in to what I believe is MPEG-2? AVI? Ugh :confused:.

---

### Post by tbroderick on 2008-08-23
> **Changturkey said:**
> Yeah I am just trying to find a guide with screen shots hopefully. I am not sure my parent's DVD supports Divx so that's why I am concerned about changing video formats in to what I believe is MPEG-2? AVI? Ugh :confused:.

Take a look at devede. 

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

It will make a playable dvd or cd out of any format supported by mplayer. I've used it to convert an avi to iso and then burned the iso using growisofs.  

```

growisofs -dvd-compat -Z <device>=dvd.iso

```

---

### Post by stinger30au on 2008-08-23
hope this helps

[http://ubuntuforums.org/showthread.php?t=781429](http://ubuntuforums.org/showthread.php?t=781429)

---

