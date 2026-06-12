---
title: "xorg.conf problem?  PanP6 6 windows on startup, shutdown"
date: 2010-02-03
forum: System76 Support
---

### Post by patchwork on 2010-02-03
Hi.  I have a PanP6 that has been working beautifully, until this morning.  I don't recall doing anything that would cause this, but all of the sudden on startup and shutdown my display reverts to six small windows.  My splash, login screen, and gnome session open as expected, so this seems to be a matter of aesethics.  I verified my xorg.conf to the version Tom submitted here: [http://ubuntuforums.org/showthread.php?t=1347503](http://ubuntuforums.org/showthread.php?t=1347503), and followed the given instructions just to make sure.  Unfortunately, after moving the xorg.conf file, I still get a message stating ```
Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid.
```when attempting to re-install the nvidia 185.18.36 driver.  I then removed and reinstalled the driver, and copied the xorg.conf file back.  Upon reboot, I still have the six screens during startup and shutdown.
 In the proprietary drivers gui, my nvidia driver is not activated, but states that another version of this driver is in use.  
If anyone has any input, I'm all ears.  As I said, I have not done anything dramatic (like reinstalling) that I can remember.

---

### Post by thomasaaron on 2010-02-03
Hi, patchwork.

I have the fix to this, but I need to send you an xorg.conf file. Can you please shoot me an email at support...at...system76...dot...com.

---

