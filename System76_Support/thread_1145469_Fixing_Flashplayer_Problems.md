---
title: "Fixing Flashplayer Problems"
date: 2009-05-01
forum: System76 Support
---

### Post by cmnorton on 2009-05-01
Why does my Gazelle Ultra flashplayer not work correctly? I tried getting the Linux Beta of Flashplayer 10, but there were no installation instructions, and I did not want to delete the links (below). Should those links go, given there's a 64-bit beta?

Here is what my links look like:

lrwxrwxrwx 1 root root 37 2009-02-26 20:07 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root 56 2009-05-01 17:38 npwrapper.libflashplayer.so -> /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
root@hiawatha:/usr/lib/firefox/plugins#

What else should I do?

---

### Post by thomasaaron on 2009-05-01
Try undoing whatever you did to install the beta. Then follow these instructions...

[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

---

### Post by Derath on 2009-05-02
Here's some installation instructions for the FP10 native 64bit

[http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html]("http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html")

---

### Post by cmnorton on 2009-05-02
> **thomasaaron said:**
> Try undoing whatever you did to install the beta. Then follow these instructions...

[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

I used Synaptic to re-install flashplayer. Thanks for the instructions.

---

