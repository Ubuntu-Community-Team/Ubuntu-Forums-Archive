---
title: "Sudden laptop shutdown, beeps on reboot"
date: 2011-12-19
forum: System76 Support
---

### Post by Pyro MX on 2011-12-19
Hi,

I have a System76 Pangolin Performance (panp7 if I recall correctly) running Fedora 16 64bit and I have been experiencing a rather inconvenient bug last night.

I was just finished transferring videos from a USB camera and my laptop shut down suddenly. No warning, no error message. Sudden power off. I powered the system back on and while the OS was loading 2 leds (caps lock and num lock I think) started flashing an the PC speaker emitted "beeps" continuously. The OS seemed to be booting normally, but I forced a shutdown just in case.

I removed the battery from the computer, put it again and rebooted. I noticed that the cooling vent on the left side of the computer was pretty hot - maybe it overheated somehow (although it was open for roughly 10 minutes).

I checked the messages log file ad found a lot of of upower warnings that I believe happened just before shutdown:

22:06:10 Miranda dbus-daemon[1100]: ** (upowerd:1411): WARNING **: Property get or set does not have an interface string as first arg

Anyway, I'm not quite sure it's the OS causing the problem or the laptop having a malfunction. It's a bit inconvenient since it's the second time it happened since I own the laptop.

Did anyone experienced such issues on Ubuntu?

Thanks in advance!

---

