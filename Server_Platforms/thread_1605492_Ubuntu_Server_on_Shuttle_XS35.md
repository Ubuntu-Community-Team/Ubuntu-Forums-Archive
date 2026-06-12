---
title: "Ubuntu Server on Shuttle XS35"
date: 2010-10-25
forum: Server Platforms
---

### Post by jeffbarish on 2010-10-25
I installed Ubuntu Server 10.04 on a Shuttle XS35.  It worked except for the Wifi.  Even after installing a driver from Realtek and updating the BIOS (so that I could force the Wifi to be on all the time) I still could not get Wifi to work.  I was hoping that the problem would vanish with 10.10, but with 10.10 I find that not only does Wifi not work, Ethernet does not work either (the installer did not recognize the hardware).  Both work fine with Ubuntu Desktop 10.10 (and 10.04).  I discovered that I could run the Desktop version headlessly, so I am now wondering whether a reasonable strategy would be to start with the current Ubuntu Desktop installation and remove components I don't need (e.g., the X server).  If so, can anyone suggest which components I can safely remove?

---

### Post by Ow@&amp;#fy on 2010-11-10
Hi jeff,

[I]I installed Ubuntu Server 10.04 on a Shuttle XS35. It worked except for the Wifi. Even after installing a driver from Realtek and updating the BIOS (so that I could force the Wifi to be on all the time) I still could not get Wifi to work. I was hoping that the problem would vanish with 10.10, but with 10.10 I find that not only does Wifi not work, Ethernet does not work either (the installer did not recognize the hardware). Both work fine with Ubuntu Desktop 10.10 (and 10.04).
[/I]

Running lspci should give you something like :

```
# update-pciids
# lspci 
...
02:00.5 Ethernet controller: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)

```

The ethernet controller should work ok with the jme driver (try ```
modprobe -l | grep jme
``` to check if you have it, then load it ```
modprobe jme
``` and see if you can get better results.


As for the wifi module, I, for one, am desperately trying to make it work on a XS35GT, and I would be really grateful if you could give pointers to how you succeeded to make it work under Ubuntu. I've been trying for days, using either the built-in driver (r8192se_pci) or the Win2k drivers with ndiswrapper, with no success so far.



*I discovered that I could run the Desktop version headlessly, so I am now wondering whether a reasonable strategy would be to start with the current Ubuntu Desktop installation and remove components I don't need (e.g., the X server).* 

Well, it might take some time and may not work flawlessly, but if it actually works for you, until you find an quicker solution, why not ? 

*If so, can anyone suggest which components I can safely remove?*

It's hard to tell you exactly what you should remove from your system, since it really depends on what you plan to do with it and how you use it, but you might be interested in the following thread (*deborphan* and *debfoster* may be your friends too): [HowTo: Create a list of installed packages]("http://ubuntuforums.org/showthread.php?t=261366").

---

### Post by rladams65 on 2011-01-28
Gentlemen,

I saw this thread as I was installing Ubuntu 10.10 server on an Shuttle XS35.  I was dreading the outcome.

I did not have the issues you described.  I had previously done the 1.09 bios upgrade to the shuttle (mentioned in numerous other forum posts), so I already had a wlan0 that behaved appropriately under linux.

What happened for me was:
1) no discovery of network interfaces on install.  It said they weren't installed.

2) However, when I booted the machine after install and did:
```

ifconfig eth0 up
ifconfig wlan0 up

```
Everything was fine.

Of course, 'network-manager' and 'wireless-tools' were not installed, and since I didn't have an ip path to the outside world, I did have to hack around to add a route and daisy-chained the eth0 through a laptop I had nearby so I could install/update the packages.  Once I did that, iwconfig seems to work fine.

---

### Post by GlenTankersley on 2011-04-01
I also had problems getting basic wired ethernet to work with:
- Ubuntu server 10.04 (Lucid)
- Shuttle XS35 Intel Atom D510 1.66GHz

Just like everybody else, the network adapter wasn't found during install.  And after install I wasn't able to connect.  So, I upgraded the bios to version [1.09]("http://ubuntuforums.org/showthread.php?t=1577104&page=1")
And installed the latest version of the [jme driver]("http://ubuntuforums.org/showthread.php?t=1402076")

However, after this, I still couldn't connect until I had changed the network interface file:  /etc/network/interfaces which was automatically set to the loopback - not eth0.  Here is what I changed it to:

```
auto eth0
iface eth0 inet dhcp
```

After that I could connect successfully.  :-)

---

