---
title: "panp4n - Configuring the touchpad to work with two finger"
date: 2009-04-05
forum: System76 Support
---

### Post by mperrydotnet on 2009-04-05
Hi there, 
I'd like to get my touchpad working with multitouch. I have tried to follow a few directions, specifically here:

[http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html](http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html)

Using those directions, I tried to configure it via hal. I also tried to configure directly in Xorg.conf, but unfortunately that seemed to also have no effect.

When that didn't work I tried to view the debug output as described using synclient -m 100. That complained about not having access to shared memory, so I followed the instructions on the Ubuntu Community Documentation to turn on the shared memory option via HAL. Once this was done, I was able to use synclient -m 100, however the 'f' column, always either displays 0 or 1. 

I'm not sure if HAL is the "preferred", but it seemed pretty straight forward. My xorg.conf is very minimalist, and that fact leads me to believe that HAL is taking over what used to be function of the X11 conf. 

Anyway, I am not sure how to proceed. Is multitouch even possible on panp4n? If so, how can I set it up?

---

### Post by Lee_Machine on 2009-04-06
I looked into this also when I first got my Pangoline and multi-touch is not just a software thing but a hardware also.

Most instructions I found were how to get mulit-touch back when you have Linux on a Macbook...why you would do that I dont know (put Linux on a Mac):lolflag:


Edit: I read the link you had and it goes against what I found earlier, hmmm....

---

### Post by drewbenn on 2009-04-06
Those instructions look like they are for a synaptics touchpad: are you sure the panp4n has a synaptics touchpad?  I ask because I know that many System76 laptops (including my panv3) have elantech touchpads.

Are you using 8.10 or 9.04, or a different version of Ubuntu?  I think that 9.04 has some new/different touchpad settings (for example you can turn off tap-to-click, which I know some people really didn't like).

What are you trying to accomplish with multitouch?  The article you linked didn't really say what the user benefits of multitouch are.

---

### Post by mperrydotnet on 2009-04-06
[INDENT]are you sure the panp4n has a synaptics touchpad?[/INDENT]
I ran ```
xinput list
``` as described on one of the pages, and it did specifically say synaptics touchpad. I'm not sure if that method is accurate or not, but for what it is worth it said what I expected.

[INDENT]Are you using 8.10 or 9.04[/INDENT]
8.10

[INDENT]What are you trying to accomplish with multitouch?[/INDENT]
Specifically, two finger scrolling and right clicking w/ two fingers.

---

### Post by thomasaaron on 2009-04-06
I think this is a bug in xserver-xorg-input-synaptic. See...

[https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-input-synaptics/+bug/270002](https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-input-synaptics/+bug/270002)

It looks like a fix has been released, and the bug report offers a work-around.

We're smack in the middle of Jaunty testing. I'll report back whether or not it is fixed in Jaunty.

---

### Post by mperrydotnet on 2009-04-06
Thanks for the information. I'll dig into this bug report tonight when I have a moment.

---

### Post by mperrydotnet on 2009-04-06
I'm sorry, I spent some time reviewing that bug on launchpad and I was unable to make heads or tails of it. I'm really not familiar with HAL nor am I familiar with using the xinput command.

When you said that there were some workarounds found in this bug did you mean the PPA packages? If those work, which I cannot confirm they do, I have no idea how to install them. 

I could still use some direction.

---

### Post by thomasaaron on 2009-04-07
Well, the post suggested adding...

> Option "MaxTapMove" "0"

...into the xorg.conf file. However, the problem with this is that, in Intrepid, the touchpad is no longer supposed to be controlled by the xorg.conf file. It is controlled by HAL (Hardware Abstraction Layer). 

So, as someone in the bug report mentions, tweaking it can cause other things to break.

There are also a bunch of diff files in there for anyone interested in compiling stuff from source code.

There is also a link to a .deb file that should fix the problem. However, the link is dead.

None of that is great news.

However, it says the fix has been released, although it doesn't appear it made it into Intrepid. We will be testing the Pangolin on Jaunty in the next few days. I'll let you know if it works there. Bump this around Friday if I've not responded.

---

### Post by mperrydotnet on 2009-04-11
> **thomasaaron said:**
> Well, the post suggested adding...



...into the xorg.conf file. However, the problem with this is that, in Intrepid, the touchpad is no longer supposed to be controlled by the xorg.conf file. It is controlled by HAL (Hardware Abstraction Layer). 

So, as someone in the bug report mentions, tweaking it can cause other things to break.

There are also a bunch of diff files in there for anyone interested in compiling stuff from source code.

There is also a link to a .deb file that should fix the problem. However, the link is dead.

None of that is great news.

However, it says the fix has been released, although it doesn't appear it made it into Intrepid. We will be testing the Pangolin on Jaunty in the next few days. I'll let you know if it works there. Bump this around Friday if I've not responded.


How goes the testing?

---

### Post by thomasaaron on 2009-04-11
Still in progress. We've been building Jaunty images, so we didn't quite get to the Pangolin last week.

---

### Post by whitethunder922 on 2009-04-17
This would be an awesome feature to have in Jaunty. Thanks!!

---

### Post by mperrydotnet on 2009-04-21
Hi there,
I saw an update to the drivers package so I figured I'd update it, and then update to Jaunty to help test. After performing the update multitouch still does not work. Running "synclient -m 100" still only shows either a zero or a one on the 'z' axis, which should depict the number of fingers.

---

### Post by mperrydotnet on 2009-05-04
Hi there. I'm still looking for some assistance with this issue. Thanks.

---

### Post by thomasaaron on 2009-05-04
It's still not working on our shop computer. This is an xserver bug, and there is a report filed on it...

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/320585](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/320585)

