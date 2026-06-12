---
title: "day of defeat source and wine"
date: 2011-04-20
forum: Wine
---

### Post by ELD on 2011-04-20
Okay guys never really good with WINE, looking to run day of defeat source on an AMD 5770 HD.

When it launches the terminal gets this:
> 
Direct3D9 is not available without OpenGL.
Direct3D9 is not available without OpenGL.


My graphics drivers are all up to date, any ideas?

---

### Post by disabledaccount on 2011-04-21
At First: what version of Catalyst, what version of kernel?
do You have HW acceleretion working in Linux? check:
>glxinfo | grep renderer
and:
>fgl_glxgears (ATI glxgears, should easily reach 300-400FPS on Your HW)

If acceleration works, then run regedit and check Wine D3D configuration under:
HKEY_CURRENT_USER\Software\Wine\Direct3D
If the key does not exist, then You can try create it and to add at least those 2 entries:
(type, name = value):
REG_SZ, UseGLSL = yes
REG_SZ, DirectDrawRenderer = opengl

---

### Post by ELD on 2011-04-21
Yeah i get over 1000 FPS.

How do i run regedit?

---

### Post by disabledaccount on 2011-04-21
If the game is installed in default prefix ( $HOME/.wine ), then just run terminal and type:
>regedit

:)

---

### Post by ELD on 2011-04-21
To tell the truth it was installed with crossover games (so still using wine essentially), would it still work the same?

---

### Post by brian70809 on 2011-04-21
Go into Crossover and go to Manage Bottles.. Select that Bottle and check the Applications.. see if DirectX 9 is installed.. if it isn't.. you need to install it.


So you then select Install Software and it opens another window.. then you go to the list and scrolldown to Runtime Support Components.. Select DirectX 9..

and there you go!

Good Luck!

Make sure you have latest ATI Driver and see what version of OpenGL it supports..

---

### Post by gradinaruvasile on 2011-04-21
> **ELD said:**
> Yeah i get over 1000 FPS.

How do i run regedit?

Over 1000???

Dude, i get 2500 with my onboard nvidia 8200. You definitely should have 5-10000 at least.

Are you using the proprietary driver? Because if not, you dont really have a chance on playing anything remotely serious on wine.

---

### Post by disabledaccount on 2011-04-21
> **gradinaruvasile said:**
> Over 1000???

Dude, i get 2500 with my onboard nvidia 8200. You definitely should have 5-10000 at least.

Are you using the proprietary driver? Because if not, you dont really have a chance on playing anything remotely serious on wine.What are you talking about?
**fgl_glxgears is not glxgears** - fgl_glxgears is at lest 6x glxgears at once + cube rotation and the result is just good (but I have ~1500FPS on HD5670, so I think his result could be better after some catalyst tunning)

I don't use crossover - and it's not exactly the same in terms of configuration so its hard to say what happened without debug output - try wine - it should work.

---

### Post by gradinaruvasile on 2011-04-22
Ok, my bad. I extracted fgl_glxgears from the ati installer and indeed gives me ~530.

BTW DoD Source should run fine, i did a test quite a while ago and was working well.

---

