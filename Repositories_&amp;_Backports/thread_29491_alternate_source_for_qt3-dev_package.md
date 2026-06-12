---
title: "alternate source for qt3-dev package?"
date: 2005-04-24
forum: Repositories &amp; Backports
---

### Post by superwesman on 2005-04-24
Hi - I have installed ubuntu and configured my wireless pci card according to the instructions posted here ....

[http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo)

... and my connection is working fine, however, I am not currently using any wireless authentication.  I attempted to follow the instructions on the page listed above regarding the installation of RaConfig, but I am unable to download the package "qt3-dev" - after much finagling, I was able to install qt3-dev-tools but that's as far as I got.

I believe that these packages are located in the repository hosted on this very server - here are the 2 relevant lines of my /etc/apt/sources.list (which is pretty as it was when I installed, I just had to uncomment everything)

```
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

```

when I try to 

```
sudo apt-get update
```

these 2 lines throw errors, so I've commented them out - does anyone know where I can get this package? is there a mirror? I've checked the main page of the repository and they claim to be switching to a new server - any advice? thanks
-w

I am running a zonet zew1600 card (with the rt2500 chip dealie) ->
linksys wrt54g -> dsl modem

---

### Post by poofyhairguy on 2005-04-26
Here it is:

[http://packages.ubuntu.com/hoary/libdevel/libqt3-dev](http://packages.ubuntu.com/hoary/libdevel/libqt3-dev)

its under a different name.

---

