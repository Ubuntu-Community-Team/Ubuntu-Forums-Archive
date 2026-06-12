---
title: "Setting up LG LCD monitor on ServalPro?"
date: 2008-12-02
forum: System76 Support
---

### Post by OldDirtyTurtle on 2008-12-02
I don't know if this is the right forum or not but figured it was worth a try since System76 uses LG monitors for their desktops.

I've got a new Serval Pro (love it) that I bought a LG W2452T Flatron LCD monitor for.  I hooked it up with a DVI cable - nothing.  I did some searching in the forums and the only thing I found was a suggestion to use the displayconfig-gtk to install the driver from the monitor's CD.  Further digging revealed that apparently displayconfig-gtk was scrubbed prior to Intrepid.

Any suggestions for getting this big beautiful monitor working?  It's a Winbloze world, but I'm fighting!

---

### Post by thomasaaron on 2008-12-02
You should be able to detect and turn the monitor on my going to a terminal and entering...
```

nvidia-settings
```

---

### Post by OldDirtyTurtle on 2008-12-02
Thanks Tom.  It was recognized, but I had real trouble configuring it correctly.  At one point I hosed my graphics and had to let Ubuntu run in default (no nVidia driver).  Once I rebooted and reactivated the driver it was back to normal.  Good times!  ;)

I can't figure out how to make it a laptop-LCD replacement.  I could only get a poorly executed dual monitor setup going.  I'd like it to be my only monitor when plugged in.

I'm returning it anyway.  I'll be reattempting with another monitor.  This one was simply too large for my workspace!

Are there any tutorials out there for configuring external monitors with the nVidia settings GUI or otherwise?

---

### Post by thomasaaron on 2008-12-02
Another option might be System > Preferences > Screen Resolution.
You might be able to turn on your external monitor and set the resolution on your laptop lcd to "off".

---

### Post by jeamer on 2008-12-03
I'm pretty sure in the nvidia control panel you can set your external display to be the primary display, then disable the laptop display, then restart and everything should be gravy. Now something someone should work on is allowing the laptop to be closed when using the external monitor as the primary :D

---

### Post by OldDirtyTurtle on 2008-12-03
Does setting the power management options not work for this?  I assumed that if I set the "When laptop lid is closed" setting to "Do Nothing" that I could close the lid and keep on truckin'.

> **jeamer said:**
> I'm pretty sure in the nvidia control panel you can set your external display to be the primary display, then disable the laptop display, then restart and everything should be gravy. Now something someone should work on is allowing the laptop to be closed when using the external monitor as the primary :D

---

### Post by jeamer on 2008-12-03
Oh yeah totally! Thanks, forgot about that.

---

### Post by wecaoniddmab891 on 2008-12-08
hello ,everyone who know how to make [runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php) fast??

---

