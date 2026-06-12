---
title: "Simple .conkyrc for a top-left corner monitor?"
date: 2010-08-08
forum: The Cafe
---

### Post by Zorgoth on 2010-08-08
Does anyone use/have a .conkyrc for a little panel-width monitor on the top left that just displays approximately the information that the gnome-panel monitor does (What I'd care about would be CPU usage, RAM (distinguishing cache from real used RAM), and if possible disk/network I/O)?  I just don't get conky myself, but I would like to have a decent clean monitor without gnome-panel...

---

### Post by Frogs Hair on 2010-08-08
Take a look at this [http://www.webupd8.org/2009/05/how-to-install-and-configure-conky.html](http://www.webupd8.org/2009/05/how-to-install-and-configure-conky.html)   You could install Screenlets from the repo , and get Info Panel from gnome look.org

---

### Post by Old_Grey_Wolf on 2010-08-08
I used this thread when I set mine up [http://crunchbanglinux.org/forums/topic/59/my-conky-config/](http://crunchbanglinux.org/forums/topic/59/my-conky-config/). There are a lot of examples to choose from there. These links are also useful for customizing something you like [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html) and [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

Depending on your network connection, e.g., wireless, Ethernet cable, and what the OS decided to label them (eth0, eth1, wlan0, etc.) you will probably have to customize them. 

I have attached my simple one I use on a 14" laptop.

---

### Post by pinguy on 2010-08-08
[http://ubuntuforums.org/showpost.php?p=9501964&postcount=12986](http://ubuntuforums.org/showpost.php?p=9501964&postcount=12986)

---

### Post by Groucho Marxist on 2010-08-09
Here is my conky display. It contains my:

[LIST]
[*]Current CPU speeds
[*]CPU usages
[*]Hard drive temperature
[*]Hard drive free space
[*]Total RAM usage (expressed as a percent)
[*]RAM usage out of total available RAM
[*]Current pollen count
[/LIST]
Would this be of some assistance to you? If so, I shall post my conky file :)

---

