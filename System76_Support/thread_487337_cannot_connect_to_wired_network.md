---
title: "cannot connect to wired network"
date: 2007-06-28
forum: System76 Support
---

### Post by dgermann on 2007-06-28
Hi--

My new Gazelle value arrived today. Tried to connect to my network (have several Ubuntu Dapper machines) and cannot get any connection.

When I run a ping 192.168.0.1 it reports "Network is unreachable." Firefox cannot find Google.

I have tried setting the network manager to roaming, dhcp and static ip. None of them works. In fact, it does not seem to even have any place to activate the connection, like Dapper does.

It reports this as settings for eth1; should it not be eth0?

I just tried a wireless connection. The icon with the two black monitors changed to bars like on the cell phone ads on tv, and hovering over it says "wireless network connection to 'name of network' 0%. I cannot ping other computers on the network, nor even google.com. My router is a netgear WNR854T, and the security is set to WPA-PSK [TKIP] + WPA2-PSK [AES]; I have set wireless security to WEP 128 bit Passphrase on the system76.

Thanks!

---

### Post by thomasaaron on 2007-06-29
Welcome aboard, dgermann.

If you don't like the eth1 instead of eth0 thing, try this:
[http://system76.com/forums/viewtopic.php?t=2062&highlight=wireless](http://system76.com/forums/viewtopic.php?t=2062&highlight=wireless)


Regarding networking:
Feisty uses network manager, not the System > Applications > Networking method used in Dapper.

If you have used System > Applications > Networking to attempt connection, you've probably hosed your interfaces file, which should look like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to 
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little 
computer monitor).

To do this, you should be able to right-click it and select your network. You will be prompted for any necessary security information.

---

### Post by dgermann on 2007-06-29
Thanks, Thomas--

I will check it out. I know I went into the same screen from both directions (network manager and system> etc) and made some changes.

Actually, all the computers on my network have static ipaddresses--only the router is set to dhcp, so I know I changed some things.

I wonder if it had to do with rebooting? After I posted, I shut down and went to another known good connection point and cable and it connected from there. So it seems to be working.

How about the wireless end? Was there a mismatch that did not allow me to connect? What do you see in my original post, if you please?

---

### Post by thomasaaron on 2007-06-29
I'm not sure. Network Manager in Feisty seems to be very picky about being EXACTLY the same as the router settings.

---

### Post by misconfiguration on 2007-06-29
> **thomasaaron said:**
> I'm not sure. Network Manager in Feisty seems to be very picky about being EXACTLY the same as the router settings.


I've noticed this as well..

---

### Post by dgermann on 2007-07-03
Hi--

Well, got a chance to play with this tonight. I edited my /etc/network/interface file 3 or 4 ways, but nothing seems to work. I now have it set to just those two lines uncommented, as someone suggested.

I ran pppoe.conf and it found 3 connections: eth1; eth2; eth1:avah (what is that??), but then says "the Access Concentrator of your provider did not respond." It is connected via a cable.

My Netgear router does not see it as connected.

I can ping the server, but no other computer on the network.

How do I go about troubleshooting this, please?

---

### Post by thomasaaron on 2007-07-05
This problem solved here:
[http://system76.com/forums/viewtopic.php?t=2257](http://system76.com/forums/viewtopic.php?t=2257)

---

### Post by dgermann on 2007-07-05
Thomas--

Many thanks for your help here and on the system76 forums. 

Yes, my issue with the system76 connection seems to have been solved; not sure if it helps a lot of other people, but it might have some clues!

---

