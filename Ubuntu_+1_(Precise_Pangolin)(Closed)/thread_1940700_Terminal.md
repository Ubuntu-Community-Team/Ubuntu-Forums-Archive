---
title: "Terminal"
date: 2012-03-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Miykel on 2012-03-14
G'Day;  The fonts in the terminal tend to overlap, especially the m & w, tried a few desktops and fonts but it's always the same but if I copy and paste the line into gedit it comes out fine ???.
Regards Miykel

---

### Post by dino99 on 2012-03-14
are you talking about Precise/Unity or GS, gnome-classic, i386/amd64, default config or custom desktop ?

---

### Post by Gregory Lee on 2012-03-14
Fonts come in two varieties: fixed width and proportional.  In proportional fonts, letters are of varying width, and "m"/"w" are wider than other letters.  Wider letters have to be spaced further apart to look right.  "Terminal" does not know how to do that -- it spaces all letters equally, so the wider ones will overlap.  It sounds like you have somehow changed the fonts you use, so that a proportional font is being used for "terminal".  If so, the fix is to change "terminal" back to using a fixed width font.

---

### Post by jerrrys on 2012-03-14
there is something wrong with default setting.  just go here and uncheck the first box.

[ATTACH]214302[/ATTACH]

---

### Post by AnojiRox on 2012-03-14
nothing LOOKS wrong... it's the same as mine, and mine works. I'm on 11.10

---

### Post by jerrrys on 2012-03-14
Hi AnojiRox

I don't know about 11.10, not running it.

---

### Post by cariboo on 2012-03-14
> **AnojiRox said:**
> nothing LOOKS wrong... it's the same as mine, and mine works. I'm on 11.10

All of us here are running 12.04.

---

### Post by jerrrys on 2012-03-14
> **cariboo907 said:**
> All of us here are running 12.04.

but of course :)

---

### Post by sudodus on 2012-03-14
Try and compare the following fonts and sizes in good old ***xterm***
```
xterm -fa courier -fs 20
``` and
```
xterm -fa default -fs 20
```
At least for me, courier is wider and [FONT="Courier New"]*[SIZE="3"]mwmw[/SIZE]*[/FONT] does not overlap.

In ***gnome-terminal*** you select the dropdown menu
Edit -- Profile settings
and choose among many fonts and font sizes :-)

---

### Post by Miykel on 2012-03-14
Thanks for the help guys; I changed the monospace fonts to courier and that fixed it.
Kind Regards Miykel

---

