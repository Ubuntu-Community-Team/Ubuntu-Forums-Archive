---
title: "Key board sound control  apt missing"
date: 2012-06-28
forum: Ubuntu One (CLOSED)
---

### Post by Silvernail on 2012-06-28
Oneiric
Gnome 3

My key board has button to lower - mute - increase volume. When I ran 'bleachkit', I used too much bleach.

There use to be a sliding bar that set the sound level when I pressed the volume button. That bar no longer exist. I still have the volume icon in the top control panel of the screen, and it works.

I would like to have the keyboard button back. Anybody got any idea what I wiped out with 'bleachkit'?

TIA
Dave

---

### Post by ajgreeny on 2012-06-28
Try ```
sudo apt-get install ubuntu-desktop
```which should pull back in anything you have lost from the original installation.

I am always very wary of these "cleaner" apps as I know from experience that they often remove things that I want, but were installed by me manually with dpkg, not using synaptic or the software-centre.

---

### Post by Silvernail on 2012-06-28
> **ajgreeny said:**
> 
I am always very wary of these "cleaner" apps as I know from experience that they often remove things that I want, but were installed by me manually with dpkg, not using synaptic or the software-centre.

I am too, now. Thanks for the feed back.
Dave

---

### Post by Silvernail on 2012-06-28
```
dave@dave:~$ sudo apt-get install ubuntu-desktop
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave:~$ 

```

---

### Post by ajgreeny on 2012-07-02
Try ```
sudo apt-get install --reinstall ubuntu-desktop
``` or perhaps it is simply ```
sudo apt-get --reinstall ubuntu-desktop
``` I am not sure which is right, so try variations of this.

---

### Post by Silvernail on 2012-07-04
The first option you suggest is the correct syntex.

But that did not reinstall the missing app.

I've look thru the keyboard routines and shortcuts. Nothing I recognize.

Thanks for your feed back, guess I'll wait til I upgrade next.
D

---

