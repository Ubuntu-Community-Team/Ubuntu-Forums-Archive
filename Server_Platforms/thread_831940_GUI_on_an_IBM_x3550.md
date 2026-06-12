---
title: "GUI on an IBM x3550"
date: 2008-06-17
forum: Server Platforms
---

### Post by isecore on 2008-06-17
Hi, I'm helping to setup a Squid-cache at my work. We're using the 64-bit version of Ubuntu 8.04 Hardy Heron (desktop) and there's something funky about setting up X.org under it.

Previously we ran 7.10 Gutsy Gibbon on it and the GUI worked fine, however I talked my supervisors into reinstalling it with 8.04 instead since it's LTS and will receive updates and security fixes longer. I also talked them into going for the 64-bit version since they'll probably add more memory to it later (currently it has 2 gigs of memory).

The machine in question is a rack-mounted IBM x-series, an x3550 to be precise. 8.04 installs, but there's something wonky with X.org and the screen just flickers. The "bulletproof" X doesn't come up at all, and xorg.conf looks very spartan.

We're running the desktop-edition since my superiors insist there needs to be a GUI running. If it was up to me we'd skip that but I'm not in charge there. When we tried installing using the Live-CD it wouldn't boot into a GUI on the cd, it just gave us a flat green screen. Thus we installed using the alternate install CD, which went fine.

However upon reboot, no X.

Unfortunately I can't post the Xorg.conf since it got left at work, but it didn't look right.

The IBM x3550 also is validated to work with 8.04 server edition (according to [this page]("http://www.ubuntu.com/products/whatisubuntu/serveredition/validatedhardware")) but I don't know how that apply to the desktop-edition.

Update: FWIW, the graphics adapter is an ATI ES1000. Of course, a server doesn't need a geforce, but none the less I find it a bit weird that 7.10 identifies it fine but 8.04 doesn't.

---

