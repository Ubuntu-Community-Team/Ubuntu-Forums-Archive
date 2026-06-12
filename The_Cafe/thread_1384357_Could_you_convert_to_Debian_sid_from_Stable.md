---
title: "Could you convert to Debian sid from Stable?"
date: 2010-01-18
forum: The Cafe
---

### Post by MasterNetra on 2010-01-18
I know Ubuntu has options in its software sources for things like back-ports and the like. Would Debian have such options to where you could effectively convert the Stable version to Sid? Just wondering.

---

### Post by ~sHyLoCk~ on 2010-01-18
Change repos to sid's and dist-upgrade?

---

### Post by Zoot7 on 2010-01-18
You can enable the Testing/Unstable repositories in Stable and go from there. But the better option IMO, if you know you want to run Testing/Unstable is to install using one of the weekly Testing builds.
[http://cdimage.debian.org/cdimage/weekly-builds/](http://cdimage.debian.org/cdimage/weekly-builds/)

---

### Post by OrangeCrate on 2010-01-18
> **MasterNetra said:**
> I know Ubuntu has options in its software sources for things like back-ports and the like. **Would Debian have such options to where you could effectively convert the Stable version to Sid?** Just wondering.

Sure, but it's not really a simple yes or no answer. Here's a link that will answer any questions you might have (plus a whole lot more)...

[http://www.debian.org/doc/FAQ/index.en.html#contents](http://www.debian.org/doc/FAQ/index.en.html#contents)

(If you're interested in Debian, this doc is worth a solid read from beginning to end.)

---

### Post by MasterNetra on 2010-03-13
> **Zoot7 said:**
> You can enable the Testing/Unstable repositories in Stable and go from there. But the better option IMO, if you know you want to run Testing/Unstable is to install using one of the weekly Testing builds.
[http://cdimage.debian.org/cdimage/weekly-builds/](http://cdimage.debian.org/cdimage/weekly-builds/)

umm which CD image in 1386 folder do I choose for the lastest? I was thinking about cd 42 or 41. Does it really matter? I ask because I'm not sure if all those are the actually installation CD's or if some or a number of them are Debian Repo cd's.

---

### Post by benerivo on 2010-03-13
> **MasterNetra said:**
> umm which CD image in 1386 folder do I choose for the lastest? I was thinking about cd 42 or 41. Does it really matter? I ask because I'm not sure if all those are the actually installation CD's or if some or a number of them are Debian Repo cd's.

The best way to access the weekly builds is from here...
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

Whatever installer cd you use, i'd reccommend not choosing to install the 'graphical environment' (ie. the standard gnome desktop) when installing, and instead you would be left with a command line installation. From there you can change the repositories to unstable and upgrade and install whatever desktop env you want.

---

### Post by MasterNetra on 2010-03-13
> **benerivo said:**
> The best way to access the weekly builds is from here...
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

Whatever installer cd you use, i'd reccommend not choosing to install the 'graphical environment' (ie. the standard gnome desktop) when installing, and instead you would be left with a command line installation. From there you can change the repositories to unstable and upgrade and install whatever desktop env you want.

But I prefer gnome, especially when moving to unfamiliar distros.

---

### Post by benerivo on 2010-03-13
If you install using  the testing cd then you could just do a normal install, and afterwards change your /etc/apt/sources.list to point to unstable. It would involve downloading the testing version of the gnome env, and then the unstable version, which may involve a big download. It won't be unfamiliar (compared to ubuntu), it just may not install easily.

---

### Post by MasterNetra on 2010-03-13
> **benerivo said:**
> If you install using  the testing cd then you could just do a normal install, and afterwards change your /etc/apt/sources.list to point to unstable. It would involve downloading the testing version of the gnome env, and then the unstable version, which may involve a big download. It won't be unfamiliar (compared to ubuntu), it just may not install easily.

Well if apps get updated in Repo in testing I'll stick with testing.

Edit: *Looks at Foresight* Anyone use or played with Foresight Linux?

---

### Post by Zoot7 on 2010-03-13
> **MasterNetra said:**
> umm which CD image in 1386 folder do I choose for the lastest? I was thinking about cd 42 or 41. Does it really matter? I ask because I'm not sure if all those are the actually installation CD's or if some or a number of them are Debian Repo cd's.
Normally the first 2 CDs are plenty, but if you want to install a good load of stuff offline the DVD is quite handy in this regard.
CD1/DVD1 is the installation disk, the rest contain packages only afaik (I normally download the DVD myself).

---

### Post by NightwishFan on 2010-03-13
I am using Sid right now and loving it. I update from Testing all the time by changing sources and dist upgrading. Testing is generally more up to date than Ubuntu, so Sid is not too far ahead. As a tip, if you want a rolling release, but still have more bugs fixed, change your sources to "testing" and not "squeeze". This will rolling release the testing distribution instead of the unstable one.

---

### Post by MasterNetra on 2010-03-13
Eeep! I just remembered. Will Debian Testing have the drivers required to run my wireless hardware? (See Spec's link in sig)

---

### Post by NightwishFan on 2010-03-13
If it works in Ubuntu, then all you have to do is install the required firmware, just search for it here:
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

---

### Post by MasterNetra on 2010-03-14
> **NightwishFan said:**
> If it works in Ubuntu, then all you have to do is install the required firmware, just search for it here:
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

I usually use the STA driver don't know its package though. Andd if I did I wonder what CD it would be on...

---

### Post by MasterNetra on 2010-03-14
Oops apparently I got the BCM43## wrong in my specs, according to the result of lspci it reads as a BCM4312

Edit: There we go corrected it.

---

### Post by snowpine on 2010-03-14
> **MasterNetra said:**
> I know Ubuntu has options in its software sources for things like back-ports and the like. Would Debian have such options to where you could effectively convert the Stable version to Sid? Just wondering.

My 2 cents, keep your nice, stable Lenny install, then install Sidux on a second partition. Sidux is basically stabilized Debian Sid, and it's the fastest install I've ever seen... about 5 minutes!

Best of both worlds. :)

---

### Post by MasterNetra on 2010-03-14
> **snowpine said:**
> My 2 cents, keep your nice, stable Lenny install, then install Sidux on a second partition. Sidux is basically stabilized Debian Sid, and it's the fastest install I've ever seen... about 5 minutes!

Best of both worlds. :)

Don't have Debian Install atm. Still using Ubuntu Karmic, but thinking of moving to a rolling release type of thing.

---

### Post by MasterNetra on 2010-03-15
hmm could Ubuntu be made to behave like a rolling release?

---

### Post by NightwishFan on 2010-03-15
I do not think so. You could constantly target the development releases, but they always use experimental stuff. Sid uses the latest Stable version usually.

---

