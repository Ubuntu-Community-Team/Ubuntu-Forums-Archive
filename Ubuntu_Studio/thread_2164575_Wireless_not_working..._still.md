---
title: "Wireless not working... still"
date: 2013-08-01
forum: Ubuntu Studio
---

### Post by Jacob-Gates on 2013-08-01
Hey guys, I have been using Ubuntu ever sense 10.10 and I have regularally upgrade to the newest version and I am used to dealing with the wireless problem with my Dell Studio laptop. Well I have added ubuntu studio to my hard drive and I just can't get the wireless working. I have search up every way I can do it and nothing has worked. If I open the software center and go to softerware sources then to the addtional drivers tab it says the the broadcom driver is there, and it is selected to be used... but still no wireless. Here is what I remember trying (I could have used others, I have spent all day googling different commands and way to fix this):

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

and

```
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter
sudo reboot
```

and 

```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo apt-get install firmware-b43legacy-installer
sudo modprobe -r b43 ssb wl
sudo modprobe wl

```

and

```
sudo apt-get update
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source

sudo apt-get install b43-fwcutter firmware-b43-installer



```

I know there were others but I can't find them nor can I remember them. If you suggest them the worst I can do is just try them again and they not work. If anyone can help I would greatly appreciate it. Thanks guys!

---

### Post by jejeman on 2013-08-01
What is the Ubuntu Studio version? Does wifi in Ubuntu of the same version works?
If not:
This question is not for Ubuntu Studio sub forum. 
Moderators should move this to general Ubuntu help where this can be resolved more quickly.

As far as I can see, something cahnge with broadcom cards in recent Ubuntu versions, and the old instructions are not valid anymore.
Did you see this
[http://ubuntuforums.org/showthread.php?t=2163523](http://ubuntuforums.org/showthread.php?t=2163523)

Also you should give hardware information
```
lshw -numeric -C network
```

---

### Post by Jacob-Gates on 2013-08-01
> **jejeman said:**
> What is the Ubuntu Studio version? Does wifi in Ubuntu of the same version works?
If not:
This question is not for Ubuntu Studio sub forum. 
Moderators should move this to general Ubuntu help where this can be resolved more quickly.

As far as I can see, something cahnge with broadcom cards in recent Ubuntu versions, and the old instructions are not valid anymore.
Did you see this
[http://ubuntuforums.org/showthread.php?t=2163523](http://ubuntuforums.org/showthread.php?t=2163523)

Also you should give hardware information
```
lshw -numeric -C network
```

it is ubuntu stuido 13.04 and in normal ubuntu 13.04 wifi works fine so it doesn't need to be moved. I have never had this much trouble in normal ubuntu but in ubuntu studio it just isn't working.

Here is the output for that command:
```
 *-network                      description: Network controller
       product: BCM4312 802.11b/g LP-PHY [14E4:4315]
       vendor: Broadcom Corporation [14E4]
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe [14E4:1698]
       vendor: Broadcom Corporation [14E4]
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:e7:c5:4e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 duplex=full firmware=sb v2.17 ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:fc500000-fc50ffff



```

---

### Post by jejeman on 2013-08-01
There should be no difference beetwen Ubuntu and Ubuntustudio regarding network setup and hardware drivers. Both use network manager and the same kernel version.
Just do what you did in Ubuntu to set it up.

I see that the driver b43-pci-bridge is installed. 
For card 4315 you need, bcmwl-kernel-source,  which is properitary STA driver. I see that you had purged it. The module is "wl". You should insert it if it is not automaticly. You can blacklist b43. As I can understand you don't need firmware, but you can leave it if you already installed it.
You can prorbably use jockey to install the "Broadcom STA wireless driver" driver.

---

### Post by Jacob-Gates on 2013-08-01
well in ubuntu 13.04 i didn't have to do anything, when I install it the live disk just realized I had broadcom and installed it for me, apparently Ubuntu finally realized their issues with those drivers. Anyways, I have blacklisted b43, nothing has changed. I tried to install bcmwl-kernel-source in terminal and it said it was already installed. and according to the software sources>additional drivers I already have "Broadcom STA  wireless driver" installed. from what I understand there should be no reason it's still not working but it's not.

---

### Post by gordintoronto on 2013-08-01
Did you *upgrade* to Ubuntu 13.04, but do a fresh install of Studio?

---

### Post by Jacob-Gates on 2013-08-01
> **gordintoronto said:**
> Did you *upgrade* to Ubuntu 13.04, but do a fresh install of Studio?

I did a fresh install of both. In the install GUI of normal Ubuntu 13.04 they added a section to add the Broadcom wireless before you install it and asks you to connect to a WiFi. Who ever is in charge of making that part of Ubuntu Studio didn't include the same thing and I have to do it like I had to in the past versions.

---

