---
title: "Terrible oblivion performance"
date: 2011-01-30
forum: Wine
---

### Post by Dustin2128 on 2011-01-30
I installed oblivion via wine 1.3 a few minutes ago, and I'm getting horrible performance for my graphics card. I've got a GeForce 9600 GT 512MB which is *far **far ***more powerful than the recommended GeForce 6800. I created a direct3D.reg file, set the video memory and adjusted off screen render mode to pbuffer. I've gotten literally no change from default settings. Ideas?
EDIT:Next to no change in performance when swapping from ultra high to very low detail settings. Something's screwey...

---

### Post by djeikyb on 2011-01-30
I have a puny Radeon x300, but I have drastically better performance after adding the xorg-edgers ppa and adding myself to the video group. Keep in mind it's not a stable release. YMMV.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

[quote="xorg crack pushers"]Packages for those who think development versions, experimental and unstable are for old ladies. We want our crack straight from upstream git! Well, straight, we want it built and packaged so we don't need to know what we're doing, except that we will break our X and put our computers on fire.[/quote]

---

### Post by Dustin2128 on 2011-01-31
> **djeikyb said:**
> I have a puny Radeon x300, but I have drastically better performance after adding the xorg-edgers ppa and adding myself to the video group. Keep in mind it's not a stable release. YMMV.

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
My ubuntu install's kinda completely borked at the moment. Any idea how I'd install under slack?

---

### Post by cwwilson721 on 2011-01-31
You DID read my dri sticky at the "Official-Unofficial Slackware Forum", right? (Look at the slackware homepage/support info to find the name, or message me, I'll let you know)

---

### Post by djeikyb on 2011-02-01
> **Dustin2128 said:**
> My ubuntu install's kinda completely borked at the moment. Any idea how I'd install under slack?Lol. This is rather pertinent. Not that you don't have an interesting question, but these *are* Ubuntu forums..

Anyway, I suspect cwwilson's answer will fix you up best. As far as getting bleeding edge Xorg, I don't know of any pre-built Slackware packages, but it's been a while since I've been in the slack world. You could always download the source and ./configure; make; make install. I don't remember being very successful doing that back in Slackware 8 though. If you find something, post it here for posterity!

EDIT: Clicked to your blog, that kernel patch for tty task groups sounds pretty sweet. Did you apply it under Ubuntu or just Slackware? /OT

---

### Post by Dustin2128 on 2011-02-06
> **djeikyb said:**
> 
EDIT: Clicked to your blog, that kernel patch for tty task groups sounds pretty sweet. Did you apply it under Ubuntu or just Slackware? /OT
Slack. </ot>

---

