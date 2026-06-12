---
title: "Cant install virtualbox guest additions"
date: 2017-10-25
forum: Virtualisation
---

### Post by linuxyogi on 2017-10-25
I have installed the mini.iso under Virtualbox, added lxde. When I try to install **guest additions **I am getting this (the shared clipboard is not yet working so I am uploading a pic

[ATTACH=CONFIG]277272[/ATTACH].

Click to enlarge

---

### Post by linuxyogi on 2017-10-25
That VM is not even starting any more. The (black) screen flashes and ends up with a black screen.

---

### Post by ian-weisser on 2017-10-25
You must install DKMS or the kernel headers so guest-additions can compile.
Neither is included on the mini .iso

---

### Post by Neffscape on 2017-11-02
Which version of VirtualBox Guest Additions are you using? Guest Additions image with the 5.2.0 release fails to work with recent Linux guest kernels.Install build-essential, DKMS and kernel headers and then check if [this image]("https://www.virtualbox.org/download/testcase/VBoxGuestAdditions_5.2.1-118447.iso") solves the problem.

---

