---
title: "Total block of computer"
date: 2008-11-24
forum: System76 Support
---

### Post by glacialfury on 2008-11-24
Twice in the last week, SERP4 totally blocked.  Screen was visible and without distortion, mouse cursor disappeared, and keyboard completely unresponsive.

Two blue lights started blinking on the panel in the upper right corner of the case; one looked like a lock with an 'A' on it, and the other looked like a lock with some form of vertical/squiggly line.  They were about a cm apart and flashed repeatedly in sequence until the system was hard-booted by holding down the power button.

Also, occasionally (rarely) while shutting down the system, rather than powering off it goes to a dark-greyish blank screen and just sits there until hard-powered off.

Edit: It just happened again, after the computer had been on for less than 10 minutes.  I should note that both times, Firefox was running, so I'll try Opera and see if it happens with that.

Edit: Occurred again while using Opera.  Booted this time into Gnome Failsafe mode; will leave it running without additional apps and see how long it lasts.

Edit: Occurred in failsafe mode with nothing "extra" running.  Should note that all three incidences described here and above were on battery, not sure if that's relevant - I'll try with adapter soon.

Theories: 
 - something to do with power management while running on battery.  I know suspend/hibernate has caused problems in the past, maybe it's not adapting well to the screen dimming (not turning off!) on battery power.
 - something wrong with the battery itself that causes the computer to block while on battery power.
 - something leaking in the background that I don't know about
 - overheating problems?

---

### Post by compholio on 2008-11-24
> **glacialfury said:**
> ...
Two blue lights started blinking on the panel in the upper right corner of the case; one looked like a lock with an 'A' on it, and the other looked like a lock with some form of vertical/squiggly line.  They were about a cm apart and flashed repeatedly in sequence until the system was hard-booted by holding down the power button.
...

That's a "kernel oops", did you install new drivers recently?  You should post your /var/log/kern.log /var/log/messages files and then we might be able to identify the source of the problem.

---

### Post by glacialfury on 2008-11-24
Files can be found at: [http://www.mediafire.com/?sharekey=48a5e18297048aaeab1eab3e9fa335ca0a45dee5c8b7767b](http://www.mediafire.com/?sharekey=48a5e18297048aaeab1eab3e9fa335ca0a45dee5c8b7767b)

As for drivers, I have not installed or updated any drivers specifically.  I do whatever the "Updates Available" icon in the system tray tells me to do though, so some may well have sneaked in through that.

This error has not occurred while I'm using the AC adapter, however it seems to occur regularly with just the battery.

One of the times it blocked was definitely between 10:00 and 10:10, if that helps you narrow things down.  Thank you for the help.

---

### Post by thomasaaron on 2008-11-24
I'm assuming you are running intrepid... Run this command...

sudo apt-get install linux-backports-modules-intrepid

---

### Post by glacialfury on 2008-11-24
Done, without incident.  While browsing the forums re: Intrepid, I also noticed I don't have the latest System76 driver installed.  Should I update that or leave well enough alone? (my webcam and mic have been working fine all along)

---

### Post by thomasaaron on 2008-11-24
It's always a good idea to run the latest System76 driver.

At a bare minimum, it shouldn't hurt.

---

### Post by compholio on 2008-11-24
> **glacialfury said:**
> ...
This error has not occurred while I'm using the AC adapter, however it seems to occur regularly with just the battery.

One of the times it blocked was definitely between 10:00 and 10:10, if that helps you narrow things down.  Thank you for the help.

Interesting... Well, it looks like it might be a problem with the tickless timer - if it happens again then trying adding clocksource=jiffies to your kernel boot options ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798)).

---

### Post by thomasaaron on 2008-11-24
compholio, good point. I had forgotten about that little beauty.

---

