---
title: "any luck with installing adobe air 2.6 onto precise?"
date: 2012-02-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by prusswan on 2012-02-21
I got passed the library problem by installing ia32-libs, but got stuck at the stage where the error is about gnome-keyring not installed (in fact it was). Is it something to do with package version? Could I possibly roll up an older version of adobe air or modify the existing bin file to work with precise?

---

### Post by bobcollard on 2012-02-21
> **prusswan said:**
> I got passed the library problem by installing ia32-libs, but got stuck at the stage where the error is about gnome-keyring not installed (in fact it was). Is it something to do with package version? Could I possibly roll up an older version of adobe air or modify the existing bin file to work with precise?
Nope.

---

### Post by prusswan on 2012-02-21
> **bobcollard said:**
> Nope.

adobe air 2.6 is the latest version in the archive. I have read that it was possible to install it in Oneiric so it should probably work in Precise too with some fix

---

### Post by prusswan on 2012-02-22
turns out someone built a deb package for 2.5

[https://launchpad.net/~thopiekar/+archive/precise-dev/+build/3020054](https://launchpad.net/~thopiekar/+archive/precise-dev/+build/3020054)

edit:
even better, package for 2.6
[http://update.devolo.com/linux/apt/pool/main/a/adobeair/](http://update.devolo.com/linux/apt/pool/main/a/adobeair/)

---

### Post by bobcollard on 2012-02-22
> **prusswan said:**
> turns out someone built a deb package for 2.5
[https://launchpad.net/~thopiekar/+archive/precise-dev/+build/3020054]("https://launchpad.net/%7Ethopiekar/+archive/precise-dev/+build/3020054")
I looked at it.  It seems to want to remove fglrx, my graphic screen driver.  Thanks anyway.

---

### Post by vagner4work on 2012-04-24
sudo apt-get update && sudo apt-get install flashplugin-installer acroread
wget [http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin](http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin)
sudo chmod +x AdobeAIRInstaller.bin
sudo ./AdobeAIRInstaller.bin

If everything works, all should be installed. If you run into problems with adobe Air about missing gnome-keyring or KDE Wallet, run the commands below to fix it, then re-run the air installer.

sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0
sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0.2.0 /usr/lib/libgnome-keyring.so.0.2.0

---

### Post by jfernyhough on 2012-04-24
Or just use the 2.6 deb from the Devolo repo... :D

---

