---
title: "Latest update broke my wireless"
date: 2008-10-16
forum: System76 Support
---

### Post by randizzle on 2008-10-16
Hi System76'ers

I am turning to this forum in the hopes that someone will be able to help me, since I am getting no love in the Network forum.

I am on a System76 Sabel Performance with a Hawking HWUG1 Wireless-G USB which uses the raillink chipset.

The latest updates have broken my wireless. I am able to see my network in the network manager, however I am unable to connect to it. I tried restoring the drivers via the System 76 driver installer, but that did not help.

rshepherd@Gigan:~$ sudo lshw -C network; cat /etc/network/interfaces; iwconfig
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 12
       serial: 00:1f:c6:86:ef:f1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=74.73.69.99 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0e:3b:09:08:27
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
auto lo
iface lo inet loopback

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=19 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any and all help will be greatly appreciated!!
Randy

---

### Post by jdb on 2008-10-17
Any and all help will be greatly appreciated!!
Randy[/QUOTE]

It looks like authorization might not be happening.
Is the Access Point set up for WEP or WPA?
You might be able to clear things out & have it ask you for a password again by running:

sudo dpkg-reconfigure network-manager

jdb

---

### Post by randizzle on 2008-10-17
Thanks I will give this a try. As a workaround I rolled back the kernel version and now things are working again. Does this change your prognosis at all?

Thanks again,
Randy

---

### Post by thomasaaron on 2008-10-18
In what kernel version did you have the problem?

```
uname -r
```

---

### Post by majoridiot on 2008-10-22
FYI- the recent 2.6.24-21-generic kernel update pretty much makes wireless on my serval
useless... it just creeeeeeeeps along.

2.6.24-19-generic works like a champ, so in addition to the new "blinking" feature of the
wireless/bluetooth LED, the -21 kernel update also broke something else.

---

