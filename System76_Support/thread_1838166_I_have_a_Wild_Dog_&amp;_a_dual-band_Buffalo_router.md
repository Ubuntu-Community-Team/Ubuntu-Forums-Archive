---
title: "I have a Wild Dog &amp; a dual-band Buffalo router: which wifi PCI card to get?"
date: 2011-09-03
forum: System76 Support
---

### Post by watchpocket on 2011-09-03
I bought a Wild Dog desktop computer from System 76 about Thanksgiving of '09 and have never gotten around to upgrading the G-standard wifi PCI card that came with it.  (it's a  D-Link WDA-1320.)

I'm wondering which wifi PCI adapter would work best with my (64-bit) Wild Dog and with a brand new** dual-band** **Buffalo WZR-HP-AG300H   router** that I just got (which btw comes with DD-WRT installed out-of-the-box).  (You can see the Buffalo here: [http://amzn.to/oYLE18](http://amzn.to/oYLE18) ).

I'm currently considering the **D-Link DWA-556** "Xtreme N PCI Express Desktop Adapter" . . . 

(as seen here: [http://bit.ly/oa7lJg](http://bit.ly/oa7lJg) -- and it has to be a total mistake, and very weird, that the description on this B&H page says that the adapter is "from Buffalo") 

. . . but I have a couple of concerns about it: 

 ([COLOR=Blue]a[/COLOR]) its wireless frequency range uses the 2.4 GHz band only, while my router uses the 2.4 and 5 GHz bands.  Does this matter, and is it even possible to get a PCI NIC card that will operate in both frequency ranges the way the router does? 

([COLOR=Blue]b[/COLOR]) apparently the DWA-556 card has its own matching router with which it is supposedly to be paired for best performance.  For example in the card's sales blurbs, it says **"***[COLOR=Black]Delivers [/COLOR][COLOR=Black]up to 14x faster                              speeds and [/COLOR][COLOR=Black]6x farther                              range[/COLOR] than 802.11g**"  Note the asterisk, which, when followed, says "[SIZE=1]**** When used with the DIR-655 Xtreme N                          Router.***"

If I buy a new wifi card I'd like it to perform optimally [I][COLOR=Red]with **my** **own** router[/COLOR].

[/I]My only other concern is how easy or difficult the installation of the driver(s) will be on Ubuntu, since these things typically come with setup wizards designed for Windows.

Any specific card recommendations, or other general thoughts about potential interoperability issues between the card, the router and my computer are welcome. (I'm running Karmic -- I know, I know.)


[/SIZE]

---

### Post by watchpocket on 2011-09-03
I did see the following at
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI)

which is encouraging:

**[B]Model**                                            [/B]DWA-556
    **[B]Chipset**[/B]                                                    Atheros AR5008E
    **[B] Driver**[/B]   Madwifi
    **[B]Supports network install?**[/B]    ?
    **[B]Supported in installed system?**[/B] Yes
    **[B]Works "out of the box"**[/B]                         Yes
    **[B]Comments**[/B]                             Works out of the box in Karmic
    **[B]Last Updated**[/B]                                    2010-03-20

(Though it'd still be great to hear from any of the System76 guys (or anyone else, thanks).

Some more info about my setup:

```

--> sudo lshw -C network             
  *-network               
       description: Ethernet interface
       product: 82567LF-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 00
       serial: 00:27:0e:01:b2:89
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.8-5 ip=67.84.245.21 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:26 memory:e3200000-e321ffff memory:e3224000-e3224fff ioport:f100(size=32)
  *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wmaster0
       version: 01
       serial: 00:24:01:11:e5:e1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:e3100000-e310ffff

--> ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:27:0e:01:b2:89  
          inet addr:67.84.245.21  Bcast:67.84.247.255  Mask:255.255.252.0
          inet6 addr: fe80::227:eff:fe01:b289/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:277395 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:178066171 (178.0 MB)  TX bytes:13324118 (13.3 MB)
          Memory:e3200000-e3220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:01:11:e5:e1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-01-11-E5-E1-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

--> iwconfig   
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by watchpocket on 2011-09-09
Anyone?

---

