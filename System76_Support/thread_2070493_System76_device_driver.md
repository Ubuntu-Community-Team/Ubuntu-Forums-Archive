---
title: "System76 device driver"
date: 2012-10-12
forum: System76 Support
---

### Post by Welly Wu on 2012-10-12
I re-installed Ubuntu 12.04.1 64 bit LTS and I proceeded to upgrade to Ubuntu 12.10 64 bit Beta 2 or Release Candidate earlier this week. I noticed that I have no proprietary drivers installed in the Additional Drivers section in the Ubuntu Software Center settings. I also noticed that my System76 device driver tells me that I am using an unsupported version of Ubuntu and that I should contact System76 for more information.

Am I correct to assume that System76 will push out an update to its System76 device driver on October 18th, 2012 when Ubuntu 12.10 64 bit is officially released? What do I need to do after that date? Just re-install it and restore my system and reboot?

Please advise. Thank you.

---

### Post by Welly Wu on 2012-10-12
I just installed the System76 Device Driver version 3.2.0 on my System76 Lemur Ultra Thin (lemu4) notebook PC. I still don't see any proprietary device drivers installed in the Additional Drivers section in the Ubuntu Software Center settings. I restored my system and I installed the drivers and I rebooted my PC several times.

What's going on here?

---

### Post by Welly Wu on 2012-10-13
sudo apt-get install mesa-utils. Now, Ubuntu says that I have Intel Ivybridge Mobile as my graphics and the standard experience.

I am waiting for System76 to respond to my original support ticket on their website.

---

### Post by isantop on 2012-10-15
Hi Welly.

That's normal. There shouldn't be any proprietary drivers on our current laptops. The 3.0.0 version of the driver didn't have support built in for 12.10. 3.2 added this support.

---

