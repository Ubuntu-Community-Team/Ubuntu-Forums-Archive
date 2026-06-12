---
title: "How up to date is Debian Testing?"
date: 2009-11-17
forum: The Cafe
---

### Post by jaxxstorm on 2009-11-17
The reason i ask is because I've got completely bored of Arch. Installing "packages" from AUR takes a fricking age, all I want to do is install Kompozer, and of course its got to compile from source and mess about.

I want a rolling distro with a decent package management system. Debian testing seems to fit the bill, but I don't want to wait two weeks for it to update.

---

### Post by blueturtl on 2009-11-17
[http://www.debian.org/releases/testing/](http://www.debian.org/releases/testing/)

edit:

You probably want Sid instead, though it can be quite unstable.
[http://www.debian.org/releases/unstable/](http://www.debian.org/releases/unstable/)

---

### Post by antenna on 2009-11-17
Have you tried yaourt for installing AUR packages?  I haven't used it for a while but usually works great.

From past experience Debian testing is quite behind Arch in terms of being up to date, especially when in a freeze.  I would happily use either distro though, probably the best ones going.

---

### Post by jaxxstorm on 2009-11-17
> **antenna said:**
> Have you tried yaourt for installing AUR packages?  I haven't used it for a while but usually works great.

From past experience Debian testing is quite behind Arch in terms of being up to date, especially when in a freeze.  I would happily use either distro though, probably the best ones going.

Yep, I'm using yaourt to install, its insane how long it takes to install packages.

If its two to three weeks behind it'll be worth it just to get things working.

I'm not considering unstable an option, with it being, y'know, unstable

---

### Post by m_duck on 2009-11-17
Debian testing isn't too far behind Arch in terms of packages at the moment. If you wanted a rolling release Debian distribution, you could check out [Sidux]("http://sidux.com/"). It is Debians unstable branch, with a bunch of their own scripts used to help stabilise it. I've only used it briefly myself, but it seems along the lines of what you want.

Having said that, both Debian testing and unstable (squeeze and sid) both have the same Kompozer package available:

[LIST]
[*][Kompozer (testing)]("http://packages.debian.org/squeeze/kompozer")
[*][Kompozer (unstable)]("http://packages.debian.org/sid/kompozer")
[/LIST]

---

### Post by Bachstelze on 2009-11-17
Sid is not really that much up-to-date either. It doesn't have Python 3, for example.

---

### Post by habtool on 2009-11-17
Ubuntu ends up being the best at the end of the day, imo

Wait till Lucid is at Alpha 1 or 2 and put that on a spare partition.
This is usually way ahead of Debian, esp with gnome.

Honestly even Ubuntu current (Karmic) with a few selected PPA's added to your sources list and you can stay at the cutting edge.

I also play with Debian Sid, Arch, Sidux etc, but Ubuntu has been home for many years now. I will install Fedora 12 later today, but there is always something missing that Ubuntu has that they dont have or I end up with some dependency issue. It was the same with Opensuse 11.2, within a few hours of install it on a open partition, something would be missing or broken.
People say the RPM dependency issues are a thing of the past, that may be true as I dont think that its a RPM issue, its more Ubuntu has better maintained repos, for which we have to thank all the MOTU guys and girls.

For me, Ubuntu current with a few PPA's works great while waiting for Ubuntu +1 (Lucid) to get to a installable state.

Running the development branch of Ubuntu for us folk that enjoy tinkering about is actually surprisingly quite stable.

What would really be nice is if Ubuntu setup its repos like debian:
Stable, testing and Unstable

We would then in effect have a rolling release system in testing and unstable. There must be a technical reason that they did not go this route, but it would have been fun if they did.

Any way, good luck with your search for a new distro.

We are very lucky to have so many choices!

---

### Post by Bachstelze on 2009-11-17
> **habtool said:**
> ubuntu ends up being the best at the end of the day, imo


+1

---

### Post by nothingspecial on 2009-11-17
> **Bachstelze said:**
> +1

+2

It`s one of the first things I do after a clean install on my fancy laptop. Add the ppas of the things I use most - gnome-do, banshee, deluge etc etc etc. The stuff I don`t use, well I don`t bother, but as far as I`m concerened I`ve got the latest, greatest.

Infact, I`ve (almost (well, a little bit)) automated the process.

Having said that, I`m not so sure the latest release of Ubuntu is all that stable. I heard an opinion stated that (something like) - releases inbetween LTS releases are used to iron out bugs before the next LTS is released. I`m coming round to that way of thinking.........

....... although I can remember a few "This broke and that broke and I can`t believe this is LTS" threads when Hardy came along.

wtf do I know?

(Uptime 36 days btw)

---

### Post by jaxxstorm on 2009-11-17
Ideally I'd like Arch + Apt, but I know its not possible. Pacman is great when you're installing prob the Arch supported repos, but once you start getting into AUR, it gets insanely messy. I'm one of those people who likes to install 5 different pieces of software to try it out (in this case I was looking for a PHP IDE) and with Arch, it took me over an hour to install them all.

> **Bachstelze said:**
> Sid is not really that much up-to-date either. It doesn't have Python 3, for example.

I'm not bothered about bleeding edge really. I don't want to have to reinstall every six months, and unfortunately with Ubuntu, I'll have to. (I know, I know, you can do update-manager -d, but it's not exactly what I'd call trustworthy) At least with Debian Squeeze I'll eventually get up to date packages without doing a distro upgrade!

---

### Post by lykwydchykyn on 2009-11-17
Been a few years since I ran Debian Testing, but it has it's own ebb and flow.  It's not entirely "rolling release".

It is pretty up-to-date and a bit volatile for the first year or so, then as the freeze approaches things start to stabilize and the updates aren't so frequent.  Then there's the long stretch between freeze and release, where you'll fall behind the cutting edge little by little until release.  

What happens at that point depends on whether your repose are set to "squeeze" or "testing".  If they're on "testing", you'll go right to squeeze+1, and things will ramp back up again.  If you're set to "squeeze", you'll of course stick with squeeze and be on Debian stable.

---

### Post by LoloftheRings on 2009-11-17
Debian sid has been more stable and much faster than Debian lenny for me. This was probably because of the newer KDE release. It hasn't been unstable at all, it all worked just fine.

I'm currently using Arch, and I'm still thinking about a switch back to good old Debian. One thing that's bothering me is the configuration. I'm just way to used to the current configuration system, last time using Ubuntu was like a nightmare to me. Debian is a bit more like Arch though.

Debian unstable was pretty cutting edge, I recieved the KDE update sooner than on Arch. I think Testing is on the same level as Ubuntu.

---

### Post by mivo on 2009-11-17
> **habtool said:**
> Ubuntu ends up being the best at the end of the day, imo

Eh, I disagree. Looking at the state 9.10 was released(!) in, I would hate to run its alpha versions on a production machine. In 18 months of running Arch and updating nearly daily, I had only two issues (both with Xorg) that could easily be fixed.

---

### Post by jaxxstorm on 2009-11-17
> **lykwydchykyn said:**
> Been a few years since I ran Debian Testing, but it has it's own ebb and flow.  It's not entirely "rolling release".

It is pretty up-to-date and a bit volatile for the first year or so, then as the freeze approaches things start to stabilize and the updates aren't so frequent.  Then there's the long stretch between freeze and release, where you'll fall behind the cutting edge little by little until release.  

What happens at that point depends on whether your repose are set to "squeeze" or "testing".  If they're on "testing", you'll go right to squeeze+1, and things will ramp back up again.  If you're set to "squeeze", you'll of course stick with squeeze and be on Debian stable.

Thansk for the advice, my repo has now been changed to testing and not squeeze :)

---

### Post by ibuclaw on 2009-11-17
> **jaxxstorm said:**
> The reason i ask is because I've got completely bored of Arch. Installing "packages" from AUR takes a fricking age, all I want to do is install Kompozer, and of course its got to compile from source and mess about.

I want a rolling distro with a decent package management system. Debian testing seems to fit the bill, but I don't want to wait two weeks for it to update.

Try [Sidux]("http://sidux.com/")

---

### Post by Xbehave on 2009-11-17
ubuntu is not rolling release and using ubuntu alphas isn't a sane option (especially as they don't want your bug reports), so recommending ubuntu to somebody looking at Rolling Release distros is just silly.

On topic:
[this]("http://oswatershed.org/") site tracks how current distros are statistically (peoples experiences are more valuable though, because stats will count not having python3 the same as not having firefox3.5).

If you look [here]("http://www.debian.org/distrib/packages") you can get a feel for how current debian is.

I have not used sid i wouldn't be too worried about the "unstable" tag though as the unstable refers to getting lots of updates not crashing.

In case you weren't aware, you can mix testing and unstable by [pinning packages]("http://jaqque.sbih.org/kplug/apt-pinning.html"), so if you want unstable firefox but testing xorg that isn't a problem. one note is that going versions older than the latest in testing is apparently* tricky though (I heard this was easy and useful in arch)

*I've only used debian stable but I did my reading)

---

### Post by mamamia88 on 2009-11-17
i would like to know this as well.  if it's not too far behind i would consider switching.  6 months is too soon to install new version of an os.

---

