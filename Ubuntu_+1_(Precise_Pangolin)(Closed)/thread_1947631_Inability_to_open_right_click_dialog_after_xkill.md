---
title: "Inability to open right click dialog after xkill"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ubuntu27 on 2012-03-27
Can someone reproduce this "bug" in Ubuntu Precise?


1) Alt + F2
2) Type ```
xkill
```

3) click on the empty desktop

----
4) Desktop wallpaper disappears.
5) Right click becomes impossible. (No menu appears)


EDIT: [Bug Rerport]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/965928")

---

### Post by cryptotheslow on 2012-03-27
Replicated here. Just results in a completely black desktop that responds to nothing. But then I did just kill it - so what is surprising about that? I xkilled it, it died and stayed dead..

I rather prefer killed things to stay dead than forever re-spawn, reanimating dead things can't be good can it?

Anyways, same happens here - although I'm not sure what I just killed it seems to stay dead.

What did you expect to happen?
Zombuntu? And a follow up Zombuntu 3D? Maybe Zombuntu Fallback Revelations? :popcorn:

Seriously - what expected behaviour do you think is bugged?

---

### Post by ubuntu27 on 2012-03-27
Thank you cryptotheslow.

I have been using Ubuntu since the second version was released (Hoary Hedgehog), and never seen this "feature" or "bug". Or at least I don't remember it.

I believe that this is a useless feature (if it is a feature) to allow the user to kill the desktop visually by using xkill and rendering the desktop unusable.

Many people can accidentally kill it.

In my case I discovered this by accident.
I tried to xkill a misbehaving app (rhythmbox), but the window closed automatically before I got the chance to "CLICK" on it. And, I clicked on the desktop by mistake.


I reported it to launchpad. We can find it as [bug#965928]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/965928")

I did not know which package to report to, so I chose a package randomly. We will appreciate if someone who knows the right package for thus bug could change it.



All right everyone, please comment or add yourself if you can reproduce [this bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/965928"). :guitar:

---

### Post by MacUntu on 2012-03-27
What's the bug? You xkill the desktop, the desktop goes away. Sounds like intended behavior to me.

> Many people can accidentally kill it.
Most users have no idea that xkill exists.

---

### Post by stinkeye on 2012-03-27
Your just killing nautilus, as it draws the desktop.
Open your home folder and nautilus restarts and your desktop 
right click is back.

---

### Post by ubuntu27 on 2012-03-27
> **stinkeye said:**
> Your just killing nautilus, as it draws the desktop.
Open your home folder and nautilus restarts and your desktop 
right click is back.

It was nautilus? Interesting. 

I remember "xkilling" the desktop on previous version of ubuntu, but this did not happened. (Can someone confirm this?)


I will leave up to others whatever or not this could be considered a bug.:)

---

### Post by stinkeye on 2012-03-27
I tested on my ubuntu studio 10.04 install and you can't kill nautilus.
It just reloads.

---

