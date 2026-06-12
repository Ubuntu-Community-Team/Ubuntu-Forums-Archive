---
title: "VirtualBox memory leak and high CPU utilization"
date: 2010-06-27
forum: Virtualisation
---

### Post by Xebec on 2010-06-27
I have 64-bit Karmic on my 8 GB box. Fresh VirtualBox 3.2.6.r63112 hosts freshly installed 64-bit Lucid with 4 GB of RAM dedicated to it. Guest additions are also freshly installed with the same VB version. There are two major problems:

1. Virtual machine always runs with 100% CPU utilized despite the fact that guest rarely climbs over 50%. The reason I can still use my host normally is that I dedicate to VM only one CPU out of four.
2. Withing 5 hours VM slowly outgrows its 4GB limit and takes all physical memory that is left - killing the host.

Is there anyone having similar problem?

---

### Post by zerohero on 2010-07-02
Similar issue on 32-bit, lucid host. Lucid-guest slowly eats all available memory in 5-8 h (but does not kill host, just becomes unusable/unresponsive/black screen). Sure looks a lot like a mem-leak.

---

### Post by delphaber on 2010-07-05
+1.

9.10 64bit running a windows xp guest. CPU and RAM load with the latest (3.2.6) virtualbox :\

---

### Post by Kane Hart on 2010-09-18
Anyone here ever solve the problem or suggest another distro that would be easy to setup and install.

I can also tell you I have this bug. It seams if I set low enough ram it does not happen but if I put to much ram into the VM being 64bit the ram will slowly eat up till she goes booom.


This really really blows btw I used the installer script on the xen wiki I use this as my statup:

```
-- quiet console=hvc0 partman/default_filesystem=ext3
```


I hope someone found a cure for this.

---

### Post by koma77 on 2010-09-25
I also have this bug.
Slowly the _host_ memory gets eaten up, but the guest stays the same, more or less.

---

### Post by Matt G Dalian on 2010-11-13
+1

I get this problem whenever I run VirtualBox, whether it's a Win XP Guest or an Ubuntu Guest.

I'm running Virtual Box 3.2.10 on Ubuntu 10.04 64 bit.

Even after I close Virtual Box my system is still using 60% of its ram (4 GB). But when I open up the system monitor I can't find the culprit.

Looks like a memory leak..

---

