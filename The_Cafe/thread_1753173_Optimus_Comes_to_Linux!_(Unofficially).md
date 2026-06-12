---
title: "Optimus Comes to Linux! (Unofficially)"
date: 2011-05-08
forum: The Cafe
---

### Post by dh04000 on 2011-05-08
[http://www.phoronix.com/scan.php?page=news_item&px=OTQxNg](http://www.phoronix.com/scan.php?page=news_item&px=OTQxNg)

Truly great news for Ubuntu/Linux users everywhere! And it was a community member, not a paid Xorg or Mesa dev who came up with this! Expect this in Ubuntu 12.04 LTS!


> However, an open-source community developer has took things into his own hands and began hacking on some "open-source Optimus" code. He's released the code over the weekend as prime-ng 2.0.

The prime-ng 2.0 code isn't about graphics switching, but rather offloading of work between Intel / NVIDIA GPUs. It's even working on NVIDIA Optimus laptops that don't have the graphics multi-plexer common to other laptops for switching between the graphics processors. This prime-ng code enables 3D acceleration to be used with Intel and NVIDIA graphics simultaneously.

With prime-ng 2.0, the Intel GPU is powering the display and basic desktop while any application(s) the user wishes to run through the NVIDIA GPU can be done by simply running optirun64 [the-application-name] to direct it through the NVIDIA GPU. So this implementation still is not seamless nor does it use any profiles or anything like is found with NVIDIA's Optimus implementation on Windows, but it's a big step forward.

At this point, the code also doesn't power-down the NVIDIA GPU when not in use, so it will continue burning through your battery. So far this prime-ng code has been confirmed to work on several ASUS, Alienware, Acer, and Dell notebooks.

On the plus side, it appears this code works when using the NVIDIA binary driver and just not the open-source Nouveau driver. While the Nouveau driver is nice for some, its usually lacking in terms of power management and other features, the actual ASIC support can be a hit-or-miss between Mesa and Linux kernel releases, and it doesn't provide serious 3D performance for most. This also means though that this implementation isn't sharing GEM/TTM buffers directly or anything in regards to the two drivers actually communicating and interacting with one another.

Another limitation though of this currently implementation is that NVIDIA's VDPAU video acceleration isn't working when the Intel IGP is powering the display, but there may be some ways to work around it.

This prime-ng support was written by a Danish developer, Martin Juhl, and its actual implementation involves using multiple X.Org Servers (one for each GPU) and VirtualGL to make everything work. So it's far from being a polished implementation, but hopefully this will be suitable as an interim solution until NVIDIA decides to officially support Optimus/Synergy in all of its glory under Linux. Even the official implementation though may not be as pleasant as the Microsoft Windows experience due to shortcomings with X.Org, but will eventually be fixed in Wayland.

---

### Post by karimruan on 2011-05-08
Why was I thinking Optimus Prime?

---

### Post by papibe on 2011-05-08
This is a great start!

Regards.

---

### Post by FuturePilot on 2011-05-08
> **karimruan said:**
> Why was I thinking Optimus Prime?

Probably because of [this]("http://www.phoronix.com/scan.php?page=news_item&px=ODA1OQ").
:lol:

---

### Post by karimruan on 2011-05-08
> **FuturePilot said:**
> Probably because of [this]("http://www.phoronix.com/scan.php?page=news_item&px=ODA1OQ").
:lol:

Yes, I must say... Probably :D

---

### Post by dh04000 on 2011-05-09
From what I've read about it, it works like Hydra Lucid. Meaning that multiple video cards of differing brands, including optimus set-ups will work with this code!

---

### Post by akand074 on 2011-05-09
> **karimruan said:**
> Yes, I must say... Probably :D

Wouldn't it be great if Optimus Prime came to linux... :O (whatever that means..)

---

### Post by dh04000 on 2011-05-09
If I understand this correctly, then I seriously can't wait to see this completed, and to see a similar service in Wayland (its a objective for wayland to have multi-gpu support).

Could you imagine being seamlessly be able to use any number, type, or brand of gpu together? No needing nvidia or ati prop. tech, which limits current gpu's with only Intel companions. This tech allows ANY. Any you have, even old ones.

---

### Post by medic2000 on 2011-05-09
.

---

