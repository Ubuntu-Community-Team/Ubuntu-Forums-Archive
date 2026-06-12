---
title: "[SOLVED] Need help installing Virtual Box Guest Additions"
date: 2012-09-18
forum: Virtualisation
---

### Post by FulciLives on 2012-09-18
Hello!

I need help installing the Virtual Box Guest Additions.

Host: Windows 7 Ultimate 64-Bit
Guest: Lubuntu 12.04 32-Bit

I got Lubuntu installed in Virtual Box but I haven't a clue how to install the Virtual Box Guest Additions.

I read somewhere that you have to install "build-essentials" which I did via Synaptic. I also ran the update manager twice (once after OS installation and again after installing build-essentials). Otherwise this is all that I've done (nothing else added or installed).

What I've tried:

At the top of the Virtual Box interface I clicked on DEVICES and under that INSTALL GUEST ADDITIONS ...

This brings up the "CD" with all the files but from there I have no idea what to do. I've tried clicking on "VboxLinuxAdditions.run" and selecting "execute" but nothing seems to happen.

What do I need to do?

Please note that I have installed VirtualBox 4.2

*** EDIT ***
I found an old 2009 post on the VirtualBox website that says to install the following:

dkms
build-essential
linux-headers-generic (Ubuntu)

I already had installed "build-essential" so I checked the other two in synaptic and "dkms" wasn't installed so I installed it. I didn't install "linux-headers-generic" as it was already installed. However still no joy trying to install the Guest Additions. Either something else is needed or I'm doing it wrong or I dunno what LOL

*** EDIT #2 ***
OK well I feel dumb. I went to the folder with the files using Terminal and typed:

sudo sh ./VBoxGuestAdditions.run

And now it is installing and it works. I still don't understand why you can't just click on the file and have it work rather than have to drop down to terminal to do it *scratches head*

---

### Post by QIII on 2012-09-18
Use the terminal to navigate to the directory containing the .run file

```
cd /media/whateverYourGuestAdditionsImageIsCalled
```  

and run the .run as sudo

```
sudo sh ./VBoxLinuxAdditions.run
```

---

### Post by FulciLives on 2012-09-18
> **QIII said:**
> Use the terminal to navigate to the directory containing the .run file

```
cd /media/whateverYourGuestAdditionsImageIsCalled
```  

and run the .run as sudo

```
sudo sh ./VBoxLinuxAdditions.run
```
Thank you my friend but I just figured it out myself while you were typing!

---

