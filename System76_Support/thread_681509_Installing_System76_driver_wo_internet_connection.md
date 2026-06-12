---
title: "Installing System76 driver w/o internet connection"
date: 2008-01-29
forum: System76 Support
---

### Post by Nkosi on 2008-01-29
How can I re-iinstall my drivers using the System76 Driver Installer without a direct internet connection? I can manually copy to the hard disk via another laptop that is connected. 

I have a gazv3 using Ubuntu (Feisty).
Otherwise delighted customer!

---

### Post by thomasaaron on 2008-01-29
The driver does some things independently of an internet connection. Other things require a connection (ALSA) becuase it downloads packages.

If you have another System76 computer running Gutsy, it should have the alsa .deb package on it. You could conceivably transfer that package to your GazV3  and look at how the driver configures it.

If you are running Gutsy, the only actual driver installed would be for sound support.

---

