---
title: "Upgrading to 16.04 from 15.10 on System76 Lemur (new)"
date: 2016-02-17
forum: System76 Support
---

### Post by frogotronic on 2016-02-17
Hi,

  Dumb question, but it's my first System76 machine - one of the new (SkyLake) i7 Intel Lemur Laptops - but System76 will give us the nod when it's okay to upgrade (i.e. when their/your System76 Driver is available)?

Thanks,
Andor

---

### Post by him610 on 2016-04-08
Not a dumb question at all. I have owned a System76 Pangolin P9 (out of production now) for the past 3-1/2 years. It originally shipped with Ubuntu 12.04. When 14.04 came out, I received a message from System76 informing me that it was okay to download and install. I can only assume they will do the same for 16.04. 
They need time to update the System76 drivers and to do some testing first.

---

### Post by frogotronic on 2016-04-09
Okay, thanks!  Me and a friend both have System76 Lemurs (6th gen Intel) and are looking forward to the new upgrade (with Kernel 4.4.x), as they've fixed the Intel Sky Lake video stack on kernel 4.3+ (15.10 is using Kernel 4.2).

---

### Post by foobar66 on 2016-04-09
I just upgraded my system76 serval to 16.04.
After the installation just do:

> sudo -s
> apt-add-repository -ys ppa:system76-dev/stable
> apt-get update
> apt-get -y install system76-driver
> apt-get -y install system76-wallpapers

If you have an nvidia card do:


> apt-get -y install system76-driver-nvidia

---

### Post by frogotronic on 2016-04-20
How'd it go?  Everything working a-ok?

---

### Post by Kale_Freemon on 2016-04-20
When 15.10 came out, my Lemur from last year updated without a hitch. That being said, do use caution when upgrading. It may be wise to wait until someone is able to actually confirm that the upgrade works flawlessly.

---

### Post by beameup on 2016-04-21
you could just flip an email to support, but most likely you are good to go

---

### Post by him610 on 2016-04-21
It has been announced on Google+ that Ubuntu 16.04 is available for download.
> Ubuntu 16.04 LTS is here! Explore all the features of 16.04 including: Snaps, moving the Unity Launcher, improved privacy settings by default, Python3.5 and so much more! To update, follow our instructions here: [http://bit.ly/1Symjed&#65279;](http://bit.ly/1Symjed&#65279;)

---

### Post by Kale_Freemon on 2016-04-22
Works pretty well on my Lemu5! If you try it on your new Lemur, let us know how it goes!

---

### Post by frogotronic on 2016-05-09
Hello,

   Been having major issues with 16.04, even with a clean install.  Turns out the kernel (4.4.5) doesn't have the Intel HD graphics driver properly installed.  Trying out the Ubuntu Kernel PPA 4.4.8 solves most of my freeze issues and/or resolution and output issues.

  Bug Report is here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1559308](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1559308)

---

### Post by Kale_Freemon on 2016-05-16
> **cement_head said:**
> Hello,

   Been having major issues with 16.04, even with a clean install.  Turns out the kernel (4.4.5) doesn't have the Intel HD graphics driver properly installed.  Trying out the Ubuntu Kernel PPA 4.4.8 solves most of my freeze issues and/or resolution and output issues.

  Bug Report is here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1559308](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1559308)

Odd, as it has been working just fine on my machine with Intel HD Graphics. Have you, by chance, installed the drivers directly from Intel? [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

That's what I've been running. Not sure if it'll make any difference, but worth a try.

---

### Post by frogotronic on 2016-05-16
> **Kale_Freemon said:**
> Odd, as it has been working just fine on my machine with Intel HD Graphics. Have you, by chance, installed the drivers directly from Intel? [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

That's what I've been running. Not sure if it'll make any difference, but worth a try.

Yes, that would make a difference.  It turns out that Ubuntu/Linux kernel developers didn't properly incorporate the Intel HD drivers in the 4.3 and 4.4.4 and 4.4.5 series kernels.  So, if one is running the stock kernels, one DOES not have the proper drivers.  I'm using the PPA kernel (4.6rc7 and it works now).

---

### Post by jlh68 on 2016-05-19
My upgrade from 15.10 to 16.04LTS went smooth without any problems.  Be sure to update the System76 driver.

---

