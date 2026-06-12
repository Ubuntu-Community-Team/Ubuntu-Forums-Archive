---
title: "What happened to  /proc/bus/usb?"
date: 2012-10-24
forum: Virtualisation
---

### Post by DavidS on 2012-10-24
I've been trying to get my new Garmin GPSmap 62s communicating with Garmin Basemap in Windows XP running in VirtualBox under Oneiric.

I have the VBox extension so that USB works, but a few extra tweaks are needed, it seems, to get the Garmin communication to work.  Several supposed solutions I have found on the internet mention that, in order to get the Garmin driver to show up in Device Manager in Windows, a line needs to be added to /etc/fstab.

But this line refers to /proc/bus/usb, and there is no such 'file' on Oneiric.

What does Oneiric use instead of /proc/bus/usb?

---

