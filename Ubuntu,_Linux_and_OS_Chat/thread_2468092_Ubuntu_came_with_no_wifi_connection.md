---
title: "Ubuntu came with no wifi connection"
date: 2021-10-18
forum: Ubuntu, Linux and OS Chat
---

### Post by morrownr on 2021-10-18
> **chili555 said:**
>  In almost every case, they have almost no concern for the 3% or so of Linux users and therefore don't provide a working driver.



Good Monday morning to you Chili555,

While we wait for the reply from jorgge, please allow me to wax poetic on the topic of wireless driver support for Linux. You are aware of the work that I put into helping Linux users successfully use USB WiFi adapters and part of that effort requires that I monitor the Linux-Wireless list where discussions, patches and additions flow freely. Monitoring that list allows me to have a good view of where we are with WiFi drivers. When it comes to drivers for the chipsets on the various cards, Intel, Atheros and Mediatek appear to be at or near 100% coverage for their products and I am talking about mac80211 style in-kernel drivers (what we want.) Even Realtek seems to be onboard as they are in the process of getting a driver for their 8852ae (ax) chipset in the kernel. The gaps in coverage are becoming very limited. That is not to say that users such as jorgge won't see an issue at times because users with bleeding edge systems may have cards where the driver has simply not found its way into the distro they are using due to lag between driver being in the kernel and the kernel finding its way into the new distro they are using.

Over on the USB WiFi adapter front, we have seen a lot of progress over the last several years. Certainly this is a niche market and there are only 2 providers of chipsets but we have mac80211 style in-kernel drivers from Mediatek for their mt7612u (ac1200) and mt7610u (ac600) chipsets and basically all modern dual band chipsets from Realtek have drivers available though I advise users to take the Mediatek route.

We are seeing improvements in other areas as well. Companies supplying computer products in this day in time are unwise to ignore Linux, as many used to do, because it is by far and away the most used operating system in the world. I'm not just talking about the 100% market share on the Top500 Supercomputers but also the billions of devices running Android and Chromebooks and servers and Raspberry Pi's and the list goes on. Learning Linux can have many benefits and I hope this initial snag that jorgge has experienced does not cause him to turn away.

Regards

---

### Post by coffeecat on 2021-10-18
@morrownr, I've split your post from the original support thread here - [https://ubuntuforums.org/showthread.php?t=2468052](https://ubuntuforums.org/showthread.php?t=2468052) - to create a new discussion thread in Ubuntu, Linux & OS Chat. This was at the request of chili555 who said he would reply to you here. That leaves the original thread on-topic for a specific support question, and creates a new discussion thread which should be interesting. I, for one, will subscribe to it.

---

### Post by morrownr on 2021-10-18
coffeecat,

No problem.

chili555,

As you know, I put a lot of spare time into helping Linux users. You do as well, we just do different things. My efforts at making quality drivers and information available for USB WiFi users causes me to have to dig and research a lot. My reply was a reaction to your lines about "the state of WiFi" on Linux for the lack of a better way of putting it. There is no doubt that things were bad 15 years ago... but a heck of a lot of progress has been made particularly over the last 5 years. At present, we have very wide coverage of good mac80211 in-kernel drivers that handle cards and adapters. Intel, Atheros and Mediatek are all in.

Is the state of Linux wireless drivers as bad as you appeared to indicate? If we look at the wireless chipsets for modern cards and adapters, say from ac600 on, I can't name a single chipset that does not have a Linux driver. Now we can argue about the pros and cons of Realtek's out-of-kernel USB drivers but even those drivers are getting to where the are pretty good. I just brought two new drivers online for the 8812au and 8811au chipsets. I'm surprised by just how good they are. Not as good as Mediatek's in-kernel drivers but not bad at all by historical standards.

I understand that as long as Linux keeps its current development model, we will see some delays in getting drivers for some hardware out there into the lastest distros but that can be worked on and progress can be made. Times change and progress can be continued.

