---
title: "Serval Performance: Disable Trackpad Click"
date: 2008-01-31
forum: System76 Support
---

### Post by lightnb on 2008-01-31
So I got my new Serval today. I've been playing with it for about an hour now and so far so good.

One thing that's really annoying though is the track pad "clicking" thing. Not the buttons that are supposed to click, but the finger-tracking part that isn't supposed to click on random whatever-it-feels-like-clicking-on when your trying to move the cursor around. Not sure if that's the best way to describe it, but hopefully someone will know what I'm talking about? :)

So how can it be disabled so that only the left click button performs the left click function?

Found some [Similar Threads]("http://ubuntuforums.org/showthread.php?t=328851"), but it's more about disabling the entire touchpad rather than a single function.

Other than that, it's been great so far, thanks!

oh- and I just found out that I'm entitled to a $25 discount since I'm a member of this forum. How can I redeem my coupon code after the order has been placed? (Since I've been a member for a while now)

Thanks,

Nick

---

### Post by Erik Johnson on 2008-02-01
I'm not sure if this would work cause per crichell's response in the thread you pointed to the touchpad is by Elantech, but here is how I disable "click" tap on my laptops that use Synaptics.

edit - /etc/X11/xorg.conf

look for "InputDevice", below which will be "Driver "synaptics". 

Anywhere before the EndSection line beneath, add the line 
Option "MaxTapTime" "0"

So I'm wondering, is there a similiar section for the Elantech?  I apologize if anyone has already pointed this out, obviously kind of new around here.

Regards,
Erik

---

### Post by thomasaaron on 2008-02-01
The Serval has an Elantech touchpad. The synaptics driver will not work with it.

The only two options I know of are:
1. Adjust the double-click timeout in System > Prefs > Mouse.
2. Disable the touchpad altogether with:
sudo modprobe -r psmouse

---

### Post by lightnb on 2008-02-01
> 
The Serval has an Elantech touchpad. The synaptics driver will not work with it.


Shouldn't the Elantech have a config file somewhere as well?

---

### Post by thomasaaron on 2008-02-01
My understanding is that there is not a configurable driver out there for it yet.
I know some folks were working on one, but I don't think the project came to fruition.

---

