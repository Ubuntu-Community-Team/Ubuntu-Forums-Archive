---
title: "Netinstall problem"
date: 2010-02-04
forum: Server Platforms
---

### Post by tomeq on 2010-02-04
HI everyone!

I'm trying to solve some sort of really annoying problem concerning netinstall (PXE boot and so on) using Ubuntu 8.04 or latest 9.10 edition... 

It works really well and the installation process goes on good until installation of packages after tasksel ran. When I'm asked about server role I mostly choose nothing or just "OpenSSH server" to get as clean as possible installation after all. 

But, this strategy fails suprisingly during netinstall - whenever "language-pack-gnome-en" package is being installed (why and what for for god's sake?!) I'm getting whole bunch of useless dependent packages like openoffice.org-common or libsnd and hundreds of other X/GNOME stuff.... 

I don't need such packages. I tried everything to get rid of it: changing Ubuntu version (8.04 and 9.10 - the same), changing apt repository (pl -> de), switching to a different http proxy (I have to use it to get packages from repos), I tried messing with aptitude during "Manual package selection" but it shows that language-pack-gnome-en is selected for removal and shouldn't be taken into install process.. I tried changing locale (Polish -> English, English -> Polish) but no change.

I have no other way to install OS on this poor machine : floppy is out, cdrom is broken, no usb booting is possible. PXE works really nice for me but it seems that all netinstalls are broken... 

Anyone got any clue on that?

---

