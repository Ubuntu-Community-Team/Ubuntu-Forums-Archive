---
title: "Cant install Nvidia Drivers"
date: 2023-10-22
forum: Ubuntu/Debian BASED
---

### Post by cystolx on 2023-10-22
[https://pasteboard.co/XYH3hQRqxmrs.png](https://pasteboard.co/XYH3hQRqxmrs.png)

im using wubuntu
and i cant select the nvidia driver to install
im using nomodset and i have disabled noveau
and i have xanmod kernel
No matter what I Select, The Apply option is grayed out
Please help

---

### Post by MAFoElffen on 2023-10-22
Wubuntu is a new Ubuntu derivative distribution in it's infancy...

I can only authoritatively talk about what is Ubuntu itself, without their possible modifications, only because I have no personal experience with that distribution. So take this with a grain of salt...

If you install NVidia drivers from the "Additional Drivers" tab of "Software & Updates", it does not say what is recommended for your device. One thing I notice about what that dialog is saying is that it is already using NVidia drivers, but say that it is using all of them at once???

What I would do first is do
```

sudo apt remove --purge nvidia-*

```
Then reboot and start up that dialog window again and see what it says then about wht is installed, what the choices are, and if the apply butten changes to not being grayed out, after you select a radio button...

But this is a different Distro... That doesn't guaranty that works with that Distro...

If you had posted what the Video device was specifically, then we could recommend what NVidia drivers works for one of us... Info on that could be found via
```

sudo lspci | grep -A3 -Ei 'vga|display|3D'
sudo lshw -C video | grep -e 'product\|driver'

```
With the results posted within CODE Tags.

Another way that helps Ubuntu users and it's own flavors, is that we use the utility 'ubuntu-drivers'
```

sudo ubuntu-drivers list
# look at the drivers displayed
sudo ubuntu-drivers install
# Let it install what it thinks is the recommended driver on it's own
sudo ubuntu-drivers install nvidia:530
# Install a specific driver from the displayed list from the list output above...

```
I do not know if Wubuntu has that utility in their repository, so that is a guess on my part, for you to try to see for yourself... It may or may not be there in their repository, and it may or may not be installed by them in their system installation as a default on that distribution...

If that doesn't work for your Distro, then there are other ways...

---

### Post by coffeecat on 2023-10-22
Not an official flavour.

*Thread moved to **Ubuntu/Debian BASED**.*

---

