---
title: "Slow 12.04 fallback"
date: 2012-09-16
forum: The Cafe
---

### Post by Duncan J Murray on 2012-09-16
I posted earlier in the year about upgrading my ancient, but main, laptop from 12.04...

[http://ubuntuforums.org/showthread.php?t=2010487](http://ubuntuforums.org/showthread.php?t=2010487)

There were lots of good suggestions, but I thought I'd try an in-situ upgrade of 10.04 to 12.04.1 fallback.  The result is functional, but very sluggish.  Everything seems to have slowed doen: bootup/opening apps/switching windows/workspaces/web browsing and even editing libreoffice impress files.  It's a split second here and there, but enough to make the experience less pleasant.

So I was thinking of solutions - I use my laptop for web/office/mutt/org-more/presentations on external projectors/rhythmbox with a large collection/shotwell, and that's probably it.

I was thinking options:

cruchbang? 12.04 mate? linux mint mate? debian+repos? centos (but not that keen on rpm) xubuntu?

to be honest would like somehing as fast and as stable as 10.04, but with modern apps and continuing updates.

I've given crunchbang a whirl on the live cd, and find it excellent/fast/efficient.  Just not sure about leaving gnome...  Debian looks really appealing, but not sure I can configure it to run latest libreoffice/firefox and all media codecs and (non free)drivers.  I'm not massively keen on the set up of xubuntu or lubuntu, though I'm sure I can configure them more like G2.  Same goes for mint.

Ideas appreciated!

---

### Post by snowpine on 2012-09-16
What are your hardware specs? It's hard for me to make a recommendation without knowing that. :)

Personally I use Fuduntu on my netbook, it uses Gnome 2 (comparable to Ubuntu 10.04) but is a "rolling release" with the latest applications.

---

### Post by mips on 2012-09-17
> **Duncan J Murray said:**
> 
to be honest would like somehing as fast and as stable as 10.04, **but with modern apps and continuing updates**.

**I've given crunchbang a whirl** on the live cd, and find it excellent/fast/efficient.  Just not sure about leaving gnome...  Debian looks really appealing, but not sure I can configure it to run latest libreoffice/firefox and all media codecs and (non free)drivers.  I'm not massively keen on the set up of xubuntu or lubuntu, though I'm sure I can configure them more like G2.  Same goes for mint.

Ideas appreciated!

Crunchbang and Debian have older apps but both are fast and stable. You could always go with the newer testing release of Crunchbang 11.

As a old G2 user xfce suites me just fine.

Other distros to look at are fedora, opensuse & arch I would say.

Or why don't you do a clean netinstall of 12.10 with xfce or G3...

---

### Post by ssam on 2012-09-17
xfce (or mate if you prefer gnome2 features). ubuntu has a lot of background tasks that you may not need. have a look in top and see what it using cpu and memory (shift+m to sort by memory usage). Then in synaptic remove anything you dont need. I would typically remove ubuntu-one, zeitgeist, accessibility stuff, bluetooth stuff, jockey, unneeded international fonts. you can also reduce what it run in you session.

in firefox there are various things you can do to save cpu power, make flash click to play (flashblock), set gifs to only play onces, noscript, disable the phishing site detection.

Also see if you can upgrade the RAM. that can often make a big difference.

---

