---
title: "Can't get Vbox x64 guests on Ubuntu 11.10 host"
date: 2011-12-29
forum: Virtualisation
---

### Post by bensewell on 2011-12-29
Hi, running a Quad Q6600 with 6GB RAM and the usual.  Been using windows but converting after using Centos and Redhat at work.

Got virtual box installed fine and had it on Win7 before converting to ubuntu.  The x64bit guests worked fine.

I can get the x32 bit guests to work fine but as soon as i start up a 64bit one i get a few errors.

I've tried allsorts including checking the bios, checking if KVM is installed and just scratching my head so far.

Any ideas?

---

### Post by Perryg on 2011-12-30
You might want to try with the execute disable bit "disabled" in the bios.

---

### Post by idef1x on 2011-12-31
Silly question maybe, but did you install the x64 version of virtualbox?

[s]kvm is another virtualisation technique and so has nothing to do with virtualbox.[/s]

---

### Post by dolphin194 on 2012-01-01
Make sure that you have a 64-Bit Ubuntu Installation, and have installed the 64-Bit version of VirtualBox.

You cannot run a 64-Bit program in a 32-Bit Operating System.

---

