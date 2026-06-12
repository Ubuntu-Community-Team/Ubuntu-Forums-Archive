---
title: "Nvidia Driver not Used"
date: 2014-04-26
forum: System76 Support
---

### Post by whollycow on 2014-04-26
I'm a Ratel owner and recently did a complete reinstall with the new 14.04. I installed the Nvidia driver as directed ```
sudo apt-get install system76-driver-nvidia
``` but when I bring up the System76 driver window, it tells me that all drivers are being provided by Ubuntu:
[ATTACH=CONFIG]252553[/ATTACH]

Am I missing something?

---

### Post by Newbunto on 2014-04-28
I see the same thing. However if you go to System Settings / Software & Updates / Additional Drivers

it says that the nVidia driver is in use (specifically 331.38 from nvidia-331-updates).

Confusing? Yes. Indicative of an actual problem? Maybe not.

/var/log/Xorg.0.log suggests that the nVidia driver is in use.

---

