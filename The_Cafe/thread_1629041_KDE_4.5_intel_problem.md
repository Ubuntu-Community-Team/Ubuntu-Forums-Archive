---
title: "KDE 4.5 intel problem?"
date: 2010-11-23
forum: The Cafe
---

### Post by armageddon08 on 2010-11-23
Has intel 945GM driver + KDE 4.5/Desktop Effects[esp. blur] problem been solved ? Previously the systems with intel 945GM cards were performing very poorly under KDE 4.5 with Desktop Effects.

---

### Post by Joe of loath on 2010-11-23
Considering how terrible the older Intel graphics chips were, I think it's more a hardware issue than a software one. No driver, no matter how good, can speed up a slow chip.

---

### Post by LowSky on 2010-11-23
That chip is very weak. I wouldn't try running any type of effects with it.

---

### Post by Dragonbite on 2010-11-23
> **armageddon08 said:**
> Has intel 945GM driver + KDE 4.5/Desktop Effects[esp. blur] problem been solved ? Previously the systems with intel 945GM cards were performing very poorly under KDE 4.5 with Desktop Effects.

Was this one of those Intel chips that failed to boot (kernel issue) starting with 10.04 and hasn't been resolved in any of the major distributions yet?  I mean, sort-of fixed;[LIST]
[*] Fedora applied the "big hammer" patch to Fedora 13 and so my Fedora has full video effects. 
[*]While Ubuntu 10.10 improved over 10.04 in that it booted up but still cannot do desktop effects while 10.04 cannot do external monitor but otherwise worked with a patch installed.
[*]openSUSE worked for a while, but a recent kernel update seems to have killed that and the prognosis isn't good
[/LIST]

I have an intel i855 chip.

---

### Post by armageddon08 on 2010-11-23
All KDE versions before 4.5 worked flawlessly on my notebook. But after upgrading to KDE 4.5 in maverick, I was completely unable to apply desktop effects. Does anyone know if any solution is available.

---

### Post by Dustin2128 on 2010-11-24
its an intel integrated chip. What are you expecting?

---

### Post by Islington on 2010-11-24
> **armageddon08 said:**
> All KDE versions before 4.5 worked flawlessly on my notebook. But after upgrading to KDE 4.5 in maverick, I was completely unable to apply desktop effects. Does anyone know if any solution is available.

did you try shutting off compatibility checks/ modifying the kwin config file?

---

### Post by Dragonbite on 2010-11-24
> **Dustin2128 said:**
> its an intel integrated chip. What are you expecting?

In Fedora I am running an older Intel chip, upgraded to KDE 4.5.3 and have full desktop effects, external monitor,  webcam and video playback so Intel or not, if the kernel and the drivers are working he should have what he wants.

I have issues with desktop effects on my mentioned Fedora (of not starting automatically during bootup, but they turn on just fine) and was told to try renaming ```
~/.kde/share/config/kwinrc
```It may be a long-shot (I'm still trying to get more familiar with KDE, a long time Gnome user) but could be worth taking a look at it.

If you try this, make sure to post whether it is successful or not.

---

### Post by Shining Arcanine on 2010-11-24
> **armageddon08 said:**
> All KDE versions before 4.5 worked flawlessly on my notebook. But after upgrading to KDE 4.5 in maverick, I was completely unable to apply desktop effects. Does anyone know if any solution is available.
I had the same problem on Gentoo Linux. I fixed it by deleting ~/.kde4/share/config/kwinrc and restarting KDE.

---

### Post by james_xxx on 2010-11-25
These issues in K/Ubuntu 10.10 are **driver** issues.

Yes, these video adapters are weak, but the folks in this thread claiming that this is the source of the current problems many are experiencing have absolutely no idea what they are talking about.

At the moment the kernel drivers for some mobile Intel GPUs, combined with the Xorg version being used in Maverick, are causing many people a lot of trouble.

Things will work fine, if one stays with 10.04 for the time being.

Chances are reasonably high that by the time 11.04 rolls out, fuller functionality for these adapters will be possible again.

---

