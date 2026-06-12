---
title: "Has anyone got Team Fortress 2 running successfully under any version of WINE 1.1.2x?"
date: 2009-07-15
forum: Wine
---

### Post by ThisEndlessFall on 2009-07-15
I would like to get this up & running under WINE, but have read that it doesn't work very well. 

Can anyone who has got it working under 1.1.25 post how they did it?

---

### Post by xArv3nx on 2009-07-16
> **ThisEndlessFall said:**
> I would like to get this up & running under WINE, but have read that it doesn't work very well. 

Can anyone who has got it working under 1.1.25 post how they did it?
i had to tweak my graphics settings in the optins menu a lot until it worked (along with turning off compiz).

i heard mainly just try changing your resolution to your native one and you'll get a major fps boost. fyi for anyone wondering the only issues tf2 has on jaunty wine atm is that it's fps is horrible even with everything on low unless you have a mad powerful computer (im assuming)

---

### Post by PureLoneWolf on 2009-07-16
Mine runs without any real issue, except for every 30-40 minutes I get a massive 1 second framelag.  Then it is fine for another 30-40 minutes.

I get no noticeable framelag during the game as described by xArv3nx - It runs perfectly with some caveats...I even run with Compiz still on (it is entirely possible that I am just lucky though).

In Steam, I specified the following launch options for TF2:

```
-windowed -width 1280 -height 1024 - heapsize 2097152 -dxlevel 80
```

I have to run windowed due to my twinview setup.  The heapsize is half of my ram and setting the dxlevel to 80 stopped me getting random crashes.  I didn't change any of the ingame graphics options at all..I am running at out of the box settings.  

It's probably not as pretty as running full DX9 on Windows, but in the heat of a game...noone likes to admire the rocket as it is hurtling towards your feet...better to airblast it away and admire the "WTF!" comments as the die at their own hand :)

Hope that helps

---

### Post by NightMKoder on 2009-07-16
If you've got an ATI card, look into a setting called OffscreenRenderingMode. ATI drivers really suck (for now).

---

### Post by ThisEndlessFall on 2009-07-16
> **PureLoneWolf said:**
> Mine runs without any real issue, except for every 30-40 minutes I get a massive 1 second framelag.  Then it is fine for another 30-40 minutes.

I get no noticeable framelag during the game as described by xArv3nx - It runs perfectly with some caveats...I even run with Compiz still on (it is entirely possible that I am just lucky though).

In Steam, I specified the following launch options for TF2:

```
-windowed -width 1280 -height 1024 - heapsize 2097152 -dxlevel 80
```I have to run windowed due to my twinview setup.  The heapsize is half of my ram and setting the dxlevel to 80 stopped me getting random crashes.  I didn't change any of the ingame graphics options at all..I am running at out of the box settings.  

It's probably not as pretty as running full DX9 on Windows, but in the heat of a game...noone likes to admire the rocket as it is hurtling towards your feet...better to airblast it away and admire the "WTF!" comments as the die at their own hand :)

Hope that helps

Thank you. I will certainly try these tips.

> **NightMKoder said:**
> If you've got an ATI card, look into a setting called OffscreenRenderingMode. ATI drivers really suck (for now).

Again, thank you. But as I have Nvidia this is of no use to me.

---

### Post by PureLoneWolf on 2009-07-18
No problem and also, I completely forgot to mention that I use a specific command to actually launch steam.

```
WINEDEBUG="fixme-all" wine Steam
```

from the directory that Steam is in

---

