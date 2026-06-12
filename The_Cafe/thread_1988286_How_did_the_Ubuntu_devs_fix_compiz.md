---
title: "How did the Ubuntu devs fix compiz?"
date: 2012-05-27
forum: The Cafe
---

### Post by Avaritia on 2012-05-27
Im curious about why Ubuntu is the only distro left still using Compiz, whilst some other distros are even dropping compiz from the repository because of issuses such as games and Open GL apps stuttering and crashing when someone uses wine.

Is there a list of changes anyway that Ubuntu made to stabalise compiz? Im curious to look at it.

---

### Post by wojox on 2012-05-27
I thought I read somewhere last year they hired the Dev from Compiz. I run Ubuntu 12.04 Unity 3D on my machine and it does a good job. 

I turned Compiz off in previous versions. :P

---

### Post by roelforg on 2012-05-27
They did that because, instead of having it plug into the window manager and making the window decorations go through another seperate program, they made compiz the wm, eliminating an extra layer of communication and thereby stabelizing everything.

---

### Post by Simian Man on 2012-05-27
I don't know that they did fix it.  Compiz (and Unity) still does not work on one of my machines even though gnome-shell and Kwin effects do.

---

### Post by Bandit on 2012-05-27
> **Simian Man said:**
> I don't know that they did fix it.  Compiz (and Unity) still does not work on one of my machines even though gnome-shell and Kwin effects do.

That kinda sucks, I have had compiz working just fine and stable since Dec 2006. KDEs built in effects have never been solid for me. Strange how things work like that.

---

### Post by Linuxratty on 2012-05-27
Well Compiz is set up to work in Mint's Mate.

---

### Post by zombifier25 on 2012-05-28
> **Avaritia said:**
> Im curious about why Ubuntu is the only distro left still using Compiz, whilst some other distros are even dropping compiz from the repository because of issuses such as games and Open GL apps stuttering and crashing when someone uses wine.

Is there a list of changes anyway that Ubuntu made to stabalise compiz? Im curious to look at it.

Dunno, but [Compiz 0.9.7's Launchpad page](https://launchpad.net/compiz-core/0.9.7) explicitly said that
```
STABLE compiz 0.9.7 series

Stable fixes only please.
```

---

