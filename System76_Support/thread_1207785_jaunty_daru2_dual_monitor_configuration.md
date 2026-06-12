---
title: "jaunty daru2 dual monitor configuration?"
date: 2009-07-08
forum: System76 Support
---

### Post by ackey on 2009-07-08
I absolutely love how easy it is to set up an external monitor in jaunty to be an extended desktop.  The resolution for my external monitor is fine, but the resolution options on the daru2 are either 4:3 or really small.  Is there a way to utilize the entire daru2 screen and have the dual monitors?  

I tried looking in xorg.conf and using dpkg-reconfigure xserver-xorg, but apparently resolutions aren't configured there anymore.  Is there a way to enable more resolution options in the "display" preferences window, or am I stuck with this if I want dual monitors?

---

### Post by thomasaaron on 2009-07-08
With an extended desktop, the it creates a virtual resolution that encapsulates both monitors. This is going to throw one of them off. I'm not sure if that can be helped with the current state of development.

---

