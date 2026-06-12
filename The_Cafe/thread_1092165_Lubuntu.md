---
title: "Lubuntu"
date: 2009-03-10
forum: The Cafe
---

### Post by NintendoTogepi on 2009-03-10
When is it coming? 9.10?

One thing - please work on keeping it very light. Not like Xubuntu which is maybe only 10-20% quicker and lighter than Ubuntu.

---

### Post by Johnsie on 2009-03-10
Ever used puppy linux? I like that one. It's a lot different to Ubuntu but that makes it interesting.

---

### Post by Eisenwinter on 2009-03-10
Or you can always try Arch.

---

### Post by Dragonbite on 2009-03-10
Is there a project page for Lubuntu?

I've done Fluxbuntu on my PI w/MMX @233 MHz laptop and it did an alright job (DSL was by far the best).  Don't know if Fluxbuntu still exists though.

---

### Post by snowpine on 2009-03-10
Check out CrunchBang Linux... it is available now, and is based on Ubuntu plus most of the components of LXDE: openbox, lxpanel, pcmanfm, etc.

Fluxbuntu is cool too, but currently the only version available is 7.10, which unfortunately will reach its "end of life" next month. And it uses Fluxbox instead of LXDE, perhaps not what the OP is looking for.

Or, do a base install of Ubuntu using the mini.iso and then 'sudo apt-get install lxde' or better yet use the Debian LXDE install CD.

---

### Post by Bart_D on 2009-03-10
> **snowpine said:**
> Check out CrunchBang Linux... it is available now, and is based on Ubuntu plus most of the components of LXDE: openbox, lxpanel, pcmanfm, etc.....

Agreed.  Plus, Openbox, by itself, looks better than LXDE which is too shiny.....and, for me, not worth it.

---

### Post by cyB3r4rd on 2009-03-10
I really hope that it'll be a really lightweight, really fast, stock, but tweakable LXDE. Sure I'd stick with the basic distribution, but I'd also change a few packages, like Leafpad -> medit, change the video player to Whaaw!, change the audio player to the GNOME-free Exaile, etc. Maybe I'd use a few Xubuntu-free stock XFCE tweaks too.
But there's one group of packages that would require a massive hacking: package management. Currently both Synaptic, the Add/Remove Software..., Update Manager and ubufox does have GNOME dependencies. A GNOME-free GTK-only replacement should be written, I think. And also they should use aptitude as backend, instead of apt-get.
I'm not a developer, but I'd love to see these improvements.

But these are just my ideas, not intended to confront anybody. :)

---

### Post by Dragonbite on 2009-03-10
> **cyB3r4rd said:**
> I really hope that it'll be a really lightweight, really fast, stock, but tweakable LXDE. Sure I'd stick with the basic distribution, but I'd also change a few packages, like Leafpad -> medit, change the video player to Whaaw!, change the audio player to the GNOME-free Exaile, etc. Maybe I'd use a few Xubuntu-free stock XFCE tweaks too.
But there's one group of packages that would require a massive hacking: package management. Currently both Synaptic, the Add/Remove Software..., Update Manager and ubufox does have GNOME dependencies. A GNOME-free GTK-only replacement should be written, I think. And also they should use aptitude as backend, instead of apt-get.
I'm not a developer, but I'd love to see these improvements.

But these are just my ideas, not intended to confront anybody. :)

Shouldn't be too bad to come up with an alternative like how they found Adept for KDE vs Synaptic for Gnome.  Worst-case scenario you can do it in the command line!

Be really cool if they built a command line interface that worked similar to Synaptic but all command line. Then you could use it for light systems, servers or if the GUI broke.

---

### Post by CJ Master on 2009-03-10
> **Dragonbite said:**
> Shouldn't be too bad to come up with an alternative like how they found Adept for KDE vs Synaptic for Gnome.  Worst-case scenario you can do it in the command line!

Be really cool if they built a command line interface that worked similar to Synaptic but all command line. Then you could use it for light systems, servers or if the GUI broke.

Aptitude?

---

### Post by kk0sse54 on 2009-03-10
> **Dragonbite said:**
> 
Be really cool if they built a command line interface that worked similar to Synaptic but all command line. Then you could use it for light systems, servers or if the GUI broke.

Aptitude? (damn CJ Master beat me to it :p)

---

### Post by Mehall on 2009-03-10
apt-get as well.

---

### Post by CJ Master on 2009-03-10
> **Mehall said:**
> apt-get as well.

No, not a visual interface.

---

### Post by Mehall on 2009-03-10
> **CJ Master said:**
> No, not a visual interface.

Oh, did we say visual interface?
oops.

I honestly can't stand aptitude though, and I rarely use Synaptic.

I haven't ever, even when I started with Linux (first distro was a kubuntu)

---

### Post by cyB3r4rd on 2009-03-10
Ok, just to make it clear: a GNOME-free, straightforward and powerful GTK-only GUI is a must for Lubuntu. That's the point. Be it powered by apt-get or aptitude.
Hope You get it. :)

(BTW: I never liked adept while I was using Kubuntu. Synaptic was among the first apps I installed instantly. :D)

---

### Post by Dragonbite on 2009-03-10
I know Fedora/CentOS has a fairly simple Python-based application called "Yumex" which is alright for Yum, wonder how difficult it would be to produce something like it for APT-GET.

Even Yast is open-source though I highly doubt they would use it.

---

### Post by gymophett on 2009-03-10
Read this everyone:
[http://blog.lxde.org/?p=208](http://blog.lxde.org/?p=208)

---

### Post by manilaph on 2009-03-12
Other distros have started using LXDE

[MoonOs]("http://www.moonos.co.cc/")

---

### Post by cyB3r4rd on 2009-03-12
> **manilaph said:**
> Other distros have started using LXDE

[MoonOs]("http://www.moonos.co.cc/")

Nice, but still has GNOME cruft added. I think that a truly fast LXDE distro should contain GTK-only apps, maybe with a few QT-only (non-KDE-dependent) stuff added. Nothing less, nothing more.

---

### Post by elfgoh on 2009-03-20
Hi folks, 

Seems that there are official pages for it now.

Have you guys seen these?

[http://launchpad.net/~lubuntu-desktop](http://launchpad.net/~lubuntu-desktop)

[http://wiki.ubuntu.com/Lubuntu](http://wiki.ubuntu.com/Lubuntu)

:KS

---

### Post by XubuRoxMySox on 2009-05-04
**Reinventing the wheel**, if you ask me. There already is a very lightweight and speedy Ubuntu that just flies along at mind-bending speed and has a very small footprint. It's called [Crunchbang Linux]("http://crunchbanglinux.org"), and it is built from a minimal Ubuntu installation. You get the Ubuntu repositories you want (including LXDE, by the way, which I'm using on Crunchbang for my own customized "Ubuntu Lite") with none of the bloat.

You want a true Ubuntu lite? It already exists right [here]("http://crunchbanglinux.org")! Just add LXDE to it using Synaptic and bingo. Custom Ubuntu Lite. It just doesn't get any better!

-Robin

---

