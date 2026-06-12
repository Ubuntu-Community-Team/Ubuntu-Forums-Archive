---
title: "Virtualbox crashes host"
date: 2009-10-10
forum: Virtualisation
---

### Post by jynyl on 2009-10-10
Running Kubuntu 9.04 with all updates.
Virtualbox installed from Kubuntu repositories.

Shortly after starting a new vm, VirtualBox crashes the host OS.  I've tried booting the vm off iso files of Kubuntu 9.04 and 9.10, same result.

VirtualBox crashes the host, screen freezes, no response from keyboard and can't even ctrl-alt-F1 to get a terminal.

TIA

Peter

---

### Post by JeremyRuhland on 2009-10-11
I have the exact same problem with Ubuntu 9.04 and a Windows XP vm. So far the only option's been to cut power to my Aspire 751h. What kind of computer are you using? I've been hoping that this isn't a hardware specific problem.

---

### Post by jynyl on 2009-10-13
Oops, it appears I set the guest OS to run 64 bit, while the host os is 32 bit.  Still, Virtualbox should handle that more elegantly than crashing the host.

Running 32 bit OS on 32 bit host (both Kubuntu 9.04) went ok until I installed guest additions, then the guest crashed when starting xorg.

Virtualbox 3 PUEL version from the Sun website seems to work much better.

---

