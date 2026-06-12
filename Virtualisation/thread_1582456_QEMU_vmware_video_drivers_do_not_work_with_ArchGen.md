---
title: "QEMU vmware video drivers do not work with Arch/Gentoo/Slackware guests"
date: 2010-09-26
forum: Virtualisation
---

### Post by manzdagratiano on 2010-09-26
I noticed that the QEMU vmware video drivers are the ones which allow you to attain high resolution settings for the X server - for instance, with my Debian guest, I could not obtain the HD 1366x768 resolution unless I booted it with the vmware drivers - the others - std or cirrus - would let me go up to 1024x768 only. So far so good with the Debian guest (except that I still do not know how to increase video card memory in QEMU/kvm for better graphics performance).

However, when I try booting my Arch or Gentoo or Slackware guests with the vmware drivers, the display freezes and coughs up the output intermittently. I have no clue as to why these drivers should not work, whilst they indeed do with Debian. My physical video card is indeed a cirrus, and though I have hardware virtualization enabled, the vmware drivers behave better than the cirrus driver when they actually work - but not with these guests. Any ideas? (I would like to run my Arch guest with an HD resolution, so also the Slack guest. Gentoo I think I will live without the X server, though I would very much like to know why the drivers do not work).

---

### Post by manzdagratiano on 2010-09-27
I believe this might actually be a bug in the vmware drivers. I am filing a bug report in Launchpad.

---

