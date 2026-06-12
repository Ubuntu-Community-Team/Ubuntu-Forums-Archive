---
title: "Video tearing with GNOME-Shell"
date: 2011-11-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Starks on 2011-11-06
I can replicate this on a fresh Precise install when using GNOME-Shell and mplayer2.

Unity is unaffected.

I have Sandybridge graphics.

---

### Post by alphacrucis2 on 2011-11-06
Is this an Optimus setup? As far as I know this is still not properly supported.

---

### Post by Starks on 2011-11-07
That has nothing to do with the topic at hand for multiple technical reasons that I don't feel compelled to explain at this time.

---

### Post by 23dornot23d on 2011-11-07
I notice it too on my desktop computer ....... but it only has 512 Meg Ram
and a Nvidia 6200 graphics card .... 

But have not noticed it on my Dual core laptop ... with a Nvidia 9300 .... and 4 Gig of memory.

---

### Post by MacUntu on 2011-11-07
Sandy Bridge X driver issue. With Compiz you can work around it, with mutter probably not. See [https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/755841](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/755841)

---

### Post by Starks on 2011-11-07
I find it profoundly stupid that GNOME3 lacks a functional equivalent of CCSM by which I could enable Vsync or adjust the swap interval.

---

### Post by JayKay3OOO on 2011-11-07
I had the same problem, but on the AMD E350 fusion platform, but I read it was due to bad driver support for integrate graphics chips.

Not had my hands on any of the integrate intel stuff or the higher end AMD integrate gpu chips to see if the problem is with all of them.

With my pc with dedicated graphics the problem does not persist.

---

### Post by ventrical on 2011-11-07
> **Starks said:**
> I find it profoundly stupid that GNOME3 lacks a functional equivalent of CCSM by which I could enable Vsync or adjust the swap interval.


There is  me and  a thousand others trying to render a work-a-round for this at the moment.

---

### Post by MacUntu on 2011-11-07
Workaround: use Unity. :-)

---

### Post by ventrical on 2011-11-08
> **MacUntu said:**
> Workaround: use Unity. :-)


   The way I have approached this new animal (said with tounge in cheek) is that I treat Unity and GNOME 3 as two seperate entities.GNOME  ver 2.x series was basically made for compiz.  GNOME was not dependent on compiz but compiz was dependent on GNOME, for the ccsm to work , to be able to display it's eye-candy. Now, GNOME fallback, GNOME (no effects)  and GNOME Classic cannot have ccsm do anything. GNOME 3 renderes some type of weak facsimilie with it's  veiwport slider bar - but it is hardly  compiz in all of it's funtionality.

  I do use Unity. It's great. And compiz works great too but I do not see where Unity is a workaround  for  current versions of GNOME that came packed with Ocelot soon to be Precise.

---

### Post by Starks on 2011-11-09
Not sure what I did, but either this was fixed with recent updates to Precise or the Ricotz Testing PPA.

---

