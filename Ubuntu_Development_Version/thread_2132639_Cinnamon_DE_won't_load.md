---
title: "Cinnamon DE won't load?"
date: 2013-04-05
forum: Ubuntu Development Version
---

### Post by ELD on 2013-04-05
I just upgraded to 13.04 now it's it's at least in Beta to test.

Cinnamon no longer loads, any idea how I can begin to trouble shoot this/any one else had the problem?

---

### Post by Redalien0304 on 2013-04-05
1st of did you use Cinnamon Stable? Try using Cinnamon nightly is what worked for me not cinnamon stable.

[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-nightly](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-nightly)

---

### Post by jbicha on 2013-04-05
What PPAs are you using? Did you look in your display manager logs (LightDM still uses ~/.xsession-errors while GDM uses ~/.cache/gdm/session.log)?

---

### Post by deadflowr on 2013-04-05
Having perused this thread, I decided to take a look at the cinnamon I have installed.
I installed through the repos, so whatever version is what's in there.

Same thing as OP, no desktop.

So I investigated further and noticed that the output for my xsession-errors kept listing caribou as not existing.

I remember that a few days ago, I ran an autoremove. So I looked at the /var/log/apt/history.log file, and lo and behold, it list the caribou packages as part of the removed.

So I simply installed caribou, and all is, so far, right as rain.

---

### Post by ELD on 2013-04-05
What exactly is caribou?

---

### Post by deadflowr on 2013-04-05
> **ELD said:**
> What exactly is caribou?

It's just an on screen keyboard app, but it uses a couple dependencies which are probably important to something like cinnamon.(My guess)

---

### Post by ELD on 2013-04-06
Hmm i'm guessing the Ubuntu package for cinnamon needs to be updated to depend on it then since its not in anymore by default?

---

