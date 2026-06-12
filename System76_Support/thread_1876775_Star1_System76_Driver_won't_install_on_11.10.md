---
title: "Star1 System76 Driver won't install on 11.10"
date: 2011-11-06
forum: System76 Support
---

### Post by Tart on 2011-11-06
I just installed 11.10 on Starling, and system76 driver gives me following error while installing. 
Wireless doesn't work. I can see networks but starling just won't connect to any one. 

Is there anything I can do?
Thank you for your help

```

Preparing to replace system76-driver 2.7.0 (using system76-driver-2.7.0.deb) ...
Unpacking replacement system76-driver ...
dpkg: dependency problems prevent configuration of system76-driver:
 system76-driver depends on python-gnome2; however:
  Package python-gnome2 is not installed.
 system76-driver depends on python-glade2; however:
  Package python-glade2 is not installed.
dpkg: error processing system76-driver (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 system76-driver

```

---

### Post by Tart on 2011-11-06
After running update, I was able to install driver and run system restore. But unfortunately starling will not connect to wireless network :-(. 

Starling also, will not restart properly. When I select restart, after ubuntu logo screen goes black; power still on, but nothing happens. I have to hold power bottom for 5 secs or so for hard restart. 

It was clean install by the way.

---

### Post by Hatsune Miku on 2011-11-06
> **Tart said:**
> I just installed 11.10 on Starling, and system76 driver gives me following error while installing. 
Wireless doesn't work. I can see networks but starling just won't connect to any one. 

Is there anything I can do?
Thank you for your help

```

Preparing to replace system76-driver 2.7.0 (using system76-driver-2.7.0.deb) ...
Unpacking replacement system76-driver ...
dpkg: dependency problems prevent configuration of system76-driver:
 system76-driver depends on python-gnome2; however:
  Package python-gnome2 is not installed.
 system76-driver depends on python-glade2; however:
  Package python-glade2 is not installed.
dpkg: error processing system76-driver (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 system76-driver

```

It was from a simple dependency problem... I would try to install the driver again and see if you get any luck. Make sure that you have "python-gnome2" & "python-glade2" installed.

---

### Post by Random201801 on 2011-11-18
Weird, my star1's wireless worked out of the box when I installed Ubuntu 11.10. No additional system76 drivers were needed.

---

### Post by Enjabain on 2011-11-26
I seem to have the exact same issues with my star1.
Just did a clean install. cant connect to visible wireless and restart hangs with a black screen at the end.

I had no trouble installing the system 76 driver.

---

### Post by isantop on 2011-11-28
We recently found a bug in the driver in that, while it runs just fine on the Star1, it doesn't end up installing any drivers. We're currently working on a fix and should have it available soon.

EDIT: Nix, that, it's already available. Please connect to Ethernet and update your system with Update Manager. Alternatively, you can download it from [planet76.com](http://planet76.com). Once you have the updated version, be sure to run the restore feature to install all of the drivers and complete the restore. This will install all of the wireless drivers.

---

### Post by Tart on 2011-12-03
Hello,


I just did another fresh install of 11.10 on Star1. Updated system, installed system76 driver, restored the system. I still have same problems. Restart doesn't work properly. Starling sees wireless networks but would not connect to them. It is trying and trying to connect and then gives up. 
Looks like it is back to 10.04 :-(
Thanks,

---

### Post by Enjabain on 2011-12-16
I solved my wireless problem (similar to yours). 

I found out I could connect to public, non passworded wireless.

Then I checked the MAC address for the star1 and apparently the upgrade to 11.10 changed my MAC address by 1 digit... weird

So just had to give my star1's new mac address access in my router.

---

### Post by Lee_Machine on 2011-12-16
Being able to see, but not connect to a wireless network is usually a wpa-supplicant issue. Network Manager should take care of all the backend config.

To make sure this is the issue turn off encryption on your wireless router and see if you can connect.

---

