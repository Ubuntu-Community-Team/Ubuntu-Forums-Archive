---
title: "How good is System76's compatibility with other Linux distros?"
date: 2013-02-12
forum: System76 Support
---

### Post by Umbra Diaboli on 2013-02-12
Hi,

So there goes my question: How good is its compatibility with other  Linux distros? (Fedora, Debian, Mint, Red Hat, etc - to name a few  popular ones).

Has anyone tried other distros on System76 hardware?

Thanks!

---

### Post by ccrs8 on 2013-02-13
For the most part, Linux is Linux when it comes to hardware compatibility.  Linux drivers aren't developed with one distro in mind.  System76 picks hardware that works with Linux.  System76 officially supports Ubuntu because it can't support all distros with it's own System76 driver, but other distros work just fine.  You may need to manually install some drivers (ie do manually what the System76 driver does with a click of a button), but that's it.

I have a Wild Dog desktop and a Lemur laptop, and they have both run Ubuntu (and Xubuntu/Kubuntu), Mint, Debian, Fedora, OpenBSD, and a few others.  They all work fine.

---

### Post by isantop on 2013-02-13
> **ccrs8 said:**
> For the most part, Linux is Linux when it comes to hardware compatibility.  Linux drivers aren't developed with one distro in mind.  System76 picks hardware that works with Linux.  System76 officially supports Ubuntu because it can't support all distros with it's own System76 driver, but other distros work just fine.  You may need to manually install some drivers (ie do manually what the System76 driver does with a click of a button), but that's it.

I have a Wild Dog desktop and a Lemur laptop, and they have both run Ubuntu (and Xubuntu/Kubuntu), Mint, Debian, Fedora, OpenBSD, and a few others.  They all work fine.

Adding to this, the drivers for all of the "system critical" components (graphics, WiFi, Ethernet, keyboard, touchpad, drives, etc.) are supported out of the box in most modern Linux Kernels (they work without any modifications or drivers in Ubuntu, at least). While most distros do modify the kernel slightly, they're all largely the same.

---

### Post by HL521 on 2013-02-13
> **Umbra Diaboli said:**
> Hi,

So there goes my question: How good is its compatibility with other  Linux distros? (Fedora, Debian, Mint, Red Hat, etc - to name a few  popular ones).

Has anyone tried other distros on System76 hardware?

Thanks!

I have the Starling 4 Netbook. I have put Gentoo, Arch, Archbang, Puppy, and is now currently running Mint 14. Didn't notice any loss of compatibility whatsoever, so I'd say you're good.

---

### Post by Umbra Diaboli on 2013-02-13
Thanks a lot for the responses!

I'm looking thinking to acquire a Sable Complete Desktop in the near future :)

---

### Post by lolwtfhax on 2013-02-14
I think you should be fine as long as the distro you install uses the same kernel version or newer as what came with your laptop.
You can run "uname -r" in a terminal to find the version.

Linux Mint pretty much IS ubuntu and fedora stays very up to date so none of those should give you issues.

Debian focuses on stability and being free so it is not going to be up to date. They will also remove driver and firmware support that other distros may include because they are not completely free, requiring you to load it separately at install time from a usb stick or something. I'm  not sure if system76 uses any hardware like that but it's something you should be aware of if you install Debian.


edit: Apparently Mint is based on Debian testing now... I haven't used it in a while :P
I'm not sure if they strip things that are considered non-free by the debian project or not. If they do then debian should work fine as well.

---

### Post by NNJRob on 2013-02-14
> **isantop said:**
> Adding to this, the drivers for all of the "system critical" components (graphics, WiFi, Ethernet, keyboard, touchpad, drives, etc.) are ***supported out of the box in most modern Linux Kernels*** (they work without any modifications or drivers in Ubuntu, at least). While most distros do modify the kernel slightly, they're all largely the same.


Just for clarification.. How do you, at System 76 define a modern Linux kernel? (e.g., 3.0 & above?, 3.2 & above?)

---

### Post by isantop on 2013-02-14
> **NNJRob said:**
> Just for clarification.. How do you, at System 76 define a modern Linux kernel? (e.g., 3.0 & above?, 3.2 & above?)

We don't really have a definition, since we don't support non-Ubuntu OSs.

---

### Post by HotShotDJ on 2013-02-15
> **Umbra Diaboli said:**
> Has anyone tried other distros on System76 hardware?I have an older System 76 Pangolin (PanP5), My mother has a Ratel (about 1 year old) and a friend of mine has had a Starling, a Meerkat, and a newer Ratel.  I have installed OpenSUSE on all of them with no problems. The Starling choked on Gnome 3 for some reason but it runs well with LXDE.  I've also tried Fedora with no hardware issues on my PanP5.

Most modern Linux distributions have a "LiveCD" that you can run without installing to your hard drive so that you can test compatibility before committing to the install.

As mentioned before, chances are very good that any computer that will run Ubuntu will also run any other modern Linux distribution.  In fact, you probably have a better chance with compatibility between Linux version than you do between Windows versions!

---

### Post by lolwtfhax on 2013-02-16
I've just downgraded to kernel 3.2 and everything is working fine. So... Any distro running this kernel should work.

---

### Post by rmc_0 on 2013-04-30
I just installed Ubuntu GNOME desktop on my Pangolin, and the System76 driver appears to be incompatible.
```
Dependency is not satisfiable: python-gnome2
```

Is there a fix for this, or do I need to hunt through my hardware to figure out what needs their drivers?

---

### Post by isantop on 2013-04-30
Have you tried running apt-get update before attempting the installation?

---

### Post by rmc_0 on 2013-04-30
What. #-oI thought I ran that already before installing other things, but I tried it again on a lark. Evidently, attempting to install the driver was the *first* thing I tried, before anything else.
Thanks! And sorry for the monumentally stupid question...

---

### Post by isantop on 2013-04-30
No problem. I had a secondary installation I installed yesterday, and was freaking out over the same problem. It wasn't until neither the driver nor Audacity nor Gimp would install that I figured that out ;-)

---

### Post by screaminj3sus on 2013-05-02
I've used my lemur ultra with many, many other distros and the compatibility has been excellent, just as good as ubuntu in most cases. prior to kernel 3.7 I had to tweak grub for the brightness keys to work and prior to 3.8 I had to install a dkms driver for the card reader, but any distro with a 3.8 kernel all hardware works perfectly out of the box!

---

