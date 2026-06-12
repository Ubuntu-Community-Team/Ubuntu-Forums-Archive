---
title: "trackpad not working, system glitch"
date: 2013-06-27
forum: System76 Support
---

### Post by dimethyl on 2013-06-27
Greetings ubuntu fans.  I have been unable to work on my system 76 gazelle professional laptop (running ubuntu 13.04, about a year and a half old) lately because of a seemingly random glitch that has caused my trackpad to become completely useless and my resolution to shrink.  I have very little knowledge of the ubuntu and system76, in the past I have used apple computers, so I would appreciate any help anyone can give.

Here are the series of events leading up to the glitch: Yesterday I left the computer in sleep mode for an hour or so with midori running a couple of windows (not unusual).  When I woke up the computer from sleep the fans started freaking out - every other second they were running extremely fast then shutting down.  So, I decided to shut the computer off.  About an hour later I started the laptop up and the fans were still freaking out in the same manner.  I decided to let the computer stay shut down until the next day.  The next time i tried to start up the computer the fans seemed normal, but at the login page my mouse was stuck at the center of the screen and the resolution seemed to be at 800x600 instead of the usual 1600x1200.  The keyboard worked fine and I was able to log in and navigate my home folder but I found that there was no sound and the dock would not be displayed by pressing the ubuntu command key as it normally would.  I tried pressing fn+F1 to revive the trackpad, but it remained unusable.  I do not seem to be able to access any programs other than the music and video files I have stored in my home folder.  I am able to shut down with the power key, and I noticed that the window showing the shut down options looks like it is from a previous system update in ubuntu 12 instead of 13.  However, the startup screen says ubunto 13.04.  I am not sure what this means, but I wanted to supply you with all the info I know about the problem.

Any ideas on what I can do to get the system running again?  I do not have a usb mouse currently but I will in a few days.  Perhaps using another mouse will allow me to be able to navigate with the mouse on the screen again.

Thank You!

---

### Post by trevm999 on 2013-06-29
Seems like quite the issue! I'm not too sure what would be going on here, but here is what I would do to troubleshoot.

First, turn off and unplug the laptop, pull the battery out and press the power button for about 5 seconds. Put the battery back in, turn on laptop and see if anything has changed.Trying a usb mouse out is a good idea too.

Boot to a know good OS. This would be a Ubuntu disc or USB drive (hopefully you have a working computer available for you to use to create one) System76 provides instructions for doing this [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System) You want use the 'Try Ubuntu' instead of 'Install Ubuntu' this is to try and isolate the problem. If everything is seems fine, then most likely the problem is with your specific OS and/or your hard drive. If it acts the same, then you have some other hardware problem.

Let me know if you are able to try this. If everything seems normal with a live cd/usb, then the next step will be to test your hard drive.

---

### Post by dimethyl on 2013-06-29
Thanks for your help trev, I really appreciate it!

I first unplugged the laptop, pulled the battery out, pressed the power button for 5 seconds, replaced the battery and turned the laptop back on but this didn't change anything.

I also tried using a couple different usb mice to no avail.

I was able to make a ubuntu disc with another computer but when I inserted the disc and held F7 to use it to startup, it asks me for a password.  After I enter my password a menu flashes for less than a second,  I think it is asking me where to boot from.  But it quickly goes away before I can select the dvd and the system boots into the seemingly inescapable glitched mode with an unusable mouse again.  I've tried holding F10 too, but the cd doesn't boot up this way either.

---

### Post by trevm999 on 2013-07-01
Hmm, I am not familiar with System76's BIOS. In theory you should also be able to go into the BIOS and set the disc drive to be the first thing your computer boots from. However, if a password is coming up before loading Ubuntu, it sounds like a firmware password is set. Typically, you have to reset a firmware password by shorting out contacts on the system board. If you have never set a firmware password, it problem could be that your computer's firmware/BIOS is corrupt and that might be your entire problem. Should probably open a case with System76 and see if they can give you instructions on booting from CD/resetting a firmware password, and possibly reinstalling the firmware.

[https://www.system76.com/login](https://www.system76.com/login)

---

