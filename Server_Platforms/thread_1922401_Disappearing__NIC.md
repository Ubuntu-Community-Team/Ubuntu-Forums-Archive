---
title: "Disappearing  NIC"
date: 2012-02-08
forum: Server Platforms
---

### Post by btxshark on 2012-02-08
I have been running an Ubuntu server on an old HP work station I had lying around for several years now. Recently it restarted due to power loss (soft shutdown triggered by UPS) and when I logged in the next day it was hung on boot with a message at the top of the screen saying that it was unable to connect to system bus. Using the recovery option in GRUB I got it to boot normally and start all the services but the message is still there and it won't connect to the network. Running ifconfig shows only the loopback interface. The interface eth0 is still set at static in the interfaces file and the device shows up when I run lspci No recent software or hardware changes have been made to the machine. I would prefer not to completely reinstall because all of the configs are how I want them but if that is the only fix, is there a way to transfer all of my settings to a new install? Thanks you any help you can give a hopeful linux noob.

---

