---
title: "screen going black"
date: 2021-09-27
forum: Ubuntu/Debian BASED
---

### Post by iconoclastica2 on 2021-09-27
My screen turns black when I don't press a key during 60 seconds.. I have disabled both the screensaver and power management. Where else can I look?

---

### Post by grahammechanical on 2021-09-27
You do not give us any information that would help us to help you.

Hardware specifications? What operating system? If it is Ubuntu what version? Is it a dual boot with another OS? What do you see on the screen before it goes black? What happens when you do press a key before 60 seconds have passed? What should happen after switching on the machine? Do you get a boot menu? What options are on the boot menu? Do you get a login screen? Is it at the login screen that the monitor screen turns black if a key has not been pressed before 60 seconds have passed?

In typing those questions my mind has ranged from problems with the boot loader to the monitor going into power save mode. Some LCD monitors will darken if there is no activity on the screen. Mine does during the loading of Ubuntu.

By the way I have given all the help I want to give.

Regards

---

### Post by iconoclastica2 on 2021-09-27
I thought it would be obvious that when talking about the screen saver I'd be in normal operation mode, after successful boot and login. Apparently not. I am. More precisely: I am reading in the browser of in a pdf, for when writing I tend to press keys all the time.
It might be relevant indeed that this is a tablet computer with detachable keyboard (Jumper EZpad-6). OS is Zorin.
Once I press a key, the screen immediately recovers. Only sometimes it turns black a second time.

---

### Post by Dennis N on 2021-09-27
> **iconoclastica2 said:**
> My screen turns black when I don't press a key during 60 seconds.. I have disabled both the screensaver and power management. Where else can I look?

Ubuntu doesn't come with a screensaver program. Did you install xscreensaver? 

Without any screensaver, the screen will blank if set to do so in **Privacy > Screen Lock**, OR **Power > Power Saving**. There is actually a 1 minute setting to blank the screen under both of these. Check how those are set.

---

### Post by QIII on 2021-09-27
Moved to Ubuntu/Debian BASED.  Zorin is not Ubuntu.  While much may be the same, small differences may count.

---

### Post by iconoclastica2 on 2021-09-28
Did I install xscreensaver? No, I did not do so. But apparently, a (few) screensavers(s) come wit Zorin preinstalled. To detect whether it is the screensaver functionality that causes my issue, I changed the setting from "blank screen" to "pop art squares" while making sure that the 'enabled' switch remained off. From then, I never did see any popart, still black screens, but their activation period had changed to 5 minutes. Which is in fact the activation time set in the screen saver settings dialog. I was never, at least not recently, on 1 minute. Afterwards I changed it to 2 minutes and now my screen blacks out after two minuts. So I think it is save to say that  the issue's cause has been narrowed down to the screen saver's functionality and I can disregard other possible causes for now.

Why does this happen with the screen saver not enbabled? (And why was it 1 minute, even though at that time the setting was 5 minutes?)

======= addition ======
Further experimenting led me to this conclusion:
* the "enable screen saver"-switch does not disable the screensaver, but prohibits selection of another screen saver than the black screen
* the "activate screen saver"-switch works independently from the former and activates any form of screen blanking when enabled.

---

