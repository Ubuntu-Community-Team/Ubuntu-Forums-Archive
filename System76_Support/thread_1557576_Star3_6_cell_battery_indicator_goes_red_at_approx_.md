---
title: "Star3 6 cell battery indicator goes red at approx 30%"
date: 2010-08-20
forum: System76 Support
---

### Post by greghk on 2010-08-20
I noticed the Star3 battery indicator went red at around 30%.
This is with the 6 cell battery. I figure the 6 cell battery is probably good for 8 hours of light use (hard to tell exactly because I use the machine off and on). So if the battery discharges linearly 30% would give me another 2 hours. Seems a bit early to start warning.

I have both the 3 cell and 6 cell batteries so I can run one to empty and switch to the other. How low should I go before recharging?

Any suggestions for battery monitors? A quick Google turns up IBAM (Intelligent Battery Monitor)

thanks,
Greg

---

### Post by isantop on 2010-08-23
That does seem a bit early. I'll see if we can get a 6-cell battery in to test with. 

Regardless of when the warning light comes on, most Li-Ion batteries are happiest when they are run down to about 10%. They will also last longest if they are stored at about 40% charge.

---

### Post by greghk on 2010-08-23
Specifically, the red shading showed up in the Gnome applet battery indicator. I will also check the front indicator light the next time this happens.

Greg

---

### Post by greghk on 2010-08-27
Only the Gnome battery indicator is red not the hardware indicator light.

I used the Starling at home continuously playing Spider solitaire (no wifi, or vide0) till the red light came on. uptime indicated 4.5 hours passed till the battery discharged to 30%. At 5 hours it was down to 23% so battery might last about 6 hours. So the warning indicator comes on approx 1.5 hours before end of battery.

I checked the Gnome battery applet for settings to control the red warning and didn't find any so my first guess is that the battery is emitting some kind of warning at 30%. 

Will try the 3 cell battery. I suppose I can always try to read the source code to find out where the 30% comes from...

---

