---
title: "removing OSE version for non free?"
date: 2008-05-07
forum: Virtualisation
---

### Post by adza on 2008-05-07
I'm trying to remove the OSE version of virtualbox for the non-free version so that i can enable usb support, i removed the OSE version using apt-get remove virtualbox --purge and then tried to install the .deb of the non-free version. However, i'm now getting a dpkg error (see screenshot) and the deb fails to install. Can i safely remove this file that this error is referring to??

---

### Post by insert_name_here on 2008-05-08
Yes, you can delete it.  But first, to be cleaner, check in Synaptic if you have anything still installed from vbox, like virtualbox-ose-modules-*

---

