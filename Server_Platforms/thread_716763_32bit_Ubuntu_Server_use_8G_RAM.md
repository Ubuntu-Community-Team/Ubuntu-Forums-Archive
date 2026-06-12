---
title: "32bit Ubuntu Server use 8G RAM?"
date: 2008-03-06
forum: Server Platforms
---

### Post by bensode on 2008-03-06
Can someone point me to the steps that I need to take to enable PAE under Ubuntu 32bit server (7.04 or higher)?  I want to enable PAE so that I can have support for 8G of RAM in my server that I plan to roll out a couple of virtual projects.  Thanks!

Bensode

---

### Post by waveform on 2008-03-07
AFAIK, the kernel used in Ubuntu 7.04 and 7.10 supports PAE automatically - in fact, this is the reason one can't use Ubuntu Feisty/Gutsy Server with VirtualBox (see the [VirtualBox Guest OS Status]("http://www.virtualbox.org/wiki/Guest_OSes") page).

---

### Post by bensode on 2008-03-07
Very handy to know.  Thanks.  I remember at one point there used to be "bigram" kernels for other distros but had a hard time Google'ing for anything current.

---

