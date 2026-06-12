---
title: "Pangolin Screen Issues"
date: 2008-11-15
forum: System76 Support
---

### Post by christophermluna on 2008-11-15
Hey there,

To begin with, I've got a panp4n, running Ubuntu 8.10.  I've been running 8.10 for several weeks now.

I have already read [this]("http://ubuntuforums.org/showthread.php?t=916337") thread, and based on Thomas's request to break these up into different threads if the problem was different, I'm posting a new thread.

When I boot the computer, I see everything normally.  I see the manufacturer's splash, the usplash with the Ubuntu logo and orange loading bar, and the login screen all fine.

When I log in, some times the screen goes extremely dark.  I can't seem to find a correlation between the screen darkening and anything I'm doing to the computer physically (like adjusting the tilt of the monitor) or with the software I'm running.

When it goes dark, I can still barely see what's rendered, but not well enough to read anything or tell where my mouse is.

Sometimes a reboot fixes it, sometimes it takes more than one reboot.

Let me know if there's more information you'd need, and any help with this would be appreciated.

Thanks in advance.

---

### Post by schmindy on 2008-11-15
Try Fn-Right arrow key to increase brightness. Also check the Power Managment tab. Hope I could help.

---

### Post by Derath on 2008-11-16
Just as additional note: when checking the power management stuff, make sure to check both gnome and kde (or whatever DE you use). I found when I made changes in KDE, the changes didn't work until I went into Gnome and made changes there as well.

---

### Post by christophermluna on 2008-11-16
Thanks for the quick reply.  The problem hasn't repeated itself yet, so I haven't been able to try Fn + Right.  But I've only had this boot this morning right now since I posted.

I checked the power management settings, and I confess that I'm not quite sure what I'm looking for.

On AC power, my system is set to put the display to sleep after 35 minutes of inactivity.  On battery power, the same, but after 10 minutes, and I have it set to dim the display when idle.

However, the problem has occured on battery power, and on AC power, and it has never occurred after even 10 minutes of inactivity.

Also, to Derath:

What's the difference between checking power management settings in Gnome, or elsewhere?  I checked power management settings under System > Preferences > Power Management.  How would I access any other power management the computer has?

---

### Post by Derath on 2008-11-16
tbh I'm not sure what the difference is. When I received my pang4n I installed KDE on it, and I wanted to screen to just blank instead of hibernate/sleep when the lid was closed, when I changed it in KDE, it still hibernated. I had to change it in gnome's power management as well as in KDE for it to work correctly. 

I guess if you use Gnome only this would not be an issue.

Just my observations.

---

### Post by thomasaaron on 2008-11-17
The function key combinations for dimming and brightening the screen are:

Fn-F8 #Dimming
Fn-F9 #Brightening

Do these work when your screen comes up dim.

I've not heard of this on the PanPx in Intrepid. So, since you always see the splash screen, I'm guessing it is a glitch from the upgrade.

---

### Post by christophermluna on 2008-11-18
Hey there, Thomas

Sorry for not getting back to you sooner.  I haven't been using the laptop much this week.  My wife is due to give birth any day now, so I might not be able to recreate the problem until after Thanksgiving, but I'll post here if it crops up again.

I can answer your question, though.  I have tried Fn + F8 and Fn + F9.  I figured that those were the combinations to dim or brighten the screen based on the symbols printed on the keyboard, and that did not work.

I also thought it must be a glitch with the upgrade somehow rather than a hardware issue.  If you have anything I can do to test it or find out more if it should happen again, you can post here and I'll do it as soon as I can, barring all the other things going on in my life right now.

---

### Post by thomasaaron on 2008-11-18
Give your wife our best. Good luck with the birth.

I'd try booting from a live CD and seeing if the brightness keys work there.
Also, are you using the standard U.S. keyboard layout? If not, that could be the issue.

---

