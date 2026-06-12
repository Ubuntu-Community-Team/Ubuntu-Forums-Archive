---
title: "Lemur3 touchpad stops working"
date: 2011-12-13
forum: System76 Support
---

### Post by voicesinthefan on 2011-12-13
I'm loving my new lemur, though I've had one reoccurring problem with the touchpad.  Every now and then it just stops working.  I can't really completely narrow down what exactly is causing the failure, except that it often happens when using chrome, though that might just be because I use that the most.

I installed gpointing-device-settings which shows "disable touchpad" NOT checked when the touchpad stops working, and I can tab down to the checkbox, check it and uncheck it to make it start working again.

I'm still rather new to ubuntu and linux, so I'm not entirely sure how to track down the problem.

---

### Post by isantop on 2011-12-13
Were you experiencing the problem before you installed gpointing-device-settings? You can configure the trackpad through System Settings (if you press the Ubuntu Key, then type "trackpad", it's the first result). It might be a good idea to remove gpointing-device-settings.

---

### Post by voicesinthefan on 2011-12-14
Yes it was occurring before I installed it.  I had actually sent an email to system76 support reporting the problem, and the reply I received suggested installing it.

---

### Post by JohnSmithNot1882 on 2011-12-19
I am having the same problem with my new Gazelle Professional.  It just stopped working until I turned it off and turned it back on.  In the process I installed two new touchpad and pointer, but I doubt this was the fix.  Why did the touch pad just stop working and start working again?  It reminds me of my Dell Latitude D630 which always seemed to have driver issues.  If anyone knows what it is or knows how to fix it, please respond.

Thank you,
John Smith Not 1882:popcorn:

---

### Post by isantop on 2011-12-21
What did you install? Also, how frequently does this happen? Can you replicate it from a Live CD? Have you tried removing the software you installed?

---

### Post by JohnSmithNot1882 on 2011-12-21
> **isantop said:**
> What did you install? Also, how frequently does this happen? Can you replicate it from a Live CD? Have you tried removing the software you installed?

This is kind of embarrassing, but I could not figure out what the Fn+F1 button did and I looked it up on the [www.system76.com](www.system76.com) website.  This was the cause of the touch pad turning off.  Not one of my smarter moments.

Thank you for your help,
John Smith Not 1882:popcorn:

---

### Post by mercgt73 on 2012-01-04
Hello,

I found this thread hoping to solve my touchpad problem.  I am using a Lemu2 with Ubuntu 11.10.  My touch-pad will suddenly stop working, within a few minutes of Power On.  I have tried to enable/disable the touch-pad using Fn+F1.  I have also tried to change touch-pad settings to try and kick start it back on, nothing.  I have a usb wireless mouse that I am using in the mean time.  

Any suggestions or diagnostic procedures?  Thanks,

-Rusty R

---

### Post by isantop on 2012-01-04
The best diagnostic out there for issues like this is running the computer from a LiveCD or LiveUSB with Ubuntu installed on it. This tells us for sure if the issue is due to hardware failure or software corruption, based on whether the issue happens from the LiveCD or not.

---

### Post by mercgt73 on 2012-01-04
> **isantop said:**
> The best diagnostic out there for issues like this is running the computer from a LiveCD or LiveUSB with Ubuntu installed on it. This tells us for sure if the issue is due to hardware failure or software corruption, based on whether the issue happens from the LiveCD or not.

Ok, I will give it a shot this week and report back what I find.  Thanks!

-Rusty

---

### Post by aftermarketgirl on 2012-02-06
I'd be interested in knowing mercgt73's results because I'm having the same issue with my new Gazelle Professional (gazp6). All I've really installed is gnome-shell/gimp/clementine and the finderprint reader, so it's hard to believe it's some added software that's borking it.

At the same time, a reboot fixes it and it's not really failing when it gets jostled or something (which I'd expect if it were loose hardware). It usually happens in the middle of some work. Also, I'm not seeing a lot of recent trackpad issues with Sager stuff on google, so maybe it is somewhere in the software.

I suppose I'll play with a liveCD when I get the chance. But I was just getting set up on this machine, and I don't know when I'll have the time. For now I'm just using a mouse.

---

### Post by birdsarah on 2012-11-03
Hi,

I have been having the same issue on my GazP6 - I found this thread:
[http://ubuntuforums.org/showthread.php?p=12335888#post12335888](http://ubuntuforums.org/showthread.php?p=12335888#post12335888)

```

sudo rmmod psmouse
sudo modprobe psmouse
```

works for me.

---

