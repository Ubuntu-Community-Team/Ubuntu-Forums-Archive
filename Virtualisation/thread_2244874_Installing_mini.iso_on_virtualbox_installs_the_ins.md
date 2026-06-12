---
title: "Installing mini.iso on virtualbox installs the installer"
date: 2014-09-19
forum: Virtualisation
---

### Post by turboruuvi on 2014-09-19
What's wrong?
When I complete installing drom the mono.iso and reboot, I'm no longer asked for the image, but
whether I'll start the installer (or the other options at start of the install image).
As if the installer didn't install the result of the install-prodedure, but the installer itself.

I'm using VirtualBox-4.3.12-93733-Win.exe on 64-bit Windows 8.1.
The mini.iso was downloaded from Ubuntu site today.
[Ubuntu 14.04 "Trusty Tahr" Minimal CD]("http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-amd64/current/images/netboot/mini.iso") 37MB* (MD5: 7297321c2fa6424417a548c85edd6e98, SHA1: e1e074b4302898698977c08013e0afe5c06245e2)
([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD))

---

### Post by steeldriver on 2014-09-19
Did you remember to 'eject' the iso from the virtual CD drive before rebooting? otherwise it's the same as leaving a real bootable CD in a real computer

---

### Post by turboruuvi on 2014-09-19
I used image file - the same way as I used the Ubuntu Desktop image (that installed fine).
(I thought a multinode with one desktop and 1 - 2 minimal servers would make a good "cluster".)

[https://www.dropbox.com/s/orbq1pjza6ubggo/mini_vm.PNG?dl=0](https://www.dropbox.com/s/orbq1pjza6ubggo/mini_vm.PNG?dl=0)

---

### Post by turboscrew on 2014-09-22
Funny, mini.iso is really left mounted in the installation whereas deskop install image is not.
Removed the mini.iso from the virtual CD drive and the installed server booted fine.
I didn't have to do that when I installed the desktop image. (I checked, and the virtual CD drive was empty.)

---

### Post by turboscrew on 2014-09-23
The case is SOLVED.
Note that turboruuvi and turboscrew are the same guy (some problems with account), so now that it's sorted out (I'm turboscrew again), I can't edit stuff I wrote as turboruuvi anymore.

---

