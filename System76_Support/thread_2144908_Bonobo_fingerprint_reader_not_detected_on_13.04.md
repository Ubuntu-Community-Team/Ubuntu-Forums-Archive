---
title: "Bonobo fingerprint reader not detected on 13.04"
date: 2013-05-13
forum: System76 Support
---

### Post by Murukesh on 2013-05-13
I have a Bonobo Extreme, with Ubuntu 12.10 (the one which comes preinstalled), Windows 8 and Ubuntu 13.04 installed. 13.04 initially started from the beta, it was fully upgraded about ten days ago. The fingerprint reader stopped working on 13.04 yesterday, but still works fine in 12.10 and Win8. That is, the pop-up asking me to swipe no longer appears and the fingerprint-gui app says "No Devices Found!', even though the device is listed. I have tried:
[LIST]
[*]Removing and reinstalling the fingerprint-gui and related programs following the directions on knowledge76. 
[*]Updated the System76 driver and installed drivers. 
[*]Again removing and reinstalling fingerprint-gui. 
[*]The above steps had a couple of log-off/log-in and reboots in between them. 
[/LIST]
I noticed that there are others who have faced the same issue with the 147:1002 reader, though not on system76 laptops - see [http://askubuntu.com/questions/103587/fingerprint-gui-can-not-recognize-my-upek-reader-147e1002](http://askubuntu.com/questions/103587/fingerprint-gui-can-not-recognize-my-upek-reader-147e1002). So I'm asking here before trying out things suggested in those posts.

---

### Post by jawsdaws on 2013-05-14
There is an update for fingerprint-gui and polkit.  It solved my troubles.

---

### Post by Murukesh on 2013-05-14
Yep. That update fixed things. I should have waited a couple of days. Thanks!

---

### Post by chmegr on 2013-05-17
worked on mine right away....maybe I missed the first update

---

### Post by chmegr on 2013-05-17
You should probably mark this thread as closed....it's under thread tools.

---

### Post by Edward_G_Prentice on 2013-08-29
The fingerprint gui seems to work, allowing me to login with a fingerswipe or typing the password. Cool feature. I'm curious, however, why the fingerprint-demo app can't find the fingerprint device.

---

