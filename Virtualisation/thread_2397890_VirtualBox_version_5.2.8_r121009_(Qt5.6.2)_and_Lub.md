---
title: "VirtualBox version 5.2.8 r121009 (Qt5.6.2) and Lubuntu 18.04 black screen"
date: 2018-08-04
forum: Virtualisation
---

### Post by rtek1000 on 2018-08-04
Hello  everyone,

Just to be aware, after installing Lubuntu, everything went  well,

But I tried changing the screen resolution to 1366x768 (before it  should have been 800x600) and after that I could no longer have the  desktop image.

Only the login screen appears, and after login the screen turns black.

I tried to make some suggested settings on some forums, but nothing worked, I did not find anything specific to Lubuntu 18.04.

Since this is a new installation, I will delete the machine and create a new one.

Thank you.

---

### Post by deadflowr on 2018-08-04
*Thread moved to **Virtualization***

---

### Post by rtek1000 on 2018-08-04
Hello,

I found a solution to my problem:

> sudo apt install build-essential dkms

> 
Selecting *Devices -> Install Guest Additions* (or press Host+D from the Virtual Box Manager) the Guest Additions CD .iso will be loaded but **not installed** in your guest OS. To install we need to run the installer script VBoxLinuxAdditions.run as root

> cd /media/user/Vbox_GAs_5.2.8/
sudo ./VBoxLinuxAdditions.run
sudo reboot
After restarting the system, the resolution was **automatically reconfigured**

Source:
[How do I install Guest Additions in a VirtualBox VM]:
[https://askubuntu.com/questions/22743/how-do-i-install-guest-additions-in-a-virtualbox-vm](https://askubuntu.com/questions/22743/how-do-i-install-guest-additions-in-a-virtualbox-vm)

---

