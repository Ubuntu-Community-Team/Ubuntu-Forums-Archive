---
title: "Activating VGA monitor output in Ubuntu"
date: 2011-04-16
forum: Ubuntu Studio
---

### Post by Ventai on 2011-04-16
Hi there, 

I'm running Ubuntu (Studio) 10.04 (Lucid) and need to try and get the video output from my motherboard to hook up to my monitor. 

This stems from an earlier attempt to get my NVidia GTX460 to work, it was with installing the community version of the driver (which seemed like, and I was advised was the best option). Essentially, I couldn't access my system after installation. 

I managed to reset the monitor output to the default config, which allowed the card to run with a terrible (default) driver. 

I'd just like to hook it up to the motherboard VGA output for now, but there doesn't seem to be an option in the monitor setup (I did check while the VGA was plugged in. The GTX was in through DVI). 

If anyone could advise me how to go about activating Ubuntu to display through the motherboard VGA I'd appreciate it .... 

Thanks

---

### Post by jejeman on 2011-04-16
It's not clear what you trying to do. Do you want to use both cards at the same time? I don't think that it is posible.
If you want to just use the onboard card you need to pull out the Nvidia card, and than to turn on onboard card in Bios. Ubuntu will see the onboard card and useit with no problem.

---

### Post by Ventai on 2011-04-16
> **jejeman said:**
> It's not clear what you trying to do. Do you want to use both cards at the same time? I don't think that it is posible.
If you want to just use the onboard card you need to pull out the Nvidia card, and than to turn on onboard card in Bios. Ubuntu will see the onboard card and useit with no problem.

Ah, I wanted to use the onboard for Ubuntu, but the GTX for the Windows install I also have on the same disk. So according to your suggestion that's not possible. 

Damn, to install the official NVidia driver was a VERY convoluted process last time I checked, logging out of X-Windows, and a whole bunch of other stuff I haven't got time for right now . . 

Thanks for your time anyway!

---

### Post by jejeman on 2011-04-16
As I said I dont think that is posible, because personaly never saw that. Maybe it is posible, it's Linux after all ;)
But the point is that you don't need that. Nvidia driver is easy install, just use jockey-gtk for that. Never use the driver from nvidia web site, always use the driver that comes from ubuntu repository (if you want your life to be easyer).
Open the system>administration>Hardware drivers and install the nvidia driver. Simple as that.

---

### Post by Ventai on 2011-04-16
> **jejeman said:**
> As I said I dont think that is posible, because personaly never saw that. Maybe it is posible, it's Linux after all ;)
But the point is that you don't need that. Nvidia driver is easy install, just use jockey-gtk for that. Never use the driver from nvidia web site, always use the driver that comes from ubuntu repository (if you want your life to be easyer).
Open the system>administration>Hardware drivers and install the nvidia driver. Simple as that.


I had another go and started another thread: [http://ubuntuforums.org/showthread.php?t=1730758](http://ubuntuforums.org/showthread.php?t=1730758) 

It looks like I  had jockey-gtk already installed. I ran the Python script in /usr/bin but got the hardware drivers message:-

'No proprietary drivers are in use on this system' 

arrrghh :)

---

### Post by jejeman on 2011-04-16
Well, as it acourd to me, you have new card, so maybe the nvidia driver for 10.04 is not supporting it. In link you have posted it says that with ubuntu 10.10 there are no problems instaling drivers via jockey-gtk.

regarding to use of onboard card look in to this therads:
[http://www.techrepublic.com/forum/questions/101-215519](http://www.techrepublic.com/forum/questions/101-215519)
[http://arstechnica.com/civis/viewtopic.php?f=16&t=122577](http://arstechnica.com/civis/viewtopic.php?f=16&t=122577)

---

### Post by Ventai on 2011-04-17
Upgrading the OS sorted it. . 

Thanks for your time!

---

