---
title: "Stable vs Cutting Edge vs Bleeding Edge || Which one needs more Hard Work ??"
date: 2011-07-26
forum: The Cafe
---

### Post by linuxyogi on 2011-07-26
Hi,

I wonder which is more difficult ? Is maintaining a Bleeding Edge distro like Gentoo or Arch 

more hectic in comparison to maintaining stable  Distros like Debian stable or Cutting 

Edge distros like openSUSE, Sabayon, Fedora, Ubuntu normal releases ?

I can only guess & I think the Bleeding Edge distros like Arch & Gentoo are more difficult to maintain coz the maintainers need to keep on updating stuff all the time while the stable releases mainly receives security updates.


What do you think ?

---

### Post by Dangertux on 2011-07-26
I think it depends, I would imagine each are very hard work. They are each very different goals.

In terms of Bleeding Edge -- you are constantly packing the newest technology into your distro, so of course it's going to be more hectic in that respect, the same sort of applies to cutting edge but to a lesser extent.

Stable distros have their own set of challenges. In that they must be stable, which is not always as easily achieved as one would imagine. Security risks need to be mitigated, hardware needs to be supported properly (not just sorta supported, actually supported), features need to be implemented and frozen , etc. The fact that major production systems depend on these stable distros dictates that a great deal of effort go into them.

So is either of them more work to maintain? I would imagine they are all difficult just that each presents a different challenge.

---

### Post by unknownPoster on 2011-07-26
Gentoo is not bleeding edge. That's a common misconception. In fact, in many cases Ubuntu is more up to date. You have to enable the testing repos like any other "normal" distribution.

---

### Post by handy on 2011-07-26
Call Arch what you like, I find it to be the easiest lowest maintenance OS that I've ever used in pushing 26 years of playing with the things.

---

### Post by LowSky on 2011-07-26
> **handy said:**
> Call Arch what you like, I find it to be the easiest lowest maintenance OS that I've ever used in pushing 26 years of playing with the things.

I have to agree. My netbook that has been running arch for a while now is pretty amazing and I don't have upgrade guilt like I get with Ubuntu from time to time. LOL

I'm thinking of moving my desktop to Arch sometime soon. The only reason I'm still with Ubuntu is the warm fuzzy feeling it gives me from a half decade of use.

---

### Post by krapp on 2011-07-26
> **handy said:**
> Call Arch what you like, I find it to be the easiest lowest maintenance OS that I've ever used in pushing 26 years of playing with the things.

Just to make sure we all understand correctly, by lowest maintenance you mean upgrading every week?

---

### Post by cgroza on 2011-07-26
Just installed Arch (the second time) and I have to say I love the feeling of getting a tty and then throwing in some bare bones Xfce package and adding everything by your self. :p

Bleeding edge is quite fun despite having some problems with the network connection.

---

### Post by Syndicalist on 2011-07-27
Using Firefox 3.6 is the biggest thing that slowed me down compared to Firefox 4.0 or 5.0....and I dislike Chromium, though it was admittedly faster when firefox was sub-bar in Linux. The fact that Ubuntu was so far behind the times was one thing that caused me to move to a distro that supports Debian Testing.

Sometimes the older versions are just slower, and using outdated software means a slower work experience. 

Then again, sometimes not. It depends on where you are in the development of the apps you use most....occasionally they regress and get slower.

---

### Post by 2F4U on 2011-07-27
I had Arch for a considerable time installed on my desktop. What finally drove me away from it was their refuse to implement any kind of package signing just because they consider it as not important. This imposes a considerable risk to my machine, because any malicious repository server could provide my machine with manipulated packages that do any kind of harm to me.

---

### Post by kaldor on 2011-07-27
> **2F4U said:**
> I had Arch for a considerable time installed on my desktop. What finally drove me away from it was their refuse to implement any kind of package signing just because they consider it as not important. This imposes a considerable risk to my machine, because any malicious repository server could provide my machine with manipulated packages that do any kind of harm to me.

This is probably the biggest reason I do not use Arch and recommend others not use Arch. I think there are a lot of security issues dealing with packages and repositories compared to Ubuntu and other distros. 

@ Krapp:

Arch is low maintenance because you install it once, then never install again. It's a rolling release, meaning new packages are always rolled in. You can install Arch right now and still have the same installation in 5 years from now, except with fully up to date packages. Basically, no messing around with upgrades. 

For example, you will not need to upgrade when the next GNOME is released. When doing your normal updates, you will find a new version of GNOME available, etc, just as if you are getting security updates on Ubuntu.

