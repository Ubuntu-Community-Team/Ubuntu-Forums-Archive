---
title: "Success with VirtualBox and Xubuntu on a FlipStart"
date: 2007-11-15
forum: Virtualisation
---

### Post by Pollywoggy on 2007-11-15
I bought a FlipStart handheld PC and these things can install Linux but it's my understanding that networking will not work with Linux as the OS for the FlipStart.

I installed VirtualBox for Windows on the FlipStart system and then copied a xubuntu Gutsy iso onto the FlipStart's  dard drive.  I opened the iso with VirtualBox and it was in effect a xubuntu LIVE session, from which I installed xubuntu.

It actually works and I can run xubuntu so that it is in front of XP and it looks as though the OS is actually xubuntu.  Networking works without the fiddling I had to do to run XP on my Gutsy desktop machine.  What I am saying is that it was easier to install Linux on an XP system than it is to install XP on a Linux system with VirtualBox, at least as far as networking is concerned.

---

### Post by raduga on 2007-12-14
> **Pollywoggy said:**
> I bought a FlipStart handheld PC and these things can install Linux but it's my understanding that networking will not work with Linux as the OS for the FlipStart.

I installed VirtualBox for Windows on the FlipStart system and then copied a xubuntu Gutsy iso onto the FlipStart's  dard drive.  I opened the iso with VirtualBox and it was in effect a xubuntu LIVE session, from which I installed xubuntu.

It actually works and I can run xubuntu so that it is in front of XP and it looks as though the OS is actually xubuntu.  Networking works without the fiddling I had to do to run XP on my Gutsy desktop machine.  What I am saying is that it was easier to install Linux on an XP system than it is to install XP on a Linux system with VirtualBox, at least as far as networking is concerned.

as mentioned on the linspire fora,
you'll want to use ndiswrapper + XP atheros 5523 drivers,
for native WiFi on a flipstart.

ACPI is a little wonky, too;  but most of the rest are fine.
(except for wan, camera, pointerstick)

---

