---
title: "DHCP times out in network manager for eth0 on gazp5"
date: 2007-12-05
forum: System76 Support
---

### Post by jmcnaught on 2007-12-05
Today Network Manager stopped working for wired connections on my Gazelle Value w/ Nvidia (model gazp5).

When I try to connect to a wired network, it keeps spinning and never ends up getting an IP address from my router.  Eventually it will show the two computers icon, but if I right click and choose connection information all of the IP addresses are 0.0.0.0.  In the dialog NM also shows that the driver is "tg3"

I have no problem connecting to wireless networks with network manager.  And if I use "sudo dhclient eth0" I get an IP address from my router instantly (although NM doesn't seem to realize it).  NM is also able to detect the ethernet cord being inserted/removed.

The only interface I have listed in /etc/network/interfaces is lo.  Both eth0 and eth1 are set to roaming mode in network-admin.

I have purged network-manager and network-manager-gnome and reinstalled them.  I've also  run the system76 driver (install & restore).

This all started after my router went bonkers and had to be reset.  After resetting it I could connect to it from all the devices in the house except my laptop (unless I use dhclient.. which I don't want to have to do regularly).

Any suggestions?

Edit: I forgot to mention that i'm running gutsy 32-bit, completely up to date.

jeremy@sabcat:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1B:38:4C:60:9E  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2679586 (2.5 MB)  TX bytes:443664 (433.2 KB)
          Interrupt:17

---

### Post by thomasaaron on 2007-12-05
Just to clarify:

Does your /etc/network/interfaces file look exactly like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

Please confirm that you are trying to connect via network manager (the little monitor icon in the upper right. Trying to connect with System > Admin > Network tends to hose the interfaces file.

---

### Post by jmcnaught on 2007-12-05
That is exactly how my /etc/network/interfaces looks.  And yes, I'm trying to connect with network manager.

---

### Post by thomasaaron on 2007-12-05
OK. I'm not trying to delay things here, but are you saying that you've (since the reset) tried a number of other computers with your router using a WIRED connection?

If not, please verify that your wired connection is good. If Network Manager is connecting to the router, but you are not getting an ip address, it makes me suspicious of the actual connections and maybe even the router itself.

NOTE:
Are you using a WIRELESS modem that is connected to your router, which is then connected to your laptop?

If so, you may need to contact your wireless provide and ask them how to configure you modem with whatever brand of router you have. We ran in to this one the other day with another customer. Everything seemed to be connecting, but there was no ip address.

---

### Post by jmcnaught on 2007-12-06
The other computers on my network (and a vonage phone) had no problem connecting, otherwise I wouldn't have posted this in the first place.

The problem however has somehow resolved itself.  You were probably correct in guessing a problem with my router.   Thanks for the help.

---