---

### Post by Syndicalist on 2011-07-27
It could be why the group Anonymous, known for their cyber-terrorism, bases their live CD with Tor and p2p and I2p installed by default on Chackra which is based on Arch? When you log in you are already using tor, and presumably others are using your system as well....at least your browsers to the extent that Tor allows.

---

### Post by el_koraco on 2011-07-27
> **Syndicalist said:**
> It could be why the group Anonymous, known for their cyber-terrorism, bases their live CD with Tor and p2p and I2p installed by default on Chackra which is based on Arch? When you log in you are already using tor, and presumably others are using your system as well....at least your browsers to the extent that Tor allows.

Wut?

---

### Post by kaldor on 2011-07-27
> **Syndicalist said:**
> It could be why the group Anonymous, known for their cyber-terrorism, bases their live CD with Tor and p2p and I2p installed by default on Chackra which is based on Arch? When you log in you are already using tor, and presumably others are using your system as well....at least your browsers to the extent that Tor allows.

Doubtful. A liveCD can't be updated.

---

### Post by linuxyogi on 2011-07-27
I am tired of distro hopping. I will be using Lucid till it reaches end of life. Just upgrading 

what I want. 

FF, Thunderbird : Using their precompiled version.

mplayer2, VLC, Gnome Mplayer  : Installed from source

Deluge, Pidgin : Using their PPAs.

---

### Post by LowSky on 2011-07-27
> **2F4U said:**
> I had Arch for a considerable time installed on my desktop. What finally drove me away from it was their refuse to implement any kind of package signing just because they consider it as not important. This imposes a considerable risk to my machine, because any malicious repository server could provide my machine with manipulated packages that do any kind of harm to me.

I love when people bring up horrible scenarios, but name one time this occurred with a user using only the Arch repos, and none of the third party ones.

Read this about Arch and package signing:

[http://www.toofishes.net/blog/real-story-behind-arch-linux-package-signing/](http://www.toofishes.net/blog/real-story-behind-arch-linux-package-signing/)

People forget that Arch is a distro with no corporate ties. All it's development is community based.

---

### Post by unknownPoster on 2011-07-27
> **LowSky said:**
> I love when people bring up horrible scenarios, but name one time this occurred with a user using only the Arch repos, and none of the third party ones.

Read this about Arch and package signing:

[http://www.toofishes.net/blog/real-story-behind-arch-linux-package-signing/](http://www.toofishes.net/blog/real-story-behind-arch-linux-package-signing/)

People forget that Arch is a distro with no corporate ties. All it's development is community based.

But what can people do if they can't wear their tinfoil hats?

---

### Post by FreeTheBee on 2011-07-27
For me personally, maintining Arch is less work than Ubuntu. Since, I use a fair amount of software that is either outdated or not at all in the ubuntu repositories. In arch these tools are usually available either in the official repositories or in the AUR, which saves me the time of searching for ppa's. Not needing to upgrade is a time saver as well. Of course occasionally bleeding edge bites me in the *** and forces me to spend some time fixing things. This is very rare though and a temporary downgrade usually does the job. 

For developers I don't really know, but the fact that Arch tries to keep it simple, stupid, should be somewhat of a time saver for them as well. They also don't spend too much effort developing things for Arch only, like canonical does for Ubuntu.

---

### Post by Syndicalist on 2011-07-28
> **kaldor said:**
> Doubtful. A liveCD can't be updated.

What part is doubtful? A CD image cant be changed, though it can be altered while its loaded into ram. You can also boot an image from USB that uses settings that are saved to a dedicated portion of the drive, and these can be "updated" sort of. The image itself does not change, especially if its a live CD.

But isnt there still security issues with a live CD that operates like that?

I plopped the live CD in, and my location is completely hidden, if I choose to use it.

---

### Post by 1saac on 2011-07-28
> **LowSky said:**
> I love when people bring up horrible scenarios, but name one time this occurred with a user using only the Arch repos, and none of the third party ones.
Can't name one, but then again, without package signing there's no real way to know if it's happened.  Of course, I can't name one time when a seat belt has saved my life either, so that means I needn't worry about wearing one, right?

---

### Post by Thewhistlingwind on 2011-07-28
> **Syndicalist said:**
> It could be why the group Anonymous, known for their cyber-terrorism, bases their live CD with Tor and p2p and I2p installed by default on Chackra which is based on Arch? When you log in you are already using tor, and presumably others are using your system as well....at least your browsers to the extent that Tor allows.

Uhhhh.......

> **el_koraco said:**
> Wut?

---

