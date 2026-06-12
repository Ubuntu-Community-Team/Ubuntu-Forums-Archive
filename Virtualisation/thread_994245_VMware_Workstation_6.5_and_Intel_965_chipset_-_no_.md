---
title: "VMware Workstation 6.5 and Intel 965 chipset - no 3D graphics"
date: 2008-11-26
forum: Virtualisation
---

### Post by bmwman on 2008-11-26
VMware Workstation 6.5 and Intel 965 chipset = no 3D graphics :confused:

I have Compiz working just fine and everything 3D is working inside the host Ubuntu 8.04.1. When I launch my virtual XP i keep getting this message "This computer does not have a 3D graphics system supported by VMware Player."

Is there any workaround on this?

Also If I'm playing music or something in Ubuntu, i can't get any sound in the virtual XP. It says"Failed to open  sound device /dev/dsp, Device or resource busy"

:confused::confused::confused:

---

### Post by stbear on 2009-01-01
Same issue here.
It seems Intel driver is not supported by current VMware products.

I use Ubuntu 8.10 and VMware Workstation 6.5.1.
3D graphics works fine on both Ubuntu and WinXP (if installed separately)

Tried to search VMware community, but there's no hope as well :(
[http://communities.vmware.com/message/1076465#1076465]("http://communities.vmware.com/message/1076465#1076465")
[http://communities.vmware.com/message/1130206#1130206]("http://communities.vmware.com/message/1130206#1130206")

Also, it appears Ubuntu 8.10 includes older intel driver 2.4.1 (package xserver-xorg-video-intel) but current version is 2.6.0-rc1 ([here]("http://intellinuxgraphics.org/download.html") or [here]("http://xorg.freedesktop.org/releases/individual/driver/")). Does it matter?

---

### Post by stbear on 2010-04-07
Ubuntu Karmic (9.10)
VMware Workstation 7.0.1
xserver-xorg-video-intel 2.9.0
15 months later

nothing changed
Do you guys mean "just throw this 2 years-old laptop away?"

---

