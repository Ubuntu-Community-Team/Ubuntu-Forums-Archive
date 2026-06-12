---
title: "any way for virtual raspberry pi?"
date: 2017-01-16
forum: Virtualisation
---

### Post by a.dusty.trail on 2017-01-16
I just got a raspberry pi and would like to try out all the different distributions for it virtually.
Can you install ubuntu mate arm (or lubuntu)on a virtual machine in ubuntu 16.04 64 bit lts?

---

### Post by Irihapeti on 2017-01-16
*Thread moved to **Virtualisation** for a better fit.*

Apparently, the ARM images won't run in VirtualBox or VMWare, but they will run in QEMU. I found [http://www.makeuseof.com/tag/emulate-raspberry-pi-pc/](http://www.makeuseof.com/tag/emulate-raspberry-pi-pc/) which looks like it could be a good starting point.

---

### Post by a.dusty.trail on 2017-01-16
Sadly it looks like the images are at least 3 years old for that. I was hoping for something much more current (and ubuntu)

---

### Post by Irihapeti on 2017-01-16
I've just installed QEMU here (yay, something else to distract me from other stuff! :) ) and after a very quick look, I would think that you could make it work with any of the Ubuntu images, or others. I may get a chance to look later today.

I've been thinking about getting a Pi, so it won't entirely be wasted time. In the meantime, someone else may have something to add.

---

### Post by a.dusty.trail on 2017-01-16
Thank you
I'll Get qemu later in the week and do some research

---

### Post by Irihapeti on 2017-01-17
Unfortunately, after a bit of investigation, it seems that it's possible to do, but rather complicated. As I have no immediate use for doing this, I'd rather leave it. It might be easier just to get some SD cards, install the images to the cards and swap them around when you want to try something new.

---

### Post by KillerKelvUK on 2017-01-17
> **a.dusty.trail said:**
> I just got a raspberry pi and would like to try out all the different distributions for it virtually.
Can you install ubuntu mate arm (or lubuntu)on a virtual machine in ubuntu 16.04 64 bit lts?

Hey, what is it about the OS's you want to "try out"?  If you're new to linux and this is about getting to know the userspace tools and filesystem then you can do this with a normal x86_64 image and be close enough to get you moving on the arm variants.  Whilst arm will have differences in packages available the Mate desktop running on a arm architecture will be v.similar to Mate running on an x86_64?

Regardless your request interested me enough to google around and like Irihapeti said there are guides on doing this although some look dated.  

[https://www.raspberrypi.org/forums/viewtopic.php?f=29&t=37386](https://www.raspberrypi.org/forums/viewtopic.php?f=29&t=37386)  <--This article looked promising, short and sweet although if you're new to linux it will look off-putting.  I noticed that a key hyperlink was now dead but it seems so did another reader and has kindly made the required files available via github here [https://github.com/dhruvvyas90/qemu-rpi-kernel](https://github.com/dhruvvyas90/qemu-rpi-kernel).  The github repo includes a kernel update that is only 4 months old and so would suggest compatibly with more recent Pi OS updates.  I've not done extensive reading but these articles look Debian or Raspbian centric so porting the approach for Ubuntu will likely need further work.

---

### Post by a.dusty.trail on 2017-01-19
Basically I just got my pi last week. There are any number of different distributions of Linux and other operating systems. I've already tried lubuntu and mate and I expect that I will go through many more to see what they offer. While I could just swap cards on the pi and try each one out I thought if there was a way to try out everything virtually that would be much easier. Right now I switch between the pi and my desktop when I'm setting up the pi and researching how to set up the pi.

Virtually I could try out everything and if I liked it I could transfer the configuration to the pi.
I thought since the pi hardware was standardised it would not be too difficult.
But if no one has blazed the trail Im not technically able to.

I was expecting to find something like the Android emulators I've seen.

---

