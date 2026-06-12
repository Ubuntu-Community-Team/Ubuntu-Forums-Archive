---
title: "Greek alphabet fonts in MS Power Toys"
date: 2010-04-13
forum: Wine
---

### Post by donsy on 2010-04-13
I installed MS Power Toys calculator in Wine and the numerics work fine but any alpha characters I type are in the Greek alphabet. For example A is alpha, B is beta, etc. My version of Wine is 1.1.31, and msttcorefonts are installed.

---

### Post by dino99 on 2010-04-14
install the latest wine 1.1.42  
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

inside ubuntu, do you have others Greek's alphabet errors ?

Maybe remove/purge then reinstall language packages with synaptic to see if its make differences.

Try again with the latest wine after you've performed winecfg (apps->wine->config)

If you still have troubles, view log inside .wine folder and into /var/log, maybe you can learn from errors.

Last tweaks that can be made is to run winetricks script: 
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)
and install everything (dupes excluded) about fonts.

search wine's bugzilla & forum & apps base about your software
[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

An other way is to copy/paste your windows's fonts into wine's fonts folder.

---

