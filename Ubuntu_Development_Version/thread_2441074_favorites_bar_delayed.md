---
title: "favorites bar delayed"
date: 2020-04-18
forum: Ubuntu Development Version
---

### Post by VMC on 2020-04-18
It takes 15 - 20 seconds for the dock to populate. The dock is there but nothing appears for 15-20 seconds.
Anyone else notice this? I would rather have someone respond who has ubuntu installed on a hard drive/SSD and not VM.

This just started about a week or two ago. From the beginning until now it work. I zsync my iso and re-install every few days, so can't be sure when exactly it started.

---

### Post by VMC on 2020-04-19
Its Wayland that's causing the trouble. Running Wayland the dock is delayed 15-20 seconds abd "Show Applications" doesn't work. 
Reboot using Ubuntu instead of Wayland, everything works.

---

### Post by corradoventu on 2020-04-19
I see the same problem of dock delayed, "Show Applications" does not work, but if I press 'super + a' the list of applications appear and after that also "Show Applications" works.
I have 20.04 installed on SSD.

---

### Post by dino99 on 2020-04-19
i suppose 'journalctl -b' might show you what is wrong

---

### Post by VMC on 2020-04-19
> **dino99 said:**
> i suppose 'journalctl -b' might show you what is wrong

No journalctl or dmesg showed nothing related. Now I know its Wayland related.
Since I found it Wayland this topic is solved. Not related specifally to the Dock.

---

