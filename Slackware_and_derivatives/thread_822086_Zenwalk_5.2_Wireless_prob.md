---
title: "Zenwalk 5.2 Wireless prob"
date: 2008-06-07
forum: Slackware and derivatives
---

### Post by Novega on 2008-06-07
Can anyone give me a little insight on how to get my wireless working? I'm using a broadcom card and I just did the whole "fw-cutter" install thing... I restarted and still nothing.

I did ```
lshw -C network
```
got

```
root[~]# lshw -C network
  *-network:0             
       description: Network controller
       product: BCM43xG 802.11b/g
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:11:2f:04:d1:d2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.160 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0d:3a:29:33:35
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
root[~]# 


```

So it looks like I have a module disabled, the question is how do I fix it?
Please try to explain as clear as possible, I've only been using linux for a month and this is my first real trip outside the safety of Ubuntu :p

---

### Post by Antman on 2008-06-08
I just installed Zenwalk 5.2 on my old Compaq n400c subnotebook. It has a Motorola Wifi PCMCIA card which is BCM43x based I believe. The only thing I had to do in order to get it to work was:
1. make sure the Broadcom BCM43 module was turned on in Zenpanel>Kernel Modules.
2. Install the windows drivers using the "Ndiswrapper Wireless Driver" applet under>System.
3.Rebooted and launched WICD and joined my wifi network.

---

### Post by Novega on 2008-06-08
hmmm...I'll give that a whirl then. I thought about using ndiswrapper but I figured the bcm native was the way to go.

I'll try that

---

### Post by Novega on 2008-06-08
Thanks for the advice Antman
But no luck with ndiswrapper, I loaded the driver but it said "no hardware found" in the box on the left side in the "Ndiswrapper applet".

](*,)

---

### Post by Antman on 2008-06-08
> **Novega said:**
> Thanks for the advice Antman
But no luck with ndiswrapper, I loaded the driver but it said "no hardware found" in the box on the left side in the "Ndiswrapper applet".

](*,)
which .inf file did you use? I can't recall the exact name but my driver cd had two .inf files for my wifi chipset. The one that worked was the one that had letter 'a' just before the ".inf" extension. So if you have two files: bcm43.inf (can't recall the exact names) and bcm43**a**.inf, the bcm43**a**.inf was the one that worked. Oh, make sure the bcm43xx kernel module is loaded (System>Zenpanel>Kernel Modules).

You may want to drop a line on the zenwalk forums also, they may have some more ideas for you to try.

---

### Post by carltonh on 2008-08-04
Not sure I can help much, but I have got Zenwalk to work with my laptop with a Broadcom bcm4318 device, which must be a bit different.

Note, which kernel you are using.  There is one method for under 2.6.24, one for 2.6.24, and one for after 2.6.24 at [www.linuxwireles.org](www.linuxwireles.org).  b43, ssb, and bcm43xx are internal kernel drivers.  If you can't get them to work, then try blacklisting them and only then try Ndiswrapper, which uses the Windows driver.

If you have both Ndiswrapper and, say b43 kernel modules running at the same time, then one may work, or none may work even though one of them would work if both weren't loaded.

I had to play with it enough that I couldn't give specific directions, because I'm not sure what part made mine work.

I will note that Ubuntu works automatically with a laptop with bcm4310 wireless, though it promts a warning about using a non-free wl module, and Sabayon worked automatically with bcm 4318 wireless, and they were respectively the only distro's that didn't require work to get wireless working in those cases respectively.

---

