---
title: "Unity 8 to replace Unity 7?"
date: 2014-04-08
forum: Ubuntu, Linux and OS Chat
---

### Post by grier-devon on 2014-04-08
So I was playing with Unity 8 on my pc and I am wondering is this suppose to replace Unity 7? If so will Unity 8 once implemented still offer a Unity 7 fall back desktop? I like how Unity 7 feels to much to be replaced by something so focused on touch.

---

### Post by cariboo on 2014-04-08
Unity 8 shouldn't be as resource hungry as Unity 7, as there are plans to drop compiz completely. It will also be optimized for the desktop, so it won't be so dependant on a touch screen. Right now it looks like it won't be the default DE until 16.04. We'll get to play with it over the next three releases, so it should be fairly stable by the time it becomes the default.

---

### Post by grier-devon on 2014-04-08
Well I know it is in early development now probably more close to the version available for phone and tablet I am just hoping it is more desktop non touch friendly then the current version I just played with as this would be a horrible desktop.

---

### Post by help_me2 on 2014-04-08
> **grier-devon said:**
> Well I know it is in early development now probably more close to the version available for phone and tablet I am just hoping it is more desktop non touch friendly then the current version I just played with as this would be a horrible desktop.

I'm sure it will be optimized for the desktop. Mark won't forget about non-touch users. But I am looking forward to seeing ubuntu laptops and phones in action. Hopefully they will be able to run android apps.

---

### Post by grier-devon on 2014-04-09
From what I seen on Ubuntu onAir it should be able to run some as Google is pushing for apps to be built with HTML5 to run on devices and according to what I was watching Mark say they should then be able to run with no problems native on Ubuntu.

---

### Post by grahammechanical on 2014-04-09
How did you install Unity 8? Over the development period there have been a couple of methods. The most recent for Trusty Tahr is to use the software Centre to install unity8-desktop-session. And that should give us an option to use Unity 8 at the login screen. But it is not Unity 8 in the full meaning of what Unity 8 will be. It does not replace Unity 7 but runs as a shell on Unity 7.

Unity 8 has a different code base to Unity 7 and it is designed to run on the Mir display manager and the Mir/Unity 8 combination is apparently working fine on phones and tablets. Mir and Unity 8 come together and will not be on Ubuntu 14.04 nor back-ported to 14.04. I cannot see any reason for providing a Unity 7 fallback. Unity 8 is no different from Unity 7 in the sense that it will still run all the desktop applications that Unity 7 now runs.

The big problem as I understand it is not the compatibility of Mir/Unity8 with desktop machines but making sure that the Ubuntu mobile applications scale correctly when the converged Ubuntu code base is run on a desktop monitor. Remember, the ultimate intention is for a Ubuntu super phone/tablet to become a PC with the addition of a keyboard, mouse and monitor.

Regards.

---

### Post by grier-devon on 2014-04-09
I installed Unity 8 under 14.04 with...
```
[COLOR=#000000]sudo apt-get install unity8-desktop-session-mir[/COLOR]
```

I see what your saying I am excited and hoping to see how Unity 8 will be constructed for non touch devices so it makes more sense.

---

### Post by Hylas de Niall on 2014-04-12
> **cariboo907 said:**
> Unity 8 shouldn't be as resource hungry as Unity 7, as there are plans to drop compiz completely. It will also be optimized for the desktop, so it won't be so dependant on a touch screen. **Right now it looks like it won't be the default DE until 16.04**. We'll get to play with it over the next three releases, so it should be fairly stable by the time it becomes the default.

Cool! All the more time with the lovely Unity 7 :D

---

