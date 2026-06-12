---
title: "Non-PAE Upgrade to 12.04?"
date: 2012-08-12
forum: Server Platforms
---

### Post by d4m1r on 2012-08-12
Hey guys, so I can currently running a 11.10 (32 bit, Non-PAE) server because I couldn't get 12.04 LTS to install....The problem ended up being the fact that 12.04 defaults to enable PAE but my old hardware doesn't support it.

Anyway, now I am trying to upgrade to 12.04 over SSH and I am pretty sure if I go ahead with the upgrade, it will brick my server....How do I know this? Because when I do sudo do-release-upgrade it tells me it will install:  **linux-headers-3.2.0-29  linux-headers-3.2.0-29-generic-pae linux-image-3.2.0-29-generic-pae. **Currently when I do a sudo apt-get upgrade it says it is keeping back: **linux-generic-pae linux-headers-generic-pae linux-image-generic-pae**

So 11.10 seems to be smart enough to NOT install the PAE stuff when upgrading, but it wants to install the PAE kernel when upgrade to 12.04 which I am guessing will make my Ubuntu server not boot....What do I do?! :confused:

---

### Post by Cheesemill on 2012-08-13
If you don't mind doing a fresh install you can just use the non-PAE version of the mini.iso to install a command line system.

[http://cdimage.ubuntu.com/netboot/precise/](http://cdimage.ubuntu.com/netboot/precise/)

---

### Post by d4m1r on 2012-08-13
> **Cheesemill said:**
> If you don't mind doing a fresh install you can just use the non-PAE version of the mini.iso to install a command line system.

[http://cdimage.ubuntu.com/netboot/precise/](http://cdimage.ubuntu.com/netboot/precise/)

That mini .iso needs the PC to be connected to the internet during install and it's not possible for me to do so....

---

