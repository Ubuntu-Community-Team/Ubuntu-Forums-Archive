---
title: "vmware x11 xwindows memory leak"
date: 2008-09-18
forum: Virtualisation
---

### Post by unclecameron on 2008-09-18
I've been running workstation 6.0.4 build 93057 on an Ubuntu Linux Hardy host for 3 months successfully, sudddenly my guest WinXP VM (and any other VM's) is taking up tons of memory for /usr/bin/X, and has become unusable. My host machine is a dual core AMD 64 2.0GHz cpu with 3G RAM, the guest VM is using 2G RAM on a 30G WinXP 64bit VM with 8.3G free space. The guest VM will run for 30 minutes or less just fine, then the memory on the host spikes, and I have to shut down both the host and guest, logout of XWindows and try it again. It takes roughly 30 minutes to power down the guest VM properly. Htop shows /usr/bin/X taking up 55% memory, and vmware-vmx running about 20 processes consuming 8.8% memory each, though CPU usage remains low. I have anti-virus software on both host and guest. I upgraded today to 6.0.5 and it didn't help. It seems like some sort of memory leak or mismanagement with Xwindows, but my machine has tons of RAM and CPU, ideas?

---

