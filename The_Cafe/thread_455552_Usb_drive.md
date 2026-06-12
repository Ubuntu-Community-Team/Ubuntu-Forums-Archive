---
title: "Usb drive"
date: 2007-05-26
forum: The Cafe
---

### Post by ASPCartman on 2007-05-26
Can i copy my current ubntu to my pendrive (cool, fast, big if what) and use it on another pc?
Or is there some way to have ubuntu in my pendrive? (I need my ubuntu with my stuff and beryl)

---

### Post by init1 on 2007-05-26
Yes, there is indeed a way to do that. You probably can't simply install to your pen drive. I tried that with xubuntu and after two hours, it stopped working. Besides, a conventional install would make it run very slow from your pendrive. The other way is to use syslinux. It would load ubuntu as a live cd. This would mean that it would load the same way every time you booted. The easiest way by far to get linux on a usb drive is slax. It is a distro based on slackware. I allows you to actually boot from you usb drive. It can be very useful. 
If all you are looking for is a way to transfer ubuntu from one pc to another, use Partimage. It makes images of your hard drive and can assemble them on the partition of your target computer

---

### Post by reacocard on 2007-05-26
It's possible, but not easy. It's probably better to just put a distro on there that's designed for being run from a flash drive, like Damn Small Linux or Wolvix.

---

### Post by ASPCartman on 2007-05-27
I used syslinux (probably ;) ) but after reboot all my settings, files e.t.c was deleted and standart live cd has loaded. I want that it was working as i get my hdd and connect it to my friend's PC . (Will it work? :) ) And is damnSmall Linux or like it based on Ubuntu/debian? I don't thing that i can to install this damn crazy fglrx and beryl. 

And why it cannot just be installed to pendrive? (Technically)

---

### Post by reacocard on 2007-05-27
> **ASPCartman said:**
> I used syslinux (probably ;) ) but after reboot all my settings, files e.t.c was deleted and standart live cd has loaded. I want that it was working as i get my hdd and connect it to my friend's PC . (Will it work? :) ) And is damnSmall Linux or like it based on Ubuntu/debian? I don't thing that i can to install this damn crazy fglrx and beryl. 

And why it cannot just be installed to pendrive? (Technically)

It can't just be installed to the drive because the hardware will be different on each computer you run it on. This means that a lot of the LiveCD hardware checks are still necessary. In theory, you could set them up on an Ubuntu install, but idk how hard that actually is.  You could try using the LiveCD's persistent mode to keep your settings, that might be the best option.

And no, you can't put fgrlx/beryl on DSL. With all beryl's driver trouble, I'm not sure having it on a full Ubuntu install on the drive would work either, at least not until we have proprietary drivers automatically enabled on the LiveCD.

---

### Post by ASPCartman on 2007-05-27
But is this possible? To make a script that will start after initializing video hardware? Like 
If " 'driver' 'fglrx' " then " xgl "
where xgl is path to xgl acceleration script. ?

---

