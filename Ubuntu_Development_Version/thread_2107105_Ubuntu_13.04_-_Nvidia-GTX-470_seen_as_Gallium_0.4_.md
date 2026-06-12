---
title: "Ubuntu 13.04 - Nvidia-GTX-470 seen as Gallium 0.4 on NVC0"
date: 2013-01-21
forum: Ubuntu Development Version
---

### Post by gokh on 2013-01-21
[IMG]http://tinypic.com/r/mu8let/6[/IMG][IMG]http://tinypic.com/r/mu8let/6[/IMG]
[IMG]http://i48.tinypic.com/mu8let.png[/IMG]

Hi friends, I'm a new user and I want to ask about my graphics card driver.  I have nvidia-gtx-470 graphics card and i make a fresh install of Ubuntu-13.04 from daily live site a few minutes ago. Here is problem or not gtx-470 seens like picture above. i try to install nvidia-current but it is not usefull than Gallium 0.4 on NVC0, i think Gallium 0.4 is more better than nvidia-current. Finally i decided to install latest nvidia driver from nvidia web site, but it gives this error "[COLOR=Red]Unable to build Kernel[/COLOR]". What can i do to install latest driver for nvidia or if it is a good idea to work with Gallium drivers. 
if any expert help me , i'll be very pleased... Thanks for all.

---

### Post by dino99 on 2013-01-21
this U+1 forum already have some threads about nvidia driver installation; you might read them first.

and use the nvidia-313 package from xorg-edgers ppa

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by grahammechanical on 2013-01-21
Here is some information based upon my own experience and research. It might help you understand what is happening.

You are using the open source Nouveau driver. Gallium is a component of Nouveau.

[http://en.wikipedia.org/wiki/Gallium3D]("http://en.wikipedia.org/wiki/Gallium3D")

NVC0 is an Nvidia code name for your Nvidia graphics adapter. This links shows some of the code names used by Nvidia for some of their chips.

[http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units]("http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units")

I also have found the Nouveau driver to be very good and Nvidia drivers to be buggy. The Additional Drivers tab in Software Sources now gives me eight drivers to try. You may find that once you get a Nvidia driver installed that the Details page will give you a label for your video adapter that is more understandable.

It is all part of being a Community Volunteer Tester. With a little bit of curiosity we can learn a lot from being a Community Volunteer tester.

Regards and welcome.

---

### Post by ventrical on 2013-01-25
It also assumed itself on my ATi card and works horribly.

---

### Post by gokh on 2013-01-27
i installed NVIDIA-Linux-x86_64-310.32 drivers and my problem was solved. Thanks for replies.

---

### Post by gokh on 2013-01-27
> **dino99 said:**
> this U+1 forum already have some threads about nvidia driver installation; you might read them first.

and use the nvidia-313 package from xorg-edgers ppa

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

it only requires  NVIDIA-Linux-x86_64-310.32 drivers. Thanks for your reply... it was solved.

---

### Post by gokh on 2013-01-27
> **ventrical said:**
> It also assumed itself on my ATi card and works horribly.

you must try ati drivers to solve this problem, and try to install mesa-utils.

[COLOR="Red"]sudo apt-get install mesa-utils[/COLOR], but normally in ubuntu-13.04 it is installed when you updated your system.

---

