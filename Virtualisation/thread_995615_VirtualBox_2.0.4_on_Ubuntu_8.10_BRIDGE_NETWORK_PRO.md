---
title: "VirtualBox 2.0.4 on Ubuntu 8.10 BRIDGE NETWORK PROBLEMS"
date: 2008-11-28
forum: Virtualisation
---

### Post by efsandino on 2008-11-28
Hi, i am using VirtualBox 2.0.4 on Ubuntu 8.10 i have the following problem after configuring my Bridge Networks. 
1. My wired networks go disconfigured after reboot i asume cos i have modified the file:

/etc/network/interfaces

The original file in my system has:

auto lo
iface lo inet loopback


But if i want that my virtual machines can have his own real ip and get in my lan i need add a Bridge, i have installed the bridge package with:

sudo apt-get install bridge-utils

And after all i have to modify the file: 
/etc/network/interfaces adding the next lines:

	auto br0
	iface br0 inet dhcp
	    bridge_ports eth0

How i said after i reebot my system my wired networks get disconfigured so i have to erase that lines to work in my lan... I have noted that the interfaces file on my last ubuntu 8.10 was more complete than the actual one on Ubuntu 8.10 i see its all in AUTO MODE and when i try to modify this configuration with the graphic configuration tool the changes does not get actualized correctly the next time i reebot my system. Can Anyone help me to get working 100% my bridged network for VirtualBox machines...

Thanks..

---

### Post by bodhi.zazen on 2008-11-28
I wrote some basic instructions in the virtualization mega thread.

The problem is with network manager, so first stop your network, then edit /etc/network/interfaces , then bring yoru network back up.

You can either add a tap interface(s) to this same file or (I need to add this to the sticky) make one with VboxAddIF

```
sudo VBoxAddIF vbox0 <user> br0
```where <user> is your log in user.

You can add additional devices, these devices are perminent and you can delete them with 

```
sudo VBoxDeleteIF vbox0
```

---

