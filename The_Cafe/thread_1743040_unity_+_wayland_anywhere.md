---
title: "unity + wayland anywhere"
date: 2011-04-29
forum: The Cafe
---

### Post by miesnerd on 2011-04-29
Hey All-
I'm not a newb, but I know this is the forum that gets the most talk so I'm posting here.

Any pre-made distro/version of ubuntu that will allow me to try out unity + wayland on computer, preferably a a AMD 64 computer?

I got 11.04 last night on my desktop and I'm adjusting but I figured for some good nerd fun, I'd like to try what is suspected to be the 11.10 setup on a "for fun" computer.

Thanks in advance,

Miesnerd

---

### Post by idoitprone on 2011-04-29
No distro will ship wayland on default. Too many people do not have the correct drivers to use it and it requires graphic driver with KMS. So far, only intel has delivered and smaller reverse-engineer opensource driver projects. You can install it on the side. Ubuntu natty allows you to install it from the software center or commandline. 
[https://lists.ubuntu.com/archives/ubuntu-x/2011-February/001062.html](https://lists.ubuntu.com/archives/ubuntu-x/2011-February/001062.html) 

Fedora also has wayland prepackage in their repos, but they do not ship unity on default, unless they get their unity respin [http://spins.fedoraunity.org/](http://spins.fedoraunity.org/)

---

### Post by miesnerd on 2011-04-29
Thanks for the response.
I'd love it if an early snapshot was available, though I realize at this point that's probably both not worthwhile and potentially not really all that workable.

I'd imagine canonical will probably devote a few dev's to such a project to integrate unity and wayland here in the next 6 months anyways, and I think a wiki (or something) so those of us who are supremely interested can track such progress would be awesome!

---

### Post by areteichi on 2011-05-01
Well it is in the Natty repository.
[http://www.omgubuntu.co.uk/2011/02/wayland-enters-ubuntu-11-04-repo/](http://www.omgubuntu.co.uk/2011/02/wayland-enters-ubuntu-11-04-repo/)

---

### Post by miesnerd on 2011-05-01
> **areteichi said:**
> Well it is in the Natty repository.
[http://www.omgubuntu.co.uk/2011/02/wayland-enters-ubuntu-11-04-repo/](http://www.omgubuntu.co.uk/2011/02/wayland-enters-ubuntu-11-04-repo/)

I know. I cant confirm if those packages even work, to be honest.
I read one place that those packages were really just there to help dev's get a handle on how the packaging would be in the future.

In addition, on every machine I've tried to use to get those packages, I've been unable to resolve dependency issues.

Thus, I guess I'm probably going to have to wait a month or two to get an alpha 1 of 11.10 so I can at least try it out then.

---

### Post by sandyd on 2011-05-01
wayland actually works. Ive tried it out from the Xorg overlay on gentoo. (mesa-9999, libdrm-9999, xf86-video-ati). I had to use the 'wayland' USE flag on mesa to get wayland rolling, but other than that, everything is quite self explanatory.
The question is only if the version on ubuntu actually works.

---

### Post by miesnerd on 2011-05-02
> **sandyd said:**
> wayland actually works. Ive tried it out from the Xorg overlay on gentoo. (mesa-9999, libdrm-9999, xf86-video-ati). I had to use the 'wayland' USE flag on mesa to get wayland rolling, but other than that, everything is quite self explanatory.
The question is only if the version on ubuntu actually works.

thanks for clarifying. THat's what I actually meant. As the thread title indicates, my end goal of the current little experiment for me is to try uinty + wayland. Thus, why I started with ubuntu.

However, after some reading, I'm thinking maybe arch would work because a)I've read they have them in the AUR builds, and b) I love arch, too.

Might try it out in gentoo, too.

---

### Post by uRock on 2011-05-02
Moved to the Cafe.

---

### Post by miesnerd on 2011-05-05
gentoo/arch users, If I want wayland + unity, better to try it out on one versus the other. I'm decently familiar with both, and I like arch a little better.. but this isnt about distro pref, its about which is going to be better to try it out on...

Thanks in advance,

Miesnerd

---

### Post by aguafina on 2011-05-05
I tried it but found very little to do. seems to at the very earliest stages of development.

---

### Post by miesnerd on 2011-05-05
> **aguafina said:**
> I tried it but found very little to do. seems to at the very earliest stages of development.
what distro did you try it in? I could never get it to work in ubuntu, but I was trying to use the packages and not compile.

---

### Post by aguafina on 2011-05-05
I think it was these I used [http://www.chaosreigns.com/wayland/buildscript/](http://www.chaosreigns.com/wayland/buildscript/)
sometime last year, so it may moved on somewhat.

---

### Post by miesnerd on 2011-05-05
> **aguafina said:**
> I think it was these I used [http://www.chaosreigns.com/wayland/buildscript/](http://www.chaosreigns.com/wayland/buildscript/)
sometime last year, so it may moved on somewhat.

excellent. Thank you, I'll try that out!

---

