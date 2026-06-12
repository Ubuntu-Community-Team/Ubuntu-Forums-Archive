---
title: "Macbook 4.1 with Ubuntu &amp; virtualbox, Compiz fusion wont work."
date: 2009-11-07
forum: Virtualisation
---

### Post by adkafka on 2009-11-07
Hello. I have a 4.1 macbook wth an intel GMA X3100 and VirtualBox 3.0.10 running Ubuntu 9.10. I have installed the guest additions and now everything works fine but Compiz. I have tried everything but it won't ativate. When I try to activate it through system<appearance<visual effects, I get "Desktop effects could not be enabled." Please, any help would be great.

Here is my output of compiz:
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
aborting and using fallback: /usr/bin/metacity 

and my xorg.conf:
# Default xorg.conf for Xorg 1.5+ without PCI_TXT_IDS_PATH enabled.
#
# This file was created by VirtualBox Additions installer as it
# was unable to find any existing configuration file for X.

Section "Device"
        Identifier      "VirtualBox Video Card"
        Driver          "vboxvideo"
EndSection

Thanks ahead of time

---

### Post by fjgaude on 2009-11-07
From what I know you can't run compiz in a virutal machine, because the video adapter is software, not the accelerated hardware which compiz needs for the desktop magic.

---

