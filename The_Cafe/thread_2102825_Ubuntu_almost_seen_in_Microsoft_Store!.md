---
title: "Ubuntu almost seen in Microsoft Store!"
date: 2013-01-08
forum: The Cafe
---

### Post by Dragonbite on 2013-01-08
I was at a presentation at our local Microsoft Store last night and the subject got onto Hyper-V on Windows 8 pro.

He was showing us the management screen and only had one image to try and run... Ubuntu.

I was so hoping that the desktop would pop-up full screen because it was on their huge display that is visible everywhere inside the store as well as out into the hall of the Mall! That would have been priceless (and worth trying to get a picture of)!

Unfortunately it doesn't work on his machine and he thinks it is because his laptop has the 2 video sources (Intel on-board and Nvidia).  I don't remember the details but I have heard people have problems with the 2-card laptop systems (Lenovo in this case).

Maybe I can convince him if I can help him get it running, make it so I am ready to take a picture of it on the large screen seen through the doors with the Microsoft sign visible?

---

### Post by moseley on 2013-01-08
rofl! :popcorn: That would be priceless but be careful of posting certain items. Microsoft has squashed many for less, I am sure. ;)

---

### Post by Dragonbite on 2013-01-08
> **moseley said:**
> rofl! :popcorn: That would be priceless but be careful of posting certain items. Microsoft has squashed many for less, I am sure. ;)

Ok, I know I would have to be careful, but it would definitely be priceless.  Actually I would fear the Inquisition that might come down to find out "who is responsible for this?!" and take the employee as a heretic!

On  the other hand I haven't bought a computer for me to use since 2000 and my current one is getting bitten by the PAE-Kernel-only for Ubuntu (so 12.04 may be the last that it will run). I am tempted to get a Windows 8 machine and would be more inclined if I knew I could run Ubuntu or any other Linux distro on it.

Maybe I'll just have to Gimp the image instead.  Hmm...

---

### Post by Swagman on 2013-01-08
PAE is running on my 12:10 install

---

### Post by Dragonbite on 2013-01-08
> **Swagman said:**
> PAE is running on my 12:10 install

That's the problem.  My laptop (Pentium M, probably from about 2003-2005) cannot run a PAE kernel. Thankfully somebody took the alternate kernel (non-PAE kernel) and made an Ubuntu 12.04 Installation CD.  Unfortunately even the alternate kernel and the kernels used in Xubuntu and Lubuntu (both which used the non-PAE kernel) are all going to be PAE included kernels.

---

### Post by mastablasta on 2013-01-09
what about mini.iso?

---

### Post by sffvba[e0rt on 2013-01-09
> **Dragonbite said:**
> Maybe I'll just have to Gimp the image instead.  Hmm...

A case of photo and it didn't happen.


404

---

### Post by Dragonbite on 2013-01-09
> **mastablasta said:**
> what about mini.iso?

nope.

---

### Post by grahammechanical on 2013-01-09
> he thinks it is because his laptop has the 2 video sources (Intel on-board and Nvidia). I don't remember the details but I have heard people have problems with the 2-card laptop systems (Lenovo in this case).

As known as Nvidia Optimus technolgy and Nvidia has only recently started to work on a driver for it. The alternative?

[http://bumblebee-project.org/]("http://bumblebee-project.org/")

> I am tempted to get a Windows 8 machine and would be more inclined if I knew I could run Ubuntu or any other Linux distro on it.

Windows 8 = secure boot. At the time of its release Ubuntu 12.10 was the only Linux distribution that came anything close to working 'out of the box' on secure boot enabled machines. Some people do not have problems. Other do. Based on posts on this forum.

Regards.

---

### Post by Dragonbite on 2013-01-09
> **grahammechanical said:**
> As known as Nvidia Optimus technolgy and Nvidia has only recently started to work on a driver for it. The alternative?

[http://bumblebee-project.org/]("http://bumblebee-project.org/")



Windows 8 = secure boot. At the time of its release Ubuntu 12.10 was the only Linux distribution that came anything close to working 'out of the box' on secure boot enabled machines. Some people do not have problems. Other do. Based on posts on this forum.

Regards.

This employee, who had to start using his personal Windows 8 Lenovo laptop for part of the demonstration, said that when you first boot into the machine the first setup question they ask is whether to enable the EUFI secure boot or not.  Changing this will make the OS have to refresh or re-start from scratch or something just as nasty, but it is able to turn it off and give you the "traditional" boot up that we know works with Linux.

Ubuntu and Fedora are working on two different ways to get past EUFI.  OpenSUSE is, I think, taking Ubuntu's approach.  The only issue is that this will likely become available in the coming releases, and I don't know if current releases are capable.

---

### Post by mJayk on 2013-01-09
I just installed ub 12.10 on a win8 preinstalled laptop.  Easy as pie, just disabled EUFI and intel fast boot from the bios.  Boot from usb and jobs a gooden.

---

