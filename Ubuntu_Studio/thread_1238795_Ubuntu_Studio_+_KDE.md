---
title: "Ubuntu Studio + KDE"
date: 2009-08-12
forum: Ubuntu Studio
---

### Post by sbrown1992 on 2009-08-12
Hello guys
I was wondering how well Ubuntu Studio and KDE got along.
Is there any major compatibility problems between the two?

and also, would it be better to 

[LIST]
[*]install Ubuntu-Studio to disk, then add the KDE metapackage
[*]or install KDE to disk, then add the Ubuntu-Studio metapackage?
[/LIST]
Thank you :)

---

### Post by sgx on 2009-08-13
Neither. I would get an older Kubuntu, with a KDE vintage 3.5.10 - 3.5.5
so you can easily set the mouse scrollwheel to glide through multiple desktops. Use synaptic to get rid of the apps you'll never use, then use it  to add only the audio apps you know you will use. You'll end up with a fast stable DAW Only get rid of apps, not system files! If you're not sure, keep it. And start with multiple partitions, a separate /home partition really separates the men from the guys who tremble when needing or wanting to re-install
Cheers

---

### Post by Stochastic on 2009-08-13
sgx has some good advice, but I'm still scratching my head over the recommendation to build it on a vintage kubuntu rather than an up-to-date one.

Essentially the only items that may not be all that compatible with KDE (keep in mind I'm a gnome guy through and through) would be some features of the ubuntustudio-desktop or ubuntustudio-looks packages.  They won't conflict in any way, but you might not get the same theme effects (then again, maybe I'm wrong on that - never tried it).

My recommendation as to how you build your system would be to install Kubuntu first, then add the Ubuntu Studio meta packages that you need on top of that.  This will avoid ever installing any gnome-centric packages on your system (which happens in the default Ubuntu Studio install), and thus keep the system free of gunk.

---

### Post by autumnraine on 2010-03-16
Hi, I was hoping to get some up-to-date advice on this. I've installed Ubuntu Studio 9.10 on my new HP dv2 AMD Neo netbook-on-steroids, and then installed Kubuntu-desktop over top of that. Will that approach retain the real-time kernel? I don't mind having the Gnome and KDE apps both installed, you get the best of both worlds. 

So is this a sound way to go about it, or will it mess up the advanced audio configurations? Should I have installed the KDE-full metapackage instead of the Kubuntu-desktop metapackage?

Thanks so much for whatever input you can give.

---

### Post by sgx on 2010-03-17
> **autumnraine said:**
> Hi, I was hoping to get some up-to-date advice on this. I've installed Ubuntu Studio 9.10 on my new HP dv2 AMD Neo netbook-on-steroids, and then installed Kubuntu-desktop over top of that. Will that approach retain the real-time kernel? I don't mind having the Gnome and KDE apps both installed, you get the best of both worlds. 

So is this a sound way to go about it, or will it mess up the advanced audio configurations? Should I have installed the KDE-full metapackage instead of the Kubuntu-desktop metapackage?

Thanks so much for whatever input you can give.

Hi, over the years, I only had an occasional, (and non-Ubuntu) issue
when I needlessly tried to update part of GTK, gnome-canvas, or xorg,
on a working system, but the whole of gnome and kde work well together, and the old addage

'if it ain't broke, don't fix it' is tatooed across my cerebrum.
So unless I'm convinced I need a great new app, I don't change things
much, just update the important ones I use daily. 

Kernels won't get installed in secret, and synaptic points out
changes as you go. No problems there.

A few desktop and taskbar features I rely on, failed to arrive in
the early KDE 4xxx, so I prefer 3.5.10, but maybe 4.4 will have them.

If you have not yet done so, when you install next time, make a separate
/home partition, so you can freely experiment without the dread of reconfiguring everything, by choosing not to reformat /home in the installer routine. Probably good luck to do a usb-stick install too,
using ext2 filesystem, without a swap partition, to minimize disk-writes.
Cheers

---

### Post by d3v1150m471c on 2010-03-17
```

sudo apt-get install kubuntu-desktop

```
Prior to authorizing the installation, note all of the packages it will install and/or remove in the event removing it is not done cleanly. This is very important.

What fun is an operating system if you can't frankenstein it? ;)

---

### Post by autumnraine on 2010-03-18
Thanks for the replies. I tried it and decided it didn't work for me - and the whole system was just a bit too slow on my netbook. But in principle I imagine it should work fine, maybe with a little tweaking.

---

### Post by Sylvester Ink on 2010-05-04
I'm considering installing Kubuntu and then eventually installing the Ubuntu Studio packages afterward.  SGX, I like your method best (installing only Kubuntu and then adding the individual software as needed), but what about the realtime kernel patches and other optimizations in Ubuntu Studio.  Won't I miss those?

---

### Post by sgx on 2010-05-05
> **Sylvester Ink said:**
> I'm considering installing Kubuntu and then eventually installing the Ubuntu Studio packages afterward.  SGX, I like your method best (installing only Kubuntu and then adding the individual software as needed), but what about the realtime kernel patches and other optimizations in Ubuntu Studio.  Won't I miss those?

Hi, kernels and audio apps are usually available as separate packages listed in synaptic, there is a PPA repository mentioned in the wiki that has an RT kernel

[https://launchpad.net/~abogani/+archive/ppa](https://launchpad.net/~abogani/+archive/ppa)

[https://wiki.ubuntu.com/UbuntuStudio/10.04release_notes](https://wiki.ubuntu.com/UbuntuStudio/10.04release_notes)

you can add PPA repos to synaptic, usually the steps are listed
at the PPA. falk and autostatic PPAs have very recent versions of audio
and other media apps.

The Ubuntu Studio package installs lots of things in one go, to make things easy, and most can easily be uninstalled later with synaptic if desired. The separate /home partition, and choosing not to reformat it in a reinstall scenario, makes reinstalls trivial, preserving most of your configuration choices, as you explore how you want your studio for the long run.
Cheers

---

