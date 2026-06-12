---
title: "Best distro for laptop?"
date: 2010-01-23
forum: The Cafe
---

### Post by The Toxic Mite on 2010-01-23
Hey everyone!
 
My stepdad's new partner gave me this old laptop recently. The known specs are as follows:
 
[LIST]
[*]750MHz Intel Pentium III
[*]128MB of RAM
[/LIST]The graphics are pretty crap as well, and the Ethernet's buggered (meaning I can't install from the minimal CD). So ideally I would need a light and stable distro with NDISwrapper included. And yes, I have tried Damn Small Linux but it cannot connect to any wireless networks when I try to use their front-end.

---

### Post by HoboElectus on 2010-01-23
Can't you upgrade the RAM?

---

### Post by Simon17 on 2010-01-23
Puppy is light with good wifi support.

---

### Post by dragos240 on 2010-01-23
> **The Toxic Mite said:**
> Hey everyone!
 
My stepdad's new partner gave me this old laptop recently. The known specs are as follows:
 
[LIST]
[*]750MHz Intel Pentium III
[*]128MB of RAM
[/LIST]
The graphics are pretty crap as well, and the Ethernet's buggered (meaning I can't install from the minimal CD). So ideally I would need a light and stable distro with NDISwrapper included. And yes, I have tried Damn Small Linux but it cannot connect to any wireless networks when I try to use their front-end.

DSL uses 2.4 linux, which does not support wireless well. Use a modern distro with minimal things installed by default.

---

### Post by The Real Dave on 2010-01-23
I'll suggest two things, Slitaz and taking a look a [KMandla's blog]("http://kmandla.wordpress.com/"), he does a lot of stuff with older computers, yours would be considered powerful ;) 

Its worth a look :) 

As for Slitaz, I've only dabbled with it myself but I've heard good things, good compatibility and almost as quick as DSL :)

---

### Post by rogue_0111 on 2010-01-23
This is from linux.org

[http://www.linux.org/dist/list.html](http://www.linux.org/dist/list.html)

Puppy is also an excellent choice.

---

### Post by earthpigg on 2010-01-23
> **The Toxic Mite said:**
> Hey everyone!
 
My stepdad's new partner gave me this old laptop recently. The known specs are as follows:
 
[LIST]
[*]750MHz Intel Pentium III
[*]128MB of RAM
[/LIST]The graphics are pretty crap as well, and the Ethernet's buggered (meaning I can't install from the minimal CD). So ideally I would need a light and stable distro with NDISwrapper included. And yes, I have tried Damn Small Linux but it cannot connect to any wireless networks when I try to use their front-end.

you could get past the 256mb requirement for any ubuntu-derivative by creating a swap partition, rebooting, and then running the installer.

[masonux]("http://sites.google.com/site/masonux/") (im biased, of course :p )
spri
crunchbang
etc



if that doesn't work out you could try '[remastersys lxde lite]("http://geekconnection.org/remastersys/forums/index.php?board=2.0")'. it's debian, and uses debian-installer, so it will install with the ram as-is. i have no idea how it's wifi support is.

[http://geekconnection.org/remastersys/forums/index.php?board=2.0](http://geekconnection.org/remastersys/forums/index.php?board=2.0)

from [here]("http://geekconnection.org/remastersys/forums/index.php?topic=96.0"): 
> I do a lot of PC recycling for folks that can't afford PC's and wanted a robust, free, feature rich operating system that would work well even on older Pentium 2 PC's with only 128MB ram. 

and fragadelic is a good guy :P

---

### Post by beetleman64 on 2010-01-23
I can't promise anything, but CrunchBang (#!) is a good, light Ubuntu based distro which should run on your specs. I've heard good things about puppy Linux too.

---

### Post by coolbrook on 2010-01-23
I'm experimenting with my first Ubuntu Mini CD install and I might put LXDE on top.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by earthpigg on 2010-01-23
> **coolbrook said:**
> I'm experimenting with my first Ubuntu Mini CD install and I might put LXDE on top.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

i made [a list]("http://sites.google.com/site/masonux/home/ease-of-use") of the package names of a few bits and pieces of the full ubuntu/gnome desktop that i find helpful with LXDE.

example:
> _Double Click to Install .deb Files_
After you install this package, you will be able to double click on .deb files to install them, just like vanilla Ubuntu.
package name: gdebi

hunting down those package names for my own use was an annoying task, so i made a list of them. making it public was the next logical step.

if anyone has any suggested additions, please share!

---

### Post by k64 on 2010-01-23
I would recommend something akin to [SLAX]('http://www.slax.org/') that has a full desktop environment but has very little in the way of resource hogging bloat. Bloat as in those 2 GB of Terminal apps that Ubuntu has.

---

### Post by Xbehave on 2010-01-23
You'll probably need to strip down a 'full' distro if you need wireless support out of the box. I think something like Xubuntu, would be a good starting point, from there i'd move towards fluxbox as a DE.

> **k64 said:**
> I would recommend something akin to [SLAX]('http://www.slax.org/') that has a full desktop environment but has very little in the way of resource hogging bloat. Bloat as in those 2 GB of Terminal apps that Ubuntu has.
What are you on about?
[LIST]
[*]Slax is good for a liveCD but AFAIK it doesn't have a good update system so isn't good for a proper install.
[*]Terminal apps that aren't running aren't really going to affect anything other than HDD usage, so i wouldn't really call them bloat.
[*]Even a full ubuntu install doesn't have 2GB of Terminal apps, let alone a minimal one.
[/LIST]

---

### Post by K.Mandla on 2010-01-23
Watch this, in great big letters: ARCH LINUX.

That's right, I said it. :evil:

---

### Post by n0dix on 2010-01-23
I run my Dell Inspiron 6400 with Arch Linux. It's fenomenal this distro. I don't get any problem. :)

