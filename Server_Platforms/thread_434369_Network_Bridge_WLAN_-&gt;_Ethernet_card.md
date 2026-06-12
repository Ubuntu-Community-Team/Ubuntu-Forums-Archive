---
title: "Network Bridge WLAN -&gt; Ethernet card?"
date: 2007-05-05
forum: Server Platforms
---

### Post by mogie on 2007-05-05
I was surprised to find so little documentation on how to set up a bridge connection between two NICs in Ubuntu while Googling. I found some documentation on linux in general, but I didn't see clearly what to do in the doc. Talking of [this doc if you were wondering. ]("http://linux-net.osdl.org/index.php/Bridge#Sample_setup")So here I am crying my throat out cause I hopes it is an easy solution to it! :)

I have a WLAN network card which I expect(!) will work on the server I'm going to set up - with driver compatibilities part of course - and a 3Com fast ethernet adapter too. The WLAN configuration (iwconfig) can I handle myself. I'm quite experienced with network configurations from earlier, in both WLAN and LAN.. :p

Basicly I want it this way:
 
Wireless router --> (WLAN client -> bridge -> 3Com Ethernet) --> other network.

I don't know if I should explain it harder. If it's a bit short please let me know :) 

Thanks to everyone trying to help me on this issue!

---

### Post by mogie on 2007-05-06
I've now configured my network with the following devices:

[LIST]
[*]eth0 - 3Com Fast Ethernet adapter
[*]wlan0 - Dlink Air 802.11b device
[*]br0 - my virtual bridge device
[/LIST]

These are my IPs:
ModemRouter (DNS/DHCP-server/Gateway to Internet) - 10.0.0.138
Access Point - 10.0.0.99 (don't think it is playing any important role since I've already preconfigured it with iwconfig. )


Installed brctl with:
```
apt-get install bridge-utils
```
I'm not sure of if I would need to compile the bridge-utils for my kernel (2.6.17-10-386 - Ubuntu Edgy 6.10) so I'm taking the chance it will work by default.

```
# brctl addbr br0                                   
# brctl addif br0 eth0                              
# brctl addif br0 wlan0     
# ifconfig eth0 0.0.0.0
# ifconfig wlan0 0.0.0.0                     
# ifconfig br0 10.0.0.70 netmask 255.255.255.0 up 
```
In the last line I'm configuring the br0 to be part of the network. I can also set it up without too replacing the line with the following:
```
# ifconfig br0 up
```
             
I've now managed to ping from:

Bridgeserver to: 
[LIST=1][*]Access Point[*]ModemRouter[*]Any client on network (both on the wired and WLAN)[/LIST]

Clients to:
[LIST=1][*]br0[/LIST]

What I cant do is to ping from clients to the ModemRouter nor AP.

To make it even more easy to understand I've made this desperately bad drawing of how I want to have it:

[ATTACH]31936[/ATTACH]

---

### Post by gnottage on 2007-05-11
I've tried to do something very similar in the past, but never had it working. In the end I used WinXP to do the bridge which just worked. Now I don't need it, but it's a shame that bridging like this isn't really working yet in Linux.

---

### Post by thomas79 on 2007-05-15
I'm stuck with a similar problem when trying to configure Ubuntu as a bridge between ethernet and wireless. However, my wireless card is a D-Link 660 Air and the wireless network is set up in ad hoc mode.

As mogie, I'm able to ping from the bridge to both networks and from both networks to the bridge, but a machine on the wireless network  can't ping a machine on the ethernet and vice versa.

Using Ethereal, I can see that ARP-messages are passing through the bridge without problems, but the ICMP-messages sent when doing a ping does not pass through the bridge.

The document that mogie mentions suggests that when only ARP and STP traffic gets through the bridge, one should disable ethernet filtering by setting the files in /proc/sys/net/bridge to zero (see [http://linux-net.osdl.org/index.php/Bridge#No_traffic_gets_trough_.28except_ARP_and_STP.29]("http://linux-net.osdl.org/index.php/Bridge#No_traffic_gets_trough_.28except_ARP_and_STP.29")). I did that, but it doesn't seem to help. It is still only ARP that goes through the bridge.

Any help would be very appreciated!

PS If needed I can post my output from ifconfig, brctl, etc. but I suppose my problem is just like mogie's, so it isn't needed.

---

### Post by RawDR on 2007-05-19
I've been trying to do this EXACT thing. I even swapped out the acx111 minipci in my PCI adapter for an isl3890  minipci (had to resolder the antenna pigtail) in hopes for better wireless support. No luck so far with the bridging.

Anyone else made any progress?

---

### Post by mogie on 2007-10-16
I also need to mention that MOST network adapters doesnt support bridging because the lack of driversupport. I remember that I've found a spesial site once documenting this, and there was some spesial drivers to configure the adapters to support this. I will try to find it ... but that was a long time ago.

Thanks again for all the response, though I gave up hope a long time ago and don't need this service anymore.

---

