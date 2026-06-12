---
title: "tethering Android via USB gives limited network access (dig only)"
date: 2010-03-16
forum: System76 Support
---

### Post by Pitt Stains on 2010-03-16
Hello, I'm running Ubuntu 9.04 (have been putting off the 9.10 upgrade forever — maybe this month!) on my Gazelle Ultra (gazu1).  The other piece of hardware involved is a T-Mobile MyTouch 3G (aka HTC Magic 32B, if memory serves). It's running Cyanogen-Mod-4.2.15.1.

When I connect the phone via USB, Ubuntu recognizes it and starts using the phone's connection -- sort of. ifconfig shows I've got an IP address, and I can use dig to resolve domain names, but I can't ping, ssh, or browse the Internet.

Unfortunately, wireless tethering isn't an option for me, as my wifi card doesn't seem to support ad-hoc mode, so it's wired or nothing for me.

Any insight is much appreciated!
-Pitt

---

### Post by Pitt Stains on 2010-03-23
*bump*

---

### Post by thomasaaron on 2010-03-23
We don't really have a way to test that. But this looks like what you're trying to accomplish...

[http://joshuaredstone.blogspot.com/2009/11/tether-via-usb-from-android-g1-to.html](http://joshuaredstone.blogspot.com/2009/11/tether-via-usb-from-android-g1-to.html)

---

### Post by Pitt Stains on 2010-04-05
Just thought I'd follow up to say that when I upgraded to 9.10, ad-hoc networking was no longer an issue.  Tethering over USB works, too, though Epiphany seems to play nicer with it than Firefox (could be I should have started Firefox *after* switching connections).

---

