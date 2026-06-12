---
title: "cupid-0.0.2 video capture"
date: 2009-02-12
forum: Ubuntu Studio
---

### Post by n.brenner on 2009-02-12
Does anybody know anything about Cupid-0.0.2.    Its a stand alone video capture much like Debut.   I cannot get it to install in Ubuntu and its only available in Mandriva and then only if u upgrade to top tier.   Ive been trying for 3 months with no success...   Checkinstall does the ./configure thing but ends up asking for Gconf, which according to my machine is already there.........any leads.

---

### Post by Stochastic on 2009-02-12
The error I was able to get was ```
checking for gstreamer-0.8 >= 0.8.7.1... checking for gstreamer-interfaces-0.8 >= 0.8.7 gstreamer-gconf-0.8 >= 0.8.7... configure: error: Gstreamer Interfaces or GConf >= 0.8.7 was not found

```
So it looks like it's not looking for plain old gconf, but rather gstreamer-gconf or it will accept gstreamer interfaces.

I hopped on google and found these two components:
[gstreamer-gconf]("http://sourceforge.net/project/showfiles.php?group_id=64773&package_id=160709")
[gstreamer-interfaces]("http://sourceforge.net/project/showfiles.php?group_id=64773&package_id=165756")

Give that a go and see if it fixes the issue.  I bet these are hidden in a gstreamer ubuntu package, but I don't know enough about gstreamer to find it.

---

### Post by n.brenner on 2009-02-13
got GStreamer-0.13----got it installed
got GStreamer-Interfaces-0.04-----got it installed
found GStreamer-GConf_0.8.12-9mdv2007.0.i586.rpm --did the alien thing and installed the .deb     Now it complains about adding the gstreamer-gconf-0.8.pc to the PKG_CONF_PATH

now what???

---

### Post by Stochastic on 2009-02-13
I'm guessing that the gstreamer-gconf you found is a release that went along with gstreamer 0.8.12, as the only gstreamer-gconf version I could find in source is 0.01

Try uninstalling your .deb of gstreamer-gconf, and installing the source for 0.1 that I linked to.

Keep in mind, I'm just guessing and gstreamer plugins are all foreign to me.

---

