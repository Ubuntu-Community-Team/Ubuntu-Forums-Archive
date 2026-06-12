---
title: "Sticky / garbled menus in GNOME Shell"
date: 2015-01-25
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-01-25
I actually first noticed this when most of the parts of GNOME 3.14 were in their staging PPA but I just filed a bug report during Alpha 2 testing:

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1413062](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1413062)

I posted a screenshot there also:

[https://launchpadlibrarian.net/195441382/Screenshot%20from%202015-01-20%2020%3A56%3A18.png](https://launchpadlibrarian.net/195441382/Screenshot%20from%202015-01-20%2020%3A56%3A18.png)

It's been suggested that it's hardware related:

> Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

I've since tried the Xorg-edgers PPA and also the 3.19.0-031900rc5-generic mainline kernel to no avail.

Anyone else seen that?

GNOME Shell works OK on this other hardware for me (after I work-around [bug #1412602]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1412602")):

> AMD Sempron Processor LE-1250 @ 2.2 GHz
nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)
nVidia MCP61 High Definition Audio (rev a2)
nVidia MCP61 Ethernet (rev a2)
2GB DDR2 RAM

Any thoughts?

---

### Post by kerry_s on 2015-01-25
yeap, did that to me to.
i got an: 
atom 330 1.6ghz x 4
intel 945g grapics
2gb ram

i went back to debian testing for now. debian has gnome 3.14 & kernel 2.16
no issues running

---

### Post by kansasnoob on 2015-01-25
> **kerry_s said:**
> yeap, did that to me to.
i got an: 
atom 330 1.6ghz x 4
intel 945g grapics
2gb ram

i went back to debian testing for now. debian has gnome 3.14 & kernel 2.16
no issues running

Could I get you to select "This bug affects you" = Yes at [the bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1413062"). That will get the bug bumped from New to Confirmed.

---

### Post by kerry_s on 2015-01-25
okay done

---

### Post by kansasnoob on 2015-01-25
> **kerry_s said:**
> okay done

Thank you :D

---

