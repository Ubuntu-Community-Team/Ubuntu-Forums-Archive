---
title: "dhcp3-server and a wireless router"
date: 2011-08-25
forum: Server Platforms
---

### Post by {davros} on 2011-08-25
if i can get this new server work and run dhcp3-server, is it possible to add a wireless router? if i assign in the routers setting an ip? so that the order of devices would be.....

modem ->
server ->
switch ->
clients and wireless router


any help would be greatly appreciated with if this will work or what i should do and how to configure it.

---

### Post by volkswagner on 2011-08-25
Yes.

You will want to set up the router as an access point only.  Don't connect to the WAN port.  The WiFi router will be an additional switch and access point.  You can the set a static ip for the WiFi access point outside your dhcp range.

Some router firmware/software will allow you to remap the WAN port if you need more available LAN ports.

---

### Post by {davros} on 2011-08-25
thank you, somehow while i slept this idea came to me, putting the wireless router in that way. i only need it for my wife's macbook. 

now to tackle the dhcp3-server and get this running. then file and web server .....

---

### Post by {davros} on 2011-08-25
right now it wont even share a connection... 

here is my ifconfig...

eth0      Link encap:Ethernet  HWaddr 00:50:45:01:08:ba  
           inet addr:[66.189.112.57]("tel:66.189.112.57")  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::250:45ff:fe01:8ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2500624 (2.5 MB)  TX bytes:206021 (206.0 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
           inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
          RX bytes:24703 (24.7 KB)  TX bytes:24703 (24.7 KB)

notice that eth1 is not listed it no longer has an address or subnet assigned to it .. trying to start over again...
 
i also dont understand what address should be assigned to eth1 honestly.

ok i first used dhcp3-server, with these settings in the dncpd.conf file ...

default-lease-time 600;
max-lease-time 7200;
 option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option domain-name “[yourdomainname.com]("http://yourdomainname.com/")”;
 subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.200;
}


i used "[mine.org]("http://mine.org/")" for the domain name cuz i really dont have one i guess.


i set eth1 to 

sudo ifconfig eth1 broadcast 192.168.1.255 netmask 255.255.255.0
  

and i got it to give out ip addresses that did nothing lol.

---

