---
title: "Why rox-2.5.1?"
date: 2008-11-16
forum: The Cafe
---

### Post by sirdilznik on 2008-11-16
I'm just curious, why does *buntu have the 2.5.1 version of ROX-Filer (best dang file manager on the planet) in the repositories?  The most recent version is 2.8 and the latest stable is 2.7.1.  Not that there are some mind-numbing new features in the newer versions, but it makes me wonder why *buntu uses a version that is several years outdated when newer versions exist.  Is there something inherently "evil" about versions >2.5.1?  Will they cause my machine to melt down into a pile of molten metal and silicon?  Well I'm willing to  take the chance and have installed 2.8 manually and it seems stable enough.  Not a real complaint as manual installation was a snap (it's just a ready to go binary), but I keep wondering why the version in the repository is so old.

---

### Post by smartboyathome on 2008-11-16
Its because nobody has bothered to package it. If someone wants it, they package it. Otherwise it goes unmaintained.

---

### Post by niccholaspage on 2008-11-16
This was like Nautilus in Hardy...

---

### Post by init1 on 2008-11-16
> **sirdilznik said:**
> I'm just curious, why does *buntu have the 2.5.1 version of ROX-Filer (best dang file manager on the planet) in the repositories?  The most recent version is 2.8 and the latest stable is 2.7.1.  Not that there are some mind-numbing new features in the newer versions, but it makes me wonder why *buntu uses a version that is several years outdated when newer versions exist.  Is there something inherently "evil" about versions >2.5.1?  Will they cause my machine to melt down into a pile of molten metal and silicon?  Well I'm willing to  take the chance and have installed 2.8 manually and it seems stable enough.  Not a real complaint as manual installation was a snap (it's just a ready to go binary), but I keep wondering why the version in the repository is so old.
What release are you using?

---

### Post by sirdilznik on 2008-11-16
> **init1 said:**
> What release are you using?

I'm trying out 2.8 right now (I still have the 2.5.1 version installed through the repos around too).  Works fine so far.  

I may have to see about learning to make proper deb packages and maybe I'll make a proper deb to update the repos myself.

---

### Post by Eclipse. on 2008-11-16
File a bug on launchpad for it to be synced from debain for jaunty (before december 25th as thats the debian import freeze date) and the latest version will be in jaunty.

---

### Post by kerry_s on 2008-11-16
> **sirdilznik said:**
> I'm just curious, why does *buntu have the 2.5.1 version of ROX-Filer (best dang file manager on the planet) in the repositories?  The most recent version is 2.8 and the latest stable is 2.7.1.  Not that there are some mind-numbing new features in the newer versions, but it makes me wonder why *buntu uses a version that is several years outdated when newer versions exist.  Is there something inherently "evil" about versions >2.5.1?  Will they cause my machine to melt down into a pile of molten metal and silicon?  Well I'm willing to  take the chance and have installed 2.8 manually and it seems stable enough.  Not a real complaint as manual installation was a snap (it's just a ready to go binary), but I keep wondering why the version in the repository is so old.


are you using a old ubuntu version, you know they use snap shots at the time of release. it only receives security updates after that.

i'm using debian lenny, the version is 2.7.1

---

### Post by init1 on 2008-11-16
> **sirdilznik said:**
> I'm trying out 2.8 right now (I still have the 2.5.1 version installed through the repos around too).  Works fine so far.  

I may have to see about learning to make proper deb packages and maybe I'll make a proper deb to update the repos myself.
Oh I meant Ubuntu release. Is this old version in Intrepid, Hardy, or an older release?

---

### Post by kernelhaxor on 2008-11-16
> **init1 said:**
> Oh I meant Ubuntu release. Is this old version in Intrepid, Hardy, or an older release?

I'm using Intrepid .. I too see version 2.5.1 .. chk out the attached screenshot ..
what version do you see?

---

### Post by niccholaspage on 2008-11-16
Ubuntu isn't a Rolling Release Distro... It doesn't always have the latest and greatest.

---

### Post by Grant A. on 2008-11-16
If you REALLY need bleeding edge software, just compile the source yourself. It's not hard to do and is very easy.

---

### Post by doorknob60 on 2008-11-16
> **niccholaspage said:**
> Ubuntu isn't a Rolling Release Distro... It doesn't always have the latest and greatest.

Yeah, but Ubuntu takes snapshots from Debian Sid, right? Debian has a newer version than that, do the Ubuntu devs only take the main packages or something (like kernel etc)?

And +1 to the compiling, that's what I did in Ubuntu when new version of Pidgin and stuff came out, but I don't need to much any more because things generally get updated pretty fast in Arch :-)

---

### Post by Grant A. on 2008-11-16
> **doorknob60 said:**
> Yeah, but Ubuntu takes snapshots from Debian Sid, right? Debian has a newer version than that, do the Ubuntu devs only take the main packages or something (like kernel etc)?

And +1 to the compiling, that's what I did in Ubuntu when new version of Pidgin and stuff came out, but I don't need to much any more because things generally get updated pretty fast in Arch :-)

Who says it has to be from Debian? You could always make your own .deb and become a maintainer.

---

### Post by sirdilznik on 2008-11-16
> **Grant A. said:**
> If you REALLY need bleeding edge software, just compile the source yourself. It's not hard to do and is very easy.

Bleeding edge is one thing but 2.5.1 is several years old, even 2.8 has been out for almost half a year.  Anyway as I stated before there is no need to compile since a ready to run binary is available and it works just fine.  It just seemed weird that a fairly popular file manager hadn't been updated in the repos in about 2 years.

I'm on Intrepid BTW.

---

### Post by handy on 2008-11-17
I only removed rox-2.8-1 off my Arch system an hour or so ago.

I tried it out, its way of doing things doesn't really appeal to me.

I'd like to try the Gentoo file manager, which was inspired by Jonathon Potter's, Directory Opus 4.* which I used to use on the Amiga.  I loved DOpus, best dirutil I have ever used. 

Gentoo is not a clone, but it is similar.  Not available in the Arch repo's (64bit anyway) at the moment.

The reason it can get away with the name, is that it has been around longer than the Gentoo distro' & the guy who developed the dirutil gave the distro' people the ok to use the name of that penguin too. :-)

***[Edit:]**  While I was working on learning how to make an Arch package of Gentoo, I discovered [**[I]_Worker_***]("http://www.boomerangsworld.de/cms/worker/index?lang=en"), which is a self proclaimed DOpus clone.  I've installed it & it looks at this early stage like it might suit me fine.[/I]

---

