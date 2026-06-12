---
title: "Pangolin p6 - Latest ubuntu releases"
date: 2012-02-02
forum: System76 Support
---

### Post by ranjan_mg on 2012-02-02
I have pangolin p6 laptop purchased a couple of years ago; I have the following issues with the latest 3.0 kernel onwards; 

1) Laptop does not suspend on lid close (Similiar bugs ->
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/863834](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/863834)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/874749](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/874749))

2) Bluetooth does not work even after typing sudo service bluetooth restart
3) Battery indicator does not trigger when AC power suppy is unplugged

All the above work just fine with kernel 2.6.38
When I upgraded 11.04 to 11.10, I kept the old kernel and I have been using it since. But, having purchased laptop from supported linux vendor, and having these thing broken really bothers me. Is system 76 looking into these issues ?

Thanks

---

### Post by isantop on 2012-02-06
> **ranjan_mg said:**
> 1) Laptop does not suspend on lid close (Similiar bugs ->
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/863834](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/863834)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/874749](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/874749))
Thanks for pointing out those bugs. We'll keep an eye on them and contribute information if we can.
> 2) Bluetooth does not work even after typing sudo service bluetooth restart

What type of bluetooth device are you using, and what action are you trying to perform?
> 3) Battery indicator does not trigger when AC power suppy is unplugged
I've seen this sort of thing on several systems. I'll need to do some more testing, but I'll have a look and see what I find out.

---

### Post by ranjan_mg on 2012-02-07
> **isantop said:**
> Thanks for pointing out those bugs. We'll keep an eye on them and contribute information if we can.

What type of bluetooth device are you using, what action are you trying to perform?

I've seen this sort of thing on several systems. I'll need to do some more testing, but I'll have a look and see what I find out.

I am trying to pair my HP touchpad. Everything works fine with kernel 2.6.38 but broken with kernel 3.0 - Oneiric onwards. Even the latest precise 12.04 seems to have it broken. Bluetooth adapter is not recognized at all. This is after doing fn+f12 and sudo service bluetooth restart. I have the bluetooth device "Bus 007 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)"

As far as suspend goes, this was reported earlier by me and others in this forum. See thread -> [http://ubuntuforums.org/showthread.php?t=1862282](http://ubuntuforums.org/showthread.php?t=1862282)

Frankly, having spent extra dollars on a certified linux laptop,more than $1000  and see all these broken and not fixed (1 - No suspend on lid closure, 2 - No bluetooth 3) Laptop oblivious of AC adapter unplugged and not to mention totally useless WebCam app - cheese - broken for almost 2 years - launchpad bug 610600), I am beginning to question why I or anyone need to spend the extra $$, I might as well buy a DELL or Toshiba or something and if I want linux, try fixing it myself.

---

### Post by isantop on 2012-02-07
I just did some testing with another system with that adapter, and everything works fine here. Make sure you're pairing it by:

[LIST]
[*]Pressing Fn+F12 once on the keyboard
[*]Click on the Bluetooth Icon in the upper panel, then choose "Set up New Device
[*]Follow the onscreen prompts to pair the tablet.
[/LIST]

Also, have you made any changes to the Bluetooth stack? We recommend using all of the stock software that comes with Ubuntu (bluez, gnome-bluetooth), and not using any third-party bluetooth managers, as we don't test with them and can't guarantee their compatibility.

As far as the Suspend and webcam issues, we don't have any control over upstream software like the Kernel and Cheese, and bugs in such packages are at the mercy of their own contributors. 

I am looking into the AC adapter bug, as that doesn't sound like an issue with an upstream package, but rather with the system itself.

---

### Post by ranjan_mg on 2012-02-07
> **isantop said:**
> I just did some testing with another system with that adapter, and everything works fine here. Make sure you're pairing it by:

[LIST]
[*]Pressing Fn+F12 once on the keyboard
[*]Click on the Bluetooth Icon in the upper panel, then choose "Set up New Device
[*]Follow the onscreen prompts to pair the tablet.
[/LIST]Also, have you made any changes to the Bluetooth stack? We recommend using all of the stock software that comes with Ubuntu (bluez, gnome-bluetooth), and not using any third-party bluetooth managers, as we don't test with them and can't guarantee their compatibility.
 
As far as the Suspend and webcam issues, we don't have any control over upstream software like the Kernel and Cheese, and bugs in such packages are at the mercy of their own contributors. 
 
I am looking into the AC adapter bug, as that doesn't sound like an issue with an upstream package, but rather with the system itself.
 
Thanks for the response. I have not made any changes to Bluetooth stack, Everything works fine on Oneric onwards with natty kernel - 2.6.38. The moment I use the default oneiric kernel, all these problems show up. Fn+F12 does not bring up the bluetooth indicator. Did you test all these on Pangalon 6 laptop ? I can send you configuration details if you need. 
 
Thanks for your time,.

---

### Post by isantop on 2012-02-07
> **ranjan_mg said:**
> Thanks for the response. I have not made any changes to Bluetooth stack, Everything works fine on Oneric onwards with natty kernel - 2.6.38. The moment I use the default oneiric kernel, all these problems show up. Fn+F12 does not bring up the bluetooth indicator. Did you test all these on Pangalon 6 laptop ? I can send you configuration details if you need. 
 
Thanks for your time,.

We don't have a PanP6 present anymore, but I did test on both a PanP7 and LemU2, which both use the same bluetooth hardware as the PanP6. 

This sounds like a software issue with your 3.0 kernel. Can you try running the system from a LiveCD or LiveUSB of Ubuntu 11.10, 64-bit? That would include a new copy of the kernel package, which should clear the issue up. If this works, then reinstalling the kernel in the installed system should fix it.

---

### Post by ranjan_mg on 2012-02-08
> **isantop said:**
> We don't have a PanP6 present anymore, but I did test on both a PanP7 and LemU2, which both use the same bluetooth hardware as the PanP6. 

This sounds like a software issue with your 3.0 kernel. Can you try running the system from a LiveCD or LiveUSB of Ubuntu 11.10, 64-bit? That would include a new copy of the kernel package, which should clear the issue up. If this works, then reinstalling the kernel in the installed system should fix it.

No, that did not work. Not sure where to go from here.

---

