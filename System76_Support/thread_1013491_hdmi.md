---
title: "hdmi"
date: 2008-12-16
forum: System76 Support
---

### Post by hvacr on 2008-12-16
I have the PP4 with 8.10 64 bit installed. I have the nvidia 177 drivers installed. I have the hdmi hooked up to my tv, and cannot get this to work. The hdmi works in vista, but nothing with this setup. I enable the tv in the nvidia x-server setting, but no luck. 

Does ubuntu not support hdmi?

---

### Post by wrender on 2008-12-16
Yes it does... you have to click "configure" and select how you want the hdmi to work. ie clone video out or twin view... etc

Sound on the other hand I am waiting to hear what the deal is.

---

### Post by hvacr on 2008-12-17
> **wrender said:**
> Yes it does... you have to click "configure" and select how you want the hdmi to work. ie clone video out or twin view... etc

Sound on the other hand I am waiting to hear what the deal is.

Does not work for me at all, in any of the settings.

---

### Post by hvacr on 2008-12-17
Got hdmi working, now how to you enable spdif output. I have enabled IEC958, but get nothing.

---

### Post by wrender on 2008-12-18
Out of curiosity... what did you have to do to fix your video situation?

---

### Post by hvacr on 2008-12-18
> **wrender said:**
> Out of curiosity... what did you have to do to fix your video situation?

When ever I want to use the hdmi, I have to go to the nvidia x-server settings. I then let it scan for monitors, my tv will show up then. I have to click the tv, choose twinview, the click the laptop screen and disable then click apply.

Not very user friendly at all, in vista I just plug in the tv and everything is a go.

---

### Post by tribaal on 2008-12-18
Same here, I need to run nvidia settings, let it scan for displays, and activate my TV (I like to set it as a separate X sceen, but that's just me).

Also I need to "save X configuration file" (need to be root for that), and logout / login for it to work the way I expect it to.

Not very user friendly indeed, hopefully this will improve over time.

- Trib'

---

