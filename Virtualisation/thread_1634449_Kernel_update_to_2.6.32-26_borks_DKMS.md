---
title: "Kernel update to 2.6.32-26 borks DKMS"
date: 2010-11-30
forum: Virtualisation
---

### Post by JKyleOKC on 2010-11-30
The recent security update for 10.04 LTS includes a new kernel version, 2.6.32-26. After installing it on a test system, my VirtualBox installation failed to start because vboxdrv failed to load. Attempting to rebuild it per the error message failed. However, rebooting and selecting the previous kernel, 2.6.32-24, allowed me to rebuild the modules and restored operation.

Searching the file system shows that the linux headers for the new version were NOT included in the update, causing DKMS to fail in its purpose of rebuilding the necessary driver modules.

While it's easy enough to manually install the header package via Synaptic, my question is "What other essential packages were omitted from this update?" While waiting for the answers, I'm not installing this update on my main system, because my data recovery business depends on having VMs operational (my customers all use Windows so I must maintain compatible systems).

Strangely, searching the forums for this problem did not yield any hits. Is it unique to my installations, or what???

---

### Post by JKyleOKC on 2010-12-02
Installing the linux-headers-2.6.32.26 package via Synaptic, building the drivers, and rebooting has made it work again.

---

