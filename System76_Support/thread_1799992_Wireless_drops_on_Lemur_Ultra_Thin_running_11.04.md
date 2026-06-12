---
title: "Wireless drops on Lemur Ultra Thin running 11.04"
date: 2011-07-08
forum: System76 Support
---

### Post by albrixa on 2011-07-08
I bought a lemur ultra thin (lemu2) about a month ago, and I have been having persistent networking problems. I have looked at many threads in the ubuntu forums, system76 and otherwise, and have not had any luck. The closest I can find to my situation is this:
[http://ubuntuforums.org/showthread.php?t=1766659&page=2](http://ubuntuforums.org/showthread.php?t=1766659&page=2)
The wireless connection works perfectly on some routers, but drops after a short period on others. Sometimes I can reconnect, sometimes not. The two most common routers I use are both netgear, one works fine the other has this problem. The one that works is a WGR614, the one that doesn't is a WPNT834. First I tried updating the firmware on the router that doesn't work for me, then I changed the security from WEP to WPA (since the one that does work for me was WPA). Both to no effect.  I have had this same problem before on a previous system76 computer (a pangolin value from 4 years ago or so), but an upgrade from 10.04 to 10.10 solved the problem so I forgot about it. Sometimes rebooting the wireless card with Fn+11 gets it working again, sometimes it doesn't. This is not isolated to just one router, I have had the problem other places too. The WPNT834 is just the only one I have the ability to mess with.

Below are all the relevant terminal outputs I can think to include (taken while connected to a problematic router)


```
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  ESSID:"NETGEAR834"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:6C:65:66:9C
          Bit Rate=54 Mb/s
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=100/100  Signal level=-45 dBm  Noise level=-120 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:90:f5:b9:9c:52
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5713 (5.7 KB)  TX bytes:5713 (5.7 KB)

wlan0     Link encap:Ethernet  HWaddr e0:91:53:3d:c5:15
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e291:53ff:fe3d:c515/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5419574 (5.4 MB)  TX bytes:674187 (674.1 KB)
          Interrupt:18 Memory:ffffc900110a0000-ffffc900110a0100


sudo lshw -C network

  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: e0:91:53:3d:c5:15
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet
physical wireless
       configuration: broadcast=yes driver=rtl819xSE
driverversion=0017.0507.2010 firmware=63 latency=0 link=no
multicast=yes wireless=802.11bg
       resources: irq:18 ioport:2000(size=256) memory:f0400000-f0403fff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:04:00.5
       logical name: eth0
       version: 03
       serial: 00:90:f5:b9:9c:52
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list
ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd
autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme
driverversion=1.0.7 duplex=half latency=0 link=no multicast=yes
port=MII speed=10Mbit/s
       resources: irq:43 memory:f0504000-f0507fff
ioport:3400(size=128) ioport:3000(size=256)


more /etc/network/interfaces

auto lo
iface lo inet loopback
auto eth0

```

---

### Post by Dan Hinojosa on 2011-09-06
I too would like this info.  It's getting aggravating, and I just had this laptop for a few hours.

---

### Post by albrixa on 2011-09-06
I resolved my problem by contacting system76 support, I recommend you try that.

---

### Post by G Luv on 2011-09-11
> **albrixa said:**
> I resolved my problem by contacting system76 support, I recommend you try that.

Did it involve them selling you an "upgrade" just to get to minimum performance?

That's what they're suggesting for me. Ridiculous.

---

### Post by johncarl81 on 2011-09-13
I had issues with the default wireless card on the Lemur as well.  Went ahead and upgraded ($25 or so) and I have to say, the upgrade makes it completely stable and incredibly fast.  Recommended.

Did the Lemur just get discontinued?

---

### Post by G Luv on 2011-09-13
> **johncarl81 said:**
> I had issues with the default wireless card on the Lemur as well.  Went ahead and upgraded ($25 or so) and I have to say, the upgrade makes it completely stable and incredibly fast.  Recommended.

Did the Lemur just get discontinued?

Yes, but if I wanted to buy an upgrade just to make it usable, I'd have bought a Windows machine.

Just sayin'.

---

### Post by isantop on 2011-09-15
Actually, you would have the same problem on the Lemur running Windows, or any other Windows machine with that wireless card. The problem lies in how the card is designed to talk to access points, which is a hardware issue. The Intel card (like any other wireless card) has the same issue on other access points, it's just that the number of access points with this problem is much, much lower. 

If you left us an email at support...at...system76...dot...com, then we'd be happy to help you out in getting your card upgraded.

---

