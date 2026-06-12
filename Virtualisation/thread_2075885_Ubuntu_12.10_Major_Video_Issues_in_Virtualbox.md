---
title: "Ubuntu 12.10 Major Video Issues in Virtualbox"
date: 2012-10-24
forum: Virtualisation
---

### Post by weirddan455 on 2012-10-24
Since 12.10 I'm having major video issues in Virtualbox.  Apart from it being slow as Christmas due to [forcing LLVMPipe]("http://www.phoronix.com/scan.php?page=news_item&px=MTIxMTg") the mouse is jumping around like a Mexican jumping bean.  It's especially noticible when scrolling a window such as the terminal.  It seems to like to bounce to the top and sides of the screen for a split second before returning and does this multiple times making the desktop virtually unsuable (pun not intended).

In 12.04, I was able to make the video better by enabling the Virtualbox drivers.  I never had any of the curser bouncing issues but I did have cursor flickering in 12.04 (which is still present in 12.10).  The cursor flickering went away in 12.04 when I installed the vbox drivers.  In 12.10, the "Additional Drivers" app appears to be gone.  I clicked the vbox drivers in System Updates but it didn't have any effect.  In 12.04 when I installed the vbox drivers it let me resize the screen by moving the vbox window and also added a vbox kernel module (vboxvideo I believe was the name) I could see with lsmod.  In 12.10, I see no such kernel module and can't resize the window.

Why does it seem like every Ubuntu release gets worse and worse?  My host machine is Arch Linux using Virtualbox 4.2.2.

---

### Post by mozkill on 2012-10-24
I agree. I am having some problems with the Virtualbox adapter package.   I disagree that it works properly using Virtualbox 4.2.2 with Ubuntu 12.10.

---

### Post by weirddan455 on 2012-10-24
OK I "fixed" the mouse jumping around by simply disabling mouse integration in Virtualbox.  I'm still working on trying to get the guest-additions installed though so I can up the resolution and hopefully get some hardware acceleration.  In 12.04 it was so easy, just click it in "Additional Drivers".  I don't know what the deal is here with 12.10.

---

### Post by mozkill on 2012-11-15
I played with it more and still had no success.  Linux Mint, on the other hand, works right out of the box and I didn't even need to install the guest additions.   I also never had an issue with Ubuntu 12.04.

What I am expecting here is the auto-resizable screen resolution that VirtualBox is able to provide via the VM.

---

### Post by pkadeel on 2012-11-15
> **mozkill said:**
> I played with it more and still had no success.  Linux Mint, on the other hand, works right out of the box and I didn't even need to install the guest additions.   I also never had an issue with Ubuntu 12.04.

What I am expecting here is the auto-resizable screen resolution that VirtualBox is able to provide via the VM.
On all guest OSs whether windows or linux "auto-resizable screen resolution" is achieved after installing the "guest additions". It is available from Guest menu > Devices
I have not so far tested it on 12.10 guest but I am sure it will work as expected.

---

### Post by markbl on 2012-11-15
> **pkadeel said:**
> On all guest OSs whether windows or linux "auto-resizable screen resolution" is achieved after installing the "guest additions". It is available from Guest menu > Devices
I have not so far tested it on 12.10 guest but I am sure it will work as expected.
3D acceleration does not work in guest additions for current VB 4.2.4 (and earlier) with a Ubuntu 12.10 guest. With no 3D, Ubuntu 12.10 falls back to LLVMpipe so it means 12.10 is very slow, unbearable for me for example. See [https://forums.virtualbox.org/viewtopic.php?f=1&t=52327](https://forums.virtualbox.org/viewtopic.php?f=1&t=52327).

---

