---
title: "Pangolin P5 - Network issues with clean install of Karmic"
date: 2010-03-06
forum: System76 Support
---

### Post by iwc5893 on 2010-03-06
I've spend the past couple of hours searching for this but haven't had much luck.

I performed a clean install of 9.10 64bit because I wanted to change the way the partitions were done, but now I am having some issues.  

I booted up with the 9.10 LiveCD, and created the partition table that I wanted and continued with the install.  Once the install was done, there were two issues that were of immediate concern.  Both the ethernet and wireless interfaces were not detected.

I was able to get the ethernet interface working by connecting to the internet with a USB-ethernet adapter so I was able to download system updates and the System76 Restore application.  I also had to install WICD because even after the restore, the ethernet and wireless interfaces were not showing up.

WICD recognized the ethernet card after the system restore, but I am unable to get the wireless working.  When I run lspci | grep Wireless I get nothing back, but ifconfig shows the wlan0 interface along with a wmaster0-00 interface as shown below
> wlan0     Link encap:Ethernet  HWaddr 00:23:14:56:ca:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-14-56-CA-00-00-00-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Cat /etc/network/interfaces returns
> auto lo
iface lo inet loopback


Any help would be appreciated.

---

### Post by iwc5893 on 2010-03-06
Here is the output of lshw -C network along with the results of rfkill list:

> $ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

$ lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:14:56:ca:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:34 memory:f0300000-f0301fff


---

### Post by iwc5893 on 2010-03-06
Got it figured out...kinda.

I ended up going the ndiswrapper route, and downloaded the Windows Vista 64bit driver for the Intel WiLink 5100 card.

I would still like to find the actual linux driver for this card, if possible, so I'm going to hold off on marking this solved until Thomas has a chance to respond.

---

### Post by patchwork on 2010-03-06
iwlagn, iwlcore, and mac80211 are the modules used by the Intel 5100 on my p6...

[http://wiki.debian.org/iwlagn](http://wiki.debian.org/iwlagn)[http://wiki.debian.org/iwlagn](http://wiki.debian.org/iwlagn)

(from lspci -v)

02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
    Subsystem: Intel Corporation Device 1201
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at f4100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

---

### Post by thomasaaron on 2010-03-08
patchwork, are you the one who emailed me with these problems on a PanP7? I ask because this subject line says panp5, and the panp5 and panp7 are very different animals in this regard.

With 9.10 64-bit Ubuntu, wired and wireless will work out of the box. Here are restore instructions...

> You can download a CD image for Ubuntu here...
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
...I recommend using 9.10 64-bit.

Once you've downloaded the CD image, you will need to burn it to a CD. However, it must be burned as an *image* and not as a *data * CD. Otherwise, it will not be bootable. Instructions for this vary based on which operating system you are using to burn the CD. Instructions for various operating systems are here.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Here are instructions for re-imaging your machine...
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)
...including instructions for downloading, installing and running your System76 driver.


If you have a panp7, we need to move this one to email.

---

### Post by patchwork on 2010-03-08
Thomas--  It wasn't me with the p7.  
(I have a p6, and no issues)  Was just posting to show the driver being used for this:
```
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
``` 

Sorry for the confusion.

---

### Post by iwc5893 on 2010-03-08
Sorry, this is supposed to be a P7 and not the P5.

Thomas, the person that submitted the order is sending the email right now.

---

