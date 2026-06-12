---
title: "[SOLVED] Whats that command line?"
date: 2008-11-13
forum: Windows
---

### Post by shiningkenmonster on 2008-11-13
When people bring their WINDOWS wifis laptops. People usually come up to me and ask how do they connect to the wifi. Its usually troubles connecting online.

how do you connect online with the Command Prompt with the ipconfig command line? 

I believe there was more than just "ipconfig" and something after it

---

### Post by I-75 on 2008-11-14
(I used the following to enable Wifi on my Compaq 762NR laptop with Ubuntu 8.04. There are other variations to the script. This should point you in the right direction. Good Luck)



[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)






sudo apt-get install build-essential

Then open the terminal from Applications&#8211;>Accessories&#8211;>Terminal and copy the following command

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

make

sudo make install

sudo modprobe ath_pci

sudo reboot

---

### Post by Skripka on 2008-11-14
d'oh wrong forum....

---

### Post by cardinals_fan on 2008-11-14
```
iwconfig interface0 essid myessid1
```

---

### Post by shiningkenmonster on 2008-11-14
wait, i am talking about WINDOWS for command prompt. is that the command?

---

### Post by cammin on 2008-11-14
ipconfig won't do that.

Vista has netsh
[http://technet.microsoft.com/en-us/library/cc755301.aspx](http://technet.microsoft.com/en-us/library/cc755301.aspx)

With XP, you have to add a new preferred network through the wireless network properties. It's probably easier to do that in Vista, too.

---

