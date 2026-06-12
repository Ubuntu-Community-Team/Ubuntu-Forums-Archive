---
title: "Vagrant Packaged Xubuntu Desktop freezes at boot on a Windows Laptop"
date: 2015-05-08
forum: Virtualisation
---

### Post by Layke on 2015-05-08
Hi guys and gals,

So I am completely stumped by this one.  I am currently building virtualized desktop development environments using Vagrant 1.7.2, Virtual Box 4.3.26, and Xubuntu 14.10 64 bit Desktop ISO.  I can successfully build, package, and upload my box from the host machine I developed the virtual Xubuntu machine on, and can successfully download it to a Mac Laptop that has no problem booting the environment.  However, on a Windows 7 Laptop, it seems to hang at booting.  I can manually select to boot from Grub, watch it successfully make the boot call to initrd, and then it goes to a black screen with the white underscore cursor frozen in place.

I have checked all the virtualization settings, tried to turn on and off various BIOS settings or options on the boot line parameters, and installing all kinds of updates like linux-firmware updates, intel graphic driver updates, etc.  I even tried creating an entirely fresh guest OS of Xubuntu on the laptop and it boots successfully.  It will even create a server based OS, install a desktop environment on said server image, and then boot into the new desktop environment successfully without a hitch.

This really is driving me crazy.  Does anyone have any idea what could possibly be the direction to look into next?  I even tried to boot with the graphics option as text, and it still freezes at the frozen output screen.  Very frustrating!

---

