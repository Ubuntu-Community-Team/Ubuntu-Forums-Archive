---
title: "Xubuntu (14-16) and QCA6174 wifi problem (wireless-info output attached)"
date: 2015-11-06
forum: Ubuntu Development Version
---

### Post by Stepan_Wot on 2015-11-06
Hi,
I've installed Xubuntu on Dell Alienware and all but one devices are working, even the Ethernet works out of the box. (Great job, developers!). However wifi performance is erratic. Most of the time it has wifi enabled checked in and connect wifi grayed out. At best I was able to connect to iphone hot-spot, but had no luck connecting to Motorola wireless. Other devices can connect to Motorola router without a problem. 

I tried DIY methods. I've followed instructions from related threads. Each time I had to reinstall OS. I've tried Xu14.04 and Xu15.10. Now I am on Xu16. I havent change anything on this os yet (just ran the information gathering script). Please follow the link to see the output.

[http://paste.ubuntu.com/13128177/](http://paste.ubuntu.com/13128177/)

I have "internet firewall, level:low", "drop broken packets" and "detect port scanning enabled" on my router.

Please guide me through this fix. 

Thank you in advance,
Stepan

---

### Post by matt_symes on 2015-11-06
16.04 is the development version. In that version, things will be in a state of flux.

Are you really trying to get help with 16.04 ? If you are then this thread does not belong here but belongs in the Ubuntu Development subforum.

You may not get much help though as most of the people in that subforum are testers who will not help trouble shoot problems but are looking for them to pass along to the developers via Launchpad.

Thread moved to Ubuntu Development subforum.

---

### Post by grahammechanical on 2015-11-06
It too early in the Xenia development cycle for there to be much difference between 15.10 and 16.04. Besides, if this problem was present in 14.04 & 15.10 it is not specific to xenial xerus in my opinion.

As far as I can tell the WiFi adapter does have a driver. 

> 03:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 20)
    Subsystem: Bigfoot Networks, Inc. Killer N1525 Wireless-AC [1a56:1525]
    Kernel driver in use: ath10k_pci

But the wireless adapter is not connected to the router.

> wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2634670 (2.6 MB)  TX bytes:815977 (815.9 KB)

You need to see UP BROADCAST RUNNING MULTICAST. Did you run the wireless info report whilst connect by ethernet and not by WiFi?

May I make a suggestion? Do not disable Networking but disconnect the wired connection. I am in the habit of being connected to the router by both ethernet and WiFi but I found that during the 15.04 development cycle I could not get a connection if Ubuntu was connected by both ethernet & WiFi. One or the other but not both. This issue disappeared during the 15.10 development cycle but then re-appeared again. As far as I could tell there was nothing wrong with the settings in network manager or with the router.

Oh, by the way. This is as it should be

> : dell-rbtn: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Do you have two WiFi adapters? Hard blocked: yes = WiFi adapter switched off in hardware. Soft blocked: yes = wiFi adapter switched off by software. 

Regards.

---

### Post by QDR06VV9 on 2015-11-07
Just one more quick note, Try disabling the IPV6

```
[COLOR=#000000][ipv6] method=auto[/COLOR]
[[/etc/NetworkManager/system-connections/Yuxi's iPhone]] (600 root)
[connection] id=Yuxi's iPhone | type=wifi | permissions=user:stepan:;
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=Yuxi's iPhone
[ipv4] method=auto [COLOR=#000000][ipv6] method=auto[/COLOR]
```

```
[ 3428.836175] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready[ 3430.371960] [COLOR=#ff0000]**ath10k_pci 0000:03:00.0: firmware crashed! **[/COLOR](uuid e4b0b8b3-87f4-400b-84b9-6a84ca76dc46)


[ 3480.002788]** [COLOR=#ff0000]IPv6: ADDRCONF(NETDEV_UP): wlp3s0[/COLOR]**: link is not ready
[ 3480.011345] ath10k_pci 0000:03:00.0: failed to start hw scan: -108 (repeated 7 times)
```

---

