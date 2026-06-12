---
title: "Ubuntu 16.04 Ethernet Help"
date: 2016-05-06
forum: Server Platforms
---

### Post by Swedz on 2016-05-06
[COLOR=#111111][FONT=Ubuntu]So, I have recently installed Ubuntu 16.04 (Server). I have Ethernet plugged in to the PC that Ubuntu is installed on, but it doesn't let me ping stuff or install packages.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][B]ifconfig -a:
[/B][/FONT][/COLOR]
```
enp8s0   Link encap:Ethernet  HWaddr **:**:**:**:**:**
         inet addr:192.168.1.7  Bcast:192.168.1.255 Mask:255.255.255.0
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:19

lo       Link encap: Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:65536  Metric:1
         RX packets:196 errors:0 dropped:0 overruns:0 frame:0
         TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1
         RX bytes:15016 (15.0 KB)  TX bytes:15016 (15.0 KB)
```
[COLOR=#111111][FONT=Ubuntu]**as for when I ping 198.199.80.11:**[/FONT][/COLOR]
```
PING 198.199.80.11 (198.199.80.11) 56(84) bytes of data.
From 192.168.1.7 icmp_seq=1 Destination Host Unreachable
```
[COLOR=#111111][FONT=Ubuntu]**the /etc/network/interfaces:**[/FONT][/COLOR]
```
source /etc/network/interfaces.d/*

auto lo enp8s0
iface lo inet loopback

auto enp8s0
iface enp8s0 inet static
address 192.168.1.7
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```
[COLOR=#111111][FONT=Ubuntu]**route -n:**[/FONT][/COLOR]
```
Kernel IP routing table
Destination     Gateway       Genmask             Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1   0.0.0.0             UG    0      0        0 enp8s0
192.168.1.0     0.0.0.0       255.255.255.0       U     0      0        0 enp8s0
```
[COLOR=#111111][FONT=Ubuntu]**ip route show:**[/FONT][/COLOR]
```
default via 192.168.1.1 dev enp8s0 onlink linkdown
192.168.1.0/24 dev enp8s0  proto kernel  scope link  src 192.168.1.7 linkdown
```
[COLOR=#111111][FONT=Ubuntu]**networking.service:**[/FONT][/COLOR]
```
networking.service - Raise network interfaces
Active: active (exited) since Mon 2016-05-02 21:00:58 EDT; 10min ago
```
[COLOR=#111111][FONT=Ubuntu](if you need any more of the networking.service just comment saying so)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**ethtool enp8s0:**[/FONT][/COLOR]
```
Supported ports: [ TP ]
Supported link modes:   10baseT/Half 10baseT/Full
                        100baseT/Half 100baseT/Full
                        100baseT/Half 100baseT/Full
Supported pause frame use: No
Supports auto-negotiation: Yes
Advertised link modes:  10baseT/Half 10baseT/Full
                        100baseT/Half 100baseT/Full
                        1000baseT/Half 1000baseT/Full
Advertised pause frame use: Symmetric
Advertised auto-negotiation: Yes
Speed: Unknown!
Duplex: Unknown! (255)
Port: Twisted Pair
PHYAD: 1
Transceiver: internal
Auto-negotiation: on
MDI-X: Unknown
Supports Wake-on: g
Wake-on: g
Current message level: 0x000000ff (255)
                       drv probe link timer ifdown ifup rx_err tx_err
Link detected: no
```
[COLOR=#111111][FONT=Ubuntu]**ethtool -i enp8s0:**[/FONT][/COLOR]
```
driver: tg3
version: 3.137
firmware-version: sb
expansion-rom-version:
bus-info: 0000:08:00.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: no
supports-register-dump: yes
supports-priv-flags: no
```
[COLOR=#111111][FONT=Ubuntu]**ip neigh show:**[/FONT][/COLOR]
```
192.168.1.1 dev enp8s0  INCOMPLETE
```
[COLOR=#111111][FONT=Ubuntu]Please be detailed with your answers, thank you in advance! :D[/FONT][/COLOR]

---

### Post by darkod on 2016-05-06
In your /etc/network/interfaces you don't need to use the broadcast and network parameters. They are calculated automatically from the netmask. But under the gateway line you need to add dns servers to use when you have static config. Add the following:
```
dns-nameservers 8.8.8.8 8.8.4.4
```

Save and close the file, and then restart the networking service or reboot the machine.

Also, how are you connecting the machine to the router? Directly to the router? And are you sure the router has the 192.168.1.1 address and that 192.168.1.7 is not used for another device in the network? Make sure you don't create IP conflict when selecting the static IP for the server.

It's strange that your interface is called enp8s0. Usually it's something like eth0.

---

### Post by Swedz on 2016-05-06
I made those changes, changed address to 192.168.104 just to test. Still the same results, unable to ping anything.

I am connecting to the router through Ethernet, I am sure the router has 192.168.1.1 because on my main PC I can go to 192.168.1.1 on my browser to access my router.

Yes, I am confused about the interface name too. :P

---

### Post by $yl9pAR%t on 2016-05-06
These new interface names was introduced along with systemd.

Can you ping your router?

Output of this command could be helpful:

```
inxi -n
```

---

### Post by Swedz on 2016-05-06
I cannot ping my router.
I cannot do inxi -n because I don't have the inxi program, and when I try to install it, it says:
```
E: Unable to locate package inxi
```

---

### Post by $yl9pAR%t on 2016-05-06
Did you tinker with firewall? If you did, paste output of:

```
sudo ufw status verbose
```

How many devices are connected to your router? Is it possible 192.168.1.7 is reserved as darkod said?

edit: sorry just noticed you have changed it.

edit2: but if this number is 192.168.1.04 (you typed 104) change it to higher (for example 192.168.1.44).

---

### Post by Swedz on 2016-05-06
I did not change my Firewall settings. I changed address to 192.168.1.44 with the same results, unable to ping my router or outer IPs.

---

### Post by darkod on 2016-05-07
Hmmm, strange. Well, lets do more troubleshooting...

In your /etc/network/interfaces change the line 'auto lo enp8s0' into 'auto lo'. You have the 'auto enp8s0' later so you don't need it twice.

Also, have you tried to see if it will work with dhcp? I agree servers should always have static IP but in this case lets see how dhcp behaves.

1. In /etc/network/interfaces modify the setting to 'iface enp8so inet dhcp'. Comment all below lines by putting # at the start. That way you can easily uncomment them later without retyping everything. Check if the server receives an IP and which one and whether ping 192.168.1.1 works. Don't forget you need to restart the server or the networking service each time you make changes to the network setup.

2. On the routers usually there are led lights for the ports. Does the light goes on for the port where you connect the server?

3. Try another port on the router side.

4. Try another network cable.

Let us know how it goes...

---

### Post by Swedz on 2016-05-07
Removed the enp8s0 on the auto lo line, same results.

I have tried dhcp before, but I tried it again anyways and it took about 5 minutes to boot up due to 'A start job is running for Raise network interfaces'. Once that finished I checked my ifconfig, just to see it doesn't have an IP anymore. But it still detects the enp8s0.

I will play around with the router stuff and I'll get back to you.

**EDIT:** I have done some inspecting and it seems as though the PC that I installed Ubuntu 16.04 Server on isn't wired correctly. Let me give you a bit of a background story so this makes sense; in my house right now, we're moving stuff around a lot. So we moved the router to a new part of the house, and this was happening the same night I was installing Ubuntu 16.04 Server for the first time. So I have concluded that this is probably an issue with my wiring. Thank you for your help! :D

---

### Post by darkod on 2016-05-07
OK then, it looks like you seem to have located the problem. Take care the wiring is good and it should work right away... If not, post back. :)

---

### Post by Swedz on 2016-05-07
It has been solved! It was faulty wiring. The wire I was using was not even plugged in. :mad:

Thank you for your help! :D
Swedz

---

