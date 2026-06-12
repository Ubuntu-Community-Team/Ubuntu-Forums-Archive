---
title: "Overheating on HP Pavilion dv6-6b50sa"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bsanehi on 2012-04-02
Hi I installed Ubuntu 12.04 beta 2 using WUBI on my HP Pavilion dv6-6b50sa and my labtop is warmer and the fan is a lot louder than usual.

**[COLOR=Black]Here are the specs:[/COLOR]**

Genuine Windows® 7 Home Premium 64
Intel® Core™ i3-2330M (2.2 GHz 3 MB L3 cache  )
6 GB DDR3(1 x 2 GB, 1 x 4 GB)
500 GB SATA (5400 rpm)
AMD Radeon HD 6490M (1 GB DDR5 dedicated, up to 4 GB total)


When running windows 7 its very cool, and the fan isn't this loud. Does anyone have any solution to the overheating?

---

### Post by nothingspecial on 2012-04-04
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by chriswyatt on 2012-04-04
Deleted post as I misunderstood WUBI, I thought it was a virtual machine that ran inside Windows.

---

### Post by bcarlowise on 2012-04-04
> **bsanehi said:**
> Hi I installed Ubuntu 12.04 beta 2 using WUBI on my HP Pavilion dv6-6b50sa and my labtop is warmer and the fan is a lot louder than usual.

**[COLOR=Black]Here are the specs:[/COLOR]**

Genuine Windows® 7 Home Premium 64
Intel® Core™ i3-2330M (2.2 GHz 3 MB L3 cache  )
6 GB DDR3(1 x 2 GB, 1 x 4 GB)
500 GB SATA (5400 rpm)
AMD Radeon HD 6490M (1 GB DDR5 dedicated, up to 4 GB total)


When running windows 7 its very cool, and the fan isn't this loud. Does anyone have any solution to the overheating?


Be sure you are using the ATI drivers. The latest open source ATI drivers that get installed from the "Additional Drivers" app work well. If you're not using them, the processor is handling much of the workload that would otherwise be handled by the GPU which causes the fan to run constantly to cool down the processors. Once the drivers are installed you can run the AMD Catalyst Control Center to check information. I also recommend running the following from a terminal window:

fgl_glxgears

Yuou should see a frame rate of at least 1400FPS (see attached screenshot)

---

### Post by bsanehi on 2012-04-04
> **bcarlowise said:**
> Be sure you are using the ATI drivers. The latest open source ATI drivers that get installed from the "Additional Drivers" app work well. If you're not using them, the processor is handling much of the workload that would otherwise be handled by the GPU which causes the fan to run constantly to cool down the processors. Once the drivers are installed you can run the AMD Catalyst Control Center to check information. I also recommend running the following from a terminal window:

fgl_glxgears

You should see a frame rate of at least 1400FPS (see attached screenshot)


When I install the ATI driver from "Additional Drivers" the overheating goes away..... but I get alot of problems. When I install the driver it changes from Ubuntu 3D to 2D and Ubuntu games don't run anymore... Here is the thread I made about it.. [http://ubuntuforums.org/showthread.php?t=1949723](http://ubuntuforums.org/showthread.php?t=1949723)


**[COLOR=Red]On a side note:[/COLOR]** The brightness levels on Ubuntu 12.04 beta 2 don't work... is this a bug? when I change the brightness levels it has no effects on the screen.

---

### Post by cariboo on 2012-04-04
Wubi is a great way to test Ubuntu, but if you intent on using it for any amount of time, I'd suggest installing it directly to the hard drive. You can use the Windows disk management tools to resize you main partition, to give you enough free space to do a regular installation.

---

### Post by bsanehi on 2012-04-04
> **cariboo907 said:**
> Wubi is a great way to test Ubuntu, but if you intent on using it for any amount of time, I'd suggest installing it directly to the hard drive. You can use the Windows disk management tools to resize you main partition, to give you enough free space to do a regular installation.


I will only directly install it, once all the bugs are fixed. ;)

---

### Post by cariboo on 2012-04-04
> **bsanehi said:**
> I will only directly install it, once all the bugs are fixed. ;)

So i guess that means, that you'll never install it. :) :) :)

---

### Post by bsanehi on 2012-04-04
> **cariboo907 said:**
> So i guess that means, that you'll never install it. :) :) :)

lol no only when they fix the bugs I'm facing, like the overheating.

---

### Post by cariboo on 2012-04-04
> **bsanehi said:**
> lol no only when they fix the bugs I'm facing, like the overheating.

Your overheating bug, may because you're running  wubi, have you created a bug report?

---

### Post by kaldor on 2012-04-04
> **bsanehi said:**
> When I install the ATI driver from "Additional Drivers" the overheating goes away..... but I get alot of problems. When I install the driver it changes from Ubuntu 3D to 2D and Ubuntu games don't run anymore... Here is the thread I made about it.. [http://ubuntuforums.org/showthread.php?t=1949723](http://ubuntuforums.org/showthread.php?t=1949723)


**[COLOR=Red]On a side note:[/COLOR]** The brightness levels on Ubuntu 12.04 beta 2 don't work... is this a bug? when I change the brightness levels it has no effects on the screen.

Indeed. The fglrx (proprietary AMD) driver has much better completeness for features like power management, but the quality of the driver itself is abysmal. The default open source driver is much more stable, but lacks proper performance and power management. 

The joys of proprietary blobs :(

---

### Post by bsanehi on 2012-04-04
> **cariboo907 said:**
> have you created a bug report?

No , I'm a big Ubuntu noob it's my first time using it. I really don't know if its a bug or its just how Ubuntu works.

Like what @kaldor said maybe they just need to work on the performance and power management, to fix this issue.

---

### Post by bcarlowise on 2012-04-04
[QUOTE=bsanehi;11817140]When I install the ATI driver from "Additional Drivers" the overheating goes away..... but I get alot of problems. When I install the driver it changes from Ubuntu 3D to 2D and Ubuntu games don't run anymore... Here is the thread I made about it.. [http://ubuntuforums.org/showthread.php?t=1949723](http://ubuntuforums.org/showthread.php?t=1949723)

Ok, I don't run a WUBI Ubuntu but still what you stated sounds backwards. The AMD drivers allow full 3D performance. Maybe it has something to do with a WUBI install but that still sounds strange to me. As you can see from the attached screenshot, with the ATI Drivers installed I am running Unity3D. It's very strange what you're experiencing.

---

### Post by cariboo on 2012-04-04
> **bsanehi said:**
> No , I'm a big Ubuntu noob it's my first time using it. I really don't know if its a bug or its just how Ubuntu works.

Like what @kaldor said maybe they just need to work on the performance and power management, to fix this issue.

kaldor is talking about the open source driver, when he is talking about performance and power management. You shouldn't have any problems as far as overheating goes with the AMD/ATI driver available from Additional Drivers.

---

### Post by bsanehi on 2012-04-05
> **cariboo907 said:**
> kaldor is talking about the open source driver, when he is talking about performance and power management. You shouldn't have any problems as far as overheating goes with the AMD/ATI driver available from Additional Drivers.


I went ahead to amd website and downloaded the driver from there and the labtop doesn't really overheat that much now. :)

**[COLOR=Red]Also the only problem I'm facing now is that I can't change the brightness levels....  When I change the brightness it has no effects on the backlight hence the brightness doesn't change.[/COLOR]**

---

