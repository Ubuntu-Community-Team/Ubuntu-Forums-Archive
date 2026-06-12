---
title: "Strange Trackpad issue on Acer C7 Chromebook with Ubuntu"
date: 2013-07-12
forum: The Cafe
---

### Post by cpk33 on 2013-07-12
Hey all, 

First post here, so I apologize if this is in the wrong section of the forums. 

There is a strange quirk with Ubuntu (12.04 Unity) on my Chomebook (Crouton chroot) where I must have either my hand/finger physically touching, or the power cord plugged in for the trackpad to work. It seems like a ground issue, but this doesn't happen in ChromeOS. I was previously using the xfce interface and the same problem occurred. It really isn't a huge issue because 95% of the time I have my other hand on the machine or it's plugged in. I was wondering if there is a fix or setting for this anywhere out there. Thanks a bunch for looking. 

-cpk

---

### Post by Xtyn on 2013-07-12
I think Crouton uses the kernel, drivers and configurations from Chrome OS. You could try to install Ubuntu normally (chrubuntu) and see if your touchpad works fine with that. As far as I'm aware, Ubuntu works well on Acer chromebooks.

---

### Post by cpk33 on 2013-07-12
Thanks xtyn. Yea totally. After trying the Samsung, I wanted to get it but didn't want the ARM limitations and glad I made the choice I did. Unity with Compiz is great. 

Is the performance lacking in chrubuntu compared to Crouton? I have a brand new C7 (2833) that was just released w/ 16gb SSD and was told at BB that RAM is soldered in (sounds fishy). If thats true, I want to keep it lightweight as possible.

---

### Post by Xtyn on 2013-07-12
Ubuntu is just as fast as Crouton, or even faster. The RAM may be soldered, but I thought the Acer model had upgradable RAM, you can check. You don't really have anything to lose by trying, Chrome OS is easy to restore, with partitions and everything.

---

### Post by regnumimbriumx on 2013-08-20
great discovery, cpk; i can verify that you need to have a hand touching the chassis on newer Acer C7s, for the trackpad to work properly (mine was purchased August '13; not sure how trackpad behaves on older models). i was wondering why the trackpad seemed so unpredictable.

re: ram, i believe i read that it's easily upgradeable on the 2gb models, so it may be the 4gb models that are soldered.

btw, here's a hardware hack for the trackpad issue. haven't tried it, myself: [http://www.instructables.com/id/Acer-C7-Trackpad-Hardware-FixHack/](http://www.instructables.com/id/Acer-C7-Trackpad-Hardware-FixHack/)

---

### Post by Joshua_Kiepert on 2013-08-31
I recently got the Acer C7 Chromebook (C710-2833) and have since installed the Ubuntu 12.04 chroot environment (using the crouton script). I too ran into this touchpad sensitivity issue and noticed that touching the VGA connector "fixed" the issue. Grounding oneself to the device actually only **increases** touchpad sensitivity. It is just a configuration problem. If you think about it, it cannot be a hardware problem since it works flawlessly within Chrome OS (for me at least). 

I was able to fix the issue completely by using the xorg touchpad configuration files supplied by [Craig Errington]("http://craigerrington.com/blog/fixing-touchpad-issues-on-arm-chromebook-chrubuntu/"): [x_alarm_chrubuntu.zip]("http://http://craigerrington.com/chrome/x_alarm_chrubuntu.zip")

```

#Backup existing xorg files
$ sudo cp -r /usr/share/X11/xorg.conf.d /usr/share/X11/backup.xorg.conf.d

#Remove the old files and put in the new ones
$ cd /usr/share/X11/xorg.conf.d
$ sudo rm *
$ sudo wget http://craigerrington.com/chrome/x_alarm_chrubuntu.zip
$ sudo unzip x_alarm_chrubuntu.zip

#Remove ARM Chromebook specific files and the zip file:
$ sudo rm 10-monitor.conf 10-keyboard.conf x_alarm_chrubuntu.zip

```

Now just restart the chroot environment and enjoy excellent touchpad sensitivity :D 

Note: I still set the touchpad sensitivity and acceleration to their highest values in the system settings too.

FYI: This Acer C7 (the latest one that comes with 16GB SSD and 2GB of RAM) is fully upgradable. I upgraded to 4GB of RAM and a 120GB SSD in mine.

Cheers

---

### Post by jason36 on 2013-09-12
Hi Joshua,

I tried the fix you posted and it seems to have worked! However, now my cursor will periodically disappear whenever I hover over a tab in Chromium, whenever I scroll, and sometimes when I click on certain buttons. Do you have any idea what might be causing this?

Thanks!

---

