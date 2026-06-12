---
title: "Intel Driver 4000 Not installed."
date: 2015-04-09
forum: Ubuntu/Debian BASED
---

### Post by Zerochilli on 2015-04-09
Hi,

I'm using linux deeping 2014.2 and My Intel 4000 Graphics driver isn't installed I tried the Intel Linux graphics installer but no luck with it because it doesn't support 14.04 LTS which is what deepin is based on. And I cannot find any other way of installing it. However I have read that Intel are included in the kernel but deepin uses 3.13.0-49 while ubuntu uses 3.16 I believe. So I don't know how to get it working.

Help appreciated. Thanks.

---

### Post by buzzingrobot on 2015-04-10
The Intel driver is used automatically when active Intel video is detected on boot, unless the user has edited the kernel parameters line in grub's configuration to prevent it from being used, or removed the xserver-xorg-intel video package.

If your video is working correctly, there's really no reason to manually install another Intel driver.

If your video is not working correctly, something else is likely wrong.

---

### Post by Zerochilli on 2015-04-10
Thanks.

That solved my issue, I just thought it wasn't there but my video is working ok so it's there.

Thanks for the info ;)

---

