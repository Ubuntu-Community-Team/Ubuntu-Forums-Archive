---
title: "Minimal distribution that supports Virtual Box"
date: 2008-11-14
forum: Virtualisation
---

### Post by C.S.Cameron on 2008-11-14
I am playing around with Virtual Box on persistent Thumbdrive.
XP runs ok as guest on a 4 GB stick, but is a bit slow.
I'm wondering, if a person wanted to build a dedicated Windows flash drive, what is the most minimal Linux distribution that will run Virtual Box?

---

### Post by bodhi.zazen on 2008-11-14
How minimal ?

You can run Virtualbox from the command line and VNC into the guest. See the VBox documentation.

You can do the same with VMWare. VMWare Server 2.0 comes with a web based GUI to manage your guests.

---

### Post by snowpine on 2008-11-14
Hi Cameron,
The smallest distro I can think of that meets your criteria is SliTaz, which includes qemu in its repositories. Never tried quemu personally but my understanding is, qemu is to virtualbox as apt-get is to synaptic (if that makes any sense). SliTaz also has a nice LiveUSB tool, tazusb.

Last couple of days, I've been playing around with Sidux (lxde or xfce; I don't like the kde version). It's based on Debian, so it should run Virtualbox just fine, and I think you would really like it as a fast, fun, powerful live USB distro. :)

---

### Post by C.S.Cameron on 2008-11-14
A persistent install of Ubuntu takes up 700 MB, I'm thinking that if it's a dedicated Windows disk, the user has to get by with MS applications and stuff, so it would not need OO, games or even a clock.
Being able to set up and run Virtual Box or VMWare from GUI is preferable.
The ability to make the drive persistent is a must.
I will check out SliTaz and Sidux, double clicking deb's is my style.

---

### Post by C.S.Cameron on 2008-11-18
Forget it, after messing with the concept a bit I figure I don't really want a dedicated bootable Windows disk.

Better to run VB off a Ubuntu flash drive and keep any virtual machines on their own stick.

---

