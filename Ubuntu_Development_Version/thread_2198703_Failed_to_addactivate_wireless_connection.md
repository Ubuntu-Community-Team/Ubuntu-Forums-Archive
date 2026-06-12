---
title: "Failed to add/activate wireless connection"
date: 2014-01-10
forum: Ubuntu Development Version
---

### Post by Bucky Ball on 2014-01-10
As per the title. When I left-click on the network icon (network-manager) and select my network, I get a window with the message 'Failed to add/activate connection' and on the next line: '(32) Insufficient privileges'. The top entry 'Ethernet Network' is greyed out even though the cable is connecting fine (but as 'ifupdown (eth0)').

When I right click on the network icon, all the options but 'Connection Information' are greyed out. Can't select.

I did fool with /etc/network/interfaces so here it is:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

... and also 'sudo lshw -C network':

```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:4a:00:12
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.190 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff memory:d0020000-d003ffff
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: b4:82:fe:3c:ad:72
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.13.0-1-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:d4000000-d4003fff
```

** Hold on. I just noticed this:

```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```

I changed the middle line to 'auto wlan0' to match the file in one of my working installs ... ? I'll change again, reboot and check.

*** Well, I tried changing that and it tries wireless first now and lets me know I can use it, a step forward, but when I click my network, I get the same error. I notice also that although I'm not connected, the signal strength seems to range from one bar to all four. So 25% to 100? 

PS: I would post a pic of this error screen but for the odd fact that I don't have any option in the menus to 'Go Advanced' or anything else. All formatting I must do manually. I don't have openjdk installed. Perhaps that's involved with it.

---

### Post by grahammechanical on 2014-01-10
As far as I know the interfaces file should only have

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

It has just that on the Xubuntu 13.10 that I am posting this from and also in Ubuntu Trusty Tahr. If anything else is added to the interfaces file then Network Manager does not work. I think that Network Manager does not use the interfaces file.

Regards.

---

### Post by steeldriver on 2014-01-10
NetworkManager by default considers interfaces that are defined in /etc/network/interfaces to belong to the 'networking' service and ignores (does not manage) them. This behaviour is controlled by the 

```

[ifupdown]
managed=false

```

parameter in /etc/NetworkManager/NetworkManager.conf - in principle you *could* change that to 'true' but in practice it's better to stick to using EITHER the GUI NetworkManager OR the non-GUI networking service

---

### Post by Bucky Ball on 2014-01-10
Tnx for the input:

> **steeldriver said:**
> 
```

[ifupdown]
managed=false

```

Strangely enough I did change that to true earlier. I just changed it back and no diff. The file now looks like this:

```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```

I also altered the /etc/network/interfaces file to include only the line advised in post #2.

---

### Post by Bucky Ball on 2014-01-11
Problem. I have no network at all now. The Network Manager icon is still there, but click it and it has 'Network connectios' as the only entry and that's greyed out. 

I will continue to tweak.

* Update: cable connection is up again. I changed /etc/network/interfaces to this as previously advised:

```
 This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

Strange that I changed it to that when the cable was up and didn't make any difference, changed it back to original and still online. Anyway, wireless still giving original error message, though.

PS: Also, remembering that I am using a 14.04 minimal install with xfce4, I go to Apps>Settings>Network connections and click add, it asks what kind of connection I want to add, I choose wireless, pops up with the window to let me input all the data but all tabs are greyed out. I can't access anything or put any details of the wireless in. I use static IPs and am wanting to set wireless up that way, but at the moment I would just like to get it up any way! ;) 

TIA in advance ...

(Again, I can't post any screenshots because the forum is not showing me the options or any icons in posts, 'Quick Reply' or 'Adv'. That is another issue for another thread. I have just installed openjdk-7 thinking that might be the issue, but not. :-K

---

### Post by Bucky Ball on 2014-01-11
NoScript was blocking the forum editing icons. All fixed now. Find attached the message I get when I try to select my, or any, wireless network.

---

### Post by Bucky Ball on 2014-01-11
Must have been directly related to the problems with login and display managers here:

[http://ubuntuforums.org/showthread.php?t=2198698](http://ubuntuforums.org/showthread.php?t=2198698)

I installed gdm and all problems went away. Thanks for the input. For the present, 14.04 LTS is officially up and running on my laptop! ;)

PS: The network signal strength is still radically swinging from 30% to 84 (and I'm sitting about two metres away), but that is the stuff of another thread. Tnx again.

---

