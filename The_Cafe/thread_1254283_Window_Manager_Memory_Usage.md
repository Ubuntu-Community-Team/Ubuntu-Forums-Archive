---
title: "Window Manager Memory Usage"
date: 2009-08-31
forum: The Cafe
---

### Post by Mark76 on 2009-08-31
I did a quick test using the mem.py script I found on K. Mandla's blog. Here are the results for a number of popular and not so popular WMs.

(Heaviest first)

**AEWM++**: 585.0 MiB
**Compiz with GTK window decorator**: 54.4 MiB (inc 50 MiB for Compiz)
**Compiz with Emerald Window Manager**: 54.3 MiB (inc 50.4 MiB for Compiz)
**FVWM2**: 5.6 MiB
**Openbox**: 5.4 MiB
**Metacity**: 5.0 MiBs
**Sawfish**: 5.0 MiB
**Fluxbox**: 4.0 MiB
**IceWM**: 2.9 MiB
**Blackbox**: 2.1 MiB
**TWM**: 1.8 MiB
**FLWM**: 1.5 MiB
**OroboROX**: 1.5 MiB
**JWM**: 1.3 MiB
**Oroborus**: 871.5 KiB


Note: This is in no way a scientific test.  Also I didn't test any of the tiling WMs.

Regardless, I hope it's of some use.

---

### Post by earthpigg on 2009-08-31
e17 is kind of wave-of-the-future and then-next-big-thing and all over digg.com... anyone recall what WM that uses?

---

### Post by cascade9 on 2009-08-31
Enlightenment is the window manager ;) e17/dr17 is just the version number.

---

### Post by Mark76 on 2009-08-31
I did try e16 (but not e17, which isn't in the repos), but it did something funny to the desktop.

---

### Post by blithen on 2009-08-31
I like e17, but it's so damn hard to install it's not worth it.

---

### Post by mrgnash on 2009-08-31
> **blithen said:**
> I like e17, but it's so damn hard to install it's not worth it.

```


sudo echo "## OpenGEU
 deb http://opengeu.linuxfreedom.com/ubuntu jaunty main extras opengeu" >> /etc/apt/sources.list && wget -q http://opengeu.linuxfreedom.com/ubuntu/dists/repo.key -O - | sudo apt-key add - && sudo apt-get update && sudo apt-get install opengeu-desktop
```

Yes, *very* hard :P

---

### Post by Harii on 2009-09-21
Did you know that oroborus can use xfce themes?
just take the theme out of the xfwm4 folder.

---

### Post by Mark76 on 2009-09-21
Yes I did :D

OroboROX (which is basically a rewrite of Oroborus in Python) can do the same.

---

### Post by stanca on 2009-10-04
4mb fluxbox to me too.;)

---

### Post by toupeiro on 2009-10-04
Uhh, you're listing heaviest first, but look at your bottom process??

AEWM++: 585.0 MiB

---

### Post by Mark76 on 2009-10-04
Hmm.

You know. I have a suspicion that might be a typo.:-k

---

### Post by cariboo on 2009-10-04
> **earthpigg said:**
> e17 is kind of wave-of-the-future and then-next-big-thing and all over digg.com... anyone recall what WM that uses?

It's been the next big thing since 1997

---

### Post by graabein on 2009-10-04
Hey, care to check [Window Maker]("http://www.windowmaker.org/index.php") while you're at it?

---

### Post by Mark76 on 2009-10-04
Sure.

5.7 MiB + 777.0 KiB =   6.5 MiB       WindowMaker (2)

The entire WM desktop is currently 532 MBs of RAM

---

