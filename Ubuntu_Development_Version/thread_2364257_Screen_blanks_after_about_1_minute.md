---
title: "Screen blanks after about 1 minute"
date: 2017-06-20
forum: Ubuntu Development Version
---

### Post by mike1772 on 2017-06-20
Lately I've developed an annoying issue that I believe occurred after installing 17.10 (though I'm not sure if it existed before but about 90% sure it didn't).  The symptoms as best as I can describe it are my screen blanks automatically after about 1 minute of not moving the mouse.  In Privacy I turned screen lock off.  In Power I have Blank screen set to never.  

In dconf-editor I tried setting org.gnome.desktop.screensaver/idle-activation-enabled to false (it says it's DEPRECATED but this seemed to work after I resigned in - but this may a fluke as the screen now stays on for hours... UNTIL the first time I move the mouse after signing on then it appears to have reverted back to blanking after every minute of inactivity.  I suspect idle-activation-enabled did nothing and my first time after that I just didn't move the mouse since I was testing if the screen blanked at all so I just walked away.

Anyone have any ideas I haven't tried?  It's getting pretty annoying as it's common I'm reading something for longer than 1 minute!  On the weekend I might re-install 17.04 to see if the problem exists there if I don't get a resolution by then.

Thanks,

---

### Post by dino99 on 2017-06-21
you might start cleaning the system, using autoremove, gtkorphan & bleachbit (as root, but be carefull when activating the features). Next, you can also purge then reinstall the graphic driver. And finally, if you have installed some non genuine packages, then downgrade them.

---

### Post by #&amp;thj^% on 2017-06-21
@-mike1772 have you tried this yet...works a treat for myself.
[https://extensions.gnome.org/extension/517/caffeine/](https://extensions.gnome.org/extension/517/caffeine/)

---

### Post by mike1772 on 2017-06-22
Sadly - I have tried caffine and no luck.  Seems like there is something else I'm missing that is causing the screen blanking as the normal things to do aren't working. :(  Thanks for the suggestion though.

---

### Post by mike1772 on 2017-06-23
Well - Re-reading from Dino99 about re-installing the graphics driver - that didn't work.  But uninstalling the nvidia driver entirely and using the open source driver did.  How odd.  I know I never had this issue before with the Nvidia drivers.  Most of the games I'm planing seem to work with the open source driver anyway so I'm going to work with that for a bit though I'd be interesting if anyone knows why the Nvidia driver is causing this.

Thanks again

---

### Post by mc4man on 2017-06-24
While it may not matter here , at this point good to mention which session out of the current 5 (gnome, ubuntu, unity, or either of the 2 wayless sessions you're using
check this setting - 
```
gsettings get org.gnome.desktop.session idle-delay
```

---

### Post by mike1772 on 2017-06-28
I'm using Ubuntu Gnome.  That command returns 

uint32 0

Which makes sense as I turned idle-delay off.  I have just re-installed the Nvidia drivers 381.22 and auto blanking after 1 minute is back unfortunately.  It only goes away with the Nouveau display drivers.  I would like to keep the nvidia drivers as some of my games work better with it but not unless I can resolve this I guess.

---

### Post by mike1772 on 2017-06-28
Also - it really seems to only affect Gnome.  In Unity the screen doesn't blank.  However as Much as I love Unity since it's going away I'm trying to make Gnome look like Unity did so I've uninstalled Unity.  I just tried KDE on the same PC and the screen is not blanking.  So it seems to be Gnome on 17.10 WITH the NVidia drivers.  So far that is the only pattern I've been able to determine.

---

### Post by mc4man on 2017-06-28
You could try - 
Re-install using current Ubuntu-17.10 image, don't remove anything, just login to gnome
Re-install using current Ubuntu-Gnome-17.10 image, it's a slightly different experience atm
or
check & see if it's DPMS related. run this command
```
xset -dpms
```

Here on an optimus machine can't duplicate your issue (current Ubuntu image), I'm guessing you have a desktop machine?

---

### Post by mike1772 on 2017-06-29
Thanks mc4man - I ran that command - I assume that turns dpms off?  I'll google it.    Yes it is a desktop machine.  I've had it since Christmas - but this behavior has only occurred since installing 17.10.  My last post was slightly inaccurate - I went back tried KDE again - it did in fact happen there.  But I spent quite a bit of time in Unity a week ago and it did not occur there.  Also - I should have mentioned the video card is a GeForce GTX960.  I will try re-installing 17.10 on the weekend and if that doesn't work - drop down to 17.04 and see what happens.

---

### Post by #&amp;thj^% on 2017-06-29
> **mike1772 said:**
> Thanks mc4man - I ran that command - I assume that turns dpms off?  I'll google it.    Yes it is a desktop machine.  I've had it since Christmas - but this behavior has only occurred since installing 17.10.  My last post was slightly inaccurate - I went back tried KDE again - it did in fact happen there.  But I spent quite a bit of time in Unity a week ago and it did not occur there.  Also - I should have mentioned the video card is a GeForce GTX960.  I will try re-installing 17.10 on the weekend and if that doesn't work - drop down to 17.04 and see what happens.

mc4man has a great thought forgot about it, you can check to what is set with:
```
xset q | grep timeout
 
```
Mine shows:
```
xset q | grep timeout
 timeout:  0    cycle:  0
```

---

### Post by VMC on 2017-06-30
Here's mine:
```
xset q | grep timeout
timeout:  900    cycle:  0
```

---

### Post by mike1772 on 2017-06-30
So - following an earlier suggestion I decided to not wait for the weekend and I re-installed 17.10 last night.  Loaded the Nvidia proprietary drivers and so far - screen isn't blanking at all.  I'm frustrated for not knowing what I did to cause this but that is greatly outweighed by the happyness that my screen stays on longer than a minute!  

Mine is currently timeout: 0 cycle: 0 by the way.

Thanks everyone for their help!

---

