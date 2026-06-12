---
title: "Wireless Troubles"
date: 2010-10-26
forum: Ubuntu Studio
---

### Post by JaymoS on 2010-10-26
[B]Short Story
    [/B]i installed ubuntu studio 10.04 followed some steps i found online to set up network manager and the wireless worked just fine, ran into some problems with firefox plugins i couldn't figure out so decided i would just reinstall studio, so i reinstalled it and now the wireless does not work but i did exactly the same thing as the first install i have network manager and network manager gnome install and have an up to date system even with manually configured settings in network connections and wifi radar still wont let me connect

[http://help.ubuntu.com/community/UbuntuStudioNetworkSetup](http://help.ubuntu.com/community/UbuntuStudioNetworkSetup)
this was all i had to do for it to work the first time

**Long Story**
 So I recently installed Ubuntu Studio 10.04 followed some steps that i got online to get network manager and network manager gnome .deb packages installed from the iso cd, had to use a wired connection at first but after activating the B43 wireless driver, the  STA(? i think it was STA) wireless driver, and a ATI/something graphics driver; the wireless just kind of started working it automatically detected networks and i could easily connect to them with just the network password, life was good. i ran into a problems with youtube videos because i installed the wrong plugin when asked to update plugins and every youtube video said "Error, please try again later" so after a few hours of searching for solutions blah blah blah, nothing worked so i just reinstalled Ubuntu Studio cause it seemed easier, i did the exact same things on the second install with getting network manager, network manager gnome, used a wired connection activated the same drivers and updated the system (basically the same things i did for the first install) and now it wont detect wireless networks so with out the wired eth0 i don't have internet access tried a lot of things i read but nothing helps tried manually putting in the SSID, MAC address, network address, security key all the information i could in network connections and wifi radar but it still wont let me access my network it wont even detect networks

PLEASE HELP! and thank you

---

### Post by JaymoS on 2010-10-26
well this is embarrassing, but apparently ubuntu was just kidding when it said it activated the Broadcom STA wireless driver, I just ran hardware drivers and it came up as inactive so i activated it and now the wireless works fine! probably should have checked that sooner

---

