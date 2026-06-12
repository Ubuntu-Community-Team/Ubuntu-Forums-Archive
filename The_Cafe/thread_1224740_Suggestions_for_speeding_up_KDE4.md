---
title: "Suggestions for speeding up KDE4?"
date: 2009-07-27
forum: The Cafe
---

### Post by sunexplodes on 2009-07-27
Hi guys. I've been looking at the screenshot threads a lot, and it's locked me in this endless install/fiddle/uninstall cycle with KDE4. Like, it looks SO beautiful, but it's SO sluggish on my machine.

Have any of you done any tweaking/screwing around with settings that has made any noticable difference in terms of speed and responsiveness?

Like, I'm a big WM user, specifically Openbox and Pek, so I KNOW a big DE like KDE is going to be slower, but.. well, I used KDE3 happily for a long time, and it was leaps and bounds faster than its successor.

Any tips?

---

### Post by Skripka on 2009-07-27
What hardware are you on, and what linux are you running?

---

### Post by sunexplodes on 2009-07-27
> **Skripka said:**
> What hardware are you on, and what linux are you running?

Older hardware, p4 2ghz, geforce fx5200, 1gb ram. I don't expect a lot, just looking for tweaks. And I'm using Arch Linux. Have tried the testing repo, the main repo, and kdemod.

---

### Post by Skripka on 2009-07-27
> **sunexplodes said:**
> Older hardware, p4 2ghz, geforce fx5200, 1gb ram. I don't expect a lot, just looking for tweaks. And I'm using Arch Linux. Have tried the testing repo, the main repo, and kdemod.

What is sluggish, specifically?  Effects?  Apps?  Boot/shutdown?

---

### Post by sunexplodes on 2009-07-27
Pretty much everything. Apps take ages to open, Konqueror is laggy as hell, Dolphin is slow, the visual effects are slow, etc.. I get that I'm using older hardware and it's a new DE, I'm just looking for tweaks and things I can edit for a boost in performance.

---

### Post by Skripka on 2009-07-27
> **sunexplodes said:**
> Pretty much everything. Apps take ages to open, Konqueror is laggy as hell, Dolphin is slow, the visual effects are slow, etc.. I get that I'm using older hardware and it's a new DE, I'm just looking for tweaks and things I can edit for a boost in performance.

What does your Xorg look like?

Do you know where the bottleneck is in your hardware?

---

### Post by lykwydchykyn on 2009-07-27
The two heaviest bits I've found are the effects and nepomuk/strigi. Though the latter really only slows you down while indexing.

If you're running amarok, it seems to be resource heavy even when it's just sitting in the tray doing nothing.

But even apart from that, I've noticed that KDE just seems to take an oddly long time to draw windows on the screen on older hardware.  It may be a QT issue, I'm not sure.

Most of my hardware now is at least fast enough not to worry about it, but I've migrated away from KDE on my older (P4 era) hardware.

Are you using the proprietary NVIDIA driver or just the default one?

---

### Post by justsomedude on 2009-07-27
Taskbar thumbnails eat up a lot of resources, try to switch those off...

---

### Post by papangul on 2009-07-27
> **lykwydchykyn said:**
>   It may be a QT issue, I'm not sure.
It's definitely not a qt issue, non kde qt applications load very fast on my old p3 hardware.

---

