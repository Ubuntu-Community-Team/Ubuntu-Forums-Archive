---
title: "64bit virtualbox"
date: 2009-11-17
forum: Virtualisation
---

### Post by Romanrp on 2009-11-17
I have a 64bit capable processor
I have downloaded the 64bit version of virtual box directly from Sun
I am running 64bit harmic
I tried to run a 64bit linux via virual box
This is what I get
THis kerenel requires an x86-64 CPU ,but only detected an i686 CPU.
Unable to boot-please use a kernel appropriate to your CPu.

help please,i nered this to work to test gentoo,slackware,freebsd and other hardcore unix os

---

### Post by baggar11 on 2009-11-17
To support 64bit guests with Virtualbox, your processor must have AMD-v/VT-x support. If your processor has this feature, you may need to enable them in the bios.

Otherwise, you're only option for 64bit guests is with vmware server.

---

### Post by Romanrp on 2009-11-18
Ok,I will try that.

---

