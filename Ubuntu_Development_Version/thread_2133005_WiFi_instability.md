---
title: "WiFi instability"
date: 2013-04-06
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2013-04-06
I've noticed in the past few hours that I'm loosing connectivity with my WiFi router. This has not been the case prior to today's update upgrade dist-upgrade.

Any one else noticing this behavior?

---

### Post by ronacc on 2013-04-06
I'm not seeing that here . the specs you listed for your machines leave out the most critical part , what wifi chip are they .Also is this happening on both . my wifi is realtek 8185 .

---

### Post by pfeiffep on 2013-04-06
I'm not using WiFi on my tower, I booted into 12.10 for a test on laptop. Will post back with updates.

How do I determine the WiFi chip?

I love your _*If it ani't broke .....*_  I live by that motto when experimenting - I learn more by breaking it then fixing it!

---

### Post by pfeiffep on 2013-04-06
Found at least 1 way to identify all hardware  -  sudo lshw

```
network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:03:03.0
                logical name: eth1
                version: 05
                serial: 00:13:ce:20:db:34
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.5 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:dfdfd000-dfdfdfff
```

---

### Post by ronacc on 2013-04-06
I know nothing about that wireless chip . Here is a thread in the networking and wireless  section that may help [  http://ubuntuforums.org/showthread.php?t=2133005  ](  http://ubuntuforums.org/showthread.php?t=2133005  )    . There are other threads in that forum that also deal with that chip . seems like many people have problems with it and not just in 13.04 .

---

### Post by pfeiffep on 2013-04-06
> [COLOR=#000000]that may help [/COLOR][http://ubuntuforums.org/showthread.php?t=2133005](http://ubuntuforums.org/showthread.php?t=2133005)  ROTFLOL  That link is to this thread!:mrgreen:

I've been running now since this post on 12.10 (2 hrs) in the exact same position in my home - put the pc to sleep a couple of times and it woke up just fine fully connected. I only have experiential data - but i believe that there some instability in 13.04 regarding wireless and power management! 

I have all the logs available from the disconnect experiences, however I'm pretty much of a novice with Linux logs and what I should be searching for! Perhaps some learned sage could give me some tips:)

---

### Post by ronacc on 2013-04-06
oops my bad I copied the wrong tab in my browser . Go  to the top of the page and select advanced search  , search in the networking and wireless  forum   keyword  2200bg and you will see many threads about it with possible cures keep trying different things until something fixes it .

---

### Post by pfeiffep on 2013-04-06
Thanks for the info ... I'll look into updating the driver based on those posts. Maybe the newest raring has updated me to instability. I did a hardware refresh - bios and from dell appropriate drivers in Feb before I embarked on the Ubuntu journey.

---

### Post by Rukiri on 2013-04-06
I've only noticed that my wifi has gotten better each kernel release so maybe upgrade your kernel? It might be better if you hand install the kernel, it may be scary but at least you know what is In your kernel instead of EVERYTHING enabled.  
I do have to manually install a driver for my ae3000 usb adapter but my ae1000 works out of the box and is pretty quick.

Wifi/Ethernet should be as good as windows and if your using openbox or a light de you may notice faster connections due to less overhead.

---

### Post by pfeiffep on 2013-04-07
@Rukiri Thanks for your reply. Gave up running Win XP on the ancient beast ... running gnome session fallback and the response is just fine. I noticed a much quicker response with 13.04 vs 12.10 interesting because 12.10 is on the internal HD and 13.04 is running on an external usb HD

---

