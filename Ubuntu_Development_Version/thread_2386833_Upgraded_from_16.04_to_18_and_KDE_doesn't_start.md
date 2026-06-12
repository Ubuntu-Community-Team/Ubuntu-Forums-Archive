---
title: "Upgraded from 16.04 to 18 and KDE doesn't start"
date: 2018-03-11
forum: Ubuntu Development Version
---

### Post by jorritTyb on 2018-03-11
So I just updated my kubuntu system from 16.04 to 18 and KDE no longer starts. I just get a normal console login. If I try to do startkde from there I get:

> $DISPLAY is not set or cannot connect to the X server.

I can do startx but then I get a low resolution desktop (1024x768) instead of what my nvidia card is capable off.

Any clues as to what can be wrong? Also when starting up my computer (before the console login window appears) I get a bunch of messages like these:

> 
[   0.045791] ACPI Exception: Could not find/resolve named package element: \_SB_.PCIO.LNK9 (20170831/dspkginit-381)


I never saw those messages when my system was still 16.04. Not sure if this has anything to do with my problem?

Thanks for any support and let me know if you need more info

---

### Post by wildmanne39 on 2018-03-11
*Thread moved to **Ubuntu Development Version, a more appropriate forum**.*

---

### Post by QIII on 2018-03-11
Hello!

Could you give us your hardware specs and tell us whether you had any proprietary drivers installed?

---

### Post by jorritTyb on 2018-03-11
Yes I had the proprietary nvidia drivers (don't remember what version though). I have a GTX 460 nvidia card. I just tried to manually update the nvidia drivers to nvidia-390 package using this guide ([http://www.webupd8.org/2016/06/how-to-install-latest-nvidia-drivers-in.html](http://www.webupd8.org/2016/06/how-to-install-latest-nvidia-drivers-in.html)) and now my system just hangs at restart... Seems I just made it worse.

Is there some kind of safe mode so I can get back to my system? I don't get a login anymore. The system just hangs when it seems to try to start the window manager.

---

### Post by QIII on 2018-03-11
One of the easiest ways to create for yourself a significant emotional event when upgrading to a new release is to fail to uninstall proprietary video drivers.

It's been a long time since I used Nvidia hardware, but I'm pretty sure that if you uninstall all Nvidia drivers from the terminal you'll be able to start again.  Log in to the text environment.  You'll have to mount the file system read-write to make changes, so issue

```
sudo mount -o remount,rw /
```

(please cut and paste that verbatim)

and then issue whatever commands are required to remove the Nvidia driver(s).

---

### Post by jorritTyb on 2018-03-11
Yes I managed to get this far and now my system starts in window mode but in very low resolution. How can I get the nvidia drivers back? Or what drivers do you recommend?

Edit: solved! Managed to get the 'recommended' drivers to work. Thanks

---

