---
title: "Problem Connecting External Monitor"
date: 2010-05-16
forum: System76 Support
---

### Post by DomIncollingo on 2010-05-16
I just purchased a new Serval (running Lucid).  The laptop is great, but I'm having trouble connecting an external monitor (an Acer) to the laptop.

After I plug the Acer into the DVI port of the serval, the nVidia X Server Settings dialog does not show the Acer.  If I press the Detect Display button on the nVidia dialog, the Acer appears, but when I try to configure it for Twin View, I get the following error message:

The current settings cannot be completely applied due to one or more of the following reasons.
- The location of an X screen has changed.
- The location type of an X screen has changed.
- The color depth of an X screen has changed.
- An X screen has been added or removed.
- Xinerama is being enabled/disabled.
For all the requested settings to take effect, you must save the configuration to the X config file and restart the X server.

If I try to save the settings to the X config file, an error occurs.

When I run an old Serval (serp3) that uses Karmic, I am able to set up Twin View with the same Acer monitor without any problems.  (And I don't have to save any settings to the X config file.)

Does anyone have any ideas what the problem might be with the new Serval running Lucid?  Thanks very much.

Dom

---

### Post by thomasaaron on 2010-05-17
Hi, Dom.

Good talking to you. For the record...

There is a problem with the Serval connecting the DVI port... through a DVI-to-VGA adapter... to at least some VGA monitors. We're not really sure, which monitors are susceptible to this, and we think the problem is probably a hardware or BIOS level problem.

Your best bet with the Serval is to use either a DVI or a HDMI monitor.

---

### Post by OwenHell on 2010-05-17
how dose one get Linux to work over HDMI i have a HTPC and in HDMI Linux is in over scan the HDTV is a Vizio 42" and dose not have a over scan feature, Ubuntu dose work over VGA just fine  over scan on the HDMI.  how to get high def Linux on my HDTV, Got any tips?  thanks for the help!

---

