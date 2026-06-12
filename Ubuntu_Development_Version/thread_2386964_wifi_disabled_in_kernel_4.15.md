---
title: "wifi disabled in kernel 4.15"
date: 2018-03-12
forum: Ubuntu Development Version
---

### Post by monkeybrain20122 on 2018-03-12
Wifi stops working after kernel upgraded to 4.15

```
$uname -r
4.15.0-10-generic
$sudo lshw -C network
[sudo] password for monkeybrain: 
  *-network DISABLED        
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0b1
       version: 01
       serial: 68:a3:c4:2f:07:b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=4.15.0-10-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f5500000-f5503fff

```

But it works if boot into kernel 4.13
```
$ uname -r
4.13.0-25-generic
$ sudo lshw -C network
[sudo] password for monkeybrain: 
  *-network                 
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0b1
       version: 01
       serial: 68:a3:c4:2f:07:b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=4.13.0-25-generic firmware=610.812 ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f5500000-f5503fff

```

Seems that some firmware is missing.

---

### Post by kerry_s on 2018-03-13
firmware=N/A on 4.15

have you tried enabling it in hardware drivers?

---

### Post by monkeybrain20122 on 2018-03-13
> **kerry_s said:**
> firmware=N/A on 4.15

have you tried enabling it in hardware drivers?

There is nothing to enable, this card always works out of the box, until 4.15.

---

### Post by kerry_s on 2018-03-13
i thought there was like a broadcom-wl, proprietary drivers also available besides the 1 in kernel.

sorry, its been years last dealing with broadcom wifi. it was always a issue on my older laptop that died a few years ago.

---

### Post by monkeybrain20122 on 2018-03-13
> **kerry_s said:**
> i thought there was like a broadcom-wl, proprietary drivers also available besides the 1 in kernel.

sorry, its been years last dealing with broadcom wifi. it was always a issue on my older laptop that died a few years ago.

yeah some broadcom cards require downloading a kernel module but not this one. It works out of the box in 4.13, from which I made the post above, I didn't install anything.

---

### Post by mc4man on 2018-03-13
maybe
[https://bbs.archlinux.org/viewtopic.php?id=234122](https://bbs.archlinux.org/viewtopic.php?id=234122)

---

### Post by jeremy31 on 2018-03-13
I think it might be something else, see the wireless script link in my signature and post results

---

### Post by Cavsfan on 2018-03-13
Would your network card use this driver?
```
[cavsfan@Le-Beast ~]$ inxi -Fnn
...
Network:   Card: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller driver: _r8169_
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 00:24:21:51:21:3a

```

---

### Post by monkeybrain20122 on 2018-03-14
> **mc4man said:**
> maybe
[https://bbs.archlinux.org/viewtopic.php?id=234122](https://bbs.archlinux.org/viewtopic.php?id=234122)

You are right!

Following your link, I found the patched kernel source [here]("https://git.kernel.org/pub/scm/linux/kernel/git/kvalo/wireless-drivers.git/commit/?id=a9e6d44ddeccd3522670e641f1ed9b068e746ff7") , I compiled and installed it and wifi works.
It is rc9 since they could not merge it to the released branch on time.
```
$ uname -r
4.15.0-rc9-custom
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network                
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0b1
       version: 01
       serial: 68:a3:c4:2f:07:b0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=4.15.0-rc9-custom [COLOR=#0000ff]firmware=610.812[/COLOR] ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f5500000-f5503fff
```

To test a bit more I tested kernel 4.16.0-041600rc2 from mainline kernel ppa, wifi card not detected. But it works in 4.16.0-rc4 from the  branch above (again compiled from source)

```

$uname -r
4.16.0-rc4-custom
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network                 
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0b1
       version: 01
       serial: 68:a3:c4:2f:07:b0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=4.16.0-rc4-custom [COLOR=#0000ff]firmware=610.812[/COLOR] ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f5500000-f5503fff

```

Thanks everyone for helping.

---

### Post by mc4man on 2018-03-14
ot. - one thing i've noticed on 18.04 is it compiles significantly faster than previous ubuntu, typically 5-6x faster. 
For ex. on same laptop ffmpeg takes 10 -12 min. before while on 18.04 a bit more than  2  min.

---

### Post by monkeybrain20122 on 2018-03-14
> **mc4man said:**
> ot. - one thing i've noticed on 18.04 is it compiles significantly faster than previous ubuntu, typically 5-6x faster. 
For ex. on same laptop ffmpeg takes 10 -12 min. before while on 18.04 a bit more than  2  min.

I don't know, this is an old machine I use for testing, the only things I have compiled on it are these kernels and it took hours, guess that is normal for kernels. Desktop is snappy and smooth, boot up is very fast and so far nothing else other than kernel 4.15 seems to have broken, but this is ventricle's unity remix iso. ;) If I have the time may set up GS on another partition ..

---

### Post by erigeron on 2018-06-24
Hello,

I'm facing a similar issue, probably also related to the missing firmware info in the network configuration.
My wifi connection works normally until it gets cut off randomly after few minutes.
I have to run a `sudo service network-manager restart` all the time and the connection starts working again for some more minutes.

This is the output of `sudo lshw -C network`:

```
  *-network                 
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 01
       serial: 40:e2:30:cb:ab:a3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.15.0-23-generic firmware=N/A ip=192.168.1.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:f7900000-f797ffff memory:f7980000-f798ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:05:00.1
       logical name: enp5s0f1
       version: 12
       serial: 78:24:af:ca:a5:34
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:33 ioport:d000(size=256) memory:f7814000-f7814fff memory:f7810000-f7813fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: docker0
       serial: 02:42:ad:11:8d:68
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.17.0.1 link=no multicast=yes
```

Can someone please explain me exactly what to do?
I'm on Ubuntu 18 LTS.
Thanks.

---

### Post by cariboo on 2018-06-24
Thread closed. Bionic has been released. @erigeron  please ask you question [here]("https://ubuntuforums.org/forumdisplay.php?f=336").

---

