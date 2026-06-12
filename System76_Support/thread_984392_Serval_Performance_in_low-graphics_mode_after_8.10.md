---
title: "Serval Performance in low-graphics mode after 8.10 upgrade"
date: 2008-11-16
forum: System76 Support
---

### Post by andrewdied on 2008-11-16
I have a serval performance, serp4 laptop that had been running 8.04 ubuntu.  Yesterday I upgraded to 8.10 through update manager, but now my laptop is stuck in low-graphics mode.  I am running the system76 driver 2.2.7.

The exact error:
The following error was encountered.  You may need to update your configuration to solve this.

(EE) Problem parsing the config file
(EE) Error parsing the config file

Oddly, when I go to system > NVIDIA X Server Settings, it says I'm not using the NVIDIA X driver.  When I booted into 8.10 just now, ubuntu reminded me that I was using closed source X drivers, though.

Should I enable the NVIDIA X Server?  Or do something else?  Thanks for the help.

---

### Post by Alvinius on 2008-11-16
You probably need to install the video driver, check this page 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by andrewdied on 2008-11-16
> **Alvinius said:**
> You probably need to install the video driver, check this page 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

It didn't *quite* have the right info.  "System > Hardware Drivers" said I had the 177 driver installed.  I back rev'd to the 173 driver, and the display worked.  I went immediately back to 177, and it still worked.

I assume that the 8.10 upgrade didn't really reset the proprietary drivers correctly.

Exact driver choices:
NVIDIA accelerated graphics driver (version 173)
NVIDIA accelerated graphics driver (version 173)[Recommended]

Thanks for the tip.

How do I mark these as solved?

---

### Post by Alvinius on 2008-11-16
They are proprietary, that is why they are not in Ubuntu release. BTW I am using 177 on 64 bbbit serp3 so far so good.

---

### Post by thomasaaron on 2008-11-17
Please follow these steps:

#Backup your xorg.conf file
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

#Re-create it. Use ALL defaults
sudo dpkg-reconfigure xserver-xorg

#Enable your nvidia drivers
System > Administration > Hardware Drivers
Check the box by the 177 driver.

#Reboot your computer

---

### Post by andrewdied on 2008-11-17
Thanks.  I fixed it by putting in the older driver, rebooting.  It stayed fixed when I went back to the newer (177) driver and rebooting again.

How do I mark a thread "solved"?

---

