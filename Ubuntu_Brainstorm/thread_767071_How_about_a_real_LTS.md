---
title: "How about a real LTS?"
date: 2008-04-25
forum: Ubuntu Brainstorm
---

### Post by vincent8422 on 2008-04-25
Imagine there is an OS that always keeps itself up-to-date, but never needs upgrade...

---

### Post by amingv on 2008-04-25
That statement contradicts itself :).

---

### Post by smartboyathome on 2008-04-25
I think he is saying that Ubuntu should be a rolling release distro, and Ubuntu would never do this, as it goes against their definition of "stability".

---

### Post by oo-boon-too on 2008-04-25
What I think would be really cool is if there was no (in my terms) 'OS siding', meaning, things such as hardware, software, etc. where not made for a certain OS. (Crys, then thinks of Video Card...)
(pause..)
That would be so nice...
;)

---

### Post by caryb on 2008-04-25
Without a "development" stream we would not be able to try out bleeding edge ideas. Could you imagine the impact of a mass rollout of Xorg 7.3 without the prior input/testing of of the Hardy testers?

BTW milestones are great! I get a stable release on my laptop for approx 2 weeks of the year


Cary

---

### Post by gnomeuser on 2008-04-26
> **vincent8422 said:**
> Imagine there is an OS that always keeps itself up-to-date, but never needs upgrade...

part of this is easy, just get rid of dpkg and apt-get. Conary is a far superior design for a rolling upgrade of packages and it allows easy rollbacks to previous states making bad updates a breeze to reverse.

This however does not make fundamental technology upgrades any easier, say like going from lvm to lvm2. Doing such changes on a running system is a big no no, for these we need some kind of preupgrade step that boots the new kernel and performs the conversion of your filesystems and so on (just imagine doing a ext3 to ext4 conversion on your old kernel which most likely has outdated ext4 drivers, the need for the new kernel becomes obvious rather quickly).

For rebootless security updates the recently released ksplice will allow certain kinds of non invasive kernel updates without a reboot, as such it could be made part of the package updating and your kernel could be patched literally underneath you.

Ressources:
[http://web.mit.edu/ksplice/](http://web.mit.edu/ksplice/)
[http://en.wikipedia.org/wiki/Conary_(package_manager](http://en.wikipedia.org/wiki/Conary_(package_manager))
[http://wiki.rpath.com/wiki/Conary](http://wiki.rpath.com/wiki/Conary)
[http://fedoraproject.org/wiki/Features/PreUpgrade](http://fedoraproject.org/wiki/Features/PreUpgrade)
[http://www.redhatmagazine.com/2008/04/15/interview-fedora-developers-seth-vidal-and-will-woods/](http://www.redhatmagazine.com/2008/04/15/interview-fedora-developers-seth-vidal-and-will-woods/)

---

### Post by ssam on 2008-04-27
there are a few distros that do this. for example gentoo, or the sid branch of debian.

---

### Post by Joeb454 on 2008-04-27
> **amingv said:**
> That statement contradicts itself :).

> **smartboyathome said:**
> I think he is saying that Ubuntu should be a rolling release distro, and Ubuntu would never do this, as it goes against their definition of "stability".

I agree on both counts. I'm not sure Ubuntu would suite being a rolling-release distro

---

### Post by DizzyTech on 2008-04-27
I quite agree that Ubuntu would not be a good rolling release distro.  I also agree that a rolling release distro would destroy Ubuntu's relative sense of stability.

But why not a hybrid system?  Doing actual releases would go as they are now, but why not have a team of people dedicated to constantly updating and fixing packages in the current Ubuntu release?  These people would do things like add latest bugfix packages, not just security updates.  Think latest Firefox, latest GIMP, etc.

---

### Post by Dr Small on 2008-04-27
If you want a rolling-release distro, why not try Arch then?

---

### Post by Dark_X on 2008-04-29
I thought that this idea was proposed already.  I think I saw it somewhere in the ubuntu wiki.
Edit: I was wrong.  It was more of a daily build thing. [https://blueprints.launchpad.net/launchpad/+spec/grumpy-groundhog](https://blueprints.launchpad.net/launchpad/+spec/grumpy-groundhog)

---

### Post by ugm6hr on 2008-04-29
> **DizzyTech said:**
> But why not a hybrid system?  Doing actual releases would go as they are now, but why not have a team of people dedicated to constantly updating and fixing packages in the current Ubuntu release?  These people would do things like add latest bugfix packages, not just security updates.  Think latest Firefox, latest GIMP, etc.

Firefox is already updated.

It would be nice to have more frequent updates for some apps though...

---

### Post by DizzyTech on 2008-04-29
I know Firefox is updated (although I've seen it take two months at times); I was just using an easily recognizable example.

---

