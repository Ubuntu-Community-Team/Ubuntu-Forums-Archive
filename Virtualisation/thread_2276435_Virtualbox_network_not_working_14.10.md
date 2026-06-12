---
title: "Virtualbox network not working 14.10"
date: 2015-05-02
forum: Virtualisation
---

### Post by pkoukoulis-r on 2015-05-02
Hi

I have installed 64bit Oracle Linux 6.6 in a VirtualBox running on 64-bit Ubuntu 14.10. VirtualBox 4.3.18
Had no issues with the installation. Guest Additions loaded fine too.

I cannot however get the network in VirtualBox to work.

I have tried both the bridged adaptor and NAT options, but both have not worked.  
I tried rebootng with Name "wlan0" and "eth0" and have set the "Promiscuous mode" to ALL, but each time no network available.

The ifconfig outputs in ubuntu and the Virtualbox are as follows:

**Ubuntu laptop ifconfig output:**


[FONT=courier new]eth0      Link encap:Ethernet  HWaddr 80:fa:5b:03:51:02  [/FONT]
[FONT=courier new]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=courier new]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]lo        Link encap:Local Loopback  [/FONT]
[FONT=courier new]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
[FONT=courier new]          inet6 addr: ::1/128 Scope:Host[/FONT]
[FONT=courier new]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT]
[FONT=courier new]          RX packets:943 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:943 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:0 [/FONT]
[FONT=courier new]          RX bytes:88280 (88.2 KB)  TX bytes:88280 (88.2 KB)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]wlan0     Link encap:Ethernet  HWaddr f8:16:54:1f:d2:86  [/FONT]
[FONT=courier new]          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0[/FONT]
[FONT=courier new]          inet6 addr: fe80::fa16:54ff:fe1f:d286/64 Scope:Link[/FONT]
[FONT=courier new]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:29136 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:8530 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=courier new]          RX bytes:37458097 (37.4 MB)  TX bytes:1432794 (1.4 MB)[/FONT]


**VirtualBox ifconfig output**


[FONT=courier new]eth2      Link encap:Ethernet  HWaddr 08:00:27:1A:AF:21  [/FONT]
[FONT=courier new]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=courier new]          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]lo        Link encap:Local Loopback  [/FONT]
[FONT=courier new]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
[FONT=courier new]          inet6 addr: ::1/128 Scope:Host[/FONT]
[FONT=courier new]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT]
[FONT=courier new]          RX packets:60 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:0 [/FONT]
[FONT=courier new]          RX bytes:4140 (4.0 KiB)  TX bytes:4140 (4.0 KiB)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]virbr0    Link encap:Ethernet  HWaddr 52:54:00:5E:66:4C  [/FONT]
[FONT=courier new]          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0[/FONT]
[FONT=courier new]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:0 [/FONT]
[FONT=courier new]          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/FONT]


Can anybody suggest how to get the network inside the Virtualbox working?

Peter

---

### Post by pkoukoulis-r on 2015-05-15
Got it working eventually

[COLOR=#5C5C5C][FONT=Ubuntu]I set the Network settings to the following: [/FONT][/COLOR]
[COLOR=#5C5C5C][FONT=Ubuntu]Attached to: Bridged Adapter [/FONT][/COLOR]
[COLOR=#5C5C5C][FONT=Ubuntu]Name: wlan0 [/FONT][/COLOR]
[COLOR=#5C5C5C][FONT=Ubuntu]Promiscuous Mode: All [/FONT][/COLOR]
[COLOR=#5C5C5C][FONT=Ubuntu]Cable Connected: Checked [/FONT][/COLOR]

[COLOR=#5C5C5C][FONT=Ubuntu]The above combination seems to have fixed the networking issue. 


[/FONT][/COLOR]

---

### Post by sudodus on 2015-05-15
Congratulations :KS

Too bad, that there was no help from our forum in your thread, but very good that you came back and shared your solution. In order to help other users at the Ubuntu Forums, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

