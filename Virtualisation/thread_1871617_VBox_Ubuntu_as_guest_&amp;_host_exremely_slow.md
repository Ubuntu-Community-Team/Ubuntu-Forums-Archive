---
title: "VBox Ubuntu as guest &amp; host exremely slow"
date: 2011-10-29
forum: Virtualisation
---

### Post by Subbeh on 2011-10-29
I'm running Ubuntu 11.04 as a host and 11.10 as guest in a Virtual Box. For some reason the guest is extremely slow; it took about 2 hours to install. I tried to allocate different amounts of memory (it's now using 1gb out of 4) and moved it from an ntfs disk to my home directory without any increase in speed.
I also run a Windows XP guest which works fine without any problems. I also tried installing using synaptic (ose) and downloading the deb file form virtualbox.org.
Does anyone know of a way to get this better? :confused:

Edit:
I noticed that Windows XP is using the IDE controller and Ubuntu uses SATA. Is there a way to switch Ubuntu from SATA to IDE? I tried removing it from the SATA controller to the IDE controller but when I start it, I get the error that there is no bootable medium found.

---

### Post by CharlesA on 2011-10-29
The HDD controller has no bearing on how fast or slow a VM runs.

What are the system specs of the host?

---

