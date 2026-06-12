---
title: "Backwards compatability of hardware for newer kernels"
date: 2017-05-18
forum: Ubuntu, Linux and OS Chat
---

### Post by SlickWilly18 on 2017-05-18
This is more of a rant with a philosophical angle. Why on earth would a new release of ubuntu lose hardware support when the PREVIOUS version was compatible. I'm thinking of of a certain TP link wireless dongle that was top rated for linux until kernel 3.17 which broke support. WHY?! Shouldn't kernels be backwards compatible for hardware Support? Is anyone else fuming over this?

---

### Post by SlickWilly18 on 2017-05-18
I really am curious as to why this is so. Are new kernels built from Scratch?

---

### Post by QIII on 2017-05-18
Hello!

Was there a driver that had to be installed to run it?

---

### Post by mastablasta on 2017-05-19
> **SlickWilly18 said:**
> Is anyone else fuming over this?

not over TP Link, but otherwise, yes. :)

good thing there are LTS and distros with long support period.

also troublehsoot first and if it really is not compatible, post a bug i guess.

---

### Post by SlickWilly18 on 2017-05-22
For my new usb wifi dangle, no. The device was automatically recognized. All I needed to do was insert the adapter and reboot.
For my old trendnet pci wifi card, I needed to install the 64bit xp version of of the driver within ndiswrapper. Using this command  ```
sudo ndiswrapper -i net819xp.inf
```
From inside the driver's 64bit xp folder that I downloaded from trendnet's website. Once I installed that driver, the card would only work some of the time, and would always give me the soft lockup error on reboot or shutdown. I ended up getting the panda wireless card adapter and never looked back. It even supports monitor mode and packet injection for all you kali folks (I tested this).:P

---

### Post by mastablasta on 2017-05-23
backwards compatibility is definitelly not assured.

I have HP laptop which when i install i think 13.04 it was all working out of the box. then version 13.10 a few buttons were no longer working. version 14.04 more buttons are no longer working, also unable to turn some things (bluetooth, wi-fi) of an on as i could easilly do before. 

for bottons i found workarround for some, but not for all. mostly function keys etc. anyway my point is it all worked. and i mean all in the first version i installed on it. 

i stayed on 14.04 on it , because with 16.04 i will lose the GPU driver support. hopefully by the time life for 14.04 ends, the opensource Radeon driver will be fully ready for it. if the PC is still working that is. which it seem like it will.

---

### Post by dark. on 2017-05-23
If backwards compatibility is not assured with oldest possible hardware in newer kernels, is there a way i can use older kernel for a old hardware that may not work with newer kernel?
For example: A old hardware (any) doesn't work with kernel 4.10 but works with kernel 3.16.
Is there a program i can use to assign kernel 3.16 to only that old hardware while rest of the system uses newer kernel 4.10?
Is it possible to manage kernel versions?

---

