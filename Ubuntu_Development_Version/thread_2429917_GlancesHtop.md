---
title: "Glances/Htop"
date: 2019-10-24
forum: Ubuntu Development Version
---

### Post by Frogs Hair on 2019-10-24
Glances and htop are now snap packages only or is it just too early in the cycle to get them via apt ?

---

### Post by cruzer001 on 2019-10-25
Hello Frogs Hair

I'm guessing that we get to test snap packages this cycle.

But after the developmental cycle is over deb packages will be available from "pkgs.org" if nowhere else.  An example:  Supposedly the chromium-browser is now only available as a snaps package in 19.10, but pkgs.org has the deb package for 19.10

Thats what I'm seeing.

---

### Post by PaulW2U on 2019-10-25
I'm not understanding your point Frogs Hair as I see both htop and glances in the focal repositories. As neither snap are released by Canonical I don't see how they could ever be part of a widening of snap tests. I doubt that any further applications will be provided as snaps by default with Ubuntu 20.04 being a LTS release.

The Chromium .deb package in both the eoan and focal repositories is a **transitional** package that ensures those upgrading have a path to move from a .deb to a snap. 

From 'apt show chromium-browser'
```
Download-Size: 48.7 kB
APT-Manual-Installed: yes
APT-Sources: http://gb.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
Description: Transitional package - chromium-browser -> chromium snap
 This is a transitional dummy package. It can safely be removed.
 .
 chromium-browser is now replaced by the chromium snap.

```
The browser itself is **not** being provided as a .deb package.

---

### Post by Frogs Hair on 2019-10-25
> [COLOR=#000000]I'm not understanding your point Frogs Hair as I see both htop and glances in the focal repositories.[/COLOR] I tried to install both last night and received message in the terminal that they only available as snap, package not found, use sudo snap install glances. I tried again this morning after reading your post and was able to install from apt ???? The packages did not come up in synaptic search either.

---

### Post by PaulW2U on 2019-10-25
I saw this on IRC last night:
[https://irclogs.ubuntu.com/2019/10/24/%23ubuntu-release.html#t17:01](https://irclogs.ubuntu.com/2019/10/24/%23ubuntu-release.html#t17:01)

I'm not sure exactly what it means in relation to the packages not being in synaptic but something relating to cnf (command-not-found) was missing for the focal release. :confused:

---

