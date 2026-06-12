---
title: "How to change to older Nvidia drivers"
date: 2021-07-10
forum: Ubuntu/Debian BASED
---

### Post by sx200n on 2021-07-10
Hello, I am running pop os 20.04 and have had issues with steam play ever since moving to the 460 Nvidia drivers. Is there a simple way of moving back to an older driver such as the 450. There are known issues with the 460 and some games and prior to moving to it, every game on steam play worked like a dream, so would like to reverse back to the 450 drivers.

---

### Post by TheFu on 2021-07-10
If the drivers are in the repo, just remove the new ones, install the older ones and put a "hold" on the one you want to keep using synaptic or apt-mark.
Drivers are tied to the kernel version, so expect breakage.

---

### Post by mastablasta on 2021-07-12
open additional drivers and install the version you want.

---

### Post by not-published on 2021-08-26
deleted never mind

---

### Post by monkeybrain20122 on 2021-08-26
Or  you can upgrade to 470 [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

BTW How did you install 460 and how did steam break? The driver from Nvidia's cuda repo does not support 32 bit and hence steam breaks. [https://github.com/ValveSoftware/steam-for-linux/issues/5778](https://github.com/ValveSoftware/steam-for-linux/issues/5778)

If this is the same issue then just have to install driver from sources other than the cuda repo (ppa above or Ubuntu's standard repo or [system76's ppa]("https://launchpad.net/~system76-dev/+archive/ubuntu/stable"), and last, though not recommended, Nvidia's run file) Cuda can be installed separately from the local installer (without sudo and without installing the driver)

---

### Post by Irihapeti on 2021-08-26
*Thread moved to **Ubuntu/Debian BASED**, as the OS isn't Ubuntu or a flavour.*

---

### Post by nicolas-santorsola on 2021-12-05
Hi. I am having a similar issue.

My PC has a EVGA NVIDIA GeForce GTX 560 graphics card, and the only way to not being stuck with 640 x 480 resolution was to uninstall nvidia-driver-470 and install 390, However, even holding that package with synaptics, after doing an upgrade of the system, it keeps the driver but it locks again to 640 x 480.

I managed to do a backup of the system and somehow restore it under 640 x 480 without seeing the buttons, however I need to do a selective upgrade to locate which package is the one breacking the old driver.

Is there a way to do a selective upgrade instead of a full upgrade?

Thanks for reading.

---