---

### Post by Xbehave on 2010-01-23
If you go with ARCH it does have ndiswrapper on the CD, but setting up wireless in arch is always [fun]("http://wiki.archlinux.org/index.php/Wireless_Setup")!

---

### Post by earthpigg on 2010-01-23
> **K.Mandla said:**
> Watch this, in great big letters: ARCH LINUX.

That's right, I said it. :evil:

if he can't do an ubuntu minimal install, he can't do an arch install for the same reasons.

---

### Post by n0dix on 2010-01-23
> **Xbehave said:**
> If you go with ARCH it does have ndiswrapper on the CD, but setting up wireless in arch is always [fun]("http://wiki.archlinux.org/index.php/Wireless_Setup")!

Well, it's not set automatically like ubuntu, but a configure pretty fast with that guide ;)

---

### Post by n0dix on 2010-01-23
> **earthpigg said:**
> if he can't do an ubuntu minimal install, he can't do an arch install for the same reasons.

Well it is not for all the people, but it is there. :lolflag:

---

### Post by Xbehave on 2010-01-23
> **earthpigg said:**
> if he can't do an ubuntu minimal install, he can't do an arch install for the same reasons.
Actually that's what I suspected^ but if he uses the arch core CD , it's like doing a minimal install but with the repo on the CD (much like a debian install, i think).

TBH i think it'd still be easier to something like:
1) Get a minimal CD,
2) Mount as a loopback device
3) Add ndiswrapper+wpasupplicant* debs to the iso
4) Burn the new image 
5) Boot minimal cd, go through until you get to the networking step
6) Switch to tty2 
7) Install and setup ndiswrapper+wpasupplicant
8*)Connect to a wireless network using wpasupplicant
9) Continue minimal install, making sure you remember to install ndiswrapper+wpasupplicant

Or [install ubuntu to a chroot]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/linux-upgrade.html") from any linux liveCD that has wireless support for you (installing from a chroot means you can install any selection of packages you want)

^It wouldn't be the first time somebody has suggested arch without actually reading the thread
*wpasupplicant is only needed if you need to connect to a wpa network, and wpa supplicant has some dependencies that may not be on the minimal cd ( libdbus-1-3 libnl1 libpcsclite1 adduser )

---

### Post by aaaantoine on 2010-01-23
Hold on a minute...  This is a Pentium III laptop.  Does it even *have* wireless?

---

### Post by L4U on 2010-01-24
Mint works *killer* on my laptop.  Everything just worked.  I don't think I needed to install anything to make any of my hardware or files work.

---

### Post by Xbehave on 2010-01-24
> **L4U said:**
> Mint works *killer* on my laptop.  Everything just worked.  I don't think I needed to install anything to make any of my hardware or files work.
The original thread title was for a "craptop", this machine is very low spec (too low for kde or gnome) and he doesn't have Ethernet so cant use a minimal install CD

---

### Post by The Toxic Mite on 2010-01-24
> **aaaantoine said:**
> Hold on a minute... This is a Pentium III laptop. Does it even *have* wireless?
 
USB dongle ;)

---

### Post by MisfitI38 on 2010-01-24
> **Xbehave said:**
> ^It wouldn't be the first time somebody has suggested arch without actually reading the thread

I've read the thread. I see no reason not to recommend it.

---

### Post by n0dix on 2010-01-24
> **MisfitI38 said:**
> I've read the thread. I see no reason not to recommend it.

+1 :guitar:

---

### Post by Xbehave on 2010-01-24
> **MisfitI38 said:**
> I've read the thread. I see no reason not to recommend it.
You clearly didn't read my post very well, I did say is as long as he uses the arch core CD, then arch is a valid suggestion, however i was just pointing out that arch users are known to post "USE ARCH!" in just about any thread.

---

### Post by MisfitI38 on 2010-01-24
> **Xbehave said:**
> You clearly didn't read my post very well
I did read it.

> ...however i was just pointing out that arch users are known to post "USE ARCH!" in just about any thread.

Ah, I see. I was not aware of that. I can't say I agree with your observation, though, because a forum search for the term "Arch Linux" does not seem to bear this out.

Anyways, thanks for the clarification, and it was not my intention to bicker with you.

---

### Post by saif_held on 2010-01-24
I would go with Puppy as well.

---

### Post by coolbrook on 2010-01-24
I was unhappy with my hardware and LXDE/Ubu Mini.  I've only got 1 GB RAM to work with and unfortunately my POS (point of sale, of course) old P3 mobo won't allow me to disable onboard (64 MB shared) video.  I've got my fingers crossed for Arch.  I may put Puppy back on that system, or a derivative with a nicer menu.  For the record Puppy/GXine kicks *** for DVD playback.

---

