---
title: "Gimp GIT version"
date: 2013-03-17
forum: Ubuntu Development Version
---

### Post by Rukiri on 2013-03-17
I've never had issues compiling software on any distro or windows/osx but gimp just does not want to be compiled...
Has anyone successfully compiled gimp's git ver on ubuntu 13.04?

---

### Post by mc4man on 2013-03-17
pretty simple, you just need newer gegl & babl.
Am attaching the set of commands I use here, feel free to use as is or adjust install prefix.
If adjusting prefix make sure to change all instances alike.
(- I install all to /opt/gimp-git, not hard to create a .desktop & or alias to run from there

If you happen to have a static ffmpeg in path then remove before build, can be returned after

If any questions ask, some comment in attached

Edit - had 1 small miss in attached - replaced (the ./configure on gegl if needed had wrong prefix, also adjusted checkinstall for pkgname
(should have just posted in thread, started but the autosave was being a pita for some reason

---

### Post by Rukiri on 2013-03-17
Hey thanks man! I'll let you know if it works, I just got some other stuff to get installed.. (Getting DVD/Blu-ray playback was the first thing on my list since vlc 2.0 is borked without extra codecs)

---

### Post by mc4man on 2013-03-17
I hope you got revised attached, was copying out of file from old install & decided to change prefix=, missed one...

---

### Post by mc4man on 2013-03-17
Forgot something - 
If one wants they can keep both the repo & git version - in that case & if using checkinstall then change the pkgname - 
ex.
```
sudo checkinstall --backup=no --deldoc=yes --fstrans=no --deldesc=yes --delspec=yes --pkgversion=2.10 --pkgname=gimp-git
```

---

### Post by Rukiri on 2013-03-17
Yes, and gimp seems to be compiling this time around.
But I've been hanging on "Copying files to the temporary directory..." for five minutes with gimp, that normal?

---

### Post by mc4man on 2013-03-17
> **Rukiri said:**
> Yes, and gimp seems to be compiling this time around.
But I've been hanging on "Copying files to the temporary directory..." for five minutes with gimp, that normal?

5 min - no, never that long here
if it doesn't complete soon then  ctrl+c the terminal & try again - use the checkinstall command in post 5
(or just use sudo make install

---

### Post by Rukiri on 2013-03-17
Everything installed correctly however I do not list gimp actually being installed...

---

### Post by mc4man on 2013-03-17
> **Rukiri said:**
> Everything installed correctly however I do not list gimp actually being installed...

see screen, I have the repo gimp & gimp-git installed

Here I run from a launcher icon, if you need a .desktop, ask..

---

### Post by Rukiri on 2013-03-17
I think I found the problem and I probably just missed it as it's 2AM..
Git version of babl seems to be 0.10 but gimp 2.10 requires 0.11, hmm, anyway to fix this?
> checking for BABL... no
configure: error: Package requirements (babl >= 0.1.11) were not met:

Requested 'babl >= 0.1.11' but version of babl is 0.1.10



---

### Post by mc4man on 2013-03-17
> **Rukiri said:**
> I think I found the problem and I probably just missed it as it's 2AM..
Git version of babl seems to be 0.10 but gimp 2.10 requires 0.11, hmm, anyway to fix this?

No - the git version is actually 0.1.11 (never changed my checkinstall from past as the package name is irrelevant when compiling against.
Not sure what you're up to, likely you ran a configure on gimp but didn't export paths
see screen for babl version

(the 13.04 gegl repo version is good enough, the purpose of using a rebuilt gegl would be to configure/enable as seen fit.

---

