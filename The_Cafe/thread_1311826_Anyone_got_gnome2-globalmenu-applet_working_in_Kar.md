---
title: "Anyone got gnome2-globalmenu-applet working in Karmic?"
date: 2009-11-02
forum: The Cafe
---

### Post by cdwillis on 2009-11-02
I noticed that there isn't a karmic branch on their PPA yet. I've tried compiling from source and I managed to take the menu panel off the frame in nautilus, but the applet didn't appear in the list when I tried to add it to the gnome panel. I thought perhaps someone here may have fiddled with it at this point.:popcorn:

---

### Post by gashcr on 2009-11-02
I did, but I'am using a dev ppa, here:

[http://ppa.launchpad.net/sushkov/personal/ubuntu](http://ppa.launchpad.net/sushkov/personal/ubuntu) karmic main

---

### Post by cdwillis on 2009-11-04
I installed it but when trying to add the applet to my panel I get this error:

```
The panel encountered a problem while loading "OAFIID:GNOME_GlobalMenuApplet".
```

---

### Post by chenxiaolong on 2009-11-25
I have the exact same problem. I hope this is fixed soon.

---

### Post by Mr. Devil on 2009-11-25
> **cdwillis said:**
> I installed it but when trying to add the applet to my panel I get this error:

```
The panel encountered a problem while loading "OAFIID:GNOME_GlobalMenuApplet".
```

I'm in the same boat.

---

### Post by chenxiaolong on 2010-01-15
There's a working version in the globalmenu-team PPA: [https://launchpad.net/~globalmenu-team/+archive/ppa](https://launchpad.net/~globalmenu-team/+archive/ppa)

You can install it by running:

sudo add-apt-repository ppa:globalmenu-team/ppa
sudo apt-get update
sudo apt-get install gnome-globalmenu

---

