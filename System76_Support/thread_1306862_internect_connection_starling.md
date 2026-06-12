---
title: "internect connection starling"
date: 2009-10-30
forum: System76 Support
---

### Post by iamadog on 2009-10-30
on system 76 netbook,

after the latest update, I couldnt connect to the internet, both wifi and wired....what to do now?

---

### Post by HotShotDJ on 2009-10-30
Did you upgrade to Karmic?  If so, see: [http://ubuntuforums.org/showthread.php?t=1303542](http://ubuntuforums.org/showthread.php?t=1303542)

---

### Post by thomasaaron on 2009-10-31
Or...

If you are still on 9.04...

In order to make the wireless card in the Starling work, we had to go directly to Realtek and get the newest driver. The System76 Driver installs Realtek's wirelss driver on your system.

Since the current Realtek driver isn't included yet in Ubuntu, kernel updates from Ubuntu may break the wireless. If this happens, you will need to run the System76 Driver and reboot your computer to restore wireless. To run the System76 Driver, go to System > Administration > System76 Driver and click the Install tab and the Install button. Once the driver is finished, you will need to reboot your computer.

---

