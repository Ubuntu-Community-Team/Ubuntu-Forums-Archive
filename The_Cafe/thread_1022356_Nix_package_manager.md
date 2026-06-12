---
title: "Nix package manager"
date: 2008-12-26
forum: The Cafe
---

### Post by scooper on 2008-12-26
[Linux.com article]("http://www.linux.com/feature/155922")
[Nix home page]("http://nixos.org")

Is there any work being done to take Ubuntu package management to the next level?

The Nix universal package manager sounds like an intriguing solution.  It allows multiple concurrent versions of different packages and their dependencies, avoiding backward compatibility issues.  Installing one bleeding edge package will never affect existing working packages by dragging in new libraries with subtle (or not) incompatibilities.

Nix can install binaries or source, if binaries are unavailable.

I would guess that one downside is disk usage.  Another might be that it could be harder to upgrade a library which is used by multiple packages.  Are there any other downsides?

What do you all think?  Couldn't this change the whole Ubuntu strategy of disjoint releases?

Cheers.

---

### Post by InfinityCircuit on 2008-12-26
No. [http://lists.debian.org/debian-devel/2008/12/msg01027.html](http://lists.debian.org/debian-devel/2008/12/msg01027.html)

---

### Post by DeadSuperHero on 2008-12-26
Well, there goes any hopes and dreams I had about Nix, for now anyways.

---

### Post by SunnyRabbiera on 2008-12-27
Well even though yes I agree that possibly a new package management/installer system is due for linux practically none of them have it right.
We need something that doesnt need pependencies or is hard to work with, this is why I like BSD's new package manager system and wish it would be ported over to linux sooner or later.
But it might break the compatibility we need.

---

### Post by jrusso2 on 2008-12-27
There are certain laws of physics like perpetual motion that never can be broken.  I guess package managers are the same thing unless they have a distro designed to use a new one.

---

### Post by SunnyRabbiera on 2008-12-27
> **jrusso2 said:**
> There are certain laws of physics like perpetual motion that never can be broken.  I guess package managers are the same thing unless they have a distro designed to use a new one.

Indeed, I sort of look forward to a linux distro based on BSD packages, I am sure it can be done.

---

### Post by InfinityCircuit on 2008-12-27
You might be interested in checking out CRUX's Ports setup.  They just released a new version, 2.5, earlier this month.

---

### Post by Anzan on 2008-12-28
> **InfinityCircuit said:**
> No. [http://lists.debian.org/debian-devel/2008/12/msg01027.html](http://lists.debian.org/debian-devel/2008/12/msg01027.html)

Agreed. No.

APT is an incredible packaging system. See the man pages for

       apt-cache, apt-get, apt.conf, sources.list, apt-secure

---

### Post by Eisenwinter on 2008-12-28
[pacman]("http://www.archlinux.org") takes all.

---

### Post by InfinityCircuit on 2008-12-28
More reference papers for the original subject:
[http://upsilon.cc/~zack/research/publications/hotswup-package-upgrade.pdf](http://upsilon.cc/~zack/research/publications/hotswup-package-upgrade.pdf)
[http://www.st.ewi.tudelft.nl/~dolstra/pubs/atomic-hotswup2008-submitted.pdf](http://www.st.ewi.tudelft.nl/~dolstra/pubs/atomic-hotswup2008-submitted.pdf)

I don't think this forum needs another stupid war between Dpkg and whatever Arch uses, but for those who do advocate Pacman: Nix obviously has some unique advantages, but they aren't worth the cost of the switch, since those advantages come with weaknesses. That's why this thread is interesting. On the other hand, does Pacman have actual advantages over Dpkg, other than supposedly lowering the barrier to make it easy to build packages? Does it try to implement some innovative new approach to package management?

---

### Post by jyaan on 2008-12-28
I've used apt-get (obviously), pacman and portage, and they are all pretty good. I suppose that I liked portage the best just because of the powerful things you can do with it (eg. I'm not interested in having this dependency). However, I did eventually get tired of having to build everything from source, yet I still miss Gentoo sometimes. :( It's a really awesome place to be for a programmer since it makes source code incredibly easy to obtain.

Anyways, a universal package manager would be nice, but it's probably not coming any time soon. Distros tend to store things in different places, and that can make things rather messy.

---

### Post by Anzan on 2008-12-29
InfinityCircuit, thanks for the PDF links. I'll review in more detail later.

jyaan, I'm just experimenting with portage on a fitPC that came with a dual-boot of Ubuntu and Gentoo.* The Gentoo has KDE already built so I'm working on setting up Fluxbox with the GTK apps I use. It's very interesting learning what works and does not... yet. 

But it also makes me appreciate all of the wonderful work that Debian developers have put into dpkg, APT, apt-get and Synaptic. 

----
* Ha ha ha. Amazing that anyone did this.

---

