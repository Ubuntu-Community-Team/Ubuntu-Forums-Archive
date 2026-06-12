---
title: "hardy is the worst ubuntu release"
date: 2009-02-28
forum: Testimonials &amp; Experiences
---

### Post by NeferalCrossfireX on 2009-02-28
i tried installing it again today after the video playback on jaunty alpha 5 kept screwing up. i tried to install the latest nvidia driver via ctrl+alt+f1 method, whick works fine with pre hardy releases, and reboot only to get stuck in the low graphics loop, this has happened everytime i have tried to install the drivers on hardy. also why do canonical supply such an outdated driver as the default install?

---

### Post by cc8balla on 2009-02-28
Why wouldn't you install Intrepid?

---

### Post by NeferalCrossfireX on 2009-02-28
> **cc8balla said:**
> Why wouldn't you install Intrepid?

i did lol, i never really appreciated before how much of an improvement intrepid is over hardy

---

### Post by solwic on 2009-02-28
> **NeferalCrossfireX said:**
> i tried installing it again today after the video playback on jaunty alpha 5 kept screwing up. i tried to install the latest nvidia driver via ctrl+alt+f1 method, whick works fine with pre hardy releases, and reboot only to get stuck in the low graphics loop, this has happened everytime i have tried to install the drivers on hardy. also why do canonical supply such an outdated driver as the default install?

Then don't use Hardy.  

Out of curiosity...what version of the nVidia driver are you trying to install?  The 180 works great with my 8400GS.

---

### Post by NeferalCrossfireX on 2009-02-28
> **jrock612 said:**
> then don't use hardy.  

Out of curiosity...what version of the nvidia driver are you trying to install?  The 180 works great with my 8400gs.

180.35

---

### Post by solwic on 2009-02-28
> **NeferalCrossfireX said:**
> 180.35

This is from the file I keep on my HDD for when I have to reinstall Ubuntu.  I found it on the forums here, though couldn't tell you exactly where:

> 
Quote:
Originally Posted by Gias Kay View Post
An easy fix:

sudo apt-get install nvidia-180-kernel-source nvidia-180-modaliases nvidia-glx-180

Go to "System > Administration > Hardware Drivers" to enable the version 180 driver, reboot and all problems gone!


Source: [https://bugs.launchpad.net/ubuntu/+s...77/+bug/289964](https://bugs.launchpad.net/ubuntu/+s...77/+bug/289964)


Usually I just run those commands and reboot.  180 shows up in the list, and I activate it and reboot again. 

No issues here.  

Good luck!

---

### Post by NeferalCrossfireX on 2009-02-28
> **jrock612 said:**
> This is from the file I keep on my HDD for when I have to reinstall Ubuntu.  I found it on the forums here, though couldn't tell you exactly where:



Usually I just run those commands and reboot.  180 shows up in the list, and I activate it and reboot again. 

No issues here.  

Good luck!

ugh why dont canonical just make the default driver the latest one :confused:

---

