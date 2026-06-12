---
title: "Ardour 2.8.1"
date: 2009-07-18
forum: Ubuntu Studio
---

### Post by roaldz on 2009-07-18
Hey all,

I made an Ardour 2.8.1 deb using Checkinstall. It´s got LV2 support. I thought I could share it, because I couldn´t find a .deb.
Made with 64studio 3.0beta

[http://www.yourfilehost.com/media.php?cat=other&file=ardour_2.8.1_1_i386.deb](http://www.yourfilehost.com/media.php?cat=other&file=ardour_2.8.1_1_i386.deb)


Roald

---

### Post by Stochastic on 2009-07-18
Great!  Care to share the .deb source package so others could build 64-bit debs or modify to their liking?

Oh, and does it have VST support compiled in?

---

### Post by roaldz on 2009-07-20
> **Stochastic said:**
> Great!  Care to share the .deb source package so others could build 64-bit debs or modify to their liking?

Oh, and does it have VST support compiled in?

That would be the same as sharing the source tarball, which you can grab from their website. You´d still need the dependencies.
It´s compiled without VST support. Maybe i´ll see if I can fix a VST-enabled version..

Roald

---

### Post by Stochastic on 2009-07-21
> **roaldz said:**
> That would be the same as sharing the source tarball, which you can grab from their website. You´d still need the dependencies.
It´s compiled without VST support. Maybe i´ll see if I can fix a VST-enabled version..

Roald

Sorry, I should have clarified, I mean can you share your diff.gz file from which the i386 .deb is built from?  This is not the upstream source tarball, but rather the changes you make to it in the debian subdirectory.

It's not that important since Karmic's repositories have 2.8 available, but I'd just like to see any improvements you've made etc...

---

### Post by roaldz on 2009-07-24
I didn´t make any improvements (that I know of:P). Just used checkinstall to compile it, to keep things straight with dpkg/apt. I thought someone could benefit from my .deb, because I couldn´t find an LV2-enabled .deb myself.

Roald

---

### Post by Grishka on 2009-07-25
some guy has Ardour 2.8.1 in [his repo](http://philip.magicalforest.se/). it's compiled with LV2, but without VST support. you're advised to add his deb-src line to your sources.list, apt-get source ardour, and edit debian/rules to your liking. also, please don't distribute packages with VST support, as it stand against Steinberg's license (that's why, for example, LMMS has a separate package for VST support). it's ok to compile with VST support for your personal use, though.

---

### Post by roaldz on 2009-07-25
Isn´t this VST-hassle solved with the FST headers?

I´m currently compiling ardour 2.8.2. Will post deb.

---

### Post by roaldz on 2009-07-25
Ardour 2.8.2:

[http://www.yourfilehost.com/media.php?cat=other&file=ardour_2.8.2_1_i386.deb](http://www.yourfilehost.com/media.php?cat=other&file=ardour_2.8.2_1_i386.deb)

Compiled with:
sudo checkinstall scons LV2=1 PREFIX=/usr -j3 install

Cheers!

---

