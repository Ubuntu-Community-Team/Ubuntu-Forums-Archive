---
title: "Root a Sharp (powered by Lenovo) Aquos TV"
date: 2015-08-04
forum: Ubuntu, Linux and OS Chat
---

### Post by nitez on 2015-08-04
Good day! I'm trying my luck on this one as it is more Android related than Ubuntu. Hope someone could help me, at least to know which direction to look first:

This is my situations:
- I am running Ubuntu 12.04 and familiar (not fluent) to command prompt
- I have a Sharp Aquos LCD-60LX750A
- The panel is running on Android (tweaked by Lenovo)
- I have access to only very limited apps (through the Lenovo app store - mostly useless games)
- I used to manage to install apps through the TVs browser but that's now been removed after an automatic upgrade (from what Sharp's service centre tells me, a new regulation prohibits the pre-installation of browsers on TVs
- The only way to install new apps (mostly Plex) onto my flat panel would be to (1) connect an external box (e.g. roku), (2) run software from a u-disk (I have 4 USB ports from which I can run keyboard, etc.) or (3) change firmware or (4) telnet/ssh into the TV (i.e. over IP as I can't find a way to connect my computer to the TV, any way for that?)

So, I'd like to exclude (3) because I cannot risk to brick a 1,000+ USD equivalent TV ... and (1) which I'd like to keep as a last resort.

So, that's leaving me two options unless you see any others 
(2) how to I make the TV boot from a USB drive. What's the trick to do that (have tried combinations of buttons as well as F1, F2, etc. when keyboard is plugged in) no success
(4) how do I telnet/ssh into a TV if I can't change the relevant settings (debug mode, etc. which I've read about for Android phones) - both telnet and ssh to the IP address tell me the ports are closed.

I know this may not be the most adequate forum to start but I have no clue about where to start.

Thanks!

---

### Post by tgalati4 on 2015-08-04
The forum rules generally discourage help on how to hack a device.  It's against the Code of Conduct.  Obviously the reason for changing the app installation policy is to improve security of the TV.  If you were to install an app that gave telnet and root access, then you have all of the linux tools available.

Many consumer products are released with weak security and over time, firmware updates close the holes that allow consumer control over the device.

This thread should be moved to Cafe.

---

### Post by nitez on 2015-08-05
Thanks for the advise tgalati4 but then again (4) wouldn't be hacking, would it? One point I forgot to reference is that I live in China so unfortunately, it goes 'a little' beyond pure security policy of the device (a smart TV without a browser???). Any further help on where to take my question would be helpful. I'm also happy to move the post to a new section, but not sure how to.

---

### Post by tgalati4 on 2015-08-05
That is the pathway into most devices.  You load some software that provides basic services (such as telnet and ssh) then you use another computer to log into the device and make modifications.  You need root access (or some clever exploit) to load that initial software.  On some devices it is built-in.  On other devices you need to replace the firmware with root-friendly firmware.

---

### Post by CharlesA on 2015-08-06
TBH, it would be easier and far safer to just use a Roku or the like to steam to the TV.

Are you sure the TV doesn't have a DLNA player? My Samsung smartTV does, I don't see why a Sharp would not.

---

