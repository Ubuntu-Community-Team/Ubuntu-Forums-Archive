---
title: "The Nvidia problem and how I got around it."
date: 2008-10-30
forum: Testimonials &amp; Experiences
---

### Post by indiapavan on 2008-10-30
It has been less than a week since I installed Ubuntu on my AMD64 PC. At first I did not know that 32 bit Operating systems are not meant for 64 bit PCs. But through a friend I got to know that I needed a 64-bit version. I got that without much difficulty and installed the Hardy Heron release for 64-bit desktop. I *thought* all was well. But as soon as I installed/enabled the drivers for my nVidia GeForce 6100  graphic card, I was facing huge display problems.

I started a thread here on the forums. But the help given was not enough to solve my problem. I don't know what prompted me to do it, but I just lowered the screen resolution and the refresh rate of my monitor. Then I switched back and it worked perfectly. I still do the above mentioned ritual every time I boot-up my PC. While this works, I am eagerly waiting for the 8.10 release. I hope these problems are solved in that release.

---

### Post by Riffer on 2008-10-30
You can run 32 bit Ubuntu, I have an AMD64 and that's what I run.

On one of your threads you were asked to install "envy", did you?  To install go to System > Administration > Synaptic and install envyng, envy-common and envyng-gtk.  Open envyng (should be in Applications > System tools) and use the option to uninstall present driver.  This is important installing the new driver won't work unless you do.  Reboot.  Open envyng again choose the option to install nVidia driver.  When done (it takes awhile) reboot again.  You should be good to go.

---

### Post by indiapavan on 2008-10-30
> **Riffer said:**
> You can run 32 bit Ubuntu, I have an AMD64 and that's what I run.

On one of your threads you were asked to install "envy", did you?  To install go to System > Administration > Synaptic and install envyng, envy-common and envyng-gtk.  Open envyng (should be in Applications > System tools) and use the option to uninstall present driver.  This is important installing the new driver won't work unless you do.  Reboot.  Open envyng again choose the option to install nVidia driver.  When done (it takes awhile) reboot again.  You should be good to go.

I did try to install envy. The problem is that my current driver (nvidia-glx-new) is returning an error every time it is un-installed.

---

### Post by Riffer on 2008-10-30
ok whats the error?

---

### Post by Riffer on 2008-10-30
Ok weird idea.  Paste into your terminal the following 

> sudo dpkg-reconfigure xserver-xorg

This will get you into a generic driver/config.  Now try uninstalling your nVidia driver.

---

