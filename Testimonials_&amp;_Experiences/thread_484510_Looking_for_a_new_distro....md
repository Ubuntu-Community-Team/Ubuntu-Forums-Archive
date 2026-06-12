---
title: "Looking for a new distro..."
date: 2007-06-25
forum: Testimonials &amp; Experiences
---

### Post by rillip on 2007-06-25
Now your first thought is probably that this is going to be some Ubuntu bash, but it's not.  I love Ubuntu and I'm keeping it.

I got Ubuntu in an urge to play around with something new.  Now I've completely abandoned Windows, except for a few games that I have a dual boot set up for.

I've got some spare parts (256 meg of ram, athalon xp 1700, 6 gig hard drive, on board video, LAN and sound [no idea of the manufacturer]) and was thinking of setting up some kind of server.

I've considered Ubuntu Server Edition,but I don't think it will be enough of a challenge for me, as I'm pretty used to Ubuntu's CLI.  I'm looking for a disto that's "harder," particularly for new users.

I know a lot of people that use Ubuntu use other distros as well. Right now I'm considering OpenSUSE and Gentoo, are there any other distros anyone can think of that sound like what I'm looking for?

Ubuntu is just too easy! :-D

---

### Post by 5-HT on 2007-06-25
[Arch]("http://archlinux.org"), [Slackware]("http://www.slackware.com/"), and[ Frugalware]("http://frugalware.org/") are quite nice. They'll take some more effort to setup and lack a lot of Ubuntu's GUI config tools (Frugalware has some though), but once done administration is a breeze.
 If you're looking for a server, [Debian]("http://debian.org") stable is a good choice, though it'll be very similar to Ubuntu.

---

### Post by dfreer on 2007-06-25
debian is probably better for a server than ubuntu is, in that aspect.
If you want something HARD, go gentoo :) gentoo pwned me lol

---

### Post by ricrac on 2007-06-25
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)  
Best way to really get a handle on linux. 
If you are comfortable and want to learn I'd recommend it before Gentoo.  Gentoo will be a lot easier after you get the basics done with LFS.

You'll want to complete:
LFS base system
BLFS for gui
CLFS for 32/64 cross compiles
HLFS for security 


Highly recommend you use virtualization. xen,kvm, or vmware (vmserver available in the commercial repos, or use vmplayer and easyvmx)
This way you can use your machine for other things but still spend an hour or two "playing" in your virtual client without ever affecting the stability of the base system.
Vmware is nice because you can use snapshots to undo any changes that mess up your system. And you can do all combos of physical2virtual, virtual2physical and virtual on physical for optional multiboot use.

---

### Post by rillip on 2007-06-25
> **ricrac said:**
> [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)  
Best way to really get a handle on linux. 
If you are comfortable and want to learn I'd recommend it before Gentoo.  Gentoo will be a lot easier after you get the basics done with LFS.

You'll want to complete:
LFS base system
BLFS for gui
CLFS for 32/64 cross compiles
HLFS for security 


Highly recommend you use virtualization. xen,kvm, or vmware (vmserver available in the commercial repos, or use vmplayer and easyvmx)
This way you can use your machine for other things but still spend an hour or two "playing" in your virtual client without ever affecting the stability of the base system.
Vmware is nice because you can use snapshots to undo any changes that mess up your system. And you can do all combos of physical2virtual, virtual2physical and virtual on physical for optional multiboot use.

I didn't understand any of that, so I may very well have to check out LFS. :-D

But looking at the site:

> ALFS :: Automated Linux From Scratch provides tools for automating and managing LFS and BLFS builds.

Isn't that... oxy moronic to the extreme?

As for virtualization, nah, it's just going to be a parts computer, it's not even assembled now.  What's the worst that can happen, I break it?  My main box (Ubuntu/W2k) won't be tinkered with. ;-)

---

### Post by Motoxrdude on 2007-06-25
The hardest would be linux from scratch (name says it all). Try out arch linux, it is a basic linux distro that needs a lot of tinkering. Slackware is another good one.

---

