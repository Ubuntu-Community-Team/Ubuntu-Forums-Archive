---
title: "Need help Broadcom Corporation bcm4312 802.11b/G"
date: 2015-07-10
forum: Ubuntu Studio
---

### Post by guillem-benet on 2015-07-10
Hi everyone,

I have installed in my brother's laptop Ubuntu Studio and everything works fine except the wireless connection. I don't know how to install the drivers I need for the wireless card to work properly or whatever i need to install. When I installed Ubuntu in his laptop I also had the same problem but I don't remember how I solved. Btw the wireless card is the one in the post tittle.
Thanks,

---

### Post by Bucky Ball on 2015-07-10
Please open a terminal and input this command:

```
sudo lshw -C network
```

Post the output back here, please.

---

### Post by Frogs Hair on 2015-07-10
If there is driver available it will be in additional drivers and you also need to enter network password by opening the menu in the panels network indicator.

Here is the most recent solved thread I could find with a different solution.  [http://ubuntuforums.org/showthread.php?t=2212132](http://ubuntuforums.org/showthread.php?t=2212132)

---

### Post by guillem-benet on 2015-07-11
> **Bucky Ball said:**
> Please open a terminal and input this command:

```
sudo lshw -C network
```

Post the output back here, please.

Here is my output:

  	 	 	 	     *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:c1:4a:ee
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:21 memory:c0300000-c0301fff

---

### Post by Bucky Ball on 2015-07-11
Try this:
```

sudo apt-get update
sudo apt-get install firmware-b43-lpphy-installer
```

Reboot. Wireless? You may need to purge the other driver first as you have the wrong one installed for that card I think. .

---

### Post by guillem-benet on 2015-07-11
OK this is not working so how I purge the drivers? Also I found this website [http://www.broadcom.com/support/?gid=1](http://www.broadcom.com/support/?gid=1), but i don't know how to install them.

---

### Post by Bucky Ball on 2015-07-11
You don't. The drivers for your card are already available in Ubuntu and it is a matter of getting them installed correctly, not dragging in others from a third-party which may only cause confusion and further breakage.

You go [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access") and see how to purge the drivers. Try this:

```
sudo modprobe -r b43 bcma
sudo modprobe -r brcmsmac bcma
sudo modprobe -r wl

```

Then run the commands I gave earlier and reboot.

---

### Post by guillem-benet on 2015-07-12
Ok in step 3 when i have to install the firmware it appears to me something like an error, i don't know exactly, so I post it so you can help. Here is all the code:

```
                         arnau@arnau-Vostro-1000:~$ tar xfvj broadcom-wl-5.100.138.tar.bz2
broadcom-wl-5.100.138/
broadcom-wl-5.100.138/linux/
broadcom-wl-5.100.138/linux/wl_apsta.o
broadcom-wl-5.100.138/linux/wl_ap.o
broadcom-wl-5.100.138/linux/wl_sta.o
broadcom-wl-5.100.138/README
broadcom-wl-5.100.138/config/
broadcom-wl-5.100.138/config/wlconfig_lx_shared
broadcom-wl-5.100.138/config/wl.mk
broadcom-wl-5.100.138/config/wl_default
broadcom-wl-5.100.138/config/wl_hnd
broadcom-wl-5.100.138/config/wlconfig_nomimo
arnau@arnau-Vostro-1000:~$ sudo b43-fwcutter -w /lib/firmware broadcom-wl.5.100.138/linux/wl_apsta.o
[sudo] password for arnau: 
Cannot open input file broadcom-wl.5.100.138/linux/wl_apsta.o
 
```

---

### Post by jejeman on 2015-07-12
You are pointing to a non existing file. Change the path.

---

### Post by guillem-benet on 2015-07-12
Ok thanks, finally he can connect to the Internet.
Many thanks to everyone.

---

### Post by Bucky Ball on 2015-07-12
Please mark thread as solved. See second link in my signature.

---

