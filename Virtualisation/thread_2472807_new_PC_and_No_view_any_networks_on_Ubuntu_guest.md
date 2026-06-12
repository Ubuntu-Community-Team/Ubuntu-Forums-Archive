---
title: "new PC and No view any networks on Ubuntu guest"
date: 2022-03-13
forum: Virtualisation
---

### Post by sergiots on 2022-03-13
Hello! 

I have installed a new PC and copied my vmware virtual machine to it.
Unfortunately I am not able to get any network connections working in the guest OS.


ifconfig only shows the loopback network.
I tried both Bridged, NAT and Host-only. I already used the Virtual Network editor to make sure bridged uses the correct adapter on the host.


But since NAT and Host-only also doesn't work I think something else is wrong, but I have no clue what I could do.


The host OS is using a WiFi adapter on the motherboard.
I use VMware Workstation Pro 14.1.7 build-12989993
My host OS is Windows 10 Pro.
My guest OS is Ubuntu 18.04.1 LTS


I would very much appreciate any help.
Thanks!

---

### Post by QIII on 2022-03-13
Moved to ***Virtualisation***

---

### Post by sergiots on 2022-03-17
Hi, no any reply about this?

---

### Post by MAFoElffen on 2022-03-17
Since your Host OS is Windows 10 Pro, peope here might be a bit hesitant to answer... Windows has some caveots about 'sharing' network interfaces...

When doing VM Hosts on Windows, it gets more intricate. Make sure you do a backup to be able to get back to a working configuration. You want to use a "Bridged" connection. Tradtiionally, if you used a bridge connection on Windows to get access between a virtual switch to a real netwrok device on your host network, then that network device is marked as a dedicated device and you lose it as an asset to the host... That is the easy, short, summarized answer.

There are ways to make a NIC 'shared' between VSwitch and the Host, for both to use... But is includes very detailed configuration setup, that must be followed to the letter. Follow a guide or tutorial somewhere to do it. I would suggest one on MS TechNet or the MS Doc's. The reason I suggest a backup "before" and many screenshots during that(?). I've done this myself, and if you do not do that, it is almost impossible to back off the changes or to remove it without a reinstall. So be warned.

Easiest and fastest still, is to dedicate a network device to the virtual network. Even if you have a laptop and cannot add an internal NIC,,, get a portable USB NIC, that will be dedicated for your bridge... If that is what you need. Much simpler.

---

