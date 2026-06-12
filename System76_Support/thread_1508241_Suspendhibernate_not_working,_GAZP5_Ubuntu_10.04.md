---
title: "Suspend/hibernate not working, GAZP5 Ubuntu 10.04"
date: 2010-06-12
forum: System76 Support
---

### Post by bkauger on 2010-06-12
Hello -- I have a Gazelle and did a clean install of Ubuntu 10.04, 32 bit and nVidia graphics.  Neither suspend nor hibernate work -- they did on this machine with earlier versions of Ubuntu (both 32 and 64 bit).

I have searched around and cannot find a fix here or anywhere else.  Am I the only person with this problem?

I would very much appreciate any ideas or help anyone might have or offer.

---

### Post by cj.surrusco on 2010-06-12
It might have something to do with a usb device. I am unable to suspend/hibernate when my wireless adapter is plugged in.

Also, check that you have swap mounted, as you need that for hibernation.

---

### Post by bkauger on 2010-06-12
Thanks for the tips.  I remembered seeing about USB devices sometimes causing problems with suspend.  I have tried suspending/hibernating after unmounting them but this hasn't made a difference.

Using Disk Utility, it looks like there is a 3.3Gb swap space (/dev/sda5).  Does this mean it's mounted?

Thanks so much!

---

### Post by cj.surrusco on 2010-06-13
Just because it shows up in disk utility doesn't necessarily mean that it is mounted. An easy way to check if it is mounted is to open system monitor.

(Alt+F2, then type "gnome-system-monitor")

Then move over to the resources tab, and check what it says under swap. If it says "O bytes out of 0", then it is not mounted.

---

### Post by bkauger on 2010-06-13
Thanks -- it is mounted.  Should it be of a certain size, and bigger than what is reported?  It's 3.1 GB.

Thanks again.

---

### Post by cj.surrusco on 2010-06-13
Your swap should be about equal in size to your RAM. Yours should be plenty big. 

What exactly happens when you try to hibernate/suspend?

---

### Post by bkauger on 2010-06-13
Thanks.  That's what I thought (I have 2 GB RAM).

When I try to suspend or hibernate, the screen goes dark, there is a great deal of writing-to-disk, then I am back at the log-in screen.  Entering my password brings me back exactly where I was...if music was playing, it starts back up, if I was replying to a thread (like I am now), I am back exactly where I left off.  Altogether it takes about 12 seconds.

I appreciate your helping me with this.

---

### Post by cj.surrusco on 2010-06-13
I would say that it is hardware that it is preventing it from not being able to fully hibernate, but since you said that it used to work with previous versions of Ubuntu, I think that isn't the case.

I wish I could help you further, but I have done some research and haven't come up with anything.

Good luck with this problem.

---

### Post by isantop on 2010-06-15
Try installing 64-bit. It could be something simple like that.

On the other hand, it may have been a problem with the install disk that wasn't caught by something larger.

If you have the disk you used to install, you can pop it in and boot from it. Before it starts up, you should see a purple screen with a white keyboard and accessability logo at the bottom. Press a key here, select a language, then arrow down to "Check disk for Defects" and press select.

Alternatively, you can try a fresh install with a new disk. That could fix the problem.

---

