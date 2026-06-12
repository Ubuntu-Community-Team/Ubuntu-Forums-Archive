---
title: "Is there any way..."
date: 2008-06-20
forum: The Cafe
---

### Post by Mazza558 on 2008-06-20
...to turn AWN reflections off? I can't find any setting that lets you do so. If I can manage this, I'll have an even nicer desktop...

---

### Post by frup on 2008-06-20
Where did you get that photo? It's amazing. It's Rangitoto, the "youngest" volcano in Auckland, New Zealand. I'm trying to work out which beach it was taken from but that is a little hard considering that Rangitoto looks similar from many angles.

If that is not edited (colours), that would be the most amazing sky in New Zealand ever! I have never seen something so stunning!

---

### Post by pmlxuser on 2008-06-20
advanced AWN configuration can be set in config Editor
1. Open Gconf (Applicatons > System Tools > Configuration Editor)/ alt + F2 conf-editor
2. Click on Apps > Avant-Window-Navigator > 
there is a line that talks about "glass_highstep & glass_step" try playing around with the values you might find what you are looking for.

---

### Post by moonbeam on 2008-06-20
About the only way at this time would be to decrease the icon offset to 0.  But that would lower your icons.

I'm currently working on the effects engine and chances are some config item to control reflection alpha will turn up over the next few weeks... no time line on it though.

---

### Post by Mazza558 on 2008-06-20
> **moonbeam said:**
> About the only way at this time would be to decrease the icon offset to 0.  But that would lower your icons.

I'm currently working on the effects engine and chances are some config item to control reflection alpha will turn up over the next few weeks... no time line on it though.

Ah, that's cool. I'm using the ppa for AWN, so I assume this'll be added as/when it gets done?

> **frup said:**
> Where did you get that photo? It's amazing. It's Rangitoto, the "youngest" volcano in Auckland, New Zealand. I'm trying to work out which beach it was taken from but that is a little hard considering that Rangitoto looks similar from many angles.

If that is not edited (colours), that would be the most amazing sky in New Zealand ever! I have never seen something so stunning!

I got it from Interfacelift as far as I know. It's not edited according to its entry.

[http://interfacelift.com/wallpaper/details.php?id=1583]("http://interfacelift.com/wallpaper/details.php?id=1583")

---

### Post by moonbeam on 2008-06-20
> **Mazza558 said:**
> Ah, that's cool. I'm using the ppa for AWN, so I assume this'll be added as/when it gets done? 

Yes the ppa will have it.  It probably won't show in awn-manager for a while (if ever).  Keep an eye out for a new key in gconf instead.

/apps/avant-window-navigator/app/reflection_alpha

is the most likely name.

---

### Post by moonbeam on 2008-06-20
> **Mazza558 said:**
> Ah, that's cool. I'm using the ppa for AWN, so I assume this'll be added as/when it gets done?

I had a quick look at it tonight. And pushed the change into trunk.  So you should see a /apps/avant-window-navigator/app/reflection_alpha_multiplier config item the next time the ppa updates.  Set it to 0.0.   Enjoy.

---

### Post by Mazza558 on 2008-06-21
> **moonbeam said:**
> I had a quick look at it tonight. And pushed the change into trunk.  So you should see a /apps/avant-window-navigator/app/reflection_alpha_multiplier config item the next time the ppa updates.  Set it to 0.0.   Enjoy.

Brilliant, thanks a lot. :)

---

