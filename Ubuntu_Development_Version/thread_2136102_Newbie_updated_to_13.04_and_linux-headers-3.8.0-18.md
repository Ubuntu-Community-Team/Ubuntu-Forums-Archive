---
title: "Newbie updated to 13.04 and linux-headers-3.8.0-18: now unity won't start."
date: 2013-04-16
forum: Ubuntu Development Version
---

### Post by waallen on 2013-04-16
Hello everyone, I've installed Ubuntu on my laptop last Friday. After I was done with setting up my stuff, I tried to install the ATI proprietary drivers (I am running on a 6990M) since I was using them on Crunchbang. I had some issues at first, like booting into a black desktop with no unity/compiz functionalities but uninstalling fglrx (if I had used apt to install the drivers) or running the ati uninstall script was enough to revert back to the open drivers. I finally managed to install the proprietary drivers by first installing the linux-headers package.
On Sunday I decided I wanted to install the 13.04 and everything was fine until today when I did a dist-upgrade which installed the linux headers mentioned in topic.
It looks like that the ATI proprietary drivers installation is successfully executed (I get the test only logo) but there are no bars appearing (unity seems to have 3d functionalities because desktop is quite responsive and so are apps even if I can't seem to drag the windows since there are no windows decorations). I tried to uninstall the ATI drivers in order to fall back to the open drivers but I boot to the same desktop with no bars.
I am not sure what has/is happened/happening, I'd be happy to just get back unity/compiz working even with open drivers but I don't know where to start looking for that. I guess I should also mention that compiz has been updated during that dist-upgrade.
Thank you in advance.

---

### Post by remixmabix on 2013-04-16
Same here (no dashboard) with 13.04, i try to install unity but it requires libnux-abiversion-20130411.0 which is not installable.

Thanks

---

### Post by waallen on 2013-04-16
In my it looks like drivers are correctly installed:```
wallen@drnng:~$ fglrxinfo display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6900M Series
OpenGL version string: 4.2.12173 Compatibility Profile Context 12.10.17

```

It seems to be an issue with compiz/dashboard/unity or something. I can even run fgl_glxgears.

---

### Post by philinux on 2013-04-16
Boot with a previous kernel from grub.  See if that works.

---

### Post by waallen on 2013-04-16
It looks like I fixed it by resetting compiz:```
 dconf reset -f /org/compiz/
setsid unity
```

---