I've been using Linux since '94 and I am proud of the progress that has been made. My efforts to get information out there regarding adapters that use the in-kernel Mediatek drivers has been helping a lot of Linux users find adapters that they are happy with. [https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi) is up to an average of over 130 hits per day and the overall site, [https://github.com/morrownr?tab=repositories](https://github.com/morrownr?tab=repositories) , is up to around 4000 hits per week. 

My earlier reply was not intended to start a ruckus. What I read caught me by surprise as I see Linux wireless support in a very positive light these days.

Regards,

Nick

---

### Post by chili555 on 2021-10-18
> Companies supplying computer products in this day in time are unwise to ignore Linux, as many used to do, because it is by far and away the most used operating system in the world. 

Quite correct; however, no one goes to Amazon to buy a USB wireless adapter for their supercomputer or their Android phone. However, when one buys a USB wireless adapter from Amazon, Newegg or even Ebay, it almost never comes with a driver CD or download link for a *working* Linux driver. 

As well, we both regret that the lions share of the desktop market is still dominated by Windows; simply because when a new user bought the computer, Windows was preinstalled and the built-in wireless worked.

> Is the state of Linux wireless drivers as bad as you appeared to indicate?

Not at all. It's only bad for the reasons you already acknowledged:

> That is not to say that users such as jorgge won't see an issue at times because users with bleeding edge systems may have cards where the driver has simply not found its way into the distro they are using due to lag between driver being in the kernel and the kernel finding its way into the new distro they are using.

Every six months or so, we go through the same things. This year, it is Intel's new Wifi6 products. The driver doesn't appear until kernel version 5.11. That means that lots of LTS Ubuntu users won't have it.

> I understand that as long as Linux keeps its current development model, we will see some delays in getting drivers for some hardware out there into the lastest distros but that can be worked on and progress can be made. Times change and progress can be continued.
Exactly!

No ruckus here. My only point was that if a new user brings a shiny 2021 laptop to the table, depending on what Ubuntu version is installed, the wireless might or might not work, unlike Windows.

By the way, none of my comments are directed at quality. Almost every device I am aware of works perfectly well once the correct driver is installed. Well, actually, the ath10k_pci devices are a bit funky.

---

### Post by grahammechanical on 2021-10-18
Can I give the point of view of a home user with next to no experience of this subject?

Fourteen years ago I needed a new computer. I was reading computer magazines and found out about Linux and Ubuntu. From the articles I read I learned not to expect all the hardware to work if I bought a machine with an OS preinstalled. On the other hand if I built my own computer I could chose hardware that through research I could have confidence that Linux would have all the drivers needed. I also learnt not to buy the latest hardware (which I could not afford) because it was unlikely that Linux would have drivers for the latest hardware. Somewhere, there used to be a list of compatible hardware.

That was the situation years ago. Both of you are saying that things have got better. Perhaps they have. If I was to buy a computer with an OS preinstalled and tried to install Linux on it I would be more concerned about fast startup and running the Live session in UEFI mode than whether there would drivers for all the hardware. Perhaps I should be more cautious. Sadly, machines with Linux preinstalled are expensive because they are aimed at the Linux programmer. Most ordinary people lack the discernment to appreciate a reasonably priced Linux computer. 

So my conclusion is: Things have got better but some things are still the same and for the same reasons.

P.S. The tread title is slightly inaccurate. No OS comes with WiFi connection, It has to be set up.

Regards

---

### Post by mastablasta on 2021-10-19
> **grahammechanical said:**
> 
So my conclusion is: Things have got better but some things are still the same and for the same reasons.


i bought a new laptop last year for my kid. wi-fi was not working and any additional drivers were not found. however, driver was available, so i patched the kernel with it. instructions were very simple. but such was the price of having new wi.fi chip in laptop.

i believe that driver is now already in kernel. so if i bought it at the end of last year it would likely be working with HWE stack or new OS version.

---

### Post by ardouronerous on 2021-10-26
> **grahammechanical said:**
> I also learnt not to buy the latest hardware (which I could not afford) because it was unlikely that Linux would have drivers for the latest hardware.


I would like to point out that this isn't always the case. My 15 year old laptop, a Dell Inspiron E1505 from 2006, until today, the WIFI drivers aren't in the Linux kernel and so no WIFI out of the box when I do a clean install. I still have to plug in my USB WIFI Adapter in order to install the driver:


```
sudo apt-get install firmware-b43-installer
```

---

### Post by mastablasta on 2021-10-28
> **ardouronerous said:**
> I would like to point out that this isn't always the case. My 15 year old laptop, a Dell Inspiron E1505 from 2006, until today, the WIFI drivers aren't in the Linux kernel and so no WIFI out of the box when I do a clean install. I still have to plug in my USB WIFI Adapter in order to install the driver:


```
sudo apt-get install firmware-b43-installer
```


it was meant that people you use the network cable on install and then add additional drivers during install. 

however, the issue nowadays is, that many modern laptops do not even have a network cable port.

---

