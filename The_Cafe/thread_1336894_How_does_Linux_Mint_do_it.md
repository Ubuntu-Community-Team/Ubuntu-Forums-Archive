---
title: "How does Linux Mint do it?"
date: 2009-11-25
forum: The Cafe
---

### Post by ninjapirate89 on 2009-11-25
How do they manage to squeeze in (almost?) everything that comes with Ubuntu and the stuff that comes with Mint and all the restricted extras onto one cd? It doesn't seem possible.

---

### Post by earthpigg on 2009-11-25
a lot of the mint-specific stuff ***replaces*** something on ubuntu...

remove add/remove programs, add mintInstall.

rinse, repeat.

---

### Post by ninjapirate89 on 2009-11-25
> **earthpigg said:**
> a lot of the mint-specific stuff ***replaces*** something on ubuntu...

remove add/remove programs, add mintInstall.

rinse, repeat.

True, but still. Isn't there very little room left on the ubuntu cd as it is? All those media codecs must take up a good bit of space.

---

### Post by earthpigg on 2009-11-25
about 100mb.

so, who wants to install ***both*** in a vm and pipe the output of a list of packages installed into diff to discover whats up with this?

---

### Post by Exodist on 2009-11-25
> **ninjapirate89 said:**
> True, but still. Isn't there very little room left on the ubuntu cd as it is? All those media codecs must take up a good bit of space.
The IMG on the CD is heavily compressed. Not actually 700MB. More like close to 2GB uncompressed.

---

### Post by MaxIBoy on 2009-11-25
> **earthpigg said:**
> about 100mb.

so, who wants to install ***both*** in a vm and pipe the output of a list of packages installed into diff to discover whats up with this?
No need to install them in a VM. You just mount the ISOs with loopback, mount a single shared folder on top of both with unionfs, chroot, and run dpkg -l.

---

### Post by ninjapirate89 on 2009-11-25
> **earthpigg said:**
> about 100mb.

so, who wants to install ***both*** in a vm and pipe the output of a list of packages installed into diff to discover whats up with this?

I actually just finished installing Mint 8 RC1 in VBox. I can get a list of all installed packages from Synaptic.

Edit -> > No need to install them in a VM. You just mount the ISOs with loopback, mount a single shared folder on top of both with unionfs, chroot, and run dpkg -l.
Nevermind then. :D 
I can do that for the Mint ISO if you give instructions.

---

### Post by 3rdalbum on 2009-11-25
Ubuntu comes with multiple languages on the one CD. Only one gets installed to your hard drive, but the other language packs are still taking up room on the disc. I think Mint removes those to get some space.

---

### Post by Uncle Spellbinder on 2009-11-25
Extremely nice distro. Triple booting now, Mint, Karmic and 7. 

What's really nice is none of the scrambling to get typical multimedia needs met. Already set and ready to go. DVD, audio/ video (mp3/avi/DivX...), browser plugins, Java...all installed automatically. On Ubuntu Karmic, my plugins  for Firefox had the default Mozilla plugin. That's it. A fresh install of Linux Mint and here's what I see in SeaMioonkey (sharing the Firefox plugins)...

**Generated:** Wed Nov 25 2009 22:44:49 GMT-0500 (EST)
**User Agent:** Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.4) Gecko/20091017 SeaMonkey/2.0
**Build ID:** 20091017083424
 
**Installed Plugins:** (6)
- DivX Browser Plug-In
- mplayerplug-in is now gecko-mediaplayer 0.9.8
- QuickTime Plug-in 7.4.5
- RealPlayer 9
- Shockwave Flash
- Windows Media Player Plug-in

Lots of other nice Mint-specific stuff to play with. Very nice distro.

---

