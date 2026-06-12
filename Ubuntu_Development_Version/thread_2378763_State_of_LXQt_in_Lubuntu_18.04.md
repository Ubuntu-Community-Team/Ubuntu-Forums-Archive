---
title: "State of LXQt in Lubuntu 18.04"
date: 2017-11-26
forum: Ubuntu Development Version
---

### Post by vasa1 on 2017-11-26
I tried the "LXQt desktop" option at login time on Lubuntu 18.04. It looked just like an Openbox session, no panel in sight, even though the output of```
echo $DESKTOP_SESSION
```was "lxqt".

---

### Post by DogMatix on 2017-11-27
I downloaded a Bionic 18.04 Lubuntu Next ISO from [here]("http://cdimage.ubuntu.com/lubuntu-next/daily-live/20171126/"). Selecting install Lubuntu from the initial menu did not start installation but I was booted into a live LXQT desktop session, which does indeed have a black background similar to Openbox but I had panels, etc. I found an installer in the Desktop directory and tried to install it but it crashed with error "installed initramfs-tools package post-installation script subprocess returned error exit status 1" and would not continue. On reboot system failed to boot with "kernel panic" error. I repeated the install but the same thing happened. However, I liked the look of the live LXQT session.

Edit: I also tried the Lubuntu 18.04 daily live current from [here]("http://cdimage.ubuntu.com/lubuntu/daily-live/current/HEADER.html") (this installed OK) but was unable to find a LXQT session option at login, only Lubuntu, Lubuntu Netbook and Openbox options.

---

### Post by DogMatix on 2017-11-30
Better experience with Lubuntu Next ISO image today. Booted to graphical installer which worked fine. Installation went OK. Rebooted to LXQT desktop. Seems snappy. Still X11 but look forward to seeing a Wayland version could be a way forward for light weight desktop users. I'll keep this around for a while and keep it updated.

---

