---
title: "User experience: Everything is &quot;HUGE&quot;"
date: 2017-10-15
forum: Ubuntu Development Version
---

### Post by ubname on 2017-10-15
Hi,

i find the new ubuntu quite pleasant exept for the fact 
that everything is quite BIG, is it possible to scale down
a bit (like in 16.04) to e.g 0.8/0.7 in some way?
i do not find this option in settings, is this a feature
to be implemented? (I understand it's quite a new interface)

Thanks

---

### Post by amano on 2017-10-15
There shouldn't be anything much bigger than in Unity.

What is your resolution? Mind trying ro crank that up?

It is in the control center (“Settings“) within the Devices section.

---

### Post by ubname on 2017-10-15
Yes in unity usually i scale down to 0.8 

resolution is 1920 x 1080 that's the max monitor resolution

i understand that i can only set values >= 1 not below

---

### Post by dino99 on 2017-10-15
Is it your issue ? [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1721082](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1721082)

---

### Post by mc4man on 2017-10-15
Install gnome-tweak-tool, as in screen you can scale fonts below 1, that may give you what you want. 
(- If you hold down on the minus it will go down fast although progress is not reflected in real-time

That bug was for the the continued use of unity, i.e. separate it's scale settings from gnome's

---

### Post by ubname on 2017-10-15
Thanks, it works for the text, not for the rest
just a issue of taste anyway.

---

### Post by jbicha on 2017-10-16
Please file a bug against gnome-shell or gnome-control-center to ask specifically for being able to scale to something like .8.

Fractional scaling is an experimental feature in GNOME 3.26 but it's not enabled by default. Even if it is enabled, I don't think the GNOME Settings app gives the option to scale to that value. (It's more interested in scaling to 125% or 150%.)

---

### Post by ubname on 2017-10-16
> **jbicha said:**
> Please file a bug against gnome-shell or gnome-control-center to ask specifically for being able to scale to something like .8.

Fractional scaling is an experimental feature in GNOME 3.26 but it's not enabled by default. Even if it is enabled, I don't think the GNOME Settings app gives the option to scale to that value. (It's more interested in scaling to 125% or 150%.)

Ok where should i report this, also i do not understand if settings is a gnome app or an ubuntu one (?)

---

### Post by jbicha on 2017-10-16
Let's start with gnome-shell. Run this command to start reporting the bug:

```

ubuntu-bug gnome-shell

```

The GNOME Settings app (gnome-control-center) comes from GNOME but Ubuntu has a few patches (like the one that adds Ubuntu Dock settings).

---

### Post by ubname on 2017-10-16
> **jbicha said:**
> Let's start with gnome-shell. Run this command to start reporting the bug:

```

ubuntu-bug gnome-shell

```

The GNOME Settings app (gnome-control-center) comes from GNOME but Ubuntu has a few patches (like the one that adds Ubuntu Dock settings).

Done it is actually a feature request dont know if we can say it is a bug (?)

---

