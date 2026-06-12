---
title: "Lightweight distro?"
date: 2010-05-05
forum: The Cafe
---

### Post by retro89 on 2010-05-05
I was looking at a laptop with these low specs:
300mhz processor
128mb ram
wifi
2 gb hard drive and sd slot
laptop runs a all day on a battery

Link to laptop: [http://www.yallstore.com/new-7-mini-netbook-laptop-notebook-wifi-windows-2gb-hd-red-p-39112.html](http://www.yallstore.com/new-7-mini-netbook-laptop-notebook-wifi-windows-2gb-hd-red-p-39112.html)

 about $100 dollars on ebay Brand New

What would be a suitable and very useable distro for this machine and has best wifi support?

---

### Post by ajgreeny on 2010-05-05
Puppy & Lubuntu are worth looking at, and also maybe Unity and slitaz.

---

### Post by WinterRain on 2010-05-05
> **ajgreeny said:**
> Puppy & Lubuntu are worth looking at, and also maybe Unity and slitaz.

lubuntu is barely usable on my lappie with 1.2ghz/512 ram. Probably won't run on his. Puppy has a better chance, or do an ubuntu minimal install with openbox. Slitaz might be the best choice though.

---

### Post by murderslastcrow on 2010-05-05
If it's especially old, something like DSL (Damn Small Linux) or Tiny Core Linux will run really well on it. However, those distros are for computers with, like, 32 MB of RAM.

If you have 128 MB of RAM, and I've only tested this with a 400 Mhz CPU, not 300 Mhz, but e17 runs very well on that kind of hardware, and it looks awesome. I suggest you look it up on YouTube if you haven't seen e17, yet. It's sleek, animated, vibrant, and runs on really crappy hardware (the N810 can run it well, for instance).

If you want to do this with Ubuntu, just install the minimal installation, and use apt to install gdm, nm-applet, e17, and a few other things remotely. I'm not sure if Lucid includes an e17 package with an xsession entry, but you can always install another DE instead while you look for ways to install e17 from a GUI.

It's not as hard as it sounds, and it'll be nicer for you as an Ubuntu user to have access to stuff like the Software Center. Rhythmbox runs well on 128 MB of RAM if you don't have too many other programs open- most open source stuff is okay on that much RAM.

But you don't wanna' tax the CPU, so you should look for packages that are a bit less grubbing. That's why I suggest e17- not only is it light on its own, but it doesn't require a separate file manager to handle the desktop, panels, etc. It's all integrated.

I hope that info was useful? There's also SliTaZ, Fluxbuntu (a few versions old :\), MoonOS, OpenGEU (this one uses e17 and ecomorph). This way, if you had a good video card, you could do some basic compiz effects on that computer, too (I don't recommend it, though XD).

There are plenty of options, but the best way to keep it light is to install the packages yourself from minimal. I hope this information helps! TLDR, I know.

---

### Post by snowpine on 2010-05-06
I love how people instantly reply with their favorite distro without actually clicking the OP's link. :)

> **retro89 said:**
> 
Link to laptop: [http://www.yallstore.com/new-7-mini-netbook-laptop-notebook-wifi-windows-2gb-hd-red-p-39112.html](http://www.yallstore.com/new-7-mini-netbook-laptop-notebook-wifi-windows-2gb-hd-red-p-39112.html)


This is a super-cheap ARM-processor netbook with Windows CE flashed to ROM. You will not be able to use most Linux distros on it (you'll need a special version that supports ARM) and you may have difficulty installing it due to BIOS and storage limitations. There is a [huge megathread on 7" ARM netbooks]("http://ubuntuforums.org/showthread.php?t=1349626") that you should definitely read before wasting your time and money on this toy (unless Windows CE fits your needs perfectly). 

My advice? Spend a little extra and get a netbook that [meets the Ubuntu minimum system requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements"). For example, for only $70 more, I found a deal on a Dell Mini 9 at the Dell Outlet; it runs Ubuntu (preinstalled!) like a champ.

To recap: the ARM "netbook" that you are considering will not run Lubuntu, SliTaz, Puppy, etc. It runs Windows CE (barely) and is a glorified Palm Pilot, not a true netbook.

---

### Post by dragos240 on 2010-05-06
The lightest would be a LFS with the most minimal kernel options, without X.

---

### Post by Khakilang on 2010-05-06
I find Lubuntu Lucid Lynx pretty fast. The other will be Crunchbang or Sltaz.

---

### Post by kio_http on 2010-05-06
Lubuntu, Puppy, DSL, and even a slimmed down OpenSuSe.

---

