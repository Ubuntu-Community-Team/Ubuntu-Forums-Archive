---
title: "VM Shutsdown Host"
date: 2024-09-09
forum: Virtualisation
---

### Post by Quarkrad on 2024-09-09
I have a request from a neighbour to build a win10 machine - all the machine is used for is to play microsoft solitaire collection and use email (I assume outlook).  I plan to build a ubuntu mate 22.04 machine and have a win10 qemu/kvm machine running inside.  I have asked the question before re launching the VM automatically at start-up so it appears as if the PC is a win 10 machine (user non-tech 80 year old who knows nothing about PCs).  My question here is, can I have a script on the host that will shut the host down when the user shuts down the win10 vm?  On a number of machines I 'look after' for various neighbours, who use ubuntu without any virtualisation, I run a script at shutdown that backs-up and updates their PC - the script includes the lines:

[B]sudo apt --yes update
sudo apt --yes upgrade
sudo apt --yes autoclean
sudo apt --yes autoremove[/B]

and eventually 

**shutdown -h now**

If I can write a script that will shut down the host when the VM shutsdown it would be nice to include these lines so the ubuntu host is updated without any user intervention.

---

### Post by TheFu on 2024-09-09
You could have something inside Win10 create an empty file on shared storage that Linux can monitor, perhaps every 5 minutes, which kicks off the linux stuff you want, then shuts down after that all finishes.  I have a script like that on my laptop, but instead of shutdown, it goes into standby nightly after the backups run.  I prevent standby mode even when the lid is closed, so if it isn't specifically requested, it doesn't happen.

If it were me, I'd only do patch work on Saturdays or Friday evenings after 5pm and I'd have **timeshift** and **back-in-time** doing backups daily, automatically to an external USB storage through the same shutdown script.  At my LUG yesterday, someone showed exactly how to setup both timeshift and back-in-time on a Linux Mint 22 system. I was impressed.  We even tested the timeshift restore.  It was easy.

BTW, support for Win10 ends Oct 2025, so I'd install Win11 instead.

I'd just install Win11 directly on the hardware and be done with it. No Linux.  If he doesn't really want Linux, I wouldn't force it. Sometimes we want to make things overly complex. Normal people just don't care.

---

