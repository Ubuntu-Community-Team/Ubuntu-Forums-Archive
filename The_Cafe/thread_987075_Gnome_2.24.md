---
title: "Gnome 2.24?"
date: 2008-11-19
forum: The Cafe
---

### Post by PCessna on 2008-11-19
I've been wondering if this would come out for Ubuntu soon, Namely 8.04?

I never checked to see when I used 8.10, but I couldn't stand 8.10 I just uninstalled it (wubi).

Anyone know? Or is it a 8.10 thing?

---

### Post by steeleyuk on 2008-11-19
Intrepid uses GNOME 2.24 (well, 2.24.1 now). It won't be backported to Hardy so if you want to use 2.24 you'll have to upgrade or compile yourself.

---

### Post by PCessna on 2008-11-19
> **steeleyuk said:**
> Intrepid uses GNOME 2.24 (well, 2.24.1 now). It won't be backported to Hardy so if you want to use 2.24 you'll have to upgrade or compile yourself.

Is GARNOME a good way? ([http://projects.gnome.org/garnome/](http://projects.gnome.org/garnome/))

I am not sure if it is ok to use though.

---

### Post by steeleyuk on 2008-11-19
Never  used it. I'm sure someone around here will have though.

I'll guess that its one of those occasions where you should backup if you do try it.

---

### Post by PCessna on 2008-11-19
Can anyone please suggest something, or should I use GARNOME?

Thanks
-PCessna

---

### Post by PCessna on 2008-11-20
> **PCessna said:**
> Can anyone please suggest something, or should I use GARNOME?

Thanks
-PCessna

Bump!

---

### Post by PCessna on 2008-11-21
> **PCessna said:**
> Bump!

Bump.

---

### Post by Changturkey on 2008-11-21
> **PCessna said:**
> Bump.

Just use GARGNOME. Or upgrade.

---

### Post by PCessna on 2008-11-21
> **Changturkey said:**
> Just use GARGNOME. Or upgrade.

How may I upgrade?

---

### Post by wersdaluv on 2008-11-21
He means, upgrade to Intrepid. If you want the latest GNOME, there's Foresight Linux.

Btw, stuff like this shouldn't be on the Cafe.

---

### Post by bobbocanfly on 2008-11-21
I've heard of people using GARNOME without problems before, so if you dont mind having b0rked GNOME for a bit if something goes wrong, then go ahead.

---

### Post by PCessna on 2008-11-21
If I go to upgrade to 8.10, can I JUST select the packages to upgrade GNOME, If so which are these

Thanks
-PCessna

---

### Post by cardinals_fan on 2008-11-21
> **PCessna said:**
> If I go to upgrade to 8.10, can I JUST select the packages to upgrade GNOME, If so which are these

Thanks
-PCessna
No.  It sounds like you would prefer a rolling release distro...

---

### Post by PCessna on 2008-11-21
> **cardinals_fan said:**
> No.  It sounds like you would prefer a rolling release distro...

a what? This shows that the devlopers of Ubuntu seem to be all about themselves, You get 8.10, or no safe GNOME 2.24. Very nice way for a Linux distro. I though Linux was customizable.. Hmm.. I gues s im wrong

---

### Post by niccholaspage on 2008-11-21
> **PCessna said:**
> a what? This shows that the devlopers of Ubuntu seem to be all about themselves, You get 8.10, or no safe GNOME 2.24. Very nice way for a Linux distro. I though Linux was customizable.. Hmm.. I gues s im wrong
You CAN get the repos for Intrepid in and install GNOME. If you don't mind taking a chance, Than you can do that.

---

### Post by doorknob60 on 2008-11-21
> **PCessna said:**
> a what? This shows that the devlopers of Ubuntu seem to be all about themselves, You get 8.10, or no safe GNOME 2.24. Very nice way for a Linux distro. I though Linux was customizable.. Hmm.. I gues s im wrong

No you're right. You already have a plenty of options:
Upgrade to Intrepid
New Distro
Compile

This is like complaining that you can't install IE7 in Windows 98...that's exaggerating, but using an older version of Ubuntu makes sense to get older version of the software that comes with it. A rolling release distro means that every time a new version of a piece of software comes out, it will be updated in the repositories, no need to upgrade your whole system or wait for a new distro release. Arch and the testing and unstable branches of Debian are examples of rolling release distros. I personally much prefer rolling release distros (I use Arch).

---

### Post by Mr. Picklesworth on 2008-11-21
> **PCessna said:**
> a what? This shows that the devlopers of Ubuntu seem to be all about themselves, You get 8.10, or no safe GNOME 2.24. Very nice way for a Linux distro. I though Linux was customizable.. Hmm.. I gues s im wrong

You are indeed wrong, at least in the respect I think you are hinting at :)
The distribution you chose is a specific configuration of components built to fit into a cohesive whole. For example, it would be a bad idea to yank out the Debian package system and replace it with something else because chances are you'll break something. The distribution is tied to Debian; it *is* Debian.

Same deal with GNOME. Each release is tied to a specific release of GNOME. You can upgrade each and every component, but that is well and truly *no different* from just installing Intrepid, give or take a few other changes like the new kernel, xorg and dkms. More often than not, GNOME is heavily influenced by the world around it and depends on those newer components itself.

If you want GNOME but you don't want Debian, for example, try any version of Fedora. Fedora 10 has GNOME 2.24. If you like Debian but want KDE, try Kubuntu. If you want GNOME 2.24 try Ubuntu 8.10. It all comes in packages.

Sure, you can go and build the latest GNOME snapshot on Ubuntu 8.04, but of course there aren't many (or, to be honest, any) people who are going to do it for you. For most people, and particularly for the distribution itself, that is a Complete Waste of Time. Especially when we consider that the major distribution upgrade Ubuntu offers from 8.04 to 8.10 is, basically, the upgrade to GNOME 2.24 you want along with the added goodies that make Ubuntu Ubuntu instead of just "Linux with GNOME and Debian". Since you don't want any of those aforementioned Ubuntu goodies of 8.10, I can only assume that you aren't quite happy with the configuration offered by Ubuntu. Maybe Arch Linux would interest you, or unstable Debian?

The "Linux is about choice" thing is an ugly marketing buzzword gone awry, and it honestly makes me sad whenever I see it. Why? Because so many people don't actually realize what this means. It doesn't mean that every options dialog has a "make this application misbehave because I told it to" switch (*cough*KDE*cough*), and it doesn't mean people are going to add it for you. Being free software means that you can download the source code, make changes and send them upstream. You have freedom to do what you want with the software and use it *however* you see fit. It does not mean that people can expect anyone else to do anything. It is no different from the real world, although people try to be a tad friendlier.
(Sorry if this didn't come across as such. I've been meaning to get that off my chest).

And no, I'm not saying the "free software is about choice" is *less* than what many people think. In fact, I think it is a lot more than what many people think when they casually use that phrase. In doing so, I fear that the most important thing is being quietly forgotten. This is choice and freedom on a scale far beyond mere pre-compiled options. You have been permitted free access to every single piece of software on your computer. You haven't just been given the keys; there are no locks.

---

### Post by kahlil88 on 2008-11-22
What don't you like about Intrepid? Hardy had a really annoying Compiz-Fusion bug that frequently locked up my system.

---

