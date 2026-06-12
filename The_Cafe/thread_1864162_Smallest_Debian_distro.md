---
title: "Smallest Debian distro?"
date: 2011-10-18
forum: The Cafe
---

### Post by Spyro543 on 2011-10-18
I'm looking for the Debian base distro with the smallest download size. Nothing special, doesn't need all the preloaded software and doesn't really need a GUI (I could just install this stuff later). The main reason I want the Debian base is because of Synaptics packages and apt-get. Soooo...any suggestions?

---

### Post by haqking on 2011-10-18
> **Spyro543 said:**
> I'm looking for the Debian base distro with the smallest download size. Nothing special, doesn't need all the preloaded software and doesn't really need a GUI (I could just install this stuff later). The main reason I want the Debian base is because of Synaptics packages and apt-get. Soooo...any suggestions?

[http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst)

and to use synaptics you will need a GUI, it is a GUI based package manager

---

### Post by keithpeter on 2011-10-18
+1 for netinstall

You download a small bootable image, then any extra packages are downloaded when you install. The total download is smaller than a full live cd as you are not downloading 700Mb and then updating 300Mb+ of that!

As the name suggests, you need an Internet connection while installing - I always used a wired network connection into the router.

If you 'unselect' all the package groups when presented with the choice by the text installer, you will have a base system with apt-get. You can then tailor xorg, window manager &c to your requirements. Best to make a shopping list first.

As mentioned by haqking, a base install is command line only, you won't get synaptic until you install xorg and a window manager.

My personal Debian Squeeze setup is described at

[http://sohcahtoa.org.uk/pages/linux-dwm-window-manager-on-debian.html](http://sohcahtoa.org.uk/pages/linux-dwm-window-manager-on-debian.html)

and that was installed using netinstall image on a desktop with a wired connection.

---

### Post by collisionystm on 2011-10-18
> **Spyro543 said:**
> I'm looking for the Debian base distro with the smallest download size. Nothing special, doesn't need all the preloaded software and doesn't really need a GUI (I could just install this stuff later). The main reason I want the Debian base is because of Synaptics packages and apt-get. Soooo...any suggestions?

DSL haha

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by haqking on 2011-10-18
> **collisionystm said:**
> DSL haha

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

note the ha ha ;-)

Dont use this, it is way out of date and no longer supported.

Though i still have it in a run it in a windows config on a 128MB USB stick somewhere lOL

---

### Post by collisionystm on 2011-10-18
Debian editions of Puppy Linux

[http://puppylinux.org/wikka/dpup](http://puppylinux.org/wikka/dpup)

---

### Post by Bachstelze on 2011-10-18
[http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-amd64/current/images/netboot/mini.iso)

26M

---

### Post by haqking on 2011-10-19
[Light Linux Distros]("http://ubuntuforums.org/showthread.php?t=1582027")

---

### Post by el_koraco on 2011-10-19
[http://daily.grml.org/](http://daily.grml.org/)

---

### Post by Gremlinzzz on 2011-10-19
Barry Kauler has announced the release of Puppy Linux 5.2 "Wary" edition, a small, fast and very light distribution designed for old and low-resource computers: "This is a massive upgrade relative to the 5.1.x series. All of the base packages were recompiled in T2. Certain choices were made in T2 with the plan of seamless upgrading from X.Org 7.3 to 7.6 - that is, the default Wary system has X.Org 7.3, but it is planned that Wary can be upgraded to X.Org 7.6 by installation of a single PET package, and all applications will work before and after. This required some very careful configuration. The idea is to 'have our cake and eat it too' - X.Org 7.3 for old hardware, easy upgrade to 7.6 for newer video hardware. The plan actually seems to be working. As usual, huge changes yet only a small version-number change. Many bug fixes, upgrades, new packages.:popcorn:

[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by Majorix on 2011-10-19
Antix.

---

### Post by snowpine on 2011-10-19
Debian netinstall.

You might also find the smxi script helpful for updating/customizing your minimal Debian system: [http://smxi.org](http://smxi.org)

---

### Post by Spyro543 on 2011-10-19
> **Bachstelze said:**
> [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-amd64/current/images/netboot/mini.iso)

26M
Looks promising! What does it include? Just Ubuntu and apt-get?

---

### Post by el_koraco on 2011-10-19
> **Spyro543 said:**
> Looks promising! What does it include? Just Ubuntu and apt-get?

minimal kernel with some wireless and wired drivers, the installer itself, and a network config utility. apt and gang are downloaded and set up after selecting the mirror.

---

### Post by BrokenKingpin on 2011-10-20
++netinstall...gives you a base debian system, and then you can just install what you need.

---

### Post by nothingspecial on 2011-10-20
> **Spyro543 said:**
> Nothing special, doesn't need all the preloaded software and doesn't really need a GUI

You're right I don't :P

+1 for Ubuntu minimal.

---

### Post by krapp on 2011-10-20
There's the Debian business card .iso, which isn't really a system, so much as a way of distribution:

> This image has a size of up to 40 MB. It is small enough to fit on business card-shaped CDs (available in differing sizes, e.g. 58×75 mm/2.3×3"). This image contains just the bare necessities to start a Debian installation, i.e. those parts of the installer which are necessary to configure networking and download the rest of the installation system.

[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)

---

### Post by koleoptero on 2011-10-20
> **el_koraco said:**
> [http://daily.grml.org/](http://daily.grml.org/)

Ah, got here before me I see... :D

---

