---
title: "Atheros Device [168c:003e] (rev 32) Zorin(Ubuntu) not connecting at all."
date: 2016-01-21
forum: Ubuntu/Debian BASED
---

### Post by zra on 2016-01-21
Full info about system:
Alienware 15 R2
512GB Nvme ssd
1TB ISCI HDD (physically removed)
16GB RAM
Nvidia 980M
E2400 Ethernet (3b:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [1969:e0a1])
1535 WiFi (3c:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:003e])
Zorin 10 Ultimate64bit (Ubuntu 15.04)
I have 2 other USB Wifi Dongles that I used during installation, and updates.

I ran sudo apt-get update, sudo apt-get upgrade, and sudo apt-get update again.
I installed my Ethernet drivers, following this guide. (post 2)
[http://askubuntu.com/questions/670347/is-there-any-way-to-install-atheros-e2400-drivers](http://askubuntu.com/questions/670347/is-there-any-way-to-install-atheros-e2400-drivers)
Issue with that is that it stopped working upon reboot, so i ran these commands to solve it (havnt rebooted since)
cd ubuntu-vivid/drivers/net/ethernet/atheros/alx/
&#65279;sudo modprobe -r alx
sudo depmod
sudo modprobe -v alx
This killed my 2 usb wifi cards.
I ran sudo apt-get update afterwards, and went on to trying to install the wifi drivers.
[http://www.killernetworking.com/support/knowledge-base/17-linux/20-killer-wireless-ac-in-linux-ubuntu-debian](http://www.killernetworking.com/support/knowledge-base/17-linux/20-killer-wireless-ac-in-linux-ubuntu-debian)
Following this; i created the folder: /lib/firmware/ath10k/QCA6174/hw3.0
In that map, I placed firmware-4.bin and broad.bin Both from the 1535 download.
sudo apt-get update'd and tried rebooting. nothing happened, so i installed a backport for ath10k, and it does not seem to be running together with the device (??)
Please read the attachment for further information

---

### Post by howefield on 2016-01-21
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by jeremy31 on 2016-01-27
Uninstall ndiswrapper as it isn't helping, go into the backports directory then ```
sudo make uninstall
```
Reboot, then change into the backports directory again and```
make clean
make defconfig-wifi
make
sudo make install
```

Reboot again, hopefully you have set the ath10k_core skip_otp parameter

---

