---
title: "Unable to boot -- same problem since 10.10"
date: 2012-02-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Ganeshx on 2012-02-29
Greetings,

I have to run 10.04 LTS due to a problem with anything beyond that (10.10, 11.04, 11.10, and 12.04 up to this point).  My problem is the exact same no matter what.  When I choose to start from the USB, it shows me a screen with a LOUD beep.  The screen gives me the options of running Ubuntu from the USB/CD, installing, and a couple other options.

I always choose run from USB, as I don't want to install before knowing if it will work or not.  At this point, I get to a screen where the wallpaper is, but no other menus or icons.  Just the wallpaper and the mouse (I can move the mouse around).

I figured I would test out 12.04 LTS Daily Build to see if this problem had yet been fixed.  It hadn't.  Same issue.  If there are any workarounds, please post them.  If not, I will file a bug report.

I use a Dell Inspiron M5030 (laptop).

Thanks.

---

### Post by cariboo on 2012-02-29
How are you creating your usb drive and do you have the option of adding kernel parameters from the initial install menu?

---

### Post by Ganeshx on 2012-02-29
I created the USB using the Universal USB Installer (from PendriveLinux) with the 64-bit daily build .iso I downloaded.  I am not sure on changing boot parameters.  Are there any guides on how I can find out?  I've never really tried, as I've never needed to.

---

### Post by Bucky Ball on 2012-02-29
10.04 LTS is the current long term support release and will provide a one click upgrade to 12.04 LTS when it is released. Why is running that a problem? If that works from the USB then I would just install it. Maybe leave space to install a newer release on another partition(s) to work with your bug (at least you would have a stable release to fall back on).

I do, of course, understand why you would like to get to the bottom of why newer releases aren't running, but wonder if there is any particular reason you want/need to run them. Good luck. ;)

---

### Post by Ganeshx on 2012-02-29
There is no reason in particular I want to run them, but I would like to be assured that when 12.04 LTS is released, I will be able to run it.  If I can install it, I probably will in June-ish when I'm out of school and it has had a little bit of time to have all major bugs worked out.

---

### Post by cariboo on 2012-02-29
If you are running Lucid, use the Startup Disk Creator utility to create your usb drive, then boot from it. Once you see the initial boot screen, the one with the little man and the keyboard, press F5 and select nomodeset from the menu, then press esc, and press enter to boot the LiveCD.

---

### Post by Bucky Ball on 2012-02-29
> **Ganeshx said:**
> There is no reason in particular I want to run them, but I would like to be assured that when 12.04 LTS is released, I will be able to run it.

Not sure that installing 12.04 now will give you much indication of that ... try when it's released (or better still, a month or two later, as you suggest). But I digress ... ;)

... and as cariboo907 suggests, try 'nomodset'. Good luck.

---

