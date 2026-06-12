---
title: "wicd/starling issues with 9.10"
date: 2010-01-12
forum: System76 Support
---

### Post by Random201801 on 2010-01-12
I was curious about the compatibility with wicd on the starling on karmic, I attempted to install and use wicd as my prefered network manager, but the wireless connections did not appear to show on wicd. I switched back to network manager, but I am unable to to run my wireless from my room, I have to move a couple more feet into my hall way to get on.

I have all the system 76 updates and other than this, everything else is okay.

Is there a way to maximize the wireless range on Network Manager (I tried sudo iwconfig wlan0 rate 5.5M), or is there a way that wicd can be compatible with 9.10?

When I was running 9.04 in my room with wicd, I was getting 100% connectivity in my room, now I hit 75% and then get disconnected while running 9.10.

Thanks,
Nick

---

### Post by thomasaaron on 2010-01-12
We don't test with wicd, but that really has nothing to do with your range problem.

1. Run ALL system updates in 9.10.
2. THEN download the 2.4.4 version of the System76 driver from [http://planet76.com/repositories](http://planet76.com/repositories) (it'll be the 2nd link from the bottom).
3. Go to your Downloads folder and double-click the driver package and follow the prompts to install it.
4. Go to Administration > System76 Driver > Restore (tab) > Restore (button) to run the driver.
5. Reboot your machine.

Did that fix your wireless range?

---

