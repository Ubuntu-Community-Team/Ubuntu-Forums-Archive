---
title: "Trackpad/mouse"
date: 2008-07-01
forum: System76 Support
---

### Post by bodam on 2008-07-01
I could probably just as easily ask this question in another forum, and I realize that it's probably a basic Linux question but, I have a Serval 4 and I am not a fan of the built-in mouse/trackpad (my hands keep brusing it while typing causing unwanted effects).  Is there a way to disable it yet still allow my external USB mouse to work?

---

### Post by ajopaul on 2008-07-02
in your /etx/X11/xorg.conf file , you will the input device section for touchpad, for me its synaptic touchpad, not sure wat u mite have, just have to comment that line and restart X, in any case backup your xorg.conf

---

### Post by thomasaaron on 2008-07-02
If you go to a terminal and enter this command...
```
sudo modprobe -r psmouse
```
...it will disable your mousepad.

To re-enable it...
```
sudo modprobe psmouse
```

---

### Post by elj4176 on 2008-07-02
My wife's new Vostro 1500 the same problem but I just want to change the sensitivity on it not disable it. Any ideas here?
She is getting frustrated that the cursor jumps all over when she is trying to type because her hand skims the touchpad.
thanks

---

### Post by thomasaaron on 2008-07-03
Sometimes the settings in System > Prefs > Mouse work for the touchpad. You might want to give that a try if you don't have System > Prefs > Touchpad.

---

