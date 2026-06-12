---
title: "Problems with Kernel 6.11RC5 Ubuntu 24.10"
date: 2024-08-30
forum: Ubuntu Development Version
---

### Post by bjo101 on 2024-08-30
Hello,

I tried using the 6.11rc5 kernal on Ubuntu 24.10 on VMWare workstation the OS seems to load and be running but I get no display.  If I boot the same install on the same physical, hardware It doesn't load my NIC witch is a Realtek Gbe family controller or my graphics drive for an NVidia GTX950.  has anyone solve either of these scenarios?

---

### Post by jbicha on 2024-08-30
Ubuntu 24.10 has Linux 6.8, not Linux 6.11.

Yeah, Linux 6.11RC is in -proposed but you should not expect things to work perfectly if you are installing things from there.

I guess you could report a bug against linux in Launchpad.

A few things are not expected to work with Linux 6.11 RC like Nvidia drivers. I think the plan is for the installer to give those computers Linux 6.8 until things are ready for the upgrade to 6.11.

---

### Post by blueadept on 2024-09-03
> **jbicha said:**
> Ubuntu 24.10 has Linux 6.8, not Linux 6.11.

Yeah, Linux 6.11RC is in -proposed but you should not expect things to work perfectly if you are installing things from there.

I guess you could report a bug against linux in Launchpad.

A few things are not expected to work with Linux 6.11 RC like Nvidia drivers. I think the plan is for the installer to give those computers Linux 6.8 until things are ready for the upgrade to 6.11.

Is the "kernel-proposed" repo no-longer being maintained, as it has 6.10, but this 6.11RC kernel seems to be in -proposed only....

---

### Post by IanW on 2024-09-04
> **blueadept said:**
> Is the "kernel-proposed" repo no-longer being maintained, as it has 6.10, but this 6.11RC kernel seems to be in -proposed only....

It's possible this is due to the recent change Canonical announced for Ubuntu kernels.

[https://discourse.ubuntu.com/t/kernel-version-selection-for-ubuntu-releases/47007](https://discourse.ubuntu.com/t/kernel-version-selection-for-ubuntu-releases/47007)

---

