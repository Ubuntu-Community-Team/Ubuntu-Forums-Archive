---
title: "Ubuntu server on x3550 M4"
date: 2015-03-05
forum: Server Platforms
---

### Post by Igor_Dettenborn on 2015-03-05
Hello everyone,

I facing a trouble when I'm trying to install the ubuntu server on a IBM x3550 M4, it doesn't detect my drivers and the network?

What am I missing?

Thanks a lot

---

### Post by nerdtron on 2015-03-06
HHmmm a fairly new server? What version of Ubuntu are you trying to install?

---

### Post by Igor_Dettenborn on 2015-03-06
Yes, fairly new. I'm trying to install this one:

[http://www.ubuntu.com/certification/hardware/201404-14963/](http://www.ubuntu.com/certification/hardware/201404-14963/)

But no success :( network and SAS drivers not detected

---

### Post by nerdtron on 2015-03-06
Download the latest LTS release 14.04.2 from here [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)

It's got an update kernel so it's worth a try. If your hardware is still not detected, I'm not sure on what to do next. Probably try the latest CentOS 7 stable build.


As for not detecting your SAS drives, are you sure you have already configured and initialized you RAID controller/setup? It could be that your drives are just sitting there, because you haven't configured the RAID controller yet.

---

### Post by Igor_Dettenborn on 2015-03-06
The IBM bios start the RAID controler, the green lights blink and everything, same with the network controller. But it don't detect, I'll test this build.

Thanks a lot

---

### Post by MAFoElffen on 2015-03-07
> **Igor_Dettenborn said:**
> Hello everyone,

I facing a trouble when I'm trying to install the ubuntu server on a IBM x3550 M4, it doesn't detect my drivers and the network?

What am I missing?

Thanks a lot
I have an IBM XSeries server here running Ubuntu Server 14.04.2 LTS. What is it doing, not doing  and not seeing? You know you can pop out of the Ubiquity installer environment into a shell via <cntrl><Shift><F2> to query how linus see the machine right?

If I'm having install problems on a server, many times, I'll have a LiveCD around to boot into a LiveImage to use for diagnostics. I like to see what Linux sees things as. Also, I've done over 4000 installs on various iron, so I also know that IBM iron is usually an easy install, but has a few quarks. One quark is the IBM ServRaid controllers. IBM and HP hard RAID doesn't boot to the RAID setup from BIOS like LSI does. Their RAID Setup is from a bootable Live image... So to keep those accessable, I setup a small jbod partition where I copy the ISO for those to, and setup booting to those to the grub boot menu. Will save you in a pinch.

Next- IBM Iron is REAL picky about option slot cards that are not from IBM. That bit me in the behind. I spent too much time trying to trace down an NMI fault that was from a fiber channel card that was causing a conflict. That same card worked great on another branded server, but that server chocked on it. Another fiber channel card and it was fine.

So maybe if you can explain what is going on, maybe I can help you with some ideas?

---

### Post by Igor_Dettenborn on 2015-03-18
I'm new to this server things, sorry, I didn't configure the RAID system as it should. After I configured the RAID everything went well in the instalation.


But now I'm facing issues with my ethernet card, I configured them 4 as Configured and with DHCP enabled, it were the two options on the BIOS setup of the network.


Even with the card recognized by the system (eth0, eth1, eth2 and eth3) it didn't work, the leds on the ethernet card blink in a slow rate, and the light on the switch stays on, I doesn't blink as it should.


What can be happening?

---

### Post by nerdtron on 2015-03-18
Then start troubleshooting. like ping, traceroute, or try to transfer file between network and see the speeds.

What is the contents of the /etc/network/interfaces file?
```
cat /etc/network/interfaces
ifconfig -a
ethtool ethX
```
replace ethX with eth0, eth1 etc..

Also are you sure the cards are labeled eth0, eth1 etc?? I think on the newer Ubuntu they will be named em1, em2 or p0p1, p0p2 etc.

---

### Post by Igor_Dettenborn on 2015-03-18
I already tried to ping, networki is unreachable :(

In the file interfaces it says:

    ```
auto lo eth0 eth1 eth2 eth3

    iface lo inet loopback

    iface eth0 inet dhcp

    iface eth1 inet dhcp

    iface eth2 inet dhcp

    iface eth3 inet dhcp
```

And the ifconfig -a show all the data of the cards, wolud you want to know them?

---

### Post by nerdtron on 2015-03-18
> And the ifconfig -a show all the data of the cards, wolud you want to know them?

I want to know if the server already did got an IP address and to confirm they really are named eth0 to eth3. 

What IP did you tried to ping?

Basic IP troubleshooting using ping:
You should ping first the local assigned IP address of the server,
 if successful then default gateway of the network, 
if successful  then ping public IP like 8.8.8.8 and
if successful then public URL like [www.google.com]("http://www.google.com").

As for the /etc/network/interfaces file, did you edit that manually or is it automatically generated?
I think it should be like:
```

auto lo 

    iface lo inet loopback

auto eth0
    iface eth0 inet dhcp

auto eth1
    iface eth1 inet dhcp

auto eth2
    iface eth2 inet dhcp

auto eth3
    iface eth3 inet dhcp

```


And you did not post the output of the ethtool commands?

Also if you run "dmesg | grep -i link" you should see if your network card are detected.
```
kenneth@nerdtron:~$ dmesg  | grep -i link
[    0.468907] audit: initializing netlink socket (disabled)
[    1.056175] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   11.202783] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.613053] [COLOR=#ff0000]**e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX**[/COLOR]
```

---

### Post by Igor_Dettenborn on 2015-03-19
Hello, this file is automatic generated, but I have another server that is running with this same structure, I think that's not the problem .

Speaking of ping, I cant even reach my local network, it always return host unreachable

```

eth0      Link encap:Ethernet  HWaddr 40:f2:e9:f3:1e:12  
          inet addr:"external"  Bcast:"external bcast"  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3337719 (3.3 MB)  TX bytes:1355808 (1.3 MB)
          Memory:90580000-905a0000 


eth1      Link encap:Ethernet  HWaddr 40:f2:e9:f3:1e:13  
          inet addr:192.168.0.254  Bcast:192.168.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:204407 (204.4 KB)  TX bytes:130644 (130.6 KB)
          Memory:905a0000-905c0000 


eth2      Link encap:Ethernet  HWaddr 40:f2:e9:f3:1e:14  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:905c0000-905e0000 


eth3      Link encap:Ethernet  HWaddr 40:f2:e9:f3:1e:15  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:905e0000-90600000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:129642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30658789 (30.6 MB)  TX bytes:30658789 (30.6 MB)


usb0      Link encap:Ethernet  HWaddr 42:f2:e9:f3:1e:11  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

ethtool etho:

```

Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: yes

```

---

### Post by Igor_Dettenborn on 2015-03-23
Do you need some more information, I use -S in the ethtool and it returned me the bytes used ...

:(

---

### Post by Igor_Dettenborn on 2015-03-24
Nothing?  :/

---

### Post by nerdtron on 2015-03-25
Sadly no more idea. I don't like to give up so have you tried other distributions? like CentOS 7?

---

