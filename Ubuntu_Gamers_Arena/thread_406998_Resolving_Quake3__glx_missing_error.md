---
title: "Resolving Quake3  glx missing error"
date: 2007-04-11
forum: Ubuntu Gamers Arena
---

### Post by vitality- on 2007-04-11
After scouring around for 20 minutes or so trying to solve a glx problem, I figured I'd post my results here for the next person to have this problem so they can find it easily.

When tarting quake3, my desktop would try switching resolutions to go into quake3 and re-appear at the desktop in a 640x480 installation.  I then ran quake3 from the console and observed the following error being output constantly to console before crashing:

Xlib: extension "GLX" missing on display

After searching around for a bit, I discovered this post:  [http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2663](http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=2663)

Basically, if you are using the nvidia-legacy drivers as I am (I have a GeForce 2), then you must add the following directive to your /etc/X11/xorg.conf file:

```

Section "Extensions" 
        Option  "Composite" "Disable"
EndSection
```

This did the trick!

---

### Post by BLTicklemonster on 2007-04-15
Having same problem with UT, after an Ubuntu upgrade, which is quickly becoming my self inflicted equivalent of the infamous "blue screen of death" in Windows...

Your trick didn't do me any good. 

This is getting old having to hunt down and redo everything every time I get an upgrade...

---

### Post by Perfect Storm on 2007-04-15
> **BLTicklemonster said:**
> Having same problem with UT, after an Ubuntu upgrade, which is quickly becoming my self inflicted equivalent of the infamous "blue screen of death" in Windows...

Your trick didn't do me any good. 

This is getting old having to hunt down and redo everything every time I get an upgrade...

Isn't that only a problem if you have installed non-repo drivers as I recall it.

---

### Post by BLTicklemonster on 2007-04-15
I was running the nvidia-glx from the non third party repos as found in synaptic.

BUT, what I just did was made sure I still had the nvidia.run drivers from nvidia's web site, booted to recovery, then installed. I was told that because I was "whatever reason it gave me" that it might not work, and I was given a choice to stop installation, or go ahead. Well, you know me... I went ahead anyway, and I'm back to normal. Well, ab-normal, but I can run glxinfo and everything is fine.

---

