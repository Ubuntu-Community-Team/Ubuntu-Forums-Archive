---
title: "removing excess component packages"
date: 2005-09-29
forum: Repositories &amp; Backports
---

### Post by david.birch on 2005-09-29
Hi, i can't quite figure if i will completely break my system, but how does one remove excess component packages i.e. the xserver-xorg-driver-XXXX ?
When i ask to remove in Synaptic, it also wants to remove x-window-system-core & xserver-xorg - which i am guessing will be by-by x...

Am i missing how to do this? otherwise, i'm sorta wondering if a 1-way dependency thing would be good for pkg mgmt? (even if upgrades of the core - like xserver-xorg reinstall all the excess stuff again, or maybe removed components are marked as optional in upgrades etc - it just seems alot of extra meggage to be flying around)

I am using the latest Breezy CD, and there are updates most days, most of which i really don't need - and it is a pain to un-check all the excess crap everytime i run the update. Is there a way similar to M$ Update that you can ask for updates to be hidden?

thx
Dave

---

### Post by heimo on 2005-09-29
x-window-system-core is a metapackage and you can remove it without removing any of its dependencies - and remove any of the dependencies independently
[http://packages.ubuntu.com/breezy/x11/x-window-system-core]("http://packages.ubuntu.com/breezy/x11/x-window-system-core")

It's the same with ubuntu-desktop and other metapackages which are there for handling dependencies. It's a good idea to install major metapackages before dist-upgrading.

---

### Post by david.birch on 2005-09-30
ah, yes. i see missed the bolded "Dummy Package" words. apologies, it is still only first few days into my transition from Gentoo...

---

### Post by david.birch on 2005-09-30
*Warning* not sure if this was caused by the fact i am running breezy, but x was broken after i did uninstall these meta-packages. It only stated it was creating .xauth, and froze - no Xorg log or .xsession-errors.  I confirmed by re-running apt-get install xserver-xorg, and it was all ok again. I am pretty sure i only uninstalled what i didn't need (i just moved from gentoo, where i only specified what i needed, so fairly certain), so maybe there are some deps with these packages... So i guess i stick to grabbing all the drivers from now on...

---