The fix will have to come from upstream on this one. I imagine it won't take very long,though.

---

### Post by mperrydotnet on 2009-05-04
> **thomasaaron said:**
> It's still not working on our shop computer. This is an xserver bug, and there is a report filed on it...

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/320585](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/320585)

The fix will have to come from upstream on this one. I imagine it won't take very long,though.

I read through this report, and the problem seems a bit different. My problem is that two fingers are not registering at all. I can tell this by running synclient -m and observing the output.

---

### Post by thomasaaron on 2009-05-05
I'm pretty sure it is the same bug. It references a loss of multi-finger tapping ability. It also references another bug report, in which a fix has been committed. 

So, the fix should come down the pike soon.

---

### Post by fj401971 on 2009-07-20
Ubuntu 9.04
2.6.28-13-generic
X.Org X Server 1.6.0
Pangolin Performance panp4n

From what I understand, the 'SynPS/2 Synaptics TouchPad'is being used whereas the actual touchpad is an Elantech or something...  

If you enable SHMconfig and then use synclient to watch what is actually inputted to the computer during tapping of the touchpad, only one finger is ever recognized despite if you use 1, 3 or 10.

There is an option to emulate two finger sensing by the touchpad sensing the amount of pressure applied, which is the "z" variable on synclient output.  The default setting for this on my system is 280, which leads me to believe that they don't want this working at all because the maximum I can get the pressure variable up to is about 87.

I plan on modifying this value to around 84 or 83 to see how this works.  This is the "EmulateTwoFingerMinZ" variable.  

What would work even better is if there was a "EmulateTwoFingerMinW" variable, because the touchpad can measure the width of the finger.  Under normal one finger taps for me, the "W" value only gets up to about 5 whereas with two fingers, it is above 10 and the value maxes out at 15 I believe.  I don't have any idea how to do this, and would venture to guess that the driver would have to be modified in order to do this.  This would seem like a good fix to have in the "System76 Driver"


Resources Consulted:
[https://wiki.ubuntu.com/X/Config/Input]("https://wiki.ubuntu.com/X/Config/Input")
[https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad")

---

### Post by thomasaaron on 2009-07-20
The PanP4*/PanP5 have Synaptics touchpads. The older Pangolins had Elantech pads.

---

### Post by laos.lindberg on 2009-08-12
hey all,

any news on the multi touch front

thanks
manning

---

### Post by thomasaaron on 2009-08-13
We haven't done any more testing lately with it under Jaunty. But we're starting to ramp up for Karmic and will be testing it there in about a month.

---

### Post by laos.lindberg on 2009-08-13
Cool!
My old toshiba was running 8.10, and when i upgraded to 9.04 i could scroll with two fingers, i had no idea why it happened but i loved it.
i can totally wait till october for the karmic upgrades!
it's not an essential feature, just one i came quickly to enjoy
thanks

---

### Post by mperrydotnet on 2009-08-13
How did you get it to work? I am still unable to multi touch on my pan4p w/ Ubuntu 9.04 installed.

---

### Post by revlimiter on 2010-01-23
I thought I'd bump this. 

Has there been any progress in the multitouch department? I've tried to get it running on my panp6 but have had no luck. Side scrolling works great though...

---

### Post by thomasaaron on 2010-01-25
Haven't really tested for it yet in Karmic. Once I dig out from the weekend email/forum pile-up, we're run some tests.

---

### Post by revlimiter on 2010-01-27
midweek bump!

---

### Post by laos.lindberg on 2010-08-16
Hey Hey
Bump Bump

Any news on two finger scroll?

I know it's not an essential feature, but i know it is something that works well in ubuntu.  and i personally like it :)

Thanks!

---

### Post by isantop on 2010-08-18
The multitouch scrolling in Lucid on the pangolin line is not supported. We're working on getting it available. It may be easier in 11.04 when Canonical puts out their new UTouch interface.

---

### Post by laos.lindberg on 2010-08-20
Thanks!  I know it's not an essential function, just one that I have enjoyed.  I can certainly wait for natty!

---

