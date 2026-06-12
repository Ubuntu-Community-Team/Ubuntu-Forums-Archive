---
title: "Nvidia driver 319.60 does not play well with kernel 3.12.0-1-generic"
date: 2013-10-31
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2013-10-31
Got a bunch of updates this morning and the 3.12 kernel was one of them. I had the Nvidia driver 319.60 installed and it worked well on the 3.11.0-12 kernel.
But while installing the 3.12.0-1 kernel, that driver broke the kernel. It got some error and would not boot into that kernel. 
Luckily I was still able to get into the 3.11.0-12 kernel and uninstall that driver and install the 304.88 driver and now I am back in business. ;)

I guess Trusty does not like the newer driver. Any thoughts?

---

### Post by howefield on 2013-10-31
I had the same issue, uninstalled 319.60 and tried the 319.32 driver which works fine.

---

### Post by OGpmpdog on 2013-10-31
> **Cavsfan said:**
> Got a bunch of updates this morning and the 3.12 kernel was one of them. I had the Nvidia driver 319.60 installed and it worked well on the 3.11.0-12 kernel.
But while installing the 3.12.0-1 kernel, that driver broke the kernel. It got some error and would not boot into that kernel. 
Luckily I was still able to get into the 3.11.0-12 kernel and uninstall that driver and install the 304.88 driver and now I am back in business. ;)

I guess Trusty does not like the newer driver. Any thoughts?


Hi there!!  I was SO pumped to finally see the 3.12 kernel, but the installation error made me frown.

I was also running Nvidia 319; I upgraded to Nvidia 325, and all is great!!:P

Except...

---

### Post by Cavsfan on 2013-10-31
> **howefield said:**
> I had the same issue, uninstalled 319.60 and tried the 319.32 driver which works fine.

Think I'll try the 319.32 driver thanks!

> **OGpmpdog said:**
> Hi there!!  I was SO pumped to finally see the 3.12 kernel, but the installation error made me frown.

I was also running Nvidia 319; I upgraded to Nvidia 325, and all is great!!:P

Except...

Except wat? :P

---

### Post by OGpmpdog on 2013-10-31
> **Cavsfan said:**
> Think I'll try the 319.32 driver thanks!



Except wat? :P

I posted a "sound shuts off" thread :P

---

### Post by Cavsfan on 2013-10-31
@howefield, do you think there will be workable drivers coming out of x-swat and and xorg-edgers ppas for this LTS?
I could easily install the latest Nvidia driver directly from their website on Lucid 10.04 LTS but, when Precise 12.04 LTS was released those newer drivers broke my installation.

I just kept the one from the regular repositories. 

Just curious. :)

---

### Post by kevpan8152 on 2013-10-31
> **Cavsfan said:**
> Got a bunch of updates this morning and the 3.12 kernel was one of them. I had the Nvidia driver 319.60 installed and it worked well on the 3.11.0-12 kernel.
But while installing the 3.12.0-1 kernel, that driver broke the kernel. It got some error and would not boot into that kernel. 
Luckily I was still able to get into the 3.11.0-12 kernel and uninstall that driver and install the 304.88 driver and now I am back in business. ;)

I guess Trusty does not like the newer driver. Any thoughts?

Yeah the first wave of NEW Files (NOT just EXISTING ones) came down the pipe this morning Chicago Time when I went to Update 14.04 and Kernel 3.12.0.1-generic was one of them! I feel Bad for you NVIDIA guys.

---

### Post by tad1073 on 2013-10-31
> **kevpan8152 said:**
> Yeah the first wave of NEW Files (NOT just EXISTING ones) came down the pipe this morning Chicago Time when I went to Update 14.04 and Kernel 3.12.0.1-generic was one of them! I feel Bad for you NVIDIA guys.

Using the nvidia driver increases by boot time by about 40 seconds but the default driver (gallium) I get booted up in about 15 seconds and that's from power on to desktop.

---

### Post by Cavsfan on 2013-11-01
> **kevpan8152 said:**
> I feel Bad for you NVIDIA guys.

Don't worry about me. I would never have any other card besides Nvidia. ;)

> **tad1073 said:**
> Using the nvidia driver increases by boot time by about 40 seconds but the default driver (gallium) I get booted up in about 15 seconds and that's from power on to desktop.

Mine boots up within seconds. No problems here and I just have a middle of the road Geforce 9800 GT with 1GB.

---

### Post by Yellow Pasque on 2013-11-03
May be relevant: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-319/+bug/1245007/comments/2](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-319/+bug/1245007/comments/2)

---

### Post by Cavsfan on 2013-11-05
> **Temüjin said:**
> May be relevant: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-319/+bug/1245007/comments/2](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-319/+bug/1245007/comments/2)

I believe that bug was fixed recently. It shows 319.60 was released 15 hours ago. [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-319](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-319)
My system updated from 319.32 to 319.60 and upon reboot everything looks good.

---

### Post by Yellow Pasque on 2013-11-05
^Thanks (I closed the bug)

---

### Post by Cavsfan on 2013-11-05
> **Temüjin said:**
> ^Thanks (I closed the bug)

Great! Thank you!

---

### Post by Cavsfan on 2013-11-05
Is it safe to go bleeding edge with “xorg crack pushers” team ppa? I see they have added Trusty.

---

### Post by Yellow Pasque on 2013-11-06
Their package does include a 3.12.x patch, so it should at least install without issue.

---

### Post by Cavsfan on 2013-11-06
> **Temüjin said:**
> Their package does include a 3.12.x patch, so it should at least install without issue.

Thanks for the info! I might hold off for a while. I updated my driver on windows 7 and it caused some serious problems. Had to roll it back and all is fine.
I'll go with the x-swat ppa rather than the “xorg crack pushers” team ppa if I do though. My card is not that new and I don't need cutting edge any way.

---

### Post by Ian_Worrall on 2013-11-07
Nvidia have just released 331.20, which now supports kernels 3.11 & 3.12 out of the box.
[http://www.phoronix.com/scan.php?page=news_item&px=MTUwNjA](http://www.phoronix.com/scan.php?page=news_item&px=MTUwNjA)

---

### Post by tad1073 on 2013-11-07
The first installation will fail but all you need to do is reboot and reinstall the driver with the "--no-unified-memory" flag or atleast that is what I had to do.

---

