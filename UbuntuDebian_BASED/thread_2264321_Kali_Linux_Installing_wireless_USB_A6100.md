---
title: "Kali Linux Installing wireless USB A6100"
date: 2015-02-06
forum: Ubuntu/Debian BASED
---

### Post by toadill9114 on 2015-02-06
Hello everyone I am having problems installing my new wireless USB A6100 mini Adapter AC600 Dual band
ID 0846:9052 Netgear, Inc.
I have downloaded the driver for this device from the Netgear website. I am not sure if this will work. 
I am running a live Kali linux CD and have also tried this with a VM. So far no luck :(
I have also read other threads on this forum that related to installing this device but still having no luck. :(
Any help is appreciated.

---

### Post by kerry_s on 2015-02-06
plug it in & do "lsusb" in terminal so we can see what fimware it needs.

---

### Post by toadill9114 on 2015-02-06
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f2:b289 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0846:9052 NetGear, Inc. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by toadill9114 on 2015-02-06
> Your device uses the rare and elusive driver 8812au. Please get a  temporary wired ethernet or similar connection, go back to the terminal  and do: 	Code:
 	sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone [https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git](https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git)
cd ~/rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe 8812au 
Your wireless should now be working.

Post back any errors; warnings are probably alright. I will have one additional step. 				

sudo apt-get update 
Works okay

but when I run

sudo apt-get install linux-headers-generic build-essential git

I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-headers-generic' has no installation candidate

---

### Post by jeremy31 on 2015-02-06
[http://ubuntuforums.org/showthread.php?t=2235778](http://ubuntuforums.org/showthread.php?t=2235778)

---

### Post by kerry_s on 2015-02-06
found it: [http://ubuntuforums.org/showthread.php?t=2240631](http://ubuntuforums.org/showthread.php?t=2240631)

doubt your going to be able to do it on a live system.

---

### Post by coffeecat on 2015-02-06
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by toadill9114 on 2015-02-06
> **kerry_s said:**
> found it: [http://ubuntuforums.org/showthread.php?t=2240631](http://ubuntuforums.org/showthread.php?t=2240631)

doubt your going to be able to do it on a live system.

sudo apt-get install linux-headers-generic build-essential git

I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-headers-generic' has no installation candidate

---

### Post by toadill9114 on 2015-02-06
> **coffeecat said:**
> *Thread moved to **Ubuntu/Debian BASED**.*

Does this make installing the driver different?

---

### Post by toadill9114 on 2015-02-06
Also I thought this would work for this O/S 
Standards are:
IEEE* 802.11 b/g/n 2.4 GHz
IEEE* 802.11 a/n/ac 5.0 GHz

---

### Post by coffeecat on 2015-02-06
You are trying to follow instructions for Ubuntu in Kali Linux, which is not even based on Ubuntu. 

As someone has said, installing wireless drivers on a live CD session isn't going to work, even if you found instructions relevant for Kali.

---

### Post by toadill9114 on 2015-02-06
> **coffeecat said:**
> You are trying to follow instructions for Ubuntu in Kali Linux, which is not even based on Ubuntu. 

As someone has said, installing wireless drivers on a live CD session isn't going to work, even if you found instructions relevant for Kali.

Could this work correctly through a VM?

---

### Post by chili555 on 2015-02-06
We know nothing about Kali. Sorry.

If the method I suggested for Ubuntu doesn't work in Kali, then I have no other suggestions.

---

### Post by QIII on 2015-02-06
Might I suggest forums.kali.org?

---

