---
title: "update linux-image-3.5.0-18?"
date: 2012-11-07
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2012-11-07
Yesterday, this tower raring i386 update went from -17 to -18.  External 1440x900 monitor.

Also my notebook amd64 1366x768 updated to -18.  

My Acer Aspire1 netbook raring i386 is stuck at -17.  Even apt-cache linux-image-3.5.0 shows only -17, but running apt-cache on this tower shows both -17 and -18. BTW, 1366x768 external monitor.

I tried update, synaptic, ... no luck getting the -17 to go to -18 on one of my 3 test pc's.

??  Any clue?

---

### Post by dino99 on 2012-11-07
3.7 is coming soon; its actually into the built queue

---

### Post by xeizo on 2012-11-08
3.7 seem to be in the repos now bit I guess we who use Nvidia have to wait until there's a Nvidia-driver which supports 3.7 available before we can use it, there was a new 304.62-driver yesterday but I'm not sure it supports 3.7, so it looks like 3.5.0-18 a little bit more it is ...

---

### Post by dino99 on 2012-11-08
note that the 3.7 builts in RR repo are not good, so need to wait for a new built, and "nouveau" works well with 3.7

---

### Post by xeizo on 2012-11-08
> **dino99 said:**
> note that the 3.7 builts in RR repo are not good, so need to wait for a new built, and "nouveau" works well with 3.7
 
I will never use Nouveau until it can do proper 3D(it will take long before that happens, if ever)  :P

---

### Post by jerrylamos on 2012-11-08
Quantal apt-sources change to raring updated to -18.

Just installed raring .iso it's at -17.

Did an update & upgrade still at -17.

apt-cache search shows only 3.5.0-17.  Yesterday before the install apt-cache search showed both -17 and -18.

??

---

### Post by jbicha on 2012-11-08
Take a look at the Ubuntu version page for the [Linux kernel]("https://launchpad.net/ubuntu/+source/linux"). You can see that quantal-updates has a newer version, but raring-proposed has 3.7 so we'll be getting that in raring soon.

---

### Post by pqwoerituytrueiwoq on 2012-11-08
Why is raring using the 3.5 kernel and not the 3.6 one

---

### Post by Harry33 on 2012-11-09
RR is jumping directly to 3.7.0. rc4
It is already there, see this:

[https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-0.5](https://launchpad.net/ubuntu/raring/+source/linux/3.7.0-0.5)

---

### Post by cecilpierce on 2012-11-09
Just upgraded with 3.7.0-0, seems OK

---

### Post by grahammechanical on 2012-11-09
Never did get 3.5.0-18 but now get 3.7.0-0. Raring is becoming more Ringtail than Quetzal at last.

---

### Post by zenarcher on 2012-11-09
I updated the kernel to 3.7.0, but that created a problem for me.  Now, when I boot the system up with the updated kernel, I seem to have an issue with my KVM switch in the system.  I get scrolling text, as the system loads...all okay until I get to this...then, everything just stops.

[2.48860]   USB 3-3.3: Product: 2 Port KVMSwicther
[2.488671]  USB 3-3.3: Manufacturer: No Brand
[2.488737]  USB 3-3.3: SerialNumber: 12T

The "T" at the end where it stops on the serial number is sort of below the rest of the line of text...and that's as far as the system will go.  Never have had a problem with the KVM switch before with any other kernel version.

zenarcher

---

### Post by zika on 2012-11-09
You rascals... Made me open proposed just to install linux-image, linux-headers and linux-lic-dev...
But, it works... ;)
There are some glitches it seems with grub...

---

### Post by jppr on 2012-11-09
I don´t have any chance to start the machine 3.7 kernel, system freezes immediately. 3.5 kernel works without problems.

---

### Post by Harry33 on 2012-11-09
> **jppr said:**
> I don´t have any chance to start the machine 3.7 kernel, system freezes immediately. 3.5 kernel works without problems.

Have you tried to install the kernel PPA's vanilla 3.7.0. rc4?

---

