---
title: "Which virtualization software do you think I should choose?"
date: 2012-11-10
forum: Virtualisation
---

### Post by briceorbryce on 2012-11-10
Hi all, I need help choosing "the best" virtualisation software for an x86 machine. I don't have any specifics on the machine but I already know that my options are limited. I also know that it does not support Vt-x (it's pretty old..~5 years).

I read that Xen was build for x64, correct? So that's out of the question already. Also, I was thinking about going with Ubuntu Server with KVM...but after more reading I think it might be better to go with some Linux distro with VMWare workstation (I believe it has the Win XP Pro license key still on it too - that's another option).

What do you think? Any input is greatly appreciated
:)

---

### Post by pkadeel on 2012-11-10
> **briceorbryce said:**
> Hi all, I need help choosing "the best" virtualisation software for an x86 machine. I don't have any specifics on the machine but I already know that my options are limited. I also know that it does not support Vt-x (it's pretty old..~5 years).

I read that Xen was build for x64, correct? So that's out of the question already. Also, I was thinking about going with Ubuntu Server with KVM...but after more reading I think it might be better to go with some Linux distro with VMWare workstation (I believe it has the Win XP Pro license key still on it too - that's another option).

What do you think? Any input is greatly appreciated
:)
Personally i have used virtualbox only on hosts with 2 or more CPUs with enough RAM.
But my guess is that the amount of RAM is definitely going to be an issue and if the host has only one CPU then that might be an issue as well. So also keep these two in consideration.

---

### Post by afz12 on 2012-11-10
Yes, Virtualbox is popular, free and quite easy to use. I've used it on XP - this runs 32 bits whether your maching is 32 or 64 bit. On an Acer5920, Virtualbox will only access one of its two cores on an XP/32 bit partition and does the same on a Linux partition. It runs quite slow because of this but allocating small amounts of RAM doesn't seem to make much difference. This notebook is i5 4 core and Virtualbox uses all 4 cores - virtualized OS' will run slower than native say about 1/2 perhaps?

I suggest you check the virtualization "mega thread" at the start of this forum - a number of virtualizers are compared.

---

### Post by briceorbryce on 2012-11-10
Thanks for the replies :KS

---

### Post by andrew.46 on 2012-11-10
Another vote here for VirtualBox, I would suggest downloading from the [VirtualBox website]("https://www.virtualbox.org/wiki/Linux_Downloads") rather than using the repository version though, much easier to stay up to date that way.

---

### Post by stuckne1 on 2012-11-11
Virtual box is good, but another free option is VMware player. I prefer virtual box because I like the interface, but I have seen many people use VMware player and prefer it. If you need stronger 3d graphics support then you need to use VMware player over virtual box.

---

### Post by nwalkey on 2012-11-12
Virtual box will run xp very well with a dual core processor and 2-4gigs of ram on the host.  Windows 7 runs faster under virtual box on my laptop (i7 @ 2.3ghz, 8gb ram, 1gig video) than it runs natively on many laptops that I have used.

---

### Post by andrew.46 on 2012-11-12
> **nwalkey said:**
> Virtual box will run xp very well with a dual core processor and 2-4gigs of ram on the host.  Windows 7 runs faster under virtual box on my laptop (i7 @ 2.3ghz, 8gb ram, 1gig video) than it runs natively on many laptops that I have used.

Indeed. One of the reasons I built my current computer with an 8 core amd chip:

```

andrew@skamandros~$ **[COLOR="Red"]uname -p[/COLOR]**
AMD FX(tm)-8150 Eight-Core Processor

```

and a roomful of ram was so I had many resources to share with VMs, multi-cores make compiling on the guest vm a breeze :).

---

