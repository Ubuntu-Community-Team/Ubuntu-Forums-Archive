---
title: "Touchpad configuration"
date: 2007-12-11
forum: System76 Support
---

### Post by EmilyRose on 2007-12-11
Hey there, I'm trying to configure the touchpad to be less senstive on my Gazelle (gazp5). I've downloaded Touchpad via Add/Remove and added the line "Option SHMConfig "true" " to /etc/X11/xorg.conf, logged out, reset and am getting:


> GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptic

I've tried removing the "Option SHMConfig "true"" line and re-typing it and resaving... no go... :( The same message comes up when I try to launch it with "gsynaptics" in the CLI

---

### Post by thomasaaron on 2007-12-12
That will not work with the GazV5.  It has an elantech touchpad, for which there is not yet a good driver. The only configuration you can do with it at this point is via System > Preferences > Mouse.

---

### Post by EmilyRose on 2007-12-12
Darn. Is there likely to be new drivers for it anytime soon? Its just a bit on the sensitive side...

---

### Post by thomasaaron on 2007-12-12
There seem to be some elantech drivers in the works. Our R&D guys know about them. I imagine there will be one eventually, but I have no ETA on it.

---

### Post by DBO on 2007-12-14
Are the drivers based on the new 2.6.23 drivers I mentioned earlier?  If so I shold find and direct you to the 2.6.22 patchset also.  I know it is out there, I will find it if I can =)

---

