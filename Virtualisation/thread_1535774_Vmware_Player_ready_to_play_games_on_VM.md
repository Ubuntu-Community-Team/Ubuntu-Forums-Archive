---
title: "Vmware Player: ready to play games on VM?"
date: 2010-07-21
forum: Virtualisation
---

### Post by sonnet on 2010-07-21
I read this review [http://www.zdnet.com/blog/perlow/virtualization-smackdown-2-oracle-vm-virtualbox-32-vs-vmware-workstation-71/13020?pg=2](http://www.zdnet.com/blog/perlow/virtualization-smackdown-2-oracle-vm-virtualbox-32-vs-vmware-workstation-71/13020?pg=2)
comparing the latest virtualbox 3.2 against vmware workstation 7.1.
I noticed the result vmware obtained on 3dmark03: 22500 with a 9800gt.
I checked on internet a see that a card like that one, normally would make a score of 35000 under windows.
So the vm brought around 60% of native performance, which seems t me quite amazing.
As today there are much more performing card than 9800gt, does that mean we can all play with good framerate all the games old at least 1-2 years?
Considering vmware player has the same 3d capabilities than workstation 7.1,
it would allow to many of us to not dual-boot.
What do you think?

---

### Post by techx4 on 2010-07-21
I am aware that workstation 7 brings with it much improved graphic support.. I was able to run deus ex (original) on my 2.4 dual core w/ 4gb ram.. haven't tried any other more demanding games though

---

### Post by sonnet on 2010-07-21
-Did you benchmark the delta in performance between native windows and under virtualization?
-Did you try workstation 7 or the new 7.1 (in the release note they promise impressive improvements)

---

### Post by dcstar on 2010-07-22
FWIW in glxgears I get ~15000 frames per sec in my 10.04 64-bit host, and in the same system running in VMware Player I get ~1800 FPS.

I have an ATI video card on my host using the hardware drivers.

---

### Post by fjgaude on 2010-07-22
> **dcstar said:**
> FWIW in glxgears I get ~15000 frames per sec in my 10.04 64-bit host, and in the same system running in VMware Player I get ~1800 FPS.

I have an ATI video card on my host using the hardware drivers.

This means the software driver within Player is about one-tenth as quick as the hardware one, eh?

---

### Post by sonnet on 2010-07-22
after I read the review I posted, I got excited and installed virtualbox and vmware player.
I must admit now I'm a bit disappointed.
I have a system with an athlon 4x2.7ghz ,8gb of memory and a 4670 radeon 1gb gddr3 vga.
With catalyst 10.4 on ubuntu 64 and on xp guests, on virtualbox 3dmark03 doesn't run. On vmware it runs, but there are many errors on visualization.
It get blocked most of the times,and the only score I could get was 3705:about 9-10 time smaller number I could get with native windows.

---

### Post by dcstar on 2010-07-25
> **fjgaude said:**
> This means the software driver within Player is about one-tenth as quick as the hardware one, eh?

Knowing the incredible level of complexity in getting the various 3D features to work in direct hardware access, I am impressed that VMware have got even basic 3D functionality working in their emulation of it.

---

### Post by cwwilson721 on 2010-07-25
Just as a joke, I thought I'd try World of Warcraft. Here we go:

In Ubuntu 10.04 64bit/wine: 60-85 FPS in Ironforge, ~50% one CPU utilization, ~25% RAM, and Latency of 90

Windows 7 Ultimate 64bit: 50-75 FPS, 65% CPU, 50% RAM, 150 Latency

VMWare (64bit virt, 2 core, WIN7 64 Guest): 10-15FPS, 100% CPU, 80% RAM, 400 Latency

All settings are the same between the three, except using the  'opengl' tag at the end of the command to start the Linux/wine version.

Hardware: Athlon 64x2 5200+, 2GB DDRII ram, 768MB DDRIII Nvidia 9600GSO

This shows what is REALLY going on here:

Linux/wine: Lower CPU usage= more room for WoW. The lower RAM usage also contributes. The lower latency is due to Linux more efficient network stack

Windows: More CPU overhead, more ram overhead, more network overhead= lower performance

VMWare: CPU usage killed this. You can walk, but that's about it. The latency being over 4x higher than native Linux was because of Windows network stack being so bogged.

In conclusion: VMWare gaming MIGHT work, but because most 3d is in software, instead of hardware, it really isn't worth it yet.

---

