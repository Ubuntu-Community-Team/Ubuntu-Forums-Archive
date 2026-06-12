---
title: "Desktop session restarts by itself"
date: 2015-11-22
forum: Ubuntu Development Version
---

### Post by Blackbug on 2015-11-22
I am using Cinnamon desktop env over ubuntu 16.04. While working, the desktop session restarts itself without any kinda warning messages. This leads to loss of all the work I am doing the moment session restarts. At the moment, this happens on Cinnamon desktop env over 16.04, however, I faced similar problem with xubuntu 15.10 a month ago. After I upgraded to 16.04 and cinnamon, I didnt have such issues for few weeks, but again they are back.

I am not sure which config files are somehow disrupted leading to such unpredictable behavior.

Please suggest.

Thanks.

---

### Post by ian-weisser on 2015-11-23
> **Blackbug said:**
> While working, the desktop session restarts itself without any kinda warning messages. This leads to loss of all the work I am doing the moment session restarts.

If you get returned to the login screen, the X server has crashed.
Look in /var/log/syslog, /var/log/Xorg.0.log, and /var/crash for helpful clues to why.

---

