---
title: "Help with home network setup"
date: 2011-02-28
forum: Server Platforms
---

### Post by skclewis on 2011-02-28
I want to set up a small home network to use as a test platform and development work.  I am using a former desktop box with an AMD-64 Dual Core processor, 1GB RAM, and two 500GB SATA drives.  I also installed a second NIC so I can attach my laptop to the server once I get it running. My Internet connection is through a satellite using a RJ-45 connectionior.  Prior to rebuilding, the desktop ran Windows XP and connected to the Internet just fine.  The service provider links my account with the MAC address.  I installed Maverick 10.10 64-bit but may not have installed all the necessary packages.  I tried to follow the Ubuntu Server Guide as well as a book I bought on Ubuntu Server 10.10 Administration.  While installing I could not use the autoconfiguration because software couldn't find the NIC or make an Internet connection.  So I opted to configure manually later.  I installed DHCP, LAMP, and Print Server packages.  All went well and the installation completed.  When it rebooted, I configured the NIC as eht0 and it shows up in ifconfig.  However there is still no Internet connection.  I am attempting to call my service provider for assistance but not sure what they can tell me.  When in Windows, the IP protocol was set for auto DHCP and DNS.  This leads me to believe the service provider is assigning an IP address when the computer connects.  Thus I am believing this may be part of my problem. I don't have a router yet but have a 3G wireless router coming (I just moved to the Philippines and all my stuff hasn't arrived).  The router works using an aircard.  My service provider offers a aircard instead of the satellite so I may switch once my router arrives.  However in the meantime, I would appreciate any help in obtaining an Internet connection on my current server configuration.  This is my first time setting up a Ubuntu/Linux server and things are confusing to me to say the least.  If I need to re-install the server package I can do it without any issues since I can't use it as it is for what I intend.  Thanks!!

---

### Post by ian dobson on 2011-03-01
Hi,

When you type ifconfig what do you see exactly? It should look something like this:-
```

eth0      Link encap:Ethernet  HWaddr bc:ae:c5:97:28:4d
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:fe97:284d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36029343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31963357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:35928764020 (35.9 GB)  TX bytes:31311359426 (31.3 GB)
          Interrupt:18 Memory:fb500000-fb520000
```
note the inet addr.

If if doesn't show an ip address for your eth0 card then edit the file /etc/network/interfaces (you can use nano to edit & control x to edit and save)

so you have the line 
iface eth0 inet dhcp

this will cause linux to use dhcp to get the ip configuration.

Regards
Ian Dobson

---

### Post by skclewis on 2011-03-09
Thanks Ian, that worked!:p

---

