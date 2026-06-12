---
title: "Ubuntu equivelant of Suse Studio?"
date: 2014-03-12
forum: The Cafe
---

### Post by Tristan_Williams on 2014-03-12
Is there an Ubuntu equivelant of Suse Studio?

If not, why not?

---

### Post by tgalati4 on 2014-03-13
It's probably not in Canonical's interest to make it any easier to spin off custom Ubuntu distros.  I think the SUSE Studio is a neat way to assemble custom distros and I would like to see a Debian flavor of it, but I'm sure it requires some extensive frameworks to make it happen.  Although I am not familiar with the current Ubuntu build process--I'm sure it is quite automated.  The fact that Ubuntu is rebuilt every 6 months is testament to the efficiency of that build process.

---

### Post by mastablasta on 2014-03-13
remastersys, now system imaging. or is suse studio different?

---

### Post by Tristan_Williams on 2014-03-13
> **mastablasta said:**
> remastersys, now system imaging. or is suse studio different?

Yes, it's different.
Basically, you go online, select which packages you want, select from a bunch of configuration options, change any files you feel like, and select from Live system, HDD image, Virtualbox, and a bunch of other formats when building.

---

### Post by lykwydchykyn on 2014-03-13
Debian provides a component called [live-helper](http://live.debian.net/) which allows you to create customized liveboot builds for ISO, USB, HDD and other media.  It's not a web service, just a collection of console utilities, but at it's core it does essentially what Suse studio does.  It works for Debian and Ubuntu, possibly other Debian derivatives as well.

You might also be interested in [instalinux](http://www.instalinux.com), which is a website that lets you build custom liveCDs from about half a dozen distros (including Ubuntu) using a simple HTML form.  It's been around for ages, and it's probably not as customizable as suse studio.

---

### Post by tgalati4 on 2014-03-13
So it looks like the pieces are in place to create a SUSE Studio service for Debian/Ubuntu distros.  When I played with the [Studio]("https://susestudio.com/"), I was quite impressed.  Of course, now with JuJu and service orchestration, the need for spinning discrete distros is going away in favor of spinning up cloud instances of services.  So in a way Studio is a neat solution for an older Use Case--burning a custom distro for installation on a discrete machine.  Now, you can spin up a service in the cloud and just point web clients to it.

---

### Post by forrestcupp on 2014-03-13
> **Tristan_Williams said:**
> Yes, it's different.
Basically, you go online, select which packages you want, select from a bunch of configuration options, change any files you feel like, and select from Live system, HDD image, Virtualbox, and a bunch of other formats when building.

Can't you pretty much do that with the minimal install?

---

### Post by lykwydchykyn on 2014-03-13
> **forrestcupp said:**
> Can't you pretty much do that with the minimal install?

This is a lot more than that.  Take a few minutes and check it out, it's really a pretty neat thing.

---

### Post by Tristan_Williams on 2014-03-13
> **forrestcupp said:**
> Can't you pretty much do that with the minimal install?

Nope. The minimal install requires you to know how to do everything yourself.
Suse studio is a web interface. You choose the packages you want. Set a few settings, and bam, instant custom distro.
Not much skill involved there.

And actually I am running Ubuntu Minimal right now :D

---

### Post by forrestcupp on 2014-03-13
In that case, they really do need something like that for Ubuntu. I tried the minimal install once, and I wasn't happy with how it worked.

---

### Post by Tristan_Williams on 2014-03-13
> **forrestcupp said:**
> In that case, they really do need something like that for Ubuntu. I tried the minimal install once, and I wasn't happy with how it worked.

I can understand being unhappy with it. I for one am overjoyed with it. It is exactly what I want. Well not exactly, but pretty close. 

I think what I want is a happy medium between Ubuntu and Gentoo.
Maybe a completely source based Ubuntu. Kind of like Gentoo, but using Ubuntu repos and framework and all that good stuff.

---

### Post by tgalati4 on 2014-03-13
The original Use Case for Studio was to respin SUSE distros for corporate environments--take off the games and multimedia stuff and just have an all-business, locked-down, company-branded distro that you could burn and then load on all of your business PC's.  Because there are already so many respins of Ubuntu (like Linux Mint) you can simply distro-hop until you find something that is close to what you want.  Then you can tweak that distro to your liking and use *remastersys* to spin a distro with your customizations to an ISO file which can be burned to a CD (if small enough) or DVD.  So it is not as convenient as the SUSE Studio service, but most of the heavy-lifting has been done by the community in the form of the plethora of Ubuntu-based distros.

I like clicking on "Random Distro" for entertainment:  [http://distrowatch.com/table.php?distribution=swift](http://distrowatch.com/table.php?distribution=swift)

---

### Post by lykwydchykyn on 2014-03-13
I can see a lot of *use* cases for it, but (at least for canonical) I can't see a *business* case for it; that kind of infrastructure can't be cheap to put together.

---

### Post by forrestcupp on 2014-03-14
> **Tristan_Williams said:**
> I can understand being unhappy with it. I for one am overjoyed with it. It is exactly what I want. Well not exactly, but pretty close. 

I think what I want is a happy medium between Ubuntu and Gentoo.
Maybe a completely source based Ubuntu. Kind of like Gentoo, but using Ubuntu repos and framework and all that good stuff.Maybe they've made the installation better than it was when I tried it out. It's been a while, and I can't remember it completely. It just seems like it was kind of confusing at some points, and it didn't give me quite as much control as I expected over what I wanted to be installed. Maybe it has changed since then. It's been a couple of years. 

> **lykwydchykyn said:**
> I can see a lot of *use* cases for it, but (at least for canonical) I can't see a *business* case for it; that kind of infrastructure can't be cheap to put together.
True. Although part of building business is making your product useful and attractive.

---

### Post by PondPuppy on 2014-03-14
Has anybody worked with UCK? [https://apps.ubuntu.com/cat/applications/precise/uck/](https://apps.ubuntu.com/cat/applications/precise/uck/)

---

