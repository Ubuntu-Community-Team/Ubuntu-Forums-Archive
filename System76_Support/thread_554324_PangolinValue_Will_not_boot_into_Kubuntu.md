---
title: "PangolinValue Will not boot into Kubuntu"
date: 2007-09-18
forum: System76 Support
---

### Post by newsun on 2007-09-18
Hi I have just received my pangolin value today and I installed kubuntu on it. Everything was working fine, then I adjusted the screen resolution via the system settings and it was set and 640x520 or something so I change to the only other setting which was 800x600 then restarted X and then the resolution was much less than previous. I then rtied the system76 driver thing on the menu and ever since I restarted after that it loads up Kubuntu and hangs in mid boot.

I have a Kubuntu disc of 7.04(not the ubuntu SR disc you guys offer) and I tried booting with that one and it hangs saying something about ttl not being enabled.

Please help I just want to use my laptop.



EDIT -- OKAY so I uninstalled then reinstalled xserver-xorg-video-intel and now I can get back in, but my resolution is still off, how do I increase it to proper 1240x800?
EDIT -- I ended up reinstalling the system76 drivers and everything seems peachy now. I don't know how it got so messed up in the first place.

---

### Post by imhavoc on 2007-09-19
the best way to install Kubuntu on an existing Ubuntu machine is to simply 'sudo apt-get install kubuntu-desktop' (or install it though Synaptic or whatever).

That way you get the comfort of the KDE/Kubuntu you love, and not the pain of having to re-stabilize a system that System76 went to a great deal of trouble to make run well.

---

### Post by newsun on 2007-09-19
yup that is how I installed kubuntu, though honestly I would much rather not have to clean up all the menus with the extra gnome items and just install kubuntu fresh with system76 drivers...what happend to me was that I changed the resolution, then could not put it back and so I ended up in a situation where I deleted the video driver and reinstalled it with the system76 driver repo and all was well

If there is a Kubuntu install or another KDE install with the santa rosa drivers included I would do that and just run the system76 driver update after install if I could

---

### Post by imhavoc on 2007-09-19
On my Darter Ultra (2), I've just decided that it's better to not mess with screen settings since all of that stuff is set up in the xorg.conf by the good folks at S76. when i realized that the resolutions displayed in the control window didn't match up to the reality, I just canceled and backed away.

I'm looking forward to Santa Rosa support in KDE, too.

---

### Post by newsun on 2007-09-20
This was what brought me to trouble was the mismatch of resolutions on the inital install, but after I got things back to peachy and ran the system76 driver update, I can now change the setting in the display control panel in kde just fine...or at least i could till I decided I wanted to work with dual boot and had to format my system to remove the LVM

---

