---
title: "Wifi drivers for a Dell Mini 9?"
date: 2009-09-30
forum: Ubuntu Moblin Remix
---

### Post by spotdog14 on 2009-09-30
Would someone kindly point me to a how to or something similar as to how to get the wifi working on my Dell Mini 9 with the most recent Moblin 2.1? 

Thanks!

BTW Its a Broadcom card.

---

### Post by NormanFLinux on 2009-09-30
Connect your Dell Mini 9 via Ethernet and reload your repositories. Hardware Drivers should then offer the Broadcom STA driver. Click to download and install it. That should get the Broadcom card enabled and then you should see your wireless networks to connect to.

---

### Post by bfiller on 2009-09-30
If you download the Dell/Moblin image from here it already has the broadcomm drivers installed.
[http://linux.dell.com/files/ubuntu/moblin-remix/dev-edition-2.0/moblin-jaunty-usb-hdd-20090914-4.img](http://linux.dell.com/files/ubuntu/moblin-remix/dev-edition-2.0/moblin-jaunty-usb-hdd-20090914-4.img)

Otherwise run jockey-gtk and activate the Broadcomm STA driver.

---

