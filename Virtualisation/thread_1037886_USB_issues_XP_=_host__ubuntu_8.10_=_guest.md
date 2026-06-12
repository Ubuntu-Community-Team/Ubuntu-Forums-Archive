---
title: "USB issues XP = host / ubuntu 8.10 = guest"
date: 2009-01-12
forum: Virtualisation
---

### Post by attrezzo on 2009-01-12
I've never experienced USB problems before, but for some reason I just hit the wall this time. I've got a fully updated ubuntu VM that's not pulling USB from it's host.

Of course I've added a usb hub under hardware. I've also installed vmware-tools and patched the install so vsock would compile. Still not working. I have vmware-toolbox set to run at login but all I ever get out of the "devices" tab is: "No removable devices are available. Either this..." You get the idea.

When I look at the VMware menu host-side it shows the usb devices connected to the system (some usb hard drives and a serial port/arduino) but the options to connect and so on are greyed out. 

I've also added:

 usbfs     /proc/bus/usb     usbfs     auto    0  0

To my /etc/fstab

I also tried

usbfs     /proc/bus/usb     usbfs      auto,devmode=0666     0 0

I looked in /etc/init.d/mountdevusbfs.sh but there is no magic mode anymore. Though this shouldn't apply the /etc/fstab stuff should have worked from what I know.

Finally, I look in /proc/bus/usb and the hubs are there but there's nothing else. What gives? Anyone else having these issues?

---

