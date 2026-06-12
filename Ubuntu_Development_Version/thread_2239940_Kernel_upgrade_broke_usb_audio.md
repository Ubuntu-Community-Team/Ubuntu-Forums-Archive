---
title: "Kernel upgrade broke usb audio"
date: 2014-08-16
forum: Ubuntu Development Version
---

### Post by Stan_Bobovych on 2014-08-16
After upgrading from 3.16.0-5 to 3.16.0-6 (on Utopic), Arctic P531 USB headstop stopped working. It was not showing up in sound settings, but I was able to see it in alsa mixer. Modifying alsa-base.conf per instructions in [http://ubuntuforums.org/showthread.php?t=2163956](http://ubuntuforums.org/showthread.php?t=2163956) fixed the problem.

---

