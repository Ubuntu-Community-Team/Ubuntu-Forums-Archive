---
title: "Desktop Effects Meerkat Nettop"
date: 2009-07-19
forum: System76 Support
---

### Post by pnjabi on 2009-07-19
Hi - I got the Meerkat Nettop last week and I am running into some issues with Visual Effects. Currently the Visual Effects are set to "None" and  when I try to enable "Normal" Visual Effects, I get the message the "desktop effects could not be enabled". Any suggestions? Thanks.

pnjabi

Meerkat Nettop
Ubuntu 9.04
2 GB RAM

---

### Post by thomasaaron on 2009-07-20
Yes.

Sounds like you may have re-installed?

This will get it going. Let me know if you need assistance with it.
[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

---

### Post by pnjabi on 2009-07-24
So, this is what I did. According to the link provided, I tried to look for the file in ~/.config/compiz/compiz-manager, but the only file I can find on my system is ~/.config/compiz/compizconfig/config. I was not sure whether I need to modify the config file, so I entered the following command on the command line: 
SKIP_CHECKS=yes compiz-manager.

This made my screen completely blank and I was unable to use GUI functionality.
So, I restarted and was able to enable the desktop effects.

Am I suppose to do anything else? Thanks.

---

### Post by thomasaaron on 2009-07-24
If it keeps working, I guess you're good. If it stops, try creating the compiz-manager file...

touch .config/compiz/compiz-manager

Then add SKIP_CHECKS=yes to it, save and reboot.

---

