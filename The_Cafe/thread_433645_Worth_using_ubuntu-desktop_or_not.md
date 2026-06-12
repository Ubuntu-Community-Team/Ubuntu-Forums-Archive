---
title: "Worth using *ubuntu-desktop or not?"
date: 2007-05-05
forum: The Cafe
---

### Post by dgorchak on 2007-05-05
I have one problem which terrifies me for a long time: to be or not to be ... erm: to use or not to use "*ubuntu-desktop" metapackage (as for me, kubuntu-desktop)?

Not boasting, I don't really like many applications that are included in kubuntu-desktop or ubuntu-desktop metapackages: I prefer aptitude instead of Adept or Synaptic, I prefer lightweight Psi and licq instead of Kopete, Claws-Mail instead of KMail, rtorrent vs anything else and so on... Allthough I'm a KDE fanboy, I'm not  a madman to use Qt-only or GTK-only apps.

I also don't have any Bluetooth devices or printers at home, so I understand that keeping all applications that depend on kubuntu-desktop isn't a good idea, but I also suppose that removing kubuntu-desktop will cause many problems with updating and dist-upgrading my system.

But I like Ubuntu for keeping a sane level of bleeding-edge apps combined with great stability (for me it was the reason to change Debian etch/sid "zoo" in my system for Ubuntu).

I suppose this problem is more for discussion than for solving such a dilemma, that's why I post here... What is better to do - switch to Debian back, or use some other distro like Arch? Or maybe it's possible to assure developers to create some package like *ubuntu-desktop-minimal? (not like ubuntu-minimal that we have now)

---

### Post by FoolsGold on 2007-05-05
I've removed the ubuntu-desktop metapackage and I'm still posting. It really doesn't mean much, at least from what I've seen. I was unable to remove Gaim without also removing ubuntu-dekstop (using Pidgin now so Gaim was irrelevant). Nothing broke.

---

### Post by dgorchak on 2007-05-05
Removal of kubuntu-desktop causes apt-get to produce much junky output (suggesting autoremoval of many packages, allthough I still need them)... so it's not the right way, I suppose...

---

### Post by mech7 on 2007-05-05
yeah lol i needed to remove it too when i was deleting GAIM.. kinda freaked me out that it wanted to remove desktop, but it took the chance and it it still running :D

---

### Post by dgorchak on 2007-05-05
I used to remove kubuntu-desktop a while ago, making system identical to my previous Debian installation... but I'm afraid to get some bugs connected with removal of this package...

Hm... at least maybe it's worth trying again

---

### Post by dspari1 on 2007-05-05
Just remember to reinstall (k)ubuntu-desktop before updating distros.

---

### Post by use a name on 2007-05-05
kde-core would be just the package for you.

---

### Post by SectionThree on 2007-05-05
> **dspari1 said:**
> Just remember to reinstall (k)ubuntu-desktop before updating distros.
If you forget, it will be reinstalled for you. Don't forget to remove it again!

---

### Post by dspari1 on 2007-05-05
> **SectionThree said:**
> If you forget, it will be reinstalled for you. Don't forget to remove it again!

Does it automaticly detect whether you are using ubuntu, kubuntu, edubuntu, and xubuntu?

---

### Post by SectionThree on 2007-05-05
Probably in one of those hidden .conf files I never look at...

---

### Post by dgorchak on 2007-05-06
> **use a name said:**
> kde-core would be just the package for you.
Thanks, I think that's a good idea

---

### Post by dgorchak on 2007-05-06
> **SectionThree said:**
> If you forget, it will be reinstalled for you. Don't forget to remove it again!
Even using apt-get or aptitude?

---

### Post by SectionThree on 2007-05-06
Probably not. Nothing's automatic when you do it manually!

---

