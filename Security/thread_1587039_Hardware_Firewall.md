---
title: "Hardware Firewall"
date: 2010-10-02
forum: Security
---

### Post by adamrehard on 2010-10-02
Hi all, I'm looking for a good hardware firewall that will run on an older pc (ie 512 MB RAM and 1GHZ CPU)  FOSS is preferable, but not required.  I've tried Astaro, but it refuses to load after a restart.  I'm hoping for AV as I support Windoze clients, and a VPN.  Past that, I can deal with anything.  

Adam

---

### Post by CharlesA on 2010-10-02
Smoothwall or pfSense should work fine.

---

### Post by wacky_sung on 2010-10-03
Below are a few more on top what CharlesA has mentioned.

[http://www.smoothwall.org/](http://www.smoothwall.org/)
[http://www.smoothwall.net/live/index.php](http://www.smoothwall.net/live/index.php)
[http://m0n0.ch/wall/](http://m0n0.ch/wall/)
[http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)
[http://www.zentyal.org/](http://www.zentyal.org/)
[http://sourceforge.net/apps/trac/ipcop/wiki](http://sourceforge.net/apps/trac/ipcop/wiki)
[http://www.pfsense.org/](http://www.pfsense.org/)

---

### Post by sikander3786 on 2010-10-03
How can you forget Ipcop? It will run pretty well on your hardware.

[http://www.ipcop.org](http://www.ipcop.org)

---

### Post by mr-woof on 2010-10-03
I'm running smoothwall 3 express now on 1ghz p3, 512mb ram and 40gb drive. I liked ipcop but I couldn't get snort and clamav to update to the newest versions, so a lot of things wouldn't work properly.

I originally had the same problem with clamav on smoothwall, but followed this and got it up and running

[http://community.smoothwall.org/forum/viewtopic.php?f=26&t=26702](http://community.smoothwall.org/forum/viewtopic.php?f=26&t=26702)

Smoothwall is now running, squid, url-filter, snort, clamav and pop3 scanning. Seems to run quite well on my old hardware :)

---

