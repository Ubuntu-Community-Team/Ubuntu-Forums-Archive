---
title: "Server with 2 NICs"
date: 2006-12-04
forum: Server Platforms
---

### Post by koolguynet on 2006-12-04
Ok, I am confused by something I am trying to do and can't get it to work.  It is completely possible that I have went about this the wrong way.  I have a little home server that runs ssh, smb, and apache.  I use it to host a few websites, enable remote access to my network and as a basic fileserver.  I managed to get a public IP address for it, but whenever I try to get a file from it while on my LAN, it would run the request through my router which is alot slower than my Gigabit switch and Samba won't work through the public IP address.  So here was my thought, get two NICs, one with the public IP and the other with a private internal IP.  I have done that and I can't make them both work at the same time.  I can disable one card and the other works fine and vice versa.  What am I doing wrong?  Can this be done?  Here is my ifconfig (note that eth1 has been disabled):
 ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:A0:C9:81:6D:B7
          inet addr:216.31.xx.15  Bcast:216.31.xx.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:c9ff:fe81:6db7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:578168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:751457823 (716.6 MiB)  TX bytes:32025966 (30.5 MiB)

eth1      Link encap:Ethernet  HWaddr 00:18:E7:07:B4:C9
          inet addr:192.168.0.50  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:132397 (129.2 KiB)  TX bytes:6065 (5.9 KiB)
          Interrupt:11 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:424 (424.0 b)  TX bytes:424 (424.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Iowan on 2006-12-04
Post the **/etc/network/interfaces** file.
I'm curious how the NIC's are set to get their addresses.

---

### Post by koolguynet on 2006-12-04
/etc/network/interfaces  Here it is:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# The primary network interface
iface eth0 inet static
address 216.31.xxx.15
netmask 255.255.255.0
gateway 216.31.xxx.8


iface eth1 inet static
address 192.168.0.50
netmask 255.255.255.0
gateway 192.168.0.1



iface eth2 inet static
address 192.168.0.50
netmask 255.255.255.0
gateway 192.168.0.1









auto eth0

---

### Post by technodigifreak on 2006-12-04
> **koolguynet said:**
> 
# The primary network interface
iface eth0 inet static
address 216.31.xxx.15
netmask 255.255.255.0
gateway 216.31.xxx.8

iface eth1 inet static
address 192.168.0.50
netmask 255.255.255.0
gateway 192.168.0.1

iface eth2 inet static
address 192.168.0.50
netmask 255.255.255.0
gateway 192.168.0.1


out of curiosity, why do eth1 and eth2 have the same IP? also, by default not one of these interfaces will come up with out the auto clauses ```
auto ethX
``` 

And what about the *network* and *broadcast* entries for each interface?

A good example of an interfaces file can be found at [http://david.decotigny.free.fr/libre/ibook2-debian/etc/network/interfaces](http://david.decotigny.free.fr/libre/ibook2-debian/etc/network/interfaces)

---

### Post by koolguynet on 2006-12-06
I don't know what the autox is, I manage everything through GUI.  As it turns out, I had the wrong Netmask and needed to reconfigure my network so it made more sense.  In essence I created a private and a public network with the two ethernet cards connected to the different networks.  It works great now!  Thanks for everyone's help!

---

### Post by andyjenkins on 2006-12-06
You do not want the gateway set on the internal NIC.  "Gateway" means that if your computer cannot figure out what interface to send a packet on, it sends it to the gateway and lets it handle it.  So, on eth0, gateway points to your ISP's router, which knows "this packet is for google -> send it towards Cali" or "this packet is for CNN.com -> send it towards Georgia (i think)."  Obviously more complicated, but this is the general idea.

How your computer decides if it "knows" where to send a packet is based on the IP and subnet masks of the interfaces, so, with your setup, any packet destined for 216.31.xxx.* (*=anything) goes out eth0, any packet destined for 192.168.0.* goes out eth1, and after this (i.e. the packet is not for 216.31.xxx.* or 192.168.0.*), it looks at its gateways.  If both interfaces are up, then there are two gateways defined, and I think it gets to pick either (maybe every other packet goes out eth0/eth1?).  What you want is for all the packets that arent 216.31.xxx.* or 192.168.0.* to go out eth0, for your gateway 216.31.xxx.8, which will then send them the correct way.

The reason it works when eth1 is disabled is that when it's checking gateways, it knows that it can't use eth1 (since it's disabled), so it has to go to 216.31.xxx.8.

So, remove 'gateway 192.168.0.1' from both eth1 and eth2 and it ought to work.  You don't need gateways defined for every interface.  You can check out your routing tables at any time by doing 'route -n' from the command line - as you turn eth0,1 and 2 on and off, you'll see this table change.

---

