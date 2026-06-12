---
title: "Run Same Ubuntu Installation from VM and on Physical Hardware?"
date: 2010-05-09
forum: Virtualisation
---

### Post by dsimcha on 2010-05-09
I have a Ubuntu 10.04/Windows 7 dual boot machine.  I have VirtualBox installed, but am willing to install another VM program if there's a better one for this.  I'd like to be able to run my Ubuntu installation, located on a physical partition, both on my real hardware (dual booting) and inside a virtual machine hosted by Windows 7.

I understand that, with some trickery, VirtualBox and VMWare can use physical partitions.  However, I'm not sure whether Ubuntu's hardware detection, etc. will allow the same installation to be run in a VM and on real hardware, especially if I install the guest additions on Ubuntu.  Also, Windows and Ubuntu are installed on the same physical disk, but Ubuntu is on a partition located in the middle of the physical drive.  I'm not sure how that would affect making this partition bootable in a VM.

As a side note, my CPU is an Athlon 64 X2 and does support AMD-V, if that helps.

---

### Post by dsimcha on 2010-05-09
Never mind.  Surprisingly, this seems to "just work" on VMWare player.  I've installed VMWare Player and set it up to boot my physical Ubuntu partition, installed VMWare tools on Ubuntu, and everything works fine.  When I rebooted and ran Ubuntu on bare metal, it still worked.  I am sincerely shocked that it was that easy.

---

