---
title: "gnewsense default packages"
date: 2007-01-15
forum: The Cafe
---

### Post by ihavenoname on 2007-01-15
Hey I would like to try gNewSense, given that some of the "blobs" in Ubuntu have in the past caused me headaches. Yet I will still need to compile some kernel modules (non-free..yes I know..I'm evil, but with Ubuntu planing to add nvidia etc. I free possible instability and perhaps adding only the garbage I need would be better than having the  garbage that everyone else needs as well. (does that make sense?) Anyways I need to know if gNewsense has the kernel headers installed by default. anyone know? (I see that they have the build-essential package in, but afaik that doesn't include the kernel headers.)

---

### Post by pvdg on 2007-02-15
I would suggest putting the question in the gNewSense forum, if you haven't done so yet:

[http://wiki.gnewsense.org/ForumMain/ForumMain](http://wiki.gnewsense.org/ForumMain/ForumMain)

---

### Post by PriceChild on 2007-02-15
AFAIK nvidia will not be in feisty by default?

---

### Post by v8YKxgHe on 2007-02-15
Canonical/Ubuntu have decided not to include binary graphics drivers by default, instead they will be much easier to install, if the user wishes.

---

### Post by PriceChild on 2007-02-16
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```That's pretty simple IMO...

---

### Post by ihavenoname on 2007-02-16
I was actually referring to Gnewsense..not Feisty. But I decided not to go there because in the end I will have to mess up the kernel anyways. (Wifi and video card). The reason I was considering it was that sometimes, the extra stuff put in the kernel by Ubuntu would mess up here. (The rt2500 drivers aren't compatible w/ network manager so I have to use ndiswrapper but that caused problems.

---

