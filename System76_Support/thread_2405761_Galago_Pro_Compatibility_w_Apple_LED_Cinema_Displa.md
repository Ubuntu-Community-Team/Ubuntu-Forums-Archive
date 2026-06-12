---
title: "Galago Pro Compatibility w/ Apple LED Cinema Display?"
date: 2018-11-10
forum: System76 Support
---

### Post by m9ke2 on 2018-11-10
**&#8203;**I am seriously considering buying a System76 Galago Pro.   I will be running Ubuntu if I purchase the laptop.

i already have an Apple LED Cinema Display Model A1316. 

This display has a permanently attached cable terminated with an Apple Mini-Display Port connector.

It would be way cool if I could use this monitor with my new laptop.

I would love some guidance from someone knowledgeable in this area.  I would especially like to hear from someone who has tried to connect this display with a Galago Pro, whether successfully or not.

Thanks!
Mike

---

### Post by undecidable on 2019-04-11
Replying late to this - just saw it.

I have a Apple 27" LED display  (2560x 1440) connected to a Galago UltraPro (Galu1).
This is an older model - 2014.  
It is connected to the miniDP connector and works perfectly,
both under both Kubuntu 14.04 and Xubuntu 18.04.

You can set it up from settings, though I generally use xrandr to turn it off and on:
```
xrandr --output eDP-1 --auto --pos 0x0 --output DP-1 --off
xrandr --output eDP-1 --auto --pos 0x180 --output DP-1 --auto --pos 1920x0
```

But note that the Galago Pro is different from the Galago UltraPro.
 if your model doesn't have a minDP port, you may need an adaptor.

---

