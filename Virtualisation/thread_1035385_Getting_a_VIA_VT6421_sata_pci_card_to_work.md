---
title: "Getting a VIA VT6421 sata pci card to work?"
date: 2009-01-09
forum: Virtualisation
---

### Post by Predtech on 2009-01-09
Hi guys, i have virtualbox 2.0.6 installed on my Ubuntu 8.10 pc and everything works great except for one thing. My VIA VT6421 sata pci card is not listed in the device manager for my virtual XP machine. 

Can anyone help me get it recognized by virtualbox so it'll become part of the XP installation.

Coincidentally, i don't have the sata card running in ubuntu, i couldn't figure out how to do that. I still have a slave drive with a Windows XP installation on it for use of the sata card but i'd love to get that wiped out and use only the virtual XP machine instead.
I am very prepared to do a full reinstall of my virtual XP machine in order to get the VT6421 working properly if needs be.

---

### Post by Predtech on 2009-01-10
Nobody at all can help me with this????

---

### Post by valentt on 2009-11-29
> **Predtech said:**
> Nobody at all can help me with this????

I found the answer on how to make this VIA VT6421 card work on Ubuntu:

sudo modprobe sata_via

more details on my blog:
[http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/](http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/)

---

