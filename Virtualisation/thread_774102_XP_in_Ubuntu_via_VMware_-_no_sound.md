---
title: "XP in Ubuntu via VMware - no sound"
date: 2008-04-29
forum: Virtualisation
---

### Post by nightfever on 2008-04-29
i'm using Ubuntu 7.10 with XP installed thru VMware and Pulse Audio as a sound server and i have no sound in XP
the device i think is /dev/audio, and even if i put /dev/audio or let it Auto Detect, still don't have sound

i've installed VMware tools, i can play audio in XP, but can't hear a thing

and one more thing: my audio device is a Realtek HD Audio, and i want to use that XP for music production. Will i have the same audio quality as if i had a clean install of xp, with dual booting?

---

### Post by bmwman on 2008-04-29
I have the same issue with VMware Workstation 6.5 in Ubuntu 8.04. I found some instructions online that you can manually add it thru Add new hardware wizzard in XP. Just select that the hardware is already connected, then pick sound devices, and from the list select Creative sound or compatible. That worked for me. Also make sure you have VMware tools installed, that's the first thing you should checj actually.

Hope this helps :)

---

### Post by nightfever on 2008-04-29
yes, done that and it says "This device is working properly."
VMware tools are installed...everything works fine....but the problem is in linux

---

### Post by bmwman on 2008-04-29
Does your sound work fine in linux?

---

### Post by nightfever on 2008-04-29
yes :)

---

